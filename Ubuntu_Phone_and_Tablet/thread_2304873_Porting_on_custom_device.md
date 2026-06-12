---
title: "Porting on custom device"
date: 2015-11-30
forum: Ubuntu Phone and Tablet
---

### Post by RonGraham on 2015-11-30
Hi all,

I ask your help for porting ubuntu on a custom device running Android and based on TI OMAP4 SoC, it is not a commercial device, is something still under development, but i'm very curious about running ubuntu on it. I have the entire source for the bootloader (u-boot), kernel (3.0.31) and AOSP (4.1.1) so i can make any modification that would be needed.

I started adding these repos to the AOSP as said in [manifest.xml]("https://code-review.phablet.ubuntu.com/gitweb?p=aosp/platform/manifest.git;a=blob;f=default.xml;h=8a14ec08015eca091cd26c691b5a6daa740ef39b;hb=refs/heads/phablet-4.4.2_r1"):
```
[COLOR=#000000][FONT=monospace]<project path="ubuntu/assets" name="ubuntu/assets" revision="refs/heads/master" />[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]<project path="ubuntu/libhybris" name="ubuntu/libhybris" revision="refs/heads/master" />[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]<project path="ubuntu/platform-api" name="ubuntu/platform-api" revision="refs/heads/master" />[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]<project path="ubuntu/upstart-property-watcher" name="ubuntu/upstart-property-watcher" revision="refs/heads/master" />
<project path="ubuntu/ubuntu_prebuilt_initrd_debs" name="ubuntu/initrd/ubuntu_prebuilt_initrd_debs" revision="refs/heads/master" />[/FONT][/COLOR]
```

After some patching for supporting Android 4.1.1 I compiled the AOSP with ubuntu-specific components, so now i have:
- xloader, primary bootloader for TI SoCs (same as android)
- uboot (same as android)
- boot.img:
- - zImage (same as android)
- - ramdisk (dont know if modified)
- recovery.img (dont know if modified)
- system.img (includes ubuntu specifics)

* dont know if modified = dont know if some file built from ubuntu specific repos came into those images

Then i got a prebuilt ubuntu touch image from [http://cdimage.ubuntu.com/ubuntu-touch/](http://cdimage.ubuntu.com/ubuntu-touch/), i understood that i should put the system.img built from AOSP inside ubuntu image, in the folder /var/lib/lxc/android/, i guess i'm missing some other files and links as i saw in rootstock-install script, but what is not clear to me is how do i start ubuntu instead of android as in my ramdisk there is still the original android init? Is there another file/patch for the ramisk? The only clue for the moment is the [COLOR=#000000][FONT=monospace]ubuntu_prebuilt_initrd_debs [FONT=arial]repo that i found in the manifest, it seems to contain a ramdisk with some nice init script, should i use it with my original zImage for building boot.img? Though it seems that ubuntu image will be in /data/, together with android ubuntu-patched system.img, so android original system partition is useless?

Note that i couldn't use [FONT=courier new][rootstock-touch-install]("http://bazaar.launchpad.net/~ogra/project-rootstock-ng/trunk/view/head:/rootstock-touch-install")[/FONT] as i'm missing a lot of tools in the android recovery shell and also some folders in recovery are not present, it would be nice to have some tool for building the same img but on host side, not on the device.[/FONT][/FONT][/COLOR][FONT=arial][COLOR=#000000]

Above all, do you think my approach for the porting is good? There's a better/more correct way?


thank you for your time!
Luca[/COLOR][/FONT]

---

### Post by grahammechanical on 2015-12-01
I am sure that I am not insulting anyone who posts on this forum by saying you are much more advanced on this subject than any of us are. No doubt you have already read this wiki page but  I draw your attention to the heading Need Help? Get in touch.

> Porting an OS to a new device is a broad subject and this guide  doesn't pretend to be exhaustive on that topic. If you need more help on  specific topics, come meet the Ubuntu teams and other like-minded  people on **IRC** : #ubuntu-touch on [Freenode]("https://wiki.ubuntu.com/IRC/ChannelList").

  You should also probably join our **mailing list** by adding yourself to the [ubuntu-phone team]("https://launchpad.net/%7Eubuntu-phone") on Launchpad and enabling the team mailing list in your Launchpad options.



I may be wrong but I think that this is the best advice that this Ubuntu user forum can give you.

Regards.

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/)

---

### Post by RonGraham on 2015-12-01
grahammechanical, well i see that this may be too much technical.

Actually I already subscribed to the mailing list and joined IRC, though i didn't have any help, that's why i posted here...well i'll keep going on IRC and mails

thanks for your reply!
Luca

---

