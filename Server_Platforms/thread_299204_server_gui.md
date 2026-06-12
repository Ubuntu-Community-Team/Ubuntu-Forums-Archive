---
title: "server gui"
date: 2006-11-13
forum: Server Platforms
---

### Post by vr.crawler on 2006-11-13
hello.
i just want to ask u if is a big security hole if u use graphical interfaces on servers. i heard some time ago that it might be, im clearly not expert in this matter and i hope someone will answer me if it is and how is that. 
i was wondering why server releases don`t have it and are very minimalistic. its logical that for functionality but with a graphical interface u can easily see things as a whole. or at least me as a non expert :)
it is indicated to have servers with gui? (in ubuntu or any other unix/linux deried OS)

---

### Post by jpeddicord on 2006-11-13
Servers were meant to **not** have a GUI, as GUIs only slow things down and waste time on the server. While a GUI does not provide a security flaw, I highly reccommend against it. A server without a GUI can run up to 2 or 3 times faster than one with a GUI.

---

### Post by cyris| on 2006-11-14
if you have the resources then i dont see a problem. be smart with what packages you choose to install on your server as gui apps are not all 100% security tight :D

---

### Post by neill on 2006-11-14
what if you use the GUI to do all the configuration stuff - and then 'turn it off'

(of course you would have already removed as many of the unwanted packages as possible)

is it possible to log out of a GUI runlevel and then login to an appropriate CLI only level ? how would you do that ?

that way you get the ease of config that the GUI brings (especially for the amateurs like me !!) but the resources aren't wasted when the server's running

possible or am i making some HUGE noob error :rolleyes: 

neill

---

### Post by neill on 2006-11-14
sudo init 3 ?

---

### Post by Shuja on 2006-11-14
A GUI really isn't a problem on a server with modern hardware.  If you really want it install it and edit your config files to not start it by default so all you have to do is a 'startx' when you want a GUI up.

---

### Post by PilotJLR on 2006-11-14
There are two problems to having a GUI:
 - resources wasted
 - possible security holes

Running a GUI simply takes away from memory available and cpu usage... for a home server, this is often not a big deal at all. For a true enterprise class server, this becomes more of an issue.

For security, I'm not saying that X has holes or issues... rather, every single application that runs has the potential to introduce an attackable flaw. So any unnecessary applications running would simply increase the chance that you have something that would be receptive to various attacks. Again, for a home server, often not a big deal...
So if you are more comfortable with using X, then go for it... although running in runlevel 3, as the previous poster stated, would be a good compromise.

---

### Post by NorthCoast on 2006-11-14
Besides the wasted resources and slight security concerns the best reason to not run a GUI is because you can do everything and anything you need from a remote machine.  "Headless", no monitor or keyboard at all.  Just because you have enough resources doesn't mean you should waste it.  Servers are meant to run for years and every little bit of wasted resource adds up over the long term.

---

### Post by crouton on 2006-11-14
I agree with NorthCoast.  SSH in from a GUI'd machine, keep the server as spartan as possible.  Lean and mean will keep chugging along much longer.

---

### Post by cyris| on 2006-11-15
All good points. I run a gui on my home server but at work its just not needed. Setup your box the way you want, you can always start off with a gui and then run at init 3.

---

### Post by vr.crawler on 2006-11-16
ok thanks for good answers.
ill search for some answers in logging in from a gui`d machine with ssh, on a server. i have them at home anyway, il try.
can i see it gui`ed if the server dont have any x installed ? and i connect with ssh ?

---

### Post by lazyart on 2006-11-16
What I did, because admittedly I needed a crutch, was to install the server, then xubuntu-desktop to get things in place, then install webmin and administer the server from another machine (web browser) via port 10000.  You'd be amazed that you can do everything from there.  It will require you to activate the root account because you can't sudo when you are installing packages and the like.

---

### Post by Gaweph on 2006-11-16
thres also Ubuntu Center, it can be found in the 3rd party section of the forums.

Its a very handy tool, and you can upload stuff to your server, download stuff, easy to use for those of us who are not cmd-line litterate (like me)

---

### Post by cyris| on 2006-11-16
I guess Ubuntu Ceneter has been renamed to iCenterX and man it looks kinda sweet :D I may give this a go in the next few days :D

---

### Post by tturrisi on 2006-11-17
I use debian etch w/ lamp & gnome-core for development and as a home wan server.  I have the resources on this box & there's absolutely no performance hit at all for apache or mysql.  But, this is a home server and I would not set it up this way for a production server where others or a business was dependant on it.

I also run debian woody on a celeron 333 w/ 256 ram w/ lamp & fluxbox.  This holds my business database & some family files.  It is closed to the wan. It's been running 24/7 for 4.5 years and has only been rebooted when I had power outages.  I don't belive I logged in in 6 months! It has no monitor either.  I used fluxbox w/ emelfm & nedit so I could quickly do the configs I wanted.  They are still there in the event I ever need to use the gui again.  No need to remove them because I have xdm disabled completely.

---

