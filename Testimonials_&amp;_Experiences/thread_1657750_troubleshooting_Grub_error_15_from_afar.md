---
title: "troubleshooting Grub error 15 from afar"
date: 2011-01-01
forum: Testimonials &amp; Experiences
---

### Post by decoherence on 2011-01-01
I gave a netbook to my aunt a couple of years back. It has been humming away nicely but recently she has been getting

GRUB loading stage 1.5

 

GRUB loading, please wait...

Error 15

supposedly out of the blue, she says... in that case all I can think of is failed hardware or a botched update (which certainly wouldn't be the first time.)

Anyway, without being able to SSH in to the machine or go to her house, I've pointed her at this doc 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

which talks about the error and how to reinstall GRUB. Unfortunately I also had to point her at 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

As the Grub2 document is deficient for systems that lack optical drives. 

If those documents don't help, I'll have to start asking more questions, maybe get her to allow ssh through her firewall and configure NAT, create me an account, etc. etc.. Bummer!

---

### Post by oldfred on 2011-01-01
The question is what version does you aunt have? Grub stage 1.5 is grub legacy or grub 0.97 which you have after upgrades from 9.04 or before. After 9.10 all new installs are grub2.

Error 15 is often from having reinstalled grub on a grub2 machine or vice versa, but it is trying to boot grub legacy from the MBR as it is the one outputting error 15. Grub2 does not have error numbers (it may have errors though).

If she can boot a live USB install, have her run this and start a thread here:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by decoherence on 2011-01-01
Thanks oldfred -- I'm sure we'll be able to get it up and running. Just wanted to 'testify' about the experience.

Great info about the Boot Info Script! That's a new one on me! thanks again,

---

