---
title: "sendign email via VPN"
date: 2010-11-13
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2010-11-13
Hi all,

need some advice on how to send emails via a VPN.
I have a server set up with a VPN (openVPN with DynDNS). My emails are located there and I can check them from home, office, where ever really, with different computers, no problem.
However, due to restrictions of some ISPs I would have to change the SMTP server used, depending on where I am with my laptop.

Now, I thought about using the VPN to also tunnel the SMTP traffic through that. But how am I doing that?
So far, when I'm connected to via VPN I simply have a local (from the server point of view) IP address to connect to my IMAP server. But how can I route the SMTP port 25 through the VPN?
Is that possible to do, also in a way that I don't have to change anything depending on where I am, as in within the network of the server or outside? Since when I'm within the network the VPN obviously isn't connecting...

I hope it makes sense what I'm trying to say...
Any help would be highly appreciated.

Cheers,
L&G

---

### Post by SeijiSensei on 2010-11-13
If the server at the other end of the VPN has an SMTP server enabled, why not just make that the default SMTP server in your email client?  I presume it has another IP address besides the one that terminates the VPN connection.  Just use that address as the SMTP server if DNS won't reliably tell you the correct IP for the server.

---

### Post by Linux&amp;Gsus on 2010-11-13
Thanks for the reply.
So, that server is doing everything for me, it has my emails, a little (extra) file storage, runs openVPN, the whole shebang. I simply can't afford (financially and space) to have another computer running permanently. Though, I do have a test machine which I can afford to, and sometimes do, screw up. But that's not the point. :)

So, that one machine has to do everything for me, it's also too old to even think about a virtual machine. But I don't think that should be a problem.
I don't have sendmail, or any SMTP server for that matter, installed on it. That is, so that I don't accidentally have a spam machine running here. Hence I was asking if it's possible to route SMTP from my laptop through the VPN.

If that is not possible or difficult I might need to look into sendmail. But I first want to be sure that there isn't another way.


Cheers,
L&G

---

### Post by SeijiSensei on 2010-11-13
I'm glad you're concerned about the potential for being exploited as an open relay, but that doesn't sound like a problem here.  If the box is behind a firewall, then it's pretty invulnerable unless you forward port 25 from the router.  Rather than doing that, I'd just use the VPN and bind the SMTP listener to the VPN address.

I have a VPN connected from this machine behind my firewall router to the (Linux) router to permit certain inbound services directly from the Internet.  Taking a similar approach means you wouldn't really need to maintain separate configurations for inside/outside.  Just use the VPN all the time.  It really adds only a trivial amount of overhead to the connection.

---

### Post by Linux&amp;Gsus on 2010-11-13
Well, yes, the server is sitting behind a modem, nothing opened in the firewall. So, from that point of view it should be OK.

However, sometimes I can be such a noob... :redface: I don't really know what you mean by binding the SMTP listener to the VPN. How am I doing that?

---

### Post by SeijiSensei on 2010-11-14
> **Linux&Gsus said:**
> However, sometimes I can be such a noob... :redface: I don't really know what you mean by binding the SMTP listener to the VPN. How am I doing that?

Sorry.  What I meant was, you can insure that the SMTP server only listens on particular interfaces ("binding") or limit the IP address blocks that can talk to it.  

If you use Postfix ("sudo apt-get install postfix"), the preferred SMTP server in Ubuntu, you'll find a configuration file called /etc/postfix/main.cf.  In it there's the line:

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

Postfix listens by default on all the network interfaces, including a VPN interface if it exists.  But you can still control which network addresses can connect to it using the mynetworks directive.  The default Ubuntu configuration only accepts connections from addresses between 127.0.0.1 and 127.255.255.255, the so-called "localhost" interface, but not from any other network addresses.  So if your VPN tunnel uses 192.168.1.1 and 192.168.1.2 for its addresses, you'd add "192.168.1.0/24" to the list in mynetworks.  (That stuff in brackets is the "IPv6" address of the localhost interface and can be safely ignored.)

Did that help?

(The sendmail program uses a different approach and binds only to specified IP addresses on the server.  So I can tell it to listen only on the VPN interface but not the ethernet interface, for instance.  These two strategies accomplish essentially the same purpose, but go about it in different ways.)

---

### Post by Linux&amp;Gsus on 2010-11-14
Just to clarify. Having Postfix installed on the server and then adjusted so that it listens to the traffic from my remote computer, right? Or is that on my laptop to push it through the VPN. (Just wanna be sure I do the right thing...)
Other then that, I think that should be enough to get me going.

Thanks again for your help. It is much appreciated.


Cheers,
L&G

---

### Post by koenn on 2010-11-14
yes, postfix on the server, configured to (only) listen to traffic coming through the vpn

---

