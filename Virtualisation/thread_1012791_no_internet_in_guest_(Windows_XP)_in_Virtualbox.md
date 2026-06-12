---
title: "no internet in guest (Windows XP) in Virtualbox"
date: 2008-12-16
forum: Virtualisation
---

### Post by Magic_Spehar on 2008-12-16
I'm using the newest PUEL version of Virtualbox (2.06).  

I'm using Ubuntu 8.10 as host and Windows XP (Windows Tiny XP revision 9 for Virtualbox) as guest.

After solving the USB issue (which is Ok now), I still can't get on the internet.  I'm using NAT.  When I start Internet Explorer, it get the infamous "Cannot find server or DNS Error"-page.

In my host I have a working fast ADSL connection.  

Please help because I really need an Internet connection under Windows because the program for the update of my Navman GPS navigator only works under Windows and unfortunately Wine is no solution here.
  
I really don't want to use a dualboot between Ubuntu and Windows because I want to be as much "Windows"-free as possible.

---

### Post by HermanAB on 2008-12-16
Windows can be FOS in this regard.  I usually have luck with the 'Repair network connection' option in the network wizard.  Even if I want to use a fixed IP address in Windows, I first let the wizard fix things and do a DHCP setup, then I go back and set the IP address manually to what I want.

'Hope that helps!

Herman

---

### Post by Magic_Spehar on 2008-12-16
I found the solution:  
I had to use Intel PRO/1000 T Server (NAT) instead of the default option.

---

### Post by techngro on 2009-04-25
I registered an account just to say THANK YOU!!!! After a night of trying to get internet to work on my Ubuntu host/Windows XP guest machine, including complicated tutorials and whatnot, your suggestion finally got it to work. I used the server option. 

thanks a lot.

---

### Post by madhavvk on 2009-07-10
Excellent!

It worked for me too!!!

Thanks.

---

### Post by smoosh on 2009-07-14
Still can't get mine to work, tried everything.  Sad face

---

### Post by steveneddy on 2009-07-14
I was going to suggest changing the adapter type.

Looks like you did that, glad you got it working.

I also had to change adapter type to get mine to work as well.

There is version 3.0 out now that works very well.

---

### Post by MKVCrazy on 2009-12-14
OMG! I almost faint! because I got it WORKING! I have been working on this since I installed VirtualBox, about 5 days ago.

THANK YOU for the thread !! :D

---

### Post by UltramasterBDJ on 2010-03-26
I'm using Windows Vista as host, and Windows XP as guest, and your solution worked for me as well!
Easy as pie! :p

Thanks, Magic_Spehar! :D

---

### Post by airplus on 2010-04-15
Thanks!!! Mine is working too!!!  :)

---

### Post by ravya on 2010-04-23
Thank you very much !!

Ravikant

---

### Post by Doobie9 on 2010-07-24
It works!

---

### Post by LordDelta on 2010-07-31
Confirmed working in Windows 7 (as a host) as well. :)

Silly Virtual Box giving us AMD Drivers. (In case you can't tell, not an authority on these driver things)

---

### Post by oremusnix on 2010-08-12
It works! So simple! Thank you!
Virtualbox 3.2.8
Host ubuntu 10.04
Guest : windows xp on physical partition

---

### Post by luckylucky on 2010-11-19
> **Magic_Spehar said:**
> I found the solution:  
I had to use Intel PRO/1000 T Server (NAT) instead of the default option.

Oh thank goodness for ubuntuforums, and for your post!  It worked!

---

### Post by spezifanta on 2011-02-14
Installing the Intel drivers (PRO2KXP.exe) fixed the problem.

---

### Post by bvtest on 2011-02-16
Uhh, isn't TinyXP a pirated version of windows?

---

### Post by CharlesA on 2011-02-17
> **bvtest said:**
> Uhh, isn't TinyXP a pirated version of windows?
On that note, thread closed.

The OP is from 2008 and it's talking about tinyxp.

---

