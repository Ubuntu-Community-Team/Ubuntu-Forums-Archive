---
title: "Newb: How likely am I to get hacked?"
date: 2007-11-08
forum: Server Platforms
---

### Post by Smartin on 2007-11-08
Hi,

I hope this isn't a stupid question but I'm new to all this...

I have a Feisty box which I use as an ftp server, running Proftp.

I have Firestarter installed also.

I also want to install OpenGroupware eventually.

Ports 20-21 are open to the internet as are ports 40000-50000.

Port 80 is open also, apache2 is running with the latest php5 and mySQL.

Only ports 20-21, 80 are forwarded from the router.

Ubuntu is set to install security updates without asking.

ssh is *not* running.

Postfix is running but not configured yet. (Still struggling ;-)

There is only one user on the box, with a decent password.

Am I relatively safe from hacks/intruders or are there some other basic things I should be doing?

I'm petrified of it being used as a spam factory.

Grateful for any comments.

Thanks!

Simon

---

### Post by HermanAB on 2007-11-08
Howdy,

You should lock things down a little using shorewall, since it protects against various nasties.  You can also add some simple rate limiting to slow down any attacks or spam blasting attempts.  Google for "iptables rate limit".

The most important thing is to use looooong passwords with 9 or more characters.  I use 16 character semi-pronounceable passwords on all public servers.  Usually a box gets hacked because some bright spark used a 4 character password.

Cheers,

H.

---

### Post by Smartin on 2007-11-08
> **HermanAB said:**
> Howdy,

You should lock things down a little using shorewall, since it protects against various nasties.  You can also add some simple rate limiting to slow down any attacks or spam blasting attempts.  Google for "iptables rate limit".

The most important thing is to use looooong passwords with 9 or more characters.  I use 16 character semi-pronounceable passwords on all public servers.  Usually a box gets hacked because some bright spark used a 4 character password.

Cheers,

H.

Herman,

Thanks for the Shorwall pointer but it looks a bit daunting for a newb :-)

Isn't firestarter sufficient?

Simon

---

### Post by HermanAB on 2007-11-08
Yup, firestarter is fine too.  I just don't like the interactive crud, but you can turn that off.  The interactive alerts are not actually useful at all:
Oh, lookee! You got an illegal packet! 
So delete the damn thing and leave me alone...

A system will work mostly fine with no filtering at all too, but once in a while, you can get hit by a script kiddie that can slow the machine down with a flood of broken packets.

Cheers,

H.

---

### Post by oregonbob on 2007-11-08
The firestarter interactive is a great teaching tool for users who want to understand more about iptables, firewalls, hack attempts, etc. Really all it is is a iptables log viewer.

My problem is the GUI quits mysteriously, and then won't start back up.

---

### Post by Smartin on 2007-11-09
> **HermanAB said:**
> Yup, firestarter is fine too.  I just don't like the interactive crud, but you can turn that off.  The interactive alerts are not actually useful at all:
Oh, lookee! You got an illegal packet! 
So delete the damn thing and leave me alone...

A system will work mostly fine with no filtering at all too, but once in a while, you can get hit by a script kiddie that can slow the machine down with a flood of broken packets.

Cheers,

H.

Herman,

Sounds like I'm in reasonable shape then...?

I have turned all the alerts of in FS...

Simon

---

### Post by Smartin on 2007-11-09
> **oregonbob said:**
> The firestarter interactive is a great teaching tool for users who want to understand more about iptables, firewalls, hack attempts, etc. Really all it is is a iptables log viewer.

My problem is the GUI quits mysteriously, and then won't start back up.

Oregonbob,

Have to say I haven't seen the gui quit but I haven't spent much time with it...

Simon

---

### Post by HermanAB on 2007-11-09
You can list the firewall rules with:
$ sudo iptables -L

but you need to read the iptables man page at least 5 times before that listing will begin to make sense...

If you see the following, then you have NO firewall:
```
[root@odin ~]# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
[root@odin ~]# 

```

If you get a long list of gobbledygook, then you are probably OK.

Cheers,

Herman

---

### Post by Smartin on 2007-11-09
> **HermanAB said:**
> You can list the firewall rules with:
$ sudo iptables -L

but you need to read the iptables man page at least 5 times before that listing will begin to make sense...

If you see the following, then you have NO firewall:
```
[root@odin ~]# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
[root@odin ~]# 

```

If you get a long list of gobbledygook, then you are probably OK.

Cheers,

Herman

Herman,

That's a great tip. Thanks!

Simon

---

