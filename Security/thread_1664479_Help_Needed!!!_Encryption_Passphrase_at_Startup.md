---
title: "Help Needed!!! Encryption Passphrase at Startup"
date: 2011-01-11
forum: Security
---

### Post by jacobroufa on 2011-01-11
I've got a server issue... I helped a friend set up a headless server to do SMB filesharing. Problem is, it keeps asking for an encryption passphrase at startup, before getting to a log in prompt. Now, I've set up servers before, and administered my own SSH, SMB, LAMP, and more for quite some time. So I'm pretty familiar with Linux and Ubuntu in particular. However with this, I'm having trouble because the goal was to let it be headless and plug in just power and ethernet and stick it in a corner somewhere. 

Is there anything I can do to either

A) stop the prompt altogether but keep encryption?
B) create some sort of secure USB key that automatically decrypts when inserted and doesn't allow a full boot without it?
C) stop the prompt and move it to post-login just to decrypt the home directory if needed?
or
D) remove encryption without reinstalling?

I've done some pretty thorough searching and there's plenty of articles and advice on setting up encryption post-install, but not very much on how to remove it once installed and nothing (that I can find) where someone's having the same issue I am.

Also, if this doesn't belong in the Security Discussions forum, please advise where I could post it? This is my first post on UbuntuForums.org so sorry if it isn't the right place. Thanks!

---

### Post by sj1410 on 2011-01-11
removing encryption without reinstalling is not possible but again depends on what partition did you encrypt.

password less encryption is possible but again depends on what exactly you did while installing the system. kindly post the details.

---

### Post by jacobroufa on 2011-01-11
> **sj1410 said:**
> password less encryption is possible but again depends on what exactly you did while installing the system. kindly post the details.

Well, during the install when it asked about the drive setup options, I chose the one that said something to the effect of "use full disk, and encrypt". Passphrase was created there and rest of the install went as normal. What other details can I provide?

---

### Post by sj1410 on 2011-01-11
OK, than this is bit tricky but possible, i have done it so you can. Just follow the procedure


[http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html)

---

