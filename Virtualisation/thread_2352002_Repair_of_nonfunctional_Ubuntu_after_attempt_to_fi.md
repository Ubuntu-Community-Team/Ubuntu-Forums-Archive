---
title: "Repair of nonfunctional Ubuntu after attempt to fix package repository"
date: 2017-02-08
forum: Virtualisation
---

### Post by mediafire2 on 2017-02-08
Hello there, all started by corrupted package repository. I tried many commands which failed, the last one seemed to reinstall everything but on next boot I get login at shell prompt and no GUI. Startx is missing, internet connection not working. Now I need to install all missing components on top of existing installation to preserve my user profile and installed 3rd party programs. Because the installed Ubuntu gives minimum functionality, I suppose I'll need to boot to some recovery environment independent on existing installation, but what should I use when the Ubuntu DVD only allows me to do either clean install or install as new OS aside of existing. FTR installed Ubuntu is 16.04 and I'm using Ubuntu 16.10 DVD. Would the possibilities be better if I used Ubuntu 16.04 DVD?

---

### Post by ajgreeny on 2017-02-08
Give us more detail if you can of what you mean by your first sentence, and also show us the commands you tried in order to solve the problem as it is impossible for us to guess at what may have happened, and therefore how to help you.

Do you have a cable connection or wifi only? You may find that ethernet will connect with no problem even if wifi is not working, and if it will connect that way run command ```
sudo apt-get install ubuntu-desktop
``` which may bring back everything that is currently missing, assuming this is Ubuntu with unity desktop.

---

### Post by mediafire2 on 2017-02-09
The fix of corrupted file /var/lib/dpkg/status was unsuccessfull because no good backup existed.
Command that could process was sudo apt-get upgrade --force or something sounding like that. 
I remember the command downloaded and installed alot of packages from internet.
The network is bridged over virtual manager support add on which is supposedly also missing or uninstalled so I don't think there's a possibility to use network from command prompt, command above gives alot of E: Failed to fetch [http://*.deb](http://*.deb)  Temporary failure resolving 'cz.archive.ubuntu.com'

---

### Post by ajgreeny on 2017-02-09
Your comment **The network is bridged over virtual manager support add on** means nothing to me and I suspect is irrelevant to your problem, but we do need to know what commands were used; you can find them in a hidden file in your home called **.bash_history**, so if you can login to the command line use command ```
less .bash_history
``` you can then scroll up and down using cursor keys or page-up, page-down keys.

---

### Post by mediafire2 on 2017-02-09
> **ajgreeny said:**
> Your comment **The network is bridged over virtual manager support add on** means nothing to me and I suspect is irrelevant to your problem.

That's because Ubuntu is running as virtual host, so no native network interface support in Ubuntu.

The last commands performed before the OS became corrupted are

[IMG]http://i.imgur.com/VQ5PwcH.png[/IMG]

So **apt-get -f install** is the command that supposedly made tte OS out of business.

---

### Post by ajgreeny on 2017-02-10
> That's because Ubuntu is running as virtual host, so no native network interface support in Ubuntu.
I'm afraid I still do not understand completely; is your Ubuntu install running as a guest in something like VirtualBox?  You call it a virtual host; host to what?

---

### Post by mediafire2 on 2017-02-10
> **ajgreeny said:**
> is your Ubuntu install running as a guest in something like VirtualBox?

Exactly. That's important for know that Ubuntu has no native network driver now.

---

### Post by ajgreeny on 2017-02-10
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit, and hopefully will get more attention from the forum VM experts, which I regret does not include me.

---

