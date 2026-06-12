---
title: "Need specific rules for iptables (or other security measures)"
date: 2009-02-12
forum: Security
---

### Post by MountainX on 2009-02-12
I want to:

1. allow SSH access by root but only from 2 specific IP addresses.**

2. allow SSH access by my user account only from any IP address.

3. disallow all other SSH access.

**I'm using dirvish for backup and it requires (afaik) root SSH login access. If I could get dirvish to work without needing to login in as root, that would resolve my issue too.

Maybe this can't be done with just iptables... I appreciate any suggestions.

---

### Post by brian_p on 2009-02-12
> **MountainX said:**
> I want to:

1. allow SSH access by root but only from 2 specific IP addresses.**

2. allow SSH access by my user account only from any IP address.

3. disallow all other SSH access.

```
man sshd_config
```

The AllowUsers option.

---

### Post by cdenley on 2009-02-12
You can simply edit /etc/ssh/sshd_config by adding this line
```

AllowUsers root@hostname MountainX@*

```
make sure there is an entry for that hostname in /etc/hosts, then restart ssh
```

sudo /etc/init.d/ssh restart

```

---

### Post by MountainX on 2009-02-12
Thanks, but I think my question is a little harder than the replies are assuming. I hoped to limit root login to just 2 specific IP addresses. 

Editing sshd_config doesn't accomplish that. I _don't want_ to just allow root access via SSH from any IP address.

---

### Post by cdenley on 2009-02-12
> **MountainX said:**
> Thanks, but I think my question is a little harder than the replies are assuming. I hoped to limit root login to just 2 specific IP addresses. 

Editing sshd_config doesn't accomplish that. I _don't want_ to just allow root access via SSH from any IP address.

Try reading the manpage more closely. When you use the AllowUsers option, it will allow only the users matched with the hostnames that you specify. The line I gave would ONLY allow root to connect from hostname or MountainX from anywhere. You would NOT be able to login as root from any unspecified host.

---

### Post by MountainX on 2009-02-12
Great. Thank you! I am starting to understand. :)

This looks like a great solution.

---

### Post by MountainX on 2009-02-12
> **cdenley said:**
> 
make sure there is an entry for that hostname in /etc/hosts, 


Is it possible to define 2 ip addresses for one host?

---

### Post by cdenley on 2009-02-12
> **MountainX said:**
> Is it possible to define 2 ip addresses for one host?

No, but you can specify two hosts.

/etc/ssh/sshd_config
```

AllowUsers root@hostname1 root@hostname2 MountainX@*

```

/etc/hosts
```

xxx.xxx.xxx.xx1 hostname1
xxx.xxx.xxx.xx2 hostname2

```

---

### Post by bodhi.zazen on 2009-02-12
To get back "on topic" , learning IPtables is well fun and it can help.

Here is a primer I am working on :

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

It is as of yet ugly and incomplete (please excuse the work in progress). Hope it helps.

---

### Post by AccountJustForThisQ on 2009-02-12
For what it's worth, I prefer to completely disallow root access through SSH, and have users run sudo or su once they're logged in; allows me to make my inner paranoiac a bit more at peace, and also provides access logs.

---

### Post by cdenley on 2009-02-12
> **AccountJustForThisQ said:**
> For what it's worth, I prefer to completely disallow root access through SSH, and have users run sudo or su once they're logged in; allows me to make my inner paranoiac a bit more at peace, and also provides access logs.

I agree, but the original poster said he needed root access for "dirvish", which I am not familiar with. If it is possible to use that application with sudo, then that would be the best solution.

---

### Post by MountainX on 2009-02-12
> **cdenley said:**
> If it is possible to use that application with sudo, then that would be the best solution.

Someone told me that it is indeed possible to make dirvish work without root access, but the steps sound very complex. I am not sure I (as a newbie) can implement it that way, and I certainly do not have time now. 

On the other hand, I do need to run my backups now. Therefore, rather than just leave SSH open to root login from anywhere (as it was), this is a much better solution.

I appreciate all the help from everyone, especially cdenley.

I have it working now (I think). What would be a good way to actually test how secure my setup is? Would anyone here want to try getting into my box?

---

### Post by bodhi.zazen on 2009-02-12
The best (simple) ways to secure you box / ssh connection is to :

1. Change the default port from 22 to a higher port. This is not simply security through obscurity, rather if you watch your ssh logs you will see the "script kiddies" target port 22. Since you are using root , you are a prime target for such scripts.

2. Use keys.

If you wish to go a few steps further install denyhosts, fail2ban, or add the iptables rule I posted on my link re ssh.

See also :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by MountainX on 2009-02-12
> **bodhi.zazen said:**
> 

2. Use keys.


In my setup for dirvish, I am using keys and no password for root login. Root login is now allowed only from my own IP address. I am also using DenyHosts (and iptables, of course).

Is this the link you were speaking of?
[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by bodhi.zazen on 2009-02-12
yes, that is the link, there is a set of rules for IPtables + SSH (near the bottom of a LONG page).

---

### Post by The Cog on 2009-02-12
You can configure sshd_config like this:
```
AllowUsers root@1.1.1.1,2.2.2.2 MountainX
```
commas to separate addresses
spaces to separate user entries
iptables won't help here because it can't see hte username being used.

---

### Post by MountainX on 2009-02-12
> **The Cog said:**
> You can configure sshd_config like this:
```
AllowUsers root@1.1.1.1,2.2.2.2 MountainX
```
commas to separate addresses
spaces to separate user entries
iptables won't help here because it can't see hte username being used.

I did it as 
```
AllowUsers root@1.1.1.1 root@2.2.2.2 MountainX@*
```

---

### Post by MountainX on 2009-02-12
> **bodhi.zazen said:**
> yes, that is the link, there is a set of rules for IPtables + SSH (near the bottom of a LONG page).

You did a nice job on that page. It's very helpful. (But it is a bit hard to read some of the dark fonts on a dark background.)

---

### Post by e1mer on 2009-02-12
> **MountainX said:**
> Is it possible to define 2 ip addresses for one host?

I think his goal is to run a program suid from (a) particular host(s).

This is a job for sudo.

/etc/groups gets a line (with values appropriate to your computer) like:
```
backup:x:34:backupuser
```

/etc/sudoers gets something like:
```
%backup hostip = (root) NOPASSWD: backup_program_path
```

That way certain boxes can have a no-password key to run the script as
```
 ssh backupuser@host 'sudo backupscript args' 
```

I am trying to do something similar, but cant get nopasswd to work right.

---

### Post by cariboo on 2009-02-12
never mind

---

### Post by bodhi.zazen on 2009-02-12
> **MountainX said:**
> You did a nice job on that page. It's very helpful. (But it is a bit hard to read some of the dark fonts on a dark background.)

Thank you for the feed back, yes it is ugly at the moment. I am working on css / theming it when I can.

---

### Post by brian_p on 2009-02-13
> **MountainX said:**
> 

I did it as 
```
AllowUsers root@1.1.1.1 root@2.2.2.2 MountainX@*
```

If root and MountainX are the only users on the box you do not need 

```
MountainX@*
```

---

### Post by MountainX on 2009-02-13
> **brian_p said:**
> If root and MountainX are the only users on the box you do not need 

```
MountainX@*
```

So just use this?

```
AllowUsers root@1.1.1.1 root@2.2.2.2 MountainX
```

Every user to be granted SSH access has to be listed here, right?

My assumption is that all other users are disallowed. I now realize that maybe I shouldn't have assumed that.

---

### Post by bodhi.zazen on 2009-02-13
No, that is correct.

You do not need the "@*" part, you do need the mountainx part (if you wish to ssh in as mountainx).

---

### Post by brian_p on 2009-02-14
> **MountainX said:**
> So just use this?

```
AllowUsers root@1.1.1.1 root@2.2.2.2 MountainX
```

Every user to be granted SSH access has to be listed here, right?


Correct, but if MountainX is the only user (apart from root) it isn't needed.

---

