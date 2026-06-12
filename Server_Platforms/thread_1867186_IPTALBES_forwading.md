---
title: "IPTALBES forwading"
date: 2011-10-22
forum: Server Platforms
---

### Post by mucho_maze on 2011-10-22
Hi

I have a setup with two servers. One in production and one as backup.A router is connecting the servers to the internet, and is redirecting all relevant ports to the production server. I would like to test services such as apache and dovecot mail on the backup server, without having to switch to this server in the router.

My first thought is IPTABLES. Does anyone know how to make IPTABLE redirect traffic coming from a specific ip address (my own address) to another ip on the local lan? Then I could let the production server forward requests from myself to the backup server.

Thanks for any input...

---

### Post by SeijiSensei on 2011-10-22
Don't the production and backup servers have different fully-qualified domain names?  To use the dovecot server on the backup, just point an IMAP client at "backup.example.com".  If they have the same name but different IP addresses, configure the client software to use the backup's address.

This seems so obvious, I must be missing something of importance here.  What is it?

If you want to redirect traffic from a specific source IP arriving on your production server, you can use iptables on a port-by-port basis.  To redirect HTTP requests from your.own.ip.address sent to production.example.com off to backup.example.com port 8080, you can add a rule like this to production.example.com:

```
iptables -t nat -A PREROUTING -p tcp -m tcp -s your.own.ip.address ---dport 80 -j DNAT --to-destination backup.example.com:8080
```

This matches traffic sent from your.own.ip.address to production.example.com:80.  It forwards that traffic to backup.example.com:8080.  Of course, it could forward it to backup:80 as well.

Make sure that there are entries in /etc/hosts for backup.example.com and production.example.com.  Firewalling rules are usually added to the kernel before the network is started, so DNS name resolution won't be available.  The other option is hard-coding the IP addresses in the iptables commands.

---

### Post by mucho_maze on 2011-10-23
Hi SeijiSensei,

Thank you very much for your reply. My servers do not have different qualified names. The backup server serves only purpose two purposes: 
  1. Take regular backups of data from the production server.
  2. Stand-in, i.e. take over if the production server breaks down

I think you have understood my situation correctly. I want to forward all traffic from the outside, through the production server, and to the backup server.

At my home a have a similar setup. As you suggested, I tried running the following from server 1:

```

iptables -t nat -A PREROUTING -p tcp -m tcp -s 192.168.1.104 --dport 80 -j DNAT --to-destination 192.168.1.21:80

```

192.168.1.104 is my laptop and 192.168.1.21 is server 2. I would then expect to see the index.html of server 2 when I enter index.html on server 1. However, nothing happens when I reload the index.html from server 2 after executing the command. After some time I get a time-out.

What am I missing?

---

### Post by koenn on 2011-10-23
do you have a rule tha says such traffic is actually allowed ?
does the server have ipforwarding on? 

and why do you need to redirect it at all ? why don't you go to  backup.example.com:8080 directly ? why wouldn't that work ?

---

### Post by SeijiSensei on 2011-10-24
I don't understand that either. Redirecting traffic seems needlessly complex.

---

### Post by Doug S on 2011-10-24
As with SenjiSensei and koenn, I do not understand the need for the forwarding either, so maybe there is something I do not understand.
 
For the questions about forwarding: I think there also needs to be a return path iptables rule. There was a [similar thread]("http://ubuntuforums.org/showthread.php?t=1855192") about a week or two ago.

---

### Post by mucho_maze on 2011-10-24
Thanks for all your suggestions.

I believe that you may all be right to a large extent. When forwarding with iptables there needs to be some return router. It should be far more simple to just use some different ports, but unfortunately that will lower the quality of my test in at least one case (apache).

As you suggested, I could try to simply prefix the ports forwarding like this:

80   => server1:80
880  => server2:80
995  => server1:995
8995 => server2:995

etc. and hope that I can find non-standard ports that are not blocked by either of the two ISPs :) Perhaps I'll just test a few services a time and re-use some ports. That okay for everything but apache, I think.

When testing web-pages build on a content management system, for instance, many paths to images and stuff are hard coded in the page sent to the client. In presta shop for instance, I don't know how to translate 'http:mydomain.com/img/purchase-icon.png' to 'http:mydomain.com:8080/img/purchase-icon.png'.

I believe it would be very nice to be able to set up full forwarding with iptables.

Thank you all for your input. Really appreciate it!

---

