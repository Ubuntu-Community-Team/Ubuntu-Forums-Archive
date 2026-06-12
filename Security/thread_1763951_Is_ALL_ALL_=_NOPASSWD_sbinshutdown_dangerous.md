---
title: "Is ALL ALL = NOPASSWD: /sbin/shutdown dangerous?"
date: 2011-05-21
forum: Security
---

### Post by eddie3000 on 2011-05-21
Well, that's the question. 

I have my computer running ubuntu at home, only my wife and I have physical access to it. It's connected to the internet when it's turned on.
I set it up so it does a data backup before shutting down. With help from other forum members I wrote a script that does this, and to avoid having to type in a password I edited the sudoers file. Does this pose a security risk? 
Anybody can shutdown the computer from gnome without a password, why do you need to be root in terminal to do so?

---

### Post by Joe of loath on 2011-05-21
Considering anyone can shut the PC down anyway, it's not too big of a deal.

---

### Post by eddie3000 on 2011-05-21
And how much of a deal is it?

---

### Post by Joe of loath on 2011-05-21
Well, how worried are you about people pressing the button on the box? :lol: It's not reachable remotely unless you have VNC or ssh with no password or key authentication, and if you have that enabled there are bigger problems to think about.

---

### Post by eddie3000 on 2011-05-21
Well I won't worry too much then. But I do have teamviewer and use it from time to time, with a password of course. I'll just pray and hope it's ok then.

---

### Post by JRV on 2011-05-21
You can change the permissions for the shutdown command and allow anyone to use it with this command:
```
sudo chmod u+s /sbin/shutdown
```

---

### Post by Lars Noodén on 2011-05-21
> **JRV said:**
> You can change the permissions for the shutdown command and allow anyone to use it with this command:
```
[s]sudo chmod u+s /sbin/shutdown[/s]
```

Yes that's another way to do it, if you keep in mind that [SUID](http://unix.worldiswelcome.com/why-suid-programs-are-dangerous) is considered quite [unsafe](http://www.net-security.org/article.php?id=92). The use of sudo to allow shutdown is the more acceptable way.

---

### Post by eddie3000 on 2011-05-21
Thanks guys for your answers. :D I'll stick to what I've got then for the time being until I learn about something better. Who knows? Maybe Ubuntu in the future will incorporate a backup feature like the one I've set up that makes things easier for unexperienced people like myself.

---

### Post by eddie3000 on 2011-05-31
I am a newbie so maybe what I am asking is silly. Would it be safer to restrict the nopasswd to a specific user and nobody elsel? How could that be done? Like this? (just guessing)

user none = NOPASSWD: /sbin/shutdown

---

