---
title: "Virtualize or Dual Boot?"
date: 2009-10-15
forum: Virtualisation
---

### Post by Sub101 on 2009-10-15
Come 22nd October I will be wiping my computer of both Ubuntu and Vista and doing a fresh install.

I rarely use Vista, but will be purchasing the £30 Windows 7 Professional through Ultimate Steal. 

My question is, would you install Windows 7 and Ubuntu Karmic as a dual boot, or virtualize Windows 7 within Karmic?

Thanks for the advice.

---

### Post by pricetech on 2009-10-15
Chalk up one vote for virtualization.  I used to dual boot but now that I can virtualize, I'll never go back.

Your mileage may, of course, vary.

---

### Post by Sub101 on 2009-10-15
Are there any issues with product keys?

---

### Post by howefield on 2009-10-15
> **Sub101 said:**
> My question is, would you install Windows 7 and Ubuntu Karmic as a dual boot, or virtualize Windows 7 within Karmic?

Completely depends on what you want to use Windows 7 for. There are a few things that virtualisation simply cannot do yet.

---

### Post by doas777 on 2009-10-15
if your apps are light, then virtualize. if they are heavy, boot.

---

### Post by Marlonsm on 2009-10-15
> **doas777 said:**
> if your apps are light, then virtualize. if they are heavy, boot.

I agree.

But, IMO Windows XP is still the best for virtualization, as it's the lightest and runs pretty much every modern program for Windows.

---

### Post by uclugLee on 2009-10-15
If you want to do anything graphic-intensive, then dual boot.  Some things the virtual world just won't do yet.
 
I worked for a long time in the Windows world running (insert flavor here) Linux in a virtual machine.  Now I'm running Ubuntu on a Dell Studio 64 bit 4 gig ram and running XP in Virtualbox.  Life is good.

---

### Post by rlj1965 on 2009-10-15
I would suggest dual boot as this will not in any way limit Windows ability to run properly. I have had some bad experiences running windows as a guest in regards to graphics (limited) and usb (host try's to claim any device plugged in so no good for hot swap items like mp3 players, cameras and hard drives).

---

### Post by Sub101 on 2009-10-16
If I virtualize how would the license key work?

If I used the license on Jaunty then did a clean install to karmic what would happen? Would Windows allow this or see it as a different system?

---

### Post by doas777 on 2009-10-16
> **Sub101 said:**
> If I virtualize how would the license key work?

If I used the license on Jaunty then did a clean install to karmic what would happen? Would Windows allow this or see it as a different system?

I assume you are talking about windows activation? is your key OEM or retail? if it is OEM, it all depends on your virtualization layer. if you buy an OEM lic to use with VMWare or VBox or whatever, then your hardware shoudl appear the same to the guest OS, with minor exceptions. thus it should reactivate fine. if you were to try to use the OEM off a prebuilt box however it may not work as OEM lics are tied irrevocably to the mobo to which they were first activated on (but if you call MS and say "I gave my PC to the kid down the street for repair, and i don't know what he did, but he had to buy some parts..." they will usually give you a new key.)

---

### Post by Marlonsm on 2009-10-16
> **doas777 said:**
> "I gave my PC to the kid down the street for repair, and i don't know what he did, but he had to buy some parts..." they will usually give you a new key.)

Or just tell the truth, say you want Windows to be virtualized...

---

### Post by doas777 on 2009-10-16
> **Marlonsm said:**
> Or just tell the truth, say you want Windows to be virtualized...

that means that you are breaching the terms of the OEM license, so they will usually tell you to buy a new license.

---

### Post by Marlonsm on 2009-10-17
> **doas777 said:**
> that means that you are breaching the terms of the OEM license, so they will usually tell you to buy a new license.

Really?
I didn't know that... I thought the license said that you could only use that OS in the hardware it was first installed. So if you run a VM in that computer, technically it's still in the same hardware, so you can use it.

---

### Post by Jekshadow on 2009-10-18
> **doas777 said:**
> I assume you are talking about windows activation? is your key OEM or retail? if it is OEM, it all depends on your virtualization layer. if you buy an OEM lic to use with VMWare or VBox or whatever, then your hardware shoudl appear the same to the guest OS, with minor exceptions. thus it should reactivate fine. if you were to try to use the OEM off a prebuilt box however it may not work as OEM lics are tied irrevocably to the mobo to which they were first activated on (but if you call MS and say "I gave my PC to the kid down the street for repair, and i don't know what he did, but he had to buy some parts..." they will usually give you a new key.)

That didn't happen to me. I bought a Windows XP OEM (SP1 I think) a while ago, and I installed it on a PC I built, two instances of VirtalBox and another PC without any problems at all.

---

### Post by pricetech on 2009-10-22
In my case, the machines are all Dell and the installation CD has their VLA key embedded.  To virtualize I simply had to use the key from the COA attached to the computer.

I think it depends mostly on the type of license.  I've had MS give me a key and I've had them refuse.  Can't say I know for certain what the difference was between the two instances.

---

### Post by doas777 on 2009-10-22
> **Jekshadow said:**
> That didn't happen to me. I bought a Windows XP OEM (SP1 I think) a while ago, and I installed it on a PC I built, two instances of VirtalBox and another PC without any problems at all.
I'm not saying it won't let you, but it is technically a breach. part of the reason is that tech community aside, the vast majority of folks that want to virtualize are in the enterprise, the place where the real money comes from. makes it easier to sell site licensing, and other license bundles for large customers. it sucks.

---

### Post by doas777 on 2009-10-22
> **Marlonsm said:**
> Really?
I didn't know that... I thought the license said that you could only use that OS in the hardware it was first installed. So if you run a VM in that computer, technically it's still in the same hardware, so you can use it.

IANAL, but there are two ways it could go. the virtualization system provides an emulated hardware system to the guest, so it will have differant hardware identified, and often different drivers. you don't for instance, install nvidia drivers in a virtual guest, you install teh "virtualbox 3d video driver", or whatever. they could argue that this represents a differant PC.

---

