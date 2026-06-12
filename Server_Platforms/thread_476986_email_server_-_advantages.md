---
title: "email server - advantages?"
date: 2007-06-17
forum: Server Platforms
---

### Post by nix4me on 2007-06-17
Hi,

Are there any advantages to running my own email server?  I have 2 accounts and my wife has 1 on our isp email server.  I run a linux server that does web, file, backup, ftp serving.  I was wondering if there are any real advantages to running a linux email server?

nix4me

---

### Post by avik on 2007-06-17
Like any type of server, running your own e-mail server will put everything under your control.  So if you want that kind of control, then that's the biggest reason to run an e-mail server.

You seem to have a great deal of experience, so maybe for you, the tradeoff (installation/management vs. control) will be ideal.

---

### Post by nix4me on 2007-06-17
Yes, I have a great deal of experience.  I have 2 linux machines and a freebsd machine.  i don't mind the admin part.

i will do some searching to find advantages.  Hopefully someone with operational experience will also chime in.

nix4me

---

### Post by chris.zeman on 2007-06-18
I guess it all depends on the situation. The main advantage, like avik said, is putting everything in YOUR control. I operate a server at home and at work, both having e-mail servers. I haven't started using the one at home yet, but I use the one at work regularly.

I've had to change web hosts a few times, and the biggest pain when changing was transferring email from the old host to the new host. There are quite a few accounts I'm responsible for, and it takes me hours when I have to do that. I haven't had to change hosts for a few years, as I've found one that finally provides decent service.

You got me thinking, though. I'm seriously considering setting up my home server to act as the mail server for all my domains. It never occurred to me before, but it really is a good idea. I'd never have to worry about email accounts if I had to transfer hosting companies.

It sounds like you're doing all your own hosting, so it only seems to make sense that you operate your own mail server as well. I guess your question should actually be,"Why not?". :D

Chris

---

### Post by Mr. C. on 2007-06-18
Pros: 
[LIST]
[*]Complete control
[*]Faster response
[*]Superior anti-spam/anti-virus
[*]Logging
[/LIST]
Cons:
[LIST]
[*]Non-trivial
[*]Static IP required
[*]Many servers will reject from dynamic or residential IP ranges
[/LIST]

---

### Post by technoteen on 2007-06-18
i would like to chip-in that have a look at zimbra, [http://www.zimbra.com](http://www.zimbra.com)
use the open source version
i am using it for hosting mail in my college and its excellent, very easy to install and maintain

---

### Post by MJN on 2007-06-18
> **Mr. C. said:**
> 
[LIST]
[*]Non-trivial
[*]**Static IP required**
[*]**Many servers will reject from dynamic or residential IP ranges**[/LIST]
 
As you know these latter two should really be caveated insofar that they're not show-stoppers. A dynamic IP is quite workable by using dynamic DNS and, whilst this may then lead onto the last point, it is usually if not always possible to relay outgoing mail via your ISP's mail server. This of course negates some of the advantages but it still leaves many others behind.
 
Mathew

---

### Post by Mr. C. on 2007-06-18
It is more serious than that - many *servers* will reject email being relayed from dynamic or residential IPs.  There is nothing an admin can do to work around this, short of getting an IP address not blacklisted.

---

### Post by VorDesigns on 2007-06-18
I've run my own mail servers for years; the advantages are many and with the advantages go the responsibilities.
In reverse:
1. You must have a fully qualified domain.  I do my own but godaddy comes highly recommended from an associate I trust.  Set up your MX record with the name of your mail server.
2.  Spend the extra few coin and get service from an ISP that will rent you  static IP addresses, I recommend two, one for the router and one for the mail server, I'll expand on this later.  Then pay the userous accounting fee to have your mail server IP reverse DNS resolve to yourmailserver.yourdomain.com.
3.  Don't forget to set up a mailbox for postmaster and have an alias for abuse that relays mail to the postmaster.  Route all your daemon messages to the postmaster account.
4.  The reason that I suggest a separate IP for your mail server and another for your router is that no matter how hard you try, you will one day spam the world however unwillingly from one of your client workstations.  Having this traffic not come from your mail server's IP will be most important to you because some of the BHLs are not maintained that well and if you ever get blackballed by Verizon, forget about ever sending them mail again.  If you don't want to afford two IP, create rules that only allow smtp from your mail server on the LAN.  This will reduced the chance of some zombies ruining your mail server reputation.
Remember, once you take on this kind of responsibility, you are responsible for archiving and maintaining accessibility to your records from a legal stand point.  
Keep a tinkerbox handy with your current configuration and at least the core mail boxes and alias' installed so that you can fail over to it quickly.  I know that most MTAs will keep trying for a couple of days but hardware is cheap enough that having a back up is to easy to do.
Once that has been done; now for the bigger advantages.
a) you wife who loves to sign up for every piece of crap on the Internet she can find can now have an alias for every piece of crap she subscribes to.  When the piece of crap turns into spam from hell, delete the alias.  Teaching the wife to ask for a new alias is your problem.
b) Mail accounts that you maintain in the wild can be forwarded to your private server.
c) Create alias address for things like your cell phone mail
d) Automate process to send you notifications
e) Create ListServer and host your favorite club
f) Run server based A/V to stiffen you protection
g) Run server based spam filtering.
h) provide mail for other members of your family.

---

### Post by MJN on 2007-06-18
> **VorDesigns said:**
> a) you wife who loves to sign up for every piece of crap on the Internet she can find can now have an alias for every piece of crap she subscribes to.  When the piece of crap turns into spam from hell, delete the alias.  Teaching the wife to ask for a new alias is your problem.

:lol: That is so so true!!

---

### Post by nix4me on 2007-06-18
Im starting to think that its too much for my simple 3 email accounts.  I am however interested in something like fetchmail.  To gather email from my isp accounts and forward mail back to it.

nix4me

---

### Post by MJN on 2007-06-19
Depending on your ultimate intent such a small number may be advantageous as it will give you plenty of opportunity to learn a lot about running a mail server whilst not having too many people relying on you!
 
Mathew

---

### Post by nix4me on 2007-06-19
Good point!

nix4me

---

### Post by andrew.46 on 2007-07-05
Hi,

> **nix4me said:**
> Hi,

Are there any advantages to running my own email server?  I have 2 accounts and my wife has 1 on our isp email server.  I run a linux server that does web, file, backup, ftp serving.  I was wondering if there are any real advantages to running a linux email server?

nix4me

What about IMAP? Simple with very little configuration.

             Andrew

---

### Post by MJN on 2007-07-05
Many ISP mail services do provide IMAP.

---

