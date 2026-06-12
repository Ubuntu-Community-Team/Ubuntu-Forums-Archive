---
title: "my srver ssh is not connect...."
date: 2009-04-15
forum: Server Platforms
---

### Post by bnejoker on 2009-04-15
hi ,
how i appear configured the adress ip 192.168.0.1 ...
thank's.......... :p

---

### Post by sahabcse on 2009-04-15
type in terminal

ssh username@ipaddress

---

### Post by wirelessmonkey on 2009-04-15
Your other thread is still live and active, and if I hadn't already read it, this post would be quite confusing.
You need to verify that you are connecting to the right port on your server, from your local network.
Advice on how to do this was given in the previous post.

---

### Post by bnejoker on 2009-04-15
1-if i put these command in terminal :
```

root@nedjemeddine-desktop:~# ssh 10.102.0.87 -p 22
root@10.102.0.87's password: 
Permission denied, please try again.
root@10.102.0.87's password: 
Permission denied, please try again.
root@10.102.0.87's password: 

```
2-but when i put these command in terminal :
```
root@nedjemeddine-desktop:~# ssh 192.168.0.1 -p22
ssh: connect to host 192.168.0.1 port 22: Connection refused
root@nedjemeddine-desktop:~# 

```
so,where is wrong:in configuration of dhcp,or in ssh server .
thank's again ....

---

### Post by ikonia on 2009-04-16
1.) you are trying to login to an ubuntu machine as root - the root password is disabled so thats never going to happen and the sshd_config file will have root login disabled, so even if you set the password - it's not going to happen.

2.) you don't need to specify -p 22 - thats the default port

3.) you're trying 2 different ip addresses, ssh is listening AND you can get to it on the 10.X network, ssh is either not listening or you can't reach the 192.x network, 

The problem is your machine is not reachable using ssh on the 192.x network. Unless you have configured your machine to be on the 192.X network as well as the 10.x network there is no problem, its user error.

Access ssh using the 10.X address that the machine currently has and use a valid username

---

