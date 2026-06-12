---
title: "disk drive for / is not ready yet or not present AFTER 13.10-&gt;14.04 upgrade"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by serge_o on 2014-03-23
I tried an upgrade to 14.04 from 13.10 on my desktop system. I my (as it seems - flawed) opinion the quality of the current 14.04 should not be very different from the release version in 3 weeks, so I was ready for a beta with glitches...
What I was not ready for was a system rendered unusable with "the disk drive for / is not ready yet or not present"

What I did  this Saturday (March 21st) was basically following this simple guide [http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/](http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/)
1) upgrade the 13.10 upto the limit with the gui updater
2) sudo apt-get update && sudo apt-get dist-upgrade  (from the guide)
3) sudo update-manager -d

the update encountered some python related error (could not find python of a version it would like to have or something like this - the console did not allow me to scroll up in this dist updater thing).
so it tried to back the upgrade off and then - see topic subj... (on the purple ubuntu screen)

the first thing that seemed odd to me is lack of initrd in the grub entry. I have several grub entries for previous 13.10 kernels from previous updates, and they all have initrd.
this is my last entry (from 14.04 I suppose, noting the 3.13 kernel)

setparams 'Ubuntu'
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root = 'hd0, msdos2'
if [x$feature_platform_search_hint = xy]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 60...long UUID here...1b
else
search --no-floppy --fs-uuid --set=root 60..same long UUID here ... 1b
fi
linux /boot/vmlinuz-3.13.0-18-generic root=/dev/sda2 ro quiet splash $vt_handoff

*********************

thats all, but normally such entries do have an "initrtd /boot/initrd.img-3.13.0.18-generic" (kernel version that matches the one in the linux cmd").
This is suspicious, or have they replaced initrd in 14.04 with some "upstart wayland unity new technology thinng?"

To sum it up.
I was really ready for the glitches of the early 14.04
I am not really ready to lose my desktop or to do a clean reinstall.
I am ready to do some work to investigate the matter and spend my time on it
ready to supply more info on the case.


P.S. I have not done anything wrong with my 13.10. so it was a perfectly normal install, which was being upgraded on a regular basis, not much extra software installed apart from a browser really...
it is not like I was installing some proprietary drivers or some tainted kernels or like...

So, what do you suggest I should try.

---

### Post by oldfred on 2014-03-24
Moved to Ubuntu+1 since 14.04 not yet released.

We always suggest only installing a version not yet released into a separate test partition. Never depend on alpha or beta software for your main working system. Some even suggest waiting to upgrade for a few weeks or months after release as some bugs do not appear until more widely used after release.

Python is critical for many background activities in Ubuntu. That may be the first thing you need to fix.
And then the install did not complete so you did not get the initrd created.

You probably will have to chroot into your install and see if you then can repair it. Otherwise a new install and restore your data from your backups.

---

### Post by frank18 on 2014-03-24
> **oldfred said:**
> Moved to Ubuntu+1 since 14.04 not yet released.

We always suggest only installing a version not yet released into a separate test partition. Never depend on alpha or beta software for your main working system. Some even suggest waiting to upgrade for a few weeks or months after release as some bugs do not appear until more widely used after release.

Python is critical for many background activities in Ubuntu. That may be the first thing you need to fix.
And then the install did not complete so you did not get the initrd created.

You probably will have to chroot into your install and see if you then can repair it. Otherwise a new install and restore your data from your backups.

i've installed Ubuntu 14.04betai 64bit  already for a month and never had a single problem so far.it works much better then 13.10 for sure.

---

### Post by frank18 on 2014-03-24
> **oldfred said:**
> Moved to Ubuntu+1 since 14.04 not yet released.

We always suggest only installing a version not yet released into a separate test partition. Never depend on alpha or beta software for your main working system. Some even suggest waiting to upgrade for a few weeks or months after release as some bugs do not appear until more widely used after release.

Python is critical for many background activities in Ubuntu. That may be the first thing you need to fix.
And then the install did not complete so you did not get the initrd created.

You probably will have to chroot into your install and see if you then can repair it. Otherwise a new install and restore your data from your backups.



i've installed Ubuntu 14.04beta1 64bit  already have it installed for  a month now  and never had a single problem so far.it works much better then 13.10 for sure.
it was a little tricky to install but once installed it's great.

---

### Post by craig10x on 2014-03-24
Personally, i never used the software updater to do an upgrade....i use the iso upgrader which works very well...if you only run one ubuntu, and had popped in a 14.04 iso of the daily build (or the final when released), the iso installer, aside from offering to wipe out your current 13.10 and make a clean install of 14.04, would also offer the option to Upgrade to 14.04 and bring over your data and most of your apps with it...that is the one i used and it's always been very reliable and fast (about 30 minutes total and i have a LOT of data)....

I always turn off any ppas (which seem to get wiped out anyway) and i always seem to need to re-install Google Chrome and MS Core fonts (because they have license agreements) but otherwise, it does essentially a clean install and brings just about everything over as i outlined...

Try THAT method the next time to want to do an upgrade...seems much more reliable then doing it through the updater...
At this point, might be best to get a daily build iso of 14.04 and install that instead...

---

