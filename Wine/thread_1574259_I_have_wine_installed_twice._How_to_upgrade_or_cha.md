---
title: "I have wine installed twice. How to upgrade or change path and uninstall."
date: 2010-09-14
forum: Wine
---

### Post by ChrisEiffel on 2010-09-14
I built wine 1.2 from source a while back. It is compiled under 

/usr/local/bin/wine

I wanted to upgrade from 1.2 to 1.3.2. I went to the ubuntu repository and got wine 1.3.2. Ubuntu installed wine 1.3.2 under 

/usr/bin/wine. 

So now I have two wines installed on my computer and the $PATH is pointing to the old one.

I have this question for all of you wine experts.** How should I upgrade my wine**? 

**Option 1 -  ubuntu software center**
If I use the ubuntu software center, what is the best way to update my path variable and uninstall the old wine 1.2?

**Option 2 - build/upgrade wine from source again**
How can I upgrade the wine 1.2 version correctly/best practice? (I know there are lot of tutorials but I'm not sure which one to trust)
Is there a benefit from building from source?

---

### Post by bdutta on 2010-09-14
> **ChrisEiffel said:**
> 

snip

So now I have two wines installed on my computer and the $PATH is pointing to the old one.

I have this question for all of you wine experts.** How should I upgrade my wine**? 

**Option 1 -  ubuntu software center**
If I use the ubuntu software center, what is the best way to update my path variable and uninstall the old wine 1.2?

**Option 2 - build/upgrade wine from source again**
How can I upgrade the wine 1.2 version correctly/best practice? (I know there are lot of tutorials but I'm not sure which one to trust)
Is there a benefit from building from source?

Chris,

Since your wine-1.2 is installed by building sources, you didn't mention, how exactly you did it, you may be better off removing that first. If you used the apt tool to resolve dependences, fetch source, build and install, then you can use apt tool to remove it, just as any Ubuntu package. you could use Synaptic as well. 

If however it was manually downloaded and built from a tarball (*.tar.gz) i.e. the typical 'make install' route, then apt isn't aware of this as a package, so you need to manually remove the package files from /usr/local/ and probably few other places. 

Once you've removed wine-1.2, the easiest way to get wine-1.3.2 (latest, as of date) is the apt route. You just need to add a PPA pointer for Launchpad, i.e. edit /etc/apt/sources.list and add a PPA url.
For example, assuming that you are on karmic (9.10), just add this line at the bottom of this file and write it back (use 'sudo', else file is read-only) --

```

deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

```

then do 'apt-get update', followed by 'apt-get install wine-1.3', and you should be good to go!

cheers,
BD

---

### Post by bdutta on 2010-09-14
And, don't forget to restart wineserver, i.e. kill previous running instance.

Post a successful 1.3.2 install, just do this:
```

/usr/bin/wineserver -k

```

---

