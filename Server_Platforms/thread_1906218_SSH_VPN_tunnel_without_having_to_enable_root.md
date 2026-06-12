---
title: "SSH VPN tunnel without having to enable root"
date: 2012-01-08
forum: Server Platforms
---

### Post by NetSkay on 2012-01-08
ive been trying to setup a VPN SSH tunnel and ive had success executing ssh -Nv -w 0:0 root@192.168.2.2 -p 50

however what i am wondering is, can i do the tunneling without having root unlocked when i try ssh -Nv -w 0:0 $username@192.168.2.2 -p 50 and have root acccount disabled while $username is set in sudoers, i get an administratively prohibited

so my question is, can i do the tunnel without having root enabled? thnx :)

---

### Post by hawkmage on 2012-01-08
A process can't bind to a port under 1025 without being root.  I am not sure what you mean by "without having root enabled" but you should be able to do it using sudo.

---

