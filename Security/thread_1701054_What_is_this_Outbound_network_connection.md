---
title: "What is this Outbound network connection?"
date: 2011-03-05
forum: Security
---

### Post by alphaamanitin on 2011-03-05
Hey guys,

Just ran this command:

```
sudo lsof -i -P -n
```

From this thread:

[http://ubuntuforums.org/showthread.php?t=1696699](http://ubuntuforums.org/showthread.php?t=1696699)

and got this:

```
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1011 avahi   13u  IPv4   8355      0t0  UDP *:5353 
avahi-dae 1011 avahi   14u  IPv6   8356      0t0  UDP *:5353 
avahi-dae 1011 avahi   15u  IPv4   8357      0t0  UDP *:41674 
avahi-dae 1011 avahi   16u  IPv6   8358      0t0  UDP *:53483 

```

I looked it up and it is something to do with finding other computers and printers on the same network. > **cariboo907 said:**
> There is no need to block outbound  connections, as there aren't any until you the user initiate them.

He says you need to initiate outbound connections.  How did I initiate that?  The other things I saw in there I know what I did to initiate, but makes me a little nervous that I initiated something not knowing it.

AlphaA

---

### Post by BkkBonanza on 2011-03-06
Avahi isn't generally a problem. Those lines you see are UDP protocol (which is connectionless) and hence, not connections. It's probably avahi listening for local data communication. You might try **netstat -nup** and **netstat -nulp** to see what addresses avahi is using. I would expect it to be localhost or LAN oriented. 

I did a quick check on my system and didn't see any avahi stuff - but I also vaguely recall removing avahi some time ago as it does stuff I don't need (local name services for MS/Apple) since I don't use MS or Apple on my network.

---

### Post by alphaamanitin on 2011-03-06
Ah.  interesting.  I need to learn more about this type of stuff.  Thanks for the info.

AlphaA

---

### Post by EJeanmaire on 2011-03-07
Someone can correct me if I am wrong, but Avahi does some network "chatting" to offer your shared devices and files and to determine if there are some other networked computers out there that are offering devices and files using MS RPC/Samba or Apple sharing.  I remove this on all of my Ubuntu installations, however, I'm assuming its there for ease of use.  When shared drives "automagically" pop up in your file explorer, thats from Avahi.

---

### Post by alphaamanitin on 2011-03-09
Will just 
```
sudo apt-get remove avahi
```get rid of it all?

AlphaA

---

### Post by BkkBonanza on 2011-03-09
I don't recall now the exact steps I used to remove it. It was something like as you suggested but the name could be different. There is a forum post here that discusses this and how it's done so I would suggest searching for it.

A quick check using "aptitude search avahi" suggests it may be "avahi-daemon".

---

### Post by alphaamanitin on 2011-03-10
Thanks.  I'll search out those posts.

AlphaA

---

