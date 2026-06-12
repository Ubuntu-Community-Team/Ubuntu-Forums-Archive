---
title: "ATI propritary driver(s) and gtk-recordmydesktop/xvidcap/etc"
date: 2009-11-05
forum: System76 Support
---

### Post by ctsdownloads on 2009-11-05
This is actually for Tom or anyone who is familiar with ATI proprietary drivers and how they work with X.

I have tried using both the default ATI proprietary driver that comes with 9.10 and even went to the very latest from AMD's website (ati-driver-installer-9-10-x86.x86_64.run). Works fine, except for anything using screen capturing.

Using gtk-recordmydesktop, I am looking at this.

```
cat ~/gtk-recordMyDesktop-crash.log
#This is the command given at initialization:
recordmydesktop -o /home/matt/Desktop/save -fps 15 -channels 2 -freq 22050 -device pulse -v_quality 63 -s_quality 10 -workdir /tmp --overwrite 


#recordMyDesktop stderror output:
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:1024
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device pulse
Recording on device pulse is set to:
2 channels at 22050Hz
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
X Error: BadAccess (attempt to access private resource denied)
Bad Access on XGrabKey.
Shortcut already assigned.
Capturing!

```

```
dmesg | tail
[ 1375.021021] usb 1-4.2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 1422.076203] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000066
[ 1423.748629] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[ 1423.749039] [fglrx] Firegl kernel thread PID: 5008
[ 1425.223805] [fglrx] Gart USWC size:627 M.
[ 1425.223807] [fglrx] Gart cacheable size:247 M.
[ 1425.223811] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 1425.223813] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
[ 1425.223814] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[ 1425.917760] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
```

I receive the same general error with a single or dual monitor, 3D effects on or off. Also tested on a non-wide screen and wide screen monitor in single monitor mode.

Same applies for xvidcap, which just becomes unusably slow with the provided video drivers. Don't know where the log is, so here are the following output instead.

```
dmesg | tail
[ 1375.021021] usb 1-4.2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 1422.076203] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000066
[ 1423.748629] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[ 1423.749039] [fglrx] Firegl kernel thread PID: 5008
[ 1425.223805] [fglrx] Gart USWC size:627 M.
[ 1425.223807] [fglrx] Gart cacheable size:247 M.
[ 1425.223811] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 1425.223813] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
[ 1425.223814] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[ 1425.917760] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
```


Now I realize this is ATI, not Ubuntu at work here. It's a proprietary driver, hence the joys of dealing with what we get. But I do not have these issues with the proprietary NVIDIA drivers and my Intel chipset on my gav5 also works fine. Any thoughts? :)

---

### Post by thomasaaron on 2009-11-06
Man, I'm not all that familiar with it. But there are a number of interesting errors there.

Have you tried disabling desktop effects to see if it works. I'm not sure if the problem is between the ati driver and the recording software, or if it's between the ati driver, compiz, and the recording software.

---

### Post by ctsdownloads on 2009-11-06
> **thomasaaron said:**
> Man, I'm not all that familiar with it. But there are a number of interesting errors there.

Have you tried disabling desktop effects to see if it works. I'm not sure if the problem is between the ati driver and the recording software, or if it's between the ati driver, compiz, and the recording software.

Yeah I did that early on - along with other troubleshooting attempts (swapping out for different monitors, etc). I am leaning with the recording software not liking how the driver plays with X. That is what my gut tells me.

I broke Xserver a number of times during my troubleshooting, but that is an easy fix with a hardwire connection to the Internet and a quick xserver reinstall as it seems that "fixing" X is no longer an option in Ubuntu.

It looks like it's going to be an Intel world for using gtk-recordmydesktop. Either than or start using the latest release [webcamstudio]("http://www.ws4gl.org/home") .52 (coming out any day now) for my desktop recording. It's java, runs fine on any distro, version of X, drivers, it doesn't care - it just works like that. Also a great way to definitively test a webcam if it ever comes up. ;) THe current version .51a is cool, but the upcoming/yet to be released version does stuff that you cannot even do on OS X or Windows. :P

---

### Post by thomasaaron on 2009-11-06
You might try running the swat ati drivers to see if those do better...

Please run these commands from a terminal...
echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

---

### Post by ctsdownloads on 2009-11-06
> **thomasaaron said:**
> You might try running the swat ati drivers to see if those do better...

Please run these commands from a terminal...
echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade


Sweet, will do that. I ran two versions of the same ati-driver-installer animal (not swat though), but anything with the word swat in it has my vote for a test run! Heh.

Thanks Tom :D

---

### Post by ctsdownloads on 2009-11-06
Almost forgot to ask - can I run a direct upgrade or should I remove the old ATI driver first? Either way is cool, but I hate messing something up if I can avoid it by asking first.

---

### Post by thomasaaron on 2009-11-06
If you're running something from ATI's website, I'd remove it first. But if you're running something from the repos, go ahead and just run the commands.

---

### Post by ctsdownloads on 2009-11-29
Finally had a chance to try it - borked X. And "bullet proof X" saw fit to delete options for reconfiguring the xserver (plus GRUB missing recovery options too), so I just purged and reinstalled xserver. Not a huge deal for me I guess, but really poorly reflecting on ATI.

This and other issues have me leaning more than ever with upgrading to a NVIDIA card. The proprietary ATI drivers are just not there yet, unfortunately. 

What finally sold me on going NVIDIA once again was disabling a second monitor only to find it also borks X. That was my last straw - ATI is not for me. NVIDIA never did this - even with their worst driver releases.

Short of this, I am **loving** the rest of the computer. Runs like a champ. But for the love of Pete, make NVIDIA an option in the future. ;)

---

