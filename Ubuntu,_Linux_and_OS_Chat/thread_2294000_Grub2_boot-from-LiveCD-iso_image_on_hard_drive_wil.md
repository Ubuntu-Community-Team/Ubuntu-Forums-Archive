---
title: "Grub2 boot-from-LiveCD-iso image on hard drive will not install."
date: 2015-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by oldefoxx on 2015-09-09
I learned a few things today, including some things that will NOT work.  So time to share.

First, I looked to see if you can boot from an iso image on the hard drive, rather than have to burn it to a CD or DVD disk.  Answer is, yes you can.  Several links then tell you how.

I tried one from [http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

They usually give pretty sound advice.  But this one didn't work for me.  Grub2 did not pick it up during the sudo update-grub process, so I looked elsewhere.

I'd completely forgotten about this one.  I posted it, and it gives other places to look as well:  [http://ubuntuforums.org/showthread.php?t=1406889](http://ubuntuforums.org/showthread.php?t=1406889)

This is the one I tried today.  It works, up to a point:  [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
The technique I used was the simplest given:  grml-rescueboot.  Grub2 picked it up without a hitch when I ran sudo update-grub.

I tried various things under the Try option.  There you are user ubuntu, with no password required.  If you mount a drive, it shows up under /media.ubuntu/sdXY, where X stands for the hard drive (a to whatever), and Y stands for the partition number (1 to whatever) **in the order created**.  You would think the designation for the partitions on the first internal drive would run sda1, sda2, sda3, swap.  Bur delete sda2 and create another partition there, and you would find you had sda1, sda5, sda3, swap.  sda4 got skipped over because that's what swap actually is.  Once used. a partition name is scrapped, so sda2 is gone.  To start over, you literally start over by replacing the partition table, which means eliminating the drive's contents.  Then you create and format new partitions.

Let's say you are going to reinstall Ubuntu 14.04.3 on sda1.  You can do it with or without a format (pick "Something else" in order to have choice in the matter).  Without format, your existing accounts and data are preserved.  With format, you lose everything on that partition.  If you spread your mount points among several partitions, those you designate to be formatted get scrubbed.  The others without format only get the specific folder, files, and subfolders deleted.  You must designate at least one partition to be root (/).  If the other partitions are not designated (left in a Do not use status), all the mount points will be on the root partition.

But, there can be problems if you replace one install of Linux with a different one later.  To prevent this, you want to delete all the folders on the root partition except /home.  /home has all the user accounts and their data, and you normally want to carry these forward.  To delete everything else, I have used "sudo rm -r /media/username/sda1/[!h]* sucessfully before, but when I booted from the iso image, it refused to permit me to do so here.  I didn't have the necessary permissions, even though I was super user via the sudo command.  I had to reboot from another partition, and do it from there.  Then I rebooted from the iso image and tried to do an install.

The install failed.  Now what I had was my iso image set up under /boot/grml/ as covered above, and was doing this from sda2, with the install happening on sda1.  I could not even get to where you pick your time zone, because the install process wanted to unmount the drive(s).  Whether you say Yes or No, the install will hang, because it still sees a drive mounted on that hard drive.  The drive it sees mounted is /isodevice.  Because /isodevice is on any partition on the sda drive, it fails because it cannot update the partition table **even though you have made no changes to the partitions themselves**.  The only way it will work, to do the install, is for /isodevice to be on an entirely different drive, one that is NOT part of the install that you are doing.  And for this to happen, you cannot have /boot/grml on the same **drive** (not just not the same partition) as where you are installing to.  Which looks like it spoils the grml-rescueboot method.  You might want the image on a USB drive,  or have it on a second internal drive, but it apparently has to be another drive.

I can't see the point of the LiveCD balking like it did.  I was making no changes to the drive or the partitions at that point, but it just would not let me pass.  In fact. I had to shut down the laptop to escape from the snare I was in.

If this is inherant in LiveCD, I don't think you can install Linux from an iso image on the same drive as to where you are installing to.  You could use a LiveCD disk in a DVD/CD drive for your install. run gparted to pre-configure your hard drive, download a newer or different Linux iso, and burn it to another DVD/CD disk, assuming that the LiveCD will let you vacate the DVD/CD drive and perform the burn process.  I'm not sure, as I haven't tried it.

I would like to see a LiveCD that can install on a single drive system when run from the iso image on that drive.

---

### Post by Bucky Ball on 2015-09-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

While we thank you for sharing, not a support request. :)

Good luck.

---

### Post by oldfred on 2015-09-09
I have same issue. 

I have created separate partitions for all my install ISO on each drive. But booting from sda, using ISO from sdb, still mounts /isodevice on sda, so I cannot install to sda from sdb. 

If you file a bug report I will add my 2 cents. They often do not respond to only one user's complaint assuming it is user only issue.

It used to be that you could select an option to unmount install ISO to install to same device. But that does not work now.

---

### Post by sudodus on 2015-09-09
Interesting issue :-)

Have you tried with the boot option **toram**? It should make the system free from the original drive. It works for me in similar cases, but I haven't tested this particular case.

---

### Post by oldefoxx on 2015-10-02
I haven't heard of toram before. but I recognized it as a contraction of "to RAM", and RAM is the electronic memory in a computer that is aslo known as Random Access Memory.

Let's see:  Can't boot from an iso image on a hard drive in any partition because the LiveCD process will shut down all the partitions as part of the  partition table update process, even though the partitions have not been changed.  Now another user says he tried to install from a booted image on a second (USB drive) iso image and he had the same problem. so maybe the Live CD is a bit too zealous, possably unmounting all the drives.  Now another suggests installing the LiveCD to RAM as a possible way around the problem.  But if the LiveCD is
unmounting drives as part of its routine, it's still going to shut down the source drive, unless that drive is a DVD/CD drive.  No, I don't think that toram is going to help.  That's just the target.  It's forcefully unmounting the source from the bit of evidence uncovered to date,  Which is wrong.  It should not be going to that extreme.

I'm not going to open a bug report on this though.  I've tried to do bug reports before, and they want you to carry the load of identifying where the problem is. I'm not expert enough to do all that.  I will write a post, start a thread, but leave it to someone else to generate the bug reports..

---

### Post by oldfred on 2015-10-02
I found this bug & the work around of just unmounting the ISO works.

 Unable to umount isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
sudo umount -l -r -f /isodevice

---

### Post by Bashing-om on 2015-10-02
et all;

I often boot .iso files from hard drive . What I have found on my system arrangement is that I must boot the hard drive that also contains the .iso file I desire to boot. Grub will always see that booting hard drive as hd0 I think is the crux of the matter.

[INDENT][INDENT]care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by oldefoxx on 2015-10-02
> **oldfred said:**
> I found this bug & the work around of just unmounting the ISO works.

 Unable to umount isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)
sudo umount -l -r -f /isodevice

It's not clear to me:  You are using a terminal window to issue this command, so how are you doing to get a terminal window opened?  Going to Try Ubuntu first?  Open a Terminal under Dash?  Typing "sudo -i"?  Then clicking on the "install Ubuntu" icon on the Desktop?  Then waiting until some point in the install process to enter the umount command in that terminal window?  I'm just gurssing here, because I'm not ready to do another install effort right now.  And other prople need to know how it is done as well.  What's the whole story?

Not the whole story in the way of all the hardware changes that are taking place that are complicating the install process to the extreme.  Now when I attempt an install process, I have a CD with Boot Repair on it to make the PC bootable if it fails to boot up for any reason.  That's something they should tell everybody to do, because it gives you a second chance to get it right.  And I always choose Something else when it comes to how the install should go down.  Anything else, and you are likely to lose whatever you have on that PC already.

---

### Post by oldfred on 2015-10-02
When I directly boot ISO, I do not get a choice on install or live mode, just live mode. Which I prefer anyway.

And I was running the mount command to see where the issue was and for whatever reason booting in UEFI mode from sda, but ISO on sdb mounted a partition on sda as /isodevice. But unmounting it and clicking on install then worked.

---

### Post by oldefoxx on 2015-11-05
> **oldefoxx said:**
> It's not clear to me:  You are using a terminal window to issue this command, so how are you doing to get a terminal window opened?  Going to Try Ubuntu first?  Open a Terminal under Dash?  Typing "sudo -i"?  Then clicking on the "install Ubuntu" icon on the Desktop?  Then waiting until some point in the install process to enter the umount command in that terminal window?  I'm just gurssing here, because I'm not ready to do another install effort right now.  And other prople need to know how it is done as well.  What's the whole story?

Not the whole story in the way of all the hardware changes that are taking place that are complicating the install process to the extreme.  Now when I attempt an install process, I have a CD with Boot Repair on it to make the PC bootable if it fails to boot up for any reason.  That's something they should tell everybody to do, because it gives you a second chance to get it right.  And I always choose Something else when it comes to how the install should go down.  Anything else, and you are likely to lose whatever you have on that PC already.

Yes. under install, you are limited to choices of how to proceed.  So you do the Try method to do everything else.  Click on any drives that you want opened first.  Type a few letters in "terminal", and it comes up.  Type "sudo -i" and there you are. the drives are mounted under /media/ubuntu/, which does not exist until the first drive is mounted by the system.  Do ehat you need to and exit.  Either right click the drive and close it, or go right into install which will want to close it.them for you.  Then on with a normal install.  But you can play games, go online, or do other things while waiting, which you could not do if you went right into install at the beginning.

---

