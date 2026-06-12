---
title: "How would Fallout 3 (Steam or Retail) work in Wine on my system?"
date: 2009-09-13
forum: Wine
---

### Post by Leopardson on 2009-09-13
I had planned to get Fallout 3 soon, but the Windows I had planned to use is no longer available and I am left with Ubuntu.
WineHQ isn't very helpful with either version of Fallout 3 (No entry at all for Steam).

Note: I plan to upgrade my computer and somehow get my hands on some cheap copy of Windows  XP. The only risk is I may have to wait to play it, which I would have to do anyway.

System:
Ubuntu 9.04 Jaunty w/ Wine 1.1.29

Video: ATI Radeon HD 3650 (1GB DDR2)
Drivers: ATi Catalyst 9.8, tested, working.

Memory: 2GB DDR 400 (Tested)

CPU: AMD Athlon 3100+ 
Slow, I know, but it should do.

Sound: RealTec Audio, built in. Works fine.


I am willing to get retail if need be, but my ideal choice is Steam as a 2 ounce DVD is easier to loose then a Steam account locked up like a Detroit-based Bank Safe on a Holiday at 3:00AM.


 Any bugs or things I should know about with  Any bugs or things I should know about with Fallout 3?

Edit: Priority is no longer too high as I will soon have access to a possibly-working (Has viruses, but I'm really, really good at killing viruses. Windows/Linux 6-year dual-booter here.) Windows XP drive. 
Also, I have Windows 7 RC on a random DVD which, if worse comes to OMFGPLEASEKILLME I can load onto a random spare drive and nab a key before October 21st.
I would still love to use it in Linux and intend to play it through should it work and submit the results to winehq.
                                                            [URL="javascript: leoHighlightsIFrameClose();"]                    
       [/URL]

---

### Post by beastrace91 on 2009-09-14
Just so you know running a game through Steam will have little to no effect on how the application runs under Wine. Steam is basically just a front end for the game and when you click the icon in the Steam menu it is just like manually running the exe file.

I know many people have been very successful running Fallout 3 under Wine using a custom compiled version of Wine with a small patch. (more info on that [here](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)) The only thing I would not be too sure of is how well the ATI drivers will allow Wine to handle the game. ATI drivers are very poor to put it kindly. If you are going to buy the game anyways, just give it a try - what do you have to lose?

~Jeff

---

### Post by Leopardson on 2009-09-14
>  - what do you have to lose?

 8 gigs of space? :P

I'll test it in wine first thing when I get it.

---

### Post by hetx on 2009-09-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

Just Gold but seems like it works with just a little bit of tweaking.

---

### Post by beastrace91 on 2009-09-14
> **Leopardson said:**
> 8 gigs of space? :P

Just remove it if you find it not working ;)

~Jeff

---

### Post by Leopardson on 2009-09-14
Thanks, HetX. I'll be sure to add that to the .INI should the game not start.
I'm grabbing the game tomorrow.

---

### Post by beastrace91 on 2009-09-14
> **Leopardson said:**
> Thanks, HetX. I'll be sure to add that to the .INI should the game not start.

I linked to the same page, just as a heads up for any future Games/Windoze apps you might try to run always be sure to give the Wine appdb a once over as it contains lots of useful information.

~Jeff

---

### Post by Duskao on 2009-09-14
It should work fine, just with your slow processor and medeocre vid card you will probably have to run it on low. The newer catalyst drivers are coming along amazingly, it's like night and day from when I started with Ubuntu 8 months ago. 

The newest drivers are catalyst 9.9, just to let you know. 

If you use POL there is a script in the repositories for FO3 and it works very well with little to no fuss. 

Good luck

---

### Post by del_diablo on 2009-09-15
You got enough RAM to at the least run it with full texture resolution. That is fact.

---

### Post by hetx on 2009-09-15
Right, Duskao makes a good point here. To make your life easier you can install Play On Linux (POL) and use it to install Fallout 3. It will handle all "fixes", it should just work.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

