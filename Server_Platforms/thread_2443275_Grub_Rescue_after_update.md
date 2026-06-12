---
title: "Grub Rescue after update"
date: 2020-05-13
forum: Server Platforms
---

### Post by emcnish on 2020-05-13
I have a HP Proliant MicroServer Gen 8 running 18.04 LTS Server.

This is the second time this has happened in the last two months.  I 'sudo apt upgrade', reboot, and end up with:
> Attempting Boot From CD-ROMAttempting Boot From Hard Drive (C:)
error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue> 

'ls' at the > prompt yields:
> (hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos2) (hd1,msdos1) (hd2) (hd2,msdos2) (hd2,msdos1) (hd3) (hd3,msdos2) (hd3,msdos1) (md/1) (md/0)


Yes, I boot into a software RAID.

The often recommended, 'set prefix=', 'insmod normal', etc... results in the " file '/boot/grub/i386-pc/normal.mod' not found." error.

I found a normal.dot in "/boot/grub.**bak**/i388-pc/" but setting the prefix to the grub.bak folder and running insmod results in "invalid arch-independent ELF magic"

I attempted:
> sudo add-apt-repository -y ppa:yannubuntu/boot-repair
sudo apt-get update
 sudo apt-get install -y boot-repair && boot-repair

This worked last time, and I was able to successfully reboot multiple times.  This time however, during the 'sudo chroot "/mnt/boot-sav/md1" dpkg --configure -a' and 'sudo chroot "/mnt/boot-sav/md1" apt-get install -fy' steps, I received:
> Errors were encountered while processing:
  linux-image-4.15.0-72-generic
  linux-image-4.15.0.91-generic

Here's a photo of as much of the Terminal I could capture:
[ATTACH=CONFIG]285849[/ATTACH]

I then attempted to rerun boot-repair and there is now no option to repair, only 'Create a Bootinfo summary':
[http://paste.ubuntu.com/p/d4nP7VJYJp/](http://paste.ubuntu.com/p/d4nP7VJYJp/)

Suggestions?

[B]EDIT 1
---------------------------------
[/B]It dawned on me after stepping away from the problem, my md1 array was not active.
I stopped both arrays, and assembled them again with the --force option
> sudo mdadm --stop /dev/md[01]
sudo mdadm --assemble --scan --force
I was then able to mount md1

[B]EDIT 2
[/B][B]---------------------------------
[/B]I stumbled across [https://askubuntu.com/questions/1040974/ubuntu-server-18-04-apt-get-fails](https://askubuntu.com/questions/1040974/ubuntu-server-18-04-apt-get-fails), and they too had this issue:
> Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you?
Their solution worked for me:
> sudo chroot "/mnt/boot-sav/md1" touch /boot/grub/menu.lst
I had to answer a couple 'which version of the menu.lst' should be kept questions (Since it was a blank file, I answered to use the package manitainer's)

Moving forward...

**EDIT 3**
**---------------------------------**
Boot continues to fail, [http://paste.ubuntu.com/p/5gbGjgw2wF/](http://paste.ubuntu.com/p/5gbGjgw2wF/)

> Attempting Boot From CD-ROM 
Attempting Boot From Hard Drive (C:)
error: file /boot/grub/i386-pc/normal.mod' not found. 
Entering rescue mode...
grub rescue) set 
cmdpath=(hd) 
prefix=(mduuid/9ce6c1092cadabf514f60055d700db37)/boot/grub
root=mduu id/9ce6c1092cadabf514f60055d700db37 
grub rescue>


I confirmed, mduuid/9ce6c1092cadabf514f60055d700db37 is the same as md/1.

**EDIT 4**
[B]---------------------------------
[/B]I have confirmed that, from the Rescue prompt, listing the folder (md/1)/boot/grub/i386-pc, there is no normal.mod. 
[ATTACH=CONFIG]285858[/ATTACH]
 But from a Live CD, after assembling and mounting MD1, normal.mod is in the folder. 

 I just found a comment in this post: [https://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](https://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found) stating > "If you have a large (e.g. 1TB) partition with Ubuntu installed and you didn't allocate additional one for /boot/, it could be the reason of such errors. When GRUB starts, it uses biosdisk driver for reading normal drivers from the /boot/grub/ directory. Sometimes, this directory could be physically located on the hard drive somewhere after the maximum supported by biosdisk sector."

Is this still possible in 18.04?  Might my normal.mod be out of reach?  If so, how do I move it earlier on the drive?

---

### Post by emcnish on 2020-05-17
I gave up and I'm moving to a different solution.  What a waste of time.

---

### Post by oldfred on 2020-05-17
Do not know RAID, so moving to Server Sub-forum where those who know RAID may be able to help.

Do not understand sdc & sdd. It looks like both are ext3, but sdc has one partition and sdd has no partitions and is just a formatted drive, which can cause issues on mounting as really then very large floppy drive.

---

### Post by LHammonds on 2020-05-18
I don't use RAID at the OS level so I don't have experience with those issues (I manage SAN directly at the hardware level which simply presents space I use at the OS level)

However, if you have /boot inside the software raid, it sounds like a bad idea for 2 reasons.  One being the issue mentioned in that last thread about needing the boot files accessible at the beginning of the partition.  Two being that if you have any issues with the raid, you cannot access /boot to for easy access to repair utilities.

There seems like only a few very-specific scenarios where having /boot inside the RAID is a workable situation.  As a rule of thumb, I try not to configure servers in such a way that it will not work well for the next server I setup.  Of course there are exceptions when installing on bare-metal because the hardware can drive certain designs but even then, I try to not make a black sheep scenario without good / documented reasons.

Can I ask what the reason was behind putting /boot inside the RAID and not on its own partition?

LHammonds

---

### Post by darkod on 2020-05-18
Looks like you've moved on. But if you still want to fix this let us know and we can help.

---

