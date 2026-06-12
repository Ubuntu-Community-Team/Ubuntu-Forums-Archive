---
title: "Root password for RatelUltra"
date: 2011-02-09
forum: System76 Support
---

### Post by jr223 on 2011-02-09
Hello,

I have been enjoying my Ratel Ultra.
So far it has been a great experince.

Now on to my question.
I noticed when I 1st started up my Ratel and Ubuntu booted there was no request to set the root password,
just to create my own which I did.

It seems that I can install and run things using my id ny guess is I'm using sudo root, but I have not and do not know the root password for the system.

So my questions are as follows.
01. Is it a good idea to set the root password of my system and install apps etc. under root as appposed to my id?
02. If not why?
03. If so how do I go about setting the password?

Thanks
Jeff

---

### Post by iponeverything on 2011-02-09
> **jr223 said:**
> 
So my questions are as follows.
01. Is it a good idea to set the root password of my system and install apps etc. under root as appposed to my id?

you don't need to set the root password - sudo gives you same functionality - the main difference being that sudo grants the authority just for the specific task, whereas becoming root is not task specific and therefor opens the system to accidental damage and malicious evil-doers that may be able to take advantage of the open window.

Applications usually require sudo authority to install so that they will be available to all users on the system and not just the user who installed it. 

> **jr223 said:**
> 
02. If not why?


see above

> **jr223 said:**
> 
03. If so how do I go about setting the password?


Forum CoC prevents answering of this, but answer is not hard to find.

> **jr223 said:**
> 
Thanks
Jeff

---

### Post by jr223 on 2011-02-09
Thanks for the info!

Understood and appriciated.

---

### Post by Dave_L on 2011-02-09
More details are available here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

