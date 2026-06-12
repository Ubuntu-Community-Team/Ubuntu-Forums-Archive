---
title: "[SOLVED] Making PAM use SHA512 instead of MD5"
date: 2008-09-19
forum: Security
---

### Post by CaptSaltyJack on 2008-09-19
A glance into /etc/pam.d/common-password shows this line:

```
password   requisite   pam_unix.so nullok obscure md5
```

Given all the talk lately of MD5 and SHA1 being somewhat insecure, I'd rather use something else like SHA512 or Whirlpool (preferably!).  How can I safely do this and "upgrade" all my users' passwords to the new hash algorithm?  And where the heck are the encrypted passwords stored these days, anyway?  /etc/passwd used to be it, but that shows nothing relevant.

Thanks.

---

### Post by cdenley on 2008-09-19
> **CaptSaltyJack said:**
> A glance into /etc/pam.d/common-password shows this line:

```
password   requisite   pam_unix.so nullok obscure md5
```

Given all the talk lately of MD5 and SHA1 being somewhat insecure, I'd rather use something else like SHA512 or Whirlpool (preferably!).  How can I safely do this and "upgrade" all my users' passwords to the new hash algorithm?  And where the heck are the encrypted passwords stored these days, anyway?  /etc/passwd used to be it, but that shows nothing relevant.

Thanks.

I think I saw a bug a while ago about SHA1 not being supported in pam. If that is correct, I don't think SHA512 will work either. I could be mistaken, though. I want pam support for the blowfish algorithm.

edit: Wow, there is support for blowfish!
```

sudo apt-get install libpam-unix2

```

Passwords are stored in /etc/shadow.
```

sudo getent shadow CaptSaltyJack

```
You should be able to change the algorithm in pam, and your old hashes should still work. The passwords would be stored using the old algorithm until you reset them.

---

### Post by CaptSaltyJack on 2008-09-19
But isn't Blowfish 2-way encryption?  Isn't it better to use hashing (1-way) for passwords?  Whirlpool is my hash of choice, but I doubt PAM supports it.

PS, thanks for the tip on the shadow file.

---

### Post by cdenley on 2008-09-19
> **CaptSaltyJack said:**
> But isn't Blowfish 2-way encryption?  Isn't it better to use hashing (1-way) for passwords?  Whirlpool is my hash of choice, but I doubt PAM supports it.

PS, thanks for the tip on the shadow file.

I think you might be right. I'm not sure. I'm still playing around with the pam settings seeing what linux can do.

---

### Post by cdenley on 2008-09-19
For getting blowfish to work
[http://ubuntuforums.org/showthread.php?t=300208](http://ubuntuforums.org/showthread.php?t=300208)
I always assumed it was very secure because it is used by OpenBSD. I'm not a cryptography expert, though. The poster in that thread seems to think it's better than MD5.

---

### Post by CaptSaltyJack on 2008-09-19
I'm no crypto expert either, but Blowfish is absolutely more secure than SHA1 or MD5.  The thing is, theoretically, someone could take /etc/shadow and decrypt passwords since Blowfish is 2-way encryption, whereas MD5/SHA1/SHA512/Whirlpool/etc are 1-way encryption.  Of course, the likelihood of someone cracking Blowfish encrypted passwords is pretty small.

Still, though, I vote that whoever is behind PAM implements Whirlpool hashing.  Whirlpool is the sh*t!

---

### Post by CaptSaltyJack on 2008-09-19
PS: Why Whirlpool blows MD5/SHA1 away:

```

$ php -a
Interactive shell

php > print md5('my password');
329670c3265b6ccd392e622733e9772f
php > print sha1('my password');
a2f8f7fa195a080a22a689041daa8f2044f9f336
php > print hash('whirlpool', 'my password');
f00fec1f21606d51fdf9358f27f54ef131e1f78c11c639d13e8be402e0137c42634d97edc5a43b0822c3312e3c86703d93f5f15493ef94a70cf3f85615a457a6

```

Of course, SHA512 is certainly no laughing matter either. :)

```

php > print hash('sha512', 'my password');
e28bdbf8faa97dab2203fcc89e397a4bf8d4a5b370421e5481a55f317caee4f81be5a810bb1cffc4695c32198717b9a6e835895852ee3a8689d0963463f2db15

```

---

### Post by cdenley on 2008-09-19
This will help you identify which algorithm you hashes actually use
[http://people.redhat.com/drepper/SHA-crypt.txt](http://people.redhat.com/drepper/SHA-crypt.txt)

---

### Post by cdenley on 2008-09-19
> **CaptSaltyJack said:**
> PS: Why Whirlpool blows MD5/SHA1 away:

```

$ php -a
Interactive shell

php > print md5('my password');
329670c3265b6ccd392e622733e9772f
php > print sha1('my password');
a2f8f7fa195a080a22a689041daa8f2044f9f336
php > print hash('whirlpool', 'my password');
f00fec1f21606d51fdf9358f27f54ef131e1f78c11c639d13e8be402e0137c42634d97edc5a43b0822c3312e3c86703d93f5f15493ef94a70cf3f85615a457a6

```

Of course, SHA512 is certainly no laughing matter either. :)

```

php > print hash('sha512', 'my password');
e28bdbf8faa97dab2203fcc89e397a4bf8d4a5b370421e5481a55f317caee4f81be5a810bb1cffc4695c32198717b9a6e835895852ee3a8689d0963463f2db15

```

I'm not sure the size of the hash is a direct indicator of the strength, but I'm sure it is a factor. Here is blowfish vs md5

blowfish: $2a$05$8lNnqkSq5R8BfMNZLIJxA.pbWvHHvn3y813YWvLrz7mFPYCOYqMA2
md5: $1$jmG9uZUU$j2diNHCtKEC/0KLchlw96.

---

### Post by CaptSaltyJack on 2008-09-19
How did you get the $1$ in your MD5 hash?  My Linux md5 command won't do it, neither will PHP.

---

### Post by cdenley on 2008-09-19
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786)
SHA512 is supported for intrepid.

---

### Post by CaptSaltyJack on 2008-09-19
Nice find!

---

### Post by cdenley on 2008-09-20
> **CaptSaltyJack said:**
> How did you get the $1$ in your MD5 hash?  My Linux md5 command won't do it, neither will PHP.

Those hashes were taken from my /etc/shadow file. They're not my real passwords, of course, just a test user I set up temporarily.

---

### Post by cdenley on 2008-10-07
I just upgraded to intrepid today. Pam uses sha512 by default. All I had to so was "sudo passwd cdenley", re-enter my password, and now I'm using sha512.

---

### Post by CaptSaltyJack on 2008-10-07
Beautiful - nice to see the Ubuntu team is on top of things!

---

