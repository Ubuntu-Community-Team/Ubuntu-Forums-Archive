---
title: "MirrorMAX stability update"
date: 2005-06-29
forum: Ubuntu Backports
---

### Post by ShaneAu on 2005-06-29
Sorry about the stablity of MirrorMAX latley, been having some issues with the main server, which hopefully will be solved soon enough. :). (It's not the ubuntu-backports mirror causing it).

So if you get any connection refused or timed out errors, just post in this thread about it.

---

### Post by stamy on 2005-07-16
I have a connection refused right now, can you take a look ?

Id like to install some multimedia stuff on my fresh Hoary installation.

Thank's a lot.

---

### Post by Kyral on 2005-07-16
Connection refused. Is there another Backports mirror I can use? I really need to install the x264 codec :D

---

### Post by Jvaldezjr on 2005-07-16
```
 Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204). - connect (111 Connection refused)
```

was gonna play with fluxbox today...guess not.

---

### Post by stevetorrefranca on 2005-07-16
[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) 

connection refuse right now

---

### Post by Darrena on 2005-07-16
There are other mirrors, for example:
[http://www.ubuntuforums.org/showthread.php?t=46459](http://www.ubuntuforums.org/showthread.php?t=46459)

---

### Post by stamy on 2005-07-16
Thank's a lot !

---

### Post by benplaut on 2005-07-16
ahh,,, that explains...

thanks for the heads up :)

---

### Post by stamy on 2005-07-16
Not all is present on this mirror, i miss for example:

xmms-mp4
lame
xvid4conf ...

So i cannot play mp3 right now with xmms, have ayou a another location for theses packages ?

Thx.

I have found another location for some packages (deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib), but my problem was that the name of my mp3 file was wrong encoded (not UTF-8 or so),

After renaming it, i can play it under xmms ! Great.

---

### Post by Darrena on 2005-07-16
[QUOTE=stamy]Not all is present on this mirror, i miss for example:

xmms-mp4
lame
xvid4conf ...

So i cannot play mp3 right now with xmms, have ayou a another location for theses packages ?

Thx.

I have found another location for some packages (deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib), but my problem was that the name of my mp3 file was wrong encoded (not UTF-8 or so),

After renaming it, i can play it under xmms ! Great.[/QUOTE]

I think those packages are in the universe/multiverse repositories, not backports

---

### Post by spartas on 2005-07-16
I'm getting a bunch of connection refused errors, but it's really not that big of a deal for me yet.  I'm just addicted to updating my system.  No new packages in the other repos, and with backports down I'll just have to wait a little while before updating again.

---

### Post by ShaneAu on 2005-07-17
Ok, thanks for telling me. :). I will be switching the load back to the fast server (which was having a rest because it was eating up it's bandwidth too fast) and take the other server offline (current one taking all the load) and get it upgraded. :). Once it's upgraded I will put all the load back onto it because the main server ("fast one") needs to have a break from serving backports.

This is going to cost me an additional $139, so if you're feeling generous, help me out and donate at [http://mirrormax.net/](http://mirrormax.net/) even if it's < $5 or something. :).

Donations or not, I'll still *try* to provide the best backports mirror :D.

---

### Post by stevetorrefranca on 2005-07-17
its alive! its alive! ... 

backports its back online and kicking again!

---

### Post by ShaneAu on 2005-07-18
Ok, well the high bandwidth server wasn't upgraded, but it did have something done. I've moved all the load back to it. I'm not sure how apache will hold up on it, but if it stays up until I check it tomorrow - good I will probably not have to worry much. :p.

I can't afford the upgrade of RAM just yet, maybe another time. :)

Please report any problems you may have with the MirrorMAX mirror here still.

---

