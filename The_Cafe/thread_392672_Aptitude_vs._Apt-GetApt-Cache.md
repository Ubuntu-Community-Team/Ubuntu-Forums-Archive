---
title: "Aptitude vs. Apt-Get/Apt-Cache"
date: 2007-03-24
forum: The Cafe
---

### Post by SavantEdge on 2007-03-24
Is aptitude better than apt-cache/apt-get?  Is there a particular reason to use one over the other?  Why are there two separate utilities?

---

### Post by zubrug on 2007-03-24
Hope fully someone will give you a better explination than mine, Aptitude is better at handling dependancies as in if you install xubuntu-desktop on your ubuntu box and then decide to remove it, aptitude will accomplish this better.
Aptitude works well on final releases but gave me trouble during development. They all work, it comes down to preferance I guess. 
I tend to use aptitude on my non-development partition.

---

### Post by Nikron on 2007-03-24
> **zubrug said:**
> Hope fully someone will give you a better explination than mine, Aptitude is better at handling dependancies as in if you install xubuntu-desktop on your ubuntu box and then decide to remove it, aptitude will accomplish this better.
Aptitude works well on final releases but gave me trouble during development. They all work, it comes down to preferance I guess. 
I tend to use aptitude on my non-development partition.

Aptitude also installs all suggested/recommended packages whereas apt-get merely shows that they are recommened/suggested.

---

### Post by igknighted on 2007-03-24
> **SavantEdge said:**
> Is aptitude better than apt-cache/apt-get?  Is there a particular reason to use one over the other?  Why are there two separate utilities?

In edgy there is not much difference.  Aptitude has always been smart enough to remove "orphaned dependencies".  Like if you are using dapper and install kubuntu-desktop, hundreds of packages get installed that KDE needs.  If you used apt-get, should you decide that KDE isnt for you and want to remove, apt-get remove kubuntu wouldn't clear out all the KDE apps that got installed, or the libraries... it would just remove "kubuntu-desktop", which by itself does nothing... it just depends on everything so it all gets installed.  Aptitude would say, "oh, all those kde apps and libraries need to go too" and would remove everything the is only on your system because kubuntu-desktop needed it.

Now, in edgy/fiesty, apt-get does this as well, but not in one step.  If these orphaned dependencies are left after an uninstall, apt-get will advise you to run apt-get autoremove.  This will clean them out.  So aptitude and apt-get now are very very similar, but before they were not.  I just use whatever is easier to type.  Usually apt-get, but when searching I find apt-cache awkward to type so I usually go with aptitude.  Go figure.  See this site for more details:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by C Shore on 2007-03-24
If you just run 'aptitude' with no parameters you get a TUI (text user interface).  This is nice if you want somethinge like Synaptic on a server box, or you just want faster and/or a console app instead of Gnome.  

Now if I could just tame minicom/screen/aptitude combo to give me proper character sets instead of munging things I'd be happy.  

I suspect the reason I get weird characters using aptitude on a serial console is that minicom doesn't properly handle UTF-8.

---

### Post by SavantEdge on 2007-03-25
I'm on Feisty (if that makes a difference), and I was originally using Apt-Get/Cache, but now have switched over to Aptitude; will Aptitude start having troubles because it won't know exactly what Apt-Get did, or will it adjust and be fine, and I'll reap the benefits of Aptitude?

---

### Post by Paul133 on 2007-08-11
Is Synapitc a front for apt or aptitude? Does it handle dependecies as well as aptitude or not?

---

### Post by SunnyRabbiera on 2007-08-11
> **Paul133 said:**
> Is Synapitc a front for apt or aptitude? Does it handle dependecies as well as aptitude or not?

Synaptic is a front end to apt, and from my experience it handles dependencies well.
But experience may vary.

---

### Post by capink on 2007-08-11
> **SavantEdge said:**
> I'm on Feisty (if that makes a difference), and I was originally using Apt-Get/Cache, but now have switched over to Aptitude; will Aptitude start having troubles because it won't know exactly what Apt-Get did, or will it adjust and be fine, and I'll reap the benefits of Aptitude?


You will not reap the benefits of aptitude for the packages you already installed using apt-get. However, you will not have any troubles switching form one to the other or mixing both of them.

---

### Post by SunnyRabbiera on 2007-08-11
Aptitude is pretty decent in itself for a terminal app, its almost like the terminal version of synaptic due to its good features.

---

### Post by forrestcupp on 2007-08-11
Synaptic and Adept are based on apt-get and not aptitude which means that uninstalling things in the GUI is just as crappy as it is with apt-get.  In Synaptic, you can install the kde-games metapackage which installs all of the kde games.  Then when you remove kde-games, it only removes the metapackage, but not any of the games it installed.  What's the use of that?  Aptitude will remove everything that it installed with that metapackage, unless something else depends on something.

The moral of the story - in the command line, **always** use aptitude.

Why, oh why can't someone create a GUI frontend to aptitude?  The TUI is clunky and unintuitive.

---

### Post by aysiu on 2007-08-11
```
sudo apt-get autoremove
``` takes care of a lot of unused dependencies.

And sometimes *aptitude* is a little overzealous in terms of what it removes.

If you're using Edgy or Feisty, I'd recommend *apt-get* over *aptitude*.

---

### Post by forrestcupp on 2007-08-12
> **aysiu said:**
> ```
sudo apt-get autoremove
``` takes care of a lot of unused dependencies.

And sometimes *aptitude* is a little overzealous in terms of what it removes.

If you're using Edgy or Feisty, I'd recommend *apt-get* over *aptitude*.

Wow!  After all you have taught us in the past, you're changing what you say?

---

### Post by Adler on 2007-08-12
Hi All,

My *Spiritual Guru* that lead me from SuSE to UBUNTU recommended *sudo aptitude*. I've been through all the SuSE, or UBUNTU releases, as well as, Linux Mint, and my preferred method of up-dating is still via the Terminal. 

Autoremove seems to do the job, but only when I'm told in Terminal that certain packages are no longer needed. Then I do the Autoremove.

Adler

---

### Post by aysiu on 2007-08-12
> **forrestcupp said:**
> Wow!  After all you have taught us in the past, you're changing what you say?
Well, the functionality changed.

---

### Post by capink on 2007-08-12
Indeed, apt-get autoremove was only introduced since Edgy. As I understand this is a feature of Ubuntu only. Neither Debian itself nor any other Debian based distro have this feature. Can anyone confirm this?

---

### Post by reyfer on 2007-08-12
As I understand reading the APT documentation, both apt-get and aptitude are frontends to APT, so I don't see the point of "one vs the other". You use what you feel more comfortable with, in the end they both use the same program.

> aptitude is a terminal-based apt frontend with a number of useful features from [http://packages.debian.org/unstable/admin/aptitude](http://packages.debian.org/unstable/admin/aptitude)

---

### Post by Lord Illidan on 2007-08-12
> **aysiu said:**
> ```
sudo apt-get autoremove
``` takes care of a lot of unused dependencies.

And sometimes *aptitude* is a little overzealous in terms of what it removes.

If you're using Edgy or Feisty, I'd recommend *apt-get* over *aptitude*.

Pah, aysiu..well at least I've been using apt-get since...well...Hoary :P Never used aptitude except when I read what you said, and *guiltily* used it...pah, I say...

---

