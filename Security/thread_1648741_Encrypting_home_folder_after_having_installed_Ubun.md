---
title: "Encrypting home folder after having installed Ubuntu"
date: 2010-12-19
forum: Security
---

### Post by Toxicbits on 2010-12-19
In my opinion there should be a tool installed in Ubuntu by default which lets the user easily encrypt his home folder. One is given the option in the installed, but if one decides to encrypt his folders afterwards that's quite hard to achieve.

Please correct me if I'm wrong but I think there's no easy way to achieve that

Or would that be unnecessary?

Toxcibits

---

### Post by bodhi.zazen on 2010-12-19
Only you can decice what is necessary to encrypt. You can encrypt directories very easily via a number of techniques, if you want a graphical interface, try cryptkeeper (it is in the repos).

If you want to encrypt the entire home directory you will need to either configure ecrpytfs or re-install, whichever you find easier.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by FuturePilot on 2010-12-19
> **Toxicbits said:**
> In my opinion there should be a tool installed in Ubuntu by default which lets the user easily encrypt his home folder. One is given the option in the installed, but if one decides to encrypt his folders afterwards that's quite hard to achieve.

Please correct me if I'm wrong but I think there's no easy way to achieve that

Or would that be unnecessary?

Toxcibits

```
ecryptfs-migrate-home
```

I'd back everything up first just in case though.

---

### Post by bodhi.zazen on 2010-12-19
> **FuturePilot said:**
> ```
ecryptfs-migrate-home
```

I'd back everything up first just in case though.

Nice one !!!

---

### Post by FuturePilot on 2010-12-19
> **bodhi.zazen said:**
> Nice one !!!

Thanks. :)
Apparently that script has been around for a while but I just found it recently.

---

### Post by Toxicbits on 2010-12-19
Ok, thanks

Toxicbits

---

### Post by R Smit on 2011-01-05
Have been looking for this a long time!
However:

"/home/myname appears to be encrypted already"  and I am sure it is NOT.
What to do next?

---

### Post by Dave_L on 2011-01-05
R Smit: Do /home/myname/.ecryptfs, /home/myname/.Private or /home/.ecryptfs/myname already exist?

---

### Post by R Smit on 2011-01-05
> **Dave_L said:**
> R Smit: Do /home/myname/.ecryptfs, /home/myname/.Private or /home/.ecryptfs/myname already exist?

Yes! You are right, that was the problem.
Thank you.

---

### Post by abum on 2013-01-06
If /home/myname/.ecryptfs, /home/myname/.Private or /home/.ecryptfs/myname already exist, did you delete them or how were you able to eventually make sure the home folder is encrypted?
I'm having the same problem; thanks!

---

### Post by R Smit on 2013-01-06
> **abum said:**
> If /home/myname/.ecryptfs, /home/myname/.Private or /home/.ecryptfs/myname already exist, did you delete them or how were you able to eventually make sure the home folder is encrypted?
I'm having the same problem; thanks!

It's been 2 years now, but I think I deleted the directories.
To be sure: backup first!

---

