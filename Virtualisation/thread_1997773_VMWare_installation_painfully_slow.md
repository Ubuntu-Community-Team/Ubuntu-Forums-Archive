---
title: "VMWare installation painfully slow?"
date: 2012-06-05
forum: Virtualisation
---

### Post by Andrewmham on 2012-06-05
Does anyone have experience running 12.04 through VMWare Workstation (player)? 

I just completed a fresh install (I also have it running dual boot on my laptop, but at my desk I would prefer to have Ubuntu available, so it's on a 22inch monitor adjacent to my Win7 laptop. 

Currently going through the motions and getting updates installed, but it has some terrible lag time...i.e. it takes a second or two for each click to register, feels almost like I'm supporting someone through logmein/teamviewer/gotomeeting etc.

Any thoughts on how I might speed this up? It's hitting my CPU pretty well, but not pegging the machine out that much...

---

### Post by LHammonds on 2012-06-05
> **Andrewmham said:**
> it takes a second or two for each clickAre you talking about a 12.04 Desktop or 12.04 Server or 12.04 Server with a GUI?

I use Ubuntu Server (without a gui) on ESXi servers...however, I connect to it through PuTTY via SSH.  I see no degradation but again, I do not use a GUI.

LHammonds

---

### Post by Andrewmham on 2012-06-05
12.04 desktop for the moment

---

### Post by stmiller on 2012-06-05
Maybe try this?

```
sudo apt-get install xserver-xorg-video-vmware
```

---

### Post by LHammonds on 2012-06-06
> **Andrewmham said:**
> 12.04 desktop for the moment
Ah, I see.  I was confused because it sounded like a desktop thing but you posted in the "Server Platform" sub-forum.

robably should have a moderator move it to [URL="http://ubuntuforums.org/forumdisplay.php?f=329"]Desktop Environments.
[/URL] (EDIT: I asked for you)

---

### Post by nothingspecial on 2012-06-06
*Thread moved to **Virtualization**.*

---

### Post by Andrewmham on 2012-06-06
My bad, in my head "server" didn't register as the type of Ubuntu installation...thanks!

Tried this command out, and it's already running the latest version...I'm wondering if it isn't just too much for the laptop to handle, I wouldn't be surprised. It did speed up a bit after the initial round of updates, but not even close to what my experience is like when I run the actual OS install; probably just going to have to live with it! Something is better than nothing I suppose :-({|=

---

### Post by kennethconn on 2012-06-06
How much memory your laptop have? How much have you given to this VM instance?

---

### Post by dcstar on 2012-06-06
> **Andrewmham said:**
> Does anyone have experience running 12.04 through VMWare Workstation (player)? 

I just completed a fresh install (I also have it running dual boot on my laptop, but at my desk I would prefer to have Ubuntu available, so it's on a 22inch monitor adjacent to my Win7 laptop. 

Currently going through the motions and getting updates installed, but it has some terrible lag time...i.e. it takes a second or two for each click to register, feels almost like I'm supporting someone through logmein/teamviewer/gotomeeting etc.

Any thoughts on how I might speed this up? It's hitting my CPU pretty well, but not pegging the machine out that much...

[LIST=1]
[*]Change the VM settings to only use 1 CPU
[*]Install VMware tools in the VM
[/LIST]

---

### Post by Andrewmham on 2012-06-07
> **kennethconn said:**
> How much memory your laptop have? How much have you given to this VM instance?

Well I feel stupid. I actually fixed this yesterday, was just coming back to update...that's exactly what it was. Bumped it from 1GB to 2GB, and it flies now. I normally don't worry about that since what I run in VMWare doesn't usually require much.

Thanks for all the help!

---

