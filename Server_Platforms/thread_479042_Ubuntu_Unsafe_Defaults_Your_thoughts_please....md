---
title: "Ubuntu Unsafe Defaults? Your thoughts please..."
date: 2007-06-19
forum: Server Platforms
---

### Post by OzzyFrank on 2007-06-19
I've come across mention of unsafe default settings in Ubuntu, which you can find here [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/) and also the official Ubuntu page [https://help.ubuntu.com/community/UnsafeDefaults](https://help.ubuntu.com/community/UnsafeDefaults). The basic settings you're advised to change are:

Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:

tmpfs /dev/shm tmpfs defaults,ro 0 0 
Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:

PermitRootLogin yes
to
PermitRootLogin no


Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:

sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su


I'd like to see what people think, and if anyone advises not to make the changes outlined. For example, r-w shared memory is seen as a threat, and apparently there is no reason for it to be that way. But are there any unforeseen problems that could occur if I change the shared memory to r-o? Or do you think these 3 suggestions are important and won't cause any hassles?

---

### Post by yabbadabbadont on 2007-06-19
A few installs ago, I tried mounting the shared memory read-only as suggested.  System wouldn't boot correctly after that...

---

### Post by OzzyFrank on 2007-06-19
Yeah, thought I might see something like that... not the first time I would have seen security tips that limit access to your system a little bit too much, hehehe! What's next? "Never connect to the internet, and preferably have your PC surrounded in 1 cubic metre of concrete"...

---

### Post by diatribe on 2007-06-19
stopping your machine from functioning isnt what I would consider a security tip

---

### Post by yabbadabbadont on 2007-06-20
> **diatribe said:**
> stopping your machine from functioning isnt what I would consider a security tip

Sure it is.  If it doesn't boot, it can't be hacked (remotely).  ;)  :D

---

### Post by Bachstelze on 2007-06-20
SSH ? su ?? Those aren't installed by default in Ubuntu ! And if someone installs them, he's supposed to know how they work and how to configure them the way he/she wants.

---

### Post by yabbadabbadont on 2007-06-20
> **HymnToLife said:**
> SSH ? su ?? Those aren't installed by default in Ubuntu ! And if someone installs them, he's supposed to know how they work and how to configure them the way he/she wants.

su *is* installed by default, even if you only install ubuntu-minimal and ubuntu-standard.  Just FYI.  ;)

---

### Post by Cheese Sandwich on 2007-06-20
> **OzzyFrank said:**
> Yeah, thought I might see something like that... not the first time I would have seen security tips that limit access to your system a little bit too much, hehehe! What's next? "Never connect to the internet, and preferably have your PC surrounded in 1 cubic metre of concrete"...

I think that was the whole purpose of Microsoft's "blue screen of death" - it was a security feature. What's a hacker going to do then, come along & fix your computer? ;)

---

### Post by gaten on 2007-06-21
I wasn;t too impressed with that article; sure, it's great to learn and constantly improve security, but phrases like "install the following software: grsecurity" make me laugh. Grsecurity is *great*, but I don't think this guide gives you a very good idea just how difficult it is to "just install" that particular software. Also, which I agree with this:

>  Disabling SSH root login, in the *default* Ubuntu install this is completely unnecessary, as the is no root account! You can't login to an account that doesn't exist ;)

They say to restrict the /home directory, which I agree with, but if that is done then you should change the whole umask value to continue using those restrictive permissions. 

Overall, I think the article is good for either listing what should be done or at least something to get you interested/reading up on security. However, the offhanded way it brushes through installing PAX and grsec and so on leads me to believe this was a "look at me!" article rather than a serious attempt to help you secure you machine.

---

### Post by piobair on 2007-06-21
I have been taught that SUDO is a great evil. NSA and the Linux community have gone to great lengths to separate root from user. SUDO relinks administrator privileges with user.If you are  connected to the Internet, your user password can (eventually) be cracked. If SUDO is disabled, cracking your user password will not accomplish anything.

---

### Post by ipsi on 2007-06-22
Yes, but they first have to guess your user account name. If root is enabled then all they already know the user name, making life much easier for them. I've noticed this with random hack attempts on my box, as the attackers always try root, but since it is disabled they're restricted to trying another account, and since they're unlikely to guess my user name, they've got a really hard job.

---

### Post by yabbadabbadont on 2007-06-22
Just configure iptables to silently drop all incoming connections.  Then they won't have any (easy) way into your system in the first place.

---

