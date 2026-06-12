---
title: "CGMiner Install problems (but also my learning disability?)."
date: 2013-12-07
forum: Ubuntu, Linux and OS Chat
---

### Post by KittyCatHerder on 2013-12-07
I haven't posted here in quite a while since the credentials system was compromised and I kept getting an infinite loop that I was finally able to figure out. Anyway, my problem is that I can not figure out how to simply install some BitCoin mining software called CGMiner. I have been using Ubuntu for a few years now and I still feel like a beginner. Every time I try to learn how to do something new with my Ubuntu machine by reading other users instructions and guides, I feel like they, every single time, assume the reader already knows how to do related tasks which are necessary prerequisites, or they assume that certain details can be left out for some reason. I don't understand how anyone ever learns how to do anything using the command line interface when I've yet to read a single guide that doesn't exclude something important. 

I first looked for GCMiner in the Ubuntu software center but it wasn't there. After a search, I found the CGMiner downloads web page and, because of a lack of instructions there or anywhere else, I had to guess which package was the right one for my system.[SIZE=3] [SIZE=2]After[/SIZE][/SIZE] decompressing the tar.bz or whatever it happened to be, I found a file inside containing "instructions" on how to install and use CGMiner. Long story short there, the instructions leave out many pre-requsite steps, such as installing other software that CGMiner depends upon to function and I am not able to find those instructions anywhere else. I basically just need help with the entire process of installing CGMiner. What I'm looking for is a set of instructions that include, literally, everything that I need to do in order to install it.

I also want to point out how difficult it can be to learn how to simply install software in Ubuntu and other Linux platforms. Nearly every single time I have tried to install some auxiliary software (CGMiner, Metasploit, etc) on my Ubuntu machine I have ran into some kind of problem that either stops me from being able to install the software, or makes it so convoluted and difficult that I end up giving up after wasting so much time and getting no where. Take Metaspolit for example. You can go to the official documentation for instructions on how to install it which consist of dozens of commands and pieces of code. If each commands prerequisite parameters aren't already met, the user must go and figure out on his own why the command didn't work and how to fix it. How does anyone ever learn anything about installing software and just generally using the command line interface to accomplish things in Ubuntu/Linux when something is always different or some parameter or option is not correctly fulfilled, which makes any documentation or instructions or guides completely useless? At least someone tell me I'm not the only one who has this problem!?

---

### Post by cariboo on 2013-12-09
I'd suggest to make things a bit easier on yourself, that you do a search for ppa's (personal package archive) for the programs you are looking for, this way it would save you a lot of work. PPA's contain an Ubuntu version of many packages created by ordinary users to make it easier for others to install them.

Once the package is downloaded, instead of using the Software Centre to install the package, use gdebi (available in the repositories), it will tell you if there are any unmet dependencies, and usually help you install them.

---

### Post by KittyCatHerder on 2013-12-13
> **cariboo907 said:**
> I'd suggest to make things a bit easier on yourself, that you do a search for ppa's (personal package archive) for the programs you are looking for, this way it would save you a lot of work. PPA's contain an Ubuntu version of many packages created by ordinary users to make it easier for others to install them.

Once the package is downloaded, instead of using the Software Centre to install the package, use gdebi (available in the repositories), it will tell you if there are any unmet dependencies, and usually help you install them.


Sorry it took me so long to reply. I don't think I've ever heard of a  personal package archive. There are some software that I want to just  install easily and use and learn all of its details later. Such is the  case with CGMiner. Maybe this technique will help. I will report back  after I have tried it. Thanks.

---

### Post by dansanti on 2013-12-13
Hi!

if you want to install cgminer, you have to build it, install bfgminer better i's more easy, 
on my blog  i write how install it
[http://probandoubuntu.blogspot.com/2013/05/bitcoin-moneda-virtual-transacciones-y.html](http://probandoubuntu.blogspot.com/2013/05/bitcoin-moneda-virtual-transacciones-y.html)

---

### Post by KittyCatHerder on 2013-12-30
> **dansanti said:**
> Hi!

if you want to install cgminer, you have to build it, install bfgminer better i's more easy, 
on my blog  i write how install it
[http://probandoubuntu.blogspot.com/2013/05/bitcoin-moneda-virtual-transacciones-y.html](http://probandoubuntu.blogspot.com/2013/05/bitcoin-moneda-virtual-transacciones-y.html)

As soon as I get some more time I'm going to try this. How well/how easy does this software do solo mining?

---

