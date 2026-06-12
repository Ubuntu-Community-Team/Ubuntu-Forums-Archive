---
title: "nfs problems"
date: 2006-09-15
forum: Server Platforms
---

### Post by dannytherocker on 2006-09-15
Hi guys,

I've a sharing problem with my 2 Ubunts (desktop & laptop).
I followed many guides on nfs but I got no good results: 
Add these lines to /etc/exports: 
/ 192.168.1.2/192.168.1.5(rw,sync)
This way I want my server to share the filesystem with all clients within the range .1.2/1.5
So open my terminal on the client and try to mount shared "/" on a client's share folder (/media/exported) I created before. This is the code:
mount -t nfs 192.168.1.2:/ /media/exported
where 192.168.1.2 is my server's ip.
Unfortunately I get this error (don't know the exact english-ubuntu-version words): failed, access denied!
denied??? I don't use firewall or something...my only protection is my router's nat.
Any suggest?
thanks in advance

---

### Post by tagra123 on 2006-09-15
> **dannytherocker said:**
> Hi guys,

I've a sharing problem with my 2 Ubunts (desktop & laptop).
I followed many guides on nfs but I got no good results: 
Add these lines to /etc/exports: 
/ 192.168.1.2/192.168.1.5(rw,sync)
This way I want my server to share the filesystem with all clients within the range .1.2/1.5
So open my terminal on the client and try to mount shared "/" on a client's share folder (/media/exported) I created before. This is the code:
mount -t nfs 192.168.1.2:/ /media/exported
where 192.168.1.2 is my server's ip.
Unfortunately I get this error (don't know the exact english-ubuntu-version words): failed, access denied!
denied??? I don't use firewall or something...my only protection is my router's nat.
Any suggest?
thanks in advance


I believe whether you have a firewall program installed or not -- iptables is working. Try installing firestarter and opening up the nfs ports.

The second thing you can do which also makes life easier is to edit the /etc/hosts file. Edit the hosts file on each computer. This solved the issue for me using static ip addresses -- the router didn't seem to properly assign names. I also lets you call the computer by name rather than an ip address.

computer1 192.168.1.2
computer2 192.168.1.3
computer3 192.168.1.4
computer4 192.168.1.5

When finished editing the files restart nfs and portmap.

sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/portmap restart

It should work.

If not try pinging the other PC and make sure you are getting a response ping 192.168.1.2 etc...

Also: Are you sure you want to share the entire filesystem?

---

### Post by dannytherocker on 2006-09-16
> **tagra123 said:**
> I believe whether you have a firewall program installed or not -- iptables is working. Try installing firestarter and opening up the nfs ports.

The second thing you can do which also makes life easier is to edit the /etc/hosts file. Edit the hosts file on each computer. This solved the issue for me using static ip addresses -- the router didn't seem to properly assign names. I also lets you call the computer by name rather than an ip address.

computer1 192.168.1.2
computer2 192.168.1.3
computer3 192.168.1.4
computer4 192.168.1.5

When finished editing the files restart nfs and portmap.

sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/portmap restart

It should work.

If not try pinging the other PC and make sure you are getting a response ping 192.168.1.2 etc...

Also: Are you sure you want to share the entire filesystem?


Thanks so much tagra123, you were right (and you're great)! I didn't know iptables was on although I hadn't installed it!
But which is the way to configure iptables for using nfs, without firestarter?? how can I open nfs ports on iptables?

Thanks in advance!

---

### Post by tagra123 on 2006-09-16
I prefer firestarter -- spoiled by the gui -- I guess.

Firestarter is an iptables editor. Even if firestarter isn't up and running the iptables are, that is you still have firewalled protection whether firestarter program is running or not.

There are some how to on the internet for iptables (google)

---

### Post by dannytherocker on 2006-09-16
> **tagra123 said:**
> I prefer firestarter -- spoiled by the gui -- I guess.

Firestarter is an iptables editor. Even if firestarter isn't up and running the iptables are, that is you still have firewalled protection whether firestarter program is running or not.

There are some how to on the internet for iptables (google)

Tagra123, sorry for boring you on, but I still have problems: I installed nfs-kernel-server (and nfs-common) on both Ubuntus to let them communicate each other and installed firestarter as well with the rule you suggested me above! but only Desktop (192.168.1.2) can access Notebook (192.168.1.3) not vice versa! the answer is always the same "access denied"! On the "status" tab of my Desktop's firestarter I can see the notebook trying to enter but after a few secs it gets stopped....
What's the matter with that???

Thanks and forgive me..

---

### Post by tagra123 on 2006-09-16
Change your exports line from

/ 192.168.1.2/192.168.1.5(rw,sync)

to

/ 192.168.1.0/255.255.255.0(rw) 

or

/ 192.168.1.1/24(rw) 


save and restart

The change to the exports allows any connection on the lan to work - you can also liast each machine if you prefer. Again make sure firestarter(is allowing the connections on both pcs/laptop)

sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/portmap restart

Make sure to restart service on each computer.

If you still have problems make sure the hosts file was edited and restart the computer.

---

### Post by dannytherocker on 2006-09-16
> **tagra123 said:**
> Change your exports line from

/ 192.168.1.2/192.168.1.5(rw,sync)

to

/ 192.168.1.0/255.255.255.0(rw) 

or

/ 192.168.1.1/24(rw) 


save and restart

The change to the exports allows any connection on the lan to work - you can also liast each machine if you prefer. Again make sure firestarter(is allowing the connections on both pcs/laptop)

sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/portmap restart

Make sure to restart service on each computer.

If you still have problems make sure the hosts file was edited and restart the computer.


WORKS, at last! I've changed /etc/exports as you suggested me! now it's ok!
Thanks for help and patience! :-)
Bye

---

