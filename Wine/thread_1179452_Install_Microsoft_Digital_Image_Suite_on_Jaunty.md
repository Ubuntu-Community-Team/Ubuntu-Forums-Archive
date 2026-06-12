---
title: "Install Microsoft Digital Image Suite on Jaunty"
date: 2009-06-05
forum: Wine
---

### Post by brynellis on 2009-06-05
I've finally managed to get rid of our Windows XP machine at home much to the disgust of my wife!  I've gradually convinced her that she can do everything she needs to do on a Linux machine!  However, there is one thing she used on Windows that I'd like to get working on Linux using WINE if possible - Microsoft Digital Image Suite 10 (lets call is MDIS from now on!).

I have installed and configured WINE and have Newsleecher running fine on there so I'm fairly confident WINE is working.

The problem I have is when I run the setup.exe of MDIS it obviously installs a specific version of MDAC required for the program to work.  It seems to do this, but then gives a message saying "MDAC has been installed successfully but the system requires a reboot.  Reboot the system and run the setup.exe again to continue installation" or words to that effect.  When I click OK it starts the process all over again - installs the MDAC (which takes about 2 secs) and then comes up with the reboot message again.  The only way I can stop this message coming up is to eject the MDIS installation CD.

I fear that I'm not going to be able to get MDIS to install on WINE but if anyone has any ideas I dearly love to know them.

I've shown my wife how to do cropping of photos using GIMP but she is so used to using MDIS I'd like to get it working if possible.

HELP! ):P
Bryn

---

### Post by NightMKoder on 2009-06-05
I think winetricks can install mdac. I don't know what version you need though, so try starting with the highest:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by NightMKoder on 2009-06-05
I think winetricks can install mdac. I don't know what version you need though, so try starting with the highest:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

EDIT: Oops, good job me for double posting -_-

---

### Post by ad_267 on 2009-06-05
What about trying something like digikam? I think that's pretty similar to what MDIS does.

Also F-Spot which comes by default is pretty good.

---

### Post by brynellis on 2009-06-06
Thanks NightMKoder.  Have winetricks and MDAC.  Not getting the message about MDAC and reboot messages now when trying to install MDIS but not getting anything else either.  I'll give it 10 - 20 minutes because Newleecher takes that long to startup under WINE so maybe I'll experience the same thing here.  Here's hoping.

Thanks again.

---

### Post by brynellis on 2009-06-08
Damn!  No joy! :(  MDIS appears as an app in the WINE menu now but when I click on it nothing happens.  It's even set up a .desktop link which has the proper MDIS icon associated but double clicking on that does nothing either.

Hmm, I'm going to have a play around but so far I'm not holding out much hope.

I appreciate the help so far guys/gals as I wouldn't have got this far.  Any other ideas?

Bryn

---

