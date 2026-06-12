---
title: "External monitor"
date: 2012-08-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by joakim2 on 2012-08-20
Anyone else having issues with multiple displays? I have an ASUS laptop with an external monitor hooked up via HDMI and the external monitor is detected and I can configure it in the "Displays" section of the system settings, but nothing ever gets output to it, it's blank. The Xorg driver is intel:

[    18.025] (II) LoadModule: "intel"
[    18.025] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so

Everything was working fine in 12.04.

---

### Post by cariboo on 2012-08-20
There was something about this on the ubuntu-desktop mailing list this morning:

> A heads up to make sure that the case of dual monitors with i945
graphics chipset (and possibly others) has been considered.  That
chipset will only run 3d if the virtual desktop is less than 2048
pixels wide so when an external monitor is plugged in only unity-2d
will run at the moment.  If the external monitor is not plugged in
then 3d is ok.  Having removed unity-2d the software will have to cope
with plugging in the external monitor in some way.  Note that this is
an issue for laptops made only a few years ago (Toshiba Satellite for
example).

I don't know if this is the problem you are having, but it could be very likely.

---

### Post by joakim2 on 2012-08-20
> **cariboo907 said:**
> There was something about this on the ubuntu-desktop mailing list this morning:



I don't know if this is the problem you are having, but it could be very likely.

ACK! Yes, that does seem likely... I sure hope they don't just drop support for Intel based multi-monitor setups, that would suck in a major way.

---

### Post by OM55 on 2012-08-20
Hello joakim2,

I use similar setting but with Acer Aspire laptops (2 separate installations), while the external monitor is HDMI connection.

I had strange compatibility issues that where all resolved when I installed the proprietary hardware driver for the video card (ATI Radeon).

So if you have not yet installed the proprietary video driver, I suggest you try and do that first, it may solve the problem.

---

### Post by joakim2 on 2012-08-20
> **OM55 said:**
> Hello joakim2,

I use similar setting but with Acer Aspire laptops (2 separate installations), while the external monitor is HDMI connection.

I had strange compatibility issues that where all resolved when I installed the proprietary hardware driver for the video card (ATI Radeon).

So if you have not yet installed the proprietary video driver, I suggest you try and do that first, it may solve the problem.

As far as I know there is no proprietary Intel driver, but I could be wrong.

---

### Post by OM55 on 2012-08-20
(I may be stating the obvious, but) did you try to run "Additional Drivers" to search for a proprietary driver?

What is your video card model? (or what is your laptop model?)

---

### Post by joakim2 on 2012-08-20
> **OM55 said:**
> (I may be stating the obvious, but) did you try to run "Additional Drivers" to search for a proprietary driver?

What is your video card model? (or what is your laptop model?)

It's an ASUS U43F with an Intel GMA integrated graphics chip.

---

### Post by OM55 on 2012-08-20
Thanks. Here are some suggestions:

The open source Intel driver: xserver-xorg-video-intel is usually installed by default (you may want to verify that by checking in Software Center for that name). Could be that the difficulty you experience was resolved in a newer version of the driver.

There are some PPAs that contain updated Intel drivers with newer versions. 
For example: [xorg-edgers drivers-only PPA]("https://launchpad.net/%7Exorg-edgers/+archive/drivers-only")
[HTML]https://launchpad.net/~xorg-edgers/+archive/drivers-only[/HTML]
You can also search and automatically add PPAs that have the most recent drivers. You can do that with Y PPA Manager. To install:

```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update
sudo apt-get install y-ppa-manager

```Just select search and check the 'in depth' checkbox, search name is: **xserver-xorg-video-intel**

You can also get the latest stable/unstable driver version directly from Intel at: [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
But this will require compiling of source code and other tweaks that you might prefer to avoid...

---

