---
title: "ssh requesting password twice"
date: 2017-05-23
forum: Virtualisation
---

### Post by pkoukoulis-r on 2017-05-23
I am attempting to connect to a router using SSH, running 64-bit Lubuntu 17.04, which I have configured in VirtualBox. 
It connects, but only after requesting for the password twice. 

The hostname and hosts files on Lubuntu appear as follows:

```
pl@router1:/etc$ cat hosts
# 127.0.0.1    localhost
127.0.1.1       router1    


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
pl@router1:/etc$ cat hostname
router1
```

The command to connect is:
```
$ ssh -l pl -p 14601 localhost
pl@localhost's password: 
Welcome to Ubuntu 17.04 (GNU/Linux 4.10.0-21-generic x86_64)


0 packages can be updated.
0 updates are security updates.


Last login: Tue May 23 09:47:10 2017 from 10.0.2.2
[....] Starting ssh (via systemctl): ssh.service==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'ssh.service'.
Authenticating as: pl,,, (pl)
Password: 
==== AUTHENTICATION COMPLETE ===
. ok 
pl@router1:~$ 
```

The port forwarding rule in VirtualBox appears as shown below.


Any suggestions as to how to ensure the password is only requested once or not at all ?

Thanks

---

### Post by TheFu on 2017-05-23
What is the router IP?
What is the host's IP?

The /etc/hosts file seems wrong.  127.0.x.x IPs are localhost - cannot be used to access different machines usually (without some sort of tunnel configured and working).

If you are ON the router, then connecting to localhost isn't an issue.

Whenever troubleshooting anything on Linux, always check the logs.  **ssh -vvv** could be helpful too.

If running inside virtualbox, is it a bridged network or NAT'ed?

---

### Post by ajgreeny on 2017-05-23
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by efflandt on 2017-05-24
Why did you comment out localhost in /etc/hosts? 127.0.0.1 is "always" localhost. Uncomment that and see if it works as expected. Although, I personally specifically disallow passwords and use keys only.

---

