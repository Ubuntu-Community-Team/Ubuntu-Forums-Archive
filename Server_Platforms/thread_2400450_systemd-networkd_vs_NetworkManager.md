---
title: "systemd-networkd vs NetworkManager"
date: 2018-09-06
forum: Server Platforms
---

### Post by 1Waffle on 2018-09-06
Hopefully I am in the right place for this. From what I can tell, out of the box, Ubuntu Server 18.04 ships with systemd-networkd, and Ubuntu Desktop 18.04 ships with NetworkManager.  

I am curious as to why Ubuntu Server uses systemd-networkd rather than NetworkManager.  In reverse I can imagine networkd causing issues with Gnome.  Would there be any major consequence with replacing networkd with NetworkManager on my system?  For me (a near layman), a  NetworkManger's killer feature is its shared connection option.  Though I should probably figure out how it works eventually. (My guess is it interacts with iptables/ufw, but ...)

I am also aware of netplan.

---

### Post by darkod on 2018-09-06
I can't answer your question directly but just to remind you that Ubuntu Server was not using NM even before 18.04 and systemd/networkd. At least to my knowledge... NM was for the GUI of Ubuntu Desktop. Not included in the server versions regardless whether systemd was used or not.

As for sharing connection, you only need to allow ip forwarding and create MASQUERADE rule in the nat table of iptables. That should do it for simple routing/forwarding of traffic. After that you can tell clients to use your ubuntu server ip as gateway and it should work.

---

