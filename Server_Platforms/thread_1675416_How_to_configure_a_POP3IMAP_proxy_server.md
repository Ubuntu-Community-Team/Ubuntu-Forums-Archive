---
title: "How to configure a POP3/IMAP proxy server???"
date: 2011-01-25
forum: Server Platforms
---

### Post by abhinavkumar940 on 2011-01-25
Dear All,

This is my first post to the forum :)

I've recently migrated my office PCs to ubuntu. My server doesn't server any big purpose but to provide Internet Connection to the rest of the nodes. Things were quite easier during the windows era using ICS.

Even in Ubuntu we were able to do it using the "shared network" option, simple & straight forward. But things got complicated only after installing "squid". Needless to say it brought in a lot of add ons as far as the http proxy serving is concerned & we are enjoying a better internet(http only) connectivity without any doubt. But we are not able to use our email clients, MS Outlook or Thunderbird

But to best of my knowledge squid strictly is a http proxy hence doesn't support handling requests on ports other than 80. (465 & 995 in my case)

Now I have two queries, 1. Can "Squid" really be used to do what I want here??? using iptables, port forwarding or any other mean
& 2. Can any one suggest a good pop3/imap proxy as good as squid is.

Looking forward to a quick response . . . . 

Thanks,
Abhinav Kumar

---

### Post by abhinavkumar940 on 2011-01-26
More than 10 hours & still no single reply . . . . 

C'mon people I really need to set this up.

---

### Post by SeijiSensei on 2011-01-26
You haven't given us enough information to help, I'm afraid.

First, where is the POP/IMAP server?  Why do you need a proxy?  Can't you just connect directly to the server's ports over the network?

If you need to push traffic through an intermediate host to a remote server, I'd suggest the hoary *tcpproxy* application.  It will proxy any TCP connection.  You'll find the source code in the list [here](http://www.sourcefiles.org/System/Daemons/Proxy/).

---

### Post by abhinavkumar940 on 2011-01-27
Hey! [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"),

First of all thanks man for the reply!

Here goes my topology.

srv.mydomain.com has two NIC one is connected to the ISP & other one is going to the router(The DHCP of the router is turned off) rest of the machines of my network is also joining me on the router.

My srv.mydomain.com is running squid (not in transparent mode) & DHCP server. Machines are getting the lease & after specifying the proxy in their browsers they are able to access internet flawlessly.

But none of the machines (WinXP or ubuntu) is able to connect to our corporate mail server (located outside our network).

I tried :
Specifying & authorising the ports in squid conf file,
Resetting iptables & allow all traffic,
Installing p3scan
Installing perdition

I was not able to configure or run the last two though.

 but nothing seems to be working. They are still not able to access mail on their machines 

I have SSL on my server & we use ports 995 & 465 for POP3 & SMTP respectively.

Please let me know if you need any more information on this topic.

---

