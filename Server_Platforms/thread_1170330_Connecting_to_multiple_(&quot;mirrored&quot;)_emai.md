---
title: "Connecting to multiple (&quot;mirrored&quot;) email servers depending on current IP/location"
date: 2009-05-26
forum: Server Platforms
---

### Post by Discus on 2009-05-26
Hello, 

I'm trying to work out a way of making multiple email servers transparent to end-users; I've done some google-ing and searched around these forums, but couldn't find anything similar (perhaps I wasn't asking the right questions). 

**Background: **
Our organisation sits on the wrong side of a massively oversubscribed ADSL link (we piggy-back on a larger organisation's link) - not much we can do about that given the price of bandwidth in South Africa. However, we do have access to another machine in the USA (hosted with Dreamhost). 

Initially, I set up a local Ubuntu 8.04 machine to fetchmail from the host in the USA, and to act as a mail relay to the server in the USA, so that end users had seemingly quick email access. This is great in-office, but when travelling, this server is almost inaccessible to end users (because of the crappy network link) and perhaps email client's unhappiness with IMAP over slow/unstable links. Hence my current problem. 

External email is always delivered to the USA server for users (the local machine does not have port 25 accessible and does not appear in the MX records) (and then fetchmail grabs it and puts it on the Ubuntu machine), but internal email (sent by and to in-office users) is delivered locally on the Ubuntu machine. Outgoing email is relayed to the USA server for delivery to non-internal emails. 

**The Problem/solution wanted: **
Essentially, what I would like to have happen is that the end user mail client connects to a single address, which then directs them to either the in-office email server (running Ubuntu), or the Dreamhost server if they are outside the home network. 

I would like to do this for both IMAP and SMTP [although the Thunderbird add-on SmtpSelect helps end-users to switch between servers, they have to remember to do so, and it doesn't help those people that choose not to use Thunderbird]. I have set up some clients to list both servers and then tell the user to check the relevant one, but that seems a little clunky! 

**Network details**
I have recently started testing offlineimap, and that looks like a great way of mirroring the two servers with each other (we only have about 8 user accounts to do this with, and only 5 users regularly travel). 

The local Ubuntu machine uses Postfix, Dovecot, fetchmail and offlineimap. 

The "home network" is a routable Class C (/24) network, although not all IPs are reachable from outside (obviously), although the server of course is. 

End users use Thunderbird, Outlook (2003/2007) and Outlook Express as clients on Windows XP. 

I imagine some sort of DNS "hack" might be a solution, but I don't know enough about it to even see how this would be done; I do have control over the DNS records for the domain (at least, as much control as dreamhost gives you!). I imagine that large organisations with distributed mailservers must run into a similar sort of problem when people move between offices [unless of course they're running just one email server!]?

Is there a way of getting this to work? 

Many thanks!

---

### Post by grantemsley on 2009-05-26
I don't know much about the mirroring aspect, but I can definately help you out with the DNS.

What you need is usually called split DNS.

The way it works, is to run your own DNS server locally (running bind on the mail server or another server in the building).  You setup DHCP to point clients to that DNS server.

On the local DNS, you set it up as authoritative for your domain, and put in appropriate records for your mail server, eg.

```

mail.example.com A 192.168.0.1

```

In your external DNS that the rest of the world sees, you have mail.example.com point to the IP of your remote server.

When connected to the local LAN, clients see mail.example.com as being on 192.168.0.1.  The outside world sees it as your remote server's IP.

If you google split DNS I'm sure you'll find a good guide for setting it up.

As an added bonus, bind will cache DNS requests, which will result in faster DNS lookups over your slow link.

---

### Post by Discus on 2009-10-01
Many thanks Grant, I'll speak to the person that administers the DNS at work and get that sorted out. :D

---

### Post by satishbhawra42 on 2009-10-01
Essentially, what I would like to have happen is that the end user mail client connects to a single address, which then directs them to either the in-office email server (running Ubuntu), or the Dreamhost server if they are outside the home network.

---

