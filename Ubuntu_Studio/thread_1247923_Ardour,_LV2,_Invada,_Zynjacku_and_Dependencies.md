---
title: "Ardour, LV2, Invada, Zynjacku and Dependencies"
date: 2009-08-23
forum: Ubuntu Studio
---

### Post by dawiba on 2009-08-23
I recently installed the Invada plugins in both LADSPA and LV2 formats. I can see and use the LADSPA version in Ardour, but not the LV2. I supposed this is because the version of Ardour in the repositories is compiled without LV2 support. I remembered reading that Ardour 2.8.2-1 was available from getdeb.net, so I went there and downloaded that version in the hope of getting LV2 support, but no luck.

First question, how can I change Ardour so that it sees LV2 plugins?

Second question, will the version of Ardour in 9.10 be compiled to use LV2 plugins?

Next I downloaded Zynjacku, since it's an LV2 host. However, when compiling, I get a message telling me it needs gtk+-2.0. I can't find this in Synaptic and gave up after trying a few different choices that looked as if they might do the job, but didn't.

Third question, what do I install from Synaptic that will give me gtk+-2.0?

Thanks

---

### Post by Stochastic on 2009-08-23
First answer: You need the LV2 libraries installed before you compile Ardour.  Here's a post regarding a .deb that should have LV2 support (i.e. it was made with a system that had LV2 libraries) [http://ubuntuforums.org/showthread.php?t=1216446](http://ubuntuforums.org/showthread.php?t=1216446)

Second answer: Ardour 2.8.2 is already part of Karmic Koala (9.10) but the LV2 libraries are NOT yet officially packaged for Ubuntu, so the official ardour package doesn't yet have LV2 support.  Some people are working to resolve this soon (but I doubt it will make it into 9.10, probably 10.04).

Third answer:  I think the package you're looking for is: libgtk2.0-dev
I came to this conclusion by running ```
apt-cache search gtk+ | grep dev | grep 2
```which searches all packages for any mention of gtk+ then narrows the field to only those lines that mention dev and then further narrows the filed to only those lines that mention 2.


I hope that helps.

---

### Post by dawiba on 2009-08-24
Thanks for the response Stochastic.

I wasn't aware that the LV2 libraries had to be installed *before* compiling Ardour. I'll remember that for the future. I downloaded the .deb package from the link you gave, but it wouldn't install, giving me a message that a later version was already installed. Thank you also for showing me the way to narrow down my searches for the right software using the terminal (another thing to remember!). I used it again for the next part of installing Zynjacku. Unfortunately, Zynjacku doesn't run, telling me there's no module 'zynworld'.

I gave up at this point trying to run the Invada LV2 plugins. I'm happy to wait until 10.04 if needed and there are already lots of plugins I *can* use without any hassle. It also helps that I'm not a big plugin user anyway. I just wanted to try it out of curiosity, assuming from what I'd read about Ardour that it supports LV2, but was a bit baffled when the plugins didn't appear.

Thanks again for your help.

---

### Post by Grishka on 2009-08-24
I have Zynjacku in [my PPA](https://launchpad.net/~thir/+archive/ppa), as well as another LV2 host - Ingen. Zynjacku is more stable, mind you. Ingen will still crash with many LV2 plugins.

---

### Post by dawiba on 2009-08-24
Grishka, I'm not going to bother just now, but thanks for your reply.

---

### Post by dawiba on 2009-08-26
Okay, I came back to this and added Grishka's PPA. The only problem is that, after updating, Ardour won't launch at all.

When I try from the terminal I get this

```
dawiba@ubuntustudio:~$ ardour2

/usr/lib/ardour2/ardour-2.8.2: error while loading shared libraries: libvamp-hostsdk.so.2: cannot open shared object file: No such file or directory
dawiba@ubuntustudio:~$
```

I've tried to fix this but to no avail. The file libvamp-hostsdk.so.2 seems to be in /usr/lib as a link. Can anyone help?

---

### Post by Stochastic on 2009-08-26
Can you post the output of ```
apt-cache policy libvamp-hostsdk2
```

Edit: Did you do an 'apt-get update' after adding his repositories?  That's very dangerous.  I notice there are a number of backports from Karmic in there, including libraw1394-2.0 - which needs support in the kernel turned on for it to work - but no kernel recompiles are in that repository to fix this issue.  You may need to 'apt-get purge' every one of his packages (provided it doesn't remove major important chunks of your OS) and re-install from the official repositories.  If you have done an 'apt-get update' I advise you seek professional support (or at least guru level community support) in fixing your operating system.  Maybe Griska can help explain things.

---

### Post by dawiba on 2009-08-26
Stochastic - 

```
dawiba@ubuntustudio:~$ apt-cache policy libvamp-hostsdk2
libvamp-hostsdk2:
Installed: 2.0-2
Candidate: 2.0-2
Version table:
*** 2.0-2 0
500 http://ppa.launchpad.net jaunty/main Packages
100 /var/lib/dpkg/status
1.3-1 0
500 http://gb.archive.ubuntu.com jaunty/universe Packages
dawiba@ubuntustudio:~$ 
```

---

### Post by Stochastic on 2009-08-26
You need to remove all the packages you installed from that repository and re-install them from the official repository.

---

### Post by dawiba on 2009-08-26
Ho hum :roll:

Hopefully I'll get it sorted [-o<

Thanks for your help

---

### Post by Grishka on 2009-08-26
> **dawiba said:**
> EDIT: I've also dicovered that Hexter, Jamin and Sooperlooper won't start now either. These are the error messages.

Hexter

```
dawiba@ubuntustudio:~$ jack-dssi-host hexter.so

jack-dssi-host: Warning: DSSI path not set
jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/dawiba/.dssi"
```

Jamin

```
dawiba@ubuntustudio:~$ jamin
jamin: error while loading shared libraries: liblo.so.0: cannot open shared object file: No such file or directory
```

SooperLooper

```
dawiba@ubuntustudio:~$ /usr/bin/slgui
/usr/bin/slgui: error while loading shared libraries: liblo.so.0: cannot open shared object file: No such file or directory
```

As before, I'd be grateful for any help :)

```
sudo ln -s /usr/lib/liblo.so.7.0.0 /usr/lib/liblo.so.0
```
will fix this.

---

### Post by dawiba on 2009-08-26
Thanks Grishka, but you're too late! I tried removing packages and only ended up in a worse mess :oops:

The moral?

If it isn't broken, don't fix it! :)

Now where did I leave my UbuntuStudio DVD?......

---

### Post by Grishka on 2009-08-26
> **dawiba said:**
> Thanks Grishka, but you're too late! I tried removing packages and only ended up in a worse mess :oops:

The moral?

If it isn't broken, don't fix it! :)

Now where did I leave my UbuntuStudio DVD?......

DON'T PANIC. I've safely downgraded all these packages to their default versions many times in the past. fire up Synaptic, choose a faulty package, and switch the version from CTRL+E menu. purging is an overkill.

---

### Post by Stochastic on 2009-08-26
> **Grishka said:**
> DON'T PANIC. I've safely downgraded all these packages to their default versions many times in the past. fire up Synaptic, choose a faulty package, and switch the version from CTRL+E menu. purging is an overkill.

Wow, I swear I learn something new everyday with this OS.  Sorry for mentioning the purge method.

---

### Post by dawiba on 2009-08-26
> **Stochastic said:**
> Wow, I swear I learn something new everyday with this OS. 

Me too! Funny how I always learn too late... :(

The computer needed a clean out anyway :)

---

