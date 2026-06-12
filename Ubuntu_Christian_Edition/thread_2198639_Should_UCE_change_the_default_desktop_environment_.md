---
title: "Should UCE change the default desktop environment or shell?"
date: 2014-01-09
forum: Ubuntu Christian Edition
---

### Post by ronbu on 2014-01-09
I would like to see Ubuntu Christian Edition 14.04 based on Ubuntu GNOME, if Ubuntu GNOME is able to offer a LTS release.  I would like to see support for both GNOME shell and GNOME fallback.  GNOME shell is supported by 8 of the 11 distros that are defined as major on distrowatch.com.  Unity is available in installer form only on Ubuntu and distros based on it.

In the 2013 linuxjournal.com Readers' Choice Awards, GNOME 3 was the choice of more readers than Unity, and Cinnamon and any other DE except for KDE.  The three options based on GNOME 3 combined had more votes than KDE.  In the 2012 linuxquestions.org Members' Choice Awards, GNOME shell was the choice of more members than Unity and Cinnamon.  GNOME shell got 12.88% of the vote and that poll, and the reason it wasn't higher is due to the unusually high percentage of Slackware users that use linuxquestions.org.  Slackware doesn't have an officially supported GNOME version available.

In my experience, I found that GNOME shell is a fast way to open up applications, faster than looking in a menu.  However, I respect those who prefer the traditional menu.  Also there is criticism over the Unity in Ubuntu 12.10 and newer sending queries in the Unity home lens to productsearch.ubuntu.com which some believe is a violation of privacy.

I would like your input on what you think should be the default DE or shell in UCE?

---

### Post by ronbu on 2014-01-17
Lately, I have been taking a liking to GNOME Classic mode.  In that mode I can use keyboard shortcuts to open some applications and use the super key for those shortcuts.  I did install Ubuntu CE on a laptop and I have been converting a Ubuntu 12.04.3 install on a desktop to Ubuntu CE.  It's working well so far.

---

### Post by ronbu on 2014-01-22
I went back to GNOME shell, after keyboard shortcuts were often failing to work on GNOME classic.  I've switched to Evolution as my email client on the laptop because of its better integration with GNOME.  I favor using GNOME apps with the exception that I like to browse with Firefox and use Libreoffice for writing and the spreadsheet.

---

### Post by jonathonblake on 2014-01-31
My preference is either KDE or XCFE desktop manager.

jonathon

---

### Post by ronbu on 2014-02-28
I am considering other possible desktop environment choices due to GNOME making Nautilus (Files) too minimalistic in GNOME 3.6 and higher along with issues with a new GNOME version breaking extensions.   Some other possibilities.  Cinnamon - Would work very well with a distro based on Linux Mint.  I had to use the terminal to get touchpad tapping to work in the Ubuntu edition.  Tapping became disabled after waking up from suspend.  I also couldn't get screen lock to work.  Would be an excellent choice if it could be made to work well in Ubuntu. MATE -  Works well in Linux Mint.  I needed to use synclient in the terminal to get touchpad tapping to work, touchpad tapping failed again after waking from suspend. KDE - Full featured desktop environment but heavy on the resources with many different default apps.  Nevertheless first known Christian distro, the now defunct "Ichthux" used KDE.  I will be testing Xfce today.

---

### Post by ronbu on 2014-03-13
I tested XFCE.  Tapping with touchpad is enabled out of the box.  Only problem is that thunar and some terminal commands is getting an error message when accessing an encrypted home directory.  This only occurs when logging out and logging back in without rebooting.  Unmounting .gvfs solves the problem.  This problem does not occurs when using other file managers.  Also, the sleep button(s) does not work out of the box.  I needed to make a shell script to get it to work along with screen lock.  This is how it would work with upower enabled.

#!/bin/sh
#
# screensaver-lock and suspend to RAM.
/usr/bin/xscreensaver-command -lock
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend

If, pmutils is being used for suspend on Ubuntu 14.04, a different script would have to be used.  I plan to install Xubuntu 14.04 beta on a USB hard drive to test Testy Tahr.  I also would like to install Linux Mint 16 on that same hard drive to test Cinnamon and Mate on LM.  I have also worked with LXDE. There is already a Christian distro which is based on Lubuntu, but it has 32 bit only.   I have tried Enlightenment, it does have plenty of power for it's size, but the default behaviors in regard to focusing windows and closing them are different than the most popular desktop environments.  So, XFCE which finished second to KDE in the 2013 Members Choice awards is currently my favorite choice for desktop environment for UCE 14.04.  However, the Ubuntu Mate repository had Mate 1.6.  The latest is Mate 1.8 which I would like to test on Xubuntu 14.04 after that is on the Ubuntu Mate repository.

---

### Post by ronbu on 2014-03-14
I was able to get touchpad click to work in both Cinnamon and Mate by changing the system settings.   The problem of screen lock not working when waking from suspend in Cinnamon on Ubuntu 12.04 is a known issue.  Mate has now emerged as my favorite choice for a default desktop for the next UCE, although the name might have to be changed if all the components of stock Ubuntu 14.04 are not on the ISO.  I give MATE the edge over XFCE due to a more pleasing default look.

---

### Post by ronbu on 2014-03-14
I have canceled plans to install Xubuntu 14.04 beta and Linux Mint 16, because I do not want to take the extra time to configure and update two extra installs.  The developers can install Ubuntu 14.04 to test Unity, and any other desktop environment that is being considered for inclusion in UCE 14.04.    I would prefer the Cinnamon desktop if screen lock could be made to work when suspending to RAM or disk.  Otherwise, I prefer Mate with UCE.  Although, either desktop shell would work well in a Christian distro based on Linux Mint.

---

### Post by Steve_and_Becky on 2014-04-22
I know I am late getting in on this topic, but I just wanted to put my 2  cents worth in.  I am a pretty new user to Linux.  I have played with  KDE on UCE 12.04, Unity on UCE 12.04, Gnome on UCE 12.04 and Xfce on UCE  12.04.  Xfce has  been the easiest one for me to work with and change appearances to suit  the way that I wanted it to work for me.  Unity was impossible for me to  change.  I didn't like having the menu on top in Gnome and never could  figure out how to get it to move to the bottom.  I was able to get the  menu to move to the bottom on KDE, but it was a pain to get KDE to apply  the themes that I wanted it to apply.  Xfce doesn't apply my favorite  desktop theme perfectly, but it comes the closest to what I want and I  love it.  I am also able to move the panels to where Iwant far more  easily than what I was able to in any other one.  There is an added  bonus--we have really old computers around here.  Our old computers run  the fastest with Xfce.  So, for me, Xfce is the what  I would like to  see.

Becky

---

### Post by Scott_Howison on 2014-06-25
Hello! I just want to throw in my vote for an Ubuntu GNOME CE 14.04. That would be awesome!

---

### Post by ronbu on 2015-03-28
My new favorite is now the Trinity Desktop Environment which is a fork of KDE 3.  The user can make it look like KDE 3, KDE 2 or Windows 7 classic mode.  I have it on Kubuntu 14.04 and on Debian wheezy.  It works especially well on Debian wheezy.  But, I don't know if UCE will ever have enough man power to have another version.  Although, they would have to change their name if they don't ship Unity.

---

### Post by bcschmerker on 2015-03-28
Based on now-aborted (as of 27 March 2015) tests on an eMachines®/Acer® EL1210-09 (I never got the nVIDIA® C77 planar GPU in the nForce® 780 and the GT218 in any of three half-height video cards to cooperate under the X.org Nouveau drivers, and the nVIDIA® 3xx driver set proved unusable due a no-login-screen KSOD issue), I am recommending UbuntuGNOME® as the baseline for Ubuntu® Christian Edition™.  The clincher was the behavior of OpenLP® in the GNOME™ desktop environment.

---

### Post by ronbu on 2015-04-09
> **bcschmerker said:**
> Based on now-aborted (as of 27 March 2015) tests on an eMachines®/Acer® EL1210-09 (I never got the nVIDIA® C77 planar GPU in the nForce® 780 and the GT218 in any of three half-height video cards to cooperate under the X.org Nouveau drivers, and the nVIDIA® 3xx driver set proved unusable due a no-login-screen KSOD issue), I am recommending UbuntuGNOME® as the baseline for Ubuntu® Christian Edition™.  The clincher was the behavior of OpenLP® in the GNOME™ desktop environment.

I reinstalled UCE on two computers, and installed Ubuntu GNOME 14.04 on a USB hard drive.  GNOME is working very well for me.  If, the version of Nautilus (Files) in GNOME 3.10 and higher is not adequate for the user, the user has the option of installing Nemo which is a file manager which has the functionality of Nautilus in GNOME 3.4.

I tried Trinity Desktop Environment on an Ubuntu 14.04 base.  The kwifimanager included failed to save my wireless password.  The user would have to switch to a different network manager if using wireless.  It is more lightweight than GNOME and KDE 4, but it's software doesn't have the full functionality of it's KDE 4 counterparts.  

I've heard good reports of recent versions of Cinnamon, but if the UCE developers switch to Cinnamon, it might as well be based on Linux Mint (the developers of Cinnamon) and be required to change the name of UCE and move to a different forum.

So therefore, I switch my vote to GNOME, and because of the five year support period of Ubuntu 12.04, the 14.04 can be skipped and I would like a version of UCE based on Ubuntu GNOME 16.04 LTS.

---

### Post by stlsaint on 2015-04-13
Noted.

---

### Post by ronbu on 2015-04-15
Ubuntu has recently solved the one key reservation I had about Unity, and that is starting with Ubuntu 15.04, the sending of search data from the Unity Lens to Amazon has been changed to an opt-in feature.  Therefore, I would now go along with a potential future UCE 16.04 release including Unity, and being based on standard Ubuntu.  It should also have GNOME Classic available.  I have been testing Ubuntu GNOME 15.04 and I have added the package "classicmenu-indicator" which brings in GNOME Classic.

---

### Post by ronbu on 2015-04-16
After installing and testing Unity in 15.04 Vivid Vervet, I still had to opt-out to avoid sending search results to Amazon.  The default Unity version in 15.04 is 7.3.2.  There is also Unity 8 available in the vivid repository.  When I tried that, I could get only the phone version to load, and I couldn't get it to work on the desktop and laptop.  Even though Ubuntu GNOME's support period for the last LTS was only three years, I now prefer to use GNOME which is a little lighter weight than Unity.  The extra features of Unity, I do not need.  Although, another UCE iso next year which includes both GNOME and Unity would be great with me.  Those who want a lighter desktop in a Christian distro have ShepherdsPup based on Puppy Linux, and C4C Lubuntu ReSpin available.

---

