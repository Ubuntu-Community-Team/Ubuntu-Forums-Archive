---
title: "Shaiya setup not working"
date: 2010-05-27
forum: Wine
---

### Post by Strevin on 2010-05-27
I have attached a screenshot with the problem. It opens fine and gives me the user agreement and I agree then this pops up and nothing happens. I have waited for over thirty minutes to see if anything happens, but it stays the same. In my wine C:\Drive I have the Ageia Tech folder. It may be working and I don't see. Please delivery me some advise.

---

### Post by asdfoo on 2010-05-28
retest with wine-1.2-rc1 or newer (release is due in 10~ hrs for rc2 I think)

---

### Post by allquixotic on 2010-05-28
Have you checked some of the user comments / troubleshooting steps (like installing the missing DLLs) at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10214) ?

---

### Post by hikaricore on 2010-05-28
No one ever bothers to read the stickies or check the appdb for that matter.
They're all like "oh i'm a noob i don't know that i'm supposed to read stickied threads that say _read me before posting_".

---

### Post by Strevin on 2010-05-28
I have read the stickies and I have downloaded the DLLs recommended on the Wine HQ all before posting this, but still does nothing. I have tried reinstalling wine and everything and I still get that screen

Hikaricore I agree with all the way people should look up the stickies and so forth, but I have and still nothing happens. Trust me the last thing I wanted to do was post this knowing a cure was  out there. Such as download the LOTR launcher and using it instead of what the .EXE offers. The thing is I can't find the launcher and I have tried over 10 pages of Google trying to read and understand what to do, but no one offers a simple walk through. I would just like if someone post the Terminal codes or links that show how to install this.

Edit: Sorry the LOTR thing is for DDO not Shaiya.

---

### Post by pr0t3g3 on 2010-05-31
> **hikaricore said:**
> No one ever bothers to read the stickies or check the appdb for that matter.
They're all like "oh i'm a noob i don't know that i'm supposed to read stickied threads that say _read me before posting_".
Holy crap man, chill.  At OP:  Your only option is to either play with it till it works or just ditch it.

---

### Post by asdfoo on 2010-05-31
post the output without native dlls, reinstalling wine does not remove the dlls you downloaded.

all your wine data is under ~/.wine

either move or remove it and retest please

---

### Post by Jace246 on 2010-07-22
i have tryed wine.. =( but i still give me an Error message.

Saying : The program updater .exe has encountered a serious problem and needs to close. 

This can be caused by a problem in the program or a deficiency in wine. You may to check **[Http://appdb.winehp.org](Http://appdb.winehp.org)** for tips about runing this application.

---

### Post by asdfoo on 2010-07-22
> **Jace246 said:**
> i have tryed wine.. =( but i still give me an Error message.

Saying : The program updater .exe has encountered a serious problem and needs to close. 

This can be caused by a problem in the program or a deficiency in wine. You may to check **[Http://appdb.winehp.org](Http://appdb.winehp.org)** for tips about runing this application.

did you try with wine-1.2?

---

### Post by vanquishedangel on 2010-09-01
I played shaiya for awhile on linux and it was working great. If i may make this recomendation, use PlayonLinux, just because it uses a seperarte configuration for each game installed and if you mess up, you can just delete that configuration and your wine install is fine. also it comes with a list of other games you might be interested in as well.

PlayonLinux is a great Frontend for wine and is an ex-stream time saver for me, plus it is great for noobs like me. I wouldn't suggest installing into your wine directly because of the many issues i have had with it, like installing dll,s that don't work with it etc. Also for shaiya you have to configure the wine libraries and make sure that you have all the correct working programs installed in it, like IE6. Thus the reason for using PlayonLinux and not messing with the libraries directly

---

### Post by Ubuntows Rocks on 2010-10-22
> **vanquishedangel said:**
> I played shaiya for awhile on linux and it was working great. If i may make this recomendation, use PlayonLinux, just because it uses a seperarte configuration for each game installed and if you mess up, you can just delete that configuration and your wine install is fine. also it comes with a list of other games you might be interested in as well.

PlayonLinux is a great Frontend for wine and is an ex-stream time saver for me, plus it is great for noobs like me. I wouldn't suggest installing into your wine directly because of the many issues i have had with it, like installing dll,s that don't work with it etc. Also for shaiya you have to configure the wine libraries and make sure that you have all the correct working programs installed in it, like IE6. Thus the reason for using PlayonLinux and not messing with the libraries directly

Well I've not tried that, but what I have done is installed Shaiya on my Laptop then moved the Shaiya folder from there to my Desktop here on ubuntu (you can anywhere I think), Then i had to find the .exe and change permissions so I could run it with wine and well that worked for me.

---

