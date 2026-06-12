---
title: "PanP4 w/Karmic has no video output"
date: 2009-12-15
forum: System76 Support
---

### Post by bill516 on 2009-12-15
Sorry Tom, the Bad Penny has turned up again!

All has been good with my upgrade to Karmic on my PanP4 until I tried Skype this evening.  Good sound, no video.

Tried Cheese.  Shows only a test pattern & raster.  Looks like Cheese also is inoperative.

Nvidia Driver is 185.18.36

System76 driver package is 2.4.0

lsusb lists ALi Corp USB 2.0 Camera.

Skype does show a USB 2.0 camera under is video settings GUI, but test does nothing.

NOTE:  Skype does not appear to be in the 9.10 repos.  I went to the Skype site and downloaded the latest 64 bit Skype available, which is 8.10. Installed, deleted and reinstalled.  No luck.

What to do next????

Need help.  Granddaughter in Fort Collins needs to see Grandmother in KY!  We do see granddaughter just fine.

And thanks once again, Tom.

Bill Julian

---

### Post by thomasaaron on 2009-12-16
Could you try Ekiga Softphone via a live 9.10 64-bit CD? It should work out of the box and will rule out a hardware problem before we start digging into it.

If you want to call me when you are booted from a live CD, I'll walk you through getting Ekiga working.

---

### Post by bill516 on 2009-12-16
I understand the idea, but Ekiga is not on my 9.10 live cd!  In fact I burned a second one just to see if there had been a change in the inventory,

So here I am on my 8.10 live cd which does have Ekiga.  I did try to configure but without success.

Here's the story so far.

Ekiga comes up and I run Druid/Wizard/Whatchamacallit.

Detects ""Symmetric NAT"  (I have a DSL connection through a wireless router)

Audio = ALSA

Output & Input = HDA Intel

Video Manager = V4L2

Video Device = USB2.0 Camera

I clicked on "Display images from your camera device"  No Image.

Ekiga is locking up when I try to run tests, Tom, which may have to do with the fact that I am running from the live cd?

---

### Post by bill516 on 2009-12-16
Tom, I went looking through my live cds for a distro that has Cheese and/or Ekiga.  Mandriva 2010 Gnome does, so I have tried Cheese.

Same result as with Ubuntu 9.10.  I get a raster pattern in the lower right corner of the window and color bars aross the rest of it.

Under Ubuntu 8.10 I had installed Cheese and it worked very reliably.  Unfortunately it is not on the 8.10 live cd, so I could not try it that way.

Bill

---

### Post by thomasaaron on 2009-12-17
The problem is, I don't think the webcam was supported out of the box with 8.10. If memory serves, the System76 Driver was required.

In both 9.04 and 9.10, it is supported out of the box with Ubuntu. So, you might also try from 9.04.

Edit: I just booted from a 9.10 64-bit CD, and it definitely has Ekiga (Applications > Internet > Ekiga Softphone).

---

### Post by bill516 on 2009-12-17
Well that's a bit weird, but OK.  Guess I put my glasses on and look at that 9.10 menu once more (don't suppose we have two UUIDs here???  oh not THAT again!.

I do have a 9.04 CD so I'll try that as well as 9.10.

I'll report back later today.

Thanks for the patience!

---

### Post by bill516 on 2009-12-17
Well, I have not completely lost it.  Ekiga is not on my 9.10 Ubuntu live cds (I have two, checked both).  Really, it is not there.

Unfortunately I did not remember that the only 9.04 I had was Kubuntu and that does not work for our purpose.  Ubuntu 9.04 does not seem to be available for download any longer, which makes sense.

So in terms of testing with a 9.04 live cd I am stuck, I'm afraid.

Meanwhile I have thrown fedora-Gnome and a couple of other distros on this machine (live cds of course) and nothing operates the lid camera.

I know that 8,10 operated without a blink (and you know what, I sometimes wish I had left well enough alone!) and I am trying to remember if I ever did any Skype with 9.10.  Honestly I just cannot recall so I'll say no.

Without a 9.04 disk is there any other way to check this thing?

---

### Post by drewbenn on 2009-12-17
> **bill516 said:**
> Ubuntu 9.04 does not seem to be available for download any longer, which makes sense.

It is still available (as are all the old Ubuntu releases), go to:
[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

---

### Post by bill516 on 2009-12-17
Thanks drewbenn!

I did find it finally with Tom's help.  Somehow missed the page - but I miss a lot of things!

Official Old Guys do that.

Meanwhile, have Jaunty burned, booted it and tried Ekiga.

Sound test passes.

Video configured for USB 2.0 Camera (PTLib/V4L)

Format set for Auto

No response to Test.  Blank video window was absent when I clicked away from video and went back to it.

So no evidence Ekiga sees my lid-camera unless Tom suggests a configuration change I should try.

Also reinstalled Skype and checked.  Same deal.  Sound is OK, video output fails.

Not good, seems to me.

---

### Post by thomasaaron on 2009-12-17
> Video configured for USB 2.0 Camera (PTLib/V4L)


That doesn't sound right. Can you call again tomorrow, and I'll walk you through it?

---

