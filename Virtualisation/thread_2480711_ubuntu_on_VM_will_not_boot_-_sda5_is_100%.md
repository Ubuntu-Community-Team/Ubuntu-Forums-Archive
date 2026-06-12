---
title: "ubuntu on VM will not boot - sda5 is 100%"
date: 2022-11-07
forum: Virtualisation
---

### Post by jumbojake on 2022-11-07
I woke up this morning to find my VM running ubuntu 22.04.1 LTS   was frozen ... on reboot it failed with a load of errors.

after some digging around I see the sda5 is 100%    ... I wonder if it filled up overnight.  I have tried safemode and also an install disk ... I can see files and directories,  but I cannot get write access to remove stuff.

I've tried various clean up scripts of old upgrade package files, but all fail with permission error   (yes, I am using sudo).

How can I recover...without loosing my data ?

Is there a way to gain wrote access to clear the partition ?
Is there a way to add a new partition to give space and re-install without loosing data ?

---

### Post by TheFu on 2022-11-07
So, you can connect a "Live Boot" aka "Try Ubuntu" ISO to the VM and boot that.  From there, you can access the existing storage inside the VM.  Depending on what it shows, you can delete from files ( be careful deleting OS files) or you can setup the log file management system to limit the allowed size of log files.  that's in the /etc/systemd/journald.conf  (which will be in a temporary mount location, not the Try Ubuntu  /etc/systemd/journald.conf ) version of the file.

I need to re-read what you've asked, but we need some data about the host and VM.

Which hypervisor is being used?  There are about 10 popular answers, each needs someone with different knowledge to help.

Is the hostOS storage full or is the VM storage full?  

The VM storage, what type of back end storage is being used. Is it .vdi, .vmdk, .qcow2, a raw file, or some more advanced storage like a logical volume provided directly to the VM?

Was a sparse file used? [https://wiki.archlinux.org/title/sparse_file](https://wiki.archlinux.org/title/sparse_file)  qcow2 and vdi VM storage often use sparse files. With really fast storage (i.e. any SSD based physical storage), there's little downside to using sparse files, but for spinning storage (i.e. HDDs), sparse files can cause a huge performance impact when compared to fully pre-allocated VM storage.  sparse files are constantly growing, which has overhead for the hypervisor.  Just something to consider.

Anyway, we need some facts to help.  When it comes to storage facts, we generally need to see the available devices, how they are mounted, how full they are from both the host and inside the VM standpoint.  If advanced volume management is being used, we'll need some extra information too.  For now, run these 2 commands from the host system and after you boot into a "try ubuntu" environment and mount all the VM storage to temporary locations.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```
Wrap the exact commands and output in forum code-tags, like I've done.

BTW, this post really belongs in the "Virtualization" sub-forum.  Hopefully a moderator will move it. You and I cannot.

---

### Post by ajgreeny on 2022-11-07
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

However, to be able to give you more help, as mentioned by TheFu, we really do need to know your hypervisor; Virtualbox, KVM/QEMU, VMware, etc etc.  Without that we are all guessing and unable to help you.

---

### Post by jumbojake on 2022-11-08
Thanks for your reply.

i am using a Windows10 Laptop, running wmware workstation, with ubuntu 22.04.1 LTS installed... the VM storage is vmdk I think.   The setup has worked well for a few years ... but since the last upgrade to the latest Ubuntu, it's been freezing up ... and on power cycles slowly seeing more errors on login.

In it's current faulty state it does not boot.  I can access through a terminal with keyboard access, via 'ALT F2' or also by using the install disk in 'try me' mode.... but in both scenarios, I cannot move data onto my hosts clipboard so cannot extract via copy/paste.

A photo of the screen output is the best I can do.. this is taken via the install disk 'try me' , from where I can gain access to the existing partition.... but I cannot see how to add a photo to this thread

MY hope is to clear out enough space to allow a re-install without loosing all of my data.

I guess two options
- clear out space on sda5 to allow re-install to happen
- allocate more host space to a new partiton and install from there

---

### Post by jumbojake on 2022-11-08
ok, I have found a way to clean data from the partition and now I have over 5G free space in sda5.

I have tried to re-install ... it identifies it can see a mount for sda5, and asks me if I want the installer unmount it..... seems like some reverse logic in the question.. but I chose to unmount it.

However, when I select 'something else' it moved me on where I can see the partition, but the option to 'install' is greyed out.

Do I need to make more space available, or am I doing something wrong ?

---

### Post by TheFu on 2022-11-08
> **jumbojake said:**
> 
i am using a Windows10 Laptop, running wmware workstation, with ubuntu 22.04.1 LTS installed... the VM storage is vmdk I think.  

Sorry, I cannot help with that setup - and you probably don't want my guesses even if all VM hypervisors are basically the same from a high-level view. ;)

The output from the  2 commands requested to be run above haven't been provided. Hard to help when requested data isn't provided.

BTW, I've never touched Win10/11 and haven't used VMware-Workstation since the late 1990s.  Allowing the host storage to become full is bad for every OS. It prevents doing some relatively easy VM-storage expansion tools from being used.  I don't know what tools for storage management VMware provides.  I do know exactly how to do it for any VM based on qemu, however, which can use raw images, qcow, qcow2, LVM2 LVs or 10 other storage backends.  Increasing available storage to a VM has many options, but those depend on how the storage is layed out.  I suspect that if there's an sda5, then LVM2 was selected, which offers all sorts of ways out of the situation .... but need to see the requested data as a starting point to confirm LVM2 is being used first.

---

### Post by jumbojake on 2022-11-08
Hi, sorry, a misunderstanding, the host is WIn10 and there is no capacity issue there... the whole setup has been stable for a few years.

The issue was on the VM, running Ubuntu .. this is a pure ubuntu issue  (not sure why it was moved to VM as it shouldn't matter).  

I am trying to re-install ubuntu, but stuck.

I can provide the output you asked for, but I cannot find a way to load a screenshot into this forum ... I cannot copy/paste from a terminal while in this fault condition.... only a screenshot.

However, I have progressed, I have managed to reduce the size of sda5 and now have more than 5G available.... I have attempted the re-install using the 'something else' option .. but stuck at the point with this error

"No EFI partition was found" ... and "Please go back and add an EFI system partition, or continue at your own risk"

But I didn't think I needed this...

---

### Post by TheFu on 2022-11-08
You can save the output to a file from any Linux command.  Please don't ever post screenshots of text.

```
$ lsblkt | tee /tmp/log.lsb-out

$ less  /tmp/log.lsb-out
NAME                              SIZE TYPE FSTYPE      MOUNTPOINT
sda                             465.8G disk             
&#9492;&#9472;sda1                          465.8G part LVM2_member 
  &#9492;&#9472;vg--hadar-lv--backups       465.7G lvm  ext4        /Backups
sdb                               477G disk             
&#9500;&#9472;sdb1                            731M part ext2        /boot
&#9500;&#9472;sdb2                              1K part             
&#9492;&#9472;sdb5                          476.2G part LVM2_member 
  &#9500;&#9472;hadar--vg-root               32.3G lvm  ext4        /
  &#9500;&#9472;hadar--vg-swap_1              4.3G lvm  swap        [SWAP]
  &#9500;&#9472;hadar--vg-libvirt--lv         175G lvm  ext4        /var/lib/libvirt
  &#9500;&#9472;hadar--vg-lv--vpn09--2004     7.5G lvm              
  &#9500;&#9472;hadar--vg-lv--blog44--1804   16.2G lvm              
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm  ext4        /var/lib/lxd
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm              
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm              
  &#9500;&#9472;hadar--vg-lv--zcs46            25G lvm              
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm              
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm              
  &#9492;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm              
    &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm              

```
This is from my hostOS. Most of those entries are LVM2 LVs, provided directly as block devices to the VMs.  I ran out of space for "regulus" - that's a virtual machine, so I added another 10G disk.  Inside regulus, the storage looks like this:
```
$ lsblkt 
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     19G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     19G lvm  ext4        /

```
Note how / is using 2 different storage devices?  That's part of the power of LVM.  When I look at the mounts:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   13G  5.3G  71% /
/dev/mapper/vgubuntu--mate-home ext4   12G   11G  395M  97% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
romulus:/raid/media             nfs4  1.8T  1.7T  5.7G 100% /R

```
You can see that / is 19G, but that size comes from LVs on both vdb1 and vda5.  LVM allows merging completely separate disks, though in reality, these are using the same physical storage on the hostOS.  The modifications are possible without even rebooting the guest machine, but only if LVM is being used.  I did have to force the guest VM to see the new storage was added by running fdisk, but I needed to add a new partition and mark it for LVM use anyways. Then I extended the Volume Group, VG, into the new storage and simply increased the existing LV "root" and the ext4 file system with 1 lvextend command. Easy-peasey.

Clear a mud?

The good news is that LVM is LVM is LVM, regardless of the Linux OS.  Any tutorial or guide from 2005 or later is just as good as another - redhat, debian, ubuntu, SuSE, whatever ... doesn't matter.
The bad news is that there isn't any GUI to manage LVM.  Since LVM is mainly used by IT professional admins and Linux servers don't have GUIs anyway, that isn't a problem. What's the point of having a GUI that can't be used on 99% of the systems?  It is a waste of effort.

---

### Post by jumbojake on 2022-11-08
understand that and tried it already, but have no way of extracting that file from the system in its current state.  If I can attach a photo, I can share the data you asked for.

When I run that command, I do not see any LVM ... I see an sda defined as 'disk', and under that, sda1, sda2 and sda5 all defined as 'part'

any thoughts about how I progress with the unexpected 'no EFI partition'  error at install ?

---

### Post by TheFu on 2022-11-08
> **jumbojake said:**
> understand that and tried it already, but have no way of extracting that file from the system in its current state.

You can't share the VM-host file system with the guest, then just drag and drop the file to the host OS using any file manage you like?  I'm fairly certain VMware could do that in the 1990s.  VirtualBox supports accessing the hostOS storage through the vboxsf driver. I think it is part of the guest additions, which have that ugly, non-F/LOSS, software license from Oracle, but since you've already decided to VMware Workstation, the guest additions probably make this all easy.   Ah - guest additions require a reboot and that would reset the try ubuntu environment.  chicken-egg problem.

Ok ... going with the Unix solution ... You could always use sftp to transfer the file to another system. On Linux, the target system needs to have ssh-server installed and the client needs ssh-client.  The metapackage "ssh" will install both, which is what I do on all my systems and sometimes into the "try ubuntu" environment.  Once that is installed, any file manager should be able to use the sftp:// URL to connect to the other system.  On a well-managed network, use the DNS name. On other networks, use the IP address.

If you are stuck using Windows, I can make some guesses.  Didn't MSFT finally add ssh support a few years ago (20+ yrs after the rest of the world switched)?  Probably easier to run the ssh-server on the VM then use something like WinSCP to connect and drag-n-drop the text files back to Windows for posting here.  Filezilla also supports sftp, I understand. Those are the GUI programs.  I'd be surprised if Win10+ ssh didn't include an sftp client. PuTTY has included psftp.exe since the 1990s. That's an sftp client which can push or pull files.

On Android, I use "ghost commander" for sftp access.  There must be 50+ other android apps with sftp capabilities.

Plenty of ways to get files off a Linux system.  Heck, you could run a 1-line webserver .... in the directory with the text output file, then using any client machine with a web browser to pull it off.  Here's a few of those:
```
Python 2.x
  $ python -m SimpleHTTPServer 8000

Python 3.x
  $ python -m http.server 8000

Ruby
   $ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 8000,
                        :DocumentRoot => Dir.pwd).start'

Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

Perl
   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'

Plack (Perl)
   $ cpan Plack   # install dependency
   $ plackup -MPlack::App::Directory -e
               'Plack::App::Directory->new(root=>".");' -p 8000

Mojolicious (Perl)
   $ cpan Mojolicious::Lite   # install dependency
   $ perl -MMojolicious::Lite -MCwd -e 'app->static->paths->[0]=getcwd;
                                    app->start' daemon -l http://*:8000

http-server (Node.js)
   $ npm install -g http-server   # install dependency
   $ http-server -p 8000

busybox httpd
   $ busybox httpd -f -p 8000 

```    

Pick 1.  I'd probably use the python3 one. quick. easy. ZERO security. After the 10 seconds to run it and pull the file, use <cntl>-c to close it.

If you ever need to do this have have hundreds of concurrent clients, use the perl Plack version. That can spawn hundreds of tiny perl servers by changing 1 config option.  Mojolicious would probably make a prettier web listing, but the dependencies are very numerous.  that cpan Mojolicious::Lite is very short, but probably would install at least 50 if not 150 other perl modules.  Yep, definitely use the python3 command. Definitely. ;)

Having the ability to create a tiny, web server that serves all the files in the current directory can be handy, but much better to use sftp with good network encryption and authentication.

---

### Post by jumbojake on 2022-11-08
I'm not sure how we have gone down this track, but as before I cannot share files or copy from clipboard in this current state...   I agree when things are working it is possible, and it was until the failure happened.

Now, in a console, I only have read access to the filesystem.  If I boot from the install disc I can delete files and create them, but cannot extract anything from it... but that really isn't the issue being reported here.... again, the only way to show something would be a screendump, but again we're a bit off track on the problem

Please can someone explain why I cannot re-install ubuntu, what I am doing wrong  ... it seems to be stuck at this error wanting an 'EFI partition' .. but I don't think I need one.  I have read this could be because the ISO image is being interpreted by the installer as EFI, but I have just built a new ubuntu VM using the same and didn't have any problems, so think the ISO and how VM presents it is fine.

---

### Post by TheFu on 2022-11-08
My guess is that the VM is setup to boot in EFI mode, but the installation is setup for Legacy BIOS booting?  Could that be it?
Or perhaps a partition for EFI booting was wiped through some mistake made previously?  We've seen that and worse in these forums. Heck, I've done worse to myself, by accident.

The reason I was suggesting installing ssh-server was so you could use rsync to get all the data you don't want to lose off, wipe the VMDK and start over from scratch.  OTOH, if you want to try to fix the existing setup, possibly with a  few commands, getting the df, lsblk and lvm information off would be very helpful.  Exact facts are helpful, without interpretations. 
I can't copy/paste lines from an image, but I can from text. That can make helpful replies compared to nebulous, big picture, posts like I've given so far.

---

### Post by MAFoElffen on 2022-11-08
LOL. There are so many ways to approach this, that it is crazy. The correct thing would be to copy the VM Disk right now, before trying to 'Fix" it...

The most logical direction after that is to grow/expand the vdmk disk. There are 2 ways to do this. Both ways, you need to make sure the VM Guest is shut down. Then delte all the snap-shots. See where this is starting to get scary?

Easiest to grow, is if your version of VMware Workstation is 7 or newer: (if older, tell me and I'll post the cli commands for this)

[LIST]
[*]Select the virtual machine from the Inventory.
[*]Click Edit Virtual Machine Settings.
[*]Click Hard Disk.
[*]Click Utilities > Expand, enter the new size, then click Expand.
[/LIST]
 Complete the steps in Increasing the size of a disk partition, so that the guest operating system is aware of the change in disk size. Which means, mount an Ubuntu LiveCD ISO and use GPARTED to grow sda5... 

Mount the virtual disk. If it had LVM, grow the pieces of the disk manager containers (PV, VG, through LV). Then grow the filesystem.

Of course, you could just boot the VM Guest from an Ubuntu LiveCD, mount the VM Disk, chroot into it and make space, before you do that... But you need a challenge right?

---

### Post by jumbojake on 2022-11-09
Thanks for your reply.... I think I have overcome the space issue, I found a way to delete stuff, using the 'try me' feature of the install disk and mounting the existing partition.... as a result the sda5 now has over 7G free.... so that issue is resolved.

But Ubuntu is still broken, will not boot  and rather than try to fix it, I just want to do a fresh re-install.

I have the ISO image, and chosen the 'somehting else' ... but stuck as it is asking for EFI partition ... which I do not understand.  

In safemode, I have checked '[COLOR=#232629][FONT=ui-monospace]/sys/firmware[/FONT][/COLOR]'  but there is no EFI present, so assume it is BIOS.   

I have also created a new ubuntu VM, using the same ISO mounted in the same way and that also uses BIOS.

So I have no idea why the re-install script is asking for an EFI partition.

---

### Post by TheFu on 2022-11-09
Oldfred posts the required partitions for EFI booting in these forums a bunch.  [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)  UEFI is what Linux usually calls it.   Below is what I have for a UEFI booting desktop with my custom LVM disk layout:
My notes on this say to setup these:
```

# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB
 swap   swap            LV/SWAP         swap    4.1GB

Types (
 BIOS = ef02
 EFI = ef00
 LINUX = 8300
 SWAP = 8200
 LVM = 8e00
)
Here's an actual booted physical system: 

nvme0n1                      465.8G disk                    
&#9500;&#9472;nvme0n1p1                     50M part vfat    EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                    600M part ext4               /boot
&#9492;&#9472;nvme0n1p3                    465G part LVM2_me            
  &#9500;&#9472;vg00-swap                  4.1G lvm  swap               [SWAP]
  &#9500;&#9472;vg00-root--00               35G lvm  ext4               /
  &#9500;&#9472;vg00-var                    35G lvm  ext4               /var
  &#9500;&#9472;vg00-home                   26G lvm  ext4    home       /home

```
That system is booting using UEFI:
```
 [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
UEFI

```

But, IMHO, using EFI/UEFI to boot VMs is a waste.  In the VM settings for all the hypervisors I've used in the last 5 yrs, we can choose "Legacy/BIOS" or "UEFI" for booting.  Ubuntu ISOs all support either method, but the system's BIOS for physical hardware decides which should be used.  For VMs, we can choose either by setting the virtual motherboard to the mode we want.
Some other reading on this topic:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick/uefi](https://help.ubuntu.com/community/Installation/FromUSBStick/uefi)
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)
[https://askubuntu.com/questions/927924/how-to-install-ubuntu-in-uefi-mode](https://askubuntu.com/questions/927924/how-to-install-ubuntu-in-uefi-mode)

When we choose "Do something Else", we say that we understand what is needed and will setup everything.  If we choose "Use entire disk", then the installer will setup whatever partitions are necessary, though not in a great way (IMHO).  Similarly, if we choose the checkboxes for either LVM or Encryption during the custom setup, we get a less than optimal disk layer .... but those automatic methods will definitely support either UEFI or Legacy booting, based on the VM settings.  Heck, it's a VM.  Create 1 of each type, look at the resulting partitions, types, file systems, etc, then you can go back and ensure your custom setup has those (at a minimum) and resize to match your needs.

The commands I use during install to get the partitioning the way I like, (in a different console login) are:
```

  export DEV=/dev/sda
  export VG_NAME=vg00
  sgdisk --clear $DEV   # create fresh GPT partition table on the device
  
  sgdisk --new=1:0:+1M   --typecode=0:ef02 --change-name=0:GRUB   $DEV  # BIOS Boot Partition (legacy)
  sgdisk --new=2:0:+50M  --typecode=0:ef00 --change-name=0:EFI-SP $DEV  # for /boot/efi
  sgdisk --new=3:0:+600M --typecode=0:8300 --change-name=0:boot   $DEV  # for /boot
  sgdisk --largest-new=4 --typecode=0:8e00 --change-name=0:LVM    $DEV  # for the LVM PV/VG and multiple LVs

  sgdisk --typecode=1:ef02 --typecode=2:ef00 --typecode=3:8300 --typecode=4:8e00 $DEV
  sgdisk --change-name=1:GRUB --change-name=2:EFI-SP --change-name=3:boot \ 
         --change-name=4:LVM $DEV
  sgdisk --hybrid 1:2:3:4 $DEV
  sgdisk --print $DEV

```
Clearly, change the DEV value for your needs.  Next, creating the LVM stuff:
```
  pvcreate ${DEV}4
  vgcreate {VG_NAME} {DEV}4
  lvcreate -L 4.1G -n swap ${VG_NAME}
  lvcreate -L 35G -n root ${VG_NAME}
  lvcreate -L 2G  -n var ${VG_NAME}
  lvcreate -L 2G  -n tmp ${VG_NAME}
  lvcreate -L 10G -n home ${VG_NAME}
   lvscan   # get the OS/installer to see the new stuff

```
Don't worry too much that the sizes inside the LVs are smaller than what it posted higher in this post.  I use the same script for servers and desktops.  Servers need much, much, much less storage if they are just doing processing, but don't hold any data.  For example, my email gateway uses less than 10G total storage for everything.  It is the primary spam email blocker for all inbound stuff. If the mail doesn't get refused, then it is forwarded to a LAN-only communications server that has all the fancy capabilities and much more storage.

And finally, formatting the partitions and adding LABELs:
```
  mkfs -t ext2 ${DEV}1  # not sure what this is about.
  mkfs -t vfat ${DEV}2  # /boot/efi
  mkfs -t ext2 ${DEV}3  # /boot
  mkswap  /dev/${VG_NAME}/swap  # swap (this was activated by the installer)
  mkfs -t ext4 /dev/${VG_NAME}/root  # /
  e2label /dev/${VG_NAME}/root root

  mkfs -t ext4 /dev/${VG_NAME}/home  # /home
  e2label /dev/${VG_NAME}/home home

  mkfs -t ext4 /dev/${VG_NAME}/var  # /var
  e2label /dev/${VG_NAME}/var  var

  mkfs -t ext4 /dev/${VG_NAME}/tmp  # /tmp
  e2label /dev/${VG_NAME}/tmp  tmp

```
In one of the installers, ext2 cannot be used for /boot for some reason. If that happens, use ext4.  Go and finish the installation using the "Do Something Else" option and assign the partitions/LVs to the mount locations.

I don't recall if we can set mount options during the install or have to wait until the first boot into the system.  Force some mount options to improve system security:
  /home nodev,nosuid
  /tmp  nodev,nosuid,noexec
  /var  nodev,nosuid,noexec
Some new releases  my choke on the noexec for /var/ and/or /tmp/ due to the crappy snap packaging.  Can always use the "Try Ubuntu" environment to remove the problem option.

Everyone has a preferred setup.  I like to allocate only the storage I'll need, until I actually need it, then add what I think will be needed for the next 3 months.  With LVM, resizing an LV larger is 5 seconds, provided the VG has unused space.  The system doesn't need to be powered off, rebooted, just run 1 lvextend command and 2 seconds later, 1G - 5TB will be added.  LVM makes adding storage to the locations we need extremely fast.  Plus, with LVM, we don't have to modify the /etc/fstab or worry about UUIDs for mounting.

Anyway, hope this all helps.

---

### Post by tea for one on 2022-11-09
> **jumbojake said:**
> I have the ISO image, and chosen the 'somehting else' ... but stuck as it is asking for EFI partition ... which I do not understand. 
As long as you are in Legacy mode, you can ignore the message and continue.
> **jumbojake said:**
> I have also created a new ubuntu VM, using the same ISO mounted in the same way and that also uses BIOS
You are up and running OK now and the problem has been solved?
> **jumbojake said:**
> So I have no idea why the re-install script is asking for an EFI partition.
The Ubuntu installer has been looking for an EFI partition for some time now and it causes few problems when booted on UEFI compatible hardware.
it is a bit irritating to see a warning when a user has deliberately booted in Legacy mode but the installation will complete.

Using KVM/Qemu and Virtual Machine Manager, I created an Ubuntu 22.04 VM.
I chose the "something else" option and ignored the warnings about EFI and Bios boot.
Installation was completed and the VM booted.
Here is the terminal output:-
```
testvm@testvm:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
[COLOR="#0000FF"]Legacy boot on HDD[/COLOR]

testvm@testvm:~$ sudo parted -l
[sudo] password for testvm: 
Model: Virtio Block Device (virtblk)
Disk /dev/vda: 26.8GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  26.8GB  26.8GB  ext4
testvm@testvm:~$ 
```

---

### Post by jumbojake on 2022-11-12
Problem resolved, painful, but got there.

I ended up doing the following
- boot from install ISO, using the 'try me', this allow me to mound the old partition, and gave write access to delete old data, created 15G space
- re-purpose new space for a new partition and install onto that, using 'side by side' install option.
- mount the old partition, which gave full access and a way to move data off the VM

- install brand new VM, SCP'd data from old to new
- re-build new VM to mimic the old

Not elegant, but got there... probably the best result following many failed options

---

