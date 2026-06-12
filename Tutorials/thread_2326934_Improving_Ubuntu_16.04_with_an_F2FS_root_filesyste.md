---
title: "Improving Ubuntu 16.04 with an F2FS root filesystem:"
date: 2016-06-06
forum: Tutorials
---

### Post by Luke_Fulcomer on 2016-06-06
[b][size=3]Moderator comment:

Do not use this "tutorial" - see close note below in post #5[/size][/b]


Improving Ubuntu 16.04 with an F2FS root filesystem:


F2FS offers major benefits and advantages over other filesystems when used on a flash device like an SSD.
    
Ubuntu has had the ability to read F2FS for quite some time (12.04), but the provided installers (even 16.04) don't have F2FS modules loaded; 
One cannot select F2FS partitions as an install destination even if they are created beforehand...


Thankfully, we can still use an F2FS root without too much effort, we just need the kernel to load the f2fs module at boot, then point grub to an f2fs partition.
There may be other ways to accomplish this, but I was not able to find any working solutions via Google-fu.


Start the ubuntu installer normally,


At the selection for install destination, select 'Something else', then manually partition:


    sda1    /boot     512MB ext4
    sda2    /swap    8GB (Whatever ram size is)
    sda3    DNU        10GB RAW (prevents you having to move it or have a gap later when you delete the ext4 partition)
    sda4    /        10GB ext4


If you have a separate disk installed:
    
    sda1     /boot    512MB ext4
    sda2    /swap    8GB
    sda3    DNU        Rest of drive space
    sdb1    /        10GB ext4


If you have a separate disk, be sure to adjust the mount points listed below.


Complete the installation normally, then reboot 


Editing the grub defaults is optional, but if you mess up somewhere you'll be able to see where things went kerfuffle.
leaving the splash and quiet options on mean you'll only see the error and not what was happening before it.


Open (alt+f2, gksudo gnome-terminal) or switch to a terminal (Ctrl+F1-F5, F6 returns to GUI)
        
```
        sudo gedit /etc/default/grub 
                  GRUB_DEFAULT=0
```


Comment out the hidden grub menu setting so we can see the damned thing;
You might have to do this before you are able to start a grub command line to run vbeinfo. 
Make sure you update-grub before you reboot if this is the case.

```

            #GRUB_HIDDEN_TIMEOUT=0
            #GRUB_HIDDEN_TIMEOUT_QUIET=true
```
            
Turn down the timeout. 3 seconds is AGES. 10 is for people who have the reaction time of a corpse.            
```

            GRUB_TIMEOUT=3
            GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
            GRUB_CMDLINE_LINUX_DEFAULT="text"
            GRUB_CMDLINE_LINUX=""
```

uncomment the graphics mode line. 
change the entry to whatever optimal resolution your display supports. you can get this from the grub command line 'vbeinfo'
```
 GRUB_GFXMODE=1366x768x32
```
uncomment the text only line
```
GRUB_TERMINAL=console
```
save the grub defaults file
```
update-grub 
```            
to pull the new defaults into the grub configuration on /boot            

now we install f2fs and setup the module in initramfs

The next two lines prepare the current installation to boot a F2FS root.
We want to do this before we copy the installation to the F2FS root.
Without the f2fs module, grub will fail to mount the f2fs partition, leaving you stuck at an initramfs prompt.

Update apt's sources, then install f2fs-tools and gparted

        ```
sudo apt update && sudo apt install f2fs-tools gparted
```

Tell initramfs to load the F2FS module at boot (rather than on demand)

```
sudo echo f2fs >> /etc/initramfs-tools/modules && sudo update-initramfs -u
        sudo reboot
```

now that the installation is ready for f2fs boot, re-enter the terminal
    
```
sudo gparted 
```
select sda3, format to F2FS the same size or larger than your ext4 partition,
copy the UUID from the partition information dialog
now we add the UUID to the fstab
```
sudo gedit /etc/fstab
```
comment out the ext4 line
paste the UUID you copied (or run blkid to find it) followed by     
```
 /    f2fs    rw,relatime,background_gc=on,user_xattr,acl,active_logs=6    0    0
```

this is what my fstab looks like
```
       # /etc/fstab: static file system information.
        #
        # Use 'blkid' to print the universally unique identifier for a
        # device; this may be used with UUID= as a more robust way to name devices
        # that works even if disks are added and removed. See fstab(5).
        #
        # <file system>    <mount point>    <type>    <options>    <dump>    <pass>
        # / was on /dev/sda4 during installation
        #UUID=71f42e33-6984-4905-9932-17cd4adb7b41    /    ext4    errors=remount-ro    0    1
        UUID=84e54b79-8671-4acb-9dbc-f89b17667cf6    /    f2fs    rw,relatime,background_gc=on,user_xattr,acl,active_logs=6    0    0
        # swap was on /dev/sda2 during installation
        UUID=0a3b409b-f7bf-4a22-a05f-0dc35e1bb111    none    swap    sw    0    0
```

if you want to check root filesystem at boot, change trailing 0 to 1
if you just want to wing it and check at boot yourself, touch /forcecheck to make init clean the filesystem at next boot. util-linux will delete the forcecheck file when it finishes.

We can't update-grub yet because the f2fs partition is still empty; grub-probe will ignore it for obvious reasons.
So, we need to copy the current root to the new f2fs root;

Reboot to Live USB/CD
switch to a terminal. 

make dirs and mount our stuff to them            
```
        sudo mkdir /media/ext4 
        sudo mkdir /media/f2fs
        sudo mount /dev/sda4 /media/ext4 
        sudo mount /dev/sda3 /media/f2fs
```

copy the installation to the f2fs partition
```
sudo cp -a /media/ext4/* /media/f2fs
```

The following lines set up the chroot so update-grub doesn't misinterpret our intention (or just fail catastrophically)
    
```
        sudo mkdir /media/f2fs 
        sudo mount /dev/sda3 /media/f2fs
        sudo mount /dev/sda1 /media/f2fs/boot
        sudo mount --bind /dev /media/f2fs/dev
        sudo mount --bind /proc /media/f2fs/proc
        sudo mount --bind /sys /media/f2fs/sys
        sudo chroot /media/f2fs
```
the prompt should change from $ to # 
```
update-grub
```

Grub will probe for partitions, pause for gyrations, call it's mum, then pass the new uuid you added to /etc/fstab into the grub configuration stored in /boot

If you're feeling saucy, delete the ext4 partition in gparted and run update-grub inside the chroot again. 
This removes unnecessary entries in the grub menu. 

Exit the chroot, make sure to cross those stubby fingers. 


```
exit
umount /media/f2fs/*
```
If you forget to unmount the bound directories, issuing a reboot takes forever (something about graceful dismounts? maybe someone else can explain)

```
sudo reboot
```

That's it! If everything went smoothly, you should now be at the login prompt or desktop; if you run mount in a terminal you will see /dev/sda3 is mounted as F2FS to /        


if you reboot and end up at an initramfs prompt with the following error:


    Target filesystem doesn't have requested /sbin/init.
    No init found. Try passing init=bootarg.


Check to be sure you are
    
    installing f2fs, and apt is not failing for whatever reason
    inserting f2fs into /etc/initramfs-tools/modules
    inserting the new UUID and options into /etc/fstab
    running update-grub from chroot after copying the installation to sda3

---

### Post by pongo101 on 2016-09-01
Thnk you so much, very useful guide, but there is a problem.

When you run update-grub the file /boot/grub/grub.cfg is updated but on "linux" line there is the partition path /dev/sd.. instead of the UUID, this is very annoying especially for the USB drive that can change name on every reboot.

The problem is caused by /usr/sbin/grub-probe launched on line 140 of /usr/sbin/grub-mkconfig, grub-probe does not support F2FS filesystem and can't read the UUID, so the variable $GRUB_DEVICE_UUID is not set and the script at /etc/grub.d/10_linux has to use the device path /dev/sd.. in $GRUB_DEVICE instead.

To workaround the problem without changing system script, I added the following line in /etc/default/grub:
```

if [ -z "$GRUB_DEVICE_UUID" ] && [ -n "$GRUB_DEVICE" ]; then
  GRUB_DEVICE_UUID=`blkid -s UUID -o value "$GRUB_DEVICE"`
fi

```

To set $GRUB_DEVICE_UUID with blkid from $GRUB_DEVICE if $GRUB_DEVICE_UUID is empty. I put it there because /usr/sbin/grub-mkconfig read it after running grub-probe but before any script in /etc/grub.d/.

---

### Post by wayover13 on 2017-10-30
This "formula" also did not work for me. The matter under discussion is probably kernel dependent. Someday all kernels may well have all necessary f2fs modules compiled ino them. But for now, a lot of systems have kernels that treat them as loadable modules, and they need to be explicitly loaded into the initramfs in order for the system to be able to cope with a root f2fs partition. I have some experience with this, having just gotten my Arch system booting to an f2fs root partition. In that case, information I was running across indicated that it would be necessary to load into the initramfs various crc* modules. But that didn't work. It wasn't until I'd explicitly loaded, in addition to those, the f2fs module, that it finally began to work.

Likewise, but in reverse, with these directions. The directives indicate that only the f2fs module needs to be loaded into the initramfs (sudo echo f2fs >> /etc/initramfs-tools/modules && sudo update-initramfs -u). But that did not make my root partition bootable. It was only after I'd loaded the various crc* modules into the initramfs that my root partition would finally boot. The names of those modules can be found in this thread: [https://bbs.archlinux.org/viewtopic.php?id=210673](https://bbs.archlinux.org/viewtopic.php?id=210673). So the additional step that may be required in order for you to get your f2fs root partition to boot will be to do something like ```
sudo echo crc32 >> /etc/initramfs-tools/modules sudo echo libcrc32c >> /etc/initramfs-tools/modules . . .
``` and so forth. My advice is that you not risk leaving out those modules. You may end up wasting hours trying to figure out why your f2fs root partition won't boot (like I did) if you do not include them in the initramfs.

---

### Post by coffeecat on 2017-10-31
I'll close this thread and, since all three respondents so far report significant problems, advise all not to follow this "tutorial".

The [Tutorial Guidelines]("https://ubuntuforums.org/showthread.php?t=2143602") are quite clear:

> **Tutorials should be supported.**

[indent]You are expected to offer support for your tutorial, within practical limits. If you fail to respond to requests for help or clarification within a reasonable time, or fail to update your tutorial, the thread will be closed or removed.[/indent]

The OP is a drive-by. The author registered to the forum, posted and logged out all on the same day over 16 months ago, and has not had the courtesy to come back since.

Thread closed.

---

