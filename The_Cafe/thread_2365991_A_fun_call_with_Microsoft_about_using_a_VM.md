---
title: "A fun call with Microsoft about using a VM"
date: 2017-07-12
forum: The Cafe
---

### Post by stlu on 2017-07-12
A friend of mine wants to experiment with various OS's in virtual machines.  He also was thinking about putting Microsoft's latest OS in a VM too.  But he was unwilling to find out if it was possible.

So as a favour, I called Microsoft to find out.  The representative asked me what OS I was running.  I said "let me check".  She replied with "Do you want me to walk you through it?" and that made me smile.  What are the chances she would tell me to open a terminal and type 'lsb_release -a'?  So I replied with "Ubuntu 16.04".  She said "What?" So I said it again.  Then she said "Can you spell it?"  So I did.  Then finally, after checking with a supervisor, she told me that it would work in a VM.

So my deed of that day: Educating at least two Microsoft staff about Ubuntu!!!

---

### Post by TheFu on 2017-07-12
You could have listed about 20 non-MSFT OSes ... just to get a reaction.

So ... will Win10 run inside a VM?  I've never seen Win10, ever, so I'm slightly curious.  I wasn't able to get passed the EULA that Windows requires now.

---

### Post by stlu on 2017-07-12
Yes, they said it will work -- I said I was using Oracle Virtualbox, so I don't know about other virtualization technologies.

---

### Post by QIII on 2017-07-12
I use Win10 in a VBox VM.

---

### Post by TheFu on 2017-07-12
> **stlu said:**
> Yes, they said it will work -- I said I was using Oracle Virtualbox, so I don't know about other virtualization technologies.

Any mention about specific license needs?  Like if you have a pre-installed Win10 machine, can that license be moved into a VM running on the same machine? That wasn't possible with WinXP, Win7/8 for pre-installed OEM versions.

---

### Post by HermanAB on 2017-07-13
I've been running Win10 in VMs since 2015.

[www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html](www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html)

---

### Post by deadflowr on 2017-07-13
You were probably pronouncing Ubuntu wrong.

---

### Post by Rocky_Bennett on 2017-07-15
> **TheFu said:**
> Any mention about specific license needs?  Like if you have a pre-installed Win10 machine, can that license be moved into a VM running on the same machine? That wasn't possible with WinXP, Win7/8 for pre-installed OEM versions.



I run both Windows 7 and Windows in a VirtualBox in my openSUSE 42.2 installation. You can run Windows 10 with or without a license indefinitely, but you can only run Windows 7 without a license for one year.

---

### Post by TheFu on 2017-07-15
> **Rocky_Bennett said:**
> I run both Windows 7 and Windows in a VirtualBox in my openSUSE 42.2 installation. You can run Windows 10 with or without a license indefinitely, but you can only run Windows 7 without a license for one year.

There are many different sorts of licenses from MSFT.  I'm 100% positive you cannot grab any install disk, put it into a system, and install that inside a VM.  I know it doesn't work all the time, because OEM installs validate the correct/expected BIOS is there. VMs never show the real BIOS.  Perhaps if you have access to retail or volume license installation files, then this isn't an issue.  Most of the end-users here will have OEM licenses that came with a PC.

My retail Win7 license demands to be authenticated within 90 days or I have to reinstall it.  Ok, I've never gone that long and I've never let it run out to really KNOW what it does.  I'm going on what the popup reminders said last time I installed it, many years ago.   Last time I moved the retail license between VM hosts, I had to call MSFT and ask for it to be allowed. To the OS, it appeared the entire motherboard had been changed. It is the same VM, I just replaced the underlying physical hardware, so I don't see the issue. 
I also have an OEM license for Win7. The OEM licenses wouldn't move between different models of the same vendor's laptops. I got the recovery disks mixed up once.

I plan to move the retail Win7 VM to a new physical system in the next year (Ryzen!). Hopefully, it won't be any hassle.  I know I've never had any issues moving Linux VMs.

Win10 ... know nothing about it. Considering they gave it away for a year, I don't know if they bothered with their previously strict license methods that began with WinXP.  I never grabbed a copy and never tried it, even inside a VM.  Couldn't swallow the EULA demands. Just couldn't do it.

My question was an attempt to gain clarification from 'the horse mouth' about VM licensing today with MSFT.  I have no interest in running in a grey area and will NOT tell any clients to do so either.

---

### Post by mikewhatever on 2017-07-15
> **stlu said:**
> A friend of mine wants to experiment with various OS's in virtual machines.  He also was thinking about putting Microsoft's latest OS in a VM too.  But he was unwilling to find out if it was possible.

So as a favour, I called Microsoft to find out.  The representative asked me what OS I was running.  I said "let me check".  She replied with "Do you want me to walk you through it?" and that made me smile.  What are the chances she would tell me to open a terminal and type 'lsb_release -a'?  So I replied with "Ubuntu 16.04".  She said "What?" So I said it again.  Then she said "Can you spell it?"  So I did.  Then finally, after checking with a supervisor, she told me that it would work in a VM.

So my deed of that day: Educating at least two Microsoft staff about Ubuntu!!!

It's actually not too funny. After thirteen years of existence and a considerable investment, Ubuntu still remains an obscure, niche OS.
There are people that like it that way, which is funny indeed.

---

### Post by bluemagoo on 2017-07-18
I have two copies of windows 7 64bit running as vm's;  had them for years.  no real issues, other than onetime I had to re-install the key of one of them.  MS assumed it was a bootleg, but it's not, these are legal copies.

---

### Post by paulconnolly on 2017-07-21
I think I've ran Win7 and Win10 on ubuntu oracle vm in the past

---

### Post by ian-weisser on 2017-07-21
I run Win 10, with retail-purchased license (not pre-installed), in in a vbox guest at work.
Install is just like bare metal - simply boot the guest from the installer.
Put in your license key when asked.
Done.

---

### Post by TheFu on 2017-07-21
And if the MS-Windows license was included, pre-installed, with the PC?  
Can it be moved into a VM?

---

