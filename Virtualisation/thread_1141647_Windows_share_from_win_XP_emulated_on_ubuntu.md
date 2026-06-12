---
title: "Windows share from win XP emulated on ubuntu"
date: 2009-04-28
forum: Virtualisation
---

### Post by rado3105 on 2009-04-28
Hi is possible to get from windows xp installed on vmware on ubuntu 9.04 to windows share(samba on server) located on network pc with ubuntu 9.04 is connected to?
It should be, because when I insalled vmware I chose NAT option. But I cant get to my server from emulated win XP. Also I have mounted that server(samba) on my ubuntu 9.04: /media/server.
Please can anybody help?

---

### Post by veloce on 2009-04-29
> **rado3105 said:**
> Hi is possible to get from windows xp installed on vmware on ubuntu 9.04 to windows share(samba on server) located on network pc with ubuntu 9.04 is connected to?
It should be, because when I insalled vmware I chose NAT option. But I cant get to my server from emulated win XP. Also I have mounted that server(samba) on my ubuntu 9.04: /media/server.
Please can anybody help?

NAT was the wrong option.  You are much better with Bridged to do this. 

(with NAT would need you to set up specific routing tables for each machine trying to contact your xp vm.)

---

### Post by rado3105 on 2009-04-30
I set it during vmware installation, is possible to change it after installation? I have tree interfaces in vmware net0, net1, net2

---

### Post by rado3105 on 2009-04-30
also internet is working, and that server is on network, physical pc is connected to, so it should be possible to connect to that server from virtual machine?

---

### Post by veloce on 2009-04-30
> **rado3105 said:**
> I set it during vmware installation, is possible to change it after installation? I have tree interfaces in vmware net0, net1, net2

You might have bridged networking set up as well.  See if you can change the virtual nic to the bridged network.

If not,just run /usr/bin/vmware-config.pl

---

### Post by veloce on 2009-04-30
> **rado3105 said:**
> also internet is working, and that server is on network, physical pc is connected to, so it should be possible to connect to that server from virtual machine?

Yes, it should work in that direction - depending on any firewall running on the host.

---

