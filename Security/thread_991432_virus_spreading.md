---
title: "virus spreading?"
date: 2008-11-23
forum: Security
---

### Post by penguinee on 2008-11-23
Hi! 
I think I just got a virus on my ubuntu desktop... (installed via wine)
it looks like a windows virus.
So, my question is: can the virus be dormant while I'm running Linux, but can it activate when I run my PC? (Win XP)
I am dual booting.

Thank you!

---

### Post by aysiu on 2008-11-23
I don't see how Windows XP can run the Windows program installed through Wine on your Ubuntu partition.

But if you delete the /home/*username*/.wine directory, that should pretty much get rid of the virus, too.

---

### Post by cariboo on 2008-11-23
First off, why leave the virus on your computer, get rid of it. Second Windows can not access an Ext3 partition without third party software, so there is a very slight chance that it will affect your winows partition. Third even if there was the slightest chance that Windows could access an Ext3 partiton, you should have an up-to-date antivirus scanner on your Windows installation.

Jim

---

### Post by lukjad on 2008-11-23
First things first: Describe in more detail the problem, it could just be a bug or misconfiguration.

If you want to test this, go to your home folder, and click on *View->Show Hidden Files*. Then copy all the files starting with a period (e.g. .gnome) to an external drive. Then you can either delete a few that you think are causing the problem or delete them all and start putting them back in, one by one to see which on causes the problem.

> **penguinee said:**
> Can the virus be dormant while I'm running Linux, but can it activate when I run my PC? (Win XP)

If you are sure it is a virus or are just wondering about viruses and Linux:

Simple answer: You can have a virus in XP when you have Ubuntu on your computer but it will not be running when you have Ubuntu running.

More Complex Answer: There are no wild or common viruses for Linux at this time. There are some that exist, but they are not common and do not spread and were designed as a test to see if they could be created. 

You can run a Windows virus from WINE, but with limited efficiency. Unless it was specifically made to search for specific files, it could not delete much. Don't try it though, because, well, who knows exactly what it will do. I installed one once and it started posting... unsuitable images to my Desktop. All I had to do was uninstall WINE, remove all the files associated with WINE and the problem went away. Needless to say, don't try this at home kids. ;)

There is also the possibility that the virus that infects XP could install itself in the MBR and/or the BIOS and affect your devices and bootup. Thus far, they are rare, but still, something to consider. (Google them, it is quite fascinating to read about.)

---

### Post by penguinee on 2008-11-23
Wow!
Thanks for your quick replies!
I think I'll kill the wine directory. Does this mean that all my other games installed with wine will die too? Oh well.


> **lukjad007 said:**
> 
If you want to test this, go to your home folder, and click on *View->Show Hidden Files*. Then copy all the files starting with a period (e.g. .gnome) to an external drive. Then you can either delete a few that you think are causing the problem or delete them all and start putting them back in, one by one to see which on causes the problem.




I'm sorry, how would one do this? (I'm really bad with linux--or does this refer to the pc? :S)

P.s. thank you for your outstanding help! This community rocks!

---

### Post by lukjad on 2008-11-23
Sorry. Here is the full path:
Click on *Places->Home Folder*
When it opens Click on:
*View->Show Hidden Folders*
I Then a bunch of files and folders should show up. Copy those that start with a period or dot.

I'll see you in the morning. Hope this helps.

---

### Post by penguinee on 2008-11-23
> **lukjad007 said:**
> Sorry. Here is the full path:
Click on *Places->Home Folder*
When it opens Click on:
*View->Show Hidden Folders*
I Then a bunch of files and folders should show up. Copy those that start with a period or dot.

I'll see you in the morning. Hope this helps.

Thank you so much!

---

### Post by hyper_ch on 2008-11-24
> **penguinee said:**
> 
I think I just got a virus on my ubuntu desktop... (installed via wine)
it looks like a windows virus.

And what makes you think so?

---

### Post by tvtech on 2008-11-24
> **cariboo907 said:**
> First off, why leave the virus on your computer, get rid of it. Second Windows can not access an Ext3 partition without third party software, so there is a very slight chance that it will affect your winows partition. Third even if there was the slightest chance that Windows could access an Ext3 partiton, you should have an up-to-date antivirus scanner on your Windows installation.

Jim


I've found a number of "tagged files"  via use of AVG and Ext3 drivers in windows,  in researching they were indeed malicious code added to linux installation, I install a lot of "untrusted source software"  so it's very likely some of it may be malicious, I tracked down the problems, deleted them and didn't have an issue.  Due to permissions restrictions on my EXT2/3 driver in windows I had to do this manually from a live cd.  But no fuss no muss happiness was had by all.  Just remember just because it's hard to program malicious software for linux directly due to pear review of open source code before publishing, it doesn't mean it's not going to happen. so the long and short of it is, if you don't want to learn much get AVG for linux give it the appropriate permissions. OR the better option is to learn how to use iptables and the other built in linux firewalls.  safer computing is smarter computing, not more software computing,

---

### Post by hyper_ch on 2008-11-24
> **tvtech said:**
> I've found a number of "tagged files"  via use of AVG and Ext3 drivers in windows,  in researching they were indeed malicious code added to linux installation, I install a lot of "untrusted source software"  so it's very likely some of it may be malicious,
So you run a scanner that looks for windows malware on your linux files and you are surprised it tags things?

---

### Post by squeakyneb on 2008-11-24
So if i have wine, some windows virus' will run? How can I disable wine, but easily re-enable it without any un/reinstallations?

---

### Post by jyaan on 2008-11-24
Yea I'm not so sure I believe it either :S

---

### Post by rakris on 2008-11-24
> **penguinee said:**
> Hi! 
I think I just got a virus on my ubuntu desktop... (installed via wine)
it looks like a windows virus.

Thank you!


You probably saw some bug in Ubuntu (Welcome to ubuntu :lolflag:) . Not a virus :)

---

### Post by HermanAB on 2008-11-24
In general, Windows viruses don't run on Wine.  Heck, even good Windows programs don't run on Wine.  A virus running on Wine would be a miracle.

---

### Post by decard_pain on 2008-11-24
as far as i'm aware no virus ran from wine could infect your system

here is why

wine can't see your linux files(unless you were stupid and added all drives to the wine config)

but I'm sure you didn't do this as the wine documentation tells you not to

also a windows virus looks for exes and dll files to infect....Linux don't run on exes and dlls
the only other thing a virus would infect is zip files but still imposable for a windows virus to infect you Linux files due to permissions.
in fact if i had a virus at hand I'd prove this by letting it run in wine.



[http://www.f-secure.com/v-descs/lindose.shtml](http://www.f-secure.com/v-descs/lindose.shtml)

[https://forums.symantec.com/syment/blog/article?message.uid=305947](https://forums.symantec.com/syment/blog/article?message.uid=305947)

these are the only 2 cross platform virusis that exist(to my knowledge)

but like i said there is no way for any virus escape the wine directory as they can't see beyond it

this is the main reason i use ubuntu instead of windows

---

### Post by aysiu on 2008-11-24
> **decard_pain said:**
> as far as i'm aware no virus ran from wine could infect your system

here is why

wine can't see your linux files(unless you were stupid and added all drives to the wine config) Are you sure about this?

Maybe things have changed since a couple of years ago, but I remember before FileZilla was ported to Linux that I used to run it in Wine to FTP files to my website, and I could FTP files in my regular /home/*username* directory.

---

### Post by decard_pain on 2008-11-24
well it could access home/documents and also the desktop but other than that it's restricted to what wine is allowed to see.

edit
in fact you are right it can use the home folder

---

### Post by beyboo on 2008-11-24
> **HermanAB said:**
> In general, Windows viruses don't run on Wine.  Heck, even good Windows programs don't run on Wine.  A virus running on Wine would be a miracle.

:lolflag:

---

