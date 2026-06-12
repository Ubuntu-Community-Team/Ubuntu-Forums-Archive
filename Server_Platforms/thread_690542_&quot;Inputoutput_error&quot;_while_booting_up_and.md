---
title: "&quot;Input/output error&quot; while booting up and &quot;Cannot execute /bin/bash:&quot; on login"
date: 2008-02-07
forum: Server Platforms
---

### Post by trymbill on 2008-02-07
Hi every body!

I've got a BIG problem! :- /  My Ubuntu, 7.10, just displays the error "Input/Output error" after every thing it tries to start up while booting up and when I try to log-in I just get the error "Cannot execute /bin/bash: Permission denied".

So nothing starts, and I can't login, and I've got no clue what's going on!

Apache2 was acting wierd so I checked my server to see wether I could find out what was wrong.  I tried to restart apache2 but it came back with an "fail" error and said that "/ was read-only" ...

... so I tried restarting the server, via SSH, and nothing happened for a while so when I went home, and tried to manually start it up this happened.

Could some one please let me know what's going on with my Ubuntu Server? :S

---

### Post by k_grdn on 2008-02-07
Hi,

Sounds like a corrupted file system possibly bad blocks, boot single user and run fsck on the volume.

Regards,

K_grdn

---

### Post by trymbill on 2008-02-07
> **k_grdn said:**
> Hi,

Sounds like a corrupted file system possibly bad blocks, boot single user and run fsck on the volume.

Regards,

K_grdn

What do you mean by "Boot single user" ?

---

### Post by k_grdn on 2008-02-07
Hi,

Boot your Linux box and start hitting 'Esc' until you get the GRUB menu. The GRUB menu passes by quickly. 

Select a boot image from the menu then press 'e' to edit.

Select the Kernel line and press 'e' to edit. It should look something like this:

   kernel /vmlinuz-`uname -r` root=/dev/mapper/Ubuntu-root ro quiet splash

Edit the line to get rid of quiet and splash and add 'single':

   kernel /vmlinuz-`uname -r` root=/dev/mapper/Ubuntu-root ro single

Then press enter. You will be returned to the menu.

Press 'b' to boot with these new settings. 
 
When prompted enter root password, 

# fdisk -l

/dev/hda10           2688        3052     2931831   83  Linux

# fsck -y /dev/hda10 (replace your device path)

This will check and repair and bad blocks on the disk, then reboot or init 2.

If you don't have root pass edit the kernel to:

kernel /vmlinuz-`uname -r` root=/dev/mapper/Ubuntu-root rw init=/bin/bash

Regards,

k_grdn

---

### Post by trymbill on 2008-02-07
Hey, thanks for the help!

I tried what you said but I didn't really get any "good" response back.

I've got Ubuntu installed on /dev/sdb and there are 3 different partitions under that hard drive.  sdb1, sdb2 and sdb5.  When I tried to fsck sdb2, which is the partition where ext3 is on and I believe that Ubuntu is mainly installed on there, it said "This device is mounted, are you sure?" and I said "Yes" and then it just came with some thing like "Free blocks" and stuff like that ... didn't really seem like it was doing anything.

sdb1 and sdb5 just returned errors or permission denied, so that didn't work either :- /

I think I did everything like you told me to ... at least I could run the commands and I could see the disks when I did fdisk -l but it looks like fsck doesn't really do anything.

Not sure what to do :(

---

### Post by k_grdn on 2008-02-07
Hi,

You need to umount the volume to perform a true fsck

# umount /dev/sda5

Then run fsck.

Check /etc/fstab find out the mount points of your devices.

Regards,

k_grdn

---

### Post by k_grdn on 2008-02-07
May be a good time to backup some data if you ain't already! 

:)

---

### Post by trymbill on 2008-02-07
Thank you for the help k_grdn :)

I tried umount'ing /dev/sdb1 (which turns out to be the Linux partition of my hard drive), did that with umount -fv /dev/sdb1 and it said that /dev/sdb1 was now umounted.  Tried fsck, but no luck ... it still just says that my partition is OK and that nothing is wrong.  It didn't complain about the partition beeing mounted, but just returned the same result none the less.

I looked at my /etc/fstab and I could see that both /dev/sdb1 and /dev/sdb5 are mentioned but they don't look like anything you've been pointing out.  Sdb1 and sdb5 are just commented out, and below each one there is this really long "UUID" number.  Is that normal? :-)

Do you know of any thing else I can do?

---

### Post by k_grdn on 2008-02-07
Hi,

Try mounting the volumes, then check /etc/mtab to see if they are mounted rw, or try creating a file on the volume.

Have you rebooted?

k_grdn

---

### Post by trymbill on 2008-02-07
Hi again,

I tried mounting /dev/sdb1 to ./ and I looked into /etc/mtab.  /dev/sdb1 was there and it was mounted 'rw' and it also said "error=remount-ro" or something like that.

I also tried creating a file on the volume, just on ./, and it said "Error: Can not create file, read-only system" :S  I thought about trying to mount /dev/sdb2 and /dev/sdb5 but I'm not sure where they are suppose to be mounted or if they are suppose to be mounted at all ...

I've tried rebooting a couple of times.  Sometimes it doesn't reboot, it just hangs on some error that it repeats over and over again.  Sometimes, when I reboot, it just goes to "Ubuntu Login:" and I can't do anything.  Pressing ctrl+alt+del forces it into rebooting in the end though.

I'm totally lost here :)  Please, let me know if you find anything else I could use :P

---

### Post by trymbill on 2008-02-08
This is just a bump :-)

---

