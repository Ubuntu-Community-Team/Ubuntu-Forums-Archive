---
title: "Accessing Internet in WIne"
date: 2010-06-14
forum: Wine
---

### Post by anm112 on 2010-06-14
I recently downloaded the demo for the game Plants vs Zombies and it runs perfectly in Wine. When I purchased the game and entered the registration code it attempts to connect to the PopCap website, then fails to connect and register. I believe that this is because my Wine cannot connect to the internet. Does anyone know how to solve this problem?

My specs:
-Ubuntu 10.4
-Wine 1.1.44

---

### Post by asdfoo on 2010-06-14
> **anm112 said:**
> I recently downloaded the demo for the game Plants vs Zombies and it runs perfectly in Wine. When I purchased the game and entered the registration code it attempts to connect to the PopCap website, then fails to connect and register. I believe that this is because my Wine cannot connect to the internet. Does anyone know how to solve this problem?

My specs:
-Ubuntu 10.4
-Wine 1.1.44

Update to Wine 1.2-rc3 and try again.

If you want to test internet connectivity type: wine iexplore [http://winehq.org](http://winehq.org)

---

### Post by anm112 on 2010-06-14
I updated wine but it still doesn't work

---

### Post by cogadh on 2010-06-14
What happened when you ran "wine iexplore http://winehq.org"?

---

### Post by anm112 on 2010-06-14
When I ran "wine iexplore http://winehq.org" the wine website popped up in Internet Explorer. I guess that means my internet does work in wine. Plants vs Zombies still doesn't though.

---

### Post by Breambutt on 2010-06-14
I bought PvZ the day it was released and played it "through" in less than a week, so I can't really remember the details, but I believe the registration site had some stupid ActiveX elements and I probably installed [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") to finish the registration. Afterwards the registered product would run just fine.

Alternatively you could probably juggle your way around it if you have a spare Windows installation lying somewhere.

Edit: Uhh. Usually interweb works just fine under Wine, I didn't even know there's a built-in IE in every Wine these days. Might've been that I just used some kind of a registration form in Firesux to get my copy activated.

On an unrelated side note PvZ was kind of disappointing, short life span for the amount of hype it received. Gotta love Insaniquarium and Bookworm though, all PopCrap quality.

---

