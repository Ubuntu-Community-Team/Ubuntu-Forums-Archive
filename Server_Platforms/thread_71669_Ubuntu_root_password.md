---
title: "Ubuntu root password"
date: 2005-10-04
forum: Server Platforms
---

### Post by Glut on 2005-10-04
Just trying to sort fact from fiction, without having to bother with the installer source. Because I'm lazy.

I noticed that the root password in the shadow file has a hash in it after the install. The standard method of disabling a password is to put in a character that cannot be a hash, such as '!' or '*'. For this reason, I do not believe that the Ubuntu root password is disabled, but simply preseeded as a part of the install. This may not be the case, as the hash that appears may indeed not be valid, but simply be there just to 'fool' someone. Although, if someone can view your shadow file, I think that you have bigger problems...
If a valid preseeded password is the case, and user bob installs sshd because he can, it is in the realm of possibility that the password is remotely crackable. However, a preseeded password should be much, much stronger than a password made by a person because it can use the entire keyspace rather than the visible subset. It is also more likely to be random than a password chosen by a person.
So it could be that the password is much more secure than a default install of another distro.

So my questions are...
given this reasoning, 
a. Is the password truley disabled, or simply preseeded?
b. If it is preseeded is there any reason that it should not be disabled?

---

### Post by mairas on 2005-10-11
Are you certain you have not set the password yourself? I just checked from both a Hoary install and a fresh Breezy install, and both have "*" as the root password hash in /etc/shadow.

Kind regards,

Matti Airas

---

### Post by Glut on 2005-10-11
Yes, it seems I had a brain fade on this. I thought I was checking a clean install, but it turned out to be one that was already modified. :oops:

---

### Post by eternal on 2005-10-14
well, i have just now completed a fresh install of ubuntu 5.10.  and i was never prompted to set the root password;  only that i had to make a user account and set it's password...  as a 6 year freebsd user, this concerns me a bit...  can any kind soul shed some light on this for us?


5 minutes later...  found and read ([https://wiki.ubuntu.com//RootSudo)](https://wiki.ubuntu.com//RootSudo)), and quote:

Ubuntu uses sudo to allow a normal user administrative privileges. Thus the traditional UNIX 'root' account is disabled (i.e. it is not possible to log in as root). All the graphical configuration utilities use sudo by default. Thus when Synaptic or something similar asks you for a password, it is asking for your password.

The first user created is part of the admin group, which can use sudo. Any users created after that are not by default. It is recommended that all users of Ubuntu use sudo, as it provides clear benefits to security. 

-------------------------------

my only suggestion is that that text would be added at the appropriate point during the install process to explain that, because that is a brilliant approach, in my opinion.

---

### Post by Pablo_Escobar on 2005-10-14
Root account is disabled by default (You can enable it if You wish).
When You need something done use "sudo" instead of "su -".

---

### Post by Rohan on 2005-10-14
If you want root just type "sudo passwd"

---

