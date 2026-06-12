---
title: "ubuntu usb stick does not boot on netbook"
date: 2011-10-14
forum: System76 Support
---

### Post by jsusanka on 2011-10-14
I have a system 76 netbook and trying to boot 11.10 via a usb stick I made from a downloaded iso using the ubuntu startup disk created on the ubuntu LTS version.  

when I boot to the usb drive it fails after showing ubuntu and the dots underneath and takes me to a busy box prompt telling to type init = boot args 

would like to run the latest ubuntu on this netbook so any help would be appreciated.

---

### Post by chriscross93 on 2011-10-15
I often run into strange issues when using live flash drives.  Generally installing Ubuntu on the flash drive again solves the problem.  If not, try using an external optical drive (if possible.)

---

### Post by jsusanka on 2012-02-17
> **chriscross93 said:**
> I often run into strange issues when using live flash drives.  Generally installing Ubuntu on the flash drive again solves the problem.  If not, try using an external optical drive (if possible.)

I don't have an external optical drive.  I have reinstalled 11.10 numerous times on different sticks.  Everytime the stick works on other computers but on this System 76 starling netbook I get a busybox prompt everytime. 

When I install the 10.04 LTS netbook edition on the stick itt works perfectly and installs on this netbook.

Should I file a bug?   Funny thing is I cannot get any distro to work after 10.04 LTS netbook edition to install not 11.04 and not 10.11.

That makes me think I should file a bug.   Buying an optical external cdrom sort kills the whole idea of buying a netbook.  Don't really want to buy an external optical drive.

---

### Post by Tart on 2012-02-17
try typing ```
live
``` in prompt. I couldn't boot from USB stick and all I got is a command prompt. Typing **live **continues with the boot process.

---

### Post by isantop on 2012-02-17
> **jsusanka said:**
> I don't have an external optical drive.  I have reinstalled 11.10 numerous times on different sticks.  Everytime the stick works on other computers but on this System 76 starling netbook I get a busybox prompt everytime. 

When I install the 10.04 LTS netbook edition on the stick itt works perfectly and installs on this netbook.

Should I file a bug?   Funny thing is I cannot get any distro to work after 10.04 LTS netbook edition to install not 11.04 and not 10.11.

That makes me think I should file a bug.   Buying an optical external cdrom sort kills the whole idea of buying a netbook.  Don't really want to buy an external optical drive.

What model is your Starling. For the Star1, you'll need to use Ubuntu 11.10, 32-bit. They were the only system we've ever sold to use a 32-bit processor. 

If it's a Star3 or later, then 64-bit is fine.

---

### Post by jsusanka on 2012-02-17
> **isantop said:**
> What model is your Starling. For the Star1, you'll need to use Ubuntu 11.10, 32-bit. They were the only system we've ever sold to use a 32-bit processor. 

If it's a Star3 or later, then 64-bit is fine.

thanks it is a star1 and I am using the 32 bit version

---

### Post by jsusanka on 2012-02-18
> **Tart said:**
> try typing ```
live
``` in prompt. I couldn't boot from USB stick and all I got is a command prompt. Typing **live **continues with the boot process.

thanks just tried that and still does not work spits some stuff and goes back to the prompt. 

I also configured grub2 to boot from the 11.10 iso and it still does it booting from the iso.  go figure.

---

### Post by isantop on 2012-02-20
Make sure it's 11.10 that you're trying to boot, and not 10.10. Also, make the USB disk on a version of Ubuntu newer than 10.10, as there were some issues with the Startup Disk Creator that may be having a bearing on your success now.

---

