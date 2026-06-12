---
title: "A new full-time convert to the Church of Ubuntu"
date: 2012-05-20
forum: Testimonials &amp; Experiences
---

### Post by tekumel on 2012-05-20
I've tinkered with Ubuntu off & on over the last two years (since 10.04).  I've always been impressed with the distro, but I've never been able to bring myself to go any further than keeping an Ubuntu virtual machine for development.

Since I started poking around Ubuntu, I've become a self-admitted Google fanboy.  I use GMail, Android, Docs (now Drive), etc. religiously.  After placing an order for a new laptop, I realized...I'm a member of Microsoftholics Anonymous, and I'm clean.  Looking at Linux software compatibility for some minor work things (particularly Citrix), I realized...I was on Windows for no reason.  The games I enjoy run in Wine.  The software functions I need have, for the most part, been replaced with cloud or open-source alternatives.

So, just for a frame of reference, here's the laptop I ordered:
Satellite P750-BT4G22
[LIST]
[*]12 Cell lithium-ion battery (98Wh)
[*]Integrated 1.3MP webcam and microphone
[*]Realtek wireless 802.11b/g/n
[*]Intel Core i7-2670QM quad core processor
[*]Nvidia GeForce GT 540M 1GB dedicated graphics with Optimus
[*]Hybrid 4G 500GB 7200RPM SATA hard drive
[*]10/100/1000 Gigabit ethernet LAN
[*]15.6" 1366X768 Trubrite LCD display
[*]8GB (4GBX2) 1333MHz DDR3 memory
[*]Motherboard type 1
[*]DVD Supermulti drive +/- double layer
[/LIST]

I've never had such a smooth installation experience as I did with Ubuntu 12.04.  In the past, I've installed from a CD; this time I decided to try a USB install.  Absolutely no issues doing so, and installation required a minimum of user interaction.  I remember having problems on my old Toshiba Qosmio laptop, with having to use the --noacpi installation flag, having issues with hard disk detection, etc.  There was **none** of that this time.  I haven't even run into any drivers I needed to install...everything simply *worked*.

And then, it was done. And I was left with the dreaded, much maligned, evil Unity desktop.  After playing with it a bit, I installed GNOME to get a comparison and...promptly went back to Unity.  I find it to be a cleaner interface, and actually enjoy the Launcher (which I didn't expect), though I wish less apps would stick themselves to it by default.

So far, so good.  I'm still poking around and installing various "can't live without" Windows software but for the most part, I'm off and running.  Thanks, Canonical, and thanks to the posters here for the minor questions I *have* run into thus far.

---

### Post by mastablasta on 2012-05-21
> **tekumel said:**
> Nvidia GeForce GT 540M 1GB dedicated graphics with Optimus
.
Optimus now works in linux? it's not officialy supported. or is it working, but drainig battery? or maybe manual switching?
> 
[LIST]
[*]Hybrid 4G 500GB 7200RPM SATA hard drive
[/LIST]
 some of these are causing issues. but not all it seems.

---

### Post by tekumel on 2012-05-21
> **mastablasta said:**
> Optimus now works in linux? it's not officialy supported. or is it working, but drainig battery? or maybe manual switching?

I'm not noticing an *excessive* drain; I'm getting about 4 hours on a 12-cell.  I haven't reached the point of looking at power management settings though, so I'm not sure if I can squeeze more out of it.

---

### Post by mastablasta on 2012-05-21
well you would have to compare it to Win7 which Nvidia supports fully with optimus and where the stronger, more power consuming GPU would only turn itself on when necessary. 
 
maybe it Works well in linux with some models. but often people reported almost halved battery time in linux compared to windows.

---

### Post by tekumel on 2012-05-21
> **mastablasta said:**
> well you would have to compare it to Win7 which Nvidia supports fully with optimus and where the stronger, more power consuming GPU would only turn itself on when necessary. 
 
maybe it Works well in linux with some models. but often people reported almost halved battery time in linux compared to windows.

I've tried to do a bit of research on the issue today, as the battery life does seem low (I have no basis for comparison, as the only Windows boot I did on the machine was to burn recovery discs and on AC).  Everything seems to point to Bumblebee...any experience with it mastablasta?

---

### Post by mastablasta on 2012-05-22
no. but bumblebee is a project that aims to bring Optimus GPU switching (at least manually if not auto) to linux. Reverse enginered. so might not always work as expected. in other words it works well for some and not at all for others...

---

