---
title: "usermod: unable to lock password file"
date: 2011-10-24
forum: Server Platforms
---

### Post by neal.browning on 2011-10-24
As the title states, I'm trying to use the usermod command to append a group to a users profile. When making the attempt, I get the error *usermod: unable to lock password file*.

I am logged in to the console as root.

This is a server box only. (No GUI installed)

There is a /etc/.pwd.lock file in place. If I delete/move this file out of the /etc directory, the lock file is created as soon as I attempt to run the usermod command.

I'm new to debian/ubuntu distros so hopefully someone can point me in the right direction and help me figure this out.

---

### Post by koenn on 2011-10-24
what command do you run, exactly ?

---

### Post by neal.browning on 2011-10-24
usermod -a -G <groupname> <username>

---

### Post by koenn on 2011-10-24
looks OK.

how did you get root ?

---

### Post by neal.browning on 2011-10-25
Logged in as root via SSH.

---

### Post by koenn on 2011-10-25
strange, 

I can reproduce a 'unable to lock password file' error when I run usermod a.o. as a non-root user, so it looks like a privilege/permission issue on first sight

that, and ubuntu defaults to not having a root user.

I assume you enabled root, or you wouldn't be able to log on as root, right?

---

### Post by neal.browning on 2011-10-25
I inherited this box from a previous sysadmin. 

I'm also assuming root is enabled since I'm logging in as root as I would with any of my (functioning) Redhat boxes.

Any idea what to look for?

---

### Post by koenn on 2011-10-25
> **neal.browning said:**
> 
Any idea what to look for?

the previous sysadmin's phone number ?

---

### Post by koenn on 2011-10-25
> **neal.browning said:**
> I inherited this box from a previous sysadmin. 

I'm also assuming root is enabled since I'm logging in as root as I would with any of my (functioning) Redhat boxes.

Any idea what to look for?


can you log in at the console and see if you have the same problem there ?

---

### Post by koenn on 2011-10-25
run ```
id root
```
see if you get uid=0 etc (maybe the root account is a fake ?)


----

if you have any other accounts on that server, make one of them a sudoer, see if you have the same problem with sudo

---

there's programs that can limit what an account can do (somethimes depending on where and how it logs in from) ) - i'm thinking pam restrictions, apparmor, specific ssh configurations, sudo configs, execute permissions, ... 

I don't really see how those would take away the right to run usermod from the root account  but then again, I'm not really familiar with most of those, so maybe you need to look into that.


---

yeah, I know, long shots. 
just thinking out loud, trying to get a handle on the problem, narrow it down

It could also just be something really silly we're overlooking ...

---

### Post by neal.browning on 2011-10-25
Same thing when logging in locally at the machine. Have tried logging in as a regular user, then su-ing in to root; have tried logging in as a regular user and sudo-ing the command; have tried logging in directly as root...

I have a message out to the previous admin, but am not expecting much in return.

Thanks for all of your help on this, BTW!

---

### Post by Jonathan L on 2011-10-26
> **neal.browning said:**
> There is a /etc/.pwd.lock file in place. If I delete/move this file out of the /etc directory, the lock file is created as soon as I attempt to run the usermod command.
.

Hi Neal

To me it looks like something else is trying to lock the password file.  I'd try to see if any other programs work (vipw, perhaps, or passwd); I'd also check the permissions on /etc and /etc/passwd, /etc/shadow and so on.  Are you absolutely certain the file gets made when you start usermod -- not earlier or by any other program?

Hope that's of some use.

kind regards,
Jonathan.

---

