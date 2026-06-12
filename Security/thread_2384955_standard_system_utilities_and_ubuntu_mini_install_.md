---
title: "standard system utilities and ubuntu mini install security"
date: 2018-02-14
forum: Security
---

### Post by Drenriza on 2018-02-14
I have been experimenting with the Ubuntu mini install ISO
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

After a basic install i see that the packages of Apparmor and Iptables are precent.
Which as i understand, Apparmor is part of the core security of Ubuntu.

**So here are my question**
Are there any security risks one should know about if for example installing Ubuntu mini and using it for either a Desktop or Server,
versus using the installation ISO's from
[URL="https://www.ubuntu.com/download/desktop"]https://www.ubuntu.com/download/desktop
[/URL][https://www.ubuntu.com/download/server](https://www.ubuntu.com/download/server)

As to why i would like to do this to begin with is that for both my desktop and server environments i would
like to cut out all the packages and processes that may follow to save resources and storage for actual work.

For my desktop with i3 this has been really nice, as boot, process start and so on works (to the eye) so much
faster and more fluent.

Thanks in advance
Kind regards

---

### Post by TheFu on 2018-02-14
Anytime you remove code, you've taken away an attack vector.  All code has bugs, so the less, the better.
OTOH, you also loose convenience of having the extra pre-installed stuff setup for you.

Apparmor and an interface into the Linux firewall (which is built into the kernel, which iptables is just an interface into like ufw or any other interface tools), aren't the only "security" aspects, but most of the others are part of the file system permissions until you get to extraordinary efforts.

I choose to load Ubuntu Server as my "middle ground", then add openbox and a few other GUI tools to my "desktops".  For me, it keeps the system with enough expected tools, but not all the full "DE" lists and lists of applications that someone less familiar with loading programs might want.

In short - if it works for you, do it.  You can always add missing stuff as needed.

---

### Post by Bashing-om on 2018-02-14
Drenriza; Hello -

I too am a proponent of a minimal install - and install to that base only what "you" want.

I value fast, light and efficient .
+10
> 
In short - if it works for you, do it. You can always add missing stuff as needed.


one of the 1st things I add is anacron's logging abilities. Took me a while to discover the missing functionality in that base install .
cron  does expect it : see:
```

cat /etc/crontab

```
to know what all anacron does for you:
```

apt show anacron

```

This as but one example, I am sure there will be others :)

[INDENT][INDENT]'buntu
[INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Drenriza on 2018-02-16
Thanks for the replies guys they are very helpfull.

And thanks for the suggestions, since i am also looking for some logging for all my installations
servers as desktop along with adding tripwire for file changes.

---

