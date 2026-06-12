---
title: "Article  on  Lynis"
date: 2016-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by rosswmcgee on 2016-11-07
I read this article and then looked in synaptic and found Lynis there though I have not installed it. I am a long time linux user, had never heard of this. Do I need it? Why do I need it?

If so could I just install from synaptic? Still wandering in the wilderness. :D



In order to install Lynis on your Ubuntu system, you must follow these steps.

1. Open a terminal window.
2. Create the file /etc/apt/sources.d/lynis.list with the following content (RELEASE is the release of Ubuntu...aka xenial):

deb [https://packages.cisofy.com/community/lynis/deb](https://packages.cisofy.com/community/lynis/deb) RELEASE main

3. Save and close the file.
4. Update apt with the command sudo apt-get update.
5. Install Lynis with the command sudo apt-get install lynis.
6. Okay the installation when prompted (you will be warned that the package cannot be authenticated).
7. Allow the installation to complete.

---

### Post by oldfred on 2016-11-08
That looks like it has you add a ppa or personal repository.
You should only add ppa that you know & trust.
Often ppa cause issues on Ubuntu version upgrade like from 14.04 to 16.04. All ppas should be removed if upgrading version. 

But some for instance, need a newer nVidia driver as they have a brand new card & must have newest driver. They then need a ppa. 
Or if you have odd hardware or want to experiment with newer kernel you may add a ppa.

ppa may give newer version than Ubuntu's repository. The apt-get installer checks all repositories you have enabled and installs newest. Sometimes that leads to the old issue of dependencies not matching.

---

### Post by Bucky Ball on 2016-11-08
If you want Lynis, install it from Software Centre. If you don't like it, uninstall it.

Just checked in 16.04 LTS. Yes, there it is in the package manager, ready to go. No PPA required. I found the Lynis webpage and looks like you are following instructions for a manual install from source or PPA (as oldfred suggests). No need.

No, you don't need Lynis. I've never heard of it in eight years of Ubuntu and being around here.

---

### Post by rosswmcgee on 2016-11-09
Hey thanks Bucky. Not looking for headaches so well enough can be left alone.

---

