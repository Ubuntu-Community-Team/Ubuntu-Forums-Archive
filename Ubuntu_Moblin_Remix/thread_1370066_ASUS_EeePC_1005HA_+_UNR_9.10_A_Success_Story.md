---
title: "ASUS EeePC 1005HA + UNR 9.10: A Success Story"
date: 2010-01-01
forum: Ubuntu Moblin Remix
---

### Post by UltraZone on 2010-01-01
[Borat] Succeeeess! Yes? [\Borat]

:popcorn:

Seriously now, I installed the wonderful UNR 9.10 on this brand spanking new ASUS EeePC 1005HA yesterday and frankly it kicks *** beyond my wildest imagination.

For anybody out there whos got one I highly recommend it, altough I would like to point out a few critical details that stalled my installation process momentarily (ok for like an entire morning)

To start out with I struggled to bring up the ¨Boot from" selector page of the Bios to boot from the USB drive.  I tried everything that I knew on my other laptop F1, F12, etc nothing worked.  Then I read I should press Esc: nope, not working either, straight to XP (shudders). Finally I dug around the Googles some more and found some extra instructions: you gotta press F2 *twice* to bring up the BIOS settings page.  It doesnt help that ASUS configures the BIOS with the *Quiet Boot* option enabled, so when you turn on the netbook the first thing you see is the Win XP splash screen.  Anyway you gotta press F2 twice immediately after turning it on.  This baby boots up hella fast.  Anyway you access the BIOS and scroll over 3 to the right to the Boot tab.  Next you go down to the OnBoard LAN boot ROM and enable that option (comes disabled by default by ASUS, hence my initial failures) and also disable the Quiet Boot option.  Then you Save changes and Exit the Bios settings page.  Next you will see an Atheros Boot page counting down for you to do something: press Shift+F10 real quick.  Next you will see a menu that allows you to boot from USB drive (obviously you should already have it plugged in).  After this Ubuntu installer boots up, no problems here.  Installation took about 1/2 hour. 

After installing Ubuntu you can go back to the Bios page and enable the Quiet Boot option so that the first thing you see is Grub.  

Oh yes, I forgot to mention.  Ethernet: check. Wireless: check.  Webcam: check (works with Cheese, havent tried chat yet).  Had to enable Medibuntu to download movie/music codecs (as you know it gets the correct codecs when you play a movie whose codecs are not installed).  Firefox requested to install Flash, so Youtube: check.

This is my face: :P

---

### Post by aljoriz on 2010-01-02
congratulations, I tried the other distros namely eeebuntu but sadly the wi-fi/ethernet does not work out of the book and it would take time to configure them until the eeebuntu 4.0 arrrives I will install UNR 9.10

the [bug ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/465497")about the mic not working is a big let down though

---

### Post by aljoriz on 2010-01-02
Currently the best linux distro suitable for 1005ha would be UNR 9.10

---

### Post by johninsf on 2010-01-04
Hey! 

Glad to hear this went well as I am planning a similar path.

I am considering the purchase of this same Asus model due to the specs of the latest netbook. (1.66ghz N280 processor, b/g/n wireless, HDD and battery life.)

I currently run U9.10 on an 2004 IBM X31 with 1gb of memory and the 1.7ghz processor. The graphics card is not the greatest but got Compiz working on it last week and the "Normal" Visual Effects are working well. This was a bit of a pain but thanks to this forum for the answer. Smart people abound here.

1. Could you confirm that this Asus model has an additional slot for another gig of memory? I think it does but would like to be sure.

2. Any problems installing from USB? (Will download on IBM laptop then install since no CD.)

These other points are great and I will definitely refer back to this post when installing Ubuntu 9.10. Even with Win7 as a vast improvement over XP, I still enjoy removing the Windows OS. There is something freeing about it. :)

Thanks.




> **UltraZone said:**
> [Borat] Succeeeess! Yes? [\Borat]

:popcorn:

Seriously now, I installed the wonderful UNR 9.10 on this brand spanking new ASUS EeePC 1005HA yesterday and frankly it kicks *** beyond my wildest imagination.

For anybody out there whos got one I highly recommend it, altough I would like to point out a few critical details that stalled my installation process momentarily (ok for like an entire morning)

To start out with I struggled to bring up the ¨Boot from" selector page of the Bios to boot from the USB drive.  I tried everything that I knew on my other laptop F1, F12, etc nothing worked.  Then I read I should press Esc: nope, not working either, straight to XP (shudders). Finally I dug around the Googles some more and found some extra instructions: you gotta press F2 *twice* to bring up the BIOS settings page.  It doesnt help that ASUS configures the BIOS with the *Quiet Boot* option enabled, so when you turn on the netbook the first thing you see is the Win XP splash screen.  Anyway you gotta press F2 twice immediately after turning it on.  This baby boots up hella fast.  Anyway you access the BIOS and scroll over 3 to the right to the Boot tab.  Next you go down to the OnBoard LAN boot ROM and enable that option (comes disabled by default by ASUS, hence my initial failures) and also disable the Quiet Boot option.  Then you Save changes and Exit the Bios settings page.  Next you will see an Atheros Boot page counting down for you to do something: press Shift+F10 real quick.  Next you will see a menu that allows you to boot from USB drive (obviously you should already have it plugged in).  After this Ubuntu installer boots up, no problems here.  Installation took about 1/2 hour. 

After installing Ubuntu you can go back to the Bios page and enable the Quiet Boot option so that the first thing you see is Grub.  

Oh yes, I forgot to mention.  Ethernet: check. Wireless: check.  Webcam: check (works with Cheese, havent tried chat yet).  Had to enable Medibuntu to download movie/music codecs (as you know it gets the correct codecs when you play a movie whose codecs are not installed).  Firefox requested to install Flash, so Youtube: check.

This is my face: :P

---

### Post by aljoriz on 2010-01-05
here's a point by point answer to your querries:

1.  eeepc 1005ha is upgradeable to 2g ram but not expandable as there is no additional memory slot.

2.  As long as you used UNetbootin to make a live install and the MD5sum are the same with the md5sum on the net you will do just fine.  

Good luck, I suggest getting the white color as finger print are less visible on a white eeepc.

---

### Post by Sprutnik on 2010-01-05
How is suspend and hibernate working for you guys ? I also run UNR 9.10 on my 1005HA, and if I wake the machine after a suspend session, my network devices sort of 'disappear'. I cant connect to either wired or wireless. If I run a ifconfig or iwconfig in the terminal, it shows none of my network devices ?

I'm soon about to try a clean install to see if that solves the problem...

---

### Post by aljoriz on 2010-01-07
would a quick restart fix the problems that arose from 'waking up'?

---

### Post by Sprutnik on 2010-01-08
Yeah, a quick restart fixes the problems. But that kinda kills the idea about suspend and hibernate ;-)

---

### Post by aljoriz on 2010-01-08
it's minor stuff like that makes me think of going to m$ again. Why can't linux make use of all of the capabilities of 1005ha directly out of the box?

---

### Post by aljoriz on 2010-01-09
> **Sprutnik said:**
> How is suspend and hibernate working for you guys ? I also run UNR 9.10 on my 1005HA, and if I wake the machine after a suspend session, my network devices sort of 'disappear'. I cant connect to either wired or wireless. If I run a ifconfig or iwconfig in the terminal, it shows none of my network devices ?

I'm soon about to try a clean install to see if that solves the problem...

its official.. that is a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432315](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432315)

Just imagine if you had the netbook in hiberate with the wi-fi connection on then you moved to a place with NO Wi-fi when you wake up, it would make sense that the devices would 'disappear or reset' :P

On a side note I tried Jolicloud but didn't like it
it doesn't make sense to spend more than 5min to install open office writer when UNR has it BUILT-IN from the start.

---

### Post by sturg_nz on 2010-01-17
I have a 1000HA and installed UNR 9.10 two days ago. After some fun & games getting into the BIOS, the install went very smoothly. Apart from the WIFI keys constantly dropping out, I'm really enjoying the experience. :D All the familiar menus are easy to find... and the boot up and shut down times are a vast improvement on the supplied XP OS.

---

### Post by Qvintvs on 2010-01-18
I've been looking to buy a 1005HA and throw UNR on it. Glad to see its working well for you.

> 1. eeepc 1005ha is upgradeable to 2g ram but not expandable as there is no additional memory slot.
Just out of curiosity, have you seen anywhere that actually sells it with 2gb built in?

---

### Post by aljoriz on 2010-01-19
In my part of the world, the answer would be NO

---

### Post by bui89 on 2010-02-06
Hello I  own asus eeepc 1005HA which according to System testing has Ralink rt3090 Wireless 802.11n. I installed and updated unr 9.10, but no wifi, did sudo apt-get install linux-backports-modules-karmic as written here [https://wiki.ubuntu]("https://wiki.ubuntu/").com/HardwareSupport/Machines/Netbooks did not help. Then I  did everything as written here, installed madwifi [http://dimitar.me/madwifi-drivers-for-u … and-above/]("http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/") , installed wicd wrote No wireless networks found. help pleaseee I am going crazy already :(

---

### Post by adm1968 on 2010-03-09
> **bui89 said:**
> Hello I  own asus eeepc 1005HA which according to System testing has Ralink rt3090 Wireless 802.11n. I installed and updated unr 9.10, but no wifi, did sudo apt-get install linux-backports-modules-karmic as written here [https://wiki.ubuntu]("https://wiki.ubuntu/").com/HardwareSupport/Machines/Netbooks did not help. Then I  did everything as written here, installed madwifi [http://dimitar.me/madwifi-drivers-for-u … and-above/]("http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/") , installed wicd wrote No wireless networks found. help pleaseee I am going crazy already :(
[FONT="Georgia"]Did you give wicd a try? I had issues with wifi on my desktop, running 9.04, and everything was solved immediately after installing this application[/FONT]

---

### Post by ajaysutton on 2010-03-10
I have no issues with hibernation on my 1000HE and UNR 9.10.  What kind of issues are you having?

---

### Post by xfran on 2010-04-03
> **Qvintvs said:**
> I've been looking to buy a 1005HA and throw UNR on it. Glad to see its working well for you.


Just out of curiosity, have you seen anywhere that actually sells it with 2gb built in?

Nope, but it is really very easy to upgrade, check the video here:
[http://www.asus1005ha.com/asus-1005ha-tips/]("http://www.asus1005ha.com/asus-1005ha-tips/")

I bought the module at the same time as the laptop, and installed the memory as in the video. 

Cheers !
:popcorn:

---

### Post by walt.smith1960 on 2010-04-08
> **bui89 said:**
> Hello I  own asus eeepc 1005HA which according to System testing has Ralink rt3090 Wireless 802.11n. I installed and updated unr 9.10, but no wifi, did sudo apt-get install linux-backports-modules-karmic as written here [https://wiki.ubuntu]("https://wiki.ubuntu/").com/HardwareSupport/Machines/Netbooks did not help. Then I  did everything as written here, installed madwifi [http://dimitar.me/madwifi-drivers-for-u … and-above/]("http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/") , installed wicd wrote No wireless networks found. help pleaseee I am going crazy already :(
I have a eee1005HA**B** and it uses Atheros for both wired and wireless internet. 9.04 did not have native support for networking, either wired or wireless. I used a USB external wifi adapter that does have native support to enable backports in 9.04. I then had WiFi but no wired internet.  Karmic native support for Atheros from the alpha releases. I did a swap file rather than a swap partition so I doubt I have hibernation; I haven't tried. Suspend and resume work quite reliably though.  9.10NBR is MUCH more usable than XP home IMO. I wonder if you'll have any more success with networking running Lucid. I'm having an issue with a Ralink RT-3572 USB adapter. I've read where some of the Kernels in testing have built-in support. I'm just going to wait 'til native support appears.  TrendNet TEW-424UB_H/W3.1_ use a RealTek chip that is supported out of the box. Be careful because TrendNet's TEW-424UB _H/W. 2.X_ used an SIS chip that is not supported natively. Both adapters look alike. I hate when that happens.

---

### Post by pualbarnes on 2010-04-10
Small world i'm running Ubuntu 9.10 mobile remix on my Asus Eee 1008ha and it works a dream, smooth even on advanced settings

---

### Post by stoneguy on 2010-04-11
Yes, 9.10 and its spawn (eg Mint 8) look real good on the 1005HA. However, 10.04 is still a problem even at Beta 2 :(

---

### Post by toor58 on 2010-04-11
What problems with 10.04? I have it on my 1005ha and except for lack of Fn key support it is running quite well. What seems to be the problem with your install?

---

### Post by whitec on 2010-04-15
10.04 is mostly fine on mine  (1005HA) but suspend is not working correctly.  When I suspend - it blanks the screen, but never actually goes into suspend mode.

I have looked around, and tried some different things, but no luck.  This is with the most up to date beta 2 kernel.

Also - having trouble getting the new script for multi-touch working automatically.  After I boot up, I can manually run it, and it works fine - but not having any luck getting it to work on bootup.

---

### Post by rudihawk on 2010-04-16
Aspire One here,working well :)

---

### Post by whitec on 2010-04-16
Actually scratch that.  Mine is good.  Problems I was having was due to a eee tray applet I was using.  Got rid of that, and all is good :-)

---

### Post by rad_sci_guy on 2010-04-19
> **toor58 said:**
> What problems with 10.04? I have it on my 1005ha and except for lack of Fn key support it is running quite well. What seems to be the problem with your install?


I can't turn on the wifi card in 10.04 beta2.  I got it to work on the initial install, but after that the wifi won't turn on.  I haven't had a chance to attach the network cable and run any updates for 10.04 but I might try today.

It's very strange as 9.10 works great for me.  The only problem with 9.10 is that I have to manually switch off the internal speakers when I attach headphones and then manually switch back when I want external speakers again.

---

### Post by rad_sci_guy on 2010-04-20
> **rad_sci_guy said:**
> I can't turn on the wifi card in 10.04 beta2.  I got it to work on the initial install, but after that the wifi won't turn on.  I haven't had a chance to attach the network cable and run any updates for 10.04 but I might try today.

It's very strange as 9.10 works great for me.  The only problem with 9.10 is that I have to manually switch off the internal speakers when I attach headphones and then manually switch back when I want external speakers again.

Well I updated the install tonight and I still don't have any wifi capability.

---

### Post by jlandaw on 2010-05-01
turn the wifi on in the BIOS

---

### Post by goseph on 2010-05-27
I have NBR 10.04 on my 1005HA and the battery life is appalling compared to winXP! Would downgrading to Karmic fix this? Does anybody have any advice?

---

### Post by Quarn on 2010-06-08
I'm using the 10.04 on my 1005HA and everything run smooth and well.. I like almost everythin of it. it's great... I just hate the damn side bar, and i don't know how to make it like the normal UBUNTU

---

### Post by GSF1200S on 2010-06-09
> **goseph said:**
> I have NBR 10.04 on my 1005HA and the battery life is appalling compared to winXP! Would downgrading to Karmic fix this? Does anybody have any advice?

Download powertop and see how many watts youre using at idle:
```
sudo apt-get install powertop
```
and then to open:
```
sudo powertop
```

I have a 1005HA-P running Arch w/ LXDE and its using about 7.3 Watts with the brightness turned all the way down. The computer will run over 9 hours with regular usage (web browser, file manager, Guayadeque), which is better than XP was for me. Uses 59.6 MB of RAM at boot. Im willing to bet that Gnome hurts your battery life at least a little bit, as more processes running typically polls the hard drive more often. Use powertop to enable USB autosuspend and VM Writecacheback to save half a watt. It also helps battery life considerably if you disable those things which you do not use in the BIOS. For instance, I basically only use WIFI and USB. My card reader, bluetooth, and camera are disabled in the BIOS (the camera even not in use is a battery killer), which helped quite a bit.

I think XP is still prolly better in some cases (battery wise), but as it ages many processes start polling the harddrive frequently which kills battery life.

**EDIT** It should also be noted that I am using a custom kernel. Arch has a user repository where people put up PKGBUILDS allowing you to install the packages they create into your package manager. I used a kernel designed for the eeepc, which basically omits all drivers unnecessary and has support for everything that is necessary. Its also optimized for the eeepc and lacks an initramfs- You could accomplish all of these same enhancements by either locating a custom kernel for Ubuntu or compiling one yourself. Its not too hard to do, and you can simply recompile if you miss a feature or something.

---

### Post by GSF1200S on 2010-06-09
> **Quarn said:**
> I'm using the 10.04 on my 1005HA and everything run smooth and well.. I like almost everythin of it. it's great... I just hate the damn side bar, and i don't know how to make it like the normal UBUNTU

Logout to the login screen and select your username. After doing so, go down to the session selector and select "Gnome Session" instead of UNE/UNR. This will load the regular Gnome interface instead of the UNE interface.

---

