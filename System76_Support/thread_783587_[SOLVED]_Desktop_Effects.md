---
title: "[SOLVED] Desktop Effects"
date: 2008-05-05
forum: System76 Support
---

### Post by Tart on 2008-05-05
Hi All,

I just got my Gazelle today. I'm very happy with it. I have a quick question about Desktop Effects. I have 8.04 installed and Intel GMA X3100 video card. I followed instruction on system76 knowledge base 

[HTML]http://knowledge76.com/index.php/GutsyCompizIntelX3100
[/HTML]
 but then I go to System->Preference->Appearance and try to enable Visual Effects, I get message that desktop effects cannot be enabled.   

I know instructions are for 7.10, and this is probably why they doesn't work. Do you have any recommendation for 8.04? 

Thank you for your help

---

### Post by fmartinez on 2008-05-05
> **Tart said:**
> Hi All,

I just got my Gazelle today. I'm very happy with it. I have a quick question about Desktop Effects. I have 8.04 installed and Intel GMA X3100 video card. I followed instruction on system76 knowledge base 

[HTML]http://knowledge76.com/index.php/GutsyCompizIntelX3100
[/HTML]
 but then I go to System->Preference->Appearance and try to enable Visual Effects, I get message that desktop effects cannot be enabled.   

I know instructions are for 7.10, and this is probably why they doesn't work. Do you have any recommendation for 8.04? 

Thank you for your help

Before trying to enable desktop effects. Consider the following: 
- What type of video card do you have (nvidia, ati)?
- you need to enable restricted drivers to the card fully functional?

I looked at the guide and no where does it tell you to make sure you have a restricted drivers enabled. 
- Creating the directories is NOT necessary! 
- After getting your video card running enabling desktop effects will take care of the rest. 
- The only good thing i saw was install compiz-config-manager
TO GET MORE SUPPORT LET US KNOW WHAT TYPE OF VIDEO CARD YOU HAVE.
HOPE THIS HELPS.

---

### Post by Tart on 2008-05-05
I have Intel GMA X3100 video card. Do I need to install restrictive drivers for it?

---

### Post by danpos on 2008-05-05
@Tart

It's not necessary. **[This thread]("http://ubuntuforums.org/showthread.php?t=695195&highlight=gma+x3100+hardy&page=2")** talks that your card is supported on Hardy Heron. I've a notebook which has a **Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller** and I'm running compiz-fusion at full capacity. :)

Regards,

Danpos.

---

### Post by thomasaaron on 2008-05-06
Testing on this one now. Stand by...

---

### Post by thomasaaron on 2008-05-06
OK, I imaged a GazV5 with Hardy using our server, and the desktop effects did not work.

From a Hardy live CD they worked.
From a Hardy install *without* updates, it *does* work.

I'm updating it now, but it doesn't look like it will finish before
I go home, so I'll report back tomorrow.

Thanks for your patience, and don't tweak on it too much just yet if you can resist the urge. :lolflag:

---

### Post by Tart on 2008-05-06
Thank you. 
I really appreciate your help and I'm sorry I created all this work for you :-)

---

### Post by thomasaaron on 2008-05-06
No, it's no big deal.

If it works fine once updates are finished, I'll need to image it with Gutsy and then upgrade it to see if that hoses effects. But we should have some closure on it by tomorrow.

---

### Post by antisocialist on 2008-05-07
you may want to consider downgrading to gutsy, i have nothing positive to say about hardy other than that it has a better upgrade icon.
however i did update so all my drivers were fully installed already.

---

### Post by thomasaaron on 2008-05-07
OK, Desktop effects work fine on the GazV5 with Hardy using a disk install.
However, it isn't working well with our server image.

The xorg.conf files are OK.

Hang tight, I've got a few more things to try, and I believe I'll have it up and running.

---

### Post by thomasaaron on 2008-05-08
OK, here is the solution:

Go to a terminal and enter this command:

sudo apt-get --purge remove nvidia-glx-new

Then restart your computer.

NOTE: THIS IS NOT FOR NVIDIA COMPUTERS. IT IS FOR OUR X3100 CHIPSETS ONLY.

---

### Post by Tart on 2008-05-08
Thank you Tom

---

