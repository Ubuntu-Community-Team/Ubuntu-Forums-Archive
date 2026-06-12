---
title: "What Is The Best IP Blocker?"
date: 2011-10-14
forum: Security
---

### Post by anicetus001 on 2011-10-14
:popcorn:

No reason other than wanting to have the best program on my Ubuntu 11.10.

I'm pretty new to Ubuntu, so this is why I ask. I like my privacy and security.

---

### Post by Dangertux on 2011-10-15
In my opinion iptables.  

```

sudo iptables -A INPUT -s 111.111.111.111 -j DROP
sudo iptables -A OUTPUT -d 111.111.111.111 -j DROP

```

I'm not sure that is the answer you're looking for though. I'm guessing you're looking for something for BT.

In that case something like this might help you

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by jre on 2011-10-15
I'd recommend PeerGuardian Linux (pgl), finally including a GUI, see my signature. It's the official succesor of moblock/blockcontrol/mobloquer.

Alternatively you may use iplist, see Dangertux's link. But it's author hasn't been here since a few months. So I don't know thether he will make any furhter updates. It works fine but you may to reconfigure it to use other list sources (The default ones frequently don't work).

Generally pgl and iplist do the same job. The more important question is what lists you use. For this have a look at iblocklist.com and choose those lists that match your needs. Take care not to choose too many lists.

---

