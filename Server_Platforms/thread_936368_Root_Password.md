---
title: "Root Password"
date: 2008-10-02
forum: Server Platforms
---

### Post by pheckmann on 2008-10-02
I've recently added a Ubuntu server to our system. The fellow that I hired to install the Ubuntu is in Japan for a few weeks. 

We had a couple of user/pws setup, one "root" and the other as mine. Now the Root one does not accept the pw that used to work on it. However mine does.

Q - first of all, now I've been told there there is no "root" or "root user" in Ubuntu? Is this different from Debian? 

Also, is there a way to recover the pw for Root? 

Thanks

---

### Post by louieb on 2008-10-02
Debian and Ubuntu disable the root account as a security measure.
While you have the right to enable the root account. This forum has a decided to follow the Ubuntu security model,  so we can't post a how to  here.

---

### Post by Primefalcon on 2008-10-02
There is a root account but it's disabled.

Unlike other Linux system you don't need to log in as root to do root things, you request root privileges for a command or a series of commands, and the computer will give you either super user privileges for that command.

Though you can still sort simulate being root in the GUI by doing this.. ```
gksudo nautilus
``` or at command line by issuing ```
sudo su
```
You can also just issue sudo or gksudo before a command to run that command with root privileges.

It's really is a more secure way by not actually having to stay as root.

---

### Post by maybeway36 on 2008-10-02
[QUOTE=louieb;5895877]Debian and Ubuntu disable the root account as a security measure.[QUOTE]

It *is* enabled in Debian, but not in Ubuntu.

---

### Post by Madman6510 on 2008-10-02
> **louieb said:**
> Debian and Ubuntu disable the root account as a security measure.
While you have the right to enable the root account. This forum has a decided to follow the Ubuntu security model,  so we can't post a how to  here.

Wait, what? Where does it say we're not allowed to tell people how to reenable the root account?

---

### Post by Bachstelze on 2008-10-02
> **Madman6510 said:**
> Wait, what? Where does it say we're not allowed to tell people how to reenable the root account?

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by Primefalcon on 2008-10-02
I apologize I never seen that.

Although I question censoring how-to's that Ubuntu itself supports, I do not see the reason why the the OS actually supports enabling it really, We don't actually need it and using it only compromises security...

---

### Post by Gannon8 on 2008-10-02
> **pheckmann said:**
> Also, is there a way to recover the pw for Root?

Don't think so, but it is set to your password by default. Just don't change it :)

---

### Post by Sef on 2008-10-02
Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by louieb on 2008-10-02
> **maybeway36 said:**
> It *is* enabled in Debian, but not in Ubuntu.

:twisted:oops

---

### Post by garyed on 2008-10-02
I'm not trying to break any rules but since we're talking about root password
I don't understand what the difference is between activating a root password
and just entering "sudo -i" ?

---

### Post by y@w on 2008-10-02
Now hold on.. The policy has nothing to do with enabling the root account.. Just enabling the root account to login to the GUI or auto-login (I assume to the GUI?). Is that a loophole in the policy or was it left open like that on purpose? There are ways to login as root without actually 'enabling' the account. Is that forbidden as well? (I apologize as this is a bit off topic, but the other thread is locked.) Are we forbidden to help pheckmann to change his/her root password?

---

### Post by pheckmann on 2008-10-03
Good stuff guys. Not the exact answer I'd hoped for but I guess I'm going on a down and dirty on Ubuntu. 

BTW - here's what came us with using my username/pw (not the root)

when I enter "sudo -1"  this is what I get:
---------------------------------------------------------
sudo: illegal option '-1'
usage: sudo -h | -K | -k | -L | -1 | -V | -v
usage: sudo [-bEHPS] [-p Prompt] [-u username|#uid] [var=value] {-i|-s|<command>}
usage: sudo -e [-S] [p prompt] [-u username|#uid] file...
----------------------------------------------------------
Will not having the root pw stop me from doing anything of importance?

---

### Post by y@w on 2008-10-03
> **pheckmann said:**
> Will not having the root pw stop me from doing anything of importance?

No, as long as your user can sudo it'll be fine.

The option you want there is the lowercase letter 'l'. It'll show what permissions you user has. If your user has full sudoer permissions it will show:
```
User <user> may run the following commands on this host:
    (ALL) ALL

```

---

### Post by pheckmann on 2008-10-03
> **y@w said:**
> No, as long as your user can sudo it'll be fine.

The option you want there is the lowercase letter 'l'. It'll show what permissions you user has. If your user has full sudoer permissions it will show:
```
User <user> may run the following commands on this host:
    (ALL) ALL

```

Got it! Thanks. 

BTW - I got an older email server that I'm going to convert to test server for our database. I've already burned the Ubuntu software - where are some good step by step instructions on the install?

---

### Post by dioltas on 2008-10-03
I'm a bit shocked that you cant post a guide to enabling the root password on this forum. What about freedom of information and all that? Isn't that a big part of the open source philosophy? 

Anyway, just google "enabling root account" or something like that and you should find a guide. I have it enabled and find it useful alot. I'm not a child, I can be trusted with the security of my own system, if I break it it's my own fault.
Oh well, rant over, just kinda dissapointed having found out about that censorship....

---

### Post by pheckmann on 2008-10-03
> **dioltas said:**
> I'm a bit shocked that you cant post a guide to enabling the root password on this forum. What about freedom of information and all that? Isn't that a big part of the open source philosophy? 

Anyway, just google "enabling root account" or something like that and you should find a guide. I have it enabled and find it useful alot. I'm not a child, I can be trusted with the security of my own system, if I break it it's my own fault.
Oh well, rant over, just kinda dissapointed having found out about that censorship....

It's already been enabled - however the password that was given to me doesn't work. We had a third party come in and install some database software on it and ever since, it does not work. So I need to somehow get to it and change the password (now, just for my peace of mind that no one can get into it, ie: the third party)

---

### Post by PocketDog on 2008-10-03
It's not censorship, it's simple common sense. If someone isn't sufficiently experienced to know how to log in as root, they're not sufficiently experienced enough to do so.

---

### Post by davidryder on 2008-10-03
> **PocketDog said:**
> It's not censorship, it's simple common sense. If someone isn't sufficiently experienced to know how to log in as root, they're not sufficiently experienced enough to do so.

Knowledge follows experience.

---

### Post by y@w on 2008-10-03
I think they want to avoid people logging in to the X as root.. at least that's how the policy reads, but no moderators have responded (see above). I see the rationale.. they want to avoid the Windows syndrome - running everything as the admin user. There are some things that you need to drop to a shell as root to do and that doesn't involve "enabling" the root user.

To answer your question pheckmann, the installation documentation can be found here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by hyper_ch on 2008-10-03
> **dioltas said:**
> I'm a bit shocked that you cant post a guide to enabling the root password on this forum. What about freedom of information and all that? Isn't that a big part of the open source philosophy?

It is freedom of information ;) you can write howtos whereever you want and publish how to enable it - just not on these forums and reasons for that were given. Considering that many people from windows have their first contact with linux using ubuntu it makes sense. Teach them first how to get along in a "limited" user account and learn the ins and outs of linux. Once they moved a bit around they will know how to enable root.

---

### Post by Sujit_Kumar on 2008-10-03
In ubuntu Root profile is disabled by default as a security measure and it is recommended to leave it so for safety reasons[-X. You can carry out administrative tasks using the "sudo" command.=D>

---

### Post by pheckmann on 2008-10-03
> **y@w said:**
> I think they want to avoid people logging in to the X as root.. at least that's how the policy reads, but no moderators have responded (see above). I see the rationale.. they want to avoid the Windows syndrome - running everything as the admin user. There are some things that you need to drop to a shell as root to do and that doesn't involve "enabling" the root user.

To answer your question pheckmann, the installation documentation can be found here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Thanks y@w

---

### Post by jamesrl on 2008-10-03
I think most people are forgetting one of the major reasons, the ubuntu security model doesn't give you a root user ... it makes it much easier to hack in to the computer when you a completely unknowledgable intruder knows what your login to use.  Most password cracking programs, try 'root' (and a few other standard account names) by default.  But as long as you can type sudo -i there's no reason to need to login as root, because you can create a root shell.

---

### Post by davidryder on 2008-10-03
> **jamesrl said:**
> I think most people are forgetting one of the major reasons, the ubuntu security model doesn't give you a root user ... it makes it much easier to hack in to the computer when you a completely unknowledgable intruder knows what your login to use.  Most password cracking programs, try 'root' (and a few other standard account names) by default.  But as long as you can type sudo -i there's no reason to need to login as root, because you can create a root shell.

I think that's a pretty good explanation. Thanks!

---

### Post by pheckmann on 2008-10-03
Got a note back from my install guy - 

> When Ubuntu is initially setup the root password is not known, this is to force novice users to use their personal accounts for most tasks and to use the sudo command for root actions so there is a log of root commands executed. However setting the root account to a known password is a standard task that is done especially when a configuring ubuntu as a production server. I set the root password and passed it along to you and Pete when I turned the server over to you.

In summary Sandee is wrong, there is most certainly a root user. The root password is set to a value unknown at the time the installation is done, however I set it to a trivial passphrase while setting up the box and passed it along as part of the turnover process. Some time after the turnover to you the password has been changed.


---

### Post by lykwydchykyn on 2008-10-03
Ok, apologies if I break any forum rules, but as I see it pheckmann is locked out of his server so here's what he needs to do:

1. First, try sudo -s or sudo -i with your user account and your normal login password.  Does that get you to a root account? If so use this command:
```

sudo passwd -l root

```
That will lock root so nobody can log in as root, as per ubuntu default.  

2. If that fails, if you just can't get a root prompt no matter what you try, you will have to boot to recovery mode (hit esc when booting to see the boot menu).  When you get to the recovery mode menu, hit "drop to a root shell". Use the "visudo" command to add your login user to the sudoers list with a line like this:
```

myuser ALL=(ALL) ALL

```
exit the shell, boot back to normal runlevel.  Then see step 1.

Either of these methods should get you back to the default Ubuntu security model.

---

### Post by cdenley on 2008-10-03
> **pheckmann said:**
> Got a note back from my install guy -
When Ubuntu is initially setup the root password is not known, this is to force novice users to use their personal accounts for most tasks and to use the sudo command for root actions so there is a log of root commands executed. However setting the root account to a known password is a standard task that is done especially when a configuring ubuntu as a production server. I set the root password and passed it along to you and Pete when I turned the server over to you.

In summary Sandee is wrong, there is most certainly a root user. The root password is set to a value unknown at the time the installation is done, however I set it to a trivial passphrase while setting up the box and passed it along as part of the turnover process. Some time after the turnover to you the password has been changed.


I would most definitely disagree. The root password is known, in a sense. the password hash stored in /etc/shadow is "!". Since this value is invalid, there is no password that would be accepted as valid. This keeps the root account fully functional without allowing anyone to actually authenticate as root.

This isn't just done for novice users. This is done for everyone. If there are any servers running which authenticate system users, root is the most commonly guessed username.
[http://cdenley.yi.org/ssh_honey/usernames.php](http://cdenley.yi.org/ssh_honey/usernames.php)
If you enable your root account and run an ssh server, it is just a matter of someone guessing your password (easy task for a "trivial" password), then the attacker has root! It is also not a good idea to run anything as root unless you have to, especially on a server.

Setting a root password is not a standard task, especially when configuring a production server. I would never enable root on any servers I run.

---

### Post by Rich78 on 2008-10-03
I disable root for all servers regardless of distro.  It's a common security practice.

sudo is a much better and more secure solution, mainly because if you're left logged in as root for any period of time, any executable run under that profile will run with root privileges and can cause all sorts of harm.

Root executions should be per action.

---

### Post by Primefalcon on 2008-10-03
> **pheckmann said:**
> Good stuff guys. Not the exact answer I'd hoped for but I guess I'm going on a down and dirty on Ubuntu. 

BTW - here's what came us with using my username/pw (not the root)

when I enter "sudo -1"  this is what I get:
---------------------------------------------------------
sudo: illegal option '-1'
usage: sudo -h | -K | -k | -L | -1 | -V | -v
usage: sudo [-bEHPS] [-p Prompt] [-u username|#uid] [var=value] {-i|-s|<command>}
usage: sudo -e [-S] [p prompt] [-u username|#uid] file...
----------------------------------------------------------
Will not having the root pw stop me from doing anything of importance?
it's sudo -i not sudo 1 (lowercase I)

Though I'd just sticking with using sudo command from the command line or if you wont to open a graphical application with root privileges such as nautilus then you use gksudo nautilus or gksudo gedit file or so on.

sudo su or sudo -i really has the same pitfalls as enabling the root account in a lot of situations

---

