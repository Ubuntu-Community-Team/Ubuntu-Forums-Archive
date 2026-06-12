---
title: "Installing Windows 2000 In VirtualBox - Crashes!"
date: 2008-09-09
forum: Virtualisation
---

### Post by Bye1918 on 2008-09-09
Okay, after figuring out that what I wanted to do in Win95 wasn't possible (and proving that as always, I'm an idiot), I moved on to Windows 2000. 

So I'm moving along, Windows 2000 is self-bootable and that's a beautiful thing. I get into the installer, and lo and behold, I make it most of the way through. But after the network drivers are installed, the next screen crashes!

Now I searched around on the web, and apparently this is a known bug. You're supposed to enter this: > VBoxManage setextradata «VBoxInternal/Devices/piix3ide/0/Config/IRQDelay» 1 to make it work. Something about modern computers being too fast for the installer.

I boot up terminal, copy-and-paste the code in, and I get this: 

> VirtualBox Command Line Management Interface Version 2.0.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling virtualBox->FindMachine(Bstr(argv[0]), machine.asOutParam()) at line 6888!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Could not find a registered machine named '«VBoxInternal/Devices/piix3ide/0/Config/IRQDelay»'
[!] Component   = VirtualBox, Interface: IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
[!] Callee      = IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
ben@ben-desktop:~$ 


How do I make the fix work? All I want is a working Windows in virtualbox. Is that too much to ask?

---

### Post by HermanAB on 2008-09-10
Virtualbox works best with Windows XP.  Other versions of Windows tend to crash.  If you need to run other Windows versions, use VMware.

Cheers,

Herman

---

### Post by Bakon Jarser on 2008-09-10
> **HermanAB said:**
> Virtualbox works best with Windows XP.  Other versions of Windows tend to crash.  If you need to run other Windows versions, use VMware.

Cheers,

Herman

Never heard that before.  I run win2k just fine in virtualbox.

If your motherboard lets you tweak your processor speed maybe you could slow it down.  Overclocking (or underclocking in this case) can have negative effects on your system though and in some cases break hardware.

---

### Post by HermanAB on 2008-09-10
For me, Win2k and Win3k runs about 30 minutes in Virtual box, then crashes.  That is the main reason I use VMware.

---

### Post by Bakon Jarser on 2008-09-10
> **HermanAB said:**
> For me, Win2k and Win3k runs about 30 minutes in Virtual box, then crashes.  That is the main reason I use VMware.

Win3k?  Somebody ripped you off.  We're not expecting win3k for another 992 years.

---

