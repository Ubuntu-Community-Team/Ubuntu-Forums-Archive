---
title: "No login after bootup"
date: 2007-01-09
forum: Server Platforms
---

### Post by djMoralita on 2007-01-09
Hi,

I wonder if it's possible to disable or remove the login process after boot-up on an Ubuntu Server 6.10 installation. I was able to do this in a desktop, remove a login, and setup a default user. Is this possible for a server (shell-based), how can this be done?

It sounds weird, but it's not my choice, :(

Cheers,

DJ

---

### Post by hal10000 on 2007-01-10
There is one user you must NOT remove or disable, (root) or you will not be able to do any administration tasks.

Before you remove or disable users, you have to create a password for the root user (if you didnt this already): [COLOR="Red"]sudo passwd root[/COLOR]
Otherwise you may run into trouble if your system refuses logins without a password (beside this would be the greatest security hole one can imagine).

You may remove the other users: (presume you are logged in as root)

1. [COLOR="Red"]userdel username[/COLOR] This preserves the user's home directory, in case there are files you may need in the future. You can then remove the home directory manually (rm -r /home/username) if you don't need it anymore.

2. [COLOR="Red"]userdel -r username[/COLOR] Files in the user&#8217;s home directory will be removed along with the home directory itself and the user&#8217;s mail spool. Files located in other file systems will have to be searched for and deleted manually.

Another way is to just disable login for the existing users. This can easily be done by editing the /etc/passwd file. In this file you see user entries at each line, the informations are in colums, each separated by a colon (see man 5 passwd for details).

Do changes here only for users with an id equal or greater than 1000 (the third column), because users with an id lower than 1000 are usually created by the system itself and are needed by the system.

To disable a user login just change the last column, which defines the login shell (usually /bin/bash) to /bin/false.

I suggest using the [COLOR="Red"]nano [/COLOR] editor for editing the /etc/passwd file.
Hope this helps.

---

### Post by kebes on 2007-01-10
> **djMoralita said:**
> Hi,

I wonder if it's possible to disable or remove the login process after boot-up on an Ubuntu Server 6.10 installation. I was able to do this in a desktop, remove a login, and setup a default user. Is this possible for a server (shell-based), how can this be done?

It sounds weird, but it's not my choice, :(

Cheers,

DJ

Did hal10000 answer your question? ...or were you asking how to make the system "auto-login" the way you can do with desktop systems.

This article:
[http://www.linuxjournal.com/article/3121](http://www.linuxjournal.com/article/3121)
looks like it discusses autologin.

(Of course you should be aware that it's not very secure to have a server set up like this.)

---

### Post by hal10000 on 2007-01-10
Maybe i misunderstood the question???????

---

### Post by kebes on 2007-01-10
> **hal10000 said:**
> Maybe i misunderstood the question???????

Yeah I couldn't tell whether the question was "how do I disable a login account" or "how to I disable the login process" (i.e.: make it login automatically).  ...so I answered the one you didnt'! :)

---

### Post by djMoralita on 2007-01-10
The question was how to remove the login prompt, so that when the system boots-up the default user is login automatically and his profile is run.  I will check your answers, and see if I get my questions answered. Thank you so much.


Cheers,

DJ

---

### Post by djMoralita on 2007-01-11
Thank you for all the reply, this server is for demo server inside VMWare. 

I tried the how-tos in this link [http://www.linuxjournal.com/article/3121](http://www.linuxjournal.com/article/3121)

but I learned in [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication)

in here that /etc/inittab is already different in edgy, I will try to mix both tutorials, :)

will let y'all know if I'm successful

---

### Post by djMoralita on 2007-01-11
My attempt didn't work, it doesn't bootup anymore, but I was still able to login as root in recovery mode.

I used this autologin script from the other tutorial:

#! /bin/bash
exec 0/dev/$1 2>&1
cat /etc/issue
shift
exec $*


and then I moved it to /sbin

then I add this line to /etc/event.d/tty1

respawn /sbin/getty -n -l /sbin/autologin tty1 login -f mefgadmin

I guess I'm  missing out on something, but I think it's possible, right?

I also tried the autologin.c but I cannot compile it even if I download gcc, and I really am not going to use xwindows or desktop, this is pure shell-based server.

Cheers,

DJ

---

### Post by hal10000 on 2007-01-11
Yes, i'm sure it is possible because we did this on work for internet cafe clients running under debian, but  (shame on me, because i did myself) i forgotten the steps. Hope i will remember some day, then I'll let you know.

---

### Post by kebes on 2007-01-11
> **djMoralita said:**
> I also tried the autologin.c but I cannot compile it even if I download gcc, and I really am not going to use xwindows or desktop, this is pure shell-based server.

Compiling the autologin.c should work (it's such a simple C-program!) ... what were the compiler errors? (Also, when you installed gcc did you do "sudo aptitude install gcc" or "sudo aptitude install build-essential" ... the latter installs gcc plus related tools that are required...).

---

### Post by djMoralita on 2007-01-12
I used apt-get install gcc, so I guess I missed on the essentials, but the error was on the execlp line, it seems the parameters are not valid. I will try, again. ASAP.

---

### Post by djMoralita on 2007-01-15
It works, I ran the following:

"sudo aptitude install gcc" and "sudo aptitude install build-essential" .

and was able to compile the c script to disable the login.

thank you so much, cheers

DJ

---

