---
title: "Best way to hide myself (other than my IP) from the outside world."
date: 2008-06-10
forum: Security
---

### Post by Private_Ops on 2008-06-10
Like my title says.

I've already got a PfSense firewall going but, I think this isn't enough.
I know there's things such as proxy's and all but, I've never fully grasped the concept of running a proxy server inside of a network.

Anyone care to explain?

Just a techy tryin to learn :)

---

### Post by Yuki_Nagato on 2008-06-10
Since you do no seem interested in hiding your IP, what else are you attempting to block out?  Do you want to hide what operating system you are using?  Do you want to stealth your ports?

As for **_ANONYMITY,_** (security by obscurity is very poor habit) The Onion Router is about as good as it gets, although very slow.

_[http://www.torproject.org/](http://www.torproject.org/)_

---

### Post by Dr Small on 2008-06-10
+1 for tor.

---

### Post by Private_Ops on 2008-06-10
> **Yuki_Nagato said:**
> Since you do no seem interested in hiding your IP, what else are you attempting to block out?  Do you want to hide what operating system you are using?  Do you want to stealth your ports?

As for **_ANONYMITY,_** (security by obscurity is very poor habit) The Onion Router is about as good as it gets, although very slow.

_[http://www.torproject.org/](http://www.torproject.org/)_


Stealthing ports would be sweet but, alas, I have VERY little experience with using ubuntu (IPtables) as a network firewall (did it for a project at school and didn't really learn much since my teacher provided me with a custom script).

The Tor thing looks interesting... haven't quite got the jist of it yet so I'll continue looking at it.

---

### Post by Dr Small on 2008-06-11
An example:
```
YOU >>>(unencrypted traffic)>>> {{(tor nodes, encrypted)}} >>>(unencrypted traffic)>>> DEST.
```

---

### Post by cdenley on 2008-06-11
> **Dr Small said:**
> An example:
```
YOU >>>(unencrypted traffic)>>> {{(tor nodes, encrypted)}} >>>(unencrypted traffic)>>> DEST.
```
I think that would be
```
YOU >>>(**encrypted** traffic)>>> {{(tor nodes, encrypted)}} >>>(unencrypted traffic)>>> DEST.
```
The data would be encrypted before it is sent to the first tor node. It would be unencrypted between the exit node and the server because the server wouldn't know how to encrypt/decrypt the traffic.

Anyone looking at your traffic going to the server can see it. Don't send any sensitive or identifiable data unless you're using SSL (https) encryption, and of course you trust whoever is hosting the site with that data. The idea is anything you send can be read, but they can't tell where it's originally coming from (in theory). However, it is so slow, I can't imagine a scenario where it would be worth it unless you're doing something illegal or something a site admin doesn't want you to do.

Tor itself doesn't really hide anything but your IP. Maybe you should look at using privoxy.

---

### Post by HermanAB on 2008-06-11
Devil's advocate: Why bother?  You are already running Linux.  Relax and enjoy it.

---

### Post by Private_Ops on 2008-06-11
> **HermanAB said:**
> Devil's advocate: Why bother?  You are already running Linux.  Relax and enjoy it.


I understand that not running windows (well, its still on the desktop but, it (the desktop) has mental problems and needs rebuilt) is a big step security wise but, I do advocate the idea of protecting yourself on the internet (and using it wisely).

I know my firewall is probably doing a good job (I don't check it often) but, I was just thinking of further possibilities of security.

---

### Post by cdenley on 2008-06-11
> **Private_Ops said:**
> I understand that not running windows (well, its still on the desktop but, it (the desktop) has mental problems and needs rebuilt) is a big step security wise but, I do advocate the idea of protecting yourself on the internet (and using it wisely).

I know my firewall is probably doing a good job (I don't check it often) but, I was just thinking of further possibilities of security.

If you want to increase your security, install the noscript plugin for firefox.
```

sudo apt-get install mozilla-noscript

```
It will protect you from flash vulnerabilities, and probably most firefox vulnerabilities.

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by Private_Ops on 2008-06-11
> **cdenley said:**
> If you want to increase your security, install the noscript plugin for firefox.
```

sudo apt-get install mozilla-noscript

```
It will protect you from flash vulnerabilities, and probably most firefox vulnerabilities.

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

Already got that. Have been running it for quite some time.... it's actually quite usefull but, can get annoying sometimes on some websites that I know are legit.

---

### Post by cdenley on 2008-06-11
Did you see the sticky thread I linked to? It covers everything I could think of regarding desktop security.

---

### Post by Private_Ops on 2008-06-11
> **cdenley said:**
> Did you see the sticky thread I linked to? It covers everything I could think of regarding desktop security.

No, thought that had to do with the FF plugin. I'll take a look at it.

---

