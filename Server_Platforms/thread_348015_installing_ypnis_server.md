---
title: "installing yp/nis server"
date: 2007-01-28
forum: Server Platforms
---

### Post by afftrash on 2007-01-28
Hi,
I'm kinda new to Ubuntu, and I've just installed my 4th  ubuntu machine.
I want it to be the nfs and yp server.
I managed to install the nfs.
But can't find any information about installing the nis/yp server.

Basically, I want all other machines to login through that machine.
Provide all the hosts and users map.

btw: is it possible to connect a windows machine to a that nis server ?

Thanks in advance.

---

### Post by Koybe on 2007-01-28
you need to install nis :
```
apt-get install nis
```Edit /etc/default/nis
```
NISSERVER=master
NISCLIENT=false
```Edit /etc/ypserv.securenets and add a line mathcinf your lan connection
```
255.255.255.0 192.168.1.0
```Restart nis
```
/etc/init.d/nis restart
```Prepare your user database :
Edit /var/yp/Makefile and set the min/max uid to match the users who can access NIS. I usaually put a higher number such as 10000 and then create my users with such a uid/gid.
```
MINUID=10000
MINGID=10000
```Add your users/group, then make the NIS database (follow on screen instructions) :
```
/usr/lib/yp/ypinit -m

```You can check services are running ok (ypserv, yppasswd, ypwxfrd)
```
rpcinfo -p
```On the client it's quite easy :
Be sure to set the correct NIS domain in /etc/defaultdomain then put the ip of the server in /etc/yp.conf
```
ypserver 192.168.1.1
```Modify /etc/nsswitch.cond to match nis
```
passwd: compat nis
group: compat nis
shadow: compat nis
```Restart nis
 ```
/etc/init.d/nis restart
```Have a check :
```
getent passwd
getent group
```

I hope this can help ;)

---

### Post by cdmdotnet on 2007-12-25
one small typo in your instructions:

Modify /etc/nsswitch.cond to match nis

the .cond should be .conf

---

