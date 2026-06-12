---
title: "Tricky virus(BIOS? Some hidden compartment in my HDD?) I just can't nail the bugger."
date: 2013-12-29
forum: Security
---

### Post by staticx2 on 2013-12-29
Windows viral attributes:

SVHost processor load same after format of harddrive(Make note I had no clue what SVHost on windows XP was or did at time of observation. I did how ever know that if something in your processes list hit a suspiciously high process useage it was clearly a virus.)

Windows installation was repeated 3 times with same results. 

I installed Ubuntu 13.04 plus updates. All things in the clear, laughing and sniffing daisies at this point.

I installed Oracle VM Virtualbox(latest version for i386 no accompanied software.) Installed WinXP 32bit naturally. Immedietly after I had connected to a video game where I met my person of interest, I had suffered some issues with my VM and suspect some issue with my ubuntu how ever not clear.

Reinstalled Ubuntu and reinstalled all the other stuff mentioned.

Same issue. Ok, time to educate myself more than I have knowledge of so far.

I went thru a process of elimination as well as informed myself of what SVHost was and it's associated programs. I downloaded DBAN on a laptop seperate from the computer in question.(I have a second desktop PC that has been victomized. Since it has its own issues I'll ask questions about it in its own thread. So, stay tuned.)

Nuked harddrive. After nuke process that took 9 hours to complete, it gave me 3 lines of dev somethings(Don't remember them exactly.) that had failed. But, the main portion of the HDD was whiped clean and ran all 7 times successfully. I reinstalled Ubuntu and upgraded my security protacols and programs roster for Ubuntu. Still laughing and sniffing daisies there. After install of XP in VM, and set myself up, I DL'd a firewall, stuck it in a shared folder with VM. Installed it, ran it, and recieved more detailed info on what's going on with SVHost. What I didn't mention was I ran netstat -anobv, -ano, and -n 20 and iptraced several IP's. Only one was reocurring in all installations. Bare in mind that I had ran netstat immedietly after connection to the internet to the second and came to the conclusion that It's really hiding somewhere.

I began a process of elimanation and have concluded that either it's hiding in one of the failed to bomb departments in my DVDRom or my BIOs.
I found a forum( [http://ubuntuforums.org/showthread.php?t=1653997&page=3&highlight=BIOS+-+compromised+viruses](http://ubuntuforums.org/showthread.php?t=1653997&page=3&highlight=BIOS+-+compromised+viruses) ) that postulated a similar thought in a radiculusly rude and sarcastic trollish kinda way. Now, the very idea of a BIOs embedded virus freaks me out. However, I'd like to entertain the idea and perhaps develope a method of approaching and eliminating it.

Since I'm not the only one suffering from a ghost in my PC, this could very well be a next gen virus and should at the very least be entertained.

---

### Post by staticx2 on 2013-12-29
NAILED IT. GOD BLESS GOOGLE.

I'm posting a link to another forum that articulates the process in which to eliminate a BIOs virus. HA

[http://forum.bitdefender.com/lofiversion/index.php/t30060.html](http://forum.bitdefender.com/lofiversion/index.php/t30060.html)

---

### Post by CharlesA on 2013-12-29
svchost does a bunch of things but I've seen it sit at 100% CPU when searching for updates, especially on XP.

Have a read:
[http://arstechnica.com/information-technology/2013/12/exponential-algorithm-making-windows-xp-miserable-could-be-fixed/](http://arstechnica.com/information-technology/2013/12/exponential-algorithm-making-windows-xp-miserable-could-be-fixed/)

---

### Post by bashiergui on 2013-12-29
> SVHost processor load same after format of harddrive(Make note I had no clue what SVHost on windows XP was or did at time of observation. I did how ever know that if something in your processes list hit a suspiciously high process useage it was clearly a virus.)svchost is a normal process necessary in Windows. Read CharlesA's link.

A process using high CPU does not define a process as a virus. Viruses could peg the CPU, but so can a ton of normal processes. 

I don't know how you leapt to the conclusion that it was a BIOS virus. I'd need a whole lot more data to make that determination.

---

