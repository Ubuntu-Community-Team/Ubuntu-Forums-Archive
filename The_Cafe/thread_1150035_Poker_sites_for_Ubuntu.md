---
title: "Poker sites for Ubuntu"
date: 2009-05-05
forum: The Cafe
---

### Post by tmos22 on 2009-05-05
Hey guys, to all the poker players out there, is there any site that i can play on with Ubuntu??

---

### Post by MontelEdwards on 2009-05-05
> **tmos22 said:**
> Hey guys, to all the poker players out there, is there any site that i can play on with Ubuntu??
Most sites that you could use with windows, you probably can use with Ubuntu, there should not be a difference.

---

### Post by OmarJ on 2009-05-05
no it's true, I've tried in the past and it's often difficult to find sites that let you play poker on linux. Coral poker works though!

---

### Post by tmos22 on 2009-05-05
Well im trying to playing on a B2B network at the moment and it isnt working for me :(

---

### Post by MontelEdwards on 2009-05-05
> **tmos22 said:**
> Well im trying to playing on a B2B network at the moment and it isnt working for me :(

what is it saying?
like an OS error or what?
elaborate

---

### Post by ssdt on 2009-05-05
most of the sites work in both so there is not much trouble with that. what type of os does it say is required or what site is it from?

---

### Post by wsonar on 2009-05-05
unless the site is coded for IE I don't see what the problem would be

make sure your flash and java work

---

### Post by bodhi.zazen on 2009-05-05
Moved to the cafe as it is not really a support thread.

I suggest you use google.

---

### Post by MontelEdwards on 2009-05-05
> **wsonar said:**
> unless the site is coded for IE I don't see what the problem would be

make sure your flash and java work
Some sites check what OS you are using, and sometimes they wont let you access it. I dont know why they do this.


You can install IE in linux with these commands.
```
sudo apt-get install cabextract wine 
```

then
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```


that will install IE


oh,
to run these go to applications >accessories>terminal

---

### Post by bodhi.zazen on 2009-05-05
> **m.deonte said:**
> Some sites check what OS you are using, and sometimes they wont let you access it. I dont know why they do this.

This information is contained in the "Headers" sent from your clients and is normally used by web site developers to select proper rendering for your browser.

---

### Post by tmos22 on 2009-05-06
I have download the poker software, but how do i install it? Its different to windows where you just click on the exe. and it installs, sorry, im a n00b when it comes to Ubuntu

---

### Post by MadCow108 on 2009-05-06
op doesn't mean poker web sites but poker clients.
I don't know of any sites that support linux.
You could try wine, but this will most certainly fail. These clients are usally full of trojan like functions written vor windows, I don't think wine would support something like that.
And you don't want it crashing in the middle of a 1000$ pot :)

You will have to use a virtual windows.

---

### Post by suitedaces on 2009-05-06
If you mean sites like pokerstars, I installed my pokerstars client quite easily with WINE. No .dll's or such needed.

---

### Post by slakkie on 2009-05-06
Haven't read the full post, but Pokerstars works great with wine.

Never tried the real money tables, but play money tables work like a charm (expect the same for real money tables).

---

### Post by suitedaces on 2009-05-06
> **slakkie said:**
> Haven't read the full post, but Pokerstars works great with wine.

Never tried the real money tables, but play money tables work like a charm (expect the same for real money tables).

Real money's where it's at! :guitar:

---

### Post by sharathpaps on 2009-05-06
If you want to play Poker in Ubuntu, then I think you should install PokerTH. 

```
sudo apt-get install pokerth
```

It is fully open source and everything can be customised through the GUI. It supports network gaming too. The interface is nice and friendly.

---

### Post by Glucklich on 2009-05-06
All the major Poker sites work with Wine. PokerStars, Full Tilt... you name it. Just install Wine as previously described and install it, like you would any other program with Windows.

---

### Post by tmos22 on 2009-05-06
K, im trying it now, thanks for the help

Everything worked out ok and now all i need to do is win some money :D

---

### Post by gtr32 on 2009-05-06
Most sites should work through web browser. Absolute Poker works in Linux but I'm not sure I would recommend them for real money play.

---

### Post by tmos22 on 2009-05-06
I am trying to play now on a b2b network, irisheyespoker.com but it is a bit dodgy, screen keeps flashing

---

### Post by glotz on 2009-05-06
> **sharathpaps said:**
> If you want to play Poker in Ubuntu, then I think you should install PokerTH.
++

---

### Post by webwiller on 2009-05-06
Pokerstars.com software runs fine under wine. Otherwise run WinXP with Virtualbox as a virtual machine and u'll run all poker softwares u want to!

An addicted! ;)

---

### Post by Junkieman on 2009-05-06
> **sharathpaps said:**
> If you want to play Poker in Ubuntu, then I think you should install PokerTH. 

PokerTH is the best I've come across, try it! :)

---

### Post by suitedaces on 2009-05-06
> **Junkieman said:**
> PokerTH is the best I've come across, try it! :)

It's nice for a bit of casual time-killing, but it doesn't provide for online gambling (I prefer "investment"!) unfortunately.

---

### Post by Junkieman on 2009-05-06
> **suitedaces said:**
> It's nice for a bit of casual time-killing, but it doesn't provide for online gambling (I prefer "investment"!) unfortunately.

True! It's great for free poker, LOL :)

---

### Post by MontelEdwards on 2009-05-06
> **tmos22 said:**
> I am trying to play now on a b2b network, irisheyespoker.com but it is a bit dodgy, screen keeps flashing
Did you try the script i gave you to install IE?

---

### Post by sgosnell on 2009-05-06
If you have Wine installed, you should be able to just download and install the software, exactly as in Windows.  All poker sites I've seen require Windows or Mac, mostly Windows.  You can't play from your browser, you have to install their software.  Properly installed, Wine works fairly well, although not perfectly.  I mostly play on Pokerstars, and not all features work, although it is playable.  I would never play online for real money, because it's far too easy to cheat, and you can be assured the cheaters know all the ways to do it.  Collusion is by far the easiest, and given the wide array of instant messenger software available, there is no way to prevent it.  It's also easy enough to just get people together in the same room and play the same tables.  I've played multiple computers side-by-side, on the same tables, just to see if it was possible, and it is certainly possible.

---

### Post by tmos22 on 2009-05-06
It might be easy but i dont think its as common as you think, i make a nice bit of money every month playing tournaments and cash games online

---

### Post by xx58 on 2009-06-21
:confused: I install the PokerStars under Wine and everything works great, ONLY problem is I cannot play it on FULL SCREEN. Can anybody help, how do make full screen work?

---

### Post by rookcifer on 2009-06-21
> **tmos22 said:**
> Hey guys, to all the poker players out there, is there any site that i can play on with Ubuntu??

Pokerstars always worked well for me in WINE.

---

### Post by rookcifer on 2009-06-21
> **gtr32 said:**
> Most sites should work through web browser. Absolute Poker works in Linux but I'm not sure I would recommend them for real money play.

Yep, neither them or Ultimate Bet (their sister site) should be trusted for real money.  A couple of huge scams came out of both of those sites.

---

### Post by ibmorjamn on 2009-06-27
> **MontelEdwards said:**
> Some sites check what OS you are using, and sometimes they wont let you access it. I dont know why they do this.


You can install IE in linux with these commands.
```
sudo apt-get install cabextract wine 
```

then
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```




oh,
to run these go to applications >accessories>terminal
that will install IE
I know this is an old thread but I did this install and it seems to have worked I'm going to try it now.I do not run ubuntu yet (pclinux09) I tried to download and burn it but it never seems to work but thats another story for another thread. LOL

---

### Post by ibmorjamn on 2009-06-29
I have since successfully downloaded and burned the disc(9.04):guitar:. it works live but yet to install !

---

