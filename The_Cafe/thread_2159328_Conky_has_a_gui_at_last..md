---
title: "Conky has a gui at last."
date: 2013-07-02
forum: The Cafe
---

### Post by philinux on 2013-07-02
[http://m.webupd8.org/2013/07/conky-manager-gui-for-managing-conky.html?m=1](http://m.webupd8.org/2013/07/conky-manager-gui-for-managing-conky.html?m=1)

Gonna try this when I get home.

---

### Post by ajgreeny on 2013-07-02
Just tried it.
Not sure it's for me.  It does not seem to give you many display or content options, though I admit I have a fairly complicated .conkyrc configuration, and my conky window is a lot more detailed than I could figure out how to produce when trying out the GUI manager.  See screenshot.

Perhaps I didn't give it enough of a proper try?

---

### Post by The Spectre on 2013-07-03
This is great, I have been wanting to get Conky set up on my System for quite a while but I haven't had the time (or patience) to go through the process of setting it up.

This will hopefully get me started.

I would eventually like to get it set up similar to VinDSL's Conky.

With any luck a similar Theme will be added or I will take the time to configure Conky to my liking...

[IMG]http://vindsl.com/images/vindsl-cal9-1st-day-monday.png[/IMG]

---

### Post by Cheesemill on 2013-07-03
Bah.

This just takes all of the fun out of conkying :cool:

---

### Post by lykwydchykyn on 2013-07-03
> **Cheesemill said:**
> Bah.

This just takes all of the fun out of conkying :cool:

As of this day, a stylish conky on the desktop is no longer a badge of l33tness :D

---

### Post by Frogs Hair on 2013-07-03
I'm pretty sure the application has been on pinguy os , but I don't know for how long.

---

### Post by ajgreeny on 2013-07-03
Perhaps I totally misunderstood how much this GUI manager can do.

It looks as if you still need to write a ~/.conkyrc  or other config file to get any decent output in your conky window.  Does the GUI just give you a theme or design and still need almost as much work on the details of the entries beneath the TEXT line?

I admit it, I'm baffled about what exactly it does for me.

---

### Post by su:bhatta on 2013-07-05
this post got me interested in conky, again... :)

---

### Post by montag dp on 2013-07-05
> **ajgreeny said:**
> Perhaps I totally misunderstood how much this GUI manager can do.

It looks as if you still need to write a ~/.conkyrc  or other config file to get any decent output in your conky window.  Does the GUI just give you a theme or design and still need almost as much work on the details of the entries beneath the TEXT line?

I admit it, I'm baffled about what exactly it does for me.Looks like it gives you some basic themes and configuration options, so it will work okay if you want a fairly simple conky and like one of the available themes.  If you like one of the themes, you can always add to it yourself to make it display more stuff.

---

### Post by ajgreeny on 2013-07-05
> **montag dp said:**
> Looks like it gives you some basic themes and configuration options, so it will work okay if you want a fairly simple conky and like one of the available themes.  If you like one of the themes, you can always add to it yourself to make it display more stuff.

That's what I thought, but as I like a transparent normal window for my conky output and don't like the themes supplied by that GUI, I shall stick with what I have.

---

### Post by Buntu Bunny on 2013-07-05
Interesting. [Voyager ]("http://voyager.legtux.org/") has had a GUI for Conky for awhile now.

---

### Post by Glynnux on 2013-07-05
Here's a simple conkyrc I adapted for my 1366x768 laptop.
It reveals all the important (to me) info at the bottom of the screen under my browser window.
Just requires Neuropolitical font installing (otherwise it will default to Sans)

---

### Post by zer010 on 2013-07-06
If this program creates it's own .conkyrc, then I'd like to see how it's configured.  Could help me hash out a few things and help me to reconfigure the one I've had.

---

### Post by Snowhog on 2013-07-07
> **ajgreeny said:**
> Just tried it.
...I have a fairly complicated .conkyrc configuration,...
Would you mind sharing your .conkyrc file?

---

### Post by cradom on 2013-07-07
There are more themes available... Instructions on how to get them under the vid.
Would imagine you could do your own theme and add it to the folder/manager.
[http://www.youtube.com/watch?v=imUdL8e5jvE](http://www.youtube.com/watch?v=imUdL8e5jvE)

---

### Post by ajgreeny on 2013-07-08
> **Snowhog said:**
> Would you mind sharing your .conkyrc file?

Very happy to do so.

It is probably only complicated when compared with those from the conky-manager package, but no matter; here it is as conkyrc.txt

---

### Post by Snowhog on 2013-07-08
> **ajgreeny said:**
> Very happy to do so.

It is probably only complicated when compared with those from the conky-manager package, but no matter; here it is as conkyrc.txt

Thank you. Your networking section has some things in it that I didn't know about.

---

### Post by ajgreeny on 2013-07-09
> **Snowhog said:**
> Thank you. Your networking section has some things in it that I didn't know about.

Is that the vnstat part?  I find it very useful to know how much I have downloaded, or more truthfully, I used to find it useful; not so much now with unlimited downloads, even though it is "subject to fair usage" whatever that may mean.

---

### Post by Snowhog on 2013-07-10
Yes, vnstat. I have 'limited' download bandwidth, but it's substantial, and I never go over, plus, the unused bandwidth for the month is 'rolled over' to the next.

---

### Post by diazepamkit on 2013-07-11
err i want to uninstall this any help?!
since i still begginer atm

i try using terminal but cant uninstall it

---

### Post by ajgreeny on 2013-07-11
> **diazepamkit said:**
> err i want to uninstall this any help?!
since i still begginer atm

i try using terminal but cant uninstall it

Uninstall what: conky?

```
sudo apt-get purge conky
``` will do just that.

---

### Post by diazepamkit on 2013-07-11
> **ajgreeny said:**
> Uninstall what: conky?

```
sudo apt-get purge conky
``` will do just that.

i mean this conky-manager.. i didnt like this app :(

---

### Post by zer010 on 2013-07-12
> **diazepamkit said:**
> i mean this conky-manager.. i didnt like this app :(

```
sudo apt-get update && sudo apt-get purge conky-manager && sudo apt-add-repository --remove ppa:teejee2008/ppa 
```

^_^d

---

### Post by deadflowr on 2013-07-12
> **diazepamkit said:**
> i mean this conky-manager.. i didnt like this app :(

Install ppa-purge.

---

### Post by diazepamkit on 2013-07-12
> **zer010 said:**
> ```
sudo apt-get update && sudo apt-get purge conky-manager && sudo apt-add-repository --remove ppa:teejee2008/ppa 
```

^_^d

well thanks a lot 
:D

---

### Post by ajgreeny on 2013-07-12
I almost always use synaptic for installing and removing applications.  It is much more flexible than the software-centre, and by using Settings ->Repositories you can make any changes you want to the software-sources, including disabling or removing any enabled ppa repos.

---

### Post by synaptix on 2013-07-12
Hooray! Think I'll go get this later tonight and play around with it.

---

### Post by ana551 on 2013-07-14
conky just never gets boring.....:D :D

---

