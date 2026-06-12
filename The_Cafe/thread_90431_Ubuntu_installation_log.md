---
title: "Ubuntu installation log"
date: 2005-11-14
forum: The Cafe
---

### Post by e-gandalf on 2005-11-14
Hi all.

I'm just finishing Ubuntu 5.10 (Kubuntu) installation for my flatmate. I wanted to share the experience, and that could be usefull in install process development for Ubuntu devs. If this is not interesting for you, just go to the next thread :)

A few words about the environment for this Ubuntu. I'm a Gentoo user, geek, Flock dev etc., I have no experience with Debian not Ubuntu before, my flatmate is a experienced windows user with very small experience with Linux (irc via shell kind of).
He has a rather old machine (Pentium 600) and decided to try Linux via Kubuntu distro.

Here is the log:

1) Booting from CD and deciding to install Ubuntu on third drive (/dev/hdd)
2) Going through installation process without a single problem - a few minor l10n glitches around. Polish localization seems not to be polished (sic!) yet ;)
3) Choosing Grub over Lilo
4) Finishing installation
5) Reboot
  - Here we found the first trap. Grub was installed on /dev/hda's MBR without a single question. It should really describe the choices. But ok, no problem.
  - Grub doesn't load. It loads two lines that it's starting and freeze.
  - After a lot of investigation, using other livecd+chroot+grub console I found that initrd failed with Error 16.
  - It should report it to me earlier, and in the boot process. I can't imagine any John Smith doing what I did to find that BIOS is too old for Grub.
  - What next? We want to install Lilo now, but how?
  - Choosing to start from CD, choose partition mount points
  - Ubuntu says that it won't install because there are already files on that partition. - It would be nice if it could find out that it's the same Ubuntu and ask if I want to fix it, upgrade, go to menu, reinstall or exit.
  - After this "error" it allows me to choose "Install Lilo"
  - Finish Installation takes quite a lot of time (much more then in step 4)
6) Reboot with Lilo - OK
7) It starts configuring. It configures apt and asks if I want to add *another* repository source. I don't. The menu is in Polish without Polish chars. Looks ugly.
8) It launches some configuration progress bar and then goes to menu from step 7. Infinity loop! 
9) I finally chooses "Yes" and it asks for CD (???), and does some magic inside and starts to configure something else. We runned out of infinity loop, but that part looks really bad and totally user confusing.
10) Last configuration took really *a lot* of time and didn't find polish locales at all.
11) X started with default gray background - it doesn't look good.

That's all for now. The login screen is on, and my flatmate will test it, Kubuntu is ready :)
Note: I know that those issues might not be Ubuntu fault, but user will not be interested... really. And I'm not asking to fix_it_now, just I thought that you may find this interesting.

---

### Post by e-gandalf on 2005-11-14
13) It exited Xorg to install missing packages (locales-pl, kde-i18n-pl etc.), failed to find them, launches X, shutdowned X and started installing those once more. Second infinity loop!

---

