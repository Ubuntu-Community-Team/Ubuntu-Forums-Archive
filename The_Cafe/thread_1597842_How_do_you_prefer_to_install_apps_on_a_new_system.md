---
title: "How do you prefer to install apps on a new system?"
date: 2010-10-15
forum: The Cafe
---

### Post by sandyd on 2010-10-15
^^

---

### Post by NightwishFan on 2010-10-15
I use tasksel on Debian, apt-get on Ubuntu.

---

### Post by hhh on 2010-10-15
OP, you forgot gdebi.

---

### Post by zekopeko on 2010-10-15
> **hhh said:**
> OP, you forgot gdebi.

And Software Centre.

---

### Post by sandyd on 2010-10-15
> **hhh said:**
> OP, you forgot gdebi.

> **zekopeko said:**
> And Software Centre.
hmm. maybe I should have changed synaptic to GUI apps....

---

### Post by DougieFresh4U on 2010-10-15
> **hhh said:**
> OP, you forgot gdebi.

Most likely old news, but I noticed that **gdbi** is not being used, instead **Software Center** opens to install packages. 
Not sure if I really like that idea:???:

---

### Post by NightwishFan on 2010-10-15
I think it works out nicely in practice.

---

### Post by cinnabubbles on 2010-10-15
I usually use the Software Centre.

If I need to though, I will use apt-get, and hope there's well-versed instructions for my newbie brain to wrap around.

---

### Post by Dustin2128 on 2010-10-15
depends on the distro. For ubuntu, a terminal apt-get out of pure habit or laziness.

---

### Post by Bapun007 on 2010-10-15
sudo apt-get install software_centre

---

### Post by matthew.ball on 2010-10-15
I have a bash script which copies a bunch of important files across (mainly config files like .bashrc) and grabs a list of installed packages ([FONT="Courier New"]dpkg --get-selections | grep -v deinstall[/FONT]) which I run before I do a re-install, then I have another script which just replaces the aforementioned files and installs the list of packages via [FONT="Courier New"]dpkg --set-selections[/FONT].

---

### Post by lovinglinux on 2010-10-15
I vote for *dpkg --get selections*, because that is the method my [Umarks]("https://addons.mozilla.org/en-US/firefox/addon/13153/") extension uses.

---

### Post by SadisticCheeto on 2010-10-15
I have no real preference. I use apt-get/aptitude, Synaptic, and the Software Center. I don't really know what determines which one I decide to use.

---

### Post by Khakilang on 2010-10-15
You forgot software centre. I am still a noob in command line and always use software centre.It is safer this way. But sometime I get my hand a little dirty and try apt-get but not too successful and end up with broken dependencies.

---

### Post by TNT1 on 2010-10-15
Software center usually. I normally only use apt-get or add repo's when I want a newer version than is in the usc, or an app that isn't in the usc.

---

### Post by Rasa1111 on 2010-10-16
i like to use apt-get the most.
sometimes use synaptic, 
once in a great while software center..
but apt-get is my favorite i think..

---

