---
title: "Ipblock doesnt work-at all"
date: 2011-04-27
forum: Security
---

### Post by FLCL on 2011-04-27
I installed IPblock in hopes of having an application similar to PeerBlock, but it hasn't worked since install. It errors on update, and errors trying to enable it(different error code every time :/)

tried to enable program and got the following:

```
iplist[4783]:error:can't find badpeers.gz 
```

```
ipblock[4763]:error: failed to start, cleaning up
```
 
added lists, tried to update and I get this error...on every list. 

```
ipblock[3830]:error: update of (insert list here) has failed.
```

Anyone know how to get it to work?

---

### Post by Jive Turkey on 2011-04-28
I think ipblock is only supported up to Karmic (I was checking it out yesterday myself).  If it is strictly for bittorrent you might consider using a bt client that supports blocklists natively.  Barring that, I've been looking into configuring the blacklist in shorewall and using a cronned script to update that.

Good luck.

This might work for you too, PG2 for linux.
[http://forums.phoenixlabs.org/thread-643.html](http://forums.phoenixlabs.org/thread-643.html)

---

### Post by Jive Turkey on 2011-04-28
I found this article on the matter also:
[http://www.maeyanie.com/2008/12/efficient-iptables-peerguardian-blocklist/](http://www.maeyanie.com/2008/12/efficient-iptables-peerguardian-blocklist/)

Rather than piling on additional software, it uses what you already have.

---

### Post by jre on 2011-04-29
AFAIK iplist is also supported post karmic. The error message looks for me, as if you simply need to choose other downlist URLs.

As already noted you may also use PGL (if you want a GUI you can either try the current development version, or install moblock/blockcontrol/mobloquer).

Using ipset (from #3) may also be a good option, but you need to make manually your own iptables rules if more stuff is blocked then you want.

---

### Post by simonplexus on 2011-04-30
This is fixable. Not sure why, however it looks like a config file mistake perhaps?

According to /etc/ipblock.lists file, badpeers.gz is now downloading as templist.gz instead:

```

# malicious p2p peers
badpeers.gz             http://www.bluetack.co.uk/config/templist.gz

```And the config (/etc/ipblock.conf) specifies that ipblock should load 'badpeers.gz'

```

BLOCK_LIST="level1.gz ads-trackers-and-bad-pr0n.gz spyware.gz dshield.gz hijacked.gz badpeers.gz"

```when checking in the iplist cache dir, we see that templist.gz is there, but badpeers.gz is not

```

root@hfw1:~# ls -la /var/cache/iplist
total 4008
drwxr-xr-x  2 root root    4096 2011-02-24 22:37 .
drwxr-xr-x 18 root root    4096 2011-02-24 11:41 ..
-rw-r--r--  1 root root   39882 2011-04-30 07:38 ads-trackers-and-bad-pr0n.gz
-rw-r--r--  1 root root     473 2010-10-21 14:33 allow.p2p
-rw-r--r--  1 root root      42 2011-04-30 19:03 allow-perm.p2p
-rw-r--r--  1 root root       0 2011-04-30 19:03 allow-temp.p2p
-rw-r--r--  1 root root    1717 2011-04-30 07:38 dshield.gz
-rw-r--r--  1 root root    3008 2011-04-30 07:38 hijacked.gz
-rw-r--r--  1 root root 3753624 2011-04-30 07:38 level1.gz
-rw-r--r--  1 root root   48382 2011-04-30 07:39 spyware.gz
-rw-r--r--  1 root root  233016 2011-04-30 07:38 templist.gz
-rw-r--r--  1 root root       0 2011-04-30 19:02 .update-stamp

```my guess is that either a config file is bad in apt or ipblock is supposed to perform a rename and does not. The fix I made is editing /etc/ipblock.conf and changing badpeers.gz to templist.gz

```

BLOCK_LIST="level1.gz ads-trackers-and-bad-pr0n.gz spyware.gz dshield.gz hijacked.gz templist.gz"

``````

ipblock -u
ipblock -s

```Im not sure if this is the correct fix for this, however it will get you working again. I would recommend reading up on why templist.gz is added to the config file in the repository.

---

### Post by Jive Turkey on 2011-04-30
The moblock package in jre's ppa looks to work pretty well based on the limited testing I tried yesterday.

The iplist solution I suggested above seems to require patching iptables and/or maybe a manual kernel build which I might try since I'd also like to play with the TARPIT in iptables sometime.

---

### Post by jre on 2011-05-01
bluetack renamed templist to badpeers almost 2 years ago.

> **Jive Turkey said:**
> The iplist solution I suggested above seems to require patching iptables and/or maybe a manual kernel build which I might try since I'd also like to play with the TARPIT in iptables sometime.
Try adding these variables to /etc/blockcontrol/blockcontrol.conf. Then e.g. replace DROP with TARPIT. Of course, the kernel rebuild will still be necessary for TARPIT
```
REJECT_IN="DROP"
REJECT_OUT="REJECT"
REJECT_FW="DROP"

```

---

