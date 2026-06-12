---
title: "Ubuntu Software password"
date: 2017-10-17
forum: Ubuntu Development Version
---

### Post by ubname on 2017-10-17
I understand that to install snap packages from the ubuntu software (center) you need an Ubuntu One account,
like the one used for this forum am I correct?

Thanks.

---

### Post by ajgreeny on 2017-10-17
Correct.

However, it is much easier as far as I can make out, to use terminal commands for installing or removing snap packages, and I think it avoids the need for the SSO password, though I might be wrong as I have not yet needed or installed any snap packages.

See **man snap** in terminal for all the info

---

### Post by dino99 on 2017-10-17
Have you tested your login password (used to open the session) ?

---

### Post by ubname on 2017-10-17
> **ajgreeny said:**
> Correct.

However, it is much easier as far as I can make out, to use terminal commands for installing or removing snap packages, and I think it avoids the need for the SSO password, though I might be wrong as I have not yet needed or installed any snap packages.

See **man snap** in terminal for all the info

Ok but i do not understand how I logged in Software (never did it myself),

When logged in, how to log out ?

thanks

---

### Post by ubname on 2017-10-17
> **dino99 said:**
> Have you tested your login password (used to open the session) ?

No, of what session(?) are we talking about?

thanks

---

### Post by dino99 on 2017-10-17
> **ubname said:**
> No, of what session(?) are we talking about?

thanks

when you start ubuntu, then you are asked a password to get the desktop; which is called a 'session'.

---

### Post by ubname on 2017-10-17
> **dino99 said:**
> when you start ubuntu, then you are asked a password to get the desktop; which is called a 'session'.

Ok, i'm actually talking about the software session used to install software,
how can I log out of that ?

I hope it's more clear :)

Thanks

---

### Post by dino99 on 2017-10-17
simply close it, hitting the top right 'red x' icon; password is only asked for loading/opening.

---

### Post by ubname on 2017-10-18
Ok thanks, to me it seems that the Software auth and Software itself are quite unstable ...

---

### Post by dino99 on 2017-10-18
many users, like me, prefer using 'synaptic'

---

### Post by ajgreeny on 2017-10-19
> **dino99 said:**
> many users, like me, prefer using 'synaptic'
+1
If I use a GUI for package management it is always synaptic.  In my 12 years of using Ubuntu I have never once used the software centre, or the variations of it that are now available..
Give synaptic a try and you will probably not regret the move.

---

### Post by ubname on 2017-10-19
Thanks, anyway i was not looking for an alternative for software but i'm trying to understand how
the auth mechanism works to install snap packages and what are the implications of using an
ubuntu one account in software.

I know synaptic but i dont think it can manage snap packages (?)

---

### Post by dino99 on 2017-10-19
note that snap project is quite young, and there are many bugs reported against it. Too young to be seriously used itself; and mixing with that buggy software manager can only give random results.

---

### Post by howefield on 2017-10-19
You might be interested in browsing through this bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1581713](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1581713)

---

### Post by ubname on 2017-10-19
Ok now it's more clear thanks!

---

### Post by ventrical on 2017-10-19
> **ubname said:**
> Ok now it's more clear thanks!

Yep .. for snap packages you need SSO - but as howefield pointed out bug..

---

### Post by grahammechanical on 2017-10-19
The snap store is also used with Ubuntu Core which is a snap based OS.

A Single Sign On account will allow a developer to load snaps into the snap store as well as install snaps from the store onto Ubuntu Core installed on a device. So, that is another reason for a password into the snap store. 

Installing Ubuntu Core will require a Single Sign On account and a SSH key imported into our Launchpad account. The first boot after installing Ubuntu Core requires that we go through a set up routine which includes putting in our Single Sign On email address. The set up process then fetches the SSH key from our launchpad account and uses it to create a user account for Ubuntu Core. We then use the reference that is given by the set up process to login to Ubuntu Core. Updates and the installation of snap apps is then done through the snap store.

Or that is the theory. In my experiments I finally managed to get Ubuntu Core installed on a second hard drive and I completed the set up process but the install fails to load to a login. I am hoping that things will improve as Ubuntu Core is upgraded. It is based on 16.04 code.

My idea was to test if GUI snaps would run on command line Ubuntu Core without a user interface such as Unity 8. We are beginning to get some desktop type snaps in the snap store. Such as Chromium & Libreoffice. There is even a snap for the Gnome 3.6 stack. I wanted to see how far I could to get to transfer the command line Ubuntu Core into a highly secure desktop-like OS.

Regards.

---

### Post by Chanath on 2017-10-19
@Graham

Where did you install Ubuntu Core? Can it be installed in a normal laptop? If so, how did you go about it?

---

### Post by cariboo on 2017-10-20
Closed as this thread has been marked solved, and Artful has been released.

---

