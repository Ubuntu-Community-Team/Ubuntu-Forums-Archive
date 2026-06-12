---
title: "Looking for a GRUB2 expert"
date: 2020-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by MadsRH on 2020-02-20
Hi
Would there be any Ubuntu community members / contributors here with some know-how about GRUB2, that would be interested in helping with a small project?

Just send me a PM or leave a comment.

---

### Post by him610 on 2020-02-21
If I had any questions about grub, I would contact oldfred.

---

### Post by CelticWarrior on 2020-02-21
> **him610 said:**
> If I had any questions about grub, I would contact oldfred.

+1

All I know about UEFI and other related things I've learned from reading his posts. :guitar:

---

### Post by oldfred on 2020-02-21
Oldfred does not do consulting. 
Others also have good ideas, so best just to post your questions and then we all can help.

Manual 2.04
[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)
Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Shell_002dlike-scripting](https://www.gnu.org/software/grub/manual/grub/grub.html#Shell_002dlike-scripting)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by MadsRH on 2020-02-21
I apologize for my first post in this thread - it was a bit too vague :) I was not trying to be secret or mysterious at all :o)

> ...so best just to post your questions and then we all can help.

Thanks you! After reading this on [the wiki]("https://help.ubuntu.com/community/Grub2"):

> GRUB 2 Theming is still under development, as is integration with gfxmenu. Theme elements will include colors, fonts, progress indicators, menus, and labels. Both of these hold great promise but are not ready for release with **Ubuntu 9.10**. 

So, my first question is: are we there yet? 10 years has past! Is a graphical grub ready for deployment with the default Ubuntu installation?

I know that since installations alongside other OS'es is [less than 10]("https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/6/6ed1ec8cecf62b1a2aff547565eee0bfba1c37e1.png")%, this is a low priority for Canonical. This means that if they were to consider moving to a graphical grub, this would have to be well tested and not introduce a ton of new bugs (aka not take away developer time). 


What I want to do, is to create a GRUB theme, have the community test it and then suggest it to Cannonical for inclusion. Like, this is well tested, there's a good fallback, it's a minimal risk and so on.

So I'm asking two things: Is this stupid and can anyone help me with the code?

[IMG]https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/optimized/2X/d/d28af0ef139b697cae4edff5ede645be9936ca9a_2_1380x898.jpeg[/IMG]

---

### Post by him610 on 2020-02-21
On this link, [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")  at the bottom of the page under External Links, there a couple of refrences you may be interested in: *6. Grub Manual - Themes* and 7. *The Definitive Guide to Theming Grub2* by Towheed Mohammed
Good luck. Keep us informed.

---

### Post by oldfred on 2020-02-21
Grub still is not graphical.
If you want graphical, see rEFInd.
Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &

But their is a lot of info on theming in grub in these threads:
A Beginner's Guide to Theming GRUB2 - towheedm  & post #28 for grub2 2.00
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)
[https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images](https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
[https://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen](https://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen)
Colors only edit
sudo -H gedit  /lib/plymouth/themes/default.grub

I change grub to only show for 3 sec, then it starts boot.
But I use noplymouth, so I do not even get Ubuntu log.
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo

There also are other boot loaders.
Systemd took over gummiboot which Pop!OS now uses.
[https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/](https://blobfolio.com/2018/06/replace-grub2-with-systemd-boot-on-ubuntu-18-04/)

EFI stub loader
[https://askubuntu.com/questions/948814/how-to-boot-load-the-kernel-using-efi-stub-efistub-loader-with-secure-boot](https://askubuntu.com/questions/948814/how-to-boot-load-the-kernel-using-efi-stub-efistub-loader-with-secure-boot)

More alternatives & discussion
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by MadsRH on 2020-02-22
Thanks for all the links. I've got a bit of reading to do :)

> Grub still is not graphical.
If you want graphical, see rEFInd.

So you are saying that it can't be done? Perhaps I've missed something, but is there a difference between theming and graphical? 
I've never heard about rEFInd but it sounds like a rather big change.

---

### Post by oldfred on 2020-02-22
I have used rEFInd for emergency boot. It uses icons & you can use mouse. Mouse does not work with grub, so not gui.

Grub can give you the screen you show with just a background image and turning off most of the scripts and adding your own 40_custom. Grub2's osprober just adds a lot of verbiage. To make it automatic you would have to edit the scripts which I do not know much about. I typically let grub find default 2 kernels & add everything else with 40_custom. And do not add background or change fonts/colors.

Long thread, Cavsfan has posted ways to customize grub manually. And has screen shots. 
This will start you at end and you can go backwards to see a lot more.
[https://ubuntuforums.org/showthread.php?t=2076205&page=55](https://ubuntuforums.org/showthread.php?t=2076205&page=55)

---

### Post by kevdog on 2020-02-22
+1 for gummiboot.  Very very easy to install and configure on UEFI systems compared to grub.

---

### Post by EuclideanCoffee on 2020-02-22
Off-topic, I'm super interested in what you're cooking up.

---

### Post by Geoffrey_Arndt on 2020-02-22
More information here . . . [https://www.slant.co/topics/2239/~best-boot-loaders](https://www.slant.co/topics/2239/~best-boot-loaders)

---

