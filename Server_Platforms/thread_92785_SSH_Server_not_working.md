---
title: "SSH Server not working"
date: 2005-11-20
forum: Server Platforms
---

### Post by Dustismo on 2005-11-20
hi,

I have been trying to get sshd to work on my machine for awhile now..

I installed ssh and sshd using synaptic but it doesnt work.

when I try to connect from another box (within my network so its not a router/port forwarding problem) I get connection refused.

Here is the debug output.
```

$ /usr/sbin/sshd -d -d -d
debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 637
debug2: parse_server_config: config /etc/ssh/sshd_config len 637
debug1: sshd version OpenSSH_4.1p1 Debian-7ubuntu4
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.

```

and the list of /etc/ssh

```
~$ ls /etc/ssh
moduli      
sshd_config       
ssh_host_dsa_key.pub  
ssh_host_rsa_key.pub
ssh_config  
ssh_host_dsa_key  
ssh_host_rsa_key

```


Anybody help?

Thanks
Dustin

---

### Post by LordHunter317 on 2005-11-20
IS SSHD running?

---

### Post by Dustismo on 2005-11-20
Seems to be..  in the process lsting I can see /usr/sbin/sshd.

---

### Post by Glut on 2005-11-21
Possibly an issue with the permissions on /etc/ssh/ssh_host_???_key. They should only be read/writable by root.

---

### Post by irv on 2005-11-25
I believe I can add to this post: I have setup a server and a workstation. Both are running SSH. I can SSH from the server to the workstation using the Connect to Server from GNOME. but I can't from the destop to the server. But I can, from a command prompt. see below.
---------------------------------------------------------------
irv@ubuntu:/var/www/web$ ssh irv@192.168.0.100
irv@192.168.0.100's password:
Last login: Fri Nov 25 07:49:18 2005 from ubuntu
Linux wabasha-server 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
irv@wabasha-server:~$
--------------------------------------------------------
I am not sure if it is a bug or not. I didn't do anything different when I setup the server and workstation.

The problem is, when I try to use Connect to Server, setting the Service type to SSH, and just set the sever to the name or IP address and selecting "Connect" it sets up a mount point, but when I try to connect it give me a message after typing in the password three times:
Can't Display Location, Couldn't display "sftp://ipaddress or server name.
When I do all this at the server end, it takes the password and lets me in. I can see all the folder on my workstation.
My question is why doesn't it work from the workstation to the server?

---

### Post by irv on 2005-11-25
I found another little tid-bit about SSH. I have installed Konqueror, and if I use the remote from the Network place, I can ssh to the server from my workstation. The problem seems to be in GNOME desktop on Ubuntu 5.10 Breezy. It has to be a bug. 
I would like to report this, does anyone know where to do this?

---

### Post by s0c0 on 2005-11-27
In FreeBSD I had to add the user to the "wheel" group or something like that, though I've never experienced such an issue with SSH on Linux.  The sshd should work out of the box and always has for me.

---

### Post by Dustismo on 2005-11-27
[QUOTE=Glut]Possibly an issue with the permissions on /etc/ssh/ssh_host_???_key. They should only be read/writable by root.[/QUOTE]


I don't think so..  Here are the permissions on that directory..

```
$ ls -al /etc/ssh
total 168
drwxr-xr-x    2 root root   4096 2005-11-04 19:29 .
drwxr-xr-x  105 root root   4096 2005-11-27 10:18 ..
-rw-r--r--    1 root root 132839 2005-10-10 16:10 moduli
-rw-r--r--    1 root root   1361 2005-10-10 16:10 ssh_config
-rw-r--r--    1 root root   1891 2005-11-04 19:43 sshd_config
-rw-------    1 root root    668 2005-11-04 19:29 ssh_host_dsa_key
-rw-r--r--    1 root root    606 2005-11-04 19:29 ssh_host_dsa_key.pub
-rw-------    1 root root    887 2005-11-04 19:29 ssh_host_rsa_key
-rw-r--r--    1 root root    226 2005-11-04 19:29 ssh_host_rsa_key.pub

```

Any other ideas?

---

### Post by cactus on 2005-11-27
1) make sure you don't have any iptables (firewall) rules denying inbound port 22 (tcp) connections.
2) make sure you have "sshd: all", or some semblance of it, in /etc/hosts.allow
3) make sure your sshd daemon is running
4) sacrifice rubber chicken
5) Recommendation: Add "AllowUser user1 user2 user3" to your /etc/ssh/sshd_config file. This reduces the number of accounts that can be accessed via ssh...like denying root user ssh rights. If someone needs root, make them sudo.
6) Do the monkey dance.

---

### Post by pingswept on 2005-11-27
[QUOTE=Dustismo]I don't think so..  Here are the permissions on that directory..

```
$ ls -al /etc/ssh
total 168
drwxr-xr-x    2 root root   4096 2005-11-04 19:29 .
drwxr-xr-x  105 root root   4096 2005-11-27 10:18 ..
-rw-r--r--    1 root root 132839 2005-10-10 16:10 moduli
-rw-r--r--    1 root root   1361 2005-10-10 16:10 ssh_config
-rw-r--r--    1 root root   1891 2005-11-04 19:43 sshd_config
-rw-------    1 root root    668 2005-11-04 19:29 ssh_host_dsa_key
-rw-r--r--    1 root root    606 2005-11-04 19:29 ssh_host_dsa_key.pub
-rw-------    1 root root    887 2005-11-04 19:29 ssh_host_rsa_key
-rw-r--r--    1 root root    226 2005-11-04 19:29 ssh_host_rsa_key.pub

```[/QUOTE]

My permissions look identical, and my sshd is working, so it's probably not a permissions problem unless sshd is running as a non-root user. What's the output of:

ps -aux | grep sshd

Is sshd being run by root?

---

