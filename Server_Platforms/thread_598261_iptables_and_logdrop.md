---
title: "iptables and logdrop"
date: 2007-10-31
forum: Server Platforms
---

### Post by Roxxor on 2007-10-31
I am learning iptables. Why does this command give this message:
```
root@roxxor-desktop:~# iptables -A INPUT -p tcp --destination-port 12345 -j logdrop
iptables v1.3.6: Couldn't load target `logdrop':/lib/iptables/libipt_logdrop.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.

```

---

### Post by MJN on 2007-10-31
The -j option specifies the target, i.e. what to do with the packet. As it stands it is looking for the 'logdrop' chain but this presumably doesn't exist. 
 
Based on what I imagine you're trying to do, create it with:
 
```
sudo iptables -N logdrop
sudo iptables -A logdrop -j LOG
sudo iptables -A logdrop -j DROP

```
 
Matching packets will then be sent to the logdrop chain which will log them then drop (the LOG and DROP targets are pre-defined actions (hence written in uppercase for clarity)
 
Run iptables -L to see a list of your chains once you've done the above - it'll probably make more sense. Speaking of sense, there are a million and one iptables HowTo's which is a problem in itself so I suggest having a read of the iptables man page (the whole lot - it's not that long) as whilst it won't turn you into an expert it will at least provide some context of how this thing works. Most will go over your head but having read it once you may find learning from the HowTo's a little easier. It may also teach you that there's not all that much to iptables - the skill is in what you do with it. A bit like bricks and mortar - simple entities within themselves but combined together by someone that knows what they're doing and the sky is the limit... (hmm... not my best analogy!)
 
I don't use a firewall myself so this is all based on my notes from when I did once dabble in this area so somebody who knows what they're talking about is more than welcome to correct me if I'm wrong!
 
Mathew

---

