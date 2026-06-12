---
title: "Hardy seems unstable - thinking of going back to Vanilla Debian"
date: 2008-09-08
forum: Testimonials &amp; Experiences
---

### Post by fatalGlory on 2008-09-08
Lately, my Ubuntu Hardy box just seems so unstable.  The thing locks up all the time (lose mouse and keyboard, sound goes haywire and picture freezes).  Granted I do a fair few hackish things with it.

What I am wondering is do any other people have these problems with hardy?  I'm wondering whether it is the system software or the NVidia (173.14.12) X Server that is the part that's actually crashing.

Is it worth me trying another distro?  (forget going back to windows world :P)

---

### Post by michaelkahl on 2008-09-08
Honestly I've only had two issues with hardy 64bit
1.  GDM theme not sticking on my work machine, but it's resolved with one command
2.  Evolution hanging while I'm trying to send/receive email on my works exchange server. (Over time this has gotten better and hasn't happened on a long time).

Other than that I haven't had issues with anything that you are mentioning.
Are you sure your mobo is in good shape, they all plug into or are part of the mobo.  Just seems like a strange thing for a video card driver to be responsible for mouse/keyboard problems, but then again I've seen stranger things with computers.
Also are you running compiz or anyother desktop effects program?

---

### Post by fatalGlory on 2008-09-08
No desktop effects, no compiz.  I prefer just metacity.  I guess I could be having hardware faults, but I certainly hope not since the parts are only about 12 months old.  My guess was with the Nvidia driver since i thought that the X Server handled mouse and keyboard input as well so a crash of the driver would possibly cause that whole lock up.

I guess that doesn't explain the audio.

The irritating thing is that this only happens every few days, so the only way to really find out if the cause of crashes is hardware, is to wait for something to fail :(

Thanks for the reply

---

### Post by 16777216 on 2008-09-08
I get soft locks, hard locks, X resets, short term freezes, long term freezes, audio stammering, video corruption, and probably some I have forgotten about. 

I too use nvidia graphics. 
NVIDIA Driver Version: 177.68
Graphics Processor: GeForce 8600 GT
Adaptive Clocking: Enabled
GPU Clock: 540Mhz
Memory Clock: 400Mhz
Memory: 512 MB
Bus Type: PCI Express 16X
X Screens: 1
Dimensions: 2304x864 pixels (1152x864*2 Heads)
Depth: 24
Display Devices: DELL  M991 (CRT-0), ViewSonic GS773 (CRT-1)

The X resets seem to only happen when running Firefox or Azureus with the use Firefox 3 controls option turned on.

The locks seem to be mostly random and don't happen that much.

The video corruption and a few of the freezes seem to be an issue with the graphics card changing clock speeds. ( Or so I have read but, I can manually over/under clock my card with out issue even if I let it auto find the best frequency so,..:confused: ) 

The audio, it seems for many, to be an issue of Hardy not having the best settings for Pulse out of the box.

I used this guide to fix my audio and it has worked great. ( YMMV )
                
[LIST]
[*][**HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)**]("http://ubuntuforums.org/showthread.php?t=789578")
[/LIST]

I have also found these:
                
[LIST]
[*][**How To: The (almost) Perfect Pulse Audio Setup**]("http://ubuntuforums.org/showthread.php?t=776739")
[*][**Comprehensive Sound Problem Solutions Guide**]("http://ubuntuforums.org/showthread.php?t=205449")
[*][**Comprehensive Multimedia & Video Howto**]("http://ubuntuforums.org/showthread.php?t=766683")
[/LIST]

---

### Post by fatalGlory on 2008-09-08
Where did you get that nvidia driver?  Mine is a lower version number but its still the latest one at the [nvidia drivers page](http://www.nvidia.com/object/unix.html).

**EDIT:** Never mind found it.  For interested people, the latest beta drivers can be downloaded at [ftp://download.nvidia.com/XFree86/Linux-x86/177.70/](ftp://download.nvidia.com/XFree86/Linux-x86/177.70/)

---

### Post by lancest on 2008-09-08
Ubuntu Hardy can run well on 512 Ram. IMHO for best (smoothest) performance need at least 1 GB of Ram. If you are a power user especially This is an up to the minute desktop OS- with more code.  I wouldn't be surprised to see a desktop box lagging on 512 Ram now and then. Depends on your needs though. Ram is cheap.

---

### Post by 16777216 on 2008-09-09
> **lancest said:**
> Ubuntu Hardy can run well on 512 Ram. IMHO for best (smoothest) performance need at least 1 GB of Ram. If you are a power user especially This is an up to the minute desktop OS- with more code.  I wouldn't be surprised to see a desktop box lagging on 512 Ram now and then. Depends on your needs though. Ram is cheap.


If you are referring to the "Memory: 512" in my post above, that is just my graphics card stats My system memory is 1GB.

CPU INFORMATION
    AuthenticAMD, AMD Athlon(tm) 64 Processor 3000+
    Number of CPUs: 1
    CPU clock currently at 2000.000 MHz with 512 KB cache

MEMORY INFORMATION
    Total memory: 1010 MB
    Total swap: 3906 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  WDC WD800JB-00JJ 
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  ST340015A        
    SCSI device -  scsi1
        Vendor:  LITE-ON  
        Model:  DVD SOHD-16P9S   
    SCSI device -  scsi4
        Vendor:  HP       
        Model:  Photosmart C3140 

SOUND CARD
    Multimedia controller
        nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 8213

NETWORK
    Ethernet controller
        Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139

---

### Post by wolfen69 on 2008-09-09
i've installed hardy on many machines without issue. it does not work perfect on every single computer in the world. no OS does. i think if you installed it on a few other machines, you would find it to be very stable. judging an OS just on just 1 computer is really not fair. but, in the end, use what works for *your* computer.

---

### Post by xeth_delta on 2008-09-09
> **fatalGlory said:**
> No desktop effects, no compiz.  I prefer just metacity.  I guess I could be having hardware faults, but I certainly hope not since the parts are only about 12 months old.  My guess was with the Nvidia driver since i thought that the X Server handled mouse and keyboard input as well so a crash of the driver would possibly cause that whole lock up.

I guess that doesn't explain the audio.

The irritating thing is that this only happens every few days, so the only way to really find out if the cause of crashes is hardware, is to wait for something to fail :(

Thanks for the reply

Do you remember what you were doing those thimes the system crashed? There can be several causes for the lock-ups, and my first suggestions would be to check on the video drivers, maybe trying another newer revision.
Then again, it might be a good idea to also run a RAM check for several hours from the installation CD. Faulty RAM can cause problems like the one you described.

---

### Post by bart1452 on 2009-02-09
Hardy 64 bit and Hardy 32 bit both are unstable on my 2005 vintage Compaq Presario with an AMD 64 Athlon 3400+ and 1 Gig memory. It might have something to do with not getting a good connection on us.archive.ubuntu.com. I don't know if all the packages downloaded or not, but there were issues with retrieving packages during the installation and I instructed it to retry. I currently have 64 bit Hardy installed.

The problems include screen video corruption, window panels not working properly, total computer non-responsiveness except for the cursor moving for the mouse after windows are opened and closed several times. The only way out then is to force a BIOS shutdown. A screen shot of one incident is included from when I tried to configure the printer with HPLIP Toolbox.

One example is that while trying to forward an email, the address book window malfunctioned and the middle 95% would not scroll while the very top and bottom did.

I ran the recovery mode and tried to repair broken packages and got the following errors:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could ot resolve 'us.arcive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/idsts/hardy-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/idsts/hardy-security/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

W: You may want to run apt-get update to correct these problems

I ran apt-get update and it didn't work.

david@ubuntuSR1550nx:~$ sudo apt-get update
[sudo] password for david: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
david@ubuntuSR1550nx:~$ 

All the apt-get update happened in a split-second so I don't think anything was downloaded and installed.

I love Ubuntu Hardy on my laptop and don't understand why it isn't working properly on my desktop.

---

