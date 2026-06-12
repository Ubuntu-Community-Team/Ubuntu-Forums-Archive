---
title: "Setting up a server for a website"
date: 2011-11-13
forum: Server Platforms
---

### Post by MGadAllah on 2011-11-13
I am in the process of ordering a hosting from [www.linode.com](www.linode.com) and they are offering an empty hosting where I install everything from scratch.
I know a very few information about linux but in a big need for the website and shared hosting is sucks.
How or what could be the way to setting up ubuntu server, then php, then apache, then mysql?
Also how to make the server secure as possible?
Thanks a lot and much appreciated.

---

### Post by Lars Noodén on 2011-11-13
I would start by reading the stickies over at the [Security discussions](http://ubuntuforums.org/forumdisplay.php?f=338) and the one security sticky at [Server platforms](http://ubuntuforums.org/forumdisplay.php?f=339).

---

### Post by MGadAllah on 2011-11-13
Do I need to get any private sessions and pay some one to teach me some basics or I can find my way out in my own?

---

### Post by Lars Noodén on 2011-11-13
You can probably find your way on your own and with asking questions here.  Are you going to install some CMS or serve static XHTML?  If the latter, then you can postpone worrying about PHP and MySQL.  

Have you set up the server so that your SSH connections are using [keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) only?  That would be the first thing to look at.

---

### Post by MGadAllah on 2011-11-13
> **Lars Noodén said:**
> You can probably find your way on your own and with asking questions here.  Are you going to install some CMS or serve static XHTML?  If the latter, then you can postpone worrying about PHP and MySQL.  

Have you set up the server so that your SSH connections are using [keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) only?  That would be the first thing to look at.

I've just ordered a hosting plan from BuyVM.net with the following details

Product/Service: 	
BuyVM - BuyVM-1024MB
Disk Usage: 	
0% 363.7 MB of 60 GB Used / 59.6 GB Free
Memory Usage: 	
1% 10.4 MB of 1 GB Used / 1013.6 MB Free
Bandwidth Usage: 	
0% 2 KB of 3 TB Used / 3 TB Free
CPUs:
4 Cores
Operating System: 	
Ubuntu Server 11.04

And I will use Drupal CMS

---

### Post by MGadAllah on 2011-11-13
- Later Edit - 
So I will do the whole thing from scratch for every single thing.

---

### Post by volkswagner on 2011-11-13
You should consider using a long term release for a production server.

10.04.3 Server edition is supported until April 2015
11.04 Server edition is supported until Oct 2012

If you use 11.04 you will need to do an upgrade (to add software and get security updates) which comes with risk of ending up with a broken system.

---

### Post by acc61287 on 2011-11-23
@MGadAllah
are you planning to host your own website?

---

### Post by MGadAllah on 2011-11-24
> **acc61287 said:**
> @MGadAllah
are you planning to host your own website?

Yes I will host it on a VPS

---

### Post by Mohamed GadAllah on 2012-01-07
Really too hard to go on with finishing up my website and keep reinstalling the VPS.
Also how to forge website tutorials is not for a VPS.
So please advise for really how to finish this task as it keeps me disappointed.

---

### Post by deonis on 2012-01-07
I don't even understand why would you get a space elsewhere. Why not  just use some junk-computer with Ubuntu and put it elsewhere at your  home? This way you will have full control over your server and you won't  pay anything to anyone.

---

### Post by Mohamed GadAllah on 2012-01-07
> **deonis said:**
> I don't even understand why would you get a space elsewhere. Why not  just use some junk-computer with Ubuntu and put it elsewhere at your  home? This way you will have full control over your server and you won't  pay anything to anyone.
You mean to host it in my own place?
But I do not have a very speed connection ... Just 4MB DL / 1MB UL
So it will not be speedy at all, and this is why I want to host it elsewhere.

But give more options if you are interested.

---

### Post by deonis on 2012-01-07
I see, well I do not know the purpose of your web site. If you just want to host some information and won't have to much bandwidth to your server then you are fine ...  Of course if you plan to have file exchange server then this solution won't work.

---

### Post by Mohamed GadAllah on 2012-01-07
> **deonis said:**
> I see, well I do not know the purpose of your web site. If you just want to host some information and won't have to much bandwidth to your server then you are fine ...  Of course if you plan to have file exchange server then this solution won't work.
The purpose of the website is an educational purposes.
I will offer educational stuffs and any files will be uploaded to [www.archive.org](www.archive.org) and just links to my websites.

---

### Post by deonis on 2012-01-07
It should be no problem whatsoever... Do you teach at a university, school ? If so consider to put your server in there ...

---

### Post by Mohamed GadAllah on 2012-01-07
> **deonis said:**
> It should be no problem whatsoever... Do you teach at a university, school ? If so consider to put your server in there ...
Things in Egypt is not like that ... we are 3rd world development country.
I should pay in my own as no such service here.

---

