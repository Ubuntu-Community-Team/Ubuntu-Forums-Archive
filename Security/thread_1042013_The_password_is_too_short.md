---
title: "The password is too short"
date: 2009-01-17
forum: Security
---

### Post by gm__ on 2009-01-17
This is the stupidest thing in the world.

The password is too short. So it wont let you to change it.

How do you want an OS to be popular when you cant even do what you want with it?

The writers of Ubuntu have to wake up a little and come down to earth and
stop annoying people with their stupid ideas!

What if i dont want a password at all? Its nobody's business but mine.

---

### Post by HermanAB on 2009-01-17
Gampaw!?  That yoooooouuu!???

---

### Post by The Cog on 2009-01-17
Root can set shorter passwords, like this:
> sudo passwd *username*
but think carefully before doing so. Be very, very wary of installing an SSH server if you have very short passwords. There are lots of brute-force password guessing bots out there.

---

### Post by gm__ on 2009-01-17
Thank you very much!

No its not Gampaw.  :)

---

### Post by lensman3 on 2009-01-17
The passwd program will complain if the password is too short, but just type the short password again and it will accept the short password.

(Which I think is a very good feature.  It tells you that you are being stupid, but lets you go ahead!!!)

---

### Post by superposition on 2009-04-25
> The passwd program will complain if the password is too short, but just type the short password again and it will accept the short password.

(Which I think is a very good feature. It tells you that you are being stupid, but lets you go ahead!!!) 

I agree, however you cannot go ahead if you want to, at least not in 9.04. I had to follow The Cog's instructions to make it work, and as he said be mindful of what the machine you are doing this to will be doing.

---

### Post by lensman3 on 2009-04-25
If you are using passwd to change the password at a terminal prompt, then when it tells you "the password is too short".  JUST TYPE THE SHORT PASSWORD IN AGAIN. And it will accept the shorter password.

(I consider this behavior a very good feature).

---

### Post by etu on 2010-01-23
"If you are using passwd to change the password at a terminal prompt, then when it tells you "the password is too short". JUST TYPE THE SHORT PASSWORD IN AGAIN. And it will accept the shorter password."

No it does not. Just tried in 9.10.

---

### Post by JackRock on 2010-01-23
> **etu said:**
> No it does not. Just tried in 9.10.

Might be a change in 9.10.  Karmic wasn't out yet as of the post prior to yours.

---

### Post by sera75 on 2010-05-09
> **lensman3 said:**
> The passwd program will complain if the password is too short, but just type the short password again and it will accept the short password.

(Which I think is a very good feature.  It tells you that you are being stupid, but lets you go ahead!!!)

This is really the behaviour I would expect too. But they changed it (at least) for 10.04:mad:

---

### Post by Linkz57 on 2010-12-20
> **The Cog said:**
> Root can set shorter passwords, like this:

but think carefully before doing so. Be very, very wary of installing an SSH server if you have very short passwords. There are lots of brute-force password guessing bots out there.


```
sudo passwd *username*
```
I have been looking for this string of code on and off for a year or more. Thank you.

---

### Post by HermanAB on 2010-12-20
OK, now please tell us your IP address so we can add it to our mail server block lists, because pretty soon, your machine will compromised and spouting spam...

---

### Post by theasprint on 2010-12-20
AWW, I had times Ubuntu saying that 

The password is too simple

and repeatedly entering the password again does not help.

* My ubuntu is 10.04 version

---

### Post by Linkz57 on 2010-12-20
> **HermanAB said:**
> OK, now please tell us your IP address so we can add it to our mail server block lists, because pretty soon, your machine will compromised and spouting spam...

Come on, bro, what are the odds ofFREE OTC PILLS SOLVE ALL YOUR PROBLEMS I HAD FRIEND HE TRY IT SAYS ITS GREAT _[CLICK HERE NOW FOR GREAT JUSTICE]("http://linkz57.deviantart.com")_

---

### Post by k66473 on 2011-08-17
"sudo passwd"  how simple could it be. thanks.

---

### Post by bodhi.zazen on 2011-08-17
> **k66473 said:**
> "sudo passwd"  how simple could it be. thanks.

That command does NOT set the user password, it sets a root password, with is probably not what you want.

Should be

```
sudo passwd user_name
```

Also you should know that changing the password with the command line will break ecryptfs (encrypted home), use the graphical tools.

---

