---
title: "Nook Application worked flawlessly"
date: 2011-03-03
forum: Wine
---

### Post by kelvinator on 2011-03-03
I did a bit of searching here and no one seems to have posted this.

The Barnes and Noble Nook Windows Desktop application works flawlessly in WINE.

---

### Post by cogadh on 2011-03-04
Tell people about it here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10502](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10502)

---

### Post by pabloikba on 2011-03-16
I just downloaded the Nook application from B&N....

I am running Ubuntu 10.10 w/Wine 1.3.15. It installed perfectly and, before running, I set the Wine Config to Win7. It runs exactly as it should (and does on PC&#347;). I entered my email and B&N password and it sync´d with my account. The books are there and they open and can be ready easily. Also, I added two books to My Stuff and they also are able to be ready. I don´t see any difference between this and running it on PC with WinXP or Win7.

Pablo

---

### Post by Rasa1111 on 2011-03-16
I heard on nookboards that it works also.
I dont use it though.
Calibre is plenty for my needs. 

but nook is amazing. lol

---

### Post by jervin2 on 2011-11-15
Nook stopped working for me under Wine 1.3.30 on Ubuntu 11.10.  Used to work under 11.04.  I get the following message:

[INDENT]We are sorry, but this Barnes and Noble application
has encountered a problem and it needs to close
(code 001).

Would you like to restart the application not?[/INDENT]

---

### Post by topher23 on 2011-12-01
Same issue as Jervin - Nook for PC throws error 001 and force closes on startup under 11.10. Bummer.

---

### Post by uhhhh2 on 2011-12-01
Here is how to troubleshoot the code 001 errors: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818&iTestingId=67721](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818&iTestingId=67721)

---

### Post by Johnny Buffalkill on 2011-12-01
[http://ubuntuforums.org/showthread.php?t=1862842&page=2](http://ubuntuforums.org/showthread.php?t=1862842&page=2)

This thread was for kindle software, but I tried the solution (deleting the contents of the Manifest folder described at the end of the link) and it seems to work for Nook too.  I haven't checked it out too closely to make sure there aren't any less conspicuous problems, but so far so good.

I have no idea if doing this will goof up any other wine programs you have installed.  I only had one other wine program installed and it wasn't quite working right, so there wasn't much risk in my case.  It might be a good idea to back them up before deleting them.

---

### Post by topher23 on 2011-12-02
Good fix - both the link and the description are the same fix - delete the contents of the windows/winsxs/manifest folder (the deadbeef files) and Nook for PC works again. Thanks a million!

---

### Post by ussndmac on 2011-12-02
> **Rasa1111 said:**
> I heard on nookboards that it works also.
I dont use it though.
Calibre is plenty for my needs. 

but nook is amazing. lol

I actually find Calibre better than the Nook app...and I don't need wine to run it. :D

---

