---
title: "Guild Wars Trilogy Too Slow"
date: 2009-12-14
forum: Wine
---

### Post by Bwathke on 2009-12-14
OK, So Ive been playing PWI with NO lag problems and Rohan online etc. No problems with lag. Now I bought Guild Wars Trilogy (Got it for 15 dollars on a BIG sale!) I installed it and it works perfectly. The only problem is... It runs VERY slowly. I have it installed on a computer with a worse video card BUT with windows and it runs very nicely. On the computer with the issue I have Ubuntu 9.10 with WINE 1.1.33. My video card is a brand new Nvidia GeForce 6200... I dont see why I should be having problems with that card. Please tell me if you have any idea on whats wrong :)

---

### Post by beastrace91 on 2009-12-15
I feel its prob a limitation of your hardware/Wine under Linux. Wine runs most applications notably slower than they do natively under Windows. :-/

Try tanking the gfx settings/resolution in GW, odds are thats the best bet for better FPS.

~Jeff

---

### Post by Toffeeapple on 2009-12-15
Hi,

Have you been [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194") and read?

I get from 30 to 60 fps on the system in my sig, it slows down to 30 odd in the major cities but everywhere else its zips along quite happily

---

### Post by Bwathke on 2009-12-15
@ToffeeApple

Yes I have been there alot but thanks for the link :)

@beastrace91

I have dropped the graphics but I get no different result :/ I dropepd them to the worst and I got ALOT more lag then I did on medium settings. My thing is that all the other games run very smoothly with better graphics and Guild Wars wont Thanks for your help :)

---

### Post by WinterWeaver on 2009-12-15
Guildwars is one of those games that are not happy with Linux. The Developers went out of their way to use specific direcx technologies that are hard to implement.

Some people have a seemless experience, but I have not. I've tried GW (My favourite game btw) on many different types of hardware in different versions of linux, with different versions of wine, including PlayOnLinux. But it's never worked smoothly.

In the end I just opted to reboot to windows and play it there.

---

### Post by Bwathke on 2009-12-15
I tried a few things and now Im getting 9 frames a second >.< So Im new to Ubuntu how do I reboot to windows? I dont think Im going to fix this problem any time soon by the looks of it.

---

### Post by WinterWeaver on 2009-12-15
Before you give up, give PlayonLinux a go. It may solve the issue, you install the game via playonlinux and run it from there.

EDIT: Here is the link:
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Bwathke on 2009-12-15
I would but Im running out of space (Only 25 GB to start with) So if I install it again that will be about 4 GB more gone :/ Thanks for the offer though!

---

### Post by beastrace91 on 2009-12-15
> **WinterWeaver said:**
> Before you give up, give PlayonLinux a go. It may solve the issue, you install the game via playonlinux and run it from there.

EDIT: Here is the link:
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

POL uses Wine. If it lags in Wine its going to lag on POL.

~Jeff

---

### Post by beastrace91 on 2009-12-15
> **Toffeeapple said:**
> I get from 30 to 60 fps on the system in my sig, it slows down to 30 odd in the major cities but everywhere else its zips along quite happily

If you are playing on the 9800GTX listed in your sig that is why. That card is easily four or five times as powerful as the 6200 the OP is using.

Personally I run GW under Ubuntu just fine - but again I've got a beast of a graphics card to make up for the overheard Wine adds.

Regards,
~Jeff

---

### Post by Bwathke on 2009-12-15
So basically there is no hope unless I install and play it under windows? If so thats alright with me it just means it will take a little bit longer to play :)

---

### Post by Bwathke on 2009-12-15
New update!

I added two registry keys and Im getting 10-15 FPS (Playable) I added UseGLSL - disabled and Multisampling - enabled. I think I should be getting higher (On windows I would get 55+ someone said with my graphics card XD) but atleast it is playable :) Thanks for the help! If you have any ideas on just increasing the FPS I would love to hear them!

---

### Post by Toffeeapple on 2009-12-16
> **beastrace91 said:**
> If you are playing on the 9800GTX listed in your sig that is why. That card is easily four or five times as powerful as the 6200 the OP is using.

Yes it's a beast I tell you.. and it's mine all mine.... mwahahahahahahah.. etc, etc.

---

### Post by beastrace91 on 2009-12-16
> **Toffeeapple said:**
> Yes it's a beast I tell you.. and it's mine all mine.... mwahahahahahahah.. etc, etc.

Haha I bet, my 260m benchmarks the same as the 9800 desktop card. Little bugger hauls. :D

~Jeff

---

### Post by tnt533 on 2010-09-07
I'm playing on Ubuntu 10.04 AMD64 with a 2.8ghz dual core, 8 gig of RAM and a nVidia 8800gtx with 120+ pipes and 768 megs of texture mem and still get LOUSY fps unless I change the windows emulation in winecfg to windows7. Then it runs smooth and quick! But... no sound. I have been changing the emulation through the list and find that any selection that does not provide sound runs the game very well. Those that do make the sound work drag the FPS down and the graphics stutter every time I try to move in-game.

Pulseaudio issue? I wouldn't be surprised. Pulse is USELESS. <-- no need to start a pulse +/- rant here guys, we've heard it all before.

Anyone else experience this?

---

