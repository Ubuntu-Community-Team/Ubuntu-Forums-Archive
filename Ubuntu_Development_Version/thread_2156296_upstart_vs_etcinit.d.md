---
title: "upstart vs /etc/init.d/"
date: 2013-06-21
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-06-21
With a rolling system (lucid --> saucy), when i glance into /etc/init.d/, i'm seeing some oldish entries that seems no more used (as they are not updated since a while).
Looks like some cleaning is expected : its confirmed by the verbosy shutdown process, mostly saying that /init.d should not be used now as upstart is the new tool.

Wonder what a fresh installation is set now , and if a script exist to clean that list ?

---

### Post by grahammechanical on 2013-06-21
I have heard that upstart is being used more so as to reduce memory usage by only starting processes as they are needed and not all at OS loading time as is done with init.

In init.d (Raring) there are 85 scripts. In init.d (Saucy) there are 60 scripts. Both fresh installs.

I wonder if this is why I have so much difficulty loading into Saucy. It seems that just as the logon screen should be loading it goes to a black screen with a white flashing cursor. I have seen messages showing that lightdm has started and two messages about something starting for upstart and something stopping for upstart.

I also get a no signal message from the monitor about this time. Sometimes I can load saucy. Sometimes I cannot. Sometimes Recovery mode>Resume will get me in. Sometimes it will not work. Changing video drivers does not seem to make any difference.

Earlier, I got to a desktop through Root Shell>startx but it was a root desktop and the power/cog menu would not appear so I could not log  out and log in a myself.

Today Saucy has taken a vacation as far as I am concerned.

Regards.

---

### Post by dino99 on 2013-06-21
> **grahammechanical said:**
> 

In init.d (Raring) there are 85 scripts. In init.d (Saucy) there are 60 scripts. Both fresh installs.

I wonder if this is why I have so much difficulty loading into Saucy. 

Regards.

My Saucy (a rolling partition) have 103 scripts ;) and the older is from 2009 :mad:
but i'm scared to remove these oldish (<2012 for example). That Saucy is going better here while booting/restart process, since yesterday we got a fix for "pointers not destroyed on shutdown" (but does not remember the package name)
Anyway i feel some cleaning is needed inside that /etc/init.d. Might ask the devs opinions about it.

---

### Post by VMC on 2013-06-21
[QUOTE=grahammechanical]
...
I wonder if this is why I have so much difficulty loading into Saucy. It seems that just as the logon screen should be loading it goes to a black screen with a white flashing cursor. I have seen messages showing that lightdm has started and two messages about something starting for upstart and something stopping for upstart....
[/QUOTE]
I have the exact same black screen with white flashing cursor only on Kubuntu-saucy. It takes somewhere around 25-27 secs to boot and then when the black screen shows up, it takes another 20 secs before I'm presented with a desktop. No so with Ubuntu-saucy.

---

### Post by grahammechanical on 2013-06-21
I am back in saucy ubuntu right now through Resume but this morning I gave up after six or seven attempts. I then tried another saucy and it was the same situation. It has been like this for days. I think that either something is not loading fast enough or is loading too fast.

---

