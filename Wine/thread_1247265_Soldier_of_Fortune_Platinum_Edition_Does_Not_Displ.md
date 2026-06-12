---
title: "Soldier of Fortune Platinum Edition Does Not Display in Ubuntu In Wine"
date: 2009-08-22
forum: Wine
---

### Post by jonnhouston on 2009-08-22
I have Ubuntu 9.04 running on a Dell Laptop Latitude D600 with 20 gig harddrive and a half gig of RAM.  I installed Wine 1.0.1 and then installed Soldier of Fortune Platinum Edition under Wine.  After installation of SOF, I opened SOF with Wine, and it started and I can hear the sound from SOF, but the screen goes blank and I cannot see any graphics, images, or anything at all.  I suspect it has something to do with situation to a lower screen resolution but I have no idea how to open SOF in Linux under Wine and make sure it loads in a lower screen resolution.  

Can anyone help me with this?  Im a newcomer to Linux and Ubuntu and I really want to make the transition to a Linux environment.

Thank you, I look forward to hearing from someone regarding this.

---

### Post by bapoumba on 2009-08-23
Moved to Wine.

---

### Post by castlefox on 2009-08-24
Here is the App Database on the WINE page.  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=585](http://appdb.winehq.org/objectManager.php?sClass=version&iId=585)


What video card/intergraded card do you have?

You might need to try out the latest development release of WINE.  The development release of WINE is up to 1.1.28

---

### Post by TyLLy_4 on 2010-06-23
the game's default resolution is too high for your display. 

edit the file sof2mp.cfg inside your base/mp directory or sof2.cfg and find the lines where it says 
```
seta r_customwidth "1280"

seta r_customheight "800"
```
then change the values to whatever you want (i recomend 800 wide 600 long

If you need any more help you can PM me or email me at leo at techteamnow dot com. 

I'll be happy to assist a fellow penguin of fortune
(when you do get things running check out SC clan server my handle is +Looser+)

P.S. Also try to mess with 
```
seta r_fullscreen "0"
```

If the ressolution dont work.

---

### Post by jcer93705 on 2010-10-17
Guys i have no sound in ubuntu 10.10 with this game with latiest wine. Whats up with that?

---

### Post by TyLLy_4 on 2010-10-17
it could be a million things ... you need to give us some more information and maybe start a new thread too. 

Where did you get the installer from? 
can you hear other apps under wine? 
can you hear the main menu in the game? 
also provide system information

---

