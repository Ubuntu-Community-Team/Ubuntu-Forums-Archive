---
title: "Wine 1.1.17 on Jaunty Jackalope - X suport error"
date: 2009-03-26
forum: Wine
---

### Post by redbob on 2009-03-26
Hi Guys... I'm swimming on Jaunty waters... 
my version isn't yet Beta.

I'm not happy to install Wine 1.1.17, always this message:
> configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this

I already installed x-dev, linux headers, build-essential, even wine-deps I installed, but no way... 

Any ideas?

---

### Post by NightMKoder on 2009-03-26
Why are you compiling wine? Just get the deb packages from their repos.

If you actually need to compile it, I'm guessing you're on 64-bit. This means that you need to add symlinks, as per [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) .

The script ([http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh)) won't work on jaunty, but you can just find/replace 8.10 with 9.04 to make it think you're on ibex.

---

### Post by redbob on 2009-03-26
OK, I can install wine 1.0.1 from repos, as from synaptic, as from apt-get. But I have an application that doesn't run so good in Wine 1.0.1 as it runs in Wine 1.1.16.

---

### Post by poisonkiller on 2009-03-27
Then download 1.1.16/17/whatever .deb packages from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
No official packages for Jaunty yet, but Intrepid's should work just as well.

---

### Post by YokoZar on 2009-03-28
> **poisonkiller said:**
> Then download 1.1.16/17/whatever .deb packages from here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
No official packages for Jaunty yet, but Intrepid's should work just as well.
I put up Jaunty ones last night.  Enjoy.

---

### Post by Reiger on 2009-03-29
Definitely will, off try Office 2007 again! (Won't install off a 1.01 you see, and didn't have luck with the Intrepid packs.)

That is when I get a connection to the server:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list
--2009-03-29 17:20:54--  http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... failed: Connection refused.

```

---

### Post by oneguynick on 2009-03-31
> **Reiger said:**
> Definitely will, off try Office 2007 again! (Won't install off a 1.01 you see, and didn't have luck with the Intrepid packs.)

That is when I get a connection to the server:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list
--2009-03-29 17:20:54--  http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... failed: Connection refused.

```

This thread came up in a Google search. It is also down for me. I have attempted Intrepid and Jaunty with no luck.

---

### Post by redbob on 2009-04-01
(Office 2007 - argh!! - nobody is perfect)...
I installed repos Wine version. My application worked up. But I'll try Wine 1.1.18, that is fresh on Winehq.org.
Bye, fellas!!! 
...
How do I mark this thread as solved???

---

