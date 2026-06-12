---
title: "vista/ubuntu network problems"
date: 2010-04-16
forum: Server Platforms
---

### Post by nipsy on 2010-04-16
Okay, back again. Server is set up. Samba is running beautifully. Except for two desktops running Basic Windows Vista. Neither one will "see" the Ubuntu Server in the network.

Here is set - up

Server running Ubuntu 8.04 regular edition- sees two laptops, but not the two desktops

2 Vista Premium laptops- see all computers on network

One desktop running Vista Basic- sees laptops and dual boot desktop, but not server

One desktop running dual boot Vista Basic and Ubuntu 8.04- sees  laptops and other desktop, but not server

How in the blue hell can we connect these 2 desktops to read the server like everything else has??

Is there something in Samba to re-configure? 

Thanks in advance!!

Oh, and thanks for all the help we've already received.........

---

### Post by Bigadada_saba on 2010-04-16
> **nipsy said:**
> Okay, back again. Server is set up. Samba is running beautifully. Except for two desktops running Basic Windows Vista. Neither one will "see" the Ubuntu Server in the network.

Here is set - up

Server running Ubuntu 8.04 regular edition- sees two laptops, but not the two desktops

2 Vista Premium laptops- see all computers on network

One desktop running Vista Basic- sees laptops and dual boot desktop, but not server

One desktop running dual boot Vista Basic and Ubuntu 8.04- sees  laptops and other desktop, but not server

How in the blue hell can we connect these 2 desktops to read the server like everything else has??

Is there something in Samba to re-configure? 

Thanks in advance!!

Oh, and thanks for all the help we've already received.........

you have to have a better look at your vista  basic machine because vista basic on a whole has issues with becoming a part of a domain. I had problem with it seeing a windows sever. Good luck.

---

### Post by nipsy on 2010-04-17
I've been searching for hours upon hours again...no one seems to have an answer for me... I even tried changing the security folder, but once I go through the routes, the two desktops don't even have the folder to change...lol

But I'm gonna keep on keeping on..

---

### Post by Speakstofei on 2010-04-17
I missed the other post you made apparently, but it sounds to me like it quite possibly has something to do with the NetBIOS protocol or MSRPC suite of protocols on the Vista Basic machines.  I'm running 5 other machines (Ubuntu Laptop, Windows 7 Laptop, XP laptop, Vista Premium Desktop, PSUbuntu) off my Karmic Server and all of them can see it without any other special things done with smb.conf. (*Note: I do prefer using the system-config-samba pkg for my admin purposes for the ease of things.)  

It could also be your firewall settings on the Vista basic machines.  Check this out:
[http://support.microsoft.com/kb/971800/EN-US](http://support.microsoft.com/kb/971800/EN-US).  I hope this helps.

---

### Post by nipsy on 2010-04-17
> **Speakstofei said:**
> I missed the other post you made apparently, but it sounds to me like it quite possibly has something to do with the NetBIOS protocol or MSRPC suite of protocols on the Vista Basic machines.  I'm running 5 other machines (Ubuntu Laptop, Windows 7 Laptop, XP laptop, Vista Premium Desktop, PSUbuntu) off my Karmic Server and all of them can see it without any other special things done with smb.conf. (*Note: I do prefer using the system-config-samba pkg for my admin purposes for the ease of things.)  

It could also be your firewall settings on the Vista basic machines.  Check this out:
[http://support.microsoft.com/kb/971800/EN-US](http://support.microsoft.com/kb/971800/EN-US).  I hope this helps.



You didn't miss much, we just had hard drive issues before..:)

Thank you for that link, unfortunately it doesn't apply to either desktop as they both run SP2 and not SP1.  We use the same samba config, which works perfectly with every computer but those two.

I said it from the get go, VISTA hates me. No wonder I love Ubuntu so much..

*Back to searching for answers to this puzzle*

---

### Post by nipsy on 2010-04-19
Still no resolution to this irritation. Even Microsoft has no answers for us...

---

