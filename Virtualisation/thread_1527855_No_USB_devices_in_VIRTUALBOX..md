---
title: "No USB devices in VIRTUALBOX."
date: 2010-07-09
forum: Virtualisation
---

### Post by timtincher on 2010-07-09
My host os: Windows XP 
My guest: Ubuntu Lucid Lynx

I was trying to attach my USB device to my virtual machine, but no drop down menu appeared. I know it's not the HOST OS' fault because all of the USB devices are working properly.

What is wrong? What do I do?

---

### Post by timtincher on 2010-07-09
Failed to access USB subsystem

Could not load the Host USB Proxy Service
(VERR_NOT_FOUND). The service may not be installed on the host computer.

 p, li { white-space: pre-wrap; }     Result Code: 
  [FONT= ]E_FAIL (0x00004005)[/FONT]
   Component: 
  Host
   Interface: 
  IHost {35b004f4-7806-4009-bfa8-d1308adba7e5}
   Callee: 
  IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}


WHAT DO I DO about this? So I can use my USB devices in my virtual PC.

SAME info as the earlier thread.

---

### Post by jflaker on 2010-07-09
is that the downloaded version from their website or the one available through the repositories?

The one from the repositories is the "Community edition - CE) and doesn't support USB....

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Follow the instructions to add the virtualbox repositories then get THEIR version...You will need to adjust as you upgrade Ubuntu versions

I have followed their instructions and the full version USB works fine.

---

### Post by timtincher on 2010-07-31
But I need Virtualbox for Windows. Not for Ubuntu. Windows is the Host operating system.

---

### Post by TNT1 on 2010-07-31
> **timtincher said:**
> But I need Virtualbox for Windows. Not for Ubuntu. Windows is the Host operating system.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Get the PUEL version for windoze hosts...

If that doesn't help, search the vbox FAQ's or try a windoze forum?

---

### Post by Meow27 on 2010-07-31
did you try running virtualbox as administrator? (in otherwords, are you an admin account?)

---

### Post by Kevuntu on 2010-07-31
First, you have to use the PUEL version (not OSE) for your windoz host.

Direct Download: [http://download.virtualbox.org/virtualbox/3.2.6/VirtualBox-3.2.6-63112-Win.exe](http://download.virtualbox.org/virtualbox/3.2.6/VirtualBox-3.2.6-63112-Win.exe)

Maybe you need to be admin as well.

It should work.

---

