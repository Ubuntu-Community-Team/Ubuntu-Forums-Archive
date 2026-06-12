---
title: "wine suddenly slow when starting apps, 100% cpu"
date: 2009-01-25
forum: Wine
---

### Post by scarf on 2009-01-25
i cannot think of what may have triggered this, but suddenly windows apps are taking a couple minutes to launch with wine.  they used to load very quickly, very normally.

i have the system monitor applet in the panel, and i notice that as soon as i launch an app with wine, the cpu spikes to 100%.  however, the color that is filling up the graph to 100% is dark blue, indicating "IOWait".  after a couple minutes waiting, the app launches, the IOWait goes away, and the cpu returns to normal.

it seems every app i try and launch has this behavior.

i have tried re-installing wine.

---

### Post by mb_webguy on 2009-01-25
Are you using the WineHQ repositories?  If so, then it could be a regression problem (which is when an upgrade actually causes a problem which didn't exist before).  Try installing an older version of Wine -- you can find debs on the WineHQ site -- and see if it helps.

---

### Post by scarf on 2009-01-25
thanks for your quick response.  i'm not exactly familiar with what you are talking about, but i think i know...

i do not think i am using the winehq repositories.  i have opened synaptic and looked in the "repositories" and i do not see any wine addresses, just ubuntu.com

the version of wine installed is: 1.0.1-0ubuntu2

i don't think it has ever been updated since i updated to ubuntu 8.10

---

### Post by mb_webguy on 2009-01-25
Ah, well, in that case, perhaps upgrading Wine will help.

Go to the [WineHQ website]("http://www.winehq.org/download/deb") and follow the instructions to add their repository to your sources.  Once you do that (and update your sources), the Update Manager should let you know that updates are available for Wine.

---

### Post by scarf on 2009-01-27
ok thanks, i appreciate that suggestion and will give a try soon.

but, it seems kind of strange to me that this behavior has started, and i would like to know what is causing it.  there haven't been any updates to wine that i can see.

also, i forgot to mention, after waiting a couple minutes for an app to load, the app performs normally; there's no more slow-down after that initial waiting period.

---

### Post by scarf on 2009-04-03
so i finally found out what was the problem, i had my ~/.fonts directory linked to an NFS share

---

### Post by mfox on 2009-04-19
I have exactly the same problem - very slow loading of a wine app, but then OK performance.  How did you figure out the problem and solve it?  Maybe it's the same problem I have.

---

### Post by scarf on 2009-05-02
> **mfox said:**
> I have exactly the same problem - very slow loading of a wine app, but then OK performance.  How did you figure out the problem and solve it?  Maybe it's the same problem I have.

in my case, i noticed a lot of network activity when starting an app.  after removing my ~/.fonts directory (which was just a link to an NFS share of fonts), everything went back to normal.

---

