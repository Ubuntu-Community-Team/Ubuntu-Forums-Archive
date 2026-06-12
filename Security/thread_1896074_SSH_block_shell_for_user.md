---
title: "SSH: block shell for user"
date: 2011-12-16
forum: Security
---

### Post by habr on 2011-12-16
Hello,  wanna block shell for ssh-user. tried to change DSHELL=/usr/sbin/nologin  and     DSHELL=/bin/false in /etc/adduser.conf The result is - ssh connection is dropping after log in/  What should I do?

---

### Post by Lars Noodén on 2011-12-16
Can you explain a little more what it is that you want to prevent and what you want to allow?

---

### Post by habr on 2011-12-16
sorry for my poor english
 I have an SSH server and wanna use it to make secure channel for RDP sessions.
I want to prevent from using shell on SSH server, user must just log in without having shell access.

so, to block shell I tried to clear the last param in user's string in /etc/passwd - the system still giving the default shell to user. tried to type in "/sbin/nologin" or "/usr/sbin/false" there - the ssh session is dropping after loging in.

---

### Post by habr on 2011-12-16
after logging in user must have the black window without command prompt

---

### Post by Lars Noodén on 2011-12-16
That should be /bin/false instead of /usr/sbin/false, the latter does not exist.

Then try connecting with the -N (capital N) option in addition to any other options you might be using. That will keep SSH from executing a remote shell.

---

### Post by CharlesA on 2011-12-16
> **Lars Noodén said:**
> That should be /bin/false instead of /usr/sbin/false, the latter does not exist.

Then try connecting with the -N (capital N) option in addition to any other options you might be using. That will keep SSH from executing a remote shell.
I haven't tried it that way, but that might work.

It would be easier to just do something like this:
[http://ubuntuforums.org/showthread.php?t=1766417](http://ubuntuforums.org/showthread.php?t=1766417)

---

### Post by Lars Noodén on 2011-12-16
> **CharlesA said:**
> I haven't tried it that way, but that might work.

-N works just fine.  The account won't show up as logged in if you look with [w](http://linux.die.net/man/1/w), though.

---

### Post by habr on 2011-12-16
Thanks for reply
I'll try it shortly and post the results

I use Windows PuTTY to connect to SSHserver

---

### Post by bodhi.zazen on 2011-12-16
-N works, but relies on the user.

I suggest ssh keys with forced commands ;)

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

Scroll down to forced command section.

---

### Post by fdrake on 2011-12-16
this should be enough without touching the/etc/passwd file:
```

#cat > /etc/nologin

```
no-root users won't be able to login(both locally and remotly)
see "man nologin"

---

### Post by matt_symes on 2011-12-16
Hi

> **bodhi.zazen said:**
> -N works, but relies on the user.

I suggest ssh keys with forced commands ;)

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

Scroll down to forced command section.

I have to concur with bodhi's suggestion. 

The book is a great read as well; an SSH tour de force. I would highly recommend reading it.

Kind regards

---

