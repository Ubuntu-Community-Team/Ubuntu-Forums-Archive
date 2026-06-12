---
title: "Is Puppy Linux secure ?"
date: 2019-05-11
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2019-05-11
As you know Puppy Linux is a single user system and that user is root.

Is Puppy Linux  secure as a daily driver ?

---

### Post by #&amp;thj^% on 2019-05-11
Secure in what way? It runs in RAM.
Your scripts of whatever kind for whatever reason (we still aren't specific) are likely not going to jump your RAM. Therefore I'd say that Puppy beats most other distros with security on steroids.

---

### Post by Rubi1200 on 2019-05-11
Depending on what you are looking for/trying to achieve there are plenty of options in terms of security and/or privacy:
[https://distrowatch.com/table.php?distribution=tails](https://distrowatch.com/table.php?distribution=tails)
[https://distrowatch.com/table.php?distribution=kodachi](https://distrowatch.com/table.php?distribution=kodachi)

There are other distros in the category security on Distrowatch but I did not add the ones aimed at penetration testing since I do not know if that is what you want/need.

As 1fallen mentioned, Puppy runs in RAM. Have not used it for a long time but my impression from the distro and the forum is that usage is secure.

Hope this helps.

---

### Post by ajgreeny on 2019-05-11
I have only ever used Puppy as a live system.
I know it can be installed to hard disk, but I have never done, and therefore I am  not aware if it is possible to create a user who does not run as root when installing.

Perhaps it's worth investigation that possibility.

---

### Post by #&amp;thj^% on 2019-05-11
More to think about with puppy thanks to ajgreeny:
An important security feature of Puppy is that (in a 'frugal' installation, which is preferred/recommended) each session can be either saved or not, to either a standard or unique file, so it's possible to run 'bespoke' sessions for specific purposes, requiring logout/login to return to 'normal' use. Restricted user accounts can also be added, for specific purposes. Given that a frugal install is effectively a 'live' system, Puppy may actually be more secure than 'normal' Linux, if used correctly.

References:

[http://www.ciphersbyritter.com/COMPSEC/ONLSECP5.HTM](http://www.ciphersbyritter.com/COMPSEC/ONLSECP5.HTM)

[http://www.murga-linux.com/puppy/viewtopic.php?t=18639](http://www.murga-linux.com/puppy/viewtopic.php?t=18639)

Notes

While we recommend frugal or USB installations the choice is entirely yours.
A "pupsave" folder can only be created on a linux filesystem. This allows you to store as much space as your partition can hold.

Puppy Linux is mostly used by programmers, systems administrators and analysts for their daily computing needs doing things like...
[list]
    [*]Internet access of dozens of websites simultaneously from several machines/user.
    [*]Developing software in almost any language ever invented.
    [*]Experimenting with endless permutations and combinations of software configurations.
    ... and even checking email and social media while answering questions here.[/list]
This shoots all my knowledge of Puppy.
Hope it helps.
Rubi1200 mentions Kodachi and I really like it for my privacy needs also.
Play around with a few of the mentioned.

---

### Post by Irihapeti on 2019-05-11
I used to be an enthusiastic Puppy Linux user some years back. From what I observed at the time, the number of people complaining about security problems was about the same as we'd see on these forums. In other words, though running as root was supposed to be less secure, in practice, it didn't seem to make any difference.

Keep in mind, though, that it's a desktop distro. I don't think that running it on a server would be a great idea.

---

### Post by LwIh%*7 on 2019-05-11
That depends on **"your" **definition of secure. As usual its built on top of the Linux kernel which devs praise it for being secure in general as for the operating system Puppy Linux I've heard that its mainly for hobbyist but to make it secure in my view all you need is a reliable firewall installed an activated at boot like for example UFW which is already installed on Ubuntu but not active by default. If you are concerned for people (e.g governments) snooping into your system or hackers and you want to remain anonymous then I don't think that the system is for you in fact you should use a system that has the network anonymized out of the box like Tails or Whonix which tries to be secure. Though that being said is your choice!

---

