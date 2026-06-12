---
title: "Report on Serval Performance 3, Hardy Heron 64bit clean, and Skype."
date: 2008-05-18
forum: System76 Support
---

### Post by jdmelton on 2008-05-18
I just finished a clean install of Ubuntu 8.04 on my Serval P3 and was very pleased with the results so far. It was painless until I tried to install Skype. I want to share my experience in case it can help someone else.

System is a System 76 Serval P3 with 2 GB ram, Intel Core 2 Duo T7100 1.8 GHz that was purchased new in December 2007 with 32 bit Ubuntu 7.10 Gutsy Gibbon installed.
Also equipped with Bluetooth, Wireless 802.11 abg, and a 2.0 Mega Pixel webcam. It also has a finger-print scanner that did not work (as stated by System 76 when I ordered it.)

I started 3 threads about it.
[http://ubuntuforums.org/showthread.php?t=646987](http://ubuntuforums.org/showthread.php?t=646987)
[http://ubuntuforums.org/showthread.php?t=652490](http://ubuntuforums.org/showthread.php?t=652490)
[http://ubuntuforums.org/showthread.php?t=675647](http://ubuntuforums.org/showthread.php?t=675647)


Tested Ubuntu 8.04 LTS (Hardy Heron) using iso image ubuntu-8.04-desktop-amd64.iso.
Ethernet, wireless, sound, usb, and the web camera worked. (I installed Cheese to test the camera.)
The Live CD looked good, and posts on System 76 forum were generally favorable, so I decided to perform a fresh install.
I did not upgrade, I did a fresh install, and used guided partitioning for the whole disk.

Here are the major steps.

1. Installed Ubuntu 8.04 LTS (Hardy Heron) using iso image ubuntu-8.04-desktop-amd64.iso.

2. Installed updates and rebooted.

3. Installed System 76 driver from the Internet, went to System -> Administration -> System76 Driver, selected Install Drivers, then rebooted.

4. Tried to install Skype from their website but received an error message about wrong architecture (32 bit vs 64 bit).

Found: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295), and post #304 states that Medibuntu has 64 bit Skype.
Went to: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and installed the repository per the instructions there.
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Then I went to Synaptic Manager and installed Skype (the 32 bit libraries were installed as dependencies).

Skype started up from Applications -> Internet -> Skype.
The camera and speakers worked. However, the built-in microphone did not work.

Found: [http://ubuntuforums.org/showthread.php?t=750647](http://ubuntuforums.org/showthread.php?t=750647)

Tested various settings and found:
- a. Set System -> Preferences -> Sound as thomasaaron wrote in Post #5 here [http://ubuntuforums.org/showthread.php?t=750647](http://ubuntuforums.org/showthread.php?t=750647).
- b. Right-click speaker in upper right of upper panel (near Date/Time) and open volume control.
- c. Go to Edit -> Preferences to call up Volume Control Preferences and select all the available tracks to be visible then close.
- d. I then get 4 tabs labeled  Playback, Recording, Switches, and Options.
- e. On Options, I have two Input Source selections. I set the one to Front Mic and the other one to Mic since I use both the built-in (Front Mic) and the headset jack (Mic).
- f. On Switches, I do not select either Caller Id or Off-Hook.
- g. On Recording, I have Capture, Capture 1, and Digital. I set all of their sliders to half (middle). I make sure none of the little speaker or microphone images have a red X in them.
- h. On Playback, I set Front Mic and Mic boosts to half. I set Headphone, PCM, and Front up all the way (top). I set Master to a comfortable level.

Recap -- On my Serval P3, Front Mic is the built-in microphone, Mic is the jack on the front left which I call the headset jacks.

The microphones work now.

I hope this is useful to someone.

---

### Post by jeamer on 2008-05-18
Just to clear up... you got everything working? 

If it is helpful to anyone else, I found all the same threads as above and got Skype to work on a Pangolin with similar specs. The settings above work perfectly (minus the mic quality, but thats OK). 

Thanks for posting the steps, its funny that independently we found the exact same process through multiple threads.

---

### Post by jdmelton on 2008-05-20
> **jeamer said:**
> Just to clear up... you got everything working? 

If it is helpful to anyone else, I found all the same threads as above and got Skype to work on a Pangolin with similar specs. The settings above work perfectly (minus the mic quality, but thats OK). 

Thanks for posting the steps, its funny that independently we found the exact same process through multiple threads.

jeamer,

Yes, everything is working...except the fingerprint scanner. Then again, I have never tried the fingerprint scanner!

I still have the occasional hang when I boot where the BIOS flash screen shows but Grub does not process. I do not believe this problem is related to Ubuntu, System 76, or Linux in general. I firmly believe it is a chipset initialization issue, based on many years of embedded systems work. When Grub does not process, the screen is blank with just a blinking cursor in the upper right hand corner. That is typical of a cleared screen and no further writes to the screen. I have seen this in embedded systems. A CTRL+ALT+DEL key sequence on my Serval triggers the reset and the computer boots properly afterwards.

It 'seems' that my Serval is faster with 64bit 8.04.

---

### Post by ssalter on 2008-08-07
Thank you jdmelton - I just tried to download Skype and got exactly that error message, so did a search and found your very useful post.

ssalter

---

