---
title: "Can't find lmms in the applications menu"
date: 2009-01-28
forum: Ubuntu Studio
---

### Post by groundnut on 2009-01-28
I've installed lmms (Linux MultiMedia Studio) and as a consequence also wine.

My problem is that I can't find lmms in the applications menu.

---

### Post by Stochastic on 2009-01-28
This thread should solve your queries: [http://ubuntuforums.org/showthread.php?t=907888](http://ubuntuforums.org/showthread.php?t=907888)

---

### Post by groundnut on 2009-01-28
Thanks Stochastic,

I have lmms in the applications menu now.

I got a new problem instead: The lmms window is shifted downwards also obscuring the panel below.

---

### Post by Stochastic on 2009-01-28
Yeah, I had that same problem.  I don't really use that app, so I haven't bothered to fix it just yet, but I believe the fix lies in simply installing the newest (or at least a newer) lmms.  The one in the repos is getting quite old.  You may also try disabling compiz to see if that fixes the bug (if you have compiz on).

---

### Post by simtaalo on 2009-01-29
you really need the latest version of lmms, getting the old version from the repo's is pretty pointless as its so buggy.

goto [https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa) pick your version of ubuntu from the drop down menu, add the lines to your /etc/apt/sources.list

then run 

```
sudo apt-get update && sudo apt-get install lmms
```

this should install the latest version 0.4.2 for you.

also come to the lmms irc room on freenode ##lmms
any problems you might have, or if you just wanna chat or maybe swap/collaborate on projects you're very welcome :)

---

### Post by Stochastic on 2009-01-29
I'm planning to clean up that lmms package and get it through the REVU process, but it may take me too long for Jaunty - depends on my schedule.  If anyone else wants to take that project on, I think it's a good idea.

---

### Post by simtaalo on 2009-01-30
what needs to be done to it? i'm willing to help, but don't think i've actually got the skills, i could talk to people in the irc room about it.

---

### Post by groundnut on 2009-01-30
I added 
[COLOR="DarkOrange"]deb [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main[/COLOR]
to the repo's

Now I have version 0.42 working alright.

many thanks,

---

### Post by simtaalo on 2009-01-30
:) glad it worked for you

have fun

---

### Post by solaralchemy on 2009-01-31
Hi I followed the instructions at
[https://launchpad.net/~tobydox/+archive/ppa](https://launchpad.net/~tobydox/+archive/ppa) 
and put information in for source I specfied intrepid
I kept checking for errors making sure  i put everything in right
updates did not install.........and when i tried to install
LMMS it gave me the old version from the unbuntu library...
I really liked LMMS on windows and would like to get it up and running on ubuntu.

I would be thankful for any trouble shooting tips

---

### Post by groundnut on 2009-02-01
hello solaralchemy,

Choose the following menu: System > Administration > Software Sources

Then add the following line to third party Software Sources:

deb [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main

The last step is installing the package with Synaptic.

---

### Post by Stochastic on 2009-02-03
YAY!! TobyDox has gotten his package changes into Jaunty.  0.4.2-0ubuntu1 will be in Universe for Jaunty.

---

### Post by simtaalo on 2009-02-03
great news :)

---

