---
title: "Can not upgrade to 13.10"
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-10-09
I wanted to do an upgrade from 13.04.

So I sued this commend 

sudo update-manager -d
But I got this error

Could not calculate the upgrade


An unresolvable problem occurred while calculating the upgrade.


 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu


If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

---

### Post by philinux on 2013-10-09
> **Chelidze said:**
> I wanted to do an upgrade from 13.04.

So I sued this commend 

sudo update-manager -d
But I got this error

Could not calculate the upgrade


An unresolvable problem occurred while calculating the upgrade.


 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu


If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

First do this.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Then try 

```
update-manager -d
```

---

### Post by Chelidze on 2013-10-09
[COLOR=#000000]**[[COLOR=#000000]philinux[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")**[/COLOR]


Thank You for the reply

 I encountered the same issue



An unresolvable problem occurred while calculating the upgrade.


 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu


If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

---

### Post by philinux on 2013-10-09
> **Chelidze said:**
> [COLOR=#000000]**[[COLOR=#000000]philinux[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")[COLOR=#000000] [/COLOR]**[/COLOR]
**[COLOR=#000000][/COLOR]**

Thank You for the reply but I encountered the same issue

Ok. Thats fine. Go into your software sources and disable all your ppa's.

---

### Post by Chelidze on 2013-10-09
> **philinux said:**
> Ok. Thats fine. Go into your software sources and disable all your ppa's.

Should I even disable this ppa's ??

I do not know how or why but now it looks different this is what I get now 

[http://i.imgur.com/peJ5gJe.png](http://i.imgur.com/peJ5gJe.png)

Should I disable ALL of them ??

---

### Post by craig10x on 2013-10-09
It is important to uncheck any ppas you have before doing the upgrade (in your software sources as phillinux mentioned)...
If you haven't started to try again yet, i would like to suggest that instead of upgrading using the software updater as you are trying to do, burn a daily build iso of 13.10 and run it in live session, then once it loads in, select "install ubuntu" from the unity dock and when the installer opens, select the option to "upgrade to 13.10" (rather then the other selection that wipes out your current install and makes a clean install of 13.10)...

that is the way I upgraded my 13.04 to 13.10 development and it worked well...all my data carried over, and most of my apps and settings...a few tweaks and i was good to go...
I only ended up having to re-install Google Chrome and MS Core Fonts...and re-adjust a few settings...quite a time saver!  and it was much faster then using the software updater which has to go to to the web for the packages...

however, before starting...uncheck your ppas until after install is done...

---

### Post by Chelidze on 2013-10-09
Thank You for the replies but even after disabling ppa's I still get the same error massage

Guess I will fill up a bug report

---

### Post by philinux on 2013-10-09
> **Chelidze said:**
> Thank You for the replies but even after disabling ppa's I still get the same error massage

Guess I will fill up a bug report

Were there any errors when you did the apt-get update upgrade.

Oh hang on the updater has changed all your sources to saucy. Might be better to take a step back and change them back to raring then make sure your system is fully up to date first.

---

### Post by Chelidze on 2013-10-09
> **philinux said:**
> Were there any errors when you did the apt-get update upgrade.

Oh hang on the updater has changed all your sources to saucy. Might be better to take a step back and change them back to raring then make sure your system is fully up to date first.

There were no errors accept what I mentioned above and about ppa's it changed back to this 
[http://i.imgur.com/peJ5gJe.png](http://i.imgur.com/peJ5gJe.png)

---

### Post by den_ on 2013-10-09
> **craig10x said:**
> It is important to uncheck any ppas you have before doing the upgrade (in your software sources as phillinux mentioned)...
If you haven't started to try again yet, i would like to suggest that instead of upgrading using the software updater as you are trying to do, burn a daily build iso of 13.10 and run it in live session, then once it loads in, select "install ubuntu" from the unity dock and when the installer opens, select the option to "upgrade to 13.10" (rather then the other selection that wipes out your current install and makes a clean install of 13.10)...

that is the way I upgraded my 13.04 to 13.10 development and it worked well...all my data carried over, and most of my apps and settings...a few tweaks and i was good to go...
I only ended up having to re-install Google Chrome and MS Core Fonts...and re-adjust a few settings...quite a time saver!  and it was much faster then using the software updater which has to go to to the web for the packages...

however, before starting...uncheck your ppas until after install is done...

I don't think just disabling (Unchecking) PPAs is ok. It can leave packages on the system, what can cause issues with resolution of dependencies. Best way would be to remove PPAs with ppa-purge if possible, and if not then trying manually to remove all packages from PPAs repositories.

---

### Post by grahammechanical on 2013-10-09
You have to un-tick all those PPAs. It is most likely that they do not have repositories for saucy as yet. Think of a repository being at the end of an internet address. The repositories for 13.04 are at the end of an internet address that has 'raring' as part of the address. To upgrade to 13.10 the normal repositories for 13.04 have to have their internet addresses changed to addresses with saucy in the address line.

The upgrade manager cannot find repositories for those PPAs because the maintainers of the PPAs have not provided an internet address with saucy in the address line for those applications. And so you are meeting two out of the three reasons for the failure to upgrade. You are upgrading to a pre-release version of Ubuntu and you have unofficial software packages not supported by Ubuntu. The Upgrade Manager cannot work out exactly what there is on your system that can be upgraded to 13.10 code.

Regards.

---

### Post by Chelidze on 2013-10-09
> **grahammechanical said:**
> You have to un-tick all those PPAs. It is most likely that they do not have repositories for saucy as yet. Think of a repository being at the end of an internet address. The repositories for 13.04 are at the end of an internet address that has 'raring' as part of the address. To upgrade to 13.10 the normal repositories for 13.04 have to have their internet addresses changed to addresses with saucy in the address line.

The upgrade manager cannot find repositories for those PPAs because the maintainers of the PPAs have not provided an internet address with saucy in the address line for those applications. And so you are meeting two out of the three reasons for the failure to upgrade. You are upgrading to a pre-release version of Ubuntu and you have unofficial software packages not supported by Ubuntu. The Upgrade Manager cannot work out exactly what there is on your system that can be upgraded to 13.10 code.

Regards.

I did that but same issue do not know why should I reboot and try again ??

---

### Post by mc4man on 2013-10-09
Did you update your sources after removing ppa's?

---

### Post by Chelidze on 2013-10-09
> **mc4man said:**
> Did you update your sources after removing ppa's?

Yes but no luck

---

### Post by craig10x on 2013-10-09
That is the problem with having too many ppas if you want to use the upgrade method...I only has 2 ppas (Chrome and Oracle Java) and i removed the Java and the PPA before upgrading and unchecked the Chrome ppa and it went very smooth....

Things look pretty messed up there...you may just have to go with a clean install of 13.10 (you can do it from a daily build)....
Not that it wil probably make a difference at this point....but i suggest you burn a daily build iso of 13.10 and run it live...then TRY doing the upgrade with that selection on the installer....if it fails, then re-boot again and do a clean install (have it wipe everything out)...

---

### Post by Chelidze on 2013-10-09
> **craig10x said:**
> That is the problem with having too many ppas if you want to use the upgrade method...I only has 2 ppas (Chrome and Oracle Java) and i removed the Java and the PPA before upgrading and unchecked the Chrome ppa and it went very smooth....

Things look pretty messed up there...you may just have to go with a clean install of 13.10 (you can do it from a daily build)....
Not that it wil probably make a difference at this point....but i suggest you burn a daily build iso of 13.10 and run it live...then TRY doing the upgrade with that selection on the installer....if it fails, then re-boot again and do a clean install (have it wipe everything out)...


 It never was a problem form my before now to upgrade. and I had ubuntu versions that had much more software installed.

About clean reinstall sure I will do it after 13.10 is out of beta but for now I do not want it 


```
 grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*/etc/apt/sources.list:# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-updates universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-security main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-security universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-security multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb http://archive.canonical.com/ubuntu raring partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu raring partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:# deb http://extras.ubuntu.com/ubuntu raring main
/etc/apt/sources.list:# deb-src http://extras.ubuntu.com/ubuntu raring main
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu raring-proposed universe main restricted multiverse
/etc/apt/sources.list:# deb http://repository.spotify.com stable non-free
/etc/apt/sources.list:# deb-src http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list:# deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list:# deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list.distUpgrade:# deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list.save:# deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-raring.list.save:# deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu raring main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list:# deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list:# deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list.distUpgrade:# deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list.save:# deb http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/indicator-multiload-stable-daily-raring.list.save:# deb-src http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list:# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list:# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list.distUpgrade:# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list.save:# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list.save:# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list:# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list:# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list.distUpgrade:# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list.save:# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/libreoffice-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list.distUpgrade:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list.save:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-raring.list.save:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list:# deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list:# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list.distUpgrade:# deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list.save:# deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-raring.list.save:# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list:# deb http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list:# deb-src http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list.distUpgrade:# deb http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list.save:# deb http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/sunab-kdenlive-svn-raring.list.save:# deb-src http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.distUpgrade:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.save:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list:# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list:# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list.distUpgrade:# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/ubuntu-wine-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list.distUpgrade:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list.save:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list.save:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list.distUpgrade:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list.distUpgrade:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list.save:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list.save:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main



```

---

### Post by Mateusz Stachowski on 2013-10-09
> **Chelidze said:**
> It never was a problem form my before know to upgrade and I had ubuntu versions that had much more software installed.

Exactly those PPA's shouldn't be a problem. I've made many upgrades of Ubuntu throughout the years and always had dozens of PPA's which upgrade-manager simply disabled on it's own.

Also if you have many programs installed I definitely discourage you from upgrading with Live image. I've made upgrade that way for the first and last time about a week ago. This removed all my custom installed programs including things like Synaptic, gdebi, htop and so on... Before I started the upgrade I had 2,5 GB o free space on my root partition when the thing completed there was more then 10 GB of free space. Basically what you will get in that upgrade process is only the core Ubuntu upgraded and all other things removed. No more upgrades this way for me.

---

### Post by craig10x on 2013-10-09
@ Mateusz Stachowski:  Interesting...well using the iso installer upgrade method was my first shot at doing an upgrade...and i had added programs like pidgin, synaptic, psensor, vlc even k3b (a kde program!) and they all came over in the upgrade...Only thing that did not make it through was Google Chrome (had to re-install, though it remembered my settings on it) and i noticed the MS Core Fonts weren't working so i removed it and re-installed it and then they were fine...

All my data transferred in (music, photos, documents) and even most of system settings like appearance theme, auto-hide, pixel size of unity icons, etc...a few system settings returned to default like Volume Control...and a few others...

Spent maybe 20 minutes fixing that stuff up and i was good to go...Also, it was fast....a clean install i find, usually take about 20 minutes...the upgrade took perhaps an extra 5 minutes or so...
I was shocked at how smooth it went overall...i was prepared for a clean install in case things went awry ;)

Oh, and a friend of mine did this method also and except for a minor glitch with his cairo dock (he uses cairo dock session) which he straightened out...everything was good on his also...
Sorry to hear your experience with it was bad but mine encouraged me to use it again the next time i upgrade...i always had the feeling that doing it with the update manager method might be more glitchy based on reading some other experiences here...

---

### Post by xc3RnbFO8P on 2013-10-09
Did you try:
> sudo apt-get autoremove

---

### Post by Chelidze on 2013-10-09
> **Ringi said:**
> Did you try:

Did not work

---

### Post by mc4man on 2013-10-09
Are any of the ppa's providing packages that are higher than those in 13.10?  (like nvidia, ect

---

### Post by Chelidze on 2013-10-09
> **mc4man said:**
> Are any of the ppa's providing packages that are higher than those in 13.10?  (like nvidia, ect

Sorry I do not quite understand what you mean by that, if you are asking me the version of the software for example nvidia drivers, then yes I am using nvidias beta 325 drivers which I can not select from default drivers menu

---

### Post by mc4man on 2013-10-10
> **Chelidze said:**
> Sorry I do not quite understand what you mean by that, if you are asking me the version of the software for example nvidia drivers, then yes I am using nvidias beta 325 drivers which I can not select from default drivers menu
Yes, that's what I mean
Maybe start by removing all the nvidia packages you have from that ppa & go back to nouveau. 
Possibly the same for gimp if the ppa packages are higher than what is in 13.10

---

### Post by Chelidze on 2013-10-10
> **mc4man said:**
> Yes, that's what I mean
Maybe start by removing all the nvidia packages you have from that ppa & go back to nouveau. 
Possibly the same for gimp if the ppa packages are higher than what is in 13.10

To be honest I done upgrades from 13.04 to 13.10 before the final beta with a lot more ppa's and this nvidia driver So I struggle to believe that that will work. if nothing will come out I will weight for the release and then will do a clean reinstall

---

### Post by kansasnoob on 2013-10-10
This is possibly a rather stupid idea, but if your sources are still set at Raring it would be interesting to see what happens if you run:

```
update-manager -d -c
```

I only mention that because the 'release-upgrader' packages were recently updated and the added "-c" should get you to the latest "release-upgrader".

But if things blow up don't be too surprised. There are lots of bugs in Saucy right now.

---

### Post by craig10x on 2013-10-10
I still think he should burn a daily build iso and use the upgrade option on the installer...i don't think he would have much to lose and it might just work...i think the upgrade is done in a different manner on the iso then it is when you do it on the software updater...(a better way, i think)...

---

### Post by kansasnoob on 2013-10-10
> **craig10x said:**
> I still think he should burn a daily build iso and use the upgrade option on the installer...i don't think he would have much to lose and it might just work...i think the upgrade is done in a different manner on the iso then it is when you do it on the software updater...(a better way, i think)...

I don't disagree with that :)

I always include the upgrade (image) tests in my iso testing:

[http://iso.qa.ubuntu.com/qatracker/testcases/1498/info](http://iso.qa.ubuntu.com/qatracker/testcases/1498/info)

It's a truly decent process and much faster than using the 'release-upgrader'. I'll grant you that apps not available from the standard repos must be manually reinstalled but it's still a much cleaner upgrade method.

But both upgrade methods must be tested prior to release.

---

### Post by craig10x on 2013-10-10
@kansasnoob: absolutely! could not agree more ;)
In fact, the ONLY apps that did not carry over for me was google chrome and mscorefonts (well actually mscorefonts is in the repos but it does have a license agreement as does chrome)....
All other apps i had installed (from ubuntu software center) were brought over with no problem....including every last piece of data i had (music, photos, videos, documents)...

watching the install, it was almost as if i was doing a clean install, you get the standard slide show...have to pick your log in and time zone just like a clean install and if you didn't look at the technical things going on underneath, you would not even know you were doing an upgrade at all...

time wise, i know usually a clean install takes around 20 minutes....the upgrade from the iso image took about 25 minutes...super fast!
i was totally amazed...and this is why i can't understand the often stubborn attitude i see here about people trying that method...they seem to think that the software updater upgrade method is the superior way to go...based on my experience, i have some reason to doubt that...

a friend of mine also used this method and it went just as well for him as it did for me...

---

### Post by xc3RnbFO8P on 2013-10-10
Check this:
[http://askubuntu.com/questions/67698/could-not-calculate-the-upgrade-on-distribution-upgrade]("http://askubuntu.com/questions/67698/could-not-calculate-the-upgrade-on-distribution-upgrade")

---

### Post by Chelidze on 2013-10-10
> **kansasnoob said:**
> This is possibly a rather stupid idea, but if your sources are still set at Raring it would be interesting to see what happens if you run:

```
update-manager -d -c
```

I only mention that because the 'release-upgrader' packages were recently updated and the added "-c" should get you to the latest "release-upgrader".

But if things blow up don't be too surprised. There are lots of bugs in Saucy right now.

Sadly did not work

> **craig10x said:**
> I still think he should burn a daily build iso and use the upgrade option on the installer...i don't think he would have much to lose and it might just work...i think the upgrade is done in a different manner on the iso then it is when you do it on the software updater...(a better way, i think)...

I understand that but I wanted to upgrade to ubuntu **13.10 BETA** version like that but when 13.10 will be released I will do a clean reinstall 

> **Ringi said:**
> Check this:
[http://askubuntu.com/questions/67698/could-not-calculate-the-upgrade-on-distribution-upgrade](http://askubuntu.com/questions/67698/could-not-calculate-the-upgrade-on-distribution-upgrade)

Sadly did not work don't have [COLOR=#000000][FONT=Ubuntu Mono]ia32-libs at all[/FONT][/COLOR]

---

### Post by xc3RnbFO8P on 2013-10-10
> **Chelidze said:**
> Sadly did not work



I understand that but I wanted to upgrade to ubuntu **13.10 BETA** version like that but when 13.10 will be released I will do a clean reinstall 



Sadly did not work don't have [COLOR=#000000][FONT=Ubuntu Mono]ia32-libs at all[/FONT][/COLOR]

I was thinking maybe you have package like ia32  "ia-32-libs aren't available for saucy"
You have Java PPA maybe some package related to that

---

### Post by Chelidze on 2013-10-10
Ok this thing worked 

```
sudo sed -i 's/raring/saucy/' /etc/apt/sources.list
```

and then

```
Sudo [FONT=Ubuntu Mono]apt-get dist-upgrade[/FONT]
```

---

### Post by craig10x on 2013-10-10
Actually, 13.10 will be final released next thursday (17th) so you burn that iso and upgrade to 13.10 at that time...if you have problems, you can always do a clean install of it after that...
When i used a daily build iso of 13.10 development to upgrade my 13.04, since it was the first time i was doing an upgrade, i had in the back of my mind that worse case scenario i would re-do it as a clean install but it worked so well, i didn't need to...

If you use a daily build iso right now...and it works out for you, then as of next thursday, you would have a final release anyway (with the updates you will get between now and then)...
so, optionally, you could go ahead and upgrade using the iso right now..if you want to try...

I got into development several months ago and in fact when 13.10's final iso is released next week i am actually going to try upgrading my current 13.10 again, so that i clear out a lot of stuff that accumulated over several months of massive updating (lol) on development...yes...believe it or not you can upgrade an already done upgrade on the SAME version...the option is offered in the installer!
If i pop in a daily build (or the final iso next week) of 13.10, it gives me the option of UPGRADING my 13.10 to Saucy Salamander (13.10) again...so it will clear out all the previous stuff and make it more like a fresh install...

I'm prepared to do a clean install of 13.10 final if things get messed up...but it will be interesting to see what will happen :D

My personal plan is once i get 13.10 final installed (by upgrading or clean install if needed) then... rather then roll from one development version to the next one, i will upgrade each final version of ubuntu and roll with it that way instead...;)

---

### Post by Chelidze on 2013-10-10
> **craig10x said:**
> Actually, 13.10 will be final released next thursday (17th) so you burn that iso and upgrade to 13.10 at that time...if you have problems, you can always do a clean install of it after that...
When i used a daily build iso of 13.10 development to upgrade my 13.04, since it was the first time i was doing an upgrade, i had in the back of my mind that worse case scenario i would re-do it as a clean install but it worked so well, i didn't need to...

If you use a daily build iso right now...and it works out for you, then as of next thursday, you would have a final release anyway (with the updates you will get between now and then)...
so, optionally, you could go ahead and upgrade using the iso right now..if you want to try...

I got into development several months ago and in fact when 13.10's final iso is released next week i am actually going to try upgrading my current 13.10 again, so that i clear out a lot of stuff that accumulated over several months of massive updating (lol) on development...yes...believe it or not you can upgrade an already done upgrade on the SAME version...the option is offered in the installer!
If i pop in a daily build (or the final iso next week) of 13.10, it gives me the option of UPGRADING my 13.10 to Saucy Salamander (13.10) again...so it will clear out all the previous stuff and make it more like a fresh install...

I'm prepared to do a clean install of 13.10 final if things get messed up...but it will be interesting to see what will happen :D

My personal plan is once i get 13.10 final installed (by upgrading or clean install if needed) then... rather then roll from one development version to the next one, i will upgrade each final version of ubuntu and roll with it that way instead...;)

Thank you for the information and your help, I finally managed to get it to work, so far not much to complain except that I am still using 3.8 kernel

---

### Post by craig10x on 2013-10-10
Very Good :) and you are welcome...
Saucy is using the 3.11 kernel...someone may be able to help you with that...

---

