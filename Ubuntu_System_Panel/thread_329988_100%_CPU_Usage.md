---
title: "100% CPU Usage"
date: 2007-01-02
forum: Ubuntu System Panel
---

### Post by Craga_89 on 2007-01-02
I don't know if this is just my computer or whether everyone else is experiencing it or not so...

Every time my gnome-panel starts up it has 100% CPU Usage **until** I press the System Panel button to bring up the menu. After that, it all goes back to usual system usage. Anyone else experiencing this? I've known about it for a long time now but I thought I better report it just incase =).

Thanks, Craig.

---

### Post by chanders on 2007-01-02
Thanks for the report Craig, but I haven't experienced that. There was a cpu problem with edgy (testing) but everything worked very well with Edgy final.

What flavor are you running?

---

### Post by Craga_89 on 2007-01-02
I'm using Ubuntu Edgy Eft Final. Well, it **was** testing but I upgraded all my packages when final came out a while back, could that be the problem? I'm running the newest version of USP, my /usr/bin/usp says "Ubuntu System Panel 0.40" in the header.

Hope this helps,
Craig.

---

### Post by daikrieg on 2007-01-16
That's true, I'm also using 6.10 final and got the same problem, but I don't remember having it when i was 6.06, so maybe it's edgy exclusive :-P

Anyway, USP rocks!

---

### Post by TheMono on 2007-01-30
I'm having a similar problem now as well. USP is now using 100% CPU all the time for me on Ubuntu 6.1 and USP 2 alpha... I'm overcoming this problem by simply not using it till I figure it out lol, but I'm keeping it updated via SVN hoping it will sort out.

Anyone have any ideas? The moment I put USP into a panel, CPU usage ramps up to 100% in a few seconds, and 'top' shows python using ~96% CPU.

---

### Post by deadlydeathcone on 2007-01-30
On the latest svn this happens only when I start usp with the terminal plugin minimized, and goes away once I unminimize it. Otherwise usp is awesome as usual. :)

---

### Post by Malac on 2007-01-30
> **deadlydeathcone said:**
> On the latest svn this happens only when I start usp with the terminal plugin minimized, and goes away once I unminimize it. Otherwise usp is awesome as usual. :)
There is a bug with the terminal plugin, which I confess has me a bit flummoxed, that causes high cpu usage if the terminal is not visible i.e. minimized or the menu is closed. 
The cpu usage returns to more normal levels once the plugin is visible. I have no idea why this should be at the moment I am looking into it. :)
However it does only effect the terminal plugin.

---

### Post by Malac on 2007-01-31
Okay I've fixed the terminal bug.
I've updated the Main tar file but here is the terminal plugin on its own.

The "terminal" one  is for the alpha test version 1.9x usp.
The "USPterm" one  is for those of you still using the 0.4x version.

If you guys could test them for me to confirm all is well.

---

### Post by TheMono on 2007-01-31
Don't have my laptop on me now, but this is what it'll be. Thanks for the fix.

---

### Post by delfick on 2007-01-31
new version seems to work fine for me :D

---

