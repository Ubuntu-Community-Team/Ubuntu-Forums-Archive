---
title: "USB Keyboard issues on Server Edition"
date: 2008-08-03
forum: Server Platforms
---

### Post by emgee3 on 2008-08-03
Long story short, my USB Keyboard does not work when booting from the latest Ubuntu server edition livecd. So this isn't exactly the same USB Keyboard issue as other people have reported, in that I am familiar with the Legacy USB settings in one's BIOS -- but I don't have such a feature in the computer I am using. The computer also doesn't have PS2 ports. I'm not interested in buying an adapter.

On the Desktop edition of Ubuntu, there's a time of 30 seconds before it chooses the default and starts. I thought I could modify the Ubuntu server .iso to put in a default setting, and I was able to do so (even extracted the boot image and rebuilt the .iso so I could boot from it) but then ran into MD5 checksum errors.

So my question is, any suggestions? I played around with desktop edition of Ubuntu for a few minutes and like the polish, but if I can't get the server version running I'll probably have to stick with a different distribution, which I'd prefer not to do.

Any help would be much appreciated.

---

### Post by mickyd on 2008-08-04
Only an idea
But why not install the desktop version strip out what you don't need and then install the server software you do want.
I know its not answering your question but should allow you to use the usb keyboard.

---

### Post by CONSERVOZOLLA on 2008-08-04
My ham radio locks up my keyboard when i tx on 10 meters

---

### Post by emgee3 on 2008-08-04
Well, I tried turning off my ham radio, but it didn't affect the outcome. So that's not it :)

I guess I could install the desktop version, but I'm reluctant to do that as from what I read, the differences are such that it's not easy to migrate from desktop to server after installation.

Still looking for suggestions. Perhaps there is an easy way to disable the MD5 checksum comparison.

---

### Post by ml41782 on 2009-08-08
If the keyboard locks up then you have RF getting into the computer. You need to 1. check grounding 2. check your reverse power. Its probably elevated. I have seen this before to the extent of shutting down the computer while conversing on packet.

---

### Post by Vegan on 2009-08-08
Sounds like there are several problems in your shop. Make sure the ground is really grounded. You may also want to take steps to shield the PC from the radio as much as possible.

---

