---
title: "twenty identical servers -how best to add a packages to them all"
date: 2007-06-13
forum: Server Platforms
---

### Post by Zendal Darkman on 2007-06-13
Rather than logging into each server individually, could anyone advise on the simplest way to add packages to them all and receive information that the packages was successfully added.

thanks

---

### Post by craigp84 on 2007-06-13
Hi Zendal Darkman,

There's no quick fix. You really should setup a proper network infrastructure to assist you with these boxes. I would type more here about how you should setup NFS (or other file sharing) and NIS (or ldap or something) and create you're own apt-repository (see apt-proxy, and google) to make this easier to manage yada yada but my fingers hurt right now so i'll keep it short...

Ok i lied about the no quick fix, but please, get something sensible in place, it'll save you time longer term.

On your linux workstation:
```
sudo apt-get install clusterssh
```

Then cssh server1 server2 server3...

Probably worthwhile setting up some public key authentication too:

On your linux workstation:
```
ssh-keygen -t dsa
cat .ssh/id_dsa.pub | ssh user@server1 'cat - >> ~/.ssh/authorized_keys'

```

Then add the command "ssh-add" in System -> Preferences -> Session or wherever it is (i'm on RHEL just now so can't check).

Bit of a brain dump but hope it helps.

-c

---

### Post by MJN on 2007-06-13
Also check out Johndoesacc's recent post (#20 at [http://ubuntuforums.org/showthread.php?t=464131](http://ubuntuforums.org/showthread.php?t=464131)) which discusses **omnitty** which may be of use/interest.
 
Mathew

---

### Post by Zendal Darkman on 2007-06-13
Thanks guys!
I've given clusterssh a go and it seems to do exactly what I wanted, and fits in nicely with the KIS rule.
If there were more servers and I needed to add packages on a frequent basis then it could be a bit cumbersome, but as things stand its ideal!

---

### Post by turinglabs on 2007-06-13
You may also want to try dsh, which will run multiple, remote commands via SSH with a single command on the client. It's a bit less cumbersome than clusterssh when you have lots of servers. I have a howto here: 

[http://geekpit.blogspot.com/2006/03/remotely-administering-groups-of.html](http://geekpit.blogspot.com/2006/03/remotely-administering-groups-of.html)

---

