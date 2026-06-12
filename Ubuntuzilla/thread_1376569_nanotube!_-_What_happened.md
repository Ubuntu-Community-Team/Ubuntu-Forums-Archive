---
title: "nanotube! - What happened???"
date: 2010-01-09
forum: Ubuntuzilla
---

### Post by Uncle Spellbinder on 2010-01-09
I don't remember the exact way to install SeaMonkey 2.0.1. I was going to use your wiki/instructions page. But it's dead??? The link in your sig now says..

***"There was an error processing your request Group not found for name: ubuntuzilla"*** and ***"The project specified does not exist"***. I hope everything is OK.


I'd really like to get SeaMonkey running. Already installed ubuntuzilla.

Edit:
Found the proper command: ***ubuntuzilla.py -a install -p seamonkey***. Still, I hope all is OK with Ubuntuzilla. Seems most links are dead.

---

### Post by nanotube on 2010-01-09
> **Uncle Spellbinder said:**
> I don't remember the exact way to install SeaMonkey 2.0.1. I was going to use your wiki/instructions page. But it's dead??? The link in your sig now says..

***"There was an error processing your request Group not found for name: ubuntuzilla"*** and ***"The project specified does not exist"***. I hope everything is OK.


I'd really like to get SeaMonkey running. Already installed ubuntuzilla.

Edit:
Found the proper command: ***ubuntuzilla.py -a install -p seamonkey***. Still, I hope all is OK with Ubuntuzilla. Seems most links are dead.

Hi
sourceforge seems to have had some database problems earlier today. everything is back to normal now.

also: unless you're running 64bit ubuntu, i suggest you stop using the ubuntuzilla script, and instead start using the ubuntuzilla repository.

see the project website for details, and let me know if you have any questions!

---

### Post by Uncle Spellbinder on 2010-01-10
I like adding repositories to the etc/apt/sources.list manually. 

What do I add? I already have the following...

```
#### Ubuntuzilla
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
```

*seamonkey-mozilla-build* is not in synaptic. Nor does *sudo apt-get install seamonkey-mozilla-build* work in terminal.


```
unclespellbinder@wombat:~$ sudo apt-get install seamonkey-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package seamonkey-mozilla-build
```







.

---

### Post by nanotube on 2010-01-10
hey

see the 'technical details' section of the site

the repository you have is for the ubuntuzilla installer script

the repo for ff+tb+sm directly is different.

also note the special instructions for the ubuntuzilla installer script users at the top of the 'installation' section.

---

### Post by Uncle Spellbinder on 2010-01-10
Will do. 

This is a fresh install of Karmic 32 bit by the way. So there should be no issues with previous installs as the script has not been used.. I'll see if I can find the correct repo to add, though I must be blind as I don't see it yet. Heading to 'Technical Details' section now....

---

### Post by Uncle Spellbinder on 2010-01-10
Ahhhhhh.  I see the difference. This is in my sources.list:
```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
```

This is in 'Technical Details':
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Got it all sorted now that I have things correct in sources.list. This is much easier than the script. **Really appreciate your work, nanotube**.

Thanks!!!

---

### Post by nanotube on 2010-01-10
you're quite welcome - glad it worked! :)

---

