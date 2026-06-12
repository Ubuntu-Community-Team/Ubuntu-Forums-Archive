---
title: "Medusa says router password is found when it isn't"
date: 2011-12-05
forum: Security
---

### Post by ShadowTek on 2011-12-05
When I test my router with the wrong password, medusa says "success". What am I doing wrong?

This is the first time I've used medusa, so I may be missing something simple.

```
~$ medusa -h 192.168.1.1 -u admin -p wrongpassword -M http
Medusa v2.0 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

ACCOUNT CHECK: [http] Host: 192.168.1.1 (1 of 1, 0 complete) User: admin (1 of 1, 0 complete) Password: wrongpassword (1 of 1 complete)
ACCOUNT FOUND: [http] Host: 192.168.1.1 User: admin Password: wrongpassword [SUCCESS]
```

---

### Post by dd76 on 2011-12-06
I may be misunderstanding but isn't Medusa a brute force password cracker for gaining access to a router?  Were you trying to test the router using Medusa?    I have no experience with Medusa but I have had a router do the same thing.  An old Netgear I had would take any password entered, I flashed the firmware and reset it but it still didn't work Netgear finally replaced it.  I have long suspected that it had gotten surged due to a storm before the problems but since nothing else on the same surge protector was damaged I was never sure.

---

### Post by ShadowTek on 2011-12-06
Yes, I am trying to use Medusa to brute-force a friend's router. They forgot the password, and I wanted to take the opportunity to do some testing and learn a few things.

Anyway, I don't know what the admin password is, but Medusa is saying success for any password that I try. When attempting a failed login with my browser, a 401 page is being returned upon failure, so the fact that a page *is* being returned might be confusing Medusa, but that's just a wild guess.

```
<HTML><HEAD><TITLE>401 Unauthorized</TITLE></HEAD> <BODY BGCOLOR="#cc9999"><H4>401 Unauthorized</H4> Authorization required. </BODY></HTML>
``` There may be some module option that I need to use, but I'm not sure what the deal is.

---

### Post by /dev/random/username on 2011-12-06
Have you tried reseting the router?

Usually after reset the login/password should be admin/admin depending on the router.

---

### Post by N00b-un-2 on 2011-12-06
> Have you tried reseting the router?
I'm pretty sure the OP's intent is to learn how to brute force crack the router, not to simply reset.  How would the OP learn anything by just hitting reset?

I'm pretty sure that tools like hydra and medusa require a dictionary of terms to query for each variable: Host, login and password.
So the fact of the matter is, the program itself is particularly limited in its function, but could be used along with a brute force cracking algorithm (which I think medusa can use by invoking the '-x' argument), but the issue therein lies in the fact that virtually all devices now have a built in lock out which will not allow access once a certain number of failed logins  is met (typically 3 or five).  Not to mention the fact that it could literally take a supercomputer weeks to successfully crack a password and login using such a brute force attack.  Hypothetically, it could be done even on a regular computer but it might take literally months or even years.

Here, watch this video of this guy doing exactly what you're attempting to do.  Watch what he types in the terminal to query his dictionary terms.

[http://www.youtube.com/watch?v=WTpjaYxbITw](http://www.youtube.com/watch?v=WTpjaYxbITw)

---

### Post by ShadowTek on 2011-12-06
Yes, I can reset the router, but I'm trying to take the opportunity to learn a little about brute-force attacks. It's also possible that the router has some non-standard default password that I could find by downloading the manual, but that's cheating. :)

Medusa allows for testing command-line specified passwords with -p, or a text file password list with -P. I saw a link to a 3.5 gigabyte txt file as a password list resource, so I guess that's what I'd need to get ahold of if I wanted to do something real.

I understand that "good" passwords are difficult to crack, but I'd like to try a simple dictionary attack and see if that works, since most people *do* use sucky passwords.

Failed-login lockouts will of course put and end to any fooling around, but I might get lucky with this older router.

Thanks for video link. I'd watched it once before, but I missed the module option that seemed to solve my problem.
```
-m DIR:GET/index.asp
```That's not in the man page, so I'll have to find more documentation about it, but using it did eliminate the false positive that I was seeing. Of course I'd need to know the correct password to make sure it's now working properly, but at least I'm making progress. :)

---

### Post by N00b-un-2 on 2011-12-06
I'm glad to be of help!

---

