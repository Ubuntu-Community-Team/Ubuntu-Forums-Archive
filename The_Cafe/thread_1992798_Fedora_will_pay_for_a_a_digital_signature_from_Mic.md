---
title: "Fedora will pay for a a digital signature from Microsoft."
date: 2012-05-31
forum: The Cafe
---

### Post by Linuxratty on 2012-05-31
I guess Ubuntu will have to pay up to Microsoft as well.

> In order to get its Linux distribution to run on the next generation of secured desktop computing hardware, the Fedora Project will obtain a digital signature from Microsoft, a developer from the project announced Wednesday.

[http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html](http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html)

---

### Post by MisterGaribaldi on 2012-05-31
This is unfortunate. Why are they doing this? They should be enjoining a class-action suit against Microsoft on the basis that this is anti-competitive behavior. Heck, Mozilla is already suing them for shutting out FF on Windows Mobile 8.

---

### Post by Bandit on 2012-06-01
Obtaining a digital signature is normally just a way for a company to let the consumer know they can trust the software is safe to install on windows. Which is something you would want if you were building software for windows. So why is Redhat/Fedora doing this again?

---

### Post by pbpersson on 2012-06-01
Apparently because Microsoft "owns" all hardware vendors, they have forced all hardware vendors to install security in the firmware to make the computers "safer".  Microsoft owns the "keys" to let the OS access the computer hardware.  If the Linux distro does not have a valid key it cannot access the hardware and the OS will not boot.

Every Linux distro will need to have a key or they will not get in.

You know....Microsoft controls the world - or at least they are moving in that direction.

---

### Post by Copper Bezel on 2012-06-01
Hey now, let's be fair. With Apple and Amazon owning all digital content and Google and Facebook owning all personal information, all Microsoft is left owning is some PCs.

And the Secure Boot feature on Intel machines can be disabled. This is only about making that step unnecessary, since it might scare off some potential users. Of course, neither of these options will be available for ARM machines that ship with Windows.

(The signed kernel modules make it a little irrelevant, too, don't they? You'd still have to disable secure boot if your Intel machine has an Nvidia graphics card, or a Broadcom wireless chip, since Fedora doesn't ship with those drivers.)

---

### Post by wilee-nilee on 2012-06-01
Sometimes compromises have to be made, personally I would be happy to see ARM users able to use Linux on their set ups.

If there are legal issues, the courts will probably take care of that part.

I'm not pro any OS to be honest, but I rarely use MS except when needed.

I started on open source and prefer to use it, but all have a good, bad and ugly side to them.

---

### Post by candtalan on 2012-06-01
Implementing UEFI Secure Boot in Fedora
May. 30th, 2012 11:11 pm mjg59

[http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)

I am concerned that  in the normal course of events, a dual boot situation will be significantly affected also.

---

### Post by sffvba[e0rt on 2012-06-01
*Threads **merged**.*


404

---

### Post by alexfish on 2012-06-01
> **MisterGaribaldi said:**
> This is unfortunate. Why are they doing this? They should be enjoining a class-action suit against Microsoft on the basis that this is anti-competitive behavior. Heck, Mozilla is already suing them for shutting out FF on Windows Mobile 8.

It does not take much to work out

hARMless, they want **** I will hold back on the  last 2 **

[http://www.raspberrypi.org/archives/805](http://www.raspberrypi.org/archives/805)

---

### Post by mörgæs on 2012-06-01
Countless developers build an OS on a voluntary basis, and in the last step a fee has to be paid to Microsoft in order to install. Could hardly be any worse.

---

### Post by Erik1984 on 2012-06-01
I've read that article yesterday, I'm still not quite sure if I understand it correctly. That UEFI stuff is quite complex. Can someone explain what exactly Fedora will obtain from Microsoft if they pay up?

---

### Post by alexfish on 2012-06-01
> **Euroman said:**
> I've read that article yesterday, I'm still not quite sure if I understand it correctly. That UEFI stuff is quite complex. Can someone explain what exactly Fedora will obtain from Microsoft if they pay up?


**UEFI** ,, should **never** have been **ACCEPTED** , those that accept UEFA , don't think what my **BRAIN** is thinking , I am to old to care.

---

### Post by wilee-nilee on 2012-06-01
> **Euroman said:**
> I've read that article yesterday, I'm still not quite sure if I understand it correctly. That UEFI stuff is quite complex. Can someone explain what exactly Fedora will obtain from Microsoft if they pay up?

All computers except ones with ARM processors can be unlocked to run other than MS OS's

Post 14 is more accurate I think.

---

### Post by JDShu on 2012-06-01
> **Euroman said:**
> I've read that article yesterday, I'm still not quite sure if I understand it correctly. That UEFI stuff is quite complex. Can someone explain what exactly Fedora will obtain from Microsoft if they pay up?

My understanding is that it allows users who want to install Fedora on UEFI enabled machines to have the same ease of installation as they do now, instead of needing to find the option to disable secure boot in the UEFI interface.

---

### Post by alexfish on 2012-06-01
> **JDShu said:**
> My understanding is that it allows users who want to install Fedora on UEFI enabled machines to have the same ease of installation as they do now, instead of needing to find the option to disable secure boot in the UEFI interface.

Understand the difference between what is free as in choice and the difference 
between a free choice that is been taxed by a cooperate company , that had nothing to do with that choice ..

reading the article will help to explain , already had been posted
[http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html](http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html)
and read about where, Ferdora and the "developers" to which have helped Fedora "FREE OF ANYTHING" to be what it is today , and also is a choice for an ARM platform.

---

### Post by neu5eeCh on 2012-06-01
> **alexfish said:**
> ....and read about where, Ferdora and the "developers" to which have helped Fedora "FREE OF ANYTHING" to be what it is today , and also is a choice for an ARM platform.

[CENTER] **All your base are belong to us!**
OK... I jest... but your sentence has to be among _*the*_ most incomprehensible I have _ever_ read. :-s[/CENTER]

---

### Post by DoubleClicker on 2012-06-01
Actually, Fedora isn't paying Microsoft.  They are paying VeriSign 

[QUOTE=Mathew Garret]
The last option wasn't hugely attractive, but is probably the least worst. Microsoft will be offering signing services through their sysdev portal. It's not entirely free (there's a one-off $99 fee to gain access edit: The $99 goes to Verisign, not Microsoft - further edit: once paid you can sign as many binaries as you want), but it's cheaper than any realistic alternative would have been. It ensures compatibility with as wide a range of hardware as possible and it avoids Fedora having any special privileges over other Linux distributions. If there are better options then we haven't found them. So, in all probability, this is the approach we'll take. Our first stage bootloader will be signed with a Microsoft key.[/QUOTE][http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)

---

### Post by MadmanRB on 2012-06-01
> **Copper Bezel said:**
> And the Secure Boot feature on Intel machines can be disabled

I am sure AMD mobo's will offer the same, secure boot will not be a deterrent for linux for long

---

### Post by alexfish on 2012-06-01
> **VTPoet said:**
> [CENTER] **All your base are belong to us!**
OK... I jest... but your sentence has to be among _*the*_ most incomprehensible I have _ever_ read. :-s[/CENTER]


To many years of programming some where else :(

some times it  is meant to be , pick out the bits;)

---

### Post by mips on 2012-06-01
> **DoubleClicker said:**
> Actually, Fedora isn't paying Microsoft.  **They are paying VeriSign** 


The very same company Mark Shuttleworth sold his company (Thawte) to and made his millions from.

---

### Post by forrestcupp on 2012-06-01
> **VTPoet said:**
> [CENTER] **All your base are belong to us!**
OK... I jest... but your sentence has to be among _*the*_ most incomprehensible I have _ever_ read. :-s[/CENTER]:lol:

> **DoubleClicker said:**
> Actually, Fedora isn't paying Microsoft.  They are paying VeriSign 

[http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)
So it's going to cost them a one-time $99 fee, and then everyone in the world can install it? Big deal.

---

### Post by rucadulu on 2012-06-01
[COLOR=black][FONT=Tahoma]Just another power grab by Microsoft. This is another reason why I will never ever by another Microsoft or Apple product. Both companies have taken steps to lock down a user’s freedom of choice and I for one will not give either another dollar of my money. There are too many other choices available for me to worry about these two companies products. I can only hope that the rest of the consumer world will wake up someday and choose to leave Microsoft and Apple products on the shelf collecting dust. [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by MisterGaribaldi on 2012-06-01
Well then, I think we the buying public should do what we can to update our systems to the latest pre-UEFI hardware, and then stop buying new, compromised, gate-keeper hardware.

In fact, regardless of whether we can get any solidarity behind that, we need to re-label UEFI in the public as something far more truthful and reflective of reality: monopolistic gate-keeper hardware. Maybe we can use the acronym MGKH, unless someone here can come up with a better term.

---

### Post by xedi on 2012-06-01
> **MisterGaribaldi said:**
> 
In fact, regardless of whether we can get any solidarity behind that, we need to re-label UEFI in the public as something far more truthful and reflective of reality

The FSF has already done it and calls it RestrictedBoot

[https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

---

### Post by MisterGaribaldi on 2012-06-01
> **xedi said:**
> The FSF has already done it and calls it RestrictedBoot

[https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

Well, I don't mind it so much when it's the FSF who steals my ideas before I have them. At least they're a force for good.

---

### Post by forrestcupp on 2012-06-01
> **rucadulu said:**
> Just another power grab by Microsoft. This is another reason why I will never ever by another Microsoft or Apple product.

Well, Microsoft contributes to the Linux kernel, so I guess you're screwed. :)

---

### Post by Paqman on 2012-06-01
> **xedi said:**
> The FSF has already done it and calls it RestrictedBoot

[https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement](https://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/statement)

Well, glad that's sorted then. I'm sure Microsoft will be in full retreat shortly.

---

### Post by Bandit on 2012-06-01
> **MisterGaribaldi said:**
> Well then, I think we the buying public should do what we can to update our systems to the latest pre-UEFI hardware, and then stop buying new, compromised, gate-keeper hardware.....

I agree. I sure as heck will not ever purchase something that will try to force me to use Win or Mac just so it will run. I will revert back to using a freaking Etch-a-Sketch before that happens.

---

### Post by tkod on 2012-06-01
I dont really get what's the big deal and all the MS hate. As much as I understand UEFI boot can be disabled in every x86 system bios. Also other operating systems than Windows can be signed, but it will be hard for linux due to fragmentation. What Fedora is paying is one time 99 bux fee, and it is to Microsoft because that's the easiest way, using MS's certificate. I don't think MS really had an elaborate and evil plan for winning those 99 bux. 

It could be a problem with arm devices, because if they ship with MS OS they will be locked to this os. Although I'm not sure, I think they just might be locked to certified OSs which will probably include android. If thats not the case, I don't think MS have much of a chance on the mobile market against Android. And therefore don't really have the influence to lock hardware. 

But as for desktop systems there will be nothing different and evil from what I've read. Fedora are just paying a one time fee so their users don't have to turn off an option in the bios, and maybe for a more flawless dual boot behaviour.

I hope I haven't offended anyone, but a lot of the conclusions made here seem completely wrong to me.

---

### Post by alexfish on 2012-06-01
> **Bandit said:**
> I agree. I sure as heck will not ever purchase something that will try to force me to use Win or Mac just so it will run. I will revert back to using a freaking Etch-a-Sketch before that happens.
Dam

Sold my Etch-a-Sketch 10 years ago , at a car boot sale , only got 50p for it

Anyone got a spare one ? , before the Price goes UP

---

### Post by KiwiNZ on 2012-06-01
It will make no difference to me.

---

### Post by Primefalcon on 2012-06-01
> **KiwiNZ said:**
> It will make no difference to me.
Nor to me, I'll ever custom build or buy from a place that will sell computers without windows such as system76.

Unfortunately I can see this holding back adoption possibly though large scale or at least adding another hurdle.

Since random user B wont be able to install an OS without buying or building a new system... people just wont do it

---

### Post by KiwiNZ on 2012-06-01
> **Primefalcon said:**
> Nor to me, I'll ever custom build or buy from a place that will sell computers without windows such as system76.

Unfortunately I can see this holding back adoption possibly though large scale or at least adding another hurdle

That's the way, allow your wallet to do your talking. I buy Macs for OSX, I also run Linux Distros in Virtual Machine or of test PC's. I will not worry as it's not worth worrying about.

---

### Post by alexfish on 2012-06-01
> **tkod said:**
> I dont really get what's the big deal and all the MS hate. As much as I understand UEFI boot can be disabled in every x86 system bios. Also other operating systems than Windows can be signed, but it will be hard for linux due to fragmentation. What Fedora is paying is one time 99 bux fee, and it is to Microsoft because that's the easiest way, using MS's certificate. I don't think MS really had an elaborate and evil plan for winning those 99 bux. 

It could be a problem with arm devices, because if they ship with MS OS they will be locked to this os. Although I'm not sure, I think they just might be locked to certified OSs which will probably include android. If thats not the case, I don't think MS have much of a chance on the mobile market against Android. And therefore don't really have the influence to lock hardware. 

But as for desktop systems there will be nothing different and evil from what I've read. Fedora are just paying a one time fee so their users don't have to turn off an option in the bios, and maybe for a more flawless dual boot behaviour.

I hope I haven't offended anyone, but a lot of the conclusions made here seem completely wrong to me.
I could not give a monkey if it where a 1 cent fee

it is the principle of the first action that sets things in motion

What next

---

### Post by KiwiNZ on 2012-06-01
> **alexfish said:**
> I could not give a monkey if it where a 1 cent fee

it is the principle of the first action that sets things in motion

What next

Don't hurt the Monkeys:P

---

### Post by alexfish on 2012-06-01
> **kiwinz said:**
> don't hurt the monkeys:p:p

ADDED a bed time story

I hiked through the Batu Caves just outside of Kuala Lumpur and afterwards, I found myself surrounded by monkeys.  They were a little more than "friendly", and ventured into a word that is better described as "vicious".  

[http://www.flickr.com/photos/stuckincustoms/2366980580/](http://www.flickr.com/photos/stuckincustoms/2366980580/)

---

### Post by malspa on 2012-06-03
> **tkod said:**
> I dont really get what's the big deal and all the MS hate. As much as I understand UEFI boot can be disabled in every x86 system bios. Also other operating systems than Windows can be signed, but it will be hard for linux due to fragmentation. What Fedora is paying is one time 99 bux fee, and it is to Microsoft because that's the easiest way, using MS's certificate. I don't think MS really had an elaborate and evil plan for winning those 99 bux. 

It could be a problem with arm devices, because if they ship with MS OS they will be locked to this os. Although I'm not sure, I think they just might be locked to certified OSs which will probably include android. If thats not the case, I don't think MS have much of a chance on the mobile market against Android. And therefore don't really have the influence to lock hardware. 

But as for desktop systems there will be nothing different and evil from what I've read. Fedora are just paying a one time fee so their users don't have to turn off an option in the bios, and maybe for a more flawless dual boot behaviour.

I hope I haven't offended anyone, but a lot of the conclusions made here seem completely wrong to me.

This is how I'm seeing things, too.

---

### Post by JDShu on 2012-06-03
> **tkod said:**
> 
But as for desktop systems there will be nothing different and evil from what I've read. Fedora are just paying a one time fee so their users don't have to turn off an option in the bios, and maybe for a more flawless dual boot behaviour.


Well for one thing, this is a huge problem in terms of usability. Linux has a reputation for being difficult to use already, and now you have to expect people who want to try Linux or any other OS on their x86 system to go into the UEFI interface to turn some option off? Remember the interface is not necessarily standard either.

The other problem is that Microsoft has the power to push an update over WIndows to the system that invalidates Fedora's key and make it stop working. That would be an issue for dual booters. They would need a good reason to do it, for example if signed code was used for an attack.

This isn't really a case of Microsoft hatred, but that the solution to a (important) problem is putting power into Microsoft's hands. If you trust the company, fine, but you still have to acknowledge what is happening.

---

### Post by oldfred on 2012-06-03
I can the the Microsoft marketing machine saying you do not have security unless you run their system. And since their systems were the epitome of lack of security many will then buy into the new "improved" Windows.

But good ole Ben Franklin was ahead of his time - parapharsed.

He who sacrifices freedom for security deserves neither.

---

### Post by alexfish on 2012-06-03
> **malspa said:**
> This is how I'm seeing things, too.

[http://www.dltk-teach.com/rhymes/monkeys/words.htm](http://www.dltk-teach.com/rhymes/monkeys/words.htm)

> Garrett admits that even this approach has drawbacks. Some kernel  functionality will be locked down. Also, kernel modules will need to be  signed. Developers who compile their own kernel binary will have to  figure out a way to get it signed, either by applying to the firmware  company directly, or creating a shim similar to Fedora's bootloader. Or,  they can run their binaries on those computers that don't require  certificates.

---

### Post by candtalan on 2012-06-03
> **tkod said:**
> I dont really get what's the big deal and all the MS hate. As much as I understand UEFI boot can be disabled in every x86 system bios. Also other operating systems than Windows can be signed, but it will be hard for linux due to fragmentation. What Fedora is paying is one time 99 bux fee, and it is to Microsoft because that's the easiest way, using MS's certificate. I don't think MS really had an elaborate and evil plan for winning those 99 bux. 

Countless of my friends started with Windows, and now have dual boot configuration. At first they were cautious and it was a comfort to them to know they also still had Windows, like they always had. In future, with UEFI, and say, an unsigned Ubuntu, I will not be able to offer them dual boot. Most of such people in future will prefer to stay with the Windows they are uncomfortable with, but that they are familiar with, rather than take the leap to another system. The Microsoft move is a very efective method of gaining control of the hardware, while apparently having the very best of reasons to do so. Kudos to Microsoft for this, however much I dislike the situation.
BTW I do not hate Microsoft, I just see them as a remarkable and successful company which uses business methods I dislike, and has products which exploit the users. Microsoft is not the only company to do this.

---

### Post by xedi on 2012-06-03
> **candtalan said:**
>  In future, with UEFI, and say, an unsigned Ubuntu, I will not be able to offer them dual boot.

Will Windows 8 not run with UEFI secure disabled?

---

### Post by malspa on 2012-06-03
> **JDShu said:**
> Well for one thing, this is a huge problem in terms of usability. Linux has a reputation for being difficult to use already, and now you have to expect people who want to try Linux or any other OS on their x86 system to go into the UEFI interface to turn some option off? Remember the interface is not necessarily standard either.

Is it any more difficult than when you have to go into the BIOS to change boot order so that you can can boot with a CD or flash drive? Just wondering.

---

### Post by malspa on 2012-06-03
> **alexfish said:**
> [http://www.dltk-teach.com/rhymes/monkeys/words.htm](http://www.dltk-teach.com/rhymes/monkeys/words.htm)

Insult noted. Cute.

---

### Post by ExSuSEusr on 2012-06-03
> **rucadulu said:**
> [COLOR=black][FONT=Tahoma]Just another power grab by Microsoft. This is another reason why I will never ever by another Microsoft or Apple product. Both companies have taken steps to lock down a user’s freedom of choice and I for one will not give either another dollar of my money. There are too many other choices available for me to worry about these two companies products. I can only hope that the rest of the consumer world will wake up someday and choose to leave Microsoft and Apple products on the shelf collecting dust. [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

Never happen.  The average person is too much a mindless sheep to think otherwise - and it is getting worse.

---

### Post by candtalan on 2012-06-03
> **xedi said:**
> Will Windows 8 not run with UEFI secure disabled?

No, not as far as I understand. That is the whole point.
Currently (with non Windows 8 compatible hardware) both Windows and non Windows share the same mainboard environment and configuration. It remains to be seen in future what method each different manufacturer will use to meet the EUFI spec to allow disable of Secure boot. Maybe it will be a mainboard hardware jumper? Exsiting implementations are buggy, and because the main customer (Microsoft) will use secure boot, then (some?) manufacturers may not give a good EUFI disable a suitable priority. 'Oh we are sorry, it does not work for such and such. What a shame, never mind'.

---

### Post by alexfish on 2012-06-03
> **candtalan said:**
> No, not as far as I understand. That is the whole point.
Currently (with non Windows 8 compatible hardware) both Windows and non Windows share the same mainboard environment and configuration. It remains to be seen in future what method each different manufacturer will use to meet the EUFI spec to allow disable of Secure boot. Maybe it will be a mainboard hardware jumper? Exsiting implementations are buggy, and because the main customer (Microsoft) will use secure boot, then (some?) manufacturers may not give a good EUFI disable a suitable priority. 'Oh we are sorry, it does not work for such and such. What a shame, never mind'.

It has Far more reaching implications than what has already mentioned  , 

There are new communication devices which require Kernel modification

No New Key = sorry , you can not connect , END OF , so your only recourse will be to use.

Yes you have guessed it!

Every one , Do you get the picture.

---

### Post by ExSuSEusr on 2012-06-03
If this isn't stopped, it will be the end end of Linux as we know it now.  In terms of it being used by the home user.  

Linux has made leaps and bounds over the past several years to the point that granny can even use it. 

This IS Microsoft gaining total control over the PC world.  TOTAL control.  The hardware vendors are going to do what ever MS tells them to do.  They pretty much have to.  When 90-some-odd percent of the World's computers use Windows and that 90-some-odd percent is your customer base.  What else are they going to do?

And, if you really are that naive that you actually buy into "the manufactures are eager to give the end user a choice to turn UEFI off..." then I want to sell you some beach front property in Arizona.  'Cause you can bet your *** that behind closed doors Microsoft is threatening to destroy them if they don't make it impossible to allow alternate OS's to access their products.

The average user doesn't care about this.  The average user uses Windows and Windows is all they know.  Most of them are far too lazy to spend even 5 minutes reading about other OS's... let alone actually try one.

If the average user (aka voter) doesn't care, the politicians don't care, if they don't care - nothing will be done about it.

This will make me buy Apple.

---

### Post by llua+ on 2012-06-03
> **candtalan said:**
> No, not as far as I understand. 
[citation needed]

---

### Post by MisterGaribaldi on 2012-06-03
Hmm... Aren't there governments which have pitched a fit over region-restricted DVDs/DVD players? If so, maybe more of that attitude is all that's needed to stop this from going anywhere. I can't imagine, for instance, ASUS / ABIT / Gigabyte / etc. giving up huge markets where such restrictions are made illegal, just to accomodate Microsoft.

I mean, obviously (and sadly) my country is too stupid to do anything about this, but surely not every government is as bad as this one. And if it can be made uneconomical enough, then maybe we'll only see this on brand-name systems but DIY-channel MOBOs won't have this built in (or it will be enable-able for Win8 compatibility).

Other than that, we're all screwed, and this could be the beginning of the end of Linux-on-the-desktop. As much as LotD no longer is of any use to me personally, I don't want to see it killed.

---

### Post by JDShu on 2012-06-03
> **malspa said:**
> Is it any more difficult than when you have to go into the BIOS to change boot order so that you can can boot with a CD or flash drive? Just wondering.

It's more difficult to need to change both things, that's for sure.

---

### Post by candtalan on 2012-06-03
> **llua+ said:**
> [citation needed]

Information is not very easy to find. May be a coincidence? However this
[http://arstechnica.com/information-technology/2012/01/windows-8s-locked-bootloaders-much-ado-about-nothing-or-the-end-of-the-world-as-we-know-it/](http://arstechnica.com/information-technology/2012/01/windows-8s-locked-bootloaders-much-ado-about-nothing-or-the-end-of-the-world-as-we-know-it/)
implies that a situation exists (or should hopefully exist) where in PCs, secure boot can be turned off by the user (re firmware). If this guess is true then by running GNU/Linux (unsigned) dual boot and Windows 8, then Windows 8 must be subsequently run with 'secure boot' turned off.
GNU/Linux advertising: 'Improve your life by turning off Microsoft Secure Boot'. Mmm, can I see that working? Maybe not.

One thing is very very clear to me. Dual boot is central to all of my activities with *many* friends. Yet nowhere in the often very detailed discussions of this and that specifications and requirements and options whatever (if they can be found, and then believed), nowhere is 'dual boot' or its practicality mentioned. I suspect that the purchased digital signature method may be, unfortunately, the only practical way out.

---

### Post by ExSuSEusr on 2012-06-03
> 
Other than that, we're all screwed, and this could be the beginning of  the end of Linux-on-the-desktop. As much as LotD no longer is of any use  to me personally, I don't want to see it killed.It's not even making the news - so I highly doubt most people are even aware.  And, even if they were aware - they wouldn't care.  As I said before - Windows is all they know.  Besides most people are too dim to realize the implications here; those have nothing to do with technology at all.

If it's not being debated NOW or being talked out NOW - not just on Linux message boards - then chances are it isn't going to be stopped.

It's going to go through - and the hardware companies will cower behind closed doors to MS and do whatever they're told - as we've seen before.  

Linux as a desktop days are numbered.  It'll go back to what it was before "Ubuntu" - a terminal based OS that can only really be used by people who understand code, compiling, authoring, and how to write their own drivers....

---

### Post by llua+ on 2012-06-03
> **candtalan said:**
> Information is not very easy to find.
Because it's mixed in with all the FUD about something that isn't released yet.

---

### Post by alexfish on 2012-06-03
> **candtalan said:**
> Information is not very easy to find. May be a coincidence? However this
[http://arstechnica.com/information-technology/2012/01/windows-8s-locked-bootloaders-much-ado-about-nothing-or-the-end-of-the-world-as-we-know-it/](http://arstechnica.com/information-technology/2012/01/windows-8s-locked-bootloaders-much-ado-about-nothing-or-the-end-of-the-world-as-we-know-it/)
implies that a situation exists (or should hopefully exist) where in PCs, secure boot can be turned off by the user (re firmware). If this guess is true then by running GNU/Linux (unsigned) dual boot and Windows 8, then Windows 8 must be subsequently run with 'secure boot' turned off.
GNU/Linux advertising: 'Improve your life by turning off Microsoft Secure Boot'. Mmm, can I see that working? Maybe not.

One thing is very very clear to me. Dual boot is central to all of my activities with *many* friends. Yet nowhere in the often very detailed discussions of this and that specifications and requirements and options whatever (if they can be found, and then believed), nowhere is 'dual boot' or its practicality mentioned. I suspect that the purchased digital signature method may be, unfortunately, the only practical way out.
"The story for ARM is rather different."  HA

If by what I read is true, then Microsoft should sell there Own Custom Built Machines,


"Microsoft rules"  should read Microsoft  Law.

---

### Post by ExSuSEusr on 2012-06-03
> **llua+ said:**
> Because it's mixed in with all the FUD about something that isn't released yet.

Yes, because it's much more practical to sit back and do absolutely until it becomes a reality - at which point it's all but impossible to over turn, then to do something now and stop it from ever taking off.

FUD?  Unless you've been hiding in a cave I think you full well know the extent Microsoft will go to have total power over the PC world.  Strong arming, breaking laws, the list goes on.  Do you think this isn't a ploy to get rid of Linux and other OS's that could eventually threaten that garbage heap called Windows?  Let's not forget the company was started with stolen ideas... so morality isn't exactly an MS strong point.

Ubuntu, Mint, Fedora - getting more and more popular as time goes on.  And, being free doesn't hurt.  If you can't see that MS sees this as a potential threat, then well... I can't help you.

This is terrible terrible news.

---

### Post by Linuxratty on 2012-06-03
>  FUD?  Unless you've been hiding in a cave I think you full well know the extent Microsoft will go to have total power over the PC world.  Strong arming, breaking laws, the list goes on.

 So true...Just read The Halloween Papers for starters:

[http://www.stromian.com/Book/Chap5.html](http://www.stromian.com/Book/Chap5.html)

---

### Post by alexfish on 2012-06-03
> **Linuxratty said:**
> So true...Just read The Halloween Papers for starters:

[http://www.stromian.com/Book/Chap5.html](http://www.stromian.com/Book/Chap5.html)
Intersting ,

Sort of Like saying,

I open this letter delivered to  door by the postman , Headlined TOP SECRET , now I am to going get sued for opening the letter , Who would be  guilty if Jury had to decide.

---

### Post by mörgæs on 2012-06-04
It is saddening to see that people are less aware due to the fact that *as of now* the signature costs only $99 and that Restricted Boot is focusing on ARMs. 

There is no logical reason to believe that Microsoft will not push this to x86 computers and that it will not be a per-installation fee in the near future. 

A one-time fee of $99 is nothing but a scam. Compared to the cost of developing Restricted Boot it can only be meant as a way to fool people.

---

### Post by KiwiNZ on 2012-06-04
If you were going to do a scam you would ask for more than a $99 fee. Multiply $99 by say 100 Distros $9900 hardly a lucrative scam. It's illogical to call this a scam. Secure boot is not new and is a good thing.

---

### Post by mörgæs on 2012-06-04
> **KiwiNZ said:**
> Multiply $99 by say 100 Distros $9900 hardly a lucrative scam.

Exactly. The fee will rise considerably in the future. The present price (which essentially is zero) is only meant to lessen people's awareness.

---

### Post by nicolasforum89 on 2012-06-04
outrageous !!!](*,)

---

### Post by KiwiNZ on 2012-06-04
> **mörgæs said:**
> Exactly. The fee will rise considerably in the future. The present price (which essentially is zero) is only meant to lessen people's awareness.

If that were the case the fee now would be zero thus awareness near zero. I do not see large if any fee increases, my dealings with MSFT do not give me any reason for concern.

---

### Post by jockyburns on 2012-06-04
If anything, it will stop Microsoft repaying the fees to those people who bought machines with Win xxx preloaded, then installed a Linux OS as the only OS on that machine (yes you can do that at the moment and reclaim money from Microsoft)
I can certainly see that this secure boot will curtail our choice of OS in the future. 
Just think on a bit,, In 5 yrs time, your computer finally gives up the ghost. You go down the High St and buy a new machine. What OS choice do you have? Windows/ Apple/ Fedora.  That looks like the only choices you'll have, unless Canonical decide to dig deep and pay $99 for a key (I'm sure this is just loose change to Mark Shuttleworth)

But,, What happens , when a few years down the line, Microsoft decide that the key will now cost $xxx per machine? (and I can see this happening) Ubuntu and any other Linux OS certainly won't be free.

---

### Post by mörgæs on 2012-06-04
Yes, that's where we are heading :-(

At this step the purpose is not to profit, it is to get the idea of payment accepted and break the free-as-in-beer principle.

Later Microsoft (or an associate) can claim: The Free Software people have chosen Restricted Boot but don't pay but a fraction of the development costs.

---

### Post by TenPlus1 on 2012-06-04
This means nothing, the more Microsoft invests in their bootloader to nab them market share and even more money, the more people will get annoyed at them epecially now that the bootloader has already been cracked...  Safe my ***...  Why would I pay 99 quid for something that was so easily bypassed...

[http://arstechnica.com/business/2011/11/security-researcher-defeats-windows-8-secure-boot/](http://arstechnica.com/business/2011/11/security-researcher-defeats-windows-8-secure-boot/)

---

### Post by Adrian98 on 2012-06-04
> **Linuxratty said:**
> I guess Ubuntu will have to pay up to Microsoft as well.



[http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html](http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html)

never expected that the Fedora would have to pay to Microsoft! As far as I see , there would be some legit reason behind this deal!

---

### Post by sffvba[e0rt on 2012-06-04
My question is this.  Why does anyone need to pay Microsoft anything? Why isn't the database and requirements being handled by the hardware vendors creating the motherboards or at the very least a third party?!

Why does the makers of an operating system need to pay a "rival" creator of an operating system to install their OS on third party hardware that has zero to do with either of the creators of said operating systems?!

That is just plain stupid, and ridiculously biased.


404

---

### Post by howefield on 2012-06-04
> **not found said:**
> My question is this.  Why does anyone need to pay Microsoft anything? Why isn't the database and requirements being handled by the hardware vendors creating the motherboards or at the very least a third party?!

Why does the makers of an operating system need to pay a "rival" creator of an operating system to install their OS on third party hardware that has zero to do with either of the creators of said operating systems?!

That is just plain stupid, and ridiculously biased.


404

Not sure this is correct, doesn't the money go to Verisign ?

---

### Post by sffvba[e0rt on 2012-06-04
> **howefield said:**
> Not sure this is correct, doesn't the money go to Verisign ?

Read another story on it now and I see it is Verisign that gets the cash... but Windows that does the signing...

So rephrase my earlier rant and basically; Why Microsoft sign for Linux?!


404

---

### Post by forrestcupp on 2012-06-04
I don't really think it matters, anyway. Most people who buy computers with Windows don't care if you can install Linux or not. Most of those people don't even know what Linux is. A lot of those people don't even know what an operating system is.

I don't believe that this is really going to make it impossible to install Linux distros on your computers. If it ends up resulting in that 15 years from now, two things will end up happening. Vendors will start giving us the option to not have secure boot in some of their models. Also, it wouldn't be long before the community found some workaround.

It's not going to be the end of the world. We'll still be able to to use Linux to look at the internetz. Have you ever noticed that about every year there is some major doom for Linux on the horizon, yet we're still going strong?

---

### Post by alexfish on 2012-06-04
> **forrestcupp said:**
> I don't really think it matters, anyway. Most people who buy computers with Windows don't care if you can install Linux or not. Most of those people don't even know what Linux is. A lot of those people don't even know what an operating system is.

I don't believe that this is really going to make it impossible to install Linux distros on your computers. If it ends up resulting in that 15 years from now, two things will end up happening. Vendors will start giving us the option to not have secure boot in some of their models. Also, it wouldn't be long before the community found some workaround.

It's not going to be the end of the world. We'll still be able to to use Linux to look at the internetz. Have you ever noticed that about every year there is some major doom for Linux on the horizon, yet we're still going strong?

Lets take the hardware . options "UEFI" do you think hardware vendors in essence will fork a product , you need to take a look at what they want on the arm platform,

It is well known that if the Precedence is accepted by ONE then
Historical events have learned , some , that it will be applied to others.

Don't get me wrong about safe-boot , think about the method or what ever people want to call it.

---

### Post by forrestcupp on 2012-06-04
> **alexfish said:**
> Lets take the hardware . options "UEFI" do you think hardware vendors in essence will fork a product , you need to take a look at what they want on the arm platform,

It is well known that if the Precedence is accepted by ONE then
Historical events have learned , some , that it will be applied to others.

Don't get me wrong about safe-boot , think about the method or what ever people want to call it.

It doesn't matter. There will be ways around it. There always are.

---

### Post by rucadulu on 2012-06-04
The issue is not whether one can find a hack or way around it. The issues that this sets up a monopolistic business model and we have laws in the United States that are suppose to prevent this. However we have a federal judicial system that has been corrupted by the corporations and no longer protects its citizens.

So for the near future at least we will be subject to more and more corporations using monopolistic business models and the consumer paying the ultimate price, the lack of freedom of choice.
 
The only way turn this around is for the American people to stand up in mass and say enough is enough and take our country back from the corporations and the special interest groups that now control policy in the United States. But we as Americans have become too scared to bite the hand that feeds us.

---

### Post by forrestcupp on 2012-06-04
> **rucadulu said:**
> 
The only way turn this around is for the American people to stand up in mass and say enough is enough and take our country back from the corporations and the special interest groups that now control policy in the United States. But we as Americans have become too scared to bite the hand that feeds us.

I agree with what you're saying. But there aren't going to be nearly enough people who actually care to make a difference. Most people don't mind that their computers come with Windows, and the majority of the people who do just buy Macs.

---

### Post by rasmus91 on 2012-06-04
But...

No, damn it! there must be around that!

When i buy a computer i expect to be able to install whatever software i want on it, and Canonical or Redhat shouldn't have to pay anything to get M$'s certificate for anything! If i wan't to build my own OS at some point its none of their damn business if i want to install that on MY computer...

And this, my friends, is why I decided when i first heard about this, that I am never going to buy a windows 8 license. these guys are just not taking anymore of my money. If they are going to anyone its going to be developers that do not wish to control my computer or my software for that matter.

When i first started liking Ubuntu, i didn't mind M$ but this is the kind of thing that fuels hate, and It's the exact same reason i decided never to invest any of my money in an apple product, why? because i do not buy items that i may not own.
M$ can argue all they want that they're doing it for the sake of security, but i call BS, they're doing it for one thing; trying to shut out every kind of competition there might be, and theres nothing more to it than that.

Good luck to anyone whos going to try their luck at cracking this M$ crap, may you have great success in your efforts.

---

### Post by Skara Brae on 2012-06-04
This is a very interesting - and disturbing - thread.

So, someday soon in the future, I would not be able to install Linux on a brand new computer because of UEFI?

Well, this feels very wrong to me. I do with my possessions what I want, without first having someone to have to pay for me, in order for me to do with my possessions what I want.

And again Microsoft is involved.

Can someone give the European Commission a phonecall (so they can sue Microsoft again)? :mad:

> Developers who compile their own kernel binary will have to figure out a way to get it signed, either by applying to the firmware company directly, or creating a shim similar to Fedora's bootloader.

> ...the act of relying on Microsoft to give its approval to run Linux on a computer...

They won't get away with this. They **can't**! Or can they? I mean, come on!

And just when you thought you were rid of Microsoft (by running GNU/Linux)...

---

### Post by Skara Brae on 2012-06-04
> Users could not install Linux as a second OS, or replace Windows with a copy of Linux, Garrett argued.
> *Users could not install Linux as a second OS, or replace Windows with a copy of Linux, Garrett argued.*
> ***Users could not install Linux as a second OS, or replace Windows with a copy of Linux, Garrett argued.***

:shock:

It is not possible that Microsoft would do this for some security reason of some kind. Since this is Microsoft, there is more to this than just security...
 
They won't get away with this.

---

### Post by Erik1984 on 2012-06-04
> **Skara Brae said:**
> :shock:

It is not possible that Microsoft would do this for some security reason of some kind. Since this is Microsoft, there is more to this than just security...
 
They won't get away with this.

The latter of those quotes is only true if secure boot can't be disabled. On most X86 hardware it will probably be possible (to disable) but this whole situation still sucks. It will make no difference but I'm 99% sure my next system won't come with Windows preinstalled. Maybe a custom build without OS or a System76 or similar (hopefully more companies like S76 will emerge), in any case not Windows8 OEM.

---

### Post by Skara Brae on 2012-06-04
> **Euroman said:**
> The latter of those quotes is only true if secure boot can't be disabled.
This is Microsoft that we are talking about here. There is, or will be, a "catch". I am convinced of that.

---

### Post by KiwiNZ on 2012-06-04
An initiative to try an enhance security I welcome, because MSFT is involved is neither here nor there.

How ever there are those who will believe differently, there is those who believe that the security risks and Malware etc are a scare tactic used by AV producers etc in order to sell their products, these people probably also believe that Burglary doesn't occur, that is a con perpetrated by Insurance companies and security companies, and further believe that the Flu does not exist, that is a ruse used by the Drug companies to sell Vaccines.

---

### Post by MisterGaribaldi on 2012-06-04
Anyone who doesn't believe viruses, trojan horses, and all other sorts of malware are a fiction are living a very deluded existence.

That being said, however, I can remember many instances over the years when AV software makers engaged in acts of FUD to get people to install their software. Heck, for that matter, there's been an awful lot of FUD (relative to the actual legitimate level of threat) in the Mac world from Symantec and others to try and panic users into installing their software.

Having witnessed the effects of Symantec's and McAfee's software in particular, I would hesitate before ever advising someone to follow those companies' recommendations.

---

### Post by Bandit on 2012-06-04
> **forrestcupp said:**
> I agree with what you're saying. But there aren't going to be nearly enough people who actually care to make a difference. Most people don't mind that their computers come with Windows, and the majority of the people who do just buy Macs.

Sad part is that Americans are the most blind when it comes to computers. They blindly use that as if they were an appliance not thinking about the OS and being that blind they dont know to stand up against such things. 

(yes I am american) /sadly..

---

### Post by MisterGaribaldi on 2012-06-05
I dunno how much this is "just stupid Americans" really. It's not like Microsoft doesn't have a world-wide lock on the desktop.

---

### Post by Erik1984 on 2012-06-05
> **MisterGaribaldi said:**
> I dunno how much this is "just stupid Americans" really. It's not like Microsoft doesn't have a world-wide lock on the desktop.

It's exactly the same where I live, Microsoft is very strong here.

---

### Post by DoubleClicker on 2012-06-05
People here are not grasping the reality of the situation.

Fedora is paying $99 to have it's prebootloader digitally signed, by VeriSign with Microsoft's key.

The prebootloader loads grub, which will boot any Linux distro.

Any distro can redistribute Fedora's prebootloader.  

Therefore, for a one time payment of $99, paid to verisign by Fedora, all Linux users everywhere can boot any distro of Linux. Microsoft authorized the signing of the prebootloader, but will have no further control, nor receive any financial compensation.

As a certified Microsoft hater, I call that a win for Linux.

---

### Post by alexfish on 2012-06-05
> **doubleclicker said:**
> people here are not grasping the reality of the situation.

Fedora is paying $99 to have it's prebootloader digitally signed, by verisign with microsoft's key.

The prebootloader loads grub, which will boot any linux distro.

Any distro can redistribute fedora's prebootloader.  

Therefore, for a one time payment of $99, paid to verisign by fedora, all linux users everywhere can boot any distro of linux. Microsoft authorized the signing of the prebootloader, but will have no further control, nor receive any financial compensation.

As a certified microsoft hater, i call that a win for linux.
$99,?
> in the approach fedora chose, the organization would pay us$99 to have  microsoft sign the binary release of the fedora distribution. Although  the cost for the certificates would be less than $200 a year for  fedora's twice-a-year release schedule


---

### Post by DoubleClicker on 2012-06-05
> **alexfish said:**
> $99,?
> 
in the approach fedora chose, the organization would pay us$99 to have microsoft sign the binary release of the fedora distribution. Although the cost for the certificates would be less than $200 a year for fedora's twice-a-year release schedule


Did you read my [first post]("http://ubuntuforums.org/showpost.php?p=11988017&postcount=17")?

I gave the [primary source.]("http://mjg59.dreamwidth.org/12368.html")

---

### Post by forrestcupp on 2012-06-05
> **KiwiNZ said:**
> and further believe that the Flu does not exist, that is a ruse used by the Drug companies to sell Vaccines.The flu exists ... it's the side effects of drugs that are a ruse to sell more drugs. :)

We can talk later about whether the drug companies manufactured the flu and HIV viruses. ;)

> **Bandit said:**
> Sad part is that Americans are the most blind when it comes to computers. They blindly use that as if they were an appliance not thinking about the OS and being that blind they dont know to stand up against such things. 

(yes I am american) /sadly..Lol. But computers *are* an appliance. They're just a tool to get things done or to have fun with. Most people don't give a rat's backside about the OS, as long as they are able to play their Facebook games and check emails. Why should they? Linux is for people who are interested in such things. It doesn't have to be for everyone.

---

### Post by Erik1984 on 2012-06-05
> **forrestcupp said:**
> The flu exists ... it's the side effects of drugs that are a ruse to sell more drugs. :)

We can talk later about whether the drug companies manufactured the flu and HIV viruses. ;)

Lol. But computers *are* an appliance. They're just a tool to get things done or to have fun with. Most people don't give a rat's backside about the OS, as long as they are able to play their Facebook games and check emails. Why should they? Linux is for people who are interested in such things. **It doesn't have to be for everyone.**

Some Linux distros are certainly not for everyone but Ubuntu is 'Linux for human beings'. Ubuntu tries to be the Linux for everyone. Sure we can discuss if Ubuntu at present state is suitable for all tasks the average user performs. However the goal is to make Ubuntu a main stream OS. UEFI secure boot *could* be a nasty obstacle on the road.

---

### Post by MadmanRB on 2012-06-05
> **KiwiNZ said:**
> An initiative to try an enhance security I welcome, because MSFT is involved is neither here nor there.


Yes but this is Microsoft we are talking about, complete and utter domination is the only thing they think about.

---

### Post by forrestcupp on 2012-06-05
> **Euroman said:**
> Some Linux distros are certainly not for everyone but Ubuntu is 'Linux for human beings'. Ubuntu tries to be the Linux for everyone. Sure we can discuss if Ubuntu at present state is suitable for all tasks the average user performs. However the goal is to make Ubuntu a main stream OS. UEFI secure boot *could* be a nasty obstacle on the road.

I'm not saying, by any means, that Ubuntu *can't* be used by everyone. My 8 year old boy uses Ubuntu and likes it much more than Windows.  I actually think that for a basic user who doesn't want to do anything non-standard, Ubuntu is easier than Windows.

I'm just saying that most people don't care enough about an OS or user interface to go through the hassle of installing it, when they already have something that works for them.

---

### Post by alexfish on 2012-06-05
> **DoubleClicker said:**
> Did you read my [first post]("http://ubuntuforums.org/showpost.php?p=11988017&postcount=17")?

I gave the [primary source.]("http://mjg59.dreamwidth.org/12368.html")

No, the OP,

[http://www.pcworld.com/businesscente...rtificate.html]("http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html")

Which statement is correct?

but also what needs to be clarified ,

1. Twice a Year , key , does this apply to grub or the Kernel
2. If applied to the kernel then, will this have significant impact on development, to deter 
3. If same rulings are applied to vendor hardware , will this impact on both developer and the user

regards

alexfish

---

### Post by sdowney717 on 2012-06-05
So now Verisign makes money off Linux users.
If redhat has to pay $200 per year, then Canonical can also pay that fee.

The fee is a meaningless number, unless your part of developing your own linux flavor and dont want to pay this tax on freedom.

Not very much money involved with this, how many different Non Windows Os's are in regular use? Less than 100? Less than 10?, Less than 5? The impact will be very low.

Why would dual booting be affected at all?
If Ubuntu pays the fee and gets this key?

If people had to go into the bios and fiddle with it, toggling on and off secure boot, then yes, that is too much.

It feels like this is the way things are, secure web sites, signed certificates, now OS secure boot. Is it really anymore secure because the OS is secure boot?

Is your car repaired any safer cause you have a certified mechanic work on it?
Is your house built better because licensed bonded tradesmen build it?
Not really.
To me all this is just white washing, lipstick on a pig, everything bad is still waiting to bite you. Maybe it just feels better to have all these certifications.

---

### Post by sffvba[e0rt on 2012-06-05
And what would signify enough of a change to warrant purchasing a new license?  No more kernel updates now? No more rolling releases?


404

---

### Post by alexfish on 2012-06-05
> **sdowney717 said:**
> 
To me all this is just white washing, lipstick on a pig, everything bad is still waiting to bite you. Maybe it just feels better to have all these certifications.:lolflag:

I'm certified

Get your certification bits an keys here

[http://rentanidiot.com/Training.asp](http://rentanidiot.com/Training.asp)

:guitar:

---

### Post by alexfish on 2012-06-05
This is a message from M:

Due to recent uproars and dissent we are moving our headquarters to
[IMG]http://www.toptenz.net/wp-content/uploads/2010/01/Pitcairn-Island.jpg[/IMG]

Due to unforsean sercumstances "no fone" "no microwave thingies" "no electricKery"

Please make arrangements with Local Hospitality agent to facilitate your landing.

Local law "now" requires a landing fee of $2000 per person

**In strict enforcement:**

There is an additional cost of $100 per hand luggage , any hand luggage over the weight of 4 ounces . will occur a penalty of 50$ per ounce.

Your suitcase will be accessed on upon landing.

Thank you for your attention.

---

### Post by KiwiNZ on 2012-06-05
> **forrestcupp said:**
> I'm not saying, by any means, that Ubuntu *can't* be used by everyone. My 8 year old boy uses Ubuntu and likes it much more than Windows.  I actually think that for a basic user who doesn't want to do anything non-standard, Ubuntu is easier than Windows.

I'm just saying that most people don't care enough about an OS or user interface to go through the hassle of installing it, when they already have something that works for them.

+1 , for most a PC, Laptop or Tablet is an appliance they purchase take home, turn on and use in the same manner as a TV, Blu Ray player etc. They don't care what makes  it work or how it works. After all how many consumers upgrade the firmware in their TV or Blu Ray player?

This does not reflect on their intelligence of literacy it merely shows their use. Like it or not Windows or OSX provides them that seamlessly and hassle free.

---

### Post by Dr. C on 2012-06-05
Anyone who belives that Secure Boot will actually protect Microsoft Windows systems from malware should consider this:

[http://www.securityweek.com/microsoft-unauthorized-certificate-was-used-sign-flame-malware]("http://www.securityweek.com/microsoft-unauthorized-certificate-was-used-sign-flame-malware")

and this

[http://news.slashdot.org/story/12/06/04/1211206/microsoft-certificate-was-used-to-sign-flame-malware]("http://news.slashdot.org/story/12/06/04/1211206/microsoft-certificate-was-used-to-sign-flame-malware")

The real motivation behind Secure Boot is not security or an attempt to lock out GNU / Linux but actually DRM.

---

### Post by KiwiNZ on 2012-06-05
> **Dr. C said:**
> 

The real motivation behind Secure Boot is not security or an attempt to lock out GNU / Linux but actually DRM.

Where is you definitive proof for this

---

### Post by mörgæs on 2012-06-05
Does anyone know if this will affect more than booting from the hard drive, for example a live boot?

---

### Post by Erik1984 on 2012-06-05
> **KiwiNZ said:**
> +1 , for most a PC, Laptop or Tablet is an appliance they purchase take home, turn on and use in the same manner as a TV, Blu Ray player etc. They don't care what makes  it work or how it works. After all how many consumers upgrade the firmware in their TV or Blu Ray player?

This does not reflect on their intelligence of literacy it merely shows their use. **Like it or not** Windows or OSX provides them that seamlessly and hassle free.

Well I don't like it because it will limit the amount of suitable systems for me to install Ubuntu on (especially with ARM processors becoming more powerful and popular). But I got the message from earlier in this thread: it's time to vote with the wallet. No more dual boot, only boxes without OS or Linux preinstalled for me.

---

### Post by oldfred on 2012-06-05
As I understand it, you would have to turn off the secure boot or it will not work or it has to have a valid key. It becomes like my old work computer that was totally locked down. 

The other issue is all of grub has to be signed and no blobs like the nVidia driver as that is not "secure". 

I can see where Microsoft can make new computers comply, but they will also want to sell to older systems which will not be locked down.

And the manufacturers have contracts with customers to sell the same model for several years so they can just image a drive for a new install. What about those?

---

### Post by Linuxratty on 2012-06-05
> **KiwiNZ said:**
> Where is you definitive proof for this

I have the same question. I've been following this and have seen nothing on DRM.

---

### Post by alexfish on 2012-06-05
> **KiwiNZ said:**
> +1 , for most a PC, Laptop or Tablet is an appliance they purchase take home, turn on and use in the same manner as a TV, Blu Ray player etc. They don't care what makes  it work or how it works. After all how many consumers upgrade the firmware in their TV or Blu Ray player?

This does not reflect on their intelligence of literacy it merely shows their use. Like it or not Windows or OSX provides them that seamlessly and hassle free.
Then I sit here and wait for an Ubuntu Pad and hope the secured boot does not to allow that **** on
then  the role is reversed.. Yip ,

---

### Post by Dr. C on 2012-06-05
> **KiwiNZ said:**
> Where is you definitive proof for this

To understand secure boot we first take a look at where this is been implemented at its logical extreme namely Windows 8 on ARM. In this scenario we have a locked bootloader that cannot be unlocked at all by the end user together with the requirement that only applications obtained from a Microsoft approved source can be installed on the device. This is infact the model used by Apple iPhone, iPad, SONY PS3 etc, Nintendo Wii, and of course Microsoft itself Xbox. Unlike the PC market in these markets the companies that do this make no secret that their motivation is DRM. In order to install pirated software on these devices one needs to first crack that bootloader lock. The other thing that is necessary in these cases, in order for the DRM to work, is to keep FLOSS, especially FLOSS under GPLv3, out. So we have Microsoft trying to launch Windows 8 on a new platform, ARM, and they exclude the one category of legacy Windows software, FLOSS, that can be easily ported from Windows x86/AMD64 to Windows on ARM (all you need is a recompile). Why? It does not make any sense when when Winodws 8 on ARM will fact stiff competition from IOS, Android, and even [Ubuntu]("http://www.ubuntu.com/devices/android"). The answer is of course DRM.

If we now take a look Windows 8 x86/AMD64 we find that Microsoft had no choice but to compromise on the DRM here, because of both legacy versions of Windows and legacy Windows applications. In addition if they tried to exclude GNU / Linux on x86/AMD64 there would be a very strong case for anti-trust both in the US and in the EU. On ARM on the other hand Microsoft may have a stronger defence as Microsoft is not dominant in the ARM market.

What we have here is not an isolated event but rather a strategy that has been mapped out for well over a decade. If one throws a frog into boiling water it will jump out right a way; however if on places a frog into cold water and slowly brings the water to a boil, the frog will not notice and will be cooked. So we start in the 1990s with Windows NT4 or Windows 98 (ice cold) and slowly add the heat over the years until we get Windows 8 RT (boiling and a cooked frog) and Windows 8 x86/AMD64 (very hot but the frog is still alive).

One only needs to take a good hard look at how DRM and lock down has been gradually added with each version of Windows, over time, to see what is really going on here.

---

### Post by skellat on 2012-06-05
> **oldfred said:**
> As I understand it, you would have to turn off the secure boot or it will not work or it has to have a valid key. It becomes like my old work computer that was totally locked down. 

The other issue is all of grub has to be signed and no blobs like the nVidia driver as that is not "secure". 

I can see where Microsoft can make new computers comply, but they will also want to sell to older systems which will not be locked down.

And the manufacturers have contracts with customers to sell the same model for several years so they can just image a drive for a new install. What about those?

I believe the term is forced obsolescence.  This is not a good shift.

---

### Post by KiwiNZ on 2012-06-05
> **Dr. C said:**
> To understand secure boot we first take a look at where this is been implemented at its logical extreme namely Windows 8 on ARM. In this scenario we have a locked bootloader that cannot be unlocked at all by the end user together with the requirement that only applications obtained from a Microsoft approved source can be installed on the device. This is infact the model used by Apple iPhone, iPad, SONY PS3 etc, Nintendo Wii, and of course Microsoft itself Xbox. Unlike the PC market in these markets the companies that do this make no secret that their motivation is DRM. In order to install pirated software on these devices one needs to first crack that bootloader lock. The other thing that is necessary in these cases, in order for the DRM to work, is to keep FLOSS, especially FLOSS under GPLv3, out. So we have Microsoft trying to launch Windows 8 on a new platform, ARM, and they exclude the one category of legacy Windows software, FLOSS, that can be easily ported from Windows x86/AMD64 to Windows on ARM (all you need is a recompile). Why? It does not make any sense when when Winodws 8 on ARM will fact stiff competition from IOS, Android, and even [Ubuntu]("http://www.ubuntu.com/devices/android"). The answer is of course DRM.

If we now take a look Windows 8 x86/AMD64 we find that Microsoft had no choice but to compromise on the DRM here, because of both legacy versions of Windows and legacy Windows applications. In addition if they tried to exclude GNU / Linux on x86/AMD64 there would be a very strong case for anti-trust both in the US and in the EU. On ARM on the other hand Microsoft may have a stronger defence as Microsoft is not dominant in the ARM market.

What we have here is not an isolated event but rather a strategy that has been mapped out for well over a decade. If one throws a frog into boiling water it will jump out right a way; however if on places a frog into cold water and slowly brings the water to a boil, the frog will not notice and will be cooked. So we start in the 1990s with Windows NT4 or Windows 98 (ice cold) and slowly add the heat over the years until we get Windows 8 RT (boiling and a cooked frog) and Windows 8 x86/AMD64 (very hot but the frog is still alive).

One only needs to take a good hard look at how DRM and lock down has been gradually added with each version of Windows, over time, to see what is really going on here.

Do not agree.

Fedora has shown how to manage it correctly.

---

### Post by Dr. C on 2012-06-05
> **KiwiNZ said:**
> Do not agree.

Fedora has shown how to manage it correctly.

They have chosen to dump ice on the the Windows 8 x86/AMD64 frog to keep it alive and write off the dead frog in Winodws 8 RT. There is some merit in this strategy at least as a temporary measure since anti-trust action could take years. From [http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html) > Microsoft's certification requirements for ARM machines forbid vendors from offering the ability to disable secure boot or enrol user keys. While we could support secure boot in the same way as we plan to on x86, it would prevent users from running modified software unless they paid money for a signing key. We don't find that acceptable and so have no plans to support it. 

We must also reconize that this is a temporary measure. From [http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html) > Is this all set in stone? 
No. We've spent some time thinking about all of this and are happy that we can implement it in the Fedora 18 timescale, but there's always the possibility that we've missed something or that a new idea will come up. If we can increase user freedom without making awful compromises somewhere else then we'll do it.

It will be very interesting to see what Canonical does here.

---

### Post by Dry Lips on 2012-06-05
[I]"I wrote about the [technical details]("http://mjg59.dreamwidth.org/6054.html")  of supporting the UEFI secure boot specification with Linux. Despite me  pretty clearly saying that this was ignoring issues of licensing and  key distribution and the like, people are now using it to claim that  Linux could support secure boot with minimal effort. In a sense, they're  right. The technical implementation details are fairly straightforward.  But they're not the difficult bit. [...]

Signing the kernel isn't enough. Signed Linux kernels must refuse to  load any unsigned kernel modules. Virtualbox on Linux? Dead. Nvidia  binary driver on Linux? Dead. All out of tree kernel modules? Utterly,  utterly dead. Building an updated driver locally? Not going to happen.  That's going to make some people fairly unhappy.[/I] [I]
[...]
We can write the code required to support secure boot on  Linux in a minimal amount of time - in fact, most of it's now done. But  significant practical problems remain, and so far we have no workable  solutions for any of them.[/I]

Source: [http://mjg59.dreamwidth.org/9844.html](http://mjg59.dreamwidth.org/9844.html)

What do you guys make of this?

---

### Post by Dr. C on 2012-06-05
> **Dry Lips said:**
> [I]"I wrote about the [technical details]("http://mjg59.dreamwidth.org/6054.html")  of supporting the UEFI secure boot specification with Linux. Despite me  pretty clearly saying that this was ignoring issues of licensing and  key distribution and the like, people are now using it to claim that  Linux could support secure boot with minimal effort. In a sense, they're  right. The technical implementation details are fairly straightforward.  But they're not the difficult bit. [...]

Signing the kernel isn't enough. Signed Linux kernels must refuse to  load any unsigned kernel modules. Virtualbox on Linux? Dead. Nvidia  binary driver on Linux? Dead. All out of tree kernel modules? Utterly,  utterly dead. Building an updated driver locally? Not going to happen.  That's going to make some people fairly unhappy.[/I] [I]
[...]
We can write the code required to support secure boot on  Linux in a minimal amount of time - in fact, most of it's now done. But  significant practical problems remain, and so far we have no workable  solutions for any of them.[/I]

Source: [http://mjg59.dreamwidth.org/9844.html](http://mjg59.dreamwidth.org/9844.html)

What do you guys make of this?

Very much the case. The requirement of signed drivers will cause many problems with propriety drivers regardless of the OS. I actually ran into this problem with sound drivers when running 64bit Windows 7 in a VM under VirtualBox. I solved the problem by only running the 32bit versions of Windows 7 in my VMs under VirtualBox. The reason is that the 64bit versions of Windows 7 require signed drivers while the 32bit versions do not. The same is true for Windows Vista. There is a pattern here for anyone who cares to look. The older Windows platform (x86) is more free. The reason is again, DRM, as a driver could be used to circumvent the HDCP DRM in Windows 7 and Vista.

In the GNU / Linux on x86/AMD64 case I suspect the solution to these problems will be to disable secure boot and be done with the issue.

---

### Post by KiwiNZ on 2012-06-05
> **Dr. C said:**
> 

It will be very interesting to see what Canonical does here.

Hopefully Canonical will do what is commercially sensible. The Fedora decision seems to fit that purpose.

Canonical's quest is the bottom line, not Windmills

---

### Post by Dr. C on 2012-06-05
> **KiwiNZ said:**
> ...

Canonical's quest is the bottom line, not Windmills

Provided of course the "Windmills" do not stand in the way of the bottom line.

---

### Post by jockyburns on 2012-06-05
Just a quick thought here,,, Did anyone take Apple to court for them refusing to support Flash on the iPad? Did anyone come up with a workaround to allow Flash content on the iPad?..... Nah, didn't think so,,,,,, SO ,,, who's going to take on Microsoft with their move on UEFI ????????

---

### Post by alexfish on 2012-06-05
> **jockyburns said:**
> Just a quick thought here,,, Did anyone take Apple to court for them refusing to support Flash on the iPad? Did anyone come up with a workaround to allow Flash content on the iPad?..... Nah, didn't think so,,,,,, SO ,,, who's going to take on Microsoft with their move on UEFI ????????

probably just a question of time , 

Once the security FRAME WORK is in place , as they say one by one

---

### Post by Dr. C on 2012-06-05
> **jockyburns said:**
> Just a quick thought here,,, Did anyone take Apple to court for them refusing to support Flash on the iPad? Did anyone come up with a workaround to allow Flash content on the iPad?..... Nah, didn't think so,,,,,, SO ,,, who's going to take on Microsoft with their move on UEFI ????????

The EU is allready primed with anti-trust regarding Microsoft. How about an 899 Million Euro fine over SAMBA compatibility for starters [http://www.zdnet.com/blog/london/eu-court-poised-for-microsoft-antitrust-fine-ruling/4892]("http://www.zdnet.com/blog/london/eu-court-poised-for-microsoft-antitrust-fine-ruling/4892")

Apple by the way has no way near the market dominance in the smartphone market that Microsoft has in the desktop OS market. Furthermore the iPad was effectively a new product entirely. Having said that I do not believe that Apple is out of the woods here either, it is just that Microsoft is a lot easier target because of their worldwide desktop OS market dominance.

---

### Post by KiwiNZ on 2012-06-05
> **jockyburns said:**
> Just a quick thought here,,, Did anyone take Apple to court for them refusing to support Flash on the iPad? Did anyone come up with a workaround to allow Flash content on the iPad?..... Nah, didn't think so,,,,,, SO ,,, who's going to take on Microsoft with their move on UEFI ????????

that is because it was a good thing Apple did

---

### Post by MisterGaribaldi on 2012-06-05
> **Dr. C said:**
> Apple by the way has no way near the market dominance in the smartphone market that Microsoft has in the desktop OS market.

Oh *really?* Got any statistics to back up that claim?

---

### Post by Dr. C on 2012-06-05
> **MisterGaribaldi said:**
> Oh *really?* Got any statistics to back up that claim?

[http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=8&qpcustomd=0]("http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=8&qpcustomd=0")
Microsoft Windows 92.53% on the desktop

[http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=8&qpcustomd=1]("http://marketshare.hitslink.com/operating-system-market-share.aspx?qprid=8&qpcustomd=1")
Apple IOS 62.65% on mobile This includes smartphones **and** tablets

---

### Post by MisterGaribaldi on 2012-06-05
Huh. Alright, I asked and you delivered. I stand corrected.

---

### Post by DoubleClicker on 2012-06-05
> **alexfish said:**
> No, the OP,

[http://www.pcworld.com/businesscente...rtificate.html]("http://www.pcworld.com/businesscenter/article/256607/fedora_linux_capitulates_to_microsoft_boot_certificate.html")

Which statement is correct?

but also what needs to be clarified ,

1. Twice a Year , key , does this apply to grub or the Kernel
2. If applied to the kernel then, will this have significant impact on development, to deter 
3. If same rulings are applied to vendor hardware , will this impact on both developer and the user

regards

alexfish
Do you know what a [primary source]("http://en.wikipedia.org/wiki/Primary_source") is? PCWorld magazine is not a primary source, it is a [secondary source]("http://en.wikipedia.org/wiki/Secondary_source"). 

To be a primary source they would have to be directly involved in the process, as was Matthew Garrett.  Go back and read it again:  There is no recurring payment,  in either grub nor the Kernel need to be signed.  Neither developers nor end-user's will be impacted beyond the inconvenience of once more step in the boot process.

---

### Post by alexfish on 2012-06-05
> **DoubleClicker said:**
> Do you know what a [primary source]("http://en.wikipedia.org/wiki/Primary_source") is? PCWorld magazine is not a primary source, it is a [secondary source]("http://en.wikipedia.org/wiki/Secondary_source"). 

To be a primary source they would have to be directly involved in the process, as was Matthew Garrett.  Go back and read it again:  There is no recurring payment,  in either grub nor the Kernel need to be signed.  Neither developers nor end-user's will be impacted beyond the inconvenience of once more step in the boot process.
Then Why the heads up on the primary?
> **Edit 16:17EDT 31/5/12: Clarification of who gets the $99** 
**Edit 02:10EDT 01/6/12: Clarification that it's a one-off payment**

(Brief  disclaimer - while I work for Red Hat, I'm only going to be talking  about Fedora here. Anything written below represents only my opinions  and my work on Fedora, not Red Hat's opinions or future plans)
if fact were fact , why have a  disclaimer that mystifies me

ADDED TO HIGHLIGHT:
I can agree with the prevention of this
[http://blog.webroot.com/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/](http://blog.webroot.com/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/)
I am not against safe boot , We the general public Need FACTS

FACTS do not make FICTION , and Disclaimers do not prove FACTS

---

### Post by Dr. C on 2012-06-05
Just for reference the "primary" source here is: [http://mjg59.dreamwidth.org/12368.html]("http://mjg59.dreamwidth.org/12368.html")

---

### Post by alexfish on 2012-06-05
> **Dr. C said:**
> Just for reference the "primary" source here is: [http://mjg59.dreamwidth.org/12368.html](http://mjg59.dreamwidth.org/12368.html)

Thanks , 

Just want to highlight  , Whilst reading this , There is a difference between "SHOULD" and "WILL" ,.

---

### Post by ExSuSEusr on 2012-06-06
The reason I don't include "Apple" in this discussion is because I consider Apple to have a completely different approach.

Apple isn't out there strong arming vendors for world dominance (figurative).

Apple makes Apple.  The hardware, the software, the OS - all Apple.

For example:

Apple isn't out there trying to force all MP3 player manufactures to implement restrictions in that the user can only use iTunes for their "RCA" player.

I actually like the iPhone more than my Droid - but I won't buy an iPhone because I know they are a complete PIA to get working with my Ubuntu or Mint installs.  So, I'll just stick with Droid. I can't blame Apple for not catering to MY needs by making THEIR products usable on the OS I choose to use.  Why should they?  Apple is it's own little world.  Good for them.  If people are willing to pay for their overpriced products - great.  I have no problem with that.  I have no real problem with Apple.

But, I see this issue as completely different.  I can't articulate the thoughts I am trying to convey.

---

### Post by Dr. C on 2012-06-06
What Microsoft is doing with Windows 8 is a complete copy of what Apple is doing. This even exteds to the locked down ARM and more open x86/AMD64 platfroms. The motivation in both cases is the same, DRM. From the end owner point of view it really makes no difference that the software and hardware are made by the same or different companies if the end owner is prevented by DRM from modifying the device to meet the end owner's needs. 

The only real difference is market share, which makes Microsoft a much easier target for anti-trust legal action.

---

### Post by KiwiNZ on 2012-06-06
> **Dr. C said:**
> What Microsoft is doing with Windows 8 is a complete copy of what Apple is doing. This even exteds to the locked down ARM and more open x86/AMD64 platfroms. The motivation in both cases is the same, DRM. From the end owner point of view it really makes no difference that the software and hardware are made by the same or different companies if the end owner is prevented by DRM from modifying the device to meet the end owner's needs. 

The only real difference is market share, which makes Microsoft a much easier target for anti-trust legal action.

And Oracle included in 9.8.7.6.5.....................

---

### Post by alexfish on 2012-06-06
> **ExSuSEusr said:**
> The reason I don't include "Apple" in this discussion is because I consider Apple to have a completely different approach.

Apple isn't out there strong arming vendors for world dominance (figurative).

Apple makes Apple.  The hardware, the software, the OS - all Apple.

For example:

Apple isn't out there trying to force all MP3 player manufactures to implement restrictions in that the user can only use iTunes for their "RCA" player.

I actually like the iPhone more than my Droid - but I won't buy an iPhone because I know they are a complete PIA to get working with my Ubuntu or Mint installs.  So, I'll just stick with Droid. I can't blame Apple for not catering to MY needs by making THEIR products usable on the OS I choose to use.  Why should they?  Apple is it's own little world.  Good for them.  If people are willing to pay for their overpriced products - great.  I have no problem with that.  I have no real problem with Apple.

But, I see this issue as completely different.  I can't articulate the thoughts I am trying to convey.

Apple have the right approach , and are Streets ahead of others in this area, including the hardware.

can only praise their foresight ,

---

### Post by catlover2 on 2012-06-06
I must be missing something big here, but someone please clarify.

[quote=http://mjg59.dreamwidth.org/12368.html]
We've decided to take a multi-layer approach to our signing for a fairly simple reason. Signing through the Microsoft signing service is a manual process, and that's a pain. We don't want to have bootloader updates delayed because someone needs to find a copy of Internet Explorer and a smartcard and build packages by hand. **Instead we're writing a very simple bootloader[2].** This will do nothing other than load a real bootloader (grub 2), validate that it's signed with a Fedora signing key and then execute it. Using the Fedora signing key there means that we can build grub updates in our existing build infrastructure and sign them ourselves. The first stage bootloader should change very rarely, and we don't envisage updating it more than once per release cycle. It shouldn't be much of a burden on release management.
[/quote]
What's stopping this "very simple bootloader" from loading an unsigned version of GRUB2 (or other bootloader for that matter) and then not messing with having GRUB, the kernel, and even kernel modules having to be signed? I get the point that the supposed purpose of secure boot is to prevent malicious code from being executed, but nowhere have I seen anything saying that there would be any problem with having this "very simple bootloader" load any unsigned thing you like.

---

### Post by DoubleClicker on 2012-06-06
> **alexfish said:**
> Then Why the heads up on the primary?
if fact were fact , why have a  disclaimer that mystifies me

ADDED TO HIGHLIGHT:
I can agree with the prevention of this
[http://blog.webroot.com/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/](http://blog.webroot.com/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/)
I am not against safe boot , We the general public Need FACTS

FACTS do not make FICTION , and Disclaimers do not prove FACTS

That is utter nonesense. You are just trying to find some straw man to puts up to discredit any facts that will shed light on the fact that there isn't an issue here, you are just trying to perpetuate the paranoia based on misinformation, misunderstanding and misdirection.  There is no substance you your argument.

The disclaimer has nothing to do with the issue at hand the disclaimer is about his position wit hardhat, and that he is not specking in the capacity of a red hat employee, but rather as a fedora member.  


I laid out the facts, you don't want to believe them.  We don't need any more facts about this, we have the facts. End of story, Fedora did the right thing, and along the way, they discovered it was not nearly the compromise with the dark empire as they initially thought it would be. In the end UEFI is going to be a good for Linux.

---

### Post by jwbrase on 2012-06-06
> **Dr. C said:**
> In the GNU / Linux on x86/AMD64 case I suspect the solution to these problems will be to disable secure boot and be done with the issue.

Except it's not really a solution.

Secure boot and UEFI are actually useful to the end user. Disabling secure boot denies that functionality to the user.

The real issue is making sure that, if a machine implements secure boot, the owner of that machine is the final signing authority for software that runs on that machine. Anything that doesn't ensure that isn't a solution.

---

### Post by alexfish on 2012-06-06
> **DoubleClicker said:**
> That is utter nonesense. You are just trying to find some straw man to puts up to discredit any facts that will shed light on the fact that there isn't an issue here, you are just trying to perpetuate the paranoia based on misinformation, misunderstanding and misdirection.  There is no substance you your argument.

The disclaimer has nothing to do with the issue at hand the disclaimer is about his position wit hardhat, and that he is not specking in the capacity of a red hat employee, but rather as a fedora member.  


I laid out the facts, you don't want to believe them.  We don't need any more facts about this, we have the facts. End of story, Fedora did the right thing, and along the way, they discovered it was not nearly the compromise with the dark empire as they initially thought it would be. In the end UEFI is going to be a good for Linux.

then I give up

[http://www.computerworld.com/s/article/9220234/Microsoft_Red_Hat_spar_over_secure_boot_loading_tech](http://www.computerworld.com/s/article/9220234/Microsoft_Red_Hat_spar_over_secure_boot_loading_tech)

---

### Post by ade234uk on 2012-06-06
I have not read every single post, so Fedora are going to pay Microsoft so you can install Fedora on a machine?

How does that work then? Are you telling me that If I bought my own motherboard, built my own PC, Microsoft will stop me from installing Ubuntu because Canonical have not paid them a fee?

If true, unfair competition. How did we get to this stage in computing where Microsoft are actually getting involved in what I purchase. 
Microsoft are not a company, they are bloody government. Hope the EU gets involved with this.

---

### Post by Linuxratty on 2012-06-06
> **ade234uk said:**
> 
If true, unfair competition. How did we get to this stage in computing where Microsoft are actually getting involved in what I purchase. 
Microsoft are not a company, they are bloody government. Hope the EU gets involved with this.

 I agree.
And I'm not sure how we got to this point,but I suspect eventually computers will be turned into dumb devices like tv's and the net will be ran like cable tv...I dread this.

---

### Post by forrestcupp on 2012-06-06
> **ade234uk said:**
> I have not read every single post, so Fedora are going to pay Microsoft so you can install Fedora on a machine?No. Evidently, they will have to pay Verisign for a signature, not Microsoft. It appears that Microsoft is pushing for this, but they aren't the ones getting paid. They just want it to happen.

> **ade234uk said:**
> How does that work then? Are you telling me that If I bought my own motherboard, built my own PC, Microsoft will stop me from installing Ubuntu because Canonical have not paid them a fee?
We don't even know for sure that this is how it would be. More than likely, it would be like signing already is in Windows. It's not going to stop you from installing something, but it will warn you that it is unsigned and may be dangerous.

---

### Post by Linuxratty on 2012-06-06
> 
We don't even know for sure that this is how it would be. More than likely, it would be like signing already is in Windows. It's not going to stop you from installing something, but it will warn you that it is unsigned and may be dangerous.
So true..Ok,here is the latest from Red hat.

[http://www.redhat.com/about/news/archive/2012/6/uefi-secure-boot](http://www.redhat.com/about/news/archive/2012/6/uefi-secure-boot)

> >Some conspiracy theorists bristle at the thought of Red Hat and other Linux distributions using a Microsoft initiated key registration scheme


 I don't appreciate people's concerns about the implications of this being dismissed in this fashion.

---

### Post by SeijiSensei on 2012-06-06
Would people feel more comfortable with a generic UEFI Linux key of the type Matthew described in his [blog]("http://mjg59.dreamwidth.org/12368.html")?  The obvious candidates for signatories are big Linux users like Google or IBM.  Suppose IBM agreed to underwrite the "millions of dollars" that it would cost according to Matthew to become the equivalent signatory?  Would that be any better?  Would hardware manufacturers include an IBM-signed key by default the same way they will be including Microsoft's key?  

Isn't this the sort of thing the Linux Foundation should be doing?  If the [Foundation's members]("http://www.linuxfoundation.org/about/members") really cared about Linux they should be willing to pony up a few thousand bucks apiece more each year to support an official Linux signing key.

I still don't really understand how this would work for virtual machines.  First, there's the issue of signing kernel modules.  Then there's the issue of how the VM manager boots up a child.  If the machine is signed, will the VM be signed?  If the machine is unsigned, can the VM be signed if, say, Oracle signed VirtualBox with Microsoft's key?  If not, then turning off secure boot in the BIOS makes running virtualized Windows 8 impossible, no?  It sounds to me like you'd have to use the UEFI utilities to generate your own signing key if you want to run virtual machines.

---

### Post by Swagman on 2012-06-06
"Early Boot Sequence"

"Startup-Sequence"

I detect an Ex Amigan !

:guitar:

---

### Post by forrestcupp on 2012-06-06
> **SeijiSensei said:**
> 
Isn't this the sort of thing the Linux Foundation should be doing?  If the [Foundation's members]("http://www.linuxfoundation.org/about/members") really cared about Linux they should be willing to pony up a few thousand bucks apiece more each year to support an official Linux signing key.That's a pretty good point.

> **SeijiSensei said:**
> I still don't really understand how this would work for virtual machines.  First, there's the issue of signing kernel modules.  Then there's the issue of how the VM manager boots up a child.  If the machine is signed, will the VM be signed?  If the machine is unsigned, can the VM be signed if, say, Oracle signed VirtualBox with Microsoft's key?  If not, then turning off secure boot in the BIOS makes running virtualized Windows 8 impossible, no?  It sounds to me like you'd have to use the UEFI utilities to generate your own signing key if you want to run virtual machines.I don't think it would work that way for VMs that are running within a Host OS that is signed. VM software, like VirtualBox, have their own virtual BIOS. I highly doubt if they are going to include Secure Boot in their virtual BIOS. So I would say that as long as your Host OS is signed, you wouldn't have any problem installing whatever you want in a VM.

---

### Post by weasel fierce on 2012-06-06
> **Swagman said:**
> "Early Boot Sequence"

"Startup-Sequence"

I detect an Ex Amigan !

:guitar:

You can leave the amiga, but the amiga never leaves you :D

---

### Post by SeijiSensei on 2012-06-06
> **forrestcupp said:**
> I highly doubt if they are going to include Secure Boot in their virtual BIOS.

Wouldn't that make it impossible to have a Windows 8 guest running in a VirtualBox VM?

---

### Post by bobman321123 on 2012-06-06
> **forrestcupp said:**
> :lol:


So it's going to cost them a one-time $99 fee, and then everyone in the world can install it? Big deal.

It's the ideals behind it. 
You wouldn't like it if every human had to pay Microsoft 1 cent to be alive. 
Practically: it's not a big deal.
Morally: It's just wrong.

---

### Post by CharlesA on 2012-06-06
> **bobman321123 said:**
> It's the ideals behind it. 
You wouldn't like it if every human had to pay Microsoft 1 cent to be alive. 
Practically: it's not a big deal.
Morally: It's just wrong.
It's only wrong cuz it's Microsoft, right?

Would there be the same outrage if the 99 bucks was paid to EFF?

---

### Post by forrestcupp on 2012-06-06
> **SeijiSensei said:**
> Wouldn't that make it impossible to have a Windows 8 guest running in a VirtualBox VM?

I don't think it's a requirement of Win8, is it? If it is, then they're going to be missing out on a lot of sales for people wanting to upgrade their computers.

Even if it is, all they'll have to do is add another option in the virtual hardware. They're not going to bite themselves in the backside. The whole point of VM software is to make it easy to install different OSs. I'm sure they'll make it easy to add that option, if necessary.

---

### Post by Bandit on 2012-06-06
I am more devastated that Mike Stone will not be able to carry Megan Piper to the high school prom, all becuz she is a porn star! Seriously, why do schools have to be that way!?!?

---

### Post by weasel fierce on 2012-06-06
> **CharlesA said:**
> It's only wrong cuz it's Microsoft, right?

Would there be the same outrage if the 99 bucks was paid to EFF?

I sure bloody hope so.

---

### Post by sffvba[e0rt on 2012-06-06
Some more info.

[http://www.muktware.com/3699/secure-boot-uefi-fedora-red-hat-99-ubuntu-microsoft](http://www.muktware.com/3699/secure-boot-uefi-fedora-red-hat-99-ubuntu-microsoft)


404

---

### Post by MisterGaribaldi on 2012-06-06
> **not found said:**
> Some more info.[http://www.muktware.com/3699/secure-boot-uefi-fedora-red-hat-99-ubuntu-microsoft](http://www.muktware.com/3699/secure-boot-uefi-fedora-red-hat-99-ubuntu-microsoft)

Clearly not a professionally-written article.

---

### Post by sffvba[e0rt on 2012-06-06
> **MisterGaribaldi said:**
> Clearly not a professionally-written article.

IMO it seems to be a case of English not being the native language...

But they do highlight most relevant info from [this article]("http://www.redhat.com/about/news/archive/2012/6/uefi-secure-boot") (which they do link to).


404

---

### Post by MisterGaribaldi on 2012-06-06
> **not found said:**
> [quote=Tim Burke, vice president, Linux Engineering]In the interest of freedom of choice, some users may not want to utilize this secure boot capability. In the UEFI system menu, they are able to disable the feature and things should operate like they do currently.

Some conspiracy theorists bristle at the thought of Red Hat and other Linux distributions using a Microsoft initiated key registration scheme. Suffice it to say that Red Hat would not have endorsed this model if we were not comfortable that it is a good-faith initiative.[/quote]

Hey not found, actually that is a pretty good and insightful link. Thanks!

So, according to Mr. Burke, UEFI is ultimately disable-able if someone wants to do that, which pretty much then invalidates the views of those mentioned in the second paragraph.

"Hey! UEFI is evil because Microsoft is going to take over the world and prevent you from doing what you want on your own computer, and it's a lock which will only let you run OSs they write..."

"You *can* just turn it off, you know."

"What?!?!?!?"

Stick a fork in it because this argument is ***done***.

---

### Post by KBD47 on 2012-06-06
The real problem with secure boot is that you will no longer be able to hand someone an Ubuntu or other Linux CD and tell them to give it a shot. No, you will have to explain that they have to disable secure boot and...there goes Linux on the desktop. Many people, especially noobs, are not going to want to disable anything that they think secures their computer. And that is probably what MS is counting on. The fact that secure boot will likely not keep a computer secure is irrelevant, the fact it is one more nail in the Linux coffin is relevant.
  Ubuntu and other Linus distros need hardware vendors to start selling laptops, netbooks, ultrabooks, and tablets with Linux pre-installed. Linux is finding out that relying on OEMs with MS pre-installed to easily allow Linux on board, those days are disappearing. There are a few pre-installed Linux systems on hardware, but not nearly enough. And with potentially new users unwilling to mess with secure boot, there needs to be another way forward regarding Linux on hardware for the future.
My two cents.

---

### Post by alexfish on 2012-06-07
> **KBD47 said:**
> The real problem with secure boot is that you will no longer be able to hand someone an Ubuntu or other Linux CD and tell them to give it a shot. No, you will have to explain that they have to disable secure boot and...there goes Linux on the desktop. Many people, especially noobs, are not going to want to disable anything that they think secures their computer. And that is probably what MS is counting on. The fact that secure boot will likely not keep a computer secure is irrelevant, the fact it is one more nail in the Linux coffin is relevant.
  Ubuntu and other Linus distros need hardware vendors to start selling laptops, netbooks, ultrabooks, and tablets with Linux pre-installed. Linux is finding out that relying on OEMs with MS pre-installed to easily allow Linux on board, those days are disappearing. There are a few pre-installed Linux systems on hardware, but not nearly enough. And with potentially new users unwilling to mess with secure boot, there needs to be another way forward regarding Linux on hardware for the future.
My two cents.

There is a very Valid reason for Secure Boot , on any System , do not need to go into the details ,

Linux as it is, Is One of the most Security based O's systems we have today , It was Built IN from day one , Suggest you start reading , and find out where security issues stemmed from, and it was not Joe soap public . and the Linux Community are in a better position to fend for them selves . Linux has given **every one this opportunity**.

We are in this position due to Prior History . Could have been prevented . but some People think they Know better .

To put any Security Issues into the hands of One corporative is |Wrong ,

Simply put , Where Others  given a Chance to Work to Gether , as in The way the Linux Community has already done so. 

alexfish

---

### Post by Bandit on 2012-06-07
So will Win8 for example "require" Secure/Restricted Boot to be turned on to boot up? I mean I can clearly see this a helping improve protection against boot viruses in windows. They are a complete PITA. If its like everything else in the BIOS that allows the user to turn the on or off, I dont see the problem. Now if it was forced without an option for the user, then thems fighting words.

But honestly I dont see most hardcore gamers or linux users going to Win8 anyway. The only people I see mainly using it would be Mom and Pops who just use their PC as an appliance.  Those of us who prefer to have their PC act like an computer or gaming box will more then likely just stick to Linux or Win7, or dual boot booth with S/R Boot turned off anyway.

---

### Post by Paqman on 2012-06-07
> **KBD47 said:**
> The real problem with secure boot is that you will no longer be able to hand someone an Ubuntu or other Linux CD and tell them to give it a shot. No, you will have to explain that they have to disable secure boot and...there goes Linux on the desktop.

TBH, having to install the OS from a CD seems to be too much for most people anyway. We've never been able to take a significant chunk of the OS market that way, so the impact will probably be pretty negligible. Losing 10% of 1% isn't a big deal.

---

### Post by jockyburns on 2012-06-07
> **MisterGaribaldi said:**
> 

"Hey! UEFI is evil because Microsoft is going to take over the world and prevent you from doing what you want on your own computer, and it's a lock which will only let you run OSs they write..."

"You *can* just turn it off, you know."

"What?!?!?!?"

Stick a fork in it because this argument is ***done***.


Problem is,,, Several years down the line, are Microsoft going to treat x86 machines the same as ARM machines and take away the ability to turn off secure boot? Only MS know if this will happen. (and they ain't going to tell )  
If this is the case then the argument certainly isn't over.

---

### Post by forrestcupp on 2012-06-07
> **Bandit said:**
> So will Win8 for example "require" Secure/Restricted Boot to be turned on to boot up? I mean I can clearly see this a helping improve protection against boot viruses in windows. They are a complete PITA. If its like everything else in the BIOS that allows the user to turn the on or off, I dont see the problem. Now if it was forced without an option for the user, then thems fighting words.
I can't see them forcing it for Win8. If they do, they'll lose *a lot* of money from upgrades to current computers that don't have it.

---

### Post by sffvba[e0rt on 2012-06-07
[http://lxer.com/module/newswire/view/168183/](http://lxer.com/module/newswire/view/168183/)

[http://www.itwire.com/opinion-and-analysis/open-sauce/55198-red-hat-deal-with-microsoft-is-a-bad-idea](http://www.itwire.com/opinion-and-analysis/open-sauce/55198-red-hat-deal-with-microsoft-is-a-bad-idea)


404

---

### Post by Linuxratty on 2012-06-07
> **not found said:**
> [http://lxer.com/module/newswire/view/168183/](http://lxer.com/module/newswire/view/168183/)

[http://www.itwire.com/opinion-and-analysis/open-sauce/55198-red-hat-deal-with-microsoft-is-a-bad-idea](http://www.itwire.com/opinion-and-analysis/open-sauce/55198-red-hat-deal-with-microsoft-is-a-bad-idea)


404

 Great finds! Why is the powers that be in the Linux world caving in like this?
 What is going on behind closed doors that they are privy to and the rest of us are not?

---

### Post by codingman on 2012-06-07
by reading the iWire site, i feel like punching Microsoft in the face.

---

### Post by KiwiNZ on 2012-06-07
> **codingman said:**
> by reading the iWire site, i feel like punching Microsoft in the face.

They have done nothing to you.

---

### Post by ExSuSEusr on 2012-06-07
> **codingman said:**
> by reading the iWire site, i feel like punching Microsoft in the face.


+1

That was a great article - but then you know how much I so love that "other company..."

---

### Post by CharlesA on 2012-06-07
> **KiwiNZ said:**
> They have done nothing to you.
Yep. That site comes off as one that hates on Microsoft and balks at the security MS operating systems have.

No OS is is free of exploits.

---

### Post by ExSuSEusr on 2012-06-07
> **CharlesA said:**
> Yep. That site comes off as one that hates on Microsoft and balks at the security MS operating systems have.

No OS is is free of exploits.

That's true.  But, one would think that a company that has been producing a product since 1983 would have mastered the art of security by now, no?

How do we know that Windows 8 isn't just NT 4.0 wrapped with new bells and whistles?  Ok, sure we can probably gather that it isn't.... but the point is - after going on 30 YEARS - and Windows is still more or less garbage.  Really?

Ubuntu has been out since... what... 2004?  And while you are correct that no OS is impervious to hacking / security breaches - it is 1000 times more secure than Windows.

I will grant you that Ubuntu is based off Debian which started back in '94?  

MS still had 10 years on Debian - and it still sucks.

MS doesn't now nor has it really ever cared about "security" - it's about the bottom line and power to them.

EDIT:

You see this what you get when you remove the variable of competition from the equation (aka capitalism).  Competition breads invention and begets innovation. Competition is the reason my Droid can function as what is essentially a hand held laptop - all while allowing me to make phone calls.  If there were only ONE phone company - do you really think our smart phones would be what they are now?  Of course not.  Why would they?  One company, no competition, no reason to develop and or innovate.

Windows is the result of when a company - a single company is allowed to rule in a vacuum.  I am being quite serious here.  Windows is complete and utter trash.  Has been for decades.  But, why should MS care?  To the average user you either use it or nothing - considering most people don't know what Linux is or are afraid of it due to the misconceptions that are floating around out there.

MS should never have been allowed to have gotten to be where it is - but that's what happens when you elect fatcats that care more about greasing their own pockets (thanks lobbyist!) than doing what's right for all.

---

### Post by ExSuSEusr on 2012-06-07
Speaking of which....

100 cool points if you know where the title Debian came from - WITHOUT CHEATING.

---

### Post by sffvba[e0rt on 2012-06-07
> **ExSuSEusr said:**
> Speaking of which....

100 cool points if you know where the title Debian came from - WITHOUT CHEATING.

Seriously... on a Linux forum...

Sure, no OS is 100% secure... but I have a sneaking suspicion that some are slightly more secure than others ;)


404

---

### Post by wilee-nilee on 2012-06-07
> **ExSuSEusr said:**
> That's true.  But, one would think that a company that has been producing a product since 1983 would have mastered the art of security by now, no?

How do we know that Windows 8 isn't just NT 4.0 wrapped with new bells and whistles?  Ok, sure we can probably gather that it isn't.... but the point is - after going on 30 YEARS - and Windows is still more or less garbage.  Really?

Ubuntu has been out since... what... 2004?  And while you are correct that no OS is impervious to hacking / security breaches - it is 1000 times more secure than Windows.

I will grant you that Ubuntu is based off Debian which started back in '94?  

MS still had 10 years on Debian - and it still sucks.

MS doesn't now nor has it really ever cared about "security" - it's about the bottom line and power to them.

EDIT:

You see this what you get when you remove the variable of competition from the equation (aka capitalism).  Competition breads invention and begets innovation. Competition is the reason my Droid can function as what is essentially a hand held laptop - all while allowing me to make phone calls.  If there were only ONE phone company - do you really think our smart phones would be what they are now?  Of course not.  Why would they?  One company, no competition, no reason to develop and or innovate.

Windows is the result of when a company - a single company is allowed to rule in a vacuum.  I am being quite serious here.  Windows is complete and utter trash.  Has been for decades.  But, why should MS care?  To the average user you either use it or nothing - considering most people don't know what Linux is or are afraid of it due to the misconceptions that are floating around out there.

MS should never have been allowed to have gotten to be where it is - but that's what happens when you elect fatcats that care more about greasing their own pockets (thanks lobbyist!) than doing what's right for all.

So go here IRC freenode ##windows  and argue your point and let me know when I want to have my popcorn ready. ;)

---

### Post by CharlesA on 2012-06-07
> **not found said:**
> 
Sure, no OS is 100% secure... but I have a sneaking suspicion that some are slightly more secure than others ;)


404

An OS is only as secure as a user makes it. The user is the weakest link, no matter what OS they are running. ;)

---

### Post by sffvba[e0rt on 2012-06-07
> **CharlesA said:**
> An OS is only as secure as a user makes it. The user is the weakest link, no matter what OS they are running. ;)

The circle we will create here will only land us in Recurring :p


404

---

### Post by CharlesA on 2012-06-07
> **not found said:**
> The circle we will create here will only land us in Recurring :p


404
Errr yeah...

Oops. :p

---

### Post by MisterGaribaldi on 2012-06-08
Um, folks, with respect, we've heard from Tim Burke on this, and therefore, absent any other new evidence of "evil" or "wrong doing" by anyone, haven't we pretty much beat this to death now?

You can use Secure Boot, and that will require a signed OS, but you can turn Secure Boot off, and then the same hardware will run anything you throw at it. Microsoft isn't doing anything to prevent this, and evidently signed onto this arrangement in the process of grouping everyone together to get this thing approved in the first place. End of story.

Besides, it's not like running an OS without having it signed and approved by hardware suddenly means the OS is a complete security risk or unworthy of being used.

---

### Post by wilee-nilee on 2012-06-08
> **MisterGaribaldi said:**
> Um, folks, with respect, we've heard from Tim Burke on this, and therefore, absent any other new evidence of "evil" or "wrong doing" by anyone, haven't we pretty much beat this to death now?

You can use Secure Boot, and that will require a signed OS, but you can turn Secure Boot off, and then the same hardware will run anything you throw at it. Microsoft isn't doing anything to prevent this, and evidently signed onto this arrangement in the process of grouping everyone together to get this thing approved in the first place. End of story.

Besides, it's not like running an OS without having it signed and approved by hardware suddenly means the OS is a complete security risk or unworthy of being used.

La. la , la I can't hear you I'm busy generating FUD. ;)

---

### Post by MisterGaribaldi on 2012-06-08
Oh, and regarding the whole "competition" thing, I agree with the sentiment there.

I can remember pre-AT&T de-reg times on the landline phone network, aka "POTS". It sucked. I mean, it worked well enough for what it was, but you rented your phone, you paid for every single device you wanted attached, you paid fairly exorbitant telco rates, even for local phone calls, and you were *not* allowed to connect your own equipment. There was relatively little innovation in phones during that time.

Now, contrast that with the post-82 de-reg/break-up. A zillion companies sprang into business making phones you could actually *gasp!* go to the store and buy. Anyone could go out and buy an answering machine, and while they started expensive, the prices dropped pretty quickly. You started seeing things like cordless phones appear on the market. Competition between all these hardware makers meant continuous and accelerating development. It also did other things, like drop your rates, allow local calls to be free, etc. A lot of good came from that, but the break-up was only the start. Without competition, it wouldn't have mattered a single bit.

---

### Post by ExSuSEusr on 2012-06-08
> **MisterGaribaldi said:**
> Um, folks, with respect, we've heard from Tim Burke on this, and therefore, absent any other new evidence of "evil" or "wrong doing" by anyone, haven't we pretty much beat this to death now?

You can use Secure Boot, and that will require a signed OS, but you can turn Secure Boot off, and then the same hardware will run anything you throw at it. Microsoft isn't doing anything to prevent this, and evidently signed onto this arrangement in the process of grouping everyone together to get this thing approved in the first place. End of story.

Besides, it's not like running an OS without having it signed and approved by hardware suddenly means the OS is a complete security risk or unworthy of being used.


That's entirely the point.

Let me ask you... IF Microsoft wanted to, could they lockout the hardware?  Yes or No? No no don't explain.. simple yes or no.

The debate isn't about whether or not they are or are not going to do i t- for the most part - it's the very fact they have the power if they wanted to - THAT is the issue at hand here.

I don't give a flip if I can "turn it off" or not the very fact that I even have to CONSIDER turning it off IS THE PROBLEM.  

No one company should ever have that kind of power.  

I realize my opinions are bias because of my visceral hatred of Microsoft... but nonetheless......

---

### Post by malspa on 2012-06-08
> **wilee-nilee said:**
> La. la , la I can't hear you I'm busy generating FUD. ;)

:lolflag:

---

### Post by MisterGaribaldi on 2012-06-08
> **ExSuSEusr said:**
> Let me ask you... IF Microsoft wanted to, could they lockout the hardware?  Yes or No? No no don't explain.. simple yes or no.

You know, as someone who hated Microsoft before it was cool... heck, as someone who hated Microsoft before there ever was such a thing as Linux which someone could put onto an x86 box and call an alternative, you can frankly save your vitriol for someone else who's more deserving of it.

I'll thank you to remember where this comes from, and it sure as heck isn't Steve Ballmer.

---

### Post by ExSuSEusr on 2012-06-08
You didn't answer the questions...

---

### Post by chocklet on 2012-06-08
My crystal ball can't seem to get such a clear read on the future as some of those here.  Mine evidently needs more hard information about the details of how things will work.

Some worthy FOSS advocates disagree on how to read the Red Hat decision (what would I pay to see a face-to-face confrontation between Carla Schroder and Caitlyn Martin?!).

There is one speculation that has the ring of truth... Restricted Boot on personal PCs will be bludgeoned and shredded by malware within days (hours?) of release into the wild.  And while there is an evil streak within me that will applaud, there is a pessimistic streak that suspects that the next level of Restricted Boot will be the more serious.

Sadly, some security people say that the biggest threat to PC security is the user, so the most effective way to maximize security is to take away control from the user.

---

### Post by KiwiNZ on 2012-06-08
This thread is like a round about, it's to to take the exit.

---

