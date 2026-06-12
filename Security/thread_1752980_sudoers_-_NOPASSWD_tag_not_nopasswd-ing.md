---
title: "sudoers - NOPASSWD tag not nopasswd-ing"
date: 2011-05-08
forum: Security
---

### Post by Mozai on 2011-05-08
Trying to add access to a normal user to append to iptables (it's for intrusion detection, since this machine is too small to run snort or fail2ban).

I'm having trouble getting a user to launch a command without being prompted for their password interactively.

Here's /etc/sudoers :
```

Defaults    requiretty
Defaults    env_reset
root	ALL=(ALL) 	ALL
Cmnd_Alias BLACKLIST_ADD = /usr/sbin/iptables -A BLACKLIST -s [0-9.]* -j REFUSE
moses ALL = NOPASSWD: BLACKLIST_ADD

```

In another terminal on the same host, as user 'moses' I attempt the command, and I'm prompted for a password:
```
[moses@nepeta ~]$ sudo /usr/sbin/iptables -A BLACKLIST -s 210.216.230.203 -j REFUSE
[sudo] password for moses:
```

What am I doing wrong here?

---

### Post by bodhi.zazen on 2011-05-08
It should just be

```
Cmnd_Alias BLACKLIST_ADD = /usr/sbin/iptables
```

I do not think you can add all those options

---

### Post by Mozai on 2011-05-08
> **bodhi.zazen said:**
> It should just be
'/usr/sbin/iptables' I do not think you can add all those options.


'man 5 sudoers' says I can.  Read for yourself:

> 
A Cmnd_List is a list of one or more commandnames, directories, and
other aliases.  A commandname is a fully qualified filename which may
include shell-style wildcards (see the Wildcards section below).  A
simple filename allows the user to run the command with any arguments
he/she wishes.  However, you may also specify command line arguments
(including wildcards).  Alternately, you can specify "" to indicate
that the command may only be run without command line arguments.

 Cmnd_List ::= Cmnd | Cmnd ',' Cmnd_List

 commandname ::= filename | filename args | filename '""'

 Cmnd ::= '!'* commandname | '!'* directory | '!'* "sudoedit" | '!'* Cmnd_Alias 

So it should be possible.  Although, in the dozen example /etc/sudoer files I've seen, I've never seen someone specify the arguments. That's really weird to me, since it seems like an efficient way of making sure the user doesn't pass bad parameters when they have root access.

This is why I'm asking the forum: after an hour and a half of reading, I don't have an example of this feature being used, only described over and over again.

---

### Post by Mozai on 2011-05-08
Found it.  There can't be a space between the tags and the command (or command alias).

Thus 'moses ALL=NOPASSWD: BLACKLIST_ADD' is wrong
and 'moses ALL=NOPASSWD:BLACKLIST_ADD' is right.
(oh, and I had the wrong path for iptables, but that has nothing to do with /etc/sudoers)

---

### Post by bodhi.zazen on 2011-05-08
Glad you got it sorted. Syntax errors can be frustrating.

Use visudo, it checks for such things ;)

You raise a good point re: options, I leaned something.

It is useful, but rare that people give restricted root access, thus not all the various options are well known.

---

