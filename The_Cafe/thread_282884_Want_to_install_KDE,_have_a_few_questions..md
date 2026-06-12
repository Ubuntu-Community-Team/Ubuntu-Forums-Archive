---
title: "Want to install KDE, have a few questions."
date: 2006-10-23
forum: The Cafe
---

### Post by RussianVodka on 2006-10-23
I tried Kubuntu Live CD the other day, and it rocks out loud. I've always been a fan of KDE, and used it when I had the chance, I just use Gnome now because, well, it came pre-installed, and I got used to it.

I've tried installing KDE in Ubuntu before, but the major problem was that it seemed kind of unwieldy (in comparison to a fresh OS install, I don't know why), and when I switched back to Gnome, I wasn't able to use my programs (it said something about that paths being changed.

But I've tried Kubuntu, and now I want KDE again. How could I go about installing it without damaging Gnome?

---

### Post by plb on 2006-10-23
apt-get install kubuntu-desktop I'd imagine.

---

### Post by maniacmusician on 2006-10-23
i'd recommend sudo **aptitude** install kubuntu-desktop instead.

or, if you want the real KDE desktop, without all the changes kubuntu has made to it, you would do:

sudo aptitude install kde

there's also other install options such as kde-core, which only installs the most basic things, and other options as well that don't come to mind right now. 

have fun!

---

### Post by RussianVodka on 2006-10-23
> **maniacmusician said:**
> i'd recommend sudo **aptitude** install kubuntu-desktop instead.

or, if you want the real KDE desktop, without all the changes kubuntu has made to it, you would do:

sudo aptitude install kde

there's also other install options such as kde-core, which only installs the most basic things, and other options as well that don't come to mind right now. 

have fun!
What's the difference between apt-get and aptitude?

---

### Post by mips on 2006-10-23
> **plb said:**
> apt-get install kubuntu-desktop I'd imagine.

Do NOT use apt-get to install Kubuntu desktop !!!

Rather do this, **[COLOR="Blue"]http://www.psychocats.net/ubuntu/kde[/COLOR]**

---

### Post by Lord Illidan on 2006-10-23
> **mips said:**
> Do NOT use apt-get to install Kubuntu desktop !!!

Rather do this, **[COLOR=Blue]http://www.psychocats.net/ubuntu/kde[/COLOR]**

No need to be so melodramatic, apt-get can also get the job done, it justs harder to remove.

---

### Post by mips on 2006-10-23
> **Lord Illidan said:**
> No need to be so melodramatic, apt-get can also get the job done, it justs harder to remove.


Ok, in future I will keep my mouth shut. I suppose it's ok if it's harder to remove kubuntu-desktop in future should he want to.

Sorry, my bad.

---

### Post by maniacmusician on 2006-10-23
> What's the difference between apt-get and aptitude?

the difference is that aptitude handles dependencies better. with aptitude, if you want to uninstall kde later, all you have to do is "sudo aptitude remove [name of package]" whereas with apt-get, that wouldn't work. so aptitude makes it easier to remove stuff that way. makes life a little easier. also keep in mind what i said about the various different packages you can use to install kde to your system

---

### Post by user1397 on 2006-10-23
you can always use my guide here on the forums to install/remove any of the desktop environments: [http://ubuntuforums.org/showthread.php?t=205002](http://ubuntuforums.org/showthread.php?t=205002)

---

### Post by aysiu on 2006-10-23
> **RussianVodka said:**
> What's the difference between apt-get and aptitude?
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by TheWizzard on 2006-10-23
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

thanks for the info on aptitude! i always used apt-get, but this orphan-control looks great. 

can't you make a sticky of this in the Installation & Upgrades section? 

question: is there a way to disable the apt-get command? i'm affraid i'll use it by accident in the future because i'm so used to it.

---

### Post by maniacmusician on 2006-10-23
that wouldn't be a good idea, because apps like the updater and automatix use apt-get. probably synaptic too.

---

### Post by aysiu on 2006-10-23
There's a way you could alias *apt-get* to use *aptitude* instead, but I wouldn't try it--you're liable to break your system!

---

### Post by user1397 on 2006-10-23
> **maniacmusician said:**
> that wouldn't be a good idea, because apps like the updater and automatix use apt-get. probably synaptic too.
i always was 100% positive that synaptic uses apt-get.  can anyone confirm this?

---

### Post by aysiu on 2006-10-23
Synaptic will not remove unused dependencies the way *aptitude* does; it behaves like *apt-get*. Whether it actually **is** *apt-get*... I don't know.

---

### Post by chaosgeisterchen on 2006-10-23
As far as I know, **Synaptic** and **Adept** are both using **dpkg** to handle packages, but how do they handle dependencies?

I strictly use aptitude as it is the better choice from my point of view. Your computer keeps being a lot more clean.

---

### Post by aysiu on 2006-10-23
As far as I know, *aptitude* also uses *dpkg*, but *aptitude* and *apt-get* do not behave the same way.

---

### Post by chaosgeisterchen on 2006-10-23
Well, that's something even I am aware of. The problem is to find out what is the mechanics behind synaptic or adept. One thing I do not like about those GUI-tools is the fact that you cannot see what happens under the coat of user interfaces.

---

### Post by TheWizzard on 2006-10-23
> **maniacmusician said:**
> that wouldn't be a good idea, because apps like the updater and automatix use apt-get. probably synaptic too.

i don't use apdater, i run a script in cron to automate updates.
no automatix form me ;) 
i can live with the command line.

---

### Post by chaosgeisterchen on 2006-10-23
Therefore I would strongly recommend **aptitude** to you. Nothing is above it concerning command line update and dependency management.

---

### Post by mattcn81 on 2006-10-23
> **mips said:**
> Do NOT use apt-get to install Kubuntu desktop !!!

Rather do this, **[COLOR="Blue"]http://www.psychocats.net/ubuntu/kde[/COLOR]**

Thanks for the link, just what I needed sir :)

---

### Post by mips on 2006-10-24
> **mattcn81 said:**
> Thanks for the link, just what I needed sir :)

No need to thank me, thank aysiu for his good writing abilities ;)

---

### Post by zAo on 2006-10-24
> **TheWizzard said:**
> thanks for the info on aptitude! i always used apt-get, but this orphan-control looks great. 

can't you make a sticky of this in the Installation & Upgrades section? 

question: is there a way to disable the apt-get command? i'm affraid i'll use it by accident in the future because i'm so used to it.
Don't worry. The latest apt has this feature too. Upgrade when Edgy is final and there you are :)

---

### Post by TheWizzard on 2006-10-25
> **zAo said:**
> Don't worry. The latest apt has this feature too. Upgrade when Edgy is final and there you are :)

cool. thanks for the info!

---

