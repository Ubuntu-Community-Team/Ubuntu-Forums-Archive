---
title: "Server Security"
date: 2010-09-16
forum: Security
---

### Post by WhiteElephant on 2010-09-16
I am going to be setting up a Ubuntu Server very soon, either to act as a primary domain controller or file storage. Either way I need an off-site backup solution to keep the data safe. I have looked at one company called Ibackup which provides backup using rsync. Is this the best method and is it secure?

To have an online backup solution the server needs internet access which worries me a little. Would setting up iptables to block all incoming wan connections be enough to protect it?

---

### Post by CharlesA on 2010-09-16
rsync can transfer files over ssh, which is encrypted, so it can't be read in transit.

You can set iptables to drop everything except what you want to let in, which is nice. :)

---

### Post by WhiteElephant on 2010-09-16
Looks like DropBox would be a better solution because it will allow me to backup the data and allow users access from home.

---

### Post by CharlesA on 2010-09-16
Indeed. :)

---

### Post by WhiteElephant on 2010-09-16
Is this the correct way to block all connections with iptables?
 
```

iptables --flush

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

```
 
I guess this will block LAN traffic too? If so, then do you know how I unblock samba traffic?

---

### Post by CharlesA on 2010-09-16
You would only need to set the INPUT chain as DROP.

However, I would not suggest doing that, since if you are connected remotely via SSH or the like, and you flush the rules, you'll get locked out.

Set everything to ACCEPT, but add a line that looks like this:

```
# Drop All
-A INPUT -j DROP

```

That'll drop anything that doesn't have a rule set for ALLOW.

Check [here]("http://bodhizazen.net/Tutorials/iptables/") a tutorial on iptables.

---

### Post by bodhi.zazen on 2010-09-17
> **WhiteElephant said:**
> Is this the correct way to block all connections with iptables?
 
```

iptables --flush

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

```I guess this will block LAN traffic too? If so, then do you know how I unblock samba traffic?

Rather then using a policy of DROP ( -P DROP) I suggest you keep the last rule in the chain as drop.

If you use these policy settings, and you then flush the rules, you will lock yourself out.

I also like iptables-save and iptables-apply (iptables-restore in init or network scripts).

---

### Post by jhayes on 2010-09-20
another thing good about rsynch, not only does it piggyback on ssh, but only copies the diif of the files. which can be a bandwidth saver. (or atleast that is what drunk me remembers.) but yeah say you move ssh to port 32154, open that port in iptables, block all else, then get ssh w/o passwords going. [http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html) 
and some other basic ssh security and you should be set.

---

### Post by CharlesA on 2010-09-20
> **jhayes said:**
> another thing good about rsynch, not only does it piggyback on ssh, but only copies the diif of the files. which can be a bandwidth saver. (or atleast that is what drunk me remembers.) but yeah say you move ssh to port 32154, open that port in iptables, block all else, then get ssh w/o passwords going. [http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html) 
and some other basic ssh security and you should be set.

Also note that you can transfer your public key to other machines by using this:

```
ssh-copy-id
```

---

