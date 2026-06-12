---
title: "Dual boot . Calamares doesn't detect WIN10 during Ubuntudde installation,"
date: 2021-04-25
forum: Ubuntu/Debian BASED
---

### Post by rolandeschain on 2021-04-25
Hi everyone!
I'm trying to do a dual boot with Ubuntudde and Windows 10, but Calamares doesn't detect Windows.
Although I disabled Secure boot, fast boot and enabled Legacy mode it doesn't work.
It shows "Install alongside", but it doesn't shows Windows 10

[https://drive.google.com/file/d/1QUVAb5xbSxD0HWOrCqvzX9rMFfR1ODOK/view?usp=sharing](https://drive.google.com/file/d/1QUVAb5xbSxD0HWOrCqvzX9rMFfR1ODOK/view?usp=sharing)

When I sellect Manual partitioning it shows this:

[https://drive.google.com/file/d/18u3o6cbm5W-WD3aYOf_2eWE-ORisCQtL/view?usp=sharing](https://drive.google.com/file/d/18u3o6cbm5W-WD3aYOf_2eWE-ORisCQtL/view?usp=sharing)

It is what I watch on Gparted:

[https://drive.google.com/file/d/1cIZvpamJerOanvKBq-nkrH8lI9zrRhIE/view?usp=sharing](https://drive.google.com/file/d/1cIZvpamJerOanvKBq-nkrH8lI9zrRhIE/view?usp=sharing)

Thanks!!

---

### Post by howefield on 2021-04-25
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Frogs Hair on 2021-04-25
I experienced only one successful installation of this distribution out of many attempts even completing installation process more than three times only to find out the installation never occurred. These are the community links for support.

[https://sourceforge.net/projects/ubuntudde/support](https://sourceforge.net/projects/ubuntudde/support)

[https://ubuntudde.com/support/](https://ubuntudde.com/support/)

---

### Post by rolandeschain on 2021-04-25
Thanks for the answer!!

I've tried with Telegram and Discord Ubuntudde communities and I've found lots of questions but not many answers....

---

### Post by yancek on 2021-04-27
>  Although I disabled Secure boot, fast boot and enabled Legacy mode it doesn't work.

I'm not sure why you would enable Legacy mode as your windows install is clearly an EFI install and if you installed ubuntudde in Legacy mode, you would need to go into the BIOS boot options to select windows whenever you want to boot it.  Legacy Grub will not boot an EFI install of windows.  If you see the windows partitions using the Something Else option, why not use that?  I've never used this system or Deepin so don't know what causes this.

---

### Post by oldfred on 2021-04-27
If you have ESP - efi system partition and drive is gpt, then Windows has to be in UEFI boot mode.
And then you need to have all other installs in UEFI boot mode.

You may need to have Windows fast start up off also.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by rolandeschain on 2021-04-27
Thanks for your replies mates. 
Yancek, I did it because in most of the YouTube tutorials I've found they do it.
Next weekend I'm going to try with. 
UEFI mode then.
oldfred I'll read your posts before. 

I'll tell you the results.

---

### Post by CelticWarrior on 2021-04-27
You need to find better tutorials.

---

### Post by yancek on 2021-04-28
You will be much better off with official documentation such as the link below which is specific to dual booting with windows 10 UEFI rather than using a YouTube videol  Anyone can post anythng on YouTube.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

