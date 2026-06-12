---
title: "dell touchpad doesn't work on new Studio intall"
date: 2015-07-08
forum: Ubuntu Studio
---

### Post by edward_barnes on 2015-07-08
version 14.04.02 in ubuntu studio.
the computer is a dell el cheapo inspiron 15 3000

[don't bust my chops i got the el cheapo to see if i could use this OS in my audio job haha.]

anyway, it came with ubuntu vanilla and when i installed ubuntu studio, the cursor stopped moving mid-install and i fortunately had a plug in usb mouse handy, which is likely better for editing of course but it would be nice to be able to use the pad while on a plane etc. 

touchpad worked find under the ubuntu vanilla administration.

i've tried various combos of fn and the numbered function keys, rebooting, turning preferences off and on etc. to no avail.

the plug in mouse works perfectly.

if this has been covered before, my humble apologies. 

thank you.

---

### Post by gdesilva on 2015-07-15
Check if touchpad is disabled on your system.

On a terminal run the command 'xinput list' - among other devices you should see something like the following which I get on my system.

SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]

Note down the id, in my case it happens to be 11.

Then issue the following command 

xinput set-prop 11 "Device Enabled" 1 (replace 11 with the number you got from your system)

If your touchpad is not listed in the output from 'xinput list then this could mean the driver loaded is not the right one.

---

### Post by Geoffrey_Arndt on 2015-07-15
One way then, for sure, to fix the issue is to re-install "genuine-Ubuntu" and simply install the apps you need from USC (ubuntu software center).   There's a plethora of audio and video software for Linux in general, more than enough for the serious enthusiast.   If you're a professional, use the tools and OS that you actually need especially to interact with like peers.

---

### Post by edward_barnes on 2015-07-16
thanks folks that is some really helpful stuff there.

i'm an audio person by trade and i'm trying to get a good handle on how to do everything in linux. 
i really appreciate the help.

---

