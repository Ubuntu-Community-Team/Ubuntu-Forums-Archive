---
title: "search for samba-shares stop working."
date: 2011-12-05
forum: Server Platforms
---

### Post by Azyx on 2011-12-05
Hi.
I have some sambaservers in my home under 192.168.0.1 subnet 255.255.255.0. On one 11.10 i have added this to the end off /etc/samba/smb.conf :

```
#Added shares
[Downloads-guest]
path=/home/a/Downloads
read only = yes
guest ok = yes
[500GB-guest]
path=/home/a/500GB
read only = yes
guest ok = yes
[COLOR="RoyalBlue"][500GB][/COLOR]
path=/home/a/500GB
read only = no
guest ok = no
valid users = a
[Media-guest]
path=/media
read only = yes
force user = a
guest ok = yes
[Media]
path=/media
read only = no
force user = a
guest ok = no
```

As you may see I share some a read-only and gest bcos i want to reach for instance music or moves without possibillity to remove or change places of the files. I have also some 'force user' bcos they are in ntfs- or hfs- filesystem from USB. 

Today, just then I chages Icones of the [COLOR="rgb(65, 105, 225)"]500GB[/COLOR]-disk, and and unmount, to see If , I was not able to mount again.

Not only my media computer 11.10 dissapeare, also nother machine i have for some backop are not able to se thrue Places-->nertwork...

But I can connect, If I chose Place-->'Connect to server' Ip to my machines 

So it the network-browser that not work. Before when I open Place--> Network frist my computers appeare, and then one 'Windows network' and then 'WORKGROUP, and under the the Computers again.

/Cheers

---

