---
title: "su vs. sudo password"
date: 2007-06-08
forum: Server Platforms
---

### Post by abalter on 2007-06-08
I wanted to be able to have a root shell.  I didn't know about the various options such as:
sudo su -
sudo bash
sudo -i
etc. 

Therefore, as many have done, I set a root password using using sudo passwd root.  I can access a root shell by typing su and then giving the password I created.  However, now if I try to (a) type sudo <x> or (b) try to open an application that requires root access such as synaptic or (c) get into administrator mode in system settings, I am asked for a password, and the one I set for root does not work!  Apparently there are two root passwords that Ubuntu looks for.

How do I set the password that I now need for these operations?

Thanks, 

Ariel

---

### Post by EndPerform on 2007-06-08
Sudo uses the password for your user when you use it, which is also the case when a prompt appears, such as the case for Synaptic.  Basically, Sudo allows you to run things with root privileges without having to become the actual root user.  Next time you try Synaptic, check out the dialog, it'll ask for your password, not root's.  Hope this helps :)

---

### Post by piers on 2007-06-08
Using [COLOR="rgb(139, 0, 0)"]sudo -s[/COLOR] is (nearly) the same as [COLOR="rgb(139, 0, 0)"]su[/COLOR] without having to set root a password and without having to type sudo every time.

---

