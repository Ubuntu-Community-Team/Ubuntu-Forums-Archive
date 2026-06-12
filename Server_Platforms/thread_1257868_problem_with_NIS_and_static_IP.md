---
title: "problem with NIS and static IP"
date: 2009-09-04
forum: Server Platforms
---

### Post by beaker15 on 2009-09-04
Hi

I'm setting up a NIS server in a test environment with just 2 PCs, one as the server, one as the client. They are both clean ubuntu installs with just updates applied and the nis package installed on both through synaptic. All config files seem to me to be correct.

The problem i have is that I boot up the server, which gets an address from DHCP and run /etc/init.d/nis start and the server starts up fine. Then if i change it to a static IP address and run the same command, i get an error like:

*Starting NIS Services

*binding to yp server
*.......
*.......
*.......
*.......
*.......
*.......
*....... [fail]


This is all before I've even booted up the client. Could this be related to nsswitch.conf?

I'm really stumped so any help on this is appreciated

thanks

---

### Post by HermanAB on 2009-09-04
Hmm... When you set the static IP address, do you modify /etc/hosts or a DNS so that the hostname and localhost resolves to the static address?

---

### Post by beaker15 on 2009-09-04
yeah, I had set the static IP addresses and hostnames in the /etc/hosts file, it was one of the first things i did. 

Actually, now you mention it.... I think i put both PCs in the host file so it would look something like this:

127.0.0.1    localhost
127.0.1.1    server1

192.168.0.1    server1
192,168.0.2    client1


that would probably explain it, i'll remove the second for entry server1 

Thanks Herman!

---

### Post by 480silverton on 2009-10-09
On your server make sure that in /etc/defaults/nis
the setting is set as

NISSERVER=true
NISCLIENT=false

and not
NISSERVER=master
NISCLIENT=false

Some instructions tell you to set the server on master when master does not even work. True and false works. Haha. I don't know if that is your problem at all but thats usually the problem that people have run into with NIS

---

