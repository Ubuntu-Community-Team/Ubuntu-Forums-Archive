---
title: "sudo:no valid sudoers sources found, quitting"
date: 2010-12-10
forum: Security
---

### Post by proch04 on 2010-12-10
Can't do anything with SUDO. 

I followed the thead posted already [http://ubuntuforums.org/showthread.php?t=1586269]("http://ubuntuforums.org/showthread.php?t=1586269")

Here is what I get as a result:

Sudo: /etc/sudoers is owned by uid 1000, should be 0

sudo: no valid suddoers sources found, quitting

Somebody HELP

---

### Post by bodhi.zazen on 2010-12-10
> **proch04 said:**
> Can't do anything with SUDO. 

I followed the thead posted already [http://ubuntuforums.org/showthread.php?t=1586269]("http://ubuntuforums.org/showthread.php?t=1586269")

Here is what I get as a result:

Sudo: /etc/sudoers is owned by uid 1000, should be 0

sudo: no valid suddoers sources found, quitting

Somebody HELP

You will need to boot to recovery mode and then

```
chown root.root /etc/sudoers
```

Probably occurred as you were running some application with sudo rather then sudo -i or sudo/su rather then gksu

When using a root shell, use sudo -i 
For graphical applications, use gksu (or kdesudo).

See:  [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by proch04 on 2010-12-10
Thank You for your quick reply.

Now, I get the Sudo working but it say

Sudo: /var/lib/sudo owned by uid 1000, should be uid 0
[sudo] password for username:

Then I enter sudo password and it work. 

Should I set /var/lib/sudo to root?


Thanks

---

### Post by bodhi.zazen on 2010-12-11
Did you change the ownership and permissions of your system files ?

It appears you did so now on at least two.

If you did, it is probably easier to back up your data and re-install.

---

### Post by proch04 on 2010-12-11
Not that I know of. I can't really backup anything because my private folder is encrypted and I'm trying to fix  this issue and deal with the encryption issue.

_Background:_ I created a passphrase for my private home where all my work is located. Then after doing some web work, I shutdown my computer. Later, I wanted to do more work and restarted my computer, then I got the message with /var/lib/ICEauthority and others messages about a server. 

So now I'm at the point where there is no message, and I just get the normal startup with ubuntu logo and a splash screen, and that's it. I get an option the shutdown and restart at the lower right hand corner.

---

