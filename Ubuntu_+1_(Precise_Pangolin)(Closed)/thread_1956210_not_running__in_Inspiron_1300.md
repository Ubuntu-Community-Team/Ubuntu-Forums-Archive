---
title: "not running  in Inspiron 1300"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-04-10
Trying beta 2 and also daily build each as live disc and try install daily build from boot menu - in all cases this machine just hangs after initial activity - after red dots progress etc 

I have tried (no acpi with nomodeset) it gets a bit further - text:
 'welcome to ubuntu precise (development branch)'

and then nothing more happens.
any suggestions please?
tia

---

### Post by candtalan on 2012-04-10
Ha.
Trying using the 
alternate iso beta2 image, and that is installing, up to the partitioner just now. Hopeful.

---

### Post by ventrical on 2012-04-10
> **candtalan said:**
> Trying beta 2 and also daily build each as live disc and try install daily build from boot menu - in all cases this machine just hangs after initial activity - after red dots progress etc 

I have tried (no acpi with nomodeset) it gets a bit further - text:
 'welcome to ubuntu precise (development branch)'

and then nothing more happens.
any suggestions please?
tia

I have a Dell Inspiron laptop. Has never failed with any Ubuntu release. I'll load up the RC now.

WOW.. I just tried my RC build on my Dell Inspiron B130 Laptop and it just stopped at the Ubuntu screen with the dots. Nothing .. no terminal .. nothing .. yet I used it live on a Dell Dimension 3100 and did a pretty well seamless install on another i386 machine.

  I'll try it in the Dell Opti that I burned it with (USB).

---

### Post by ventrical on 2012-04-10
Runs great on my Dell OptiGX270. Writing this with todays live build. Appears that there is a Ubiquity bias for Dell Inspirons.

 I'd file a bug but I just spent 6 hours trying to resurrect an WindowsXp system...

---

### Post by candtalan on 2012-04-10
Sounds like my experience
My install from the alternate  beta 2 image went ok, however it will not run up after the grub choice. Grub got installed ok.
Tried recovery mode and updating from root prompt but  it is not working. 
Guess I will have to await a daily build which  will work in some way?

Ideas?

---

### Post by ventrical on 2012-04-10
> **candtalan said:**
> Sounds like my experience
My install from the alternate  beta 2 image went ok, however it will not run up after the grub choice. Grub got installed ok.
Tried recovery mode and updating from root prompt but  it is not working. 
Guess I will have to await a daily build which  will work in some way?

Ideas?

The beta2-dvd worked great. So did beta1 and alpha. All of a sudden it seems the Dell Inspirons are blanked out. File a bug. and I'll  sign it.

or wait  and zsync  tommorows daily or the day after. Could be a major bug for Inspirons.

---

### Post by candtalan on 2012-04-10
I see a good grub menu (lots of other partitions on this demo laptop) then get 

b43-phy0 errors firmware file(s) not found b43/ucode5.fw and b43-open/ucode5.fw not found

I asked in irc #ubuntu-bugs and was suggested to
<astraljava> candtalan: Can you try adding a kernel parameter 'b43.blacklist=yes' for the next boot?

This worked (yay!) and it booted, albeit with a fleeting error message.

It installed as beta2 so I am now doing (498 ) updates 

It is suggested this  comes from an upstream bug, not ubuntu.

---

### Post by ventrical on 2012-04-10
I tired again with my Inspiron, just gently tapped the <shift> key, <Try Ubuntu>, works like a breeze. No bug.. just me needs a vacation or somthing.

---

### Post by candtalan on 2012-04-10
> **ventrical said:**
> I tired again with my Inspiron, just gently tapped the <shift> key, <Try Ubuntu>, works like a breeze. No bug.. just me needs a vacation or somthing.

Why the 'shift' key?

---

### Post by candtalan on 2012-04-10
> **candtalan said:**
> I see a good grub menu (lots of other partitions on this demo laptop) then get 
b43-phy0 errors firmware file(s) not found b43/ucode5.fw and b43-open/ucode5.fw not found
I asked in irc #ubuntu-bugs and was suggested to
<astraljava> candtalan: Can you try adding a kernel parameter 'b43.blacklist=yes' for the next boot?
This worked (yay!) and it booted, albeit with a fleeting error message.
It installed as beta2 so I am now doing (498 ) updates 
It is suggested this  comes from an upstream bug, not ubuntu.

The updates went in ok.
However, still the boot process would not complete unless I used the b43 blacklist insert as above.
After completion of the updates, and a reboot using the above string, I then used Ubuntu software centre to install the b43 firmware package

firmware-b43-installer
Installer package for firmware for the B43 driver

and then I am glad to say, the subsequent boot was normal and no kernel string was needed


edit:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/956677](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/956677)

---

### Post by ventrical on 2012-04-11
> **candtalan said:**
> Why the 'shift' key?


 I'm not sure .. I was just trying it out.. I was thinking I would get a Grub menu on the USB .. so I did it by reflex. No Grub menu .. but the opening menu (a little different from  the live open menu.) So I guess it just needed a nudge.

---

