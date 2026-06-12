---
title: "I have Compiz working in Vbox 4.0.2"
date: 2011-02-10
forum: Virtualisation
---

### Post by Hedgehog1 on 2011-02-10
Getting compiz working in Virtual Box 4.0.2 is (at best) non-obvious.  But it does work.  I have Wobbly Windows running in both Ubuntu 10.10 and Mint Julia Vbox machines.

:popcorn:

1) Make sure you have one empty logical CD/DVD drive (Empty, no .iso attached) on your powered off Ubuntu/Mint 'Machine'

2) In the display section, Make sure your the Video memory is at 128mb and the 'Enable 3D acceleration' is checked. Do not check the 2D one - that is for MS windows only.

3) Run the machine.  Once the OS is loaded and use-able, use the 'Devices' menu and select 'Install Guest Additions'

Now, it appears that 'Install Guest Additions' didn't do anything - but it really did (this is that non-obvious part).  It attached an .iso to your CD/DVD.  There is no display to indicate this, you 'just gotta know'.

Now mount the Guest Additions CD/DVD .iso, and you will be prompted for premission to auto run it, and then asked for your password to install it.  Among other things, this installs a proper driver that supports Compiz.

I needed to reboot after the install of guest additions, and then I was able to select a high animation level and get my 'wobbly windows'.

:guitar:

I am now upgrading a working 10.10 Vbox with compiz running to 11.4 Natty.  We shall see if I can keep compiz going and get Unity to work in Virtual Box in Natty.

I will let you know.

:KS

---

### Post by Hedgehog1 on 2011-02-10
SOOOOO close!

My system is using a nice NVidia card. 11.4 alpha 2 gives them a black screen of death right now when compiz is running.

When I loaded 11.4 Alpha 2 without compiz starting successfully, I got the 'traditional' gnome UI, but no unity.

So I think it worked, but now I have to try it again with the alpha 1 version of 11.4 (which does not do the black screen of death for NVidia cards).

:lolflag:

---

### Post by Hedgehog1 on 2011-02-10
I have attached a screen shot showing compiz running in Virtual Box 4.0.2.

For this to work - the 'host' system must have a 3D graphics card and be capable of running compiz itself.

This screen shot is of Mint - but I have Ubuntu 10.10 in a Vbox also running compiz just fine.

:KS

---

### Post by Hedgehog1 on 2011-02-10
Here is the Ubuntu 10.10 using compiz in Virtual box.

:popcorn:

---

