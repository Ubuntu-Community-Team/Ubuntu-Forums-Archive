---
title: "Firewall"
date: 2004-11-04
forum: Server Platforms
---

### Post by Artiom on 2004-11-04
It might be a stupid question, but do I need firewall ?

(coming from windows, where without firewall you couldn't live for an hour)

---

### Post by jdodson on 2004-11-04
its not a stupd question at all, though i would recommend searching the forums on your topic before posting :grin: here is a very excellent [resource for you](http://www.ubuntuforums.org/showthread.php?t=1597&highlight=firewall) on your question.

---

### Post by Artiom on 2004-11-04
thanks, but those links tell me how to install, not if I need it.

My question is, as regular user of internet, do I need firewall?

---

### Post by jdodson on 2004-11-04
read it again.  ok, i will be nice i will paste text out of the post that starts the whole thread, i would recommend not just skimming documents::grin: 

**QUOTED FROM Gecko**
Holy Batman! Why doesn't Ubuntu come with a firewall?

Layman's Terms
It does not need one. It does not have anything listening to the network.

Technical Term's
Since Ubuntu doesn't run any daemons that listen to the outside world by default (the postfix install only listens on localhost) there's no need for a default firewall. The rationale is that if a user's got a need for installing a world-facing daemon, they'll be aware that they should configure a firewall/ACL for it too.

---

### Post by Artiom on 2004-11-04
thanks for your effort  :o 

Now I have general idea about firewall - if you are not running server or something like that, then you don't need it.  :mrgreen:

---

### Post by bluefuse on 2004-11-06
coming from a windows world, as I have, hackers and young school kids sitting at home decide to make more fun of the day looking for windows machines to violate, by default in XP telnet and other services are already armed. if you are in windows go to the run command and type in services.msc then you will soon realize why zonealarm and some other firewalls and a must. I always consider a good router a must, even a unix box can be hacked and violated....

---

### Post by bluefuse on 2004-11-06
just a quick note lookup shorewall in the spm manager....

---

### Post by jdong on 2004-11-07
[QUOTE=Artiom]thanks for your effort  :o 

Now I have general idea about firewall - if you are not running server or something like that, then you don't need it.  :mrgreen:[/QUOTE]

Actually, I can't comprehend why a properly configured server would need a firewall. Using a firewall is like wrapping your entire house in duct tape to shut the door. It's better to start off better configured.


Note that when new services are installed, they default to auto-starting. If you're an install junkie, then maybe a firewall is a good layer of security!

---

### Post by HiddenWolf on 2004-11-13
Can anyone advice me, If I tell apache to come up automaticly, but only to listen to localhost/80, I should be safe right.

I currently have apache and mysql running since I enjoy building sites in php, but I've never given configuration a lot of concern.

---

### Post by Magneto on 2004-11-13
[QUOTE=HiddenWolf]Can anyone advice me, If I tell apache to come up automaticly, but only to listen to localhost/80, I should be safe right.

I currently have apache and mysql running since I enjoy building sites in php, but I've never given configuration a lot of concern.[/QUOTE]

You should be fine.  do a netstat -l  that will tell you all your open -l istening ports

---

### Post by Artiom on 2004-11-13
[QUOTE=jdong]Actually, I can't comprehend why a properly configured server would need a firewall. Using a firewall is like wrapping your entire house in duct tape to shut the door. It's better to start off better configured.


Note that when new services are installed, they default to auto-starting. If you're an **install junkie**, then maybe a firewall is a good layer of security![/QUOTE]

I am.  #-o

---

### Post by HiddenWolf on 2004-11-13
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.locald:sunrpc *:*                     LISTEN
tcp        0      0 localhost.localdoma:www *:*                     LISTEN
tcp        0      0 localhost.localdoma:725 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
udp        0      0 *:bootpc                *:*
udp        0      0 localhost.locald:sunrpc *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     11132    /tmp/orbit-hidde/linc -1799-0-29bc52854d038
unix  2      [ ACC ]     STREAM     LISTENING     10976    /tmp/orbit-hidde/linc -177a-0-7cc0033f9b027
unix  2      [ ACC ]     STREAM     LISTENING     22501    /tmp/orbit-hidde/linc -1ed2-0-278f7a806afb1
unix  2      [ ACC ]     STREAM     LISTENING     22557    /tmp/orbit-hidde/linc -1edf-0-33b939935562c
unix  2      [ ACC ]     STREAM     LISTENING     16645    /tmp/orbit-root/linc- 1a6d-0-49208783d35f5
unix  2      [ ACC ]     STREAM     LISTENING     9078     /var/run/dbus/system_ bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     9295     /var/run/mysqld/mysql d.sock
unix  2      [ ACC ]     STREAM     LISTENING     9833     /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     10355    @/tmp/dbus-q3XItKRFcE
unix  2      [ ACC ]     STREAM     LISTENING     9001     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     10870    /tmp/orbit-hidde/linc -1773-0-5833849d60898
unix  2      [ ACC ]     STREAM     LISTENING     10895    /tmp/orbit-hidde/linc -1777-0-714819bbb3e73
unix  2      [ ACC ]     STREAM     LISTENING     10350    /tmp/ssh-hyfXll5861/a gent.5861
unix  2      [ ACC ]     STREAM     LISTENING     10370    /tmp/orbit-hidde/linc -171d-0-2db2c17261056
unix  2      [ ACC ]     STREAM     LISTENING     10380    /tmp/orbit-hidde/linc -16e5-0-3d403d916b2b9
unix  2      [ ACC ]     STREAM     LISTENING     10511    /tmp/.ICE-unix/5861
unix  2      [ ACC ]     STREAM     LISTENING     10519    /tmp/keyring-3WNiUu/s ocket
unix  2      [ ACC ]     STREAM     LISTENING     10529    /tmp/.esd/socket
unix  2      [ ACC ]     STREAM     LISTENING     10541    /tmp/orbit-hidde/linc -172e-0-2953ec53ef970
unix  2      [ ACC ]     STREAM     LISTENING     10562    /tmp/orbit-hidde/linc -1730-0-79a110625c34f
unix  2      [ ACC ]     STREAM     LISTENING     10160    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10571    @/tmp/fam-hidde-
unix  2      [ ACC ]     STREAM     LISTENING     10681    /tmp/orbit-hidde/linc -1756-0-1245f1bdadb1f
unix  2      [ ACC ]     STREAM     LISTENING     10721    /tmp/orbit-hidde/linc -175e-0-38aa0c6772d10
unix  2      [ ACC ]     STREAM     LISTENING     10729    /tmp/orbit-hidde/linc -1762-0-38aa0c67777b2
unix  2      [ ACC ]     STREAM     LISTENING     10798    /tmp/orbit-hidde/linc -1760-0-26d8fec366c88
unix  2      [ ACC ]     STREAM     LISTENING     10823    /tmp/orbit-hidde/linc -1770-0-4336fb999c2e0
unix  2      [ ACC ]     STREAM     LISTENING     11001    /tmp/orbit-hidde/linc -178e-0-d7d92ff124de
unix  2      [ ACC ]     STREAM     LISTENING     11020    /tmp/orbit-hidde/linc -1790-0-d7d92ff6dd7b
unix  2      [ ACC ]     STREAM     LISTENING     11097    /tmp/orbit-hidde/linc -1792-0-29bc528555a6
unix  2      [ ACC ]     STREAM     LISTENING     10952    /tmp/mapping-hidde

```

Sounds like a lot.

---

### Post by Magneto on 2004-11-13
[QUOTE=HiddenWolf]```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.locald:sunrpc *:*                     LISTEN
tcp        0      0 localhost.localdoma:www *:*                     LISTEN
tcp        0      0 localhost.localdoma:725 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
udp        0      0 *:bootpc                *:*
udp        0      0 localhost.locald:sunrpc *:*

```

Sounds like a lot.[/QUOTE]


these are the ones you need to look at-  with tcp and udp protocol listings
all your ports that are listening are local and not exposed to the world so you are safe
this is why the fine gentleman in a prior post noted that a properly configured server does not need a firewall- you have no open exposed ports - if you do have ports that are open but that only are used by properly maintained software you are safe

edited to compensate for sleepdeprivationinduced non-clarity

---

### Post by HiddenWolf on 2004-11-13
[QUOTE=Magneto]these are the ones you need to look at-  with tcp and udp protocol listings
all your ports that are listening are local and not exposed to the world so you are safe
this is why the fine gentleman in a prior post noted that a properly configured server does not need a firewall- no open exposed ports - or ports that are open but that only are used by properly maintained software[/QUOTE]

Good, thanks man.

---

