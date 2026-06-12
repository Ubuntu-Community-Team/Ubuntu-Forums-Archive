---
title: "Ubuntu 16.04  64 bit - which one ?"
date: 2016-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Tim036 on 2016-04-17
I use 14.04 also 15.04 and 15.10

But their capability seems to be decaying....

Some web sites demand the latest Adobe Flash player to be available.... or suitable compatible substitute..

Also Codecs which make it possible to listen to music or what DVDs which I already own are impossible to watch...
Fixes which don't work seem readily available....
Several different versions of 16.04 are due over the next 8 weeks or so but which ones do what ?

I ask this question because Ubuntu has been brilliant for me over the last 4 or 5 years and I just want to return to that state...

I'd prefer to be able to pick one that is as good as 14.04 was !  Rather than waste a lot of time evaulating several OS's that won't meet my needs !

Any thoughts or pointers would be greatly appreciated !

A nervous,

Tim

---

### Post by him610 on 2016-04-17
Hello Tim036.
I don't know if you have a real problem, or you are just opening this thread for a discussion (in case it will probably get moved.)

The release of LTS 16.04 in any one of the flavors - Ubuntu, Xubuntu, Lubuntu, etc. will all be similar to each one's predecessor release, but each will have improvements in capabilities. If you were happy with Ubuntu 14.04 then you should be happy with Ubuntu 16.04, and likewise for Xubuntu, Lubuntu, and Kubuntu. Some folks recommend waiting for six months or so after the initial release for any unforeseen problems to surface and be rectified, but I have been using the latest 16.04 beta versions of both Ubuntu and Xubuntu and have experienced no problems whatsoever.

To paraphrase Parkinson, "Software expands to fill the capabilities of the operating system and hardware."

---

### Post by grahammechanical on 2016-04-17
> Some web sites demand the latest Adobe Flash player to be available.... or suitable compatible substitute..

Adobe Flash Player is proprietary software. It cannot be installed on Ubuntu as it is not in the Ubuntu software repositories. But we can install an installer application (flashplugin-installer) that will itself install Adobe Flash Player. But there is one little problem. Adobe stopped developing Adobe flash player for Linux years ago.

This matter is not the capacity of Ubuntu degrading over time. In my case I use Google Chrome when I need to view online videos such as those at Ubuntu On Air. Or play music videos online.

This situation will not change with the release of 16.04. I know because I have been using the development version of 16.04 for months. This situation will only change when web designers stop using Adobe Flash Player and convert to HMTL5 video format for playing videos. 

Regards.

---

### Post by QLee on 2016-04-17
> **Tim036 said:**
> 
Any thoughts or pointers would be greatly appreciated !

I'm using 14.04 and I can listen to music and play DVD's, how is this not working for you?

As to Flash, there is a plugin available from an Ubuntu Partner repository.
> QLee@Atlas:~$ apt-cache policy adobe-flashplugin
adobe-flashplugin:
  Installed: 1:20160407.1-0ubuntu0.14.04.1
  Candidate: 1:20160407.1-0ubuntu0.14.04.1
  Version table:
 *** 1:20160407.1-0ubuntu0.14.04.1 0
        500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner i386 Packages
        100 /var/lib/dpkg/status


---

### Post by slickymaster on 2016-04-17
Not a support request.

*Moved to the ***Ubuntu, Linux and OS Chat*** sub-forum*

---

### Post by Rocky_Bennett on 2016-04-17
> **QLee said:**
> I'm using 14.04 and I can listen to music and play DVD's, how is this not working for you?

As to Flash, there is a plugin available from an Ubuntu Partner repository.




Exactly my thoughts. Ubuntu 14.04 has not changed recently, the installed OS still has the same features and capabilities today that it had last year. Maybe the OP is experiencing hardware issues.

---

### Post by Tim036 on 2016-04-17
> **Rocky_Bennett said:**
> Exactly my thoughts. Ubuntu 14.04 has not changed recently, the installed OS still has the same features and capabilities today that it had last year. Maybe the OP is experiencing hardware issues.

Yes 14.04 is fine on all front apart from Adobe flash. But the fix is impossible with with the www sites that using only the very latest version.

Its only a few days to go for 16.04 so I'll try the first version and see how it goes....

Many thanks for all those who have responded....

:  )))

Tim

---

### Post by kansasnoob on 2016-04-17
If properly installed flash in ubuntu should be up to 11.2.202.616:

> **flashplugin-nonfree** (11.2.202.616ubuntu0.14.04.1) trusty-security; urgency=medium

  * New upstream release 11.2.202.616
    - debian/flashplugin-installer.{config,postinst},
      debian/post-download-hook: Updated version and sha256sum

 -- Chris Coulson <chris.coulson@canonical.com>  Thu, 07 Apr 2016 11:55:21 +0100


Some sites such as Crackle complain about flash being out of date because they only think in Windows world mode :( In those cases I use Chrome browser which uses its own version of flash.

To play Hulu videos in Firefox I have to add the package 'hal':

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

You'll notice there that I mention two other possibilities for streaming videos in Ubuntu.

---

### Post by Tim036 on 2016-04-17
> **kansasnoob said:**
> If properly installed flash in ubuntu should be up to 11.2.202.616:



Some sites such as Crackle complain about flash being out of date because they only think in Windows world mode :( In those cases I use Chrome browser which uses its own version of flash.

To play Hulu videos in Firefox I have to add the package 'hal':

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

You'll notice there that I mention two other possibilities for streaming videos in Ubuntu.

I downloaded this:-

flashplugin-installer_11.2.202.616ubuntu1_amd64.deb

and clicked on it, and Ubuntu Software Centre came up then locked up with :-

flasgplugin-nonfree-extrasound:i386 saying 'Applying changes' but doing nothing

and

'Flashplugin-installer' saying 'Waiting' but al doing nothing...

so I think I'm lost....

:  (

Tim

---

### Post by mastablasta on 2016-04-18
well now we know why things don't work as they should :P
2 options:
1. use the repository to install the flash (or use restricted extras package which comes with all sorts of codecs + flash). same goes for DVD. you may need to enable nonfree repositories and install a package. search official documentation for more info:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

2. for flash you have another option to get the latest version. you will need to install google chrome (or chromium and add pepper flash to it). [http://askubuntu.com/questions/510056/how-to-install-google-chrome](http://askubuntu.com/questions/510056/how-to-install-google-chrome)

the really new sites should use HTML5 not Flash that is no longer supported on less and less appliances.

---

### Post by sammiev on 2016-04-18
Pepperflash works great in Firefox without adding Chrome.

See [here]("http://ubuntuhandbook.org/index.php/2015/10/ipepper-flash-for-firefox-ubuntu-15-10/").

---

### Post by Tim036 on 2016-04-20
> **mastablasta said:**
> well now we know why things don't work as they should :P
2 options:
1. use the repository to install the flash (or use restricted extras package which comes with all sorts of codecs + flash). same goes for DVD. you may need to enable nonfree repositories and install a package. search official documentation for more info:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

2. for flash you have another option to get the latest version. you will need to install google chrome (or chromium and add pepper flash to it). [http://askubuntu.com/questions/510056/how-to-install-google-chrome](http://askubuntu.com/questions/510056/how-to-install-google-chrome)

the really new sites should use HTML5 not Flash that is no longer supported on less and less appliances.

Wow !  That sheds some light on the problem !

I woke up 'Ubuntu Software Centre'    and found just using 'pepperflash' and rebooting, Firefox behaved it self !

A brilliant 'nugget of gold' !!!!

Thank you so much for helping me on this, I would never have got there on my own !!!  Big Cheer for the Forum !!

:P:P:P

Tim

---

