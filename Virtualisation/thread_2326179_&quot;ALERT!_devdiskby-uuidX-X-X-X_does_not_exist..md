---
title: "&quot;ALERT! /dev/disk/by-uuid/X-X-X-X does not exist.&quot; when booting Ubuntu with Xen"
date: 2016-05-29
forum: Virtualisation
---

### Post by Mikael_Niemel on 2016-05-29
Well, I decided to go ahead and try Ubuntu server with Xen to virtualize stuff. This is mostly because my server is a bit older Opteron machine, which doesn't support full hardware virtualization, so KVM is out and VirtualBox doesn't have as good performance as Xen. Also, I'd like to use zfs (as it's finally supported properly in Linux, yay!) from Dom0 as the storage for various virtual machines.

So, I tried to install Xen according to instructions (minus LVM part): [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

But I get this error when trying to boot Ubuntu with Xen. When I choose plain Ubuntu from the Grub menu, then it boots just fine.


[COLOR=#272727][FONT=Verdana]Gave up waiting for root device. Common probleMs:[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]— Boot args (cat /proc/cmdline)[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]— Check rootdelay= (did the systeM wait long enough?)[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]— Check root= (did the systeri wait for the right device?)[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]— Missing Modules (cat /proc/Modules; ls /dev)[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]ALERT? /dev/disk/by-uuid/X—X—X—X—X does not exist.[/FONT][/COLOR]
[COLOR=#272727][FONT=Verdana]Dropping to a shell!


Any idea how to solve this?[/FONT][/COLOR]

---

### Post by Mikael_Niemel on 2016-06-01
..anybody?

---

### Post by MAFoElffen on 2016-06-01
Please post the linux boot line argument from your Xen boot section. The line will start with "linux".

---

### Post by Mikael_Niemel on 2016-06-02
I didn't find a line starting with "linux" in the Xen boot section in /boot/grub/grub.cfg. This is what that section has:

> menuentry 'Ubuntu GNU/Linux, with Xen hypervisor' --class ubuntu --class gnu-linux --class gnu --class os --class xen $menuentry_id_option 'xen-gnulinux-simple-X-X-X-X-X$        insmod part_msdos
        insmod ext2
        set root='hd5,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  X-X-X-X-X
        else
          search --no-floppy --fs-uuid --set=root X-X-X-X-X
        fi
        echo    'Loading Xen 4.6-amd64 ...'
        if [ "$grub_platform" = "pc" -o "$grub_platform" = "" ]; then
            xen_rm_opts=
        else
            xen_rm_opts="no-real-mode edd=off"
        fi
        multiboot       /boot/xen-4.6-amd64.gz placeholder   ${xen_rm_opts}
        echo    'Loading Linux 4.4.0-22-generic ...'
        module  /boot/vmlinuz-4.4.0-22-generic placeholder root=UUID=X-X-X-X-X ro
        echo    'Loading initial ramdisk ...'
        module  --nounzip   /boot/initrd.img-4.4.0-22-generic
}




And this is the normal Ubuntu section, which works fine, and has the "linux" line

> menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-X-X-X-X-X' {        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd5,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  X-X-X-X-X
        else
          search --no-floppy --fs-uuid --set=root X-X-X-X-X
        fi
        linux   /boot/vmlinuz-4.4.0-22-generic root=UUID=X-X-X-X-X ro
        initrd  /boot/initrd.img-4.4.0-22-generic
}




---

### Post by MAFoElffen on 2016-06-03
Please post file /ect/default/grub...

EDIT-- 
Didn't hear back from you yet... but this is what I am looking for / if you addedd Xen boot option to your command line in your default file such as this:
```

# Xen boot parameters for all Xen boots
GRUB_CMDLINE_XEN="dom0_mem=1024M,max:1024M"

```

---

### Post by Mikael_Niemel on 2016-06-04
I have been a bit busy, so I'm taking a look it just now.

Anyways, I didn't find a line like that at all, I'll try adding it..

EDIT: That didn't work.. also, here's my current [COLOR=#000000] /ect/default/grub. Line starting with [/COLOR]GRUB_CMDLINE_XEN was added by me just now.[COLOR=#000000]

[/COLOR]```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_XEN="dom0_mem=1024M,max:1024M"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Mikael_Niemel on 2016-06-16
Any further ideas how to solve this? :(

---

### Post by MAFoElffen on 2016-06-16
Yes. I had to look further back into this specific error. I found it under some Ubuntu Precise 12.04 LTS error codes. It doesn't specifically have to do with Xen itself. It has to do with the boot process. This error usually comes up when it reads the fstab and tries to mount filesystems for parts of the default directories. For instance, where "/" (root) and swap is, identified by their  UUID's ... and when it hits a UUID that it can not find, it thorows this message, and usaully drops down to a grub rescue or  busybox prompt.

The thing to do is to look at, and/or post your /etc/fstab file and the results of 
```

sudo blkid

```
then you/we would match up the UUID's and ensure that what is in the fstab matches up with the output of what is physically there.

Does that make sense as a plan?

---

### Post by Mikael_Niemel on 2016-06-17
Here's my /etc/fstab file:

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=88bae243-a8d2-4435-913a-eca6e6807646
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=a41a19e5-80f2-4715-8062-56f3b9915a46
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

IIRC those commented out UUIDs were there before I replaced them with /dev/sda1 and /dev/sda5 as I tried to solve the issue. Anyways, the odd thing is that Ubuntu boots just fine without Xen, doesn't it use the same fstab file?

Also, here's what blkid gave:

```
/dev/sda1: UUID="88bae243-a8d2-4435-913a-eca6e6807646" TYPE="ext4" PARTUUID="0009e8cc-01"
/dev/sda5: UUID="a41a19e5-80f2-4715-8062-56f3b9915a46" TYPE="swap" PARTUUID="0009e8cc-05"
...
...

```

---

### Post by MAFoElffen on 2016-06-18
I do not see anything wrong with the original filesystem UUID's. After you update an fstab file, then you should update your initramfs files... so the initial boot ram disk matches what is physically there.

But you bring up an interesting point. one thing that is different between the normal boot on a kernel and a Xen boot, (as it relates to finding storage devices) is the initramfs images.

If update the boot images for 4.4.0-22-generic via:
```

sudo update-initramfs -u 4.4.0-22-generic 

```
^That was the kernel version, right?

---

### Post by Mikael_Niemel on 2016-06-18
Did you mean running

```
sudo update-initramfs -u -k 4.4.0-22-generic
```

as without -k it gave an error.

Anyways, it didn't work, it still gives the same error message when booting to Xen.

EDIT: And yeah, that's the kernel version.

---

### Post by MAFoElffen on 2016-06-18
Wow. I'm researching, as I'm running out of ideas of what could be going on.

I'm very curious if a search in dmesg (grep) of the sytems log sheds any light on what was going on when it hits that device not found error... <-- Talking about that actually gave me a few more ideas.

That gives me an idea. In the past dev cycles, when systemd was being integrated into debian, there is now a program call bootchart that creates a chart of what is going on and the timings of that in a chart form image file.
```

sudo apt-get install bootchart

```
The resultant charts (after a boot or boot attempt) can then be found in /var/log/bootchart... If you could post a chart of what is going on...

The other idea is to turn on systemd's journalctl journaling on as persistent, to see a failed boot, previous to what is the current boot.
```

sudo mkdir -p /var/log/journal
sudo vim /etc/systemd/journald.conf

```
Under the [Journal] section, set the Storage= option to "persistent" to enable persistent logging:
```


[Journal]
Storage=persistent

```
Then boot to Xen and after it fails, boot as normal. After logging in:
```

sudo journalctl -b -1

```
jopurnalctl displays the system log in a somewhat more human readable form that the system log. It may be easier to see what is going in in that form.

---

### Post by Mikael_Niemel on 2016-06-18
For some strange reason journalctl doesn't seem to record journals from Xen boot, but it does do it for normal Ubuntu boots. When I configured it, rebooted to Xen and then to Ubuntu I tried to run 

```
[COLOR=#000000][FONT=&quot]sudo journalctl -b -1[/FONT][/COLOR]
```

it said that such journal doesn't exist. I tried to boot again to Xen, but after that I only got journals from previous Ubuntu boot. 

Also, for some reason /var/log/bootcharts stays empty even though I installed it..

---

### Post by MAFoElffen on 2016-06-18
That is nuts. When I get home, I'll fire up one of my Xen servers and check some things out for you on mine... Give me a few hours.

---

### Post by MAFoElffen on 2016-06-19
Like I said, yours is acting weird, but we can work with weird.

My xen server is in Ubuntu 16.04 server. When I do 
```

journalctl -b

```
It displays my logs. Here's a summary of where your error is most likely getting hit...

Initial boot and parses the capabilities of the CPU and it's capabilities within Xen. Continues with the BIOS, memory and then other embedded controllers on the main board... (many lines) After hitting the video controller and attached display(s), then it quueries the I/O devices.

It first hits the cd/dvd device, then usb devices, then the HDD controller. (mine is Hard RAID) Right after hitting the HDD controller, it looks for attached drives (in my case logical RAID volumes). This is where your error occurs.

Since for some reason journalctl is not working on your machine ... The System Log is always there... But the system log in /var/log/syslog is timespan forever. So if failed attempt was today
```

cat /var/log/systemlog | grep "Jun 19" | grep "scsi host" -A 5 | more

```
...That would filter out just today's system log > devices under a scsi controller > a page at a time. 

When you find your HDD controller, add the controller number to the "scsi host" filter string. For example, if found on "scsi host 4" then that is your next string to filter on. Then add lines to display to the "-A" switch, to see what happened on that. For example:
```

cat /var/log/systemlog | grep "Jun 19" | grep "scsi host 4" -A 40 | more

```

---

### Post by Mikael_Niemel on 2016-06-19
I tried that, and there's still no trace of logs when I booted to Xen.

However, when I booted to the "emergency shell" to which it crashes, it looks like the PATA controller I'm using for the IDE OS disk is not visible at all in dmesg (it is in normal Ubuntu boot), and neither is the OS disk in /dev/disk/by-uuid. Maybe that could be the reason why it's not even able to save the logs?

---

### Post by MAFoElffen on 2016-06-19
So it is not even seeing that device from grub to do a boot of that OS. That makes more sense now.

From your previous description, I thought your Xen instance was in the same install volume as the normal Ubuntu that was booting successfully. So from the Ubuntu install that does boot, can that see your other disk?

---

### Post by Mikael_Niemel on 2016-06-19
Actually my Xen instance is in the same install volume as normal Ubuntu, there's just different boot options for whether or not to use Xen. 

So yes, the disk works fine during the normal Ubuntu boot.

EDIT: I'll get a S-ATA OS disk and see if it works then..

---

### Post by Mikael_Niemel on 2016-06-24
Okay, now that I got a S-ATA OS disk, Ubuntu boots just fine with Xen..

---

### Post by MAFoElffen on 2016-06-24
Great! 

Then if now working fine, please revisit this thread and mark it as solved:
 Upper right of page, select link "Thread Tools" > Select link "Marked Thread as Solved". This will help others to find answers to their similar issues.

---

### Post by Mikael_Niemel on 2016-06-24
Yeah, now it seems to work. But one more unrelated question, is there some way to specify Xen guests to be run on 32-bit only mode in the config file? I didn't find such option with quick googling.

---

### Post by MAFoElffen on 2016-06-25
Xen and KVM both use QEMU and Libvirt. So, since they both use the same QEMU and virstet, a lot of the file locations and their format is the same. The terminology for them defers between the 2. ....and Xen uses another toolset on top of wqemu and virsh.

The older version of Xen used the individual DomU conf files in /etc/xen. now xm was replaced with xl ... and honestly, I'm still getting used to that and trying to find the specific differences and how to work with it (specific behind the scene details).

Xen does PV (para-virtualized machine) and HVM (fully virtualized machine)... By the older xml format, there was:
```

...
  <os>
    <type arch='x86_64' machine='xenpv'>linux</type>
  </os>
...

```
where if you wanted to run only a 32bit guest, you changed that section to
```

...
  <os>
    <type arch='i686' machine='xenpv'>linux</type>
  </os>
...

```
/etc/xen/xl.conf iis the default conf file. It is in a xen formal, rather that the xml format that KVM uses.

in the xen for, it is "different." Xen is now shielded on where and how the DomU config files. I hear that the individual guests may now be stored in a db, instead of individually, as before... but not confirmed yet, and I'm still looking fr them on my own to see just how it is physically (real world, behind the scenes).

But if I start up a DomU domain and do 
```

sudo xl list -lV Domain_Name

```
it lists out the config for that domain in it's own kind of format.

But if I do 
```

sudo virsh edit Domain_Name

```
It starts an editor, to edit the config in XML format. xl also has an option to convert a config from xl format to xml // and xml to xl.

I'm thinking that if I edit a domain in xml... htne dump the converted xml to xl format... then I can see what it actually changes in the xl format.

The file /etc/xen/xl.conf is the default configuration file. So if we found what that change is, and applied that change to that file... 

But I can't try that until Monday. Almost out the door to a funeral and celebration of life for my belated brother-in-law.

---

### Post by Mikael_Niemel on 2016-06-26
My condolences. And no need to hurry, this is just a hobby project for me..


Anyways, I have been using /etc/xen/*.cfg config files to setup DomU, but I haven't found any options for that. Adding line 'arch = "i686"' didn't do anything. I haven't seen that xml format anywhere, either, and 

```
[COLOR=#000000][FONT=&quot]sudo xl list -lV Domain_Name
```

Outputs the data in JSON format, and there's no arch option visible.[/FONT][/COLOR]

---

