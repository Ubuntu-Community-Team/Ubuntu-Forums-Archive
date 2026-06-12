---
title: "Setting up mail servers"
date: 2011-02-24
forum: Server Platforms
---

### Post by zander x on 2011-02-24
Hello,

This probably isn't the right place, but I figure someone here can point me in the right direction.

How do you setup send and receive mail servers using Webmin under Ubuntu 10.04? There's so many options and choices that I don't know where to start. I'm trying to use PostFix for send and Dovecot for receive but Dovecot has decided to go on strike and won't work. Help help help. Thanks!

---

### Post by HermanAB on 2011-02-25
Howdy,

Setting up a Lego mail server with postfix, dovecot, apache, spam assassin, clamav etc is a good way to learn about mail servers, but if you want some thing that is easier and which has a proper database backend, go here:
[http://citadel.org](http://citadel.org)

Citadel is a complete system with an Easy Install script that runs in about 20 minutes.  It is the easiest Linux mail system, guaranteed.

---

### Post by elico on 2011-02-25
really recommend you on this manual:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

one of the best that will give you what you need.
also if you want more then you can look at 
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
but there is one line of settings missing\broken in it.
also the best i have ever had is:
[http://www.kernel-panic.it/openbsd/mail/mail1.html](http://www.kernel-panic.it/openbsd/mail/mail1.html)

the only different from openbsd is how to install the software (using apt-get).

---

### Post by zander x on 2011-02-27
I appreciate the help!

I tried Citadel: the install was nice and automated, but I can't get in or do anything. I can't even figure out where the program installed itself. The cursor is just blinking as if to say "well, what do you want me to do?"

Now I am trying the link on ubuntu.com... actually those directions don't work because I get Citadel every time...help... why does this have to be so difficult?

---

