---
title: "VMware and ActiveSync"
date: 2006-08-16
forum: Virtualisation
---

### Post by funnyguyfunnyguy on 2006-08-16
Has anyone successfully installed ActiveSync under VMware Server? I am unable to connect my audiovox smartphone with it. The phone does conect under Ubuntu (the host operating system) but windows cannot find it. Any ideas?

---

### Post by jack frost on 2006-09-17
I tried using xandros at one time because it came with that code-weavers software (cross-over office). It had active-sync included; but whenever I ran it..it froze up.. YOu may try to get a copy of that. I am hoping version 6 will have more support.

---

### Post by Bagboy23 on 2007-02-11
It works with Vmware workstation (5.5.3) and Vmware Player as Windows XP Home guest. But often does not recognise the connected USB. What you have to do is first enable USB to work with your laptop, then add that line to fstab (do a search on this forum). 

In Vmware workstation, it's an odd thing, but if you co to device manager (My Computer > Properties > Manage devices?) then it does a quick search for all things attached to the comp and then activesync kicks in). I have found that you have to do that a lot.

Alternatively, just use Vmware player and it always works. Everytime you attach the device it shows a "Generic Device" button at the top menu, if that is clicked, give it a few minutes and you PPC will be recognised. You have to give it a few minutes for it to kick in. I don't know why, but it's a guest OS, so it's slow.

---

### Post by cyberco on 2008-02-05
What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'

---

### Post by Andreas_DK on 2008-02-05
> **cyberco said:**
> What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'

:popcorn:Superb, this works also for me on my linux. I tried a lot before including changing registry parameters in the phone, but nothing worked. I was so desperate that it was just before to start a windows computer up again for this synchronization purpose only.

phone:
Windows Mobile Standard (Smartphone) wm6 (no touch screen)
HTC S710

host: ubuntu 7.10 with kernel 2.6.20-16-386

guest: 
VMware Player 2.0.2 build-59824 (vmplayer)
Windows XP Home Version 2002 SP2

Activesync 4.5.0 build 5096

Thanks a lot
Andreas

---

### Post by hillel213 on 2008-04-02
> **cyberco said:**
> What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'

I have an HTC Mogul phone and this suggestion worked!

However, please make sure you integrate some of the other suggestions just in case.  For example, [http://ubuntuforums.org/showthread.php?t=588225]("http://ubuntuforums.org/showthread.php?t=588225")

Host Machine: Ubuntu 7.11
Virtual Machine: Windows XP Home

Active Sync, Microsoft Outlook 2003, Windows Mobile 6

---

### Post by Calash on 2008-04-02
On Virutalbox it is flaky at best, randomly dropping the USB connection on my phone (HTC Mogul, Verizon version)

Going to try some of these suggestions and see if it helps :)

---

### Post by Cagnulein on 2008-11-19
Works for me too

phone:
Windows Mobile Standard (Smartphone) wm6 
HTC JaS Jar Universal

host: 2.6.26-ARCH 

guest:
VMware Workstation 6.0.5_109488-1
Windows XP Professional Version 2002 SP2

Activesync 4.5.0 build 5096

---

### Post by Andre-D on 2008-12-18
Anyone tried to make a VmWare Thinapp of Outlook 2007 + Activesync ?  - that would be SWEET, I will try some day.

---

### Post by baccand on 2009-10-07
> **cyberco said:**
> What solved this issue for me is changing the connection settings on my WM5 device. What I did:

On the WM5 device:
- go to settings/connections
- click 'usb to pc'
- turn off  'enable advanced network functionality'

I am using VMPlayer 2.5.3 and ....It works!
Thanks, now I am back in business!

---

### Post by RealG187 on 2009-10-07
> **jack frost said:**
> I tried using xandros at one time because it came with that code-weavers software (cross-over office). It had active-sync included; but whenever I ran it..it froze up.. YOu may try to get a copy of that. I am hoping version 6 will have more support.Don't you have to pay for cross-over office?

So there are more WM users who are also Ubuntu users?

---

