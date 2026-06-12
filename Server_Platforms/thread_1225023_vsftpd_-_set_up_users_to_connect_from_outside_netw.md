---
title: "vsftpd - set up users to connect from outside network"
date: 2009-07-28
forum: Server Platforms
---

### Post by ade234uk on 2009-07-28
Ok I managed to install vsftp and set this up for local only.
What I would like to do is the following:

1) Set up a user with username and password

2) Set up the directory a user will get to once logged in from outside the network

3) Set up vsftp to allow access from one or two IP address outside the network.

Like setting up Apache, do I open up port 22 on the router, and forwarding all requests to the ipaddress of the ftp server i.e 192.168.0.4

---

### Post by drave99 on 2009-07-28
any user with an account on the box will be able to connect, there home directory is the default location when they login

make ABSOLUTELY SURE that anonymous connections are disabled so ONLY users with an account can connect

you might want to restrict users to there own home directories with the "chroot_local_users" option. then use links if they need to get elseware

restricting connections from one or two IP address's is a firewall thing, see iptables. yes you have to use port forwarding for port 22

---

### Post by ade234uk on 2009-07-28
Thank you very much for your help.
The whole point of this excercise is to turn my redundant machine in to one file server, so I can get all the files off my External hard drives and in one place.

---

### Post by ade234uk on 2009-07-29
The worked brilliantly. 

I can now login in to ftp with my username and password. How do I specify a directory, then lock the user to that directory?

---

