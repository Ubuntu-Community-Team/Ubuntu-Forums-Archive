---
title: "Updating iPhone 3G software from 3.1.3 to 4.2 using WinXP on Virtualbox"
date: 2011-08-20
forum: Tutorials
---

### Post by mcdragon on 2011-08-20
Just wanted to record some of my experience with upgrading my iPhone's software and thought it might be useful.

I have not had a Windows system on either of my two machines for a few months now so I was reluctant to upgrade the software - also I was worried about possible slow responsiveness of iOS 4.2 on the iPhone 3G.

First I upgraded Virtualbox to the latest edition (4.1.2 at the moment) and also installed the latest Extension pack. The extension pack was necessary to support USB devices. Once installed go to the Settings for that specific VM (in my case it was a Windows XP VM), on the left menu select USB and then tick both "Enable USB Controller" and “Enable USB 2.0 (EHCI) Controller”, then start that VM. Once WinXP loaded you have to mount the USB device in the menu: Devices - USB Devices - Apple …
WinXP will (should) then recognize the iPhone.

Make sure everything is properly synced and backed-up. Its up to you, of course, to be sure.

Install or upgrade iTunes to the latest version and just follow the instructions on how to upgrade the software.

Here is where I encountered a problem. I kept on getting the error message: “The iPhone “iPhone” could not be restored. An unknown error occurred (1604)”. First I thought this was specific to Virtualbox and thought I have permanently bricked the phone as even if I disconnected the iPhone I kept getting the little image that instructed you to connect the phone to iTunes.

I did what was advised like switching off all other USB devices and connecting the USB device directly in the back of the PC - instead of in the front or using a USB hub.

Then I did two things at once. While iTunes tried to restore the phone it kept un-mounting the device from the system. I forced to mount it again twice - both times by using the Virtualbox menu: Devices - USB Devices - Apple …
The other thing I did was to use a different USB cable.

One or both of those things worked and I can’t check which one. In any case I have my iPhone back but that probably won’t stop me from getting an Android phone ASAP.

bye,
Martin

---

### Post by tycen on 2012-10-12
I know it's an old post - but thanks for posing that.  I had the same issue with Windows 7 in virtualbox.  All of my software was up-to-date.  I did not change cables or ports.  For me the fix was to keep making sure the ipod was mounted to the VM.  You're right, it unmounted about 2 times.  Thanks for the tip!

---

