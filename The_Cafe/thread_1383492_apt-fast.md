---
title: "apt-fast"
date: 2010-01-17
forum: The Cafe
---

### Post by Ian dewhurst on 2010-01-17
I found this while digging around online, it basically replaces the command apt-get for removal/upgrade/install, here is the original article.

[http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html](http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html)

It truly is faster than apt-get.

---

### Post by Dark Aspect on 2010-01-17
> **Ian dewhurst said:**
> I found this while digging around online, it basically replaces the command apt-get for removal/upgrade/install, here is the original article.

[http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html](http://www.webupd8.org/2010/01/new-apt-fast-version-now-with-full-full.html)

It truly is faster than apt-get.

Interesting find, I'll check this out through virtualbox since I am no longer a 100% Ubuntu user. I never reallly found apt-get to be that slow, I wonder if the script would work on debian.

---

### Post by Slug71 on 2010-01-17
How bout Smart Package Manager?

---

### Post by Xbehave on 2010-01-17
It only speeds up downloads by using axel (i think that means it uses pipelining to clobber the server, so please don't use this when the servers are running slow such as on release days)

In particular looking at the script shows it has no effect on removals
```
# !/bin/sh
# apt-fast v0.02 by Matt Parnell http://www.mattparnell.com, this thing is fully open-source
# if you do anything cool with it, let me know so I can publish or host it for you
# contact me at admin@mattparnell.com

# Special thanks to Travis/travisn000 from the PCLinux Forums for making improvements that allow
# for more complex apt-get commands. See the thread: http://www.pclinuxos.com/forum/index.php/topic,66385.0.html

# Use this just like apt-get for faster package downloading. Make sure to have axel installed.

# If the user entered arguments contain upgrade, install, or dist-upgrade
if echo "$@" | grep -q "upgrade\|install\|dist-upgrade"; then
  echo "Working...";

  # Go into the directory apt-get normally puts downloaded packages
  cd /var/cache/apt/archives/;

  # Have apt-get print the information, including the URI's to the packages
  # Strip out the URI's, and download the packages with Axel for speediness
  # I found this regex elsewhere, showing how to manually strip package URI's you may need...thanks to whoever wrote it
  apt-get -y --print-uris $@ | egrep -o -e "(ht|f)tp://[^\']+" > apt-fast.list && cat apt-fast.list | xargs -l1 axel -a

  # Perform the user's requested action via apt-get
  apt-get $@;

  echo -e "\nDone! Verify that all packages were installed successfully. If errors are found, run apt-get clean as root and try again using apt-get directly.\n";

else
   apt-get $@;
fi
```

This seams like classic premature optimisation, you only need this script if your download speeds are slow but that's probably because you have a slow internet connection so the effect of this will be marginal.

---

### Post by Settwi on 2010-01-17
Or, I know this works in Ubuntu 9.1, possibly synaptic package manager?  it has a search function AND a graphical interface so it's not just all command-based stuff,
Now, im sure most of you know the syntax of this command (apt-get) but, if someone new to ubuntu looks at this thread, here's a heads-up.
[sudo] apt-get [install, autoremove, remove] YOURapplicationNAMEhere

---

### Post by Xbehave on 2010-01-17
> **Settwi said:**
> [sudo] apt-get [install, autoremove, remove] YOURapplicationNAMEhere
not for autoremove
sudo apt-get [install,remove] AppName
sudo apt-get [update,upgrade,autoremove] 

'advanced'
sudo apt-get [purge,source,build-dep] AppName
sudo apt-get [dist-upgrade,dselect-upgrade. clean, autoclean,check]

tbh i'd forget about autoremove and check by just using aptitude.

---

### Post by nilarimogard on 2010-01-18
I guess there is something wrong on my system, because apt-get usually downloads with 100 kb/s tops, while downloads in a browser work at ~800 kb/s (the same source tested - Launchpad). So this helped me...

---

