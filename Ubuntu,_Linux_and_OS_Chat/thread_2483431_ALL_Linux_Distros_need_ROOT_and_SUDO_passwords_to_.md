---
title: "ALL Linux Distros need ROOT and SUDO passwords to be set in the installation"
date: 2023-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by llifandd on 2023-01-30
I use Debian (Ubuntu) on most things with Mint etc. on a few other things... and one of the issues that arise is the setting up of root and sudo passwords, after the installation AND it only comes about after the need to do it arises, usually while installing specialist software, or when needing to do specific programming or editing or administrative tasks.

These settings need to be made at the very start, when installing the operating system, to save the "Oh my god - what do I do now" events down the track.

It needs to be adopted across all Linux systems - upon the install and it needs to be made known, with the installation instructions.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As a side note - This is one of the very few postings about this entire issue. It's also from 2011 - that is 11 years old......

And technically - it's OK, but for systems operations, it's no longer good enough to NOT be able to set this up on the install, or to lack instructions on how too, with the OS... 

AND having to go online and look it up and find it, - it's one of the many downfalls of the Linux coders / software makers; is that while the "good old days" where a main program was on one site and the bits that went with it were on other sites and the instructions were else where, for all the bits, these are such bad practices - and instead of 10,000 people being able to "Click = Install" of the entire program off one site, the 10,000 people have to spend hours link hopping through forums and comments and multiple websites - it's just wastes enormous amounts of everyone's time - which makes some aspects of Linux a huge time wasting pain in the neck, 

This issue with setting up the passwords for SUDO and ROOT - and the failure to facilitate this right at the very start and to have the instructions with the OS in a text file, also falls into that category.

It's time for this issue to be adopted across ALL Linux variants......

<Snip>

Edit by QIII:  Please refer to oldfred's post below for Forum Rules regarding root and sudo.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

What makes these forums so sucky is that all the NOSEY admins and their morals and lecturing and their "You can post this, but you cannot post that" - and then editing other peoples posts - it's just like a big dysfunctional and incestious family.

It's people like you and the general rudness and bad manners and interfering with how others express themselves, is the reason why people leave and the forums become a concentration of nastiness - of the admins / moderators and their toadies.

I am leaving.

---

### Post by oldfred on 2023-01-30
You should not be using root password.
Most Windows users then do not leave root & leave system insecure. 

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by agentl074 on 2023-01-30
That's why we have sudo ;) ... and you can always change your account settings -- names and passwords graphically or via terminal -- but always keep the former passwords since the keyrings occasionally ask for the previous password!

---

### Post by QIII on 2023-01-30
> It needs to be adopted across all Linux systems

No. It doesn't.  Distributors are free to do as they choose.

Personally, I think not having the root account active by default is a good idea.  No matter the distribution, logging in as root is dangerous and should not be habitual.  There is rarely any reason to.  sudo works for 99.99% of anything you would ever want to do.

If you want root activated, you can do it yourself.

---

### Post by ian-weisser on 2023-01-30
I recall seeing similar hyperbole 20 years ago.

Seems like the same answers then apply now: 

- If you want to use root, and you know how to do so, then use a distro that sets a root password.
- If you want to haywire Ubuntu into using root, go right ahead...without us. If you break something, you're on your own.

Ubuntu's target audience is new and unskilled users. Most folks do not appreciate being asked questions that they don't really understand yet have permanent implications. "Grandma, write this down, it's your root password." That's exactly the kind of silliness that other distros did, and why Ubuntu won the distro wars by offering simple, safe, sane, secure defaults...and as few questions on the installer as they can manage.

If you're not a new/unskilled user, then you already know how to do whatever you like.

---

### Post by TheFu on 2023-01-30
I've been a Unix and Linux admin nearly 30 yrs.  I have to say, I prefer NOT having a root account being used and find distributions that use root to be backwards.

There are simple ways to have root access to run commands for setup.

Of course, this is just my opinion, just like the OP is posting his opinion.  Different opinions are allowed. Pick what works for you, but Ubuntu certainly isn't broken because the root account isn't setup to work the way other distros do.  I have lots of opinions on many things in Ubuntu too.  For example, I have no use for nano. I think it is an abomination and should never be installed on any computer, ever, anywhere.  I suspect there are other opinions on that. ;)   Until Canonical comes around to my way of thinking on nano, the first command I'll run on every Ubuntu fresh install will be 'sudo apt purge nano' so I never need to see it.  My system setup automation removes nano too ... while it is setting up my ssh deployment keys, aliases and adding/purging about 30 other software packages.

As others have said, it is trivial to setup root to work like other distros do it, so anyone with the skill to accomplish it, can.  It is 1 command, btw.  Hardly a hardship.  It is easy to automate too.

---

### Post by grahammechanical on 2023-01-30
The installer of both Debian and its fork Devuan invite the user to set a root password as well as a user password. Debian's installation guide says this:

> At installation time, you are asked whether you want to use the root account or not. 

[LIST]
[*]If you want to *(the default)*, you'll be asked to provide a **complex** password for root. *Use a strong one!* 

[*]If not, no root account is enabled and the password of the first user created will be used for administration tasks.
[/LIST]

[https://wiki.debian.org/Root](https://wiki.debian.org/Root)

The Devuan installation guide shows the relevant dialog boxes near the end of the guide.

[https://www.devuan.org/os/documentation/install-guides/ascii/live-gui](https://www.devuan.org/os/documentation/install-guides/ascii/live-gui)

In Ubuntu the first user is effectively the Administrator. We use the Settings utility to add users and we can limit the authority that these users have. I do not see Ubuntu's way of doing this is any less secure for home and business users than the way other distributions do it. And as noted above Ubuntu's way does reduce the number of users who through ignorance mess up the OS.

Regards

---

