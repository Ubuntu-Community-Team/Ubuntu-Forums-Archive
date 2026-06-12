---
title: "install from iveCD"
date: 2008-07-25
forum: Ubuntu Brainstorm
---

### Post by chris200x9 on 2008-07-25
Hi, I just tried the install option from the liveCD rather than the try and install, and from my perspective it is pretty useless in its current state. I was expecting it to be a fast track to install but I was wrong it still takes forever to boot up into a gui then it takes you to the installer but nothing else to pass the time while you install. My suggestion is to make the install option just that for quick installs, I was thinking maybe something semi-interactive and ncurser based similar to the arch install cd only instead of installing "bare bones" it installs the whole ubuntu system gui and all.

---

### Post by olskar on 2008-07-25
Like the alternate cd? ;)

---

### Post by kdnewton on 2008-07-25
> **chris200x9 said:**
> I was expecting it to be a fast track to install but I was wrong it still takes forever to boot up into a gui then it takes you to the installer but nothing else to pass the time while you install.

The LiveCDs of Ubuntu now give you the entire desktop to use during the install. You can still play the included LiveCD games, word processors and web browser while installing.

---

### Post by zipperback on 2008-07-25
When you boot into the LiveCD it provides you with a fully functional desktop Ubuntu Desktop system. 

The system on the LiveCD is fully functional, however any changes that you make to the system are temporary because it is running only in the system memory and from the LiveCD.

Once you have tested the system and have determined that you like what you see, you just need to click the install icon on the desktop and it installs the system for you. All you need to do is provide a little basic information and the installer does the rest.

Modification of the system is very easy once you have the system installed.

If you are comfortable with the command line, you can use apt-get to manage your packages **(Example: "sudo apt-get update && sudo apt-get install build-essential")**, or if you prefer a GUI interface you can use **"Applications -> Add / Remove"** or you can use **"System -> Administration -> Synaptic Package Manager"**.

And as I said above, if you are comfortable with the command line **"Applications -> Accessories -> Terminal"** you can tweak the system however you would like to.

- zipperback
:popcorn:

---

### Post by chris200x9 on 2008-07-25
> **olskar said:**
> Like the alternate cd? ;)

yes, but thinking of it now why have to download and burn 2 iso's with *almost* the same things? Think about this scenerio a person has a computer downloads and burns an ubuntu liveCD and installs it on his home computer then finds a really old computer with not enough ram to boot the liveCD but he wants to install ubuntu he must go download the alternate cd burn it then install even though he already has an ubuntu cd. 

> **kdnewton said:**
> The LiveCDs of Ubuntu now give you the entire desktop to use during the install. You can still play the included LiveCD games, word processors and web browser while installing.

this is true if when the cd first boots you choose "try without changing my computer" but if you go to the second choice "install ubuntu" you are launched into a gui that provides you a hardy background and the gui installer no panels nothing. (which takes sometime to load, hence my ncuser suggestion)

---

### Post by snowpine on 2008-07-25
I agree it would be neat if the functionality of the Alternate CD was added to the Live CD, then you could install to multiple computers using the same disk and choose whichever type of installation is appropriate. Perhaps with a prominently-displayed message like "The alternate installation method is recommended for computers with less than ___ RAM."

However, the downside would be that people with slow computers (who may also have a slow internet connection, slow CD burner, etc.) would have to waste resources downloading the contents of the Live CD, which they don't need. So I think there will always be a place for a separate Alternate CD.

---

### Post by zipperback on 2008-07-26
> **snowpine said:**
> I agree it would be neat if the functionality of the Alternate CD was added to the Live CD, 

I think this is a good idea.

- zipperback
:popcorn:

---

### Post by smartboyathome on 2008-07-26
The reason the alternate CD cant be added to the LiveCD is because the installers they use are different. The Alternate CD installs from DEB packages, and those packages take up the whole cd (700mbs). The LiveCD installs from the live environment it loads up (that is why teh installer takes so long to load, it is mounting the squashfs file which is compressed to 25% of the size).

---

