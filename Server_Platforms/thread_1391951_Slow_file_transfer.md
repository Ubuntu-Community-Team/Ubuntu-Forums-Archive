---
title: "Slow file transfer"
date: 2010-01-27
forum: Server Platforms
---

### Post by mw4jet on 2010-01-27
Hi and thank you all, I have found alot of good advice browsing the forums.
 
I have 8.04.3 server-32bit. It is on an HP 2.3ghz Pent 4 with 512 mb of RAM.
I had previously installed Ubuntu and Kubuntu in a dual boot with XP (actually had a triple boot with XP, Ubuntu, and a BETA Windows 7) for a while, Grub got messed up so I ended up wiping it and just put my XP back on it. 
 
I have been intimidated by the command line and when thinking server, I tried the 30 day deal with windows Home server, its OK but it's $100.00 for the permenant version.
 
Anyway, I manned up to the challenge, installed Ubuntu server, set up as SSH and Samba. I administer from PuTTy and WEBMIN, I tried TightVNC but the GUI seemed very useless, so on a reinstall I went headless. 
totally
The problem is I have alot of MP3 files I want to transfer back to the server that I had previously transfer to and back again from the Windows server, it was sceamin' fast compared to this. 
 
I have found threads talking about using NTFS, I have the EX3, or whatever the Ubuntu format is. Could that cause slow transfers, from NTSF through Samba to Ubuntu?
 
Some direction would be greatly appreciated.

---

### Post by gobbledigook on 2010-01-27
if you are using samba to connect and transfer your files then it should just work! i have gigabit LAN and my local file transfer speeds are very quick! you could try posting your smb.conf located at /etc/samba/smb.conf to see if there are any issues.... but i would put my money on a bad wireless connection? are you wireless or LAN?

---

### Post by mw4jet on 2010-01-27
I have wireless, the server is hardwired to the router, I will verify, but xp to xp, xp to vista, etc... are fine. Will check to night.

---

### Post by mw4jet on 2010-01-27
I'm pretty green with Ubuntu so see if I did this right. I could not get a response with the file from above,
 
 > /etc/samba/smb.conf 
 
First permission denied, then I tried sudo as well, got no file found.

---

### Post by coral66 on 2010-01-28
Try /etc/smb.conf

---

### Post by mw4jet on 2010-01-28
Same thing....no such file or directory.
 
 
I've spent this evening looking for info....the problem is not uncommon, just that there are no clear fixes for someone new to Ubuntu like me.

---

### Post by BobVila on 2010-01-29
> **mw4jet said:**
> Same thing....no such file or directory.
 
 
I've spent this evening looking for info....the problem is not uncommon, just that there are no clear fixes for someone new to Ubuntu like me.

How are you connecting to the server? It seems odd that your smb.conf isn't in either of the places it would normally be...

---

### Post by Vegan on 2010-01-29
look for your smb.conf is /etc/samba/smb.conf

---

### Post by mw4jet on 2010-01-30
I am using Putty. I copied and pasted Vegan's text:
 
>  
/etc/samba/smb.conf 

 
No good, received:
 
>  
-bash: /etc/samba/smb.conf: Permission denied

 
If I type in: 
 
>  
sudo /etc/samba/smb.conf 

 
I receive:
 
> sudo: /etc/samba/smb.conf: command not found 
 
 
I find threads blaming realtek network controller cards, some say nts is faster than samba.
 
I have been copying music files from my xp toughbook to the server, so far 12-14 gigs have been copied and its been 12 hours, I have about 36 gigs more to go, at this rate it might be done by Monday night, (Sat morn now) LOL.
 
 
I know it is not a hardware issue because I did the exact same thing with a windows home server installed an the same PC as Ubuntu server is now on, it took about 7-8 hrs to move the whole deal. I transferred it both directions with no noticable difference.
 
 
The only thing I have done is install ssh and samba on initial install. It is hard wired to Lynksys router--54mbps-- "g", I suppose I could hard-wire the Toughbook to the same router and try that. 
 
I installed webmin and did a 
 
> sudo apt-get update
 
It performed that quite fast, can't say how much data is coming in and at what rate.
 
I'll keep looking, let me know if this makes sense to any of you.

---

### Post by mw4jet on 2010-01-30
BTW,
 
What is this smb.conf file going to tell me----or you---?

---

### Post by mw4jet on 2010-01-30
Removed wireless card from source pc, hardwired directly to router that server is wired to and problem gone. Have not noticed and speed problems on the network before......new project? Maybe later.

---

