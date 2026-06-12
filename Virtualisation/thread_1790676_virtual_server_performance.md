---
title: "virtual server performance"
date: 2011-06-25
forum: Virtualisation
---

### Post by bigmonmulgrew on 2011-06-25
I have setup a virtual server
Both the host and the guest are ubuntu server 11.04 
the guest is a LAMP

When connecting to the host via ssh there seems to be a delay between typing in the logon name and the server requesting the password.
Also while using fireftp to connect to the server there is also a delay after clicking connect.

 Both delays are around 10 seconds but do vary a little
Connecting to the host machine is virtually instant

Any idea what may be causing this delay, should I be concerned, and how to rectify it?

---

### Post by HermanAB on 2011-06-26
Likely a DNS problem - it takes about 10s to time out.  Look at the network with tcpdump to see what is going on.

---

### Post by bigmonmulgrew on 2011-06-28
I've never used tcpdump.
I typed "tcpdump" into the command line and got command not found.
Am I typing it wrong? Do I just need to install it? Will there be somethign else installed already I can use?

---

### Post by SeijiSensei on 2011-06-28
Don't bother with tcpdump.  Just add the hostnames and IP addresses of the two machines to /etc/hosts on both host and guest.  I bet that will help.

Alternatively, you can edit /etc/ssh/sshd_config on the server and set "UseDNS" to "No".

---

