---
title: "Newb Server install Problem"
date: 2008-02-04
forum: Server Platforms
---

### Post by PaulCheeseman on 2008-02-04
Hi

The basic server is installed, but I cant seem to install anything else!

Example, trying to add a GUI (gleaned form several posts how to do it)

sudo apt-get update 
or
sudo aptitude install xorg

infact I have tried a lot of sudo apt-get commands, and everyone of them errors with:

sendmail: fatal: open /etc/postfix/main.cf: no such file or directory

(or similar depending on what I try to do)

At this point I have no idea what I am doing wrong. I even re installed the basic software incase I had messed that up!

I assume I am doing something wrong to fail on all install attempts ?:confused:

Paul

---

### Post by freebeer on 2008-02-05
The command to add a GUI to the server version is, I believe:

```

  sudo apt-get install ubuntu-desktop 

```

Try that and let us know if it worked.  If you get errors, take note of thos errors and post them up so we can have a look.

---

### Post by 3dcandy on 2008-02-05
or if you fancy a KDE desktop it's

```
sudo apt-get install kubuntu-desktop
```

---

### Post by gnaunited on 2008-02-05
Or since it says server then:
```
sudo apt-get install xubuntu-desktop
```

Also, try and paste the entire error message.

---

### Post by PaulCheeseman on 2008-02-07
Thanks for the replies. I am guessing it may be a permissions issue ...

when I typed in  *sudo apt-get install ubuntu-desktop*

I got *[sudo] password for paulcheeseman*

After typing in my password I got
[I]
paulcheeseman is not in the sudoers file. this incedent will be reported.
paulcheeseman@Ubuntu: ~$ sendmail: fatal: open /etc/postfix/main.cf: no such file or directory[/I]

Then back to the paulcheeseman@Ubuntu:~$

---

### Post by freebeer on 2008-02-07
That error message implies that your user account doesn't have sudo privileges.  By default, the first user created at install is granted sudo privs, and all subsequent users added aren't given such privs.  I presume that's what happened.  To give that account sudo privs, you'll need to add it to the "admin" group (I'm pretty sure that's the only one).  You'll probably need to do that from an account with sudo privs, though.

---

### Post by PaulCheeseman on 2008-02-07
That makes sense, but odly, that was the only account I have created.

I kinda expected to have full rights being the first one.

How do I give this account full rights please? (this is where I show how little I know about Linux, being a Novel, them Mic****ft person) I am keen to learn, just need a helping hand to start with :D

---

### Post by PaulCheeseman on 2008-02-07
Ok, after a few searches, tried this:

*sudo adduser paulcheeseman admin*

It asked for password, then said

[I]paulcheeseman is not in the sudoers file. this incedent will be reported.
paulcheeseman@Ubuntu: ~$ sendmail: fatal: open /etc/postfix/main.cf: no such file or directory[/I]

What IS this sudoers file ? do I need to manually edit it? or am I going totally wrong ...

Paul

---

### Post by mmichalik on 2008-02-07
I'm going to jump in here for a bit.  I hope I can help.

During the install of the OS, you were asked to create a login and password.  Was paulcheeseman the one you made?  Or did you make one like "admin" or "administrator" or something like that?

If you made an "admin" type one, that's the one you have to log in as in order to grant paulcheeseman the admin privileges needed.

---

### Post by PaulCheeseman on 2008-02-07
I only made paulcheeseman. 

What I will do though, as the practice wont hurt, is re run the install, now I'm not scared of it :) and look more closely at the account setup.

---

### Post by mmichalik on 2008-02-07
cool and good luck!

---

### Post by gnaunited on 2008-02-07
Or you could reboot into rescue mode and then do it - probably save you a lot of trouble in the end.

---

### Post by PaulCheeseman on 2008-02-07
Ok, did full re install again, and as I found in some further searches, in basic install mode, only a basic user gets setup. So .... following another thread, logged into safe/recoverymode, (as root) changed the root password, and ran the 'sudo apt-get install ubuntu-desktop command from there, and it worked :) 

So thats a start. I assume things can only get harder ? 

Thanks for the help, and pointers.

Paul

---

### Post by PaulCheeseman on 2008-02-07
> Or you could reboot into rescue mode and then do it - probably save you a lot of trouble in the end.

I found that thread after starting the re install :( but the setup practice wont hurt, as I plan to setup a few of these when I have got more comfortable with them. And at least all this messing around is giving me more of an insight into how some things work, than if it just worked (however nice that may seem to be)


PS: its also nice to see an ACTIVE forum where people answer you quickly, beats waiting for weeks as per some I have to use ...=D>

---

### Post by phasmatis on 2008-03-23
Time to bump up an old thread.

I found this thread by putting "sendmail: fatal: open /etc/postfix/main.cf" into Google. Turns out it's a common problem.

I just installed Ubuntu 7.10 Server edition. I've installed it before with no problems, BTW. This time, the username I created during the install is giving me the same error message:

```
phasmatis@ubuntu:~$ sudo man sudo
phasmatis is not in the sudoers file.  This incident will be reported.
phasmatis@ubuntu:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

phasmatis@ubuntu:~$

```

Anyway, booting into recovery mode and manually adding "phasmatis ALL=(ALL) ALL" to the /./etc/sudoers file fixed the problem. Note that visudo doesn't work from the recovery console! Or maybe it's not set as an executable by default. Also you have to use the installation terminal and not the one on /dev/sda1 or whatever.

Hope this helps someone!

---

