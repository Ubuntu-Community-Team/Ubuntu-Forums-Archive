---
title: "UbuntuStudio installation fails @ ttf-mscorefonts-installer"
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by eeter on 2009-11-04
As it turned out the installation of UbuntuStudio Karmic does not lead to a fully functional system.

Installation fails at 
Selecting and Installing Software
ttf-mscorefonts-installer

And also when installing GRUB it fails :S 

I'm sorry but after half an hour I couldn't find the right place where to post this error or bug in Launchpad and I'm reeaaallly tired already of this last ruined month (nearly 0 productivity and most of the time trying to get things working properly - I'm holding myself back today not to smash my computer against the wall).

And why on earth the installer is still like the old one :confused: I really enjoyed the Ubuntu installer.

---

### Post by AutoStatic on 2009-11-04
> **eeter said:**
> Installation fails at 
Selecting and Installing Software
ttf-mscorefonts-installer
You have to retry installing it. The ttf-mscorefonts-installer downloads the cab files with the fonts from a Sourceforge mirror and sometimes this mirror is too slow or simply down. This causes the installation to fail.

> **eeter said:**
> And also when installing GRUB it fails :S I know close to nothing about Grub2 so can't help you on that one.

---

### Post by eeter on 2009-11-04
But at this point where I have a unbootable system on my hard drive  I don't know how to proceed.. :(

---

### Post by jeebustrain on 2009-11-04
boot back to the CD and try again? I had vid card issues when I was installing and ended up having to go through the install like 4 times before I got it right.

---

### Post by eeter on 2009-11-04
> **jeebustrain said:**
> boot back to the CD and try again? I had vid card issues when I was installing and ended up having to go through the install like 4 times before I got it right.

It has been 3 times for me already and I really do not believe in this any more. I could waste all my life trying it again and again... It s just not working right.

---

### Post by AutoStatic on 2009-11-04
> **eeter said:**
> But at this point where I have a unbootable system on my hard drive  I don't know how to proceed.. :(Any error messages? What happens when you boot your PC without the LiveCD? Is Grub not installed at all?

---

### Post by eeter on 2009-11-04
It didn't install GRUB because the installation does not complete when ttf-mscorefonts-install fails. Strangely...
But I finally managed to get it done.
On the installation start-screen I pressed F6 and selected "Only free software" and it helped.

Thanks for your help anyway guys!

---

### Post by AutoStatic on 2009-11-04
Ah, I didn't know Ubuntu Studio installs the MS fonts by default, my bad. I never install Ubuntu Studio, I always start with a vanilla install and take off from there. So it failed during installation. I would consider this a bug since the MS font installer depends on a working internet connection. So if you don't have internet the installation fails, doesn't seem right to me. But good that it works now.

---

### Post by dummy910 on 2009-11-04
I had a the similar problem(tt-mscore fonts thing) last week when a friend upgraded a 9.04 studio box to 9.10. It ended up being a combo of **ubuntustudio-audio** and **ubuntustudio-desktop** that got borked when the user did the upgrade(not paying attention to questions more than likely). 

Your case being a tad different in that you can't even boot to the desktop,,, see if you can boot into a recover-mode "console", and _having an internet connection_, type the following into the terminal:
```
sudo apt-get install ubuntustudio-audio
```
then
```
sudo apt-get install ubuntustudio-desktop --fix-missing
```
then
reboot into normal mode.

---

### Post by tneijsel on 2009-11-05
This solution will not solve the problem in my case.

When I run the upgrade script te handler returns a bad address call at for example the first line:
[http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) wrong connection and/or cannot find host-address

my system is still not fully functional after the upgrade from ubuntu 9.01 to 9.10

---

### Post by jonathank89 on 2009-11-06
I posted a new thread with the fix for this:

[http://ubuntuforums.org/showthread.php?p=8262208#post8262208](http://ubuntuforums.org/showthread.php?p=8262208#post8262208)

---

### Post by Stochastic on 2009-11-07
Hmm, there looks to be a number of problems surrounding this package.  I'll admit this flew under the developers and tester's radar during this release.  Sorry.
[SIZE="3"]
[LIST]
[*]ttf-mscorefonts-installer is a "recommends" by wine
[*]wine is required by lmms-vst
[*]lmms-vst is a "recommends" by lmms
[*] lmms is required by ubuntustudio-audio[/LIST][/SIZE]
"recommends" are packages that are installed by default on a typical Ubuntu Studio (or Ubuntu) installation.  They are not required for the program to function, but may be key in certain features of the program.

[LIST]
[*]**New Installations**

 If you are installing Ubuntu Studio Karmic 9.10 without access to the internet (or without a wired internet connection) you will need to refrain from selecting the Audio Software package of software during the task selection step.  It is safe to select the Audio Plugins package if you would like.

 To get the audio software package installed after you're up and running
[LIST]
[*]**A)** If you're now connected to the internet
 Simply install the [ubuntustudio-audio]("apt:ubuntustudio-audio") package from your favorite package mangager.
[*]**B)** If you still don't have internet
 - You must turn off the default "recommends" installation. -
  In Synaptic Package Manager this option is in Settings -> Preferences -> General Tab -> Marking Changes Section  -> Second checkbox
 
 Then you can safely install [ubuntustudio-audio]("apt:ubuntustudio-audio") and [lmms-vst]("apt:lmms-vst") without the internet connection.

 Then you can turn "recommends" back on, but watch every package installation for ubuntustudio-audio, lmms, lmms-vst, or wine updates (but chances are you won't be doing many package installations without internet).
[/LIST]

[*]**Upgrades**
 If you have any troubles during the upgrade from 9.04 to 9.10 of Ubuntu Studio (or any Ubuntu install with the ubuntustudio-audio meta):
 Uninstall ubuntustudio-audio, lmms, lmms-vst, wine, ttf-mscorefonts-installer, and msttcorefonts manually.  Then proceed with the A) or B) options above for getting those programs back.
[/LIST]

---

### Post by prupert on 2010-04-06
I came across the same issue just yesterday - surely you should put a note about this on the webpage somewhere (or remove LMSS from the default install and make it an optional extra until the dependency issue is resolved)?

For most users, they will try to install, the install will fail and they will give up........

I also found that the install froze on the "Applying Users and Passwords Screen" - twice.....simply doing a hard reboot fixed it, but it was hardly a graceful install....

---

