---
title: "Hundreds of thousands of ATMs in the world use WindowsXP"
date: 2014-01-28
forum: The Cafe
---

### Post by lz1dsb on 2014-01-28
I recently read an article about a "big" problem many banks are facing due to the end of support of WindowsXP. It turns out that hundreds of thousands of ATMs use WinXP and the support ends in April this year.
I was wondering... isn't this an opportunity for the system integrators out there - to offer Linux as an alternative? What an ATM machine does? Establish a secure channel to the main office, send authorization for each transaction, execute the transaction by controlling the money counting machine... it's mostly that. It needs to be stable, reliable, secure. The distribution could be off course customized, so that only the stuff that is needed is compiled. 
I don't know... to me it looks like a great opportunity, Plus, besides the support there are no licensing fees, so each bank could potentially save millions... What do you think?

---

### Post by Don_Stahl on 2014-01-28
I think that the ATMs almost always run a special "point-of-service-ready embedded" version of XP. See this Wikipedia link: [http://en.wikipedia.org/wiki/Windows_Embedded_POSReady](http://en.wikipedia.org/wiki/Windows_Embedded_POSReady) 

Unlike desktop Windows XP, Microsoft will continue supporting XPe through 2016. That's a point that's missed in nearly every news story on ATMs and XP.

However, what your suggesting is very feasible. The other day I was rebooting a programmable logic controller (PLC) which runs several instruments on a light industrial process, and... there was the penguin! Linux is already in use for automation. It's a short step from a PLC to an ATM.

---

### Post by TheFu on 2014-01-28
This is not the first time something like this happened.
ATMs ran MS-DOS, OS/2, Win2000, WinXP previously. This is just another migration.

It all comes down to the ATM and backend processing companies - most banks do not build their own software - they pay someone else like TSYS or Jack Henry.

There is other news - at least for the USA.  EMV card support was scheduled for Oct 2014, but that has been moved to Oct 2015, so different card readers will need to be installed. I suspect the OS change and hardware updates will happen concurrently.

---

### Post by lz1dsb on 2014-01-28
That's a valid point! I didn't know about this, and indeed the articles seem to miss this vital information ;) 
I think Linux in embedded environments is really picking up. There's not even an Arduino board that runs Linux! Which is awesome!

[COLOR=#DD4814][COLOR=#000000][SIZE=2]TheFu[/SIZE]: [SIZE=2]EMV cards? Do you mean the cards with a magnetic stripe? I haven't used such in ages ;)[/SIZE][/COLOR][/COLOR]

---

### Post by mastablasta on 2014-01-29
even for desktop you can get extended support for winXP but it will be pricey. which is what happens when you lock yourself in.

i dont' htink ATM is much of an issue regarding support. they probabyl replace them every once a while and when they replace the amt new system is probably used as well.

what i found interesting is the thing i read about not long ago - criminals making small hole into atm to get to USB plug and then loading malware on it that enabled them to empty the ATM (windows at it's best :-) ). they glued the hole back, when bank refilled they just emptied it again (big notes only...). banks didn't notice the theft for quite some time. apparently malware is made so that the person withdrawing needs to call to "cetral HQ" to get a code. well id ont' knwo much abotu these systems anyway, but i bet this is used on windows ATM mahcines.

---

### Post by Ubi_one_2014 on 2014-01-29
windows does not belong on mission criticle environments like ATM's , Hospitals, Nucleare Reactors.  period

---

### Post by mastablasta on 2014-01-29
you forgot that they used it on uranium centrifuges in Iran :-D maybe they also use it on nuclear power plants.

---

### Post by TheFu on 2014-01-29
Control centers are very different from your home and work PC.  I've worked in them and wrote and deployed software to a few around the world.  All were on air-gapped networks.  Nothing came in (well, except via encrypted satellite transmission) and data was transmitted out of the control center over private lines to other centers around the world. 1-way protocols were used.

There is nothing wrong with running any OS in an environment like a control center, provided the issues are known, people are trained, retrained, tested, and issues mitigated.  Anyone caught thinking about breaking the network rules should be fired (or shot, depending on the severity).  Heck, we never patched anything after deployment unless it was required to correct an unpredictable failure mode that couldn't be mitigated or some new software required newer core libraries. Patching systems that are working fine is a risk greater than any patch fix could possibly provide.  If it ain't broke, don't touch it.

Also - don't let anyone else touch it and don't let it be accessed from outside the room.  Superglue in every USB port, anti-tamper tape on every console access port, don't let the computers be touched without breaking anti-taper tape.  No data input except by swapping the HDD or over the secured network - period.  All other ways to get programs in need to be physically prevented.  Temporary contractors are the worse ... always carrying a flash drive.  Strip search those people - with a cavity search - no USB devices, none. Not even the keyboards or mice.

Oh - and no wireless or wifi or bluetooth devices in the room either. Leave your cell phone, BT-headset in the car or back in your desk.  Control centers need these extra protections. This applies to trusted environments where everyone is know, had background and probably government background checks by the FBI/NSA.

OTOH, if the device is on a non-air-gapped network OR used by untrusted people (like ATMs are), then I'd want the minimal OS possible with only the programs necessary to do the job.  Running a full WinXP on a POS system is crazy, but running a full Linux on a POS would be just as crazy. Don't make things easier for the crackers.  Lock it down so that doing anything except the 1 exact purpose the device is meant to be used for can be done. Nothing else.

I have no doubt that WinXP is used in control centers and on nuclear vessels.  That is changing, but legacy is legacy.

---

### Post by lz1dsb on 2014-01-30
Wow... TheFu, that was a nice insight. I really haven't thought that there're so many issues.

---

### Post by chili555 on 2014-01-30
> What an ATM machine does? Establish a secure channel to the main office, send authorization for each transaction, execute the transaction by controlling the money counting machine... it's mostly that. And it also texts its owner to say it's jammed or low on money or out of money,  etc. The owner I'm related to shows up later in shorts and a grease-stained t-shirt with a cigar in his mouth and $50,000 in twenties in a wrinkled paper bag and tells the machine to shuddup, ya damn nag!.

---

### Post by Jonor on 2014-03-20
A somewhat interesting [COMPUTERWORLD update]("http://www.computerworld.com/s/article/9247096/ATM_operators_eye_Linux_as_alternative_to_Windows_XP") mentioning that almost 30% of installed point of sale systems at convenience stores and petroleum retailers already are Linux-based.

---

### Post by kurja on 2014-03-21
I work with industrial automation systems, and yes, there are xp systems running stuff around the world in chemical factories, powerplants etc. They're not by any means ordinary default installs though (thank gods for that).

Tux pops up often, too.

---

### Post by lz1dsb on 2014-03-22
30%... That's quite a big number if we're talking worldwide. I've always thought that having a Win machine for POS terminal is such a waste of money ad resources. Fortunately with the advent of the bare bone machines in small form factor it's getting easier and cheaper to build such machines, if you're not that big to build the cases and everything in house of course :)

---

### Post by james114 on 2014-03-22
I don't see any point of sale system installed linux-based OS yet (most of them are Windows XP.)

---

