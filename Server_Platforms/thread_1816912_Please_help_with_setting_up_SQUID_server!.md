---
title: "Please help with setting up SQUID server!"
date: 2011-08-02
forum: Server Platforms
---

### Post by hoanggeneral on 2011-08-02
Hi all;

I am trying to set up a SQUID server on my Red Hat Linux 7.3. to act as a cache server.
The machine has 2 network interface: 
eth0 172.30.254.4/23
eth1 172.3.254.65/23
Default gateway is 172.30.254.19/23
The hostname is "amelie".
The squid version that I am having is 2.4.
These are what I added in /etc/squid/squid.conf

> visible_hostname amelie

http_port 80

acl allow_network src 172.30.254.4/23

http_access allow localhost
http_access deny all
Then I restart the squid server by issuing the command "service squid restart". However, I received the mesg: "aclParseIpData: WARNING: Netmask masks away part of the specified IP in '172.30.254.4/23'.
I tried to change the "acl allow_network src 172.30.254.4/23" to
"acl allow_network src 172.30.254.4/22"
"acl allow_network src 172.30.254.4/24"
"acl allow_network src 172.30.254.65/23"
"acl allow_network src 172.30.254.65/22"
"acl allow_network src 172.30.254.65/24"
but none works!
When I set clients to use the proxy, the clients can ping any site on the internet but they cannot browse any page!
Is there any thing that I missed or did wrong?
I have very little knowledge of SQUID.
Please help me out!

Thank you.

---

### Post by rudelgurke on 2011-08-03
Well - if I see it right you try to apply a Class C netmask on a class B network which will fail.
Try to change the netmask for your interfaces:

172.30.254.0/16
172.30.2.0/16

As example. And if you're really using RedHat Linux 7.3 consider an upgrade because that one belongs to a museum.

---

### Post by ephmanjmm on 2011-08-04
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1555629](http://ubuntuforums.org/showthread.php?t=1555629)

---

