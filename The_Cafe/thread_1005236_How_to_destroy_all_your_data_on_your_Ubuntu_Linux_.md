---
title: "How to destroy all your data on your Ubuntu Linux system!"
date: 2008-12-08
forum: The Cafe
---

### Post by sulekha on 2008-12-08
Hi all,

 found  an interesting link here:

 [http://www.ubuntu-unleashed.com/2008/03/how-to-intentionally-screw-up-and-wipe.html]("http://www.ubuntu-unleashed.com/2008/03/how-to-intentionally-screw-up-and-wipe.html")

---

### Post by Dr Small on 2008-12-08
Yes?
We know about all these commands, and they are only dangerous if used incorrectly and proper privileges have been acquired; Unlike "format c:" on Windows, which requires no special privileges at all, to erase the hard drive.

---

### Post by bodhi.zazen on 2008-12-08
There are many more tools then those, some are more complete then others.

---

### Post by sulekha on 2008-12-09
> **Dr Small said:**
> Yes?
We know about all these commands, and they are only dangerous if used incorrectly and proper privileges have been acquired; Unlike "format c:" on Windows, which requires no special privileges at all, to erase the hard drive.


 is there any way to prevent the execution of these commands, just as we use
iptables to block sites

---

### Post by mentallaxative on 2008-12-09
> **sulekha said:**
> is there any way to prevent the execution of these commands, just as we use
iptables to block sites

Educate yourself on them and don't run unfamiliar code from questionable sources. Unfortunately it's harder to protect ignorant users against themselves than from malicious outsiders.

---

### Post by eldragon on 2008-12-09
after reading that.. i can safely say im qualified to run a blog.....and my dog is......and.....well.

---

### Post by sdowney717 on 2008-12-09
a malicious script that asks for your sudo password could wipe out your system. 
Maybe we will see more of this if linux gets a lot more popular on the desktop.

How about a blacklisted command list that when one of these commands tries to run it is compared to the list and stopped?

---

### Post by Johnsie on 2008-12-09
This is exaclty why you should be MORE THAN careful when installing debs you download of the web. It would be very easy for someone to include a post installation script that wipes your sytem or does something else that isn't good for your computer (ie. spyware, botnet etc).  You've given the deb root access to your system, it can do whatever the hell it wants. People seem to think that Ubuntu is invulnerable. Anyone who thinks that is naive. Ubuntu is only as secure as the person who has sudo. Statistically you are less likely to get hit than on Windows (at the moment) but that doesn't mean the problem/vulnerability does not exist, it just means few people have bothered exploiting it so far.

---

### Post by bodhi.zazen on 2008-12-09
> **sulekha said:**
> is there any way to prevent the execution of these commands, just as we use
iptables to block sites

There are 2 methods of prevention :

1. Education. As has been stated do not run commands if you are unfamiliar with them. We try to "police" these forums and remove potentially harmful commands ...

2. The only other option is Apparmor, which would restrict access outside of home.

Truth is, however, if someone has physical access there is not much you can do.

---

### Post by koenn on 2008-12-09
> **sulekha said:**
> is there any way to prevent the execution of these commands, just as we use
iptables to block sites

> **sdowney717 said:**
> How about a blacklisted command list that when one of these commands tries to run it is compared to the list and stopped?

dd is a very useful command, often used in procedures for disk cloning, creating disk images, moving physical servers to virtual machines, dumping a CD to disk for editing / remastering, and a number of more exotic uses.

blocking or blacklisting it would make a useful tool inaccessible when you need it. A blacklist with a backdoor for legit use already is in place : its what sudo does.

And even if you'd blacklist dd, there's tons of commands that can be abused in a similar way. If you blacklist all those as well, you won't have an operating system left.

---

