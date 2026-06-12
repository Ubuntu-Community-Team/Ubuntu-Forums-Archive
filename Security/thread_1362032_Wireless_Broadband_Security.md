---
title: "Wireless Broadband Security"
date: 2009-12-22
forum: Security
---

### Post by soldier4jesus on 2009-12-22
I've got a question.  I have been trying to find topics on wireless broadband security. The things that I have been able to find have made everything just as clear as mud, so I thought that I would come on here and see what I can find out.

I have Verizon Wireless USB card that I use for my primary internet.  I don't have any kind of router or anything like that that I'm connecting through....I just connect straight to the internet.  I currently just have the Ubuntu firewall running on my computer.  My question is, what else do I need to add to my computer to make it more secure.  I know that I need to add the programs that look for root kits, but that's about the extent of my knowledge.  I was reading the other day about snort, but then I read that it doesn't work on wireless networks and I would need airsnort, but when I went to that, that program had been discontinued.  Can someone help me with this?  Thanks so much and Merry Christmas!!


God Bless!!
Wesley

---

### Post by bodhi.zazen on 2009-12-22
For general security see : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

When you say you are worried about security, what is it you are worried about exactly  ? 

Why do you feel you need something like snort ?

---

### Post by soldier4jesus on 2009-12-22
I just don't want someone being able to "hijack" my internet connection and being able to see what I'm viewing or steal my passwords. I have read the link that you posted on here, but I'm not that computer savy when it comes to some of terms being used.  Basically what I was trying to do is to give y'all, that are a lot more up-to-date and computer savy, a description of how I was logging into the internet just to see if I needed anything else besides just the firewall.  Thanks so much for your response.


God Bless!!
Wesley

---

### Post by bodhi.zazen on 2009-12-22
If you are not running a server you probably do not need a firewall.

If you are running wireless, because you are broadcasting your network packets, it is in theory possible for them to be intercepted and decoded. Same is true for say cellphones.

Look for white vans in your driveway and tech savvy neighbors.

Security is not a simple subject and only you can decide how paranoid you are and how much time you wish to spend learning additional security features. If you look at the security link I gave you, that is the proverbial "tip of the iceberg" in terms of security and you can learn as much or as little as you wish.

Security is not install it and forget it =)

---

### Post by soldier4jesus on 2009-12-22
O.K.  Thanks so much for your help with this.

God Bless!!
Wes

---

### Post by BkkBonanza on 2009-12-22
Make absolutely sure that you are using WPA2 security and a very good password on your wifi access. Do not use WEP mode or MAC address restriction only - if you value security at all. Your biggest security vulnerability is if you don't secure your wifi traffic.

If you have no choice about that then change your access provider or use a ssh secure tunnel to somewhere more safe. Just ask if you need more details on how to check this or what to do.

---

### Post by lisati on 2009-12-22
Just a thought: is the verizon wireless card one which hooks into a mobile phone network? If so, it's likely to work differently to the wireless many of us are used to on our home network.

---

### Post by bodhi.zazen on 2009-12-23
> **lisati said:**
> Just a thought: is the verizon wireless card one which hooks into a mobile phone network? If so, it's likely to work differently to the wireless many of us are used to on our home network.

I do not have one of these cards, but my understanding is they are basically a modem with a wireless phone connection and not a WAP , so no WEP or WPA.

---

### Post by soldier4jesus on 2009-12-23
It is a modem, but does work just like a cell phone....it even has it's own cell #.  On Ubuntu, you just plug it into one of the USB ports, and then click on the network icon in the top and the click on "Verizon" and it automatically will connect to the internet.

God Bless!!
Wes

---

### Post by __p1n__ on 2009-12-23
You should be okay from the surrogate to the mast.  Verizon uses CDMA(AES) and not GSM(A5.)  A5/1 is currently vulnerable to bruteforce attacks and A5/2 is crackable.

From the mast to the internet your communication is as vulnerable as anything is on Verizon's network.

---

### Post by soldier4jesus on 2009-12-23
Thanks so much for all your responses.

God Bless and Merry Christmas!!
Wesley

---

