---
title: "I'm not allowed to use Linux at school. How to fix this? Petition!"
date: 2008-11-09
forum: The Cafe
---

### Post by linuxisevolution on 2008-11-09
I was using Puppy Linux on my flash drive for a while, but one day the librarian walked by, and said "Whats that?" I said, "Linux." And.. She said "Have you taken this up with the business department?". Now, I got into 'trouble' and all the tech guys say "its not a good idea", and that, "it posses security threats." Well... I'm not allowed to WORK with my Linux format documents, but a bunch of other kids play wow everyday in the library, with there flash drives! Sign the petition, and teach the administrators a bit about our world.

---

### Post by Mr. Picklesworth on 2008-11-09
Why not just send them a nicely written letter? It's nicer to give them the choice to learn than a wave of might, attempting to force them in a direction with pure noise. They are probably not aware that the limitation to Microsoft-only formats is unethical.

---

### Post by linuxisevolution on 2008-11-09
I'm working on a letter now.

---

### Post by cardinals_fan on 2008-11-09
If you post a copy, I'll give my opinion.

---

### Post by Frak on 2008-11-09
No, it is a security threat.

I would say "no, it's a security threat", but if they were smart, they would password protect the BIOS settings and remove any boot options for other devices besides the HD. Further, don't give people access to administrator accounts. "Linux" or rather "Look, it's just Linux" is a security threat because it does introduce a foreign material into a networked facility. This opens an issue to worms, stealths, and polymorphs.

---

### Post by brunovecchi on 2008-11-09
If the sysadmins have a setup at your library that restricts permissions to the users of any type (ie, file permissions, visiting certain web sites, etc) then I doubt they'll let you use Puppy Linux, since it would override their setup.

But, If they just have a simple XP install (with the default system administration privileges), then there's no reason for them to deny you the use of your OS of choice, since it implies that they allow unrestricted access to the hardware the library provides.

---

### Post by linuxisevolution on 2008-11-09
I scan my flash drive weekly for viruses, and none have turned up... "if they were smart, they would password protect the BIOS settings and remove any boot options for other devices besides the HD." Thats what I said.

---

### Post by linuxisevolution on 2008-11-09
> **brunovecchi said:**
> If the sysadmins have a setup at your library that restricts permissions to the users of any type (ie, file permissions, visiting certain web sites, etc) then I doubt they'll let you use Puppy Linux, since it would override their setup.

But, If they just have a simple XP install (with the default system administration privileges), then there's no reason for them to deny you the use of your OS of choice, since it implies that they allow unrestricted access to the hardware the library provides.

They block the network via websense, which puppy will not let me past. It also does not override the file permissions. I tested it :)

---

### Post by Skripka on 2008-11-09
EASY.  Continue using as you like.  If you get caught apologize and claim ignorance.


I'll WARN you.  Sys admins at educational institutions *_**WILL NOT BUDGE**_*.  It doesn't matter what you can show them or tell them, they will _***NOT***_ budge in _***ANY***_ official capacity.

People do p2p, the install all manner of crap (plugins, softwares etc) on school machines to play games to facebook you name it--and keeping them working most of the time is a nightmare....most folks don't know how you're able to boot Linux off a flash dongle, but they WILL NOT officially sanction such. If students KNEW they could boot an OS off a USB dongle-there would be NO END to the possible problems--that is there perspective, and it is a very real one quite frankly.



You will NOT change their minds. Or their policies. They make one official allowance, and they have to let anyone-that is the nature of things.

---

### Post by smartboyathome on 2008-11-09
You should not try to force your school into this. If they don't want to, then its their choice. The more you try to force them, the more they will not want to do it. Its simple human nature.

---

### Post by Frak on 2008-11-09
> **linuxisevolution said:**
> They block the network via websense, which puppy will not let me past. It also does not override the file permissions. I tested it :)
The main one that's a threat is if they use elevation security on websense. Websense can ask for a profile header from the user and scan it for it's permissions. If you are a Power user or Administrator (usually) you can bypass the block because the header changed. There is a boot util disk on the intarwebs that allows you to reset the administrator password to nothing and allow anybody to access the account. In fact, some Linux distributions are made to support this.

Our system uses elevation security and domain account restrictions. We techs can use this to numb the domain controller (doesn't check privileges) and test settings for it. Thing is, though, somebody else can use their high elevation to bypass websense that way.

The reason why I'm so hard on this is because I can lose my job and get sued if the state finds out about it.

---

### Post by linuxisevolution on 2008-11-09
> **Skripka said:**
> EASY.  Continue using as you like.  If you get caught apologize and claim ignorance.


I'll WARN you.  Sys admins at educational institutions *_**WILL NOT BUDGE**_*.  It doesn't matter what you can show them or tell them, they will _***NOT***_ budge in _***ANY***_ official capacity.  Have I put enough HTML markup emphasis there?

People do p2p, the install all manner of crap (plugins, softwares etc) on school machines to play games to facebook you name it--and keeping them working most of the time is a nightmare....most folks don't know how you're able to boot Linux off a flash dongle, but they WILL NOT officially sanction such.  If students KNEW they could boot an OS off a USB dongle-there would be NO END to the possible problems--that is there perspective, and it is a very real one quite frankly.



You will NOT change their minds.  Or their policies.  They make one official allowance, and they have to let anyone-that is the nature of things.


Very well said. But, all I need is to be able to use OpenOffice or abiword. Neither of which will harm anything. They would just have to add the .exe to the public drive. But, they stick to their own ignorance.

---

### Post by Lord Xeb on 2008-11-09
Actually, there is a small problem with what you are doing. Linux can be used to hack and such and you are remove all the administrative restrictions that the computer had on it. You CAN access the HD on the computer, you CAN execute foreign commands from Linux and get passwords, and you CAN get into the servers from a terminal inside the network. So, the IT guys are correct. Now if you had a seperate computer to run it on (like I do with my laptop) they would not care as much because you do not have direct access to a computer.

---

### Post by linuxisevolution on 2008-11-09
They don't use elevation security. Websense is installed on the server, and remembers what ip's you have connected to, then blocks them when it reads its database...

---

### Post by Skripka on 2008-11-09
> **linuxisevolution said:**
> Very well said. But, all I need is to be able to use OpenOffice or abiword. Neither of which will harm anything. They would just have to add the .exe to the public drive. But, they stick to their own ignorance.



It has nothing to do with ignorance, but practicality.  If people KNEW they could boot an OS off a flash dongle-imagine how quickly Uni nets would go down in flames?  It is a difficult task even assuring working wireless nets on the 2 Evil Empires OSes, as well as wired nets--and getting official support for Linux from Sys admins will not happen in all honesty.


I used a UnderPoweredBook during my undergrad schooling.  I wanted to use the wireless net which used a IDIOTIC ActiveX security protocol which did not seem to support OSX.4 at all (ergo I could not use the campus wide wireless net on my laptop).  I asked the IT admins for help--they told me that "we don't officially support macs, sorry"  Their own computer labs are full of iMacs and this is what they tell me.  Ya, I was pyassed.  That is what you run into.

Points on you for doing the right thing--but I'll eat my shoes if you actually win--being able to run a Linux OS of a USB dongle.

---

### Post by smartboyathome on 2008-11-09
> **linuxisevolution said:**
> Very well said. But, all I need is to be able to use OpenOffice or abiword. Neither of which will harm anything. They would just have to add the .exe to the public drive. But, they stick to their own ignorance.

Then if they don't allow you to use it use an online service like Google Docs at school, and at home export them to your computer. Schools aren't democratic, after all.

---

### Post by linuxisevolution on 2008-11-09
Get ready to eat your shoes. Shikies are nice ;)

---

### Post by akiratheoni on 2008-11-09
Honestly, you should probably listen to the techies there. You may be smarter than them when it comes to Linux, but they have their jobs at stake when you run Linux on the computers. They won't budge at all. It's only school, I can live on Windows for two hours a day. It's not that big of a deal -- I'm just using Firefox and that's it. Have you looked into portable versions of OpenOffice.org and Abiword to put on your flash drive? That's probably the best solution, honestly, especially if that's the only reason why you're using Puppy Linux.

---

### Post by linuxisevolution on 2008-11-09
I do have the portable versions on my flash drive. Thats why Im running puppy.

---

### Post by Frak on 2008-11-09
> **linuxisevolution said:**
> I do have the portable versions on my flash drive. Thats why Im running puppy.
[http://portableapps.com/](http://portableapps.com/)

---

### Post by Skripka on 2008-11-09
> **akiratheoni said:**
> Honestly, you should probably listen to the techies there. You may be smarter than them when it comes to Linux, but they have their jobs at stake when you run Linux on the computers. They won't budge at all. It's only school, I can live on Windows for two hours a day. It's not that big of a deal -- I'm just using Firefox and that's it. Have you looked into portable versions of OpenOffice.org and Abiword to put on your flash drive? That's probably the best solution, honestly, especially if that's the only reason why you're using Puppy Linux.

Or more simply-use more standard file formats to save your work--is there a reason the OP must save things in OO.org and AbiWord formats and not the Old Faithful .doc format?

---

### Post by linuxisevolution on 2008-11-09
I am working on a 200+ page project. .odt works, and .doc has its problems when switching from the programs.

---

### Post by cardinals_fan on 2008-11-09
@linuxisevolution: two choices for transferring documents:

* Google Docs: Yes, Google watches you.  But if you aren't writing anything important, Google Docs can be very handy for transferring documents between home and school.  
**EDIT: Maybe this is a bit big/important for Docs (saw above post)**

* RTF format: Save your Microsoft Office docs in .rtf format and they should open up just fine in Abiword or OpenOffice.

---

### Post by bobyo134 on 2008-11-09
well i think there bill gates slaves to honest, i mean they cant even say Linux, they say luxlin

---

### Post by linuxisevolution on 2008-11-09
Bob is right -he goes to my school.

---

### Post by linuxisevolution on 2008-11-09
Thanks, I'll try it. Do images work at all?

---

### Post by cardinals_fan on 2008-11-09
> **linuxisevolution said:**
> Thanks, I'll try it. Do images work at all?
In rtf?  Sure.

---

### Post by Giant Speck on 2008-11-09
I really don't know how to say this without being potentially offensive, but if the school doesn't want you to use Linux on their computers, then you should respect their decision and not use Linux.

The computers are owned by the school, and they can regulate the use of the computers however they please.  

I'm surprised that they allow people to play World of Warcraft on school computers.  When I was school, we weren't even allowed to play Solitare.

---

### Post by Grant A. on 2008-11-09
*sigh*, yet more Windows bashing. It's Balmer who ruined the company, Bob, not Bill Gates.

I also noticed a comment in this thread saying they should lock-up their BIOS, while this is true, you can still run Linux from a flash drive on a Windows computer via QEMU. If they were REALLY smart, they would disable you from being able to use removable drives at all. ;)

[quote=Giant Speck]
I really don't know how to say this without being potentially offensive, but if the school doesn't want you to use Linux on their computers, then you should respect their decision and not use Linux.

The computers are owned by the school, and they can regulate the use of the computers however they please. 
[/quote]

+1

---

### Post by cardinals_fan on 2008-11-09
> **Grant A. said:**
> *sigh*, yet more Windows bashing. It's Balmer who ruined the company, Bob, not Bill Gates.

I also noticed a comment in this thread saying they should lock-up their BIOS, while this is true, you can still run Linux from a flash drive on a Windows computer via QEMU. If they were REALLY smart, they would disable you from being able to use removable drives at all. ;)
Running Linux in QEMU doesn't have any real risks.  A live CD allows many more possibilities.

---

### Post by Grant A. on 2008-11-09
> **cardinals_fan said:**
> Running Linux in QEMU doesn't have any real risks.  A live CD allows many more possibilities.

Yes, but if they were really concerned about security, they wouldn't allow foreign disks/drives at all. This is like washing your hands *before* you go to the restroom (lavatory).

---

### Post by linuxisevolution on 2008-11-09
We can't install any software in the windows accounts. So QEMU is a no-go.

---

### Post by Grant A. on 2008-11-09
QEMU would be installed on the flash drive, if memory serves.

---

### Post by Giant Speck on 2008-11-09
> **Grant A. said:**
> *sigh*, yet more Windows bashing. It's Balmer who ruined the company, Bob, not Bill Gates.

I also noticed a comment in this thread saying they should lock-up their BIOS, while this is true, you can still run Linux from a flash drive on a Windows computer via QEMU. If they were REALLY smart, they would disable you from being able to use removable drives at all. ;)

I don't think the original poster was bashing Windows or Microsoft, and I'm not accusing you of claiming that.  What the original poster is concerned about is that the school seems to consider running Linux from a flash drive a security risk, but doesn't consider running World of Warcraft from a flash drive a security risk.

I remember at my high school, all of the computers were logged into guest accounts.  In order to do anything major, such as install programs, you had to log into the administrator account.

---

### Post by linuxisevolution on 2008-11-09
Same with our school. :(

---

### Post by KiwiNZ on 2008-11-09
This is between the School authorities and the OP

This is not something for these Forums

---

