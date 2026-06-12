---
title: "Brute force attacking my server"
date: 2012-02-16
forum: Security
---

### Post by fernandoch on 2012-02-16
Hello,

Someone is running this on my server grep "Failed password for root from" /var/log/auth.log
```

Feb 16 16:05:45 plato sshd[1440]: Failed password for root from 187.32.76.178 port 48506 ssh2
Feb 16 16:06:37 plato sshd[1442]: Failed password for root from 187.32.76.178 port 58975 ssh2
Feb 16 16:07:33 plato sshd[1444]: Failed password for root from 187.32.76.178 port 41208 ssh2
Feb 16 16:08:21 plato sshd[1446]: Failed password for root from 187.32.76.178 port 51674 ssh2
Feb 16 16:09:08 plato sshd[1456]: Failed password for root from 187.32.76.178 port 33908 ssh2
Feb 16 16:10:01 plato sshd[1458]: Failed password for root from 187.32.76.178 port 44374 ssh2
Feb 16 16:10:49 plato sshd[1460]: Failed password for root from 187.32.76.178 port 51163 ssh2
Feb 16 16:12:25 plato sshd[1463]: Failed password for root from 187.32.76.178 port 43868 ssh2
Feb 16 16:13:11 plato sshd[1465]: Failed password for root from 187.32.76.178 port 54358 ssh2
Feb 16 16:13:57 plato sshd[1472]: Failed password for root from 187.32.76.178 port 36659 ssh2
Feb 16 16:14:48 plato sshd[1478]: Failed password for root from 187.32.76.178 port 47147 ssh2
Feb 16 16:17:36 plato sshd[1915]: Failed password for root from 187.32.76.178 port 54502 ssh2
Feb 16 16:18:28 plato sshd[1920]: Failed password for root from 187.32.76.178 port 36760 ssh2
Feb 16 16:19:15 plato sshd[1928]: Failed password for root from 187.32.76.178 port 47241 ssh2
Feb 16 16:20:09 plato sshd[1946]: Failed password for root from 187.32.76.178 port 57779 ssh2
Feb 16 16:20:59 plato sshd[1948]: Failed password for root from 187.32.76.178 port 36451 ssh2
Feb 16 16:21:46 plato sshd[1956]: Failed password for root from 187.32.76.178 port 46943 ssh2
Feb 16 16:22:35 plato sshd[1960]: Failed password for root from 187.32.76.178 port 57418 ssh2
Feb 16 16:23:20 plato sshd[1962]: Failed password for root from 187.32.76.178 port 39665 ssh2
Feb 16 16:24:06 plato sshd[1966]: Failed password for root from 187.32.76.178 port 50146 ssh2
Feb 16 16:24:54 plato sshd[1968]: Failed password for root from 187.32.76.178 port 60624 ssh2
Feb 16 16:25:40 plato sshd[1970]: Failed password for root from 187.32.76.178 port 57325 ssh2
Feb 16 16:26:28 plato sshd[1973]: Failed password for root from 187.32.76.178 port 39570 ssh2
Feb 16 16:27:17 plato sshd[2376]: Failed password for root from 187.32.76.178 port 50046 ssh2
```

How can I block it with ufw? I have these rules

```
root@plato:/etc/ufw# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         LIMIT       Anywhere
80                         ALLOW       Anywhere
Anywhere                   DENY        187.32.76.178
```

Pretty annoying this guy...

---

### Post by 1clue on 2012-02-16
If you need an exposed ssh server then put it on some random port.  You can make it more secure from jokers like this by changing the name of the root user.

Root user is UID=1, it doesn't matter what you call it.
As root, edit /etc/passwd and change 'root' to some other name.
Also edit /etc/group and change all 'root' to that other name.

Keep in mind that this can't match your existing users.

Another thing you can do is disable your sshd from allowing root logins from remote computers.  This hurts a default Ubuntu installation not one bit because you are set up automatically with sudo needing a password.

Another thing you can and should do is use a really good password on EVERY account.  Currently I'm using between 15 and 20 characters pulled out of an ssl encryption key for my passwords.  I cycle through them on my accounts, so the most critical systems get the new password, then when I change on the next most critical group they get the one I just changed out of on the critical system, and then the third set gets the one from the second set.  So I only ever have to learn one password at a time, but have several active.

Finally, divorce your Linux box from a direct Internet connection.  Set yourself up with an appliance cable modem/whatever, and an appliance firewall/switch of some sort.  Lock the switch down, and then also lock your Linux box down.  Defense in depth.

---

### Post by fernandoch on 2012-02-16
Thank you for your reply, but this is an online shop... I need it online :)

I just wanted to block that IP out with ufw.

I have set the limit also, but he is not attacking so frequently as 6 attemps in the last 30 seconds, so he is not being denied.

---

### Post by fernandoch on 2012-02-16
It seems ufw is not even working I added a rule, last line

```
root@plato:/etc/ufw# ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         LIMIT       Anywhere
80                         ALLOW       Anywhere
Anywhere                   DENY        187.32.76.178
22                         DENY        207.45.182.51
```

And I can still connect from that IP to my ssh server. How is that possible? The server is running on port 22...

---

### Post by fernandoch on 2012-02-16
I fixed it :) It was my mistake, specific rules must come first as it says in here [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

> Once a rule is matched the others will not be evaluated (see manual below) so you must put the specific rules first. As rules change you may need to delete old rules to ensure that new rules are put in the proper order.

```
root@plato:/etc/ufw# ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   DENY        187.32.76.178
Anywhere                   DENY        207.45.182.51
80                         ALLOW       Anywhere
22                         LIMIT       Anywhere
```

I hope this helps someone else...

UFW -> SPECIFIC RULES FIRST.

---

### Post by 1clue on 2012-02-16
> **fernandoch said:**
> Thank you for your reply, but this is an online shop... I need it online :)

I just wanted to block that IP out with ufw.

I have set the limit also, but he is not attacking so frequently as 6 attemps in the last 30 seconds, so he is not being denied.

You can still keep it "online" and get some protection on there.  There's a huge difference between an unprotected Linux box on the Internet and a protected one with ssh exposed through an external firewall as well as an internal ufw rule.  I do that with my home systems, not doing it with an online shop is just asking for trouble, especially if any sort of sensitive data or customer data is on there.

Your attacker is almost certainly automated.  That means sooner or later it's coming from some other IP.  Simply changing the name of root user will block this sort of attack completely.

Making a Really Good Password also blocks this sort of thing, since they almost always use a top 200 list or top N list to brute force attacks.

---

### Post by jramshu on 2012-02-16
Disable password authentication and use keys. Setup something like fail2ban or denyhosts, or use iptables.

---

### Post by lisati on 2012-02-16
> **jramshu said:**
> Disable password authentication and use keys. Setup something like fail2ban or denyhosts, or use iptables.

+1 to fail2ban or denyhosts.

---

### Post by Andrew_P on 2012-02-16
If the cracker is employing a program to try passwords in some kind of sequence, and if you could figure out which ones he's already tried, set the password to one of those, assuming he's not going to re-run the ones that failed.  You could really mess with his mind.  Heh, heh. :twisted:

---

### Post by redmk2 on 2012-02-16
> **1clue said:**
> ...
Root user is UID=1, it doesn't matter what you call it.

Eh, come again?  Root is UID=0 and GID=0 on Linux.  See below:

For getent passwd
```
$ getent passwd
**[COLOR="Red"]root:x:0:0:root:/root:/bin/bash[/COLOR]**
daemon:x:1:1:daemon:/usr/sbin:/bin/sh

```

For getent group
```
$ getent group
**[COLOR="Red"]root:x:0:[/COLOR]**
daemon:x:1:

```

---

### Post by Dangertux on 2012-02-16
Yep root = UID/GID 0

Also ... Instead of changing root's UID which is a little outside the box, just make sure your username is a sudoer then.

```

sudo usermod -L root

```

Which should already be done by default on Ubuntu anyway.

Hope this helps.

---

### Post by redmk2 on 2012-02-16
> **Dangertux said:**
> Yep root = UID/GID 0

Also ... Instead of changing root's UID which is a little outside the box, just make sure your username is a sudoer then.

```

sudo usermod -L root

```

Which should already be done by default on Ubuntu anyway.

Hope this helps.

The comment by @1clue kinda blows his cred.

+1 to you.  I like your work @Dangertux.

---

### Post by 1clue on 2012-02-16
> **redmk2 said:**
> Eh, come again?  Root is UID=0 and GID=0 on Linux.  


Wow, my bad.  I don't know what I was thinking.

---

### Post by 1clue on 2012-02-16
> **Dangertux said:**
> Yep root = UID/GID 0

Also ... Instead of changing root's UID which is a little outside the box, just make sure your username is a sudoer then.

```

sudo usermod -L root

```

Which should already be done by default on Ubuntu anyway.

Hope this helps.

Why not change the name anyway?  That makes it one fewer pieces of information the attacker does not have about your box.  Better yet, it becomes a piece of MISinformation that they have.  They assume you have an account named root, and that is not true.

A large percentage of intrusions which try to get root authority assume that the super-user is called 'root'.  If they get a restricted account somehow and want full access, they are likely to write whatever hack based on 'root' instead of finding out what's in the /etc/passwd file.

I've been changing the root account name for years, never found a bad side-effect yet.  Goes back to 'defense in depth' and all that.

---

### Post by redmk2 on 2012-02-16
> **1clue said:**
> Why not change the name anyway?  That makes it one fewer pieces of information the attacker does not have about your box.  Better yet, it becomes a piece of MISinformation that they have.  They assume you have an account named root, and that is not true.

A large percentage of intrusions which try to get root authority assume that the super-user is called 'root'.  If they get a restricted account somehow and want full access, they are likely to write whatever hack based on 'root' instead of finding out what's in the /etc/passwd file.

I've been changing the root account name for years, never found a bad side-effect yet.  Goes back to 'defense in depth' and all that.

The UID/GID is still 0!  Whatever cocks your pistol.  I have a friend with flypaper all over the house.  He says it keeps the elephants away.  True enough, I've never seen an elephant in his neighborhood (Los Angeles).

---

### Post by kevdog on 2012-02-17
This type of attack against a specific port and service is made for a fail2ban implementation.

---

### Post by dgw on 2012-02-17
> **Andrew_P said:**
> If the cracker is employing a program to try passwords in some kind of sequence, and if you could figure out which ones he's already tried, set the password to one of those, assuming he's not going to re-run the ones that failed.  You could really mess with his mind.  Heh, heh. :twisted:
This is a really bad idea. The attacker is probably using a list of common passwords, and the next attacker is likely to use a similar list of common passwords. Changing your root password to a common password is a horrible idea. Use fail2ban and disable root logins if you need password authentication.

---

### Post by fernandoch on 2012-02-17
Thank you guys, very good stuff in here :)

I will check the denyhosts and fail2ban.

---

### Post by Dangertux on 2012-02-17
> **1clue said:**
> Why not change the name anyway?  That makes it one fewer pieces of information the attacker does not have about your box.  Better yet, it becomes a piece of MISinformation that they have.  They assume you have an account named root, and that is not true.

A large percentage of intrusions which try to get root authority assume that the super-user is called 'root'.  If they get a restricted account somehow and want full access, they are likely to write whatever hack based on 'root' instead of finding out what's in the /etc/passwd file.

I've been changing the root account name for years, never found a bad side-effect yet.  Goes back to 'defense in depth' and all that.

Because from an external point of view an account that is locked might as well not exist?

---

### Post by 1clue on 2012-02-18
> **Dangertux said:**
> Because from an external point of view an account that is locked might as well not exist?

That statement assumes that there can be no bugs in the lockout, or in any service which might incorrectly handle security.

It also assumes that no malicious attack could happen internally.

I'm a software developer.  I have seen lots of stupid stuff in the past.  I've seen lots of poorly secured or unsecured services, and some of it was somebody running suid on some script they hacked together just to get something working, fully intending to fix it later but later still hadn't come a year down the road.

Against the brute force ssh attack on a stock Ubuntu box, changing the name doesn't do anything at all because as you said, it's locked out anyway on Ubunutu.  If you changed that lockout, then trying to ssh as 'root' when 'root' is 'something_else' will fail.

If you have injected a script in an email and convinced the user to execute it, that script might be looking for 'root' and not find it because it doesn't exist.

It's true that trying tricks like 'sudo' don't care what the superuser is called, but sudoers is one of the first places you look when trying to secure your box.

---

### Post by HermanAB on 2012-02-20
Howdy,

Note that you can stop any and all brute force attacks with a one liner.

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

You don't need complicated things like fail2ban etc if you use this rule.

---

### Post by Lars Noodén on 2012-02-20
+1 for both using keys instead of password log in and limiting using IP Tables.  There is a lot to be said for keeping things simple.

---

