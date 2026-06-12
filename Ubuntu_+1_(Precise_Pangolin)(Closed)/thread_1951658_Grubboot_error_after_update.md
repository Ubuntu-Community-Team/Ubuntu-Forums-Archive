---
title: "Grub/boot error after update"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hitime on 2012-04-02
On the daily updates 4/2 of the 64bit version of Ubuntu desktop, I received an error after a reboot following an update:

error: invalid blocklist
Press any key to continue

After hitting a key and giving it a moment my system does boot into the login, but I would definitely like to find fix what I believe to be my grub setup.  I really haven't had many problems (running for over a month) until this update.  If someone could point me in the right direction it would be most appreciated, I'm thinking the grub config has to be redone.

Thanks,
hitime

---

### Post by funeral1988 on 2012-04-02
Me too! This happens after grub updates.
Ubuntu 12.04 updated, x64

---

### Post by cariboo on 2012-04-02
Have either of you tried to reinstall grub?

---

### Post by funeral1988 on 2012-04-02
> **cariboo907 said:**
> Have either of you tried to reinstall grub?

When installing get this:

arch@ubox:~$ sudo grub-install --force /dev/sda --no-floppy
[sudo] password for arch: 
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: non-sector-aligned data is found in the core file.

---

### Post by oldfred on 2012-04-03
If you have no embedding area and are installing to sda, then are your using gpt without a bios_grub partition? Or have you installed to a PBR as those are the two main places grub has to use blocklist to squeeze itself in.

 However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02. Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

---

### Post by neverknows on 2012-04-03
this hit me too, I did some research and my first sector is 34 on a gpt default install of 12.04.

the boot-repair app could not fix it, but did add my 12.04 to an old install on a second drive.

right now i have to boot to my old disk and select my new disk to boot 12.04.

---

### Post by mrfelker on 2012-04-03
This just happened to me after updating Ubuntu 12.04 from the beta.  I get the error "invalid blocklist" " press any key to continue"  and I can continue to the login screen without further problems.  Reinstall grub from the Ubuntu startup disk rescue mode did not improve matters.  My boot partition is on a primary /dev/sdb1. I can't insatll to MBR because I use a 3-thrid party boot loader which I won't give up I hope the developers can fix this but I doubt it.  To change the grub program at this late date is either on purpose (to get people to instatll the "final")  or a grave mistake.  Either way it really is a bummer

---

### Post by phil.lxnet on 2012-04-03
I have just opened a bug report that I think may be related:-

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411)

My grub update today resulted in:-
error: out of partition.
Press any key to continue...
but seems related as I have grub installed to a partition not the MBR.

---

### Post by dino99 on 2012-04-03
> **phil.lxnet said:**
> I have just opened a bug report that I think may be related:-

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972411)

My grub update today resulted in:-
error: out of partition.
Press any key to continue...
but seems related as I have grub installed to a partition not the MBR.

if you run : sudo dpkg-reconfigure grub-pc
it will tell you that installing it inside a partition is a bad idea.

---

### Post by oldfred on 2012-04-03
It looks like the very newest grub 1.99 now does not work with blocklists. 

I have seen another user who just installed with gpt and it worked until now. He went back and added the bios_grub and then it worked.

---

### Post by sgage on 2012-04-03
> **funeral1988 said:**
> When installing get this:

arch@ubox:~$ sudo grub-install --force /dev/sda --no-floppy
[sudo] password for arch: 
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: non-sector-aligned data is found in the core file.

I got this just an hour ago with a clean install of today's build, trying to install grub on /dev/sda2. So I booted with the LiveCD, chrooted to the new install, and tried installing grub to the MBR - same error.

I ran the install over again from scratch, and it worked (installing grub in the MBR - I didn't try /dev/sda2 yet).

---

### Post by Kamigawa on 2012-04-03
> **funeral1988 said:**
> When installing get this:

arch@ubox:~$ sudo grub-install --force /dev/sda --no-floppy
[sudo] password for arch: 
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: non-sector-aligned data is found in the core file.

I have got the exact same problem and I don't know what to do (seems to be a problem of newer GRUB versions as it also happened with Fedora 17 Alpha).
Has anybody an idea how to solve the issue?

---

### Post by xebian on 2012-04-03
The update today was a pleasant surprise.  I now see a background and it's a Debian stars, logo and an earth top sphere at the bottom, some text like universal OS.:guitar:

---

### Post by Kamigawa on 2012-04-03
At the moment I'm able to boot into Ubuntu 12.04 using the [Super GRUB2 Disk]("http://www.supergrubdisk.org/"). But this isn't a comfortable situation of course.

---

### Post by ranch hand on 2012-04-03
Ah, the "Space Fun" theme.  One thing you can say about Debian is that they are not the least interested in cutting edge artwork.

Just got that changed in a new install of Debian Wheezy on the Dreaded Mother in Laws box to show a more "mature" background for grub.  Still need to get the Xfce log in splash replaced with the same image.

On the other hand, grub works.

---

### Post by sgage on 2012-04-03
It seems an upgrade to grub in the last few minutes has fixed the problem - I was able to install grub to /dev/sda2.

---

### Post by zika on 2012-04-03
I was given choice to install Grub in:
- /dev/sda (I guess it is MBR)
- /dev/sda1 (partition, I guess)
I chose /dev/sda. Did I make a mistake? Machine boot-ed OK...

---

### Post by sgage on 2012-04-03
> **zika said:**
> I was given choice to install Grub in:
- /dev/sda (I guess it is MBR)
- /dev/sda1 (partition, I guess)
I chose /dev/sda. Did I make a mistake? Machine boot-ed OK...

On this machine, I dual-boot with Windows. Windows will not hibernate properly unless its own bootloader is in the MBR (dev/sda), so I put grub in my Precise partition (/dev/sda2) and let the Windows bootloader chaing to it. (I use EasyBCD in Windows to easily configure the bootloader to find my Linux.)

There's nothing wrong at all with putting it in /dev/sda - in fact, that's the recommended way to do it. When you install it in /dev/sdax (if you install it from a command line so you can see the messages), you get messages on how they'd really rather you put grub in the MBR. I guess it's a bit of a kludge to make it work the way I prefer.

---

### Post by funeral1988 on 2012-04-03
Today's update solved a problem. Fixed for me, no more errors on boot.:p

---

### Post by Kamigawa on 2012-04-04
It also works for me after installing todays updates :)

---

### Post by hitime on 2012-04-04
Sorry I have disappeared for a day, but the update today also repaired my issue also...  The joys of beta :smile:

---

### Post by zika on 2012-04-05
For the first time in the whole 12.04 testing (I must admit) I was worried upgrading Grub just several minutes ago... ;)

---

### Post by DShad on 2012-04-08
Hi!

I'm using Ubuntu 12.04 beta (64bits) and I did some updates and here is what is happening since:

Error: Invalid Blocklist
Press any key to continue...

So I press a key and everything boot as usual.  Is there any way I can get rid on that warning?

I'm on a multiboot HDD with Ubuntu 12.04, a SWAP partition and WIndows XP.

Thank you

---

### Post by zika on 2012-04-08
> **DShad said:**
> Hi!

I'm using Ubuntu 12.04 beta (64bits) and I did some updates and here is what is happening since:

Error: Invalid Blocklist
Press any key to continue...

So I press a key and everything boot as usual.  Is there any way I can get rid on that warning?

I'm on a multiboot HDD with Ubuntu 12.04, a SWAP partition and WIndows XP.

Thank you
[http://ubuntuforums.org/showthread.php?t=1951658](http://ubuntuforums.org/showthread.php?t=1951658)

---

### Post by DShad on 2012-04-09
> **xebian said:**
> The update today was a pleasant surprise.  I now see a background and it's a Debian stars, logo and an earth top sphere at the bottom, some text like universal OS.:guitar:

It's weird because my system is up-to-date but my problem still remains...

Any idea anybody?

Thank you!

---

