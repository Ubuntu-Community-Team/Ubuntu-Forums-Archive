---
title: "World of Warcraft"
date: 2009-02-04
forum: Wine
---

### Post by demodw on 2009-02-04
Greetings,
After having installed a router, World of Warcraft stopped working on my Ubuntu installation. What happends is I can open it fine, but after I enter my username + Password and hit enter, the application freezes. Sometimes it just goes "Disconnected" after a while, after times I have to force it to shut down.
It worked fine before, both in Windows Vista and Ubuntu.
After installing the router, it only works in Vista.
I have double checked that the correct ports are open, I've tried installed Firestarter and opened ports etcetc.
Did the same for my laptop, same result.
There's no entry in any logs for the application, neither any "different" output from WINE when I run it through a terminal.

The router in use is a Zyxel NBG334W.

edit: Besides this, the internet works flawlessly.

---

### Post by finku on 2009-02-04
You sure you didn't touch anything within the game and all patches were applied to the game?

---

### Post by demodw on 2009-02-04
Yes, absolutely sure. if I unplug the router it works again.

---

### Post by finku on 2009-02-05
I don't know if this might help but you might give it a shot. Make sure your computer has direct access to the internet, if behind a router make sure all ports are forwarded to your computer IP [ifconfig]. 

Also as a tentative, I would turn off app-armor, by going into terminal and typing the following:

```
sudo /etc/init.d/apparmor stop 
```

---

