---
title: "Samba Domain Controller + App Server for Windows clients"
date: 2009-01-17
forum: Server Platforms
---

### Post by uzi09 on 2009-01-17
Hey all.

I've been planning on doing a linux server for a SOHO with windows and linux clients.

The Objectives
===============
# Primary domain controller (i guess that means it authenticates the users and lets them join the domain)
# Mail server
# File server
# Need remote access at all times (Will SSH be enough??)
# App server (keep reading)

Primary Domain Controller (PDC)
================================
I realize there have been a number of articles, and an even greater number of questions, on setting up linux as a domain controller. Most answers point to configuring Samba accordingly. That's fine, I'll hopefully get that sorted out.

Mail Server
=============
I've yet to find a nice simple how-to to set one up. If you can recommend some, I'd greatly appreciate it.

# File Server
===============
Samba == shouldn't be a problem

# Remote Access
===================
Will SSH be enough? Apparently you can create a tunnel using SSH and Puttty & then are able to map network drives. Not exactly sure how it all comes together. If you can clear it up, that would be very helpful!

# App server
==============
Problem is the SOHO needs to use two critical applications: GoldMine & Quickbooks. I know there are alternatives, however the boss wants those two.
(I got him thinking about SugarCRM, but I've gotta set one up for him and show him that it'll work seamlessly. Only problem is I'm quite new to it myself. As far as Quickbooks is concerned, there doesn't seem to be a good enough alternative)


GoldMine - I can have the database running on the file server and point on the links to the server, so it should work that way.

Quickbooks - Apparently you can't do the same.

The Plan
=========
I was considering having a dedicated XP client for these two applications that the server will allow clients access to.

Is this possible to setup? Any ideas how else I can go about using a linux server for everything else, but have these two programs run as well (centrally)?

I was hoping to use Ubuntu 8.04 Hardy for the Server and doing it myself, however there are possibilities of using Red Hat w/ commercial support since this will be for a business and we need to ensure things are working properly all the time.

If you have any other ideas for possible solutions, it'll be much appreciated!


Thank you in advance.

---

### Post by kidders on 2009-01-18
Hi there,

> **uzi09 said:**
> Primary Domain Controller (PDC)
Samba *can* be made to work just fine as a domain controller, but there are plenty of little gotchas, so be prepared to spend some time ironing out the kinks. It's been a while since I've used this particular Samba configuration, but (for what it's worth) I do remember having to tinker with roaming profiles for a while to get it right.

> **uzi09 said:**
> Mail Server
Setting up a mail server is basically very straightforward. What complicates it is that every howto has its own take on what combination of services to run alongside it. You'll probably need ...
[LIST]
[*]An SMTP server capable of LDAP authentication. (I would suggest either Postfix or Exim.)
[*]An IMAP server capable of LDAP authentication. (I would suggest Courier or Dovecot.)
[*]You may or may not want spam protection, but you will certainly want clamav integration to protect your Windows machines.
[/LIST]
One of the decisions you'll need to make is whether to run synchronous or asynchronous spam/virus checks. The choice is between Receive mail -> Run various checks -> Deliver message (the simple model), and handing received mail off to a second mail server for processing & delivery.

The asynchronous model is worth considering where the volume of mail delivered is sufficient to warrant it, and is also a good idea in commercial Windows environments (in my opinion), so that resource-hungry operations like scanning large attachments for viruses can't interfere with mail reception & cause messages to bounce.

Anyhow, once you decide on details like these, you'll (hopefully!) find that the number of howtos left that meet your needs is pretty small.

> **uzi09 said:**
> Remote Access
SSH is perfect for administrative access to a system, because it gives you secure access to absolutely everything. If you're thinking of using it to give non-admin users remote access, it's not a suitable choice ... simply because you need to know too much about how a network actually works to make any use of things like tunnels. In this case, I would recommend that you consider a VPN.

For example, to do what you suggested (tunnel Windows file sharing over SSH), you need to ...
[LIST]
[*]Know the ports it uses and what for.
[*]Realise that a connection to a file sharing service on the machine handling the tunnel will always appear to come from "localhost", in case you run into any unforeseen security issues.
[*]If the tunnel terminates on a Windows box, you'll need to remember that your own local file sharing service will prevent it binding to 127.0.0.1, and set up a virtual network adapter.
[/LIST]

> **uzi09 said:**
> App server
Personally, I wouldn't recommend even *trying* to run shared Windows apps on a Linux box in a business environment. Running them on a Windows machine, as you suggest, seems the best solution.

Regarding what distro/support package to choose, the safe approach is to go with something you're satisfied has a long track record in business, because you can at least have *some* level of confidence that you'll never come up against a problem that hasn't been seen a thousand times before, and that there's a well-documented way to do anything you might need. If you're willing to support the network yourself though, I would say go with what you know.

I hope that helps.

---

### Post by Thirtysixway on 2009-01-18
For network drives, you can use samba.  I'm not sure how you're configuring it but I used to map the M:\ drive on my windows machine to my samba folder on my Ubuntu server

```
net use M: \\192.168.1.10\myfolder /USER:usernamehere passwordhere
```

One thing you may be able to do is setup a virtual machine running xp or 2000 and run your windows applications on that.

---

### Post by brown.hornet on 2009-01-18
First of all I am most likely going to get flamed on this but here goes – and no I am not a MS crony; systems should be deployed based on business needs not OS ideology.

As such - based on your ‘overall’ requirements I would suggest that you work with Windows 2003 SBS Premium Edition.  Though Ubuntu server is free there are all sorts of gotchas when trying to get it configured as a Domain Controller (as discussed in kidders post) as well as when trying to get it to play well with Windows systems.

Discussion follows:

# Primary Domain Controller

	Windows 2003 SBS is a Domain Controller out of the box with little to no effort allowing you to get up and running quickly and easily.  There seems to be more discussion on how to get Ubuntu system into a Windows Domain

     ([http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html](http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html)) 

 than there is in getting a Windows system into an Ubuntu Domain. 

# Mail Server
 	
	SBS 2003 comes with Exchange Server again this can easy configured using built in Wizards and GoldMine integrates easily with Exchange.
 
# File Server

	Using SBS 2003 will eliminate the need to use SAMBA other than on the Ubuntu workstations.  Also this would allow you the ability to use this sever to ‘host’ your QB as well as GoldMine db’s (I have a friend that us using QB in network mode – also SBS 2003 Premium includes SQL 2005).  Additionally should you have any other Linux bases system you can use Crossover ([www.codeweavers.com](www.codeweavers.com)) to run QB and possibly GoldMine though I have not tried running either personally, I use Crossover on my Mac to run Office 2003 (primarily Outlook).

# Need Remote Access

	With SBS you can enable ‘Remote DeskTop’ which will allow up to two users to access this server remotely for management purposes.  Should you wish to run/work with applications I would suggest deploying a second server with MS Terminal Services enabled.

Again I am not opposed in using Ubuntu Server, however, if this is your first time deploying an Ubuntu Server, you want/prefer access to commercial support, and you need integration with Windows workstations moving to a Linux environment may not be the best solution for your business now.

Respectfully –

---

### Post by uzi09 on 2009-01-21
Thanks very much for the great responses. So I'm going to put things off on hold for the business atm.

Something interesting I came across the other day dealt with a VM running Windows as a service and through a special utility the user is able to run specific applications.
(Here's the full story & how-to: [http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1238129,00.html))

I was wondering, if this were to be done on a Linux server in a Linux only environment. Would it be possible for this to work from a client's computer? Any idea on how to go about implementing such a thing?

ATM I'm working on trying to actually get that up and running as the how-to shows. Hopefully this procedure can resolve some issues we've had getting this up and running.

Look forward to hearing from you all.

---

