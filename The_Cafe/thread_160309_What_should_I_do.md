---
title: "What should I do ?"
date: 2006-04-14
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-04-14
Well, I've been just straight ubuntu for over 3 months and have really liked ubuntu. It's great. I have had almost no problems with Ubuntu but any I have had a very minor. When I first got my computer, it had windows on it and I used it for 2-3 weeks before it broke. When it broke I tried to restore but that didn't help. I found out that I can download the drivers and then it will work. The reason that I kinda need to switch back to windows is my mom. She says that I need to change back to do "reports." Which I can do on Ubuntu. I was planning to completly back-up my system and then restoring the entire thing but I am not sure about this...I have a 15 gig dapper partition that I never us, can I make my system restore install to that partition ?

---

### Post by stuporglue on 2006-04-14
> She says that I need to change back to do "reports." Which I can do on Ubuntu.

Why not create a great looking report about why you should stick with Ubuntu instead of Windows? Have a handout (OO Write), some data and graphs about efficiency (OO Calc) and a short presentation to show the family (OO Present). 

If you have to reinstall Windows, and you have real install disks, install Windows to the 15 Gig dapper partition. Windows will overwrite the MBR, so Ubuntu will be there invisible untill you're able to switch back. When you're ready to switch back, use a live CD to re-install grub to the MBR. 

Obviously, don't do anything your mom would get mad about.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=stuporglue]Why not create a great looking report about why you should stick with Ubuntu instead of Windows? Have a handout (OO Write), some data and graphs about efficiency (OO Calc) and a short presentation to show the family (OO Present). 

If you have to reinstall Windows, and you have real install disks, install Windows to the 15 Gig dapper partition. Windows will overwrite the MBR, so Ubuntu will be there invisible untill you're able to switch back. When you're ready to switch back, use a live CD to re-install grub to the MBR. 

Obviously, don't do anything your mom would get mad about.[/QUOTE]
I only have a system restore disc :(

---

### Post by Stew2 on 2006-04-14
Most standard "restore" discs that I have seen dont give you any options for partition selection when you use them. They simply restore the computer to the state that it was in when you bought it, wiping everything in the process. You could back up your Ubuntu stuff, restore your drive, then reinstall Ubuntu and dual boot if so desired. Hope this helps.
Regards,
Stew

Edit: If you do go the dual boot route, you can edit grub to boot Windows by default, then if someone else in the family wants to use Windows, they wont have to change the boot selection every time they start the computer.

---

### Post by stuporglue on 2006-04-14
> wiping everything in the process.

Yup. So, you can't use your HD as the backup place!

---

### Post by Stew2 on 2006-04-14
[QUOTE=stuporglue]Yup. So, you can't use your HD as the backup place![/QUOTE]

Ummm... I meant to back up to removeable media. Guess I should have been more specific. :)

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=stuporglue]Yup. So, you can't use your HD as the backup place![/QUOTE]
I have no idea what to do. I don't have anything that I could put the back-up on. It only has a 1gig mem stick too, so with over 3 gigs of music + my breezy install + all the programs I have it wouldn't fit. Great.

---

### Post by Stew2 on 2006-04-14
[QUOTE=MasterChief1234]I have no idea what to do. I don't have anything that I could put the back-up on. It only has a 1gig mem stick too, so with over 3 gigs of music + my breezy install + all the programs I have it wouldn't fit. Great.[/QUOTE]

No CDRW?

---

### Post by matthinckley on 2006-04-14
I'm at work right now (using windows..) so I can't look up the actual commands but I know there is a way to do a full backup using tar and have it split the file into chunks that will fit onto cd's or dvd's so you could back it up this way and burn it on cd's or dvd's

then you could use your restore disc to reinstall the factory os 

use the ubuntu cd to resize your win partition and install ubuntu

then restore the backup from the cd's or dvd's


just food for thought...


Matt

---

### Post by NeghVar on 2006-04-14
Is it your computer or your moms? If it is yours I'd advise educating her as to the fact that Ubuntu will do what you need easily. Also if it is hers, bring up the fact that Linux is 99.9% free of viruses and 100% free of spyware. Also note the cost ratio should Microsoft ever decide that you NEED to update by changing some of the code in oh I don't know say the .doc format.

Also, if you happen to use the computer for school work, show her how difficult it is to run windows games, if you play this one right she will agree that it saves you from being distracted. I know it can be done fairly easily, but hey she don't need to know that, she just needs to know that you can't install it, no need to lie lol, just omit certain facts that don't support your case.

Feel free to argue with other advantages, such as the inherent security, the fact you don't need to restart for simple updates, or any updates that I've found so far. Oh and if you really wanna pour it on, bring it up that many corporations use Linux in some part of their organiazation and that since your already proficient in Windows that you are familiarising yourself with alternatives so that should you ever have to use it in the workplace you can be proficient with it, impress your bosses and thereby possibley advance your career...

Note for some of these you must be a good con artist lol.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=NeghVar]Is it your computer or your moms? If it is yours I'd advise educating her as to the fact that Ubuntu will do what you need easily. Also if it is hers, bring up the fact that Linux is 99.9% free of viruses and 100% free of spyware. Also note the cost ratio should Microsoft ever decide that you NEED to update by changing some of the code in oh I don't know say the .doc format.

Also, if you happen to use the computer for school work, show her how difficult it is to run windows games, if you play this one right she will agree that it saves you from being distracted. I know it can be done fairly easily, but hey she don't need to know that, she just needs to know that you can't install it, no need to lie lol, just omit certain facts that don't support your case.

Feel free to argue with other advantages, such as the inherent security, the fact you don't need to upgrade for simple updates, or any updates that I've found so far. Oh and if you really wanna pour it on, bring it up that many corporations use Linux in some part of their organiazation and that since your already proficient in Windows that you are familiarising yourself with alternatives so that should you ever have to use it in the workplace you can be proficient with it, impress your bosses and thereby possibley advance your career...

Note for some of these you must be a good con artist lol.[/QUOTE]
It's 100 % my computer. Thanks for the advice. The windows restore disc is "too scratched to use ;) " :)

---

### Post by NeghVar on 2006-04-14
> It's 100 % my computer. Thanks for the advice. The windows restore disc is "too scratched to use

That works too lol. But ya, I'm not sure of the relationship you have with yr mom and what she is like, if it were me and my computer and my mom id tell her flat out no. For what I do Ubuntu works perfectly.

I go on the net, I use FF regardless of MS/Linux, I IM, Gaim works great, although I wish I could change my name in yahoo, and in my spare time i write scripts/screenplays, once again I use OOo in MS or Linux so I have no compeling reason to use windows, except photoshop, but i just dont edit pictures now.

---

### Post by xXx 0wn3d xXx on 2006-04-14
Ok, thanks everyone :) Problem solved. Looks like I'll be using Ubuntu for a long time.

---

