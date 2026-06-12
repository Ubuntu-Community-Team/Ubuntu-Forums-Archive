---
title: "stuck half way through kernel update"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by cabz on 2013-03-28
I wasdoing my daily update on my  pc running 13.04 daily build, at some point i lost internet connection, after I regained signal my update became stuck,I have tried shutting down and rebooting but the updater goes right back to the same spot and stops , any ideas on how I can get this cleared out and going again?

[ATTACH=CONFIG]240664[/ATTACH]

---

### Post by Frogs Hair on 2013-03-28
Shut down again and try from the terminal and watch for any prompts to run other commands. 

```
sudo dpkg --configure -a
``` ```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

### Post by cabz on 2013-03-28
> **Frogs Hair said:**
> Shut down again and try from the terminal and watch for any prompts to run other commands. 

```
sudo dpkg --configure -a
``` ```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

well i tryed that and it did'nt work, so for giggles i tryed going into 
"advance options" on reboot . i ran the "check files " option and the "repair broken packages " option and that seeems to have cleared it up. what command would i use or where do I look to see what kernel version I am running now?

---

### Post by ronacc on 2013-03-28
in a terminal run ```
 uname -a 
```

---

### Post by kevpan815 on 2013-03-28
For me KERNEL 3.9 RC4 is Locking Up!

---

### Post by cabz on 2013-03-28
> **ronacc said:**
> in a terminal run ```
 uname -a 
```

cool that got it, I am running the newest version kernel. the one that got stuck updateing .
now i need to get a better wireless router!

---

### Post by grahammechanical on 2013-03-29
You have had the same issue that I have had for yesterday and today. After brute force shut and rebooting I ran dpkg configure and that settinled things down but this morning Update Manager reloaded and became stuck again. 

I fixed this today by running Synaptic Package manager (not installed by default) and finding the 3.8.0-15 kernel and all it components and marking them for re-installation. That worked and cleared this stoppage of Update Manager.

I saw in the news yesterday that some web site or other was under a massive Denial of Service Attack that had the knock on effect of slowing down the Internet. I think that our problems were related to this.

Regards.

---

### Post by ronacc on 2013-03-29
I also had a stall during upgrading of the -15 kernel yesterday  but since I was using synaptic it was easily rectified . The repos were generally flaky, many hash sum mismatches when reloading the repo's, had to reload several times to get them all current , seemed worse on the main server than the US one .

---

### Post by Elfy on 2013-03-29
I just assumed it was local to me - but had the same issue yesterday with kernel update.

---

### Post by craig10x on 2013-03-29
Same here...update manager froze when trying to install the latest kernel update but i was able to get it straightened out by going to the package manager, locating the previous kernel (which had a ! mark in front of it)...when i moused over it, there was an option to "upgrade" so i let it do that, and it installed the newest kernel...and the update manager has worked fine since...

Having just had a problem with the updates freezing during install the day before (where i had to go into the terminal to get it straightened out) i thought it was the same problem again, but apparently it wasn't...
It's quite possible of course, that BOTH incidents i had was related to that internet issue grahammechanical mentioned above...

---

### Post by cabz on 2013-03-29
synaptic is the one thing i forgot to install on my pc. gonna do that now (~:

---

