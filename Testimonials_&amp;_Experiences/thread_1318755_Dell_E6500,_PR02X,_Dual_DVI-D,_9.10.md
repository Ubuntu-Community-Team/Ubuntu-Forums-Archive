---
title: "Dell E6500, PR02X, Dual DVI-D, 9.10"
date: 2009-11-07
forum: Testimonials &amp; Experiences
---

### Post by trenchtractor on 2009-11-07
Hi, I'm still new to Ubuntu and since I have an uncommon set-up, thought I'd post some of my experiences...

My set-up:

-Dell E6500 with intel G45 series video
-E-Port Plus PR02X port replicator with dual digital video (HDMI, DVI-D)
-2 x LG L20WT displays, each at 1680x1050, using 2 x DVI-D Single Link cables

Initially I tried 9.04, but there seemed to be no solution to get the dual displays running in extended desktop mode... the vitual desktop was too small for the 3360 wide display with the G45.  I wasted many hours to not find a solution, and found 9.04 would run the two monitors on my desktop using an nVidia card, so in the end I blamed the G45.  Interestingly, Compiz worked the entire time despite the desktop being cut short on one display.  Also, wireless worked flawlessly on my network.

As a result of desperate frustration, I went to the evil MS product, using W7 RC.  Dual screen worked exactly as desired, wireless was again flawless.  Actually, W7 is a really good product. 

On release of 9.10, I imaged my windows build half expecting for the display issues to remain the same as 9.04... to my delight, 9.10 appeared to have fixed the limited display for virtual desktop.  Yippee.

Overall, I am quite pleased with the 9.10 build and congratulations to the team of developers.  But, there is always a 'but'.

Problems I have as of today:

1. Compiz doesn't work.  I have a single display set-up on the old T42, and compiz works perfectly.  I imagine this is as a result of the large virtual desktop and the G45 video.

2. Wireless doesn't work properly.  This is a funny one.  I've not changed any hardware, nor have I changed my network config.  I have two wireless AP's, one upstairs, one downstairs, both configured the same, apart from SSID, both using WPA.  No matter which one I use, I get a connection initially, then it disconnects, gets me web access for about a minute, then drops, then re-connects.  Strength is fantastic.  The T42 9.10 machine works perfect.  I can connect to a low strength unsecured AP in my street reliably.  Also, if my Dell connects to the AP, it drops the connection to any other machine already connected.  As I pointed out earlier, 9.04 didn't do this and neither did W7, Vista or XP.  The wireless card is a Broadcom unit, and I've noted some people having issues getting connections.  I intend to learn how to update the driver to the proprietary one, and I will also try WEP encryption...

3. Audio. Hmmm.  I'm not sure how to address this one.  I have the desktop speakers plugged into the PR02X port replicator, and with windows, the machine detected the port and disables the speakers on the laptop itself.  Unfortunately, this is not the case with 9.10... I'm not sure if it happened with 9.04.  And I'm not sure how to even begin finding a solution.  No matter how I try to drop volume to the laptop speakers, all controls work both outputs.  I have a suspicion last time I had Ubuntu installed, I plugged the speakers into the laptops headphone socket, but that is not an ideal solution since the thing is un-docked quite regularly, and the whole point of the port replicator is to never have to plug anything into it.

So that's my experience thus far... I don't use the security features like the card reader or finger print reader, so I can't comment there... and because I have USB hard drives set up in the bios, an external HDD will cause the GRUB repair dialogue on boot up.

I'm still a noob, but I'm happy to research...

---

### Post by running_rabbit07 on 2009-11-07
It is great to hear that your monitors work with 9.10. I would recommend posting your 3 problems in their respective sub-forum of the help section to get the proper attention.

Welcome to Ubuntu.

---

### Post by solwic on 2009-11-07
Like rabbit said, post your problems in the appropriate forums...and welcome to the light.  :)

---

### Post by trenchtractor on 2009-11-07
Thanks.  Yeah, I want to look into it deeper myself first... then I can at least make an intelligible post.  

The real problem with the audio seems to be a lack of people using port replicators, so a lack of information... the old D series replicators had a hardware identifier that XP used to change your profile between docked/un-docked, so were picked up as a device... with Vista, MS changed how they deal with hardware profiles, and the E series replicators weren't considered to need the identifier...

---

### Post by HappyFeet on 2009-11-07
Use WEP instaed of WPA. Unless you are the ultra paranoid type and think there are hackers stalking you, it will be good enough. Good luck to you.

---

### Post by trenchtractor on 2009-11-08
OK,  *had my AP's set to a fixed channel because one of the older lappy's only goes to CH 10, while the AP's go to 13.  A reconfigure of the downstairs WPA to auto channel and it seems stable as.  I'm not sure what the go is, maybe it just needed a refresh of the config settings... but I still have issues with the fixed channel upstairs...  No matter, I'll just use the downstairs AP for myself and the older lappy can hook up to the upstairs AP.*

---

### Post by trenchtractor on 2009-11-08
Ok, good news about compiz... removed and reinstalled compiz and the advanced desktop effects, reboot, configure the Cube and Ratate Cube and all is good when the laptop is removed from the dock... I'll try it on the dock next time I drop it on.

---

### Post by trenchtractor on 2009-11-08
After getting compiz working, I suffered from a problem with EweToob... see the bug here:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

### Post by solwic on 2009-11-08
> **HappyFeet said:**
> Use WEP instaed of WPA. Unless you are the ultra paranoid type and think there are hackers stalking you, it will be good enough. Good luck to you.

That makes a difference in connection stability?  Seriously?

---

