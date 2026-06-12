---
title: "Cannot install Office'03 nor Photoshop CS4"
date: 2009-05-26
forum: Wine
---

### Post by Lockheed on 2009-05-26
I installed ubuntu 9.04 and upgraded wine to 1.1.22. 
When I try to install MS Office 2003 I get past settings menu and get to the window with "Preparing to install..." message but the progress bar never moves and then after 30 seconds I get this message:
```
The program msiexec.exe had encountered a serious problem and needs to close. We are sorry blah, blah.
```

With Photoshop (and Dreamweaver) the message is exactly the same except it appears right efter I click setup.exe.

Can someone have any idea how to solve this? I really need those.

---

### Post by asdfoo on 2009-05-26
They're regressions, used to work a few Wine versions ago but fixes have gone in for other programs which broke these.  Either downgrade or wait for them to be fixed in a future release.

---

### Post by Lockheed on 2009-05-26
How do I downgrade? Do I remove Wine in Synaptic and then download older DEB? Will it not break my recently installed Wine apps?

---

### Post by asdfoo on 2009-05-26
> **Lockheed said:**
> How do I downgrade? Do I remove Wine in Synaptic and then download older DEB? Will it not break my recently installed Wine apps?

Yes and maybe, but probably not.

All your data is kept in your home directory under .wine, whichever Wine version you install will access the files there, it should work without issue.

---

### Post by alex.rayu on 2009-05-27
A serious program. A serious problem. :D What did you expect?

You get an older deb you might install it and then upgrade to a newer deb to have newly added fixes work. Who knows - what if it works for you.

---

### Post by Lockheed on 2009-05-28
I tried 1.1.18 for 9.04 and 1.1.17 for 8.10 but  the only change is that now instead of error message, installation window just disappears.

Does it mean there is no way to run those programs in linux except VM?

---

### Post by alex.rayu on 2009-05-29
So far, WINE does not work with them. VM or Windows on another boot partition is the only option.

---

### Post by Lockheed on 2009-05-29
How about Office 2003? I would supposed it should work.

---

### Post by Meow27 on 2009-05-29
here is what i did

i got playonlinux

from there i donwloaded wine 1.1.16 and the latest. i used the MS office 2003 script for 1.1.16

and it works. i run it natively now with 1.1.22

---

### Post by Lockheed on 2009-05-29
Where did you get Office 2003 script? I tried installing it with Playonlinux and everything went just the same except POL thinks it is installed and created some nonworking shortcuts.

---

### Post by lmellor on 2009-11-22
I have recently made a script that should at least help you a little bit along your travels...

[http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html]("http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html")

I hope it fares you well.

---

### Post by Lockheed on 2009-11-25
I managed to run Office 2003 without any scripts but Photoshop CS4 is stilla no go.

For your script to work, do I need to have playonlinux?

---

### Post by Lockheed on 2009-12-12
> **lmellor said:**
> I have recently made a script that should at least help you a little bit along your travels...

[http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html]("http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html")

I hope it fares you well.


I tried running it but instsantly I get this error:
```
~/Desktop$ ./ps4.sh
bash: ./ps4.sh: /bin/bash^M: bad interpreter: No such file or directory

```

---

### Post by lmellor on 2010-05-07
sorry for my delayed reply, yes the script is for playonlinux which I find to be one of the most valuable tools available to wine.

---

