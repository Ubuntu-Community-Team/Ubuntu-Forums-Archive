---
title: "Problem with installing Wine"
date: 2010-06-09
forum: Wine
---

### Post by Cannonzim on 2010-06-09
Alright, so I've got this new machine, and I just installed Ubuntu 10.04 on it. I'm trying to install wine, and in the terminal I keep getting this same error

sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

I can get it installed in synaptic, or in the ubuntu software section. I've also tried uninstalling wine and installing wine1.2, but that didn't work either. Help anyone?

---

### Post by maestrobwh1 on 2010-06-09
[http://www.winehq.org/](http://www.winehq.org/)

And use their repo and install wine from there.

---

### Post by Cannonzim on 2010-06-09
I tried downloading using Software Sources as well, but it still doesn't do anything after the window closes. No system update manager notification or anything.

---

### Post by cogadh on 2010-06-09
After you add the new software source, you need to tell it to install Wine, it won't do it automagically for you. Either use Synaptic or run the terminal command "sudo apt-get install wine".

---

### Post by Cannonzim on 2010-06-09
I did that as well, still nothing.

---

### Post by cogadh on 2010-06-09
Define "nothing". Are you getting the same errors in the terminal that you reported in your initial post or something different?

---

### Post by Soulcage on 2010-06-10
If you're using karmic or lucid you need to install the package called wine1.2 NOT wine.
```
sudo apt-get install wine1.2
```

---

### Post by cogadh on 2010-06-10
The "wine" package is just a dummy placeholder package that points to the current version of Wine. You don't need to specify "wine1.2", it will go to that package anyway.

---

