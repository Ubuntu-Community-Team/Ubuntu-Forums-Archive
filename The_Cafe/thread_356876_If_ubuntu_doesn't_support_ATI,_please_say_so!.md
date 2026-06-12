---
title: "If ubuntu doesn't support ATI, please say so!"
date: 2007-02-08
forum: The Cafe
---

### Post by orthorim on 2007-02-08
Hi, I tried ubuntu 6.10 on my laptop and I was impressed - I would love to run this full time. I would much rather switch to that than to Vista, which I also tried and which has left me rather disillusioned.

There's a snatch though: I have an ATI card, and I had to learn the hard way that ATI cards just don't work on Ubuntu. I had two particular problems: My display resolution was not recognized so ubuntu ran in 1400x1000 on my 1680x1050 display, making everything look.. well... fat.

Then the graphics were extremely slow which means it wasn't hardware accelerated. 

I am sorry but that's not acceptable. 

It would be acceptable if there was an ATI driver that I could download from the ATI website and double click to install. But reading long discussions about "woohoo, who got the ATI drivers to work on their system?" does not fill me with confidence here. It sounds more like "crazy time sink with uncertain outcome" to me, which in my case means I am not interested.

I don't want to whine - I understand the reasons proper ATI drivers are not included in ubuntu. But I want to request that the install CD recognizes the ATI card and presents me with a warning that says "We do not officially support ATI cards. If you want to try it on your own be our guest and here's the relevant forum instructions."

This is probably not the forum to argue that ubuntu should, for their user's sake, include evil proprietary binary drivers from ATI/NVidia, provided these companies give unrestricted distribution rights. So I am going to rest my case here.

Final word: If hardware is ill supported, please let me know before I waste x amount of hours on this. It just makes me not like ubuntu. 

I know better than to buy an ATI laptop or any ATI card next time around - but until then no ubuntu for me :(

---

### Post by meng on 2007-02-08
I got my ATI laptop card working, did you look here?
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by cowlip on 2007-02-08
I believe there's a bug on Launchpad which causes widescreens to be unrecognized (fixed in Fedora Core but not Ubuntu)...

And no, ATI cards aren't really supported.  MOst of them work with the reverse-engineered driver, but the most recent ones don't yet.

---

### Post by -Ghost9- on 2007-02-08
It took me 3 days to find directions that got mine to work, but I finally got it working!!

I have an ati x850xt and it appears to be running 3d apps ok.

these are the instructions that got me working:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

It's not as easy as download and double click, but it worked for me!

---

### Post by Henry Rayker on 2007-02-08
Unreasonable expectations.

I don't think there is a single justifiable reason why they should waste space on the disk for a database of working and non-working hardware just to keep lazy users from having to actually do a little research before they try installing the OS.

---

### Post by orthorim on 2007-02-09
> **Henry Rayker said:**
> Unreasonable expectations.

I don't think there is a single justifiable reason why they should waste space on the disk for a database of working and non-working hardware just to keep lazy users from having to actually do a little research before they try installing the OS.

I am sorry, but that's a retarded statement. I am hoping you are not working for ubuntu. If you were, maybe you should read the tagline - "linux for human beings". 

As for the "waste of time" statement - that's particularly silly. As if there were thousands upon thousands of different graphics cards and ATI was merely one of them and it would be a huge amount of work to treat them all equally and add detectors. Newsflash: 99% of laptops have integrated graphics, NVidia, or ATI. 60% of all new machines sold are laptops. How hard it is to add a detector for these three - in fact, make that ONE because NVidia and integrated seem to work OK, judging by the forum.

---

### Post by orthorim on 2007-02-09
> **cowlip said:**
> I believe there's a bug on Launchpad which causes widescreens to be unrecognized (fixed in Fedora Core but not Ubuntu)...

And no, ATI cards aren't really supported.  MOst of them work with the reverse-engineered driver, but the most recent ones don't yet.

Thanks for that, I wish I had known that before. 

Don't get me wrong, I know how bad these ATI drivers are. I hate them even under Windows. Hoping that this will improve now that AMD owns ATI.

---

### Post by orthorim on 2007-02-09
> **meng said:**
> I got my ATI laptop card working, did you look here?
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Thanks for that, I did see these - rather scary, I must say - instructions. I would give them a shot but only if I hear from someone who has gotten them to work 100% with an ATI X1600 (mobility) card, which is the one in my laptop. If I am reasonably confident that all this fiddling will result in stable and accelerated graphics, I might try it, but not before.

---

### Post by Choad on 2007-02-09
in fairness, windows xp would be even worse at handling your somewhat exotic display adapter.

in an ideal world, everythign would work all of the time. ask yourself this: do we live in an ideal world?

im fairly confident that if you asked the right question in the right place then you would get all the help you need to set it up tho.

---

### Post by joplass on 2007-02-09
i could well be over my head here but my gateway 450sx with ati has worked since the first ubuntu up to now.
again maybe i am missing the point the thread creator is trying to make.

---

### Post by machoo02 on 2007-02-09
Not to steer you away from Ubuntu, but there are other distrobutions that do include the drivers from ATi off the bat, and have them set up OOTB.  For example, try one of the Sabayon live CDs.  It asks you if you want to use the proprietary drivers, sets them up, and restarts X.  And this is on a live CD, so no install necessary.

---

### Post by orthorim on 2007-02-09
> **Choad said:**
> in fairness, windows xp would be even worse at handling your somewhat exotic display adapter.

in an ideal world, everythign would work all of the time. ask yourself this: do we live in an ideal world?

im fairly confident that if you asked the right question in the right place then you would get all the help you need to set it up tho.

I am not sure what you mean with the XP statement - yes, Windows XP worked right off the bat with this card. So did Vista. I don't think it's really that exotic. Most higher end notebooks have had this card for a while now, and it's now starting to trickle down into the lower end part of the spectrum as well. 

Anyway - the point I was trying to make was that the linux for the rest of us, fond of sharing etc, would be well advised to tell me, the user, that his card isn't supported. 

And there were mixed responses, which I find quite interesting. I am absolutely not accepting any statements along the line "well it's free so it's crappy" or "well, RTFM brother" or anything like that. That's soooo 1990ies. I think Linux is better than that.

Re: Sabayon CD - I am definitely going to try that, thanks so much for the tip! Don't worry I am also going to try the next version of ubuntu...

---

### Post by ghandi69_ on 2007-02-09
I definitely agree with you man, users should definitely be warned about the ATI graphics issue... 

My question to you is, where do you think is the best place to provide this information?  

I was thinking maybe a readme file that would display before startup, but we all know how well people read those.

The other thing. with linux (and as with windows, to a lesser extend) there are a lot of things that don't work right away upon install, and you would have to distinguish about what things are important for users to know and what things are not.  

The cool thing about ubuntu and linux as opposed to windows though.. is that in windows.. if something doesn't work.. thats usually about it.. it doesn't work... and theres not much else you can do about it.

In linux however... less things work right away... but its possible to get EVERYTHING to work how you want it with some work.

---

### Post by patrickfromspain on 2007-02-09
probably someone has said it already:

**IT'S NOT UBUNTU NOT SUPPORTING ATI, BUT ATI NO SUPPORTING LINUX**

---

### Post by ghandi69_ on 2007-02-09
True... but at time of use, it matters not..

So really... when so & so buys a videocard from ATI.. it should have a warning somewhere that states they do not support linux..

A warning at both places (from ati and from ubuntu) couldn't hurt though, cuz at somepoint.. it matters not whos not supporting who... but just that it doesn't work.

---

### Post by lzfy on 2007-02-09
It is really not that hard as it looks like. I have a laptop with an ATI x700. The most important thing to do after a clean install is to update the system. After that follow this tutorial
[Link]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_Driver_Manually")

After that you have 3d support and you can even install Beryl in 5 minutes.

---

### Post by macogw on 2007-02-09
> **orthorim said:**
> Thanks for that, I wish I had known that before. 

Don't get me wrong, I know how bad these ATI drivers are. I hate them even under Windows. Hoping that this will improve now that AMD owns ATI.

AMD likes Linux, right?  Maybe they'll do better than the ATi guys, and not make everyone wait 6 months for drivers after a card's released.  I'm sticking with Intel though.  The graphics work OOTB, no binaries-that-can-break, AIGLX works fine...nVidia can still have the problem of binaries that break the X server.  That's why I wasn't part of the August problems.

---

