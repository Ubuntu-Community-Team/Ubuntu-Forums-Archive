---
title: "Feisty/Gutsy/Hardy Quick Guide (including multimedia playback)"
date: 2007-10-04
forum: Ubuntu Customization Guide
---

### Post by ubuntu_demon on 2007-10-04
[B]I'm posting this as a forum user and not as a staff member. This is all on your own risk.

Legal Notice :[/B] Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country.

This HOWTO focuses on the most common customizations (including multimedia playback) suitable for average users.

There is a good reason why Ubuntu doesn't include better multimedia support on default. 

[I]Some file formats are proprietary, which means that they are owned by a company or other organisation. Sometimes, the owners of such formats charge licensing fees or impose legal restrictions on the use of their formats. This means that people may be unable to use or distribute these formats without first paying a fee or applying for a license.

A Free or open format is one which can be used by anyone, free of legal restrictions on how they use the format. Free formats are very popular - the World Wide Web is based on the open HTML standard. Ubuntu supports many free formats and the open-source community as a whole encorages their wider use. [/I]

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

First you might want to install the following packages to make most multimedia work by entering the following command. Explanation about the packages : ubuntu-restricted-extras contains most non-free formats you will ever need. vlc is a videoplayer you can try if some video won't play with the default video player (totem). gstreamer0.10-pitfdll is another codec (which gets installed by ubuntu-restricted-extras in Hardy). Kubuntu users should use kubuntu-restricted-extras instead. Xubuntu users should use xubuntu-restricted-extras instead.

```

sudo aptitude install vlc ubuntu-restricted-extras gstreamer0.10-pitfdll

```

If you have problems with flash and sound (for example sound problems with youtube) try restarting your browser. If that doesn't work you might want to try to remove or install the package libflash-mozplugin and restart your browser once again.

If watching streaming (non-flash) video's on a website doesn't work you could try the MediaPlayerConnectivity plugin to watch the video with an external application (vlc) :
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
(you might need to remove the package totem-mozilla)

If you want newer versions of certain software you can optionally enable backports in system->administration->software sources or by editting your /etc/apt/sources.list :
```

sudo gedit /etc/apt/sources.list

```

Uncomment the line which looks somewhat like this :
```

#deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```

For more information about backports :
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

If you are not satisfied with totem and vlc then you might want to use mplayer (sudo aptitude install mplayer) with w32codecs ( or ppccodecs or w64codecs if you use one of those architectures) but these packages come **from Medibuntu which is an unofficial repository which is less safe so only do this if you understand what you are doing and if you really really need it**. More information : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you need dvd playback you need libdvdcss2 **from Medibuntu which is an unofficial repository which is less safe so only do this if you understand what you are doing and if you really really need it**. More information : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Here's more information about using multimedia :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

Here's a guide which is a little bit similar to this one. I didn't try it.
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

Here's more Ubuntu documentation :
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/HowToGetHelp](https://help.ubuntu.com/community/HowToGetHelp)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Some more links for beginners in here (information is a bit old) :
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

**I'm posting this as a forum user and not as a staff member. This is all on your own risk.**

---

### Post by anonymous_x on 2007-11-12
Thnx Demon. . . .
The Links were helpful. . .I really appreciate!

---

### Post by ubuntu_demon on 2007-11-14
> **anonymous_x said:**
> Thnx Demon. . . .
The Links were helpful. . .I really appreciate!
You are welcome :)

---

### Post by Berean on 2008-01-23
Thanks very much for you informative post.  I installed today (Gutsy Gibbon) and am much better armed now I've your suggestions.  Once again, Thank you.

---

### Post by Frak on 2008-03-19
Thanks for the post demon. It's nice to know that new users can easily have their system work with a few clicks, and seasoned users can still choose what goes into it (with a little help in this case) :)

---

### Post by Kopachris on 2008-12-11
Okay, so just to be safe, I shouldn't include the restricted extras in a distro, right?  Could I have a check box in the installer to download and install the restricted extras *after* installation?  Maybe I should simply have the main help page (with a link to the "common addons" page) pop up when you start up for the first time after install, just to be safe?  I'm in the USA, but I want to be wary of other countries at the same time.

---

