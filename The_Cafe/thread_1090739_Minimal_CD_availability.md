---
title: "Minimal CD availability"
date: 2009-03-08
forum: The Cafe
---

### Post by BGFG on 2009-03-08
Hey guys,
How soon is the minimal cd available after the Final release usually ? Looking forward to Jaunty...

Ok, no replies yet :) so i'll add that i plan to Do a minimal Jaunty install then beef up the system as the need arises, so i've actually been checking into the terminal command for 'Pure Gnome'. I happened across this on CSMonkey Blog:
```

$ sudo aptitude install x-window-system-core gnome

```

Would this work ?

---

### Post by Mehall on 2009-03-10
Should do I imagine.

Especially if you replace "gnome" with "kde" :P

And I also wanna know when the Jaunty Minimal will be out.

---

### Post by InfinityCircuit on 2009-03-10
The contents of the installer will probably not change significantly at the end of the dev cycle, so you should be able to use Beta or RC images.

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by Mehall on 2009-03-10
> **InfinityCircuit said:**
> The contents of the installer will probably not change significantly at the end of the dev cycle, so you should be able to use Beta or RC images.

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso)

Excellent! Thank you, I didn't know where these were kept for the mini iso!

---

### Post by myusername on 2009-03-10
xorg is a dependancy of gnome so all you would have to do is:
sudo apt-get install gnome-core or gnome

---

### Post by InfinityCircuit on 2009-03-10
> **myusername said:**
> xorg is a dependancy of gnome so all you would have to do is:
sudo apt-get install gnome-core or gnome

I don't believe that that is correct.

[http://packages.ubuntu.com/intrepid/gnome](http://packages.ubuntu.com/intrepid/gnome)

---

### Post by BGFG on 2009-03-11
After some more checking and referring to this:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I'm working on this as my first apt-get:
```

sudo apt-get install xorg gnome-core firefox gksu synaptic packagekit hal dbus

```

---

### Post by mkvnmtr on 2009-03-11
I think if you use the 8.10 minimal disk and as soon as you get the command line you ask for a dist upgrade in a short time you will have a 9.04 install to start to work on.

---

### Post by BGFG on 2009-03-11
> **mkvnmtr said:**
> I think if you use the 8.10 minimal disk and as soon as you get the command line you ask for a dist upgrade in a short time you will have a 9.04 install to start to work on. 
Great suggestion, didn't even think of that, but just for ceremonial significance, I'll wait for the 9.04 minimal. :) Funny huh ?
In any case, I suppose it's safe to assume that all the included minimal components are stable already...

According to how slim i can keep my system come 9.10, I may do a dist-upgrade. i currently have over 1200 and the couple attempted upgrades were very unpretty.

---

### Post by BGFG on 2009-04-25
Just completed the install, I had Jaunty installed already and everything was working perfectly already so i went into the minimal install pretty confidently.

I now know that contrary to what I was told, the Jaunty minimal install includes dbus and synaptic by default so i have only installed xorg, gnome-core , GDM, Shiretoko and qmmp.

Due to the fact that i changed my username, I now have two home directories, I'll decide whether or not I'll leave that as it is or sort it out. System is very responsive, now just to customise :) 

Further bulletins as events warrant :)

---

