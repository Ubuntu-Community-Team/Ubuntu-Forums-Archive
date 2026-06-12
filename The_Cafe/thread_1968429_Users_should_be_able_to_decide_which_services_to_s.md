---
title: "Users should be able to decide which services to start?"
date: 2012-04-29
forum: The Cafe
---

### Post by x-shaney-x on 2012-04-29
One particularly bad thing I have noticed through 12.04 testing and now on final release is the time it takes to go from login screen to fully loaded desktop.

At times I have wondered if the desktop is going to load at all or if something has gone wrong.

Well I cam across a post on Webupd8 which shows how to show hidden startup entries in "Startup Applications".

After disabling most of the items (which are not needed or wanted) the desktop now loads instantly.

Fair enough, ubuntu devs don't want users messing up their system but surely some of those things are very specific to certain users and aren't needed by everyone?

Things like screen reader, bluetooth and restricted drivers are useful to many people but certainly not all so why shouldn't users be able to disable these?

I don't use ubuntu one, gwibber or desktop sharing but again, I have to have those running otherwise.

---

### Post by Paqman on 2012-04-29
> **x-shaney-x said:**
> 
After disabling most of the items (which are not needed or wanted) the desktop now loads instantly.

> 
why shouldn't users be able to disable these?


Sounds like they are. They're probably not settings that should be exposed to anyone, but it sounds like anyone with a bit of Google-fu and a DIY mindset should have no trouble.

The relative ease of accessing stuff "under the hood" is one of the most appealing reasons to use Linux IMO.

---

### Post by Copper Bezel on 2012-04-29
I do think it's more awkward than it needs to be. I particularly don't understand why all of those need to be system-wide instead of just being handled in Startup Applications. I don't have U1 installed, and I don't see any processes running for Gwibber et al., but I did need to remove nm-applet's autostart, since I use Shell and Shell doesn't use nm-applet. (Or, at least, letting it run from autostart mucks up the network notifications, and not letting it run doesn't.)

I thank y'all for the prompt to check System Monitor, by the way. I forgot I had a Wine app running and nearly broke my brain when I saw explorer.exe in the process list.

---

### Post by x-shaney-x on 2012-04-29
Yea but it took me a while to find that info and things like screen reader are hardly going to damage the system if disabled so not all should be hidden at all.

What would be so wrong with an "Advanced" button?

---

### Post by mips on 2012-04-29
> **x-shaney-x said:**
> 
What would be so wrong with an "Advanced" button?

/waits for someone to say you are sounding like [Linus]("http://www.desktoplinux.com/news/NS8745257437.html") :biggrin:

---

### Post by x-shaney-x on 2012-04-29
Hehe.  Yea I see your point but this is more about taking back control of your system.

Looking back I think the vast majority of users wouldn't want to bother altering services or wouldn't even think about it.

If it wasn't for the desktop taking so long to load (which it didn't in 11.10) I wouldn't have bothered about it myself.

Maybe something that should be added to one of the "tweaking" applications then?

---

### Post by cariboo on 2012-04-29
To populate startup applications (gnome-session-properties) isn't all that hard, it's just a matter of running two commands:

```
cd /etc/xdg/autostart/
```

and then:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

the result should look like the screenshot.

---

### Post by x-shaney-x on 2012-04-29
Yes and that is how I did it but it's not exactly obvious.

---

### Post by forrestcupp on 2012-04-29
If you're going to tease us with the ability to show hidden services, you should either give us a link or show us how.

> **x-shaney-x said:**
> 
If it wasn't for the desktop taking so long to load (which it didn't in 11.10) I wouldn't have bothered about it myself.
I noticed that it took just as long in 11.10 as it does for me in 12.04. I noticed it before I upgraded.

---

### Post by philinux on 2012-04-29
> **forrestcupp said:**
> If you're going to tease us with the ability to show hidden services, you should either give us a link or show us how 

Post #7 has the info. I agree it's not ideal.

---

### Post by Papi47 on 2012-04-29
x-shaney-x Thank you for reminding me to do that.  I have always unticked things I didn't need to start.

---

### Post by x-shaney-x on 2012-04-30
Disregarding whether users should be able to tweak some of the startup items, certain ones shouldn't be hidden at all and should be displayed all the time.
Chat and gwibber in particular.

---

### Post by philinux on 2012-04-30
> **x-shaney-x said:**
> Disregarding whether users should be able to tweak some of the startup items, certain ones shouldn't be hidden at all and should be displayed all the time.
Chat and gwibber in particular.

And bluetooth, desktop sharing and orca.

---

### Post by Copper Bezel on 2012-04-30
Some of those are only launched if they're set to, though. The startup application entry runs the service, but the service exits if it's disabled within its own settings manager. So you're running a couple of quick (superfluous) checks at startup, but it's not as if the services are running.

---

### Post by Lucradia on 2012-04-30
> **cariboo907 said:**
> To populate startup applications (gnome-session-properties) isn't all that hard, it's just a matter of running two commands:

```
cd /etc/xdg/autostart/
```

and then:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

the result should look like the screenshot.


I think the OP also wants **Services**, which can only be turned off in console, via programs like **sudo sysvconfig &** and **bum** (GUI).

(anacron, acpi, etc. to name a few.) There is another service that can also change the run level at which they start at, rather than disabling them entirely (this specific application I'm talking about only has a command-line version.)

---

### Post by x-shaney-x on 2012-05-01
> **Lucradia said:**
> I think the OP also wants **Services**, which can only be turned off in console, via programs like **sudo sysvconfig &** and **bum** (GUI).

(anacron, acpi, etc. to name a few.) There is another service that can also change the run level at which they start at, rather than disabling them entirely (this specific application I'm talking about only has a command-line version.)

No, I was just talking about the startup applications stuff.
I have messed around with system startup services in the past but I don't tend to bother now.

In fact these days, I want to do as little fiddling with things as possible and I try to stick to defaults as much as I can (for various reasons, blame KDE).
I wouldn't have wanted to fiddle with the startup applications but 8-10 seconds for the desktop to load fully seemed excessive, especially when it is less than 2 seconds now.

---

### Post by Lucradia on 2012-05-01
> **x-shaney-x said:**
> No, I was just talking about the startup applications stuff.
I have messed around with system startup services in the past but I don't tend to bother now.

In fact these days, I want to do as little fiddling with things as possible and I try to stick to defaults as much as I can (for various reasons, blame KDE).
I wouldn't have wanted to fiddle with the startup applications but 8-10 seconds for the desktop to load fully seemed excessive, especially when it is less than 2 seconds now.

Whenever I try KDE, I *must* change the default settings. Often times, this makes it almost impossible for a KDE norm. to actually bear with my KDE set-up due to how many changes I have to make for it to work with me. That's why I stick with XFCE / GNOME 2 / LXDE or better yet, no DE at all via OpenBox and startx.

I could never understand how someone who wants ease-of-use and functionality could actually bear the defaults of KDE.

---

### Post by x-shaney-x on 2012-05-01
That's my problem with KDE.  I think it is absolutely great but I tend to configure every part of it because it is so easy to.
I tend to spend more time getting it perfect than I do actually working on it.
Main reason I switched to unity.

---

