---
title: "Need help w/Intel945/950 resolution issues running on VirtualBox - Gutsy -Screenshots"
date: 2007-10-21
forum: Virtualisation
---

### Post by RobotFriendly on 2007-10-21
Hello. First off, I'm a fresh user to ubuntu, and I am (almost) completely in love with it. I also know that many people have posted in the forums with similar issues with their Intel 945 chipsets and low resolutions, and while I have tried many of the things posted in those threads, I have had no luck. I will try to keep it as brief as possible. I have also taken a number of screen shots that hopefully might give a clue. 

One thing that baffles me is the resolution was fine when booting into the live cd, and I had all of the same resolution options that I do in Windows (up to 1024x768 ). I also get 1024x768 on the boot up and shut down screens, but as soon as I get to the login window, I am immediately scaled back to 800x600. 

The machine I'm using is a Thinkpad r60 w/1.5GB's ram, running WinXPSP2 as my primary OS, and I am loading Gutsy with innotek VirtualBox 1.5.2, which let me say was much easier to install under than Microsoft VirtualPC, in which I had keyboard/mouse issues. It installed easily under VirtualBox though. However, they both have the same resolution problem. Also, 7.10 runs great on VirtualBox, and all other drivers are working great (audio, wifi, etc). Here are the first couple of screenshots showing my VirtualBox config.
[ATTACH]47204[/ATTACH]
[ATTACH]47205[/ATTACH]

The next couple of screenshots show my video card details in XP.
[ATTACH]47207[/ATTACH]
[ATTACH]47208[/ATTACH]

Here are the steps I've taken to correct my issue, based on other posts in the forum. First I ran gksudo displayconfig -gtk. In there it had my driver set to a generic VESA driver, and my monitor was set to 'Plug and Play' with a max resolution of 800x600. While there is a lot of IBM monitors listed, I cannot find anything on my system that has a number that matches what is in that list. The closest I could find is the generic 'LCD Panel 1024x768'. I was however able to select my 945 chipset family from the Intel video driver list, and I could see that it was referencing the i810 driver. I ok'd out of everything at which point it told me that I needed to logout for the new changes to take effect. After logging out I was prompted with a message that told me Ubuntu is running in low graphics mode, and I have the option to configure, which takes me back to the standard Screen Resolution preferences window, which didn't reflect any of the changes that I had just made. 

The next option that I tried involved running sudo dpkg-reconfigure xserver-xorg (I also saw to try sudo dpkg-reconfigure -phigh xserver-xorg, and when I ran that it said that phigh wasn't installed). When asked if I wanted to auto-detect I said yes, and was immediately told that there was 'No X server known for your video hardware'. The next screen asked me to to select an X driver, which the first time I ran this I chose 'Intel' (after reading on another post later stating to try the i810 driver rather than the Intel one, I redid this process selecting that one as well, with the same results). The next screen asked for the Identifier of the video card. I wasn't sure what to put, so I put in verbatim what was listed in windows as the 'Adapter String', which was Mobile Intel(R) 945GM Express Chipset Family (on a later try, I used what was labeled in Windows as the 'Chip Type', which was Intel(R) GMS 950, with the same results). The next screen was for the Video card bus identifier, which it had correctly auto-detected at 0:2:0 (I verified in windows). When asked how much memory to allocate to it, I put in 131072 (128MB in kb's), which was equal to the amount of ram I allocated for it in VirtualBox. From this point on I accepted all defaults through the kb/mouse auto detection, until I got to the Monitor Detect section, where it detected it as 'Generic Monitor'. In this field I wasn't sure what to put in, and the only thing I could find in windows in regards to the monitor name was 'ThinkPad Display 1024x768', so that is what I put in here. I then selected 1024x768 as the max resolution and then selected medium on Method for selecting monitor screen, and then selected 1024x768 @ 60hz, as this is what it is set to in Windows. I selected a bit depth of 16 and wrote the configuration changes to file. I was then back to the normal terminal window letting me know that it had overwritten the file and made a backup of the original. 

At that point I did a reboot, and on the reboot, at first I got a 1024x768 splash screen like I had been getting all along, and then the following screen shot was displayed for a few seconds, before continuing to boot to the normal login screen.
[ATTACH]47209[/ATTACH]

After logging in, everything was the exact same as before, stuck at 800x600. At this point I am unsure where to go, and lack the knowledge to dig any deeper. 

Thank you in advance for reading my book-long message and for any ideas you might have to get me going.


Thanks a bunch,
Travis

---

### Post by daniel_szollosi-nagy on 2007-10-21
Hmmm, interesting.

If I read the above correctly you are running an Ubuntu guest on an XP host. Virtualbox emulates an entire different hardware from what your real hardware is. You are most likely only messing things up by forcing the Intel chipset for Ubuntu inside of Virtualbox. You should not need to install any drivers specific to your hardware, only drivers supplied by Virtualbox.

Don't think you need all that video memory either, as Compiz will probably not work under Virtualbox. The emulated video card is not a 3D card - 8 megs of video RAM should be plenty. The video RAM you set in Virtualbox comes out of your system memory, not your video card.

Make sure you install the Guest Additions (under the Devices menu of your virtual machine). I think it mounts a CD with the relevant drivers. (I've only ran XP inside Virtualbox, so I can't be any more precise on how it behaves with an Ubuntu guest)

Hope this helps!

---

### Post by Tux Aubrey on 2007-10-22
As above - the key is to mount the VBoxGuestAdditions.iso and run the VboxLinuxAdditions.run file in the guest (as per the Vbox manual) and then edit xorg.conf to provide the resolution you actually want.

I don't think this has anything to do with your windows settings (but I run Linux in Linux, so I don't know)

---

### Post by RobotFriendly on 2007-10-24
Thank you for your help and suggestions. I got close many many times, but unfortunately was never able to get *everything* working properly. I had the most success by installing Ubuntu as the host and using Parallels to run XP, but I was never able to get the network functioning properly or dual screens to work in both OS's. At this point I have given up. 

Thanks again

---

