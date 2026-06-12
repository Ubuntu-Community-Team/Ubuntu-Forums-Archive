---
title: "virtualbox image?"
date: 2010-10-08
forum: Virtualisation
---

### Post by tech7 on 2010-10-08
Hey, I'm a noob to the virtualbox thing.  I installed windows 7 on a virtualbox on my ubuntu lucid and couldn't get things like usb, audio inputs, dvd-rom and whatnot to work. I also, for the life of me, could not get virtualbox additions to work out either.

So I went looking and found a "windows 7 virtualbox image" that already has some nice things like firefox and virtualbox additions installed.  

What is the deal with this?  Is using a "virtualbox image" different or better than just straight up installing an OS on virtualbox via DVD like I had done?

Any info would be greatly appreciated!!! Thanks!!

---

### Post by SeijiSensei on 2010-10-08
> **tech7 said:**
> So I went looking and found a "windows 7 virtualbox image" that already has some nice things like firefox and virtualbox additions installed.

Distributing a Virtualbox virtual machine image of Windows 7 infringes Microsoft's copyright in Windows.  Distributing the Windows Guest Additions infringes Oracle's. Furthermore, your image is going to have the same registration key as that of anyone else who downloads this image.  Once the key is registered by someone, all other copies of Windows with that key will be refused registration. Windows might run for another 30 days, but eventually it will no longer run.

In jurisdictions where Microsoft has an enforceable copyright, you can only legally install into Virtualbox a licensed copy of Windows with a unique registration key.  While there's usually a key on a sticker attached to computers running Windows, that won't pass muster with Microsoft if you try using it to register the copy in your virtual machine.  I explain why below.

The cheapest plausibly legal solution in the US is an "OEM" version of Windows which sells for $100 at [Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16832116754").  Even then it takes a bit of stretching to comply with the terms of the license:

[quote=Microsoft]
Use of this OEM System Builder Channel software is subject to the terms of the Microsoft OEM System Builder License. This software is intended for pre-installation on a new personal computer for resale. This OEM System Builder Channel software requires the assembler to provide end user support for the Windows software and cannot be transferred to another computer once it is installed. To acquire Windows software with support provided by Microsoft please see our full package "Retail" product offerings.[/quote]

You might be able to comply with the resale clause by selling the computer to yourself, though whether installation in a virtual machine constitutes "pre-installation on a new personal computer" is clearly open to question.  The support requirement is easily met; you'll be providing it to yourself. 

The next clause is significant and explains why you can't use the registration key on a sticker to validate an installation in a VM.  The version of Windows that came with your computer is also an OEM version and "cannot be transferred to another computer once it is installed."

Finally if you want a fully-licensed version of Windows with support from Microsoft you can buy the "retail" version; it costs [$174]("http://www.newegg.com/Product/Product.aspx?Item=N82E16832116716&cm_re=window_7_retail-_-32-116-716-_-Product").

I don't think the [Family Pack]("http://www.newegg.com/Product/Product.aspx?Item=N82E16832116775&cm_re=window_7_retail-_-32-116-775-_-Product") upgrade version, with 3 licenses for about $150, works in a VM either.  As an upgrade, it only installs if it finds a licensed copy of Windows already on the machine.  There obviously won't be one on a new virtual machine.

---

### Post by snowpine on 2010-10-08
SeijiSensei is correct; the only scenario that we are allowed to discuss on these forums is installing a legal, retail version of Windows.

Assuming that your copy of Windows is legit :) let me ask, are you use the "OSE" version of VirtualBox from the Ubuntu repositories, or the "PUEL" version from virtualbox.org? You will need the PUEL version if you want to get your USB ports working. More info is available in the Virutalbox Manual at virtualbox.org.

---

### Post by tech7 on 2010-10-09
wow, thanks snowpine..

Yep, I'm using OSE.  So, I'm going to check into PUEL, now.  I'll look into that manual, too.  

Thanks a lot guys!!!

---

### Post by tech7 on 2010-10-14
I never did actually get the usb ports to work with puel..  but i did get the whole shared file thing down pat, and that actually totally defeated the purpose of using the usb ports for me..  thanks for the suggestion!!

---

