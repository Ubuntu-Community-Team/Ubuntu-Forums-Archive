---
title: "Bridged VirtualBox"
date: 2008-08-27
forum: Virtualisation
---

### Post by FLCL on 2008-08-27
How do i go about bridging the network connections in VirtualBox? I don't see anything for it in the settings. Can anyone help me out?:confused:

---

### Post by Blind Tiger on 2008-08-27
Try the following link:
[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

Does NAT networking not suit your purposes?

---

### Post by FLCL on 2008-08-28
That helped quite a bit, but i am stuck at the part for finalizing the modifications to virtualbox.

> To take the modifications into account, restart the VirtualBox host networking script:

```
$sudo /etc/init.d/virtualbox-ose restart
```

The one in the help file is from the repos, which is the open source version. Mine is from the website, so the ose command does not work. I have tried it without the ose and the same effect. Does anyone know what command i would use?:confused:

---

### Post by Blind Tiger on 2008-08-28
A system restart should accomplish the same result.

---

### Post by FLCL on 2008-08-28
alright, and following the bridge, when followed this section, i got a message and im not sure if it was supposed to display or if that means i can't perform that action:

> Now make a bridge and put your current interface into it:```
sudo tunctl -t tap1 -u USERNAME
```

I received this following that command: 
```
Set 'tap1' persistent and owned by uid 1000

```

Any Idea?

---

### Post by FLCL on 2008-08-28
SO i continued on, but now im getting some problems with the bridge.

```
sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addif br0 eth0
```

Which gives me this error: 
> device eth0 is already a member of a bridge; can't enslave it to bridge br0.


Can someone please help?

---

