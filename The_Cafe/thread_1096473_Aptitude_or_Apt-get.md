---
title: "Aptitude or Apt-get?"
date: 2009-03-14
forum: The Cafe
---

### Post by CJ Master on 2009-03-14
When you're using a distro with the option, which one do you use? :)

---

### Post by tech13 on 2009-03-14
Does it matter really? I have used both and got the same results.

---

### Post by days_of_ruin on 2009-03-14
apt-get.Because its what I know and I don't see any reason to use aptitude.

---

### Post by Thirtysixway on 2009-03-14
> **tech13 said:**
> Does it matter really? I have used both and got the same results.

I don't think you're supposed to mix the two.  They each can handle packages a little differently, causing issues.

---

### Post by inobe on 2009-03-14
i stick with synaptic/ apt

---

### Post by BGFG on 2009-03-14
I recently had to resort to deborphan to find and remove unused/orphaned packages on my system and subsequently found out that all dependancies installed with a package using aptitude are removed upon uninstallation with aptitude. 

So from now on, Aptitude.

---

### Post by wolfen69 on 2009-03-14
> **Thirtysixway said:**
> I don't think you're supposed to mix the two.  They each can handle packages a little differently, causing issues.

as long as you do
```
sudo aptitude update 
```
first, you will be fine. then you can aptitude install.

---

### Post by Kvark on 2009-03-14
> **BGFG said:**
> I recently had to resort to deborphan to find and remove unused/orphaned packages on my system and subsequently found out that all dependancies installed with a package using aptitude are removed upon uninstallation with aptitude. 

So from now on, Aptitude.
Doesn't...
```

sudo apt-get autoremove

```
...remove all orphaned packages?

---

### Post by lykwydchykyn on 2009-03-14
aptitude all the way.  I wish people would use it when giving advice, it really has much better conflict handling, incorporates a number of seperate older tools like apt-cache, and has a nice ncurses interface for when you really need to get down to business.

I guess for just quick installs & upgrades it doesn't matter, but for situations where you're going to be managing from the CLI (server installs, e.g.) it's a much more capable solution.

I switched to it when I noticed that the Debian team was calling it the recommended package manager.

---

### Post by TBOL3 on 2009-03-15
I would use aptitude.  But I think the Add/Remove Applications App in the Applications menu, uses apt.

---

### Post by mamamia88 on 2009-03-15
i usually use aptitude doesn't it remove unnescessary packages when installing?

---

### Post by BGFG on 2009-03-15
> **Kvark said:**
> Doesn't...
```

sudo apt-get autoremove

```
...remove all orphaned packages?

Nope. I frequently run that command and still found around 30 unused packages with deborphan. Subsequently tested aptitude by installing packagekit (with all it's dependancies) and removing, and aptitude removed everything.

I suggest you try deborphan on your system and see for yourself.

---

### Post by days_of_ruin on 2009-03-15
> **TBOL3 said:**
> I would use aptitude.  But I think the Add/Remove Applications App in the Applications menu, uses apt.

It does and so does synaptic.So I think its safer to use apt-get if you are also going to be using synaptic and gnome-app-install (The actual program name for Add/Remove).

---

### Post by lykwydchykyn on 2009-03-15
> **days_of_ruin said:**
> It does and so does synaptic.So I think its safer to use apt-get if you are also going to be using synaptic and gnome-app-install (The actual program name for Add/Remove).

aptitude, apt-get, synaptic, and add/remove are all front-ends for the APT system, which is libapt-pkg.  What is unsafe about using more than one?  I've been mixing Synaptic and aptitude for years.

---

### Post by munishvit on 2009-03-15
Using aptitude over apt-get are largely irrelevant if you're using Edgy Eft (6.10), Feisty Fawn (7.04), or any latest version of Ubuntu.
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by lisati on 2009-03-15
Although I voted aptitude, it can depend on what I'm doing. One advantage of the aptitude approach is that it can pull in dependencies that you've forgotten, which can save you some typing.

---

### Post by konqueror7 on 2009-03-15
i use *apt-get* because its much shorter to type...:D

---

### Post by x33a on 2009-03-15
> **konqueror7 said:**
> i use *apt-get* because its much shorter to type...:D

1 character shorter :P

i mostly use aptitude, sometimes apt-get especially while following some tutorial.

---

### Post by sisco311 on 2009-03-15
> **konqueror7 said:**
> i use *apt-get* because its much shorter to type...:D

> **x33a said:**
> 1 character shorter :P

i mostly use aptitude, sometimes apt-get especially while following some tutorial.

nope, that is ain't true. apt-get is 1 character longer.

```
apt-g<TAB> #6
```

```
apti<TAB> #5
```

---

### Post by samjh on 2009-03-15
I haven't experienced any practical differences between the two in Debian.  In Ubuntu, I use apt-get, because aptitude tends to want to automatically remove packages that I actually want to keep.

---

### Post by billgoldberg on 2009-03-15
> **BGFG said:**
> I recently had to resort to deborphan to find and remove unused/orphaned packages on my system and subsequently found out that all dependancies installed with a package using aptitude are removed upon uninstallation with aptitude. 

So from now on, Aptitude.

use apt-get autoremove instead of apt-get remove.

---

### Post by konqueror7 on 2009-03-15
> **sisco311 said:**
> nope, that is ain't true. apt-get is 1 character longer.

```
apt-g<TAB> #6
```

```
apti<TAB> #5
```

nope, its 1 letter shorter...;)

---

### Post by missbliss on 2009-03-15
I just use apt-get b/c it was the firs thing I came across, hence being the first thing I got used to.

---

### Post by tombom62 on 2009-03-15
apt-get
;cause Im used to it;)

---

### Post by CJ Master on 2009-03-15
Yea, but apt-get seems to fail a lot for me, which is why I love how aptitude can "problem solve."

---

### Post by tombom62 on 2009-03-15
I haven;t ever had an apt-get problem.

---

### Post by run1206 on 2009-03-15
same here, i've never had a problem with apt-get either :?
i use both but i voted apt-get cuz it's what i'm used to using.

---

### Post by CJ Master on 2009-03-16
You've never had a problem where you try to use apt-get and there were dependancies that couldn't be deleted, so it won't let you?

Aptitude is very nice for situations like those.

---

### Post by bobmatino17 on 2009-03-16
apt-get, its what my dad taught me to use and thats really all ive ever used on debian based machines.

---

### Post by dragos240 on 2009-03-16
apt-get has super cow powers, aptitude doesn't, simple as that.

---

### Post by run1206 on 2009-03-16
> **CJ Master said:**
> You've never had a problem where you try to use apt-get and there were dependencies that couldn't be deleted, so it won't let you?

Aptitude is very nice for situations like those.

nope, never had that problem. whenever i did sudo apt-get autoremove, all the dependencies got deleted :?

---

### Post by unutbu on 2009-03-16
I can't say for sure, but I wonder if your problems with apt-get come from using both apt-get and aptitude on the same system. 

If you stick to one or the other exclusively, I think you improve your chances of never running into any problems.

---

### Post by Citizen Bleys on 2009-04-24
*thread necromancy*

Can anybody actually explain what the difference is?  Aside from apt-get moo, I mean.

---

### Post by BGFG on 2009-04-24
> **Citizen Bleys said:**
> *thread necromancy*

Can anybody actually explain what the difference is?  Aside from apt-get moo, I mean.

Aptitude is a wee bit better at handling dependancies.

Eg. sudo aptitude install 'whatever' installs a package and all it's dependancies, if there is a problem, aptitude will attempt to resolve it intelligently. Sudo aptitude remove 'whatever' removes the package and all the extra packages that were installed with it in one fell swoop. No need to 'autoremove' as in apt-get. Aptitude will also automatically 'autoremove' everytime it is run, as long as orphaned packages exist.

not really that major eh? i use them both anyway. Just remember that for which ever one you intend to use, run apt-get or aptitude update before.

---

### Post by ninja_numbnuts on 2009-06-12
Which do you use?

---

### Post by Chemical Imbalance on 2009-06-12
Aptitude.  
It automatically removes unused dependencies when uninstalling a package and it has a CLI package manager.

---

### Post by OutOfReach on 2009-06-12
apt-get: force of habit

---

### Post by Dharmachakra on 2009-06-12
Aptitude. It's more similar to pacman.

---

### Post by HappyFeet on 2009-06-12
> **Chemical Imbalance said:**
> Aptitude.  
It automatically removes unused dependencies when uninstalling a package and it has a CLI package manager.

Taking 2 seconds to do
```
sudo apt-get clean && sudo apt-get autoremove
```
is no big deal. Besides, apt-get is less things to type. ;) But whatever floats your boat. My computer works perfect either way, which is all that counts.

---

### Post by hayden92 on 2009-06-12
apt-get 

Not out of preference, it just that I've never looked into aptitude

---

### Post by BslBryan on 2009-06-12
> **outofreach said:**
> apt-get: Force of habit
+1

---

### Post by CJ Master on 2009-06-12
[Did you search first?](http://ubuntuforums.org/showthread.php?t=1096473)

Anyway, now I use pacman. ;) But aptitude otherwise.

---

### Post by Dark Aspect on 2009-06-12
What is the difference? I have used both before when following howtos but I didn't really even notice the two where different.

---

### Post by Slug71 on 2009-06-13
smart

---

### Post by kerry_s on 2009-06-13
aptitude is the first thing i remove from my install.
it has screwed up enough times i don't even want it there.

---

### Post by keplerspeed on 2009-06-13
Aptitude. I was advised to use it when I first started using ubuntu, as it is:
> a wee bit better at handling dependancies

---

### Post by anystupidname on 2009-06-13
> **dragos240 said:**
> apt-get has super cow powers, aptitude doesn't, simple as that.

Sure, but aptitude has snakes n' elephants n' stuff...
[http://upload.wikimedia.org/wikipedia/commons/c/c6/Aptitude_moo.png](http://upload.wikimedia.org/wikipedia/commons/c/c6/Aptitude_moo.png)

:D

---

### Post by Chemical Imbalance on 2009-06-13
> **kerry_s said:**
> aptitude is the first thing i remove from my install.
it has screwed up enough times i don't even want it there.

How do you mean?

Are you talking about dpkg locks?

---

### Post by The Toxic Mite on 2009-06-13
I use apt-get for packages, and aptitude for software.

:P

---

### Post by BlazeFire247 on 2009-06-13
Apt-get:

I'm used to it
I don't remember using aptitude
It's one of the commands I remember next to "sudo" :lol:

---

### Post by Firestem4 on 2009-06-13
generally i only use a graphical manager when I want to browser around and see whats there. Its much easier to do with a GUI Interface than text.

When I know something I want to install any other time, and its quicker to do apt-cache show/search, i will just use the terminal.

---

### Post by CJ Master on 2009-06-13
> **Firestem4 said:**
> generally i only use a graphical manager when I want to browser around and see whats there. Its much easier to do with a GUI Interface than text.

When I know something I want to install any other time, and its quicker to do apt-cache show/search, i will just use the terminal.

What about when there's some package where you know the package name? Such as apt-get firefox?

---

### Post by gnomeuser on 2009-06-13
I've used debian in the past but I honestly never felt at home with apt-get or dpkg as a whole. When I need to use a cli interface I strongly prefer yum, it's command design feels very elegant and it's output is a thing of beauty.

When it comes to every day tasks, I prefer PackageKit's GNOME applications, I tend to prefer using a gui for things like applying updates, installing new software and so on.

---

### Post by sim-value on 2009-06-13
emerge ! :P

Na i use apt-get aptitude i just know that ppl claim that it washed their dishes and worked better with meta-packages ...

---

### Post by clonne4crw on 2009-06-24
apt-get is shorter to type

---

### Post by monsterstack on 2009-06-24
I used Linux for about a year before I discovered the following application.

```
sudo aptitude
```

Go ahead, try it. You'll be surprised.

---

### Post by Chemical Imbalance on 2009-06-24
> **monsterstack said:**
> I used Linux for about a year before I discovered the following application.

```
sudo aptitude
```

Go ahead, try it. You'll be surprised.

It is indeed handy at the console.

---

### Post by kk0sse54 on 2009-06-24
apt-get, although it's been a while since I've used it since I'm not too big of a fan of Debian package management as a whole.

---

### Post by gregh7470 on 2009-06-24
> **CJ Master said:**
> When you're using a distro with the option, which one do you use? :)
   I use aptitude and here is why:
apt-get will install dependencies just like aptitude but when you remove these packages with apt-get, it won't remove the libraries this package installed even though they are no longer needed... aptitude keeps a log of its actions in /var/log/aptitude and removes **everything**.
When you install that package with aptitude and remove it with aptitude, aptitude 'detects' that those library packages aren't used anymore and will therefore automatically remove them.
Some commands you can try:

```
aptitude update
aptitude upgrade
aptitude dist-upgrade
man aptitude
```I would strongly recommend sticking with just one package manager since they don't keep track of one another - if you use synaptic for awhile then switch to apt-get then aptitude your asking for trouble, even a broken OS.
Whenever I do a fresh install...because I experiment a lot...I start with ```
aptitude update
```Even when used in terminal mode it's 'click-able'...you can click the menus and make choices.  I know synaptic is easier but if you get used to aptitude you want regret it.

---

### Post by forrestcupp on 2009-06-24
> **gregh7470 said:**
> I use aptitude and here is why:
apt-get will install dependencies just like aptitude but when you remove these packages with apt-get, it won't remove the libraries this package installed even though they are no longer needed...

That's what apt-get autoremove is for.  

Before they added autoremove, aptitude was the preferred method.  Now, there's really no reason for aptitude, especially when there are good GUI frontends for apt-get and not for aptitude.

It's not wise to mix the two.

---

### Post by philcamlin on 2009-06-24
apt-get :popcorn:

---

### Post by ad_267 on 2009-06-24
Is there a way to search package descriptions using aptitude?

"apt-cache search package_name" searches names and descriptions, but the -n option searches only in the package name. "aptitude search" just searches the package names.

I voted apt-get.

---

### Post by raymondh on 2009-06-24
apt-get

---

### Post by bryonak on 2009-06-25
> **ad_267 said:**
> Is there a way to search package descriptions using aptitude?

"apt-cache search package_name" searches names and descriptions, but the -n option searches only in the package name. "aptitude search" just searches the package names.

I voted apt-get.

As opposed to apt-*, description search is off by default... to turn it on, prefix with a ~d:
```
aptitude search ~dTEXT
```

I prefer aptitude because it's
a) faster to write: apit[tab] is one char less than apt-g[tab] and two chars less than apt-ca[tab]
b) unified. I can do "aptitude search" aswell as "aptitude install" aswell as "aptitude markauto", while I have to use three different programs with apt-*.
c) offering an additinal UI which is far easier to navigate than apt-* when handling broken dependencies.

The main reason I see in favour of apt-* is the lazyness to switch ;)
Which is understandable, because there is nothing wrong with the old apt-* tools, so most people don't bother to use something else.

---

### Post by adssse on 2009-06-27
apt-get into it

---

### Post by Gizenshya on 2009-06-27
apt-get

---

