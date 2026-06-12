---
title: "boot up manager - bum - all other threads are locked"
date: 2015-02-22
forum: The Cafe
---

### Post by Li_Wu on 2015-02-22
B.U.M. is actually a nice GUI program to administer the init.d system, runlevels asf.
[ATTACH=CONFIG]260164[/ATTACH]
But all threads about it, the wiki asf. are pretty much locked, dead or inaccessible. So the ubiquitous calls for participation are really just a joke.
So I thought, I'd at least open a single thread in this forum on BUM, which indeed is open for posting ):P  in 2015.

Now let's discuss 'bum'. There are some flaws in some translations and even the english 'original' leaves sth. to be desired. But kudos for openly spelling out :

> Almost all the services started with init scripts in runlevels 2-3-4-5 and rcS.d don't have a standard, "human readable" description of their main behaviour. [SIZE=3][COLOR=#b22222][B]
Very often the package description for these services is very cryptic 
and the common user is quite disorientated and doesn't understand the meaning.[/B][/COLOR][/SIZE] Boot-Up Manager (BUM) will use a special list to display the package description in its main view window.
To contribute to this list, please feel free to update this wiki-web page: [http://wiki.ubuntu.com/InitScriptHumanDescriptions](http://wiki.ubuntu.com/InitScriptHumanDescriptions)


so even the English original falls a bit short under this premise, but it sure tries to improve, unlike some soft I could mention.

---

### Post by kerry_s on 2015-02-22
> **Li_Wu said:**
> B.U.M. is actually a nice GUI program to administer the init.d system, runlevels asf.

But all threads about it, the wiki asf. are pretty much locked, dead or inaccessible. So the ubiquitous calls for participation are really just a joke.

So I thought, I'd at least open a single thread in this forum on BUM, which indeed is open for posting ):P  in 2015.


ubuntu uses systemd, init.d was replaced. bum will more than likely screw up your day trying to fix what it broke.

---

### Post by Li_Wu on 2015-02-22
> **kerry_s said:**
> ubuntu uses systemd, init.d was replaced. 

that sure confirms that bum is imperfect yet - not even informing the user whether is works on a particular init system.

rcconf is an ersatz Textmode GUI for bum, but offers nothing except en-/disable services. That's not good enough.

---

### Post by Li_Wu on 2015-02-22
[https://www.linux.com/images/stories/fig-1-systemadm.jpg](https://www.linux.com/images/stories/fig-1-systemadm.jpg)

as usual, it is made somewhat difficult to use the above tool, the name of which - or package name - is unbeknownst it seems.

itz systemdgui but u can't have it

---

### Post by blueeyedcreature on 2015-12-15
> **Li_Wu said:**
> [https://www.linux.com/images/stories/fig-1-systemadm.jpg](https://www.linux.com/images/stories/fig-1-systemadm.jpg)

as usual, it is made somewhat difficult to use the above tool, the name of which - or package name - is unbeknownst it seems.

it is called systemadm and you can install it via 'apt-get install systemd-ui'

looks like something we have to live with instead of bum

also on the console: systemctl

---

