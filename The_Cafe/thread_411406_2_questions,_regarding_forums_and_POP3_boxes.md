---
title: "2 questions, regarding forums and POP3 boxes"
date: 2007-04-16
forum: The Cafe
---

### Post by Peter1234123 on 2007-04-16
OK, as it stands now, I have a fully working pubically viewable website, I am about to buy a domain name, I was wondering, how would I add POP3 mailboxes, (I think I need a DNS?) and make, and host forums on my server?

---

### Post by TheRingmaster on 2007-04-16
this is what you want for dns.

[Dynamic Network Services, Inc. -- DynDNS -- Welcome]("http://www.dyndns.com/")

---

### Post by Crashmaxx on 2007-04-16
Is this a home server you are talking about? Or a site hosted elsewhere? Or a full server hosted elsewhere?

Regardless, a forum is a piece of cake. Assuming you have a LAMP server or at least hosting with PHP, you can install phpBB very easily. It was basically a set of files you put on the server. Run the install script and you have full forums ready to go. vBullitein is no doubt a nice alternative, but you will have to pay for it. And if it is a small forum, probably overkill.

You don't need DNS specifically at all really. If this is a home server, then you likely have a dynamic ip and would need a service like dyndns.org to host the actual domain and have them redirect traffic to your server. They charge a small fee for actual domains and not one of their address, but it is very reasonable. If you have your server hosted, then the hosting company would take care of this for you.

Email is independent of DNS, but you need to have full access to your server and not just some web space. Assuming you have a full Ubuntu server or similar, you just need to install and setup a MTA and MDA. Postfix is very easy to setup and is a full scale MTA. If you just want a few accounts on it though, don't get too crazy configuring it. You actually don't need to change more then a couple settings to get it to work from default. Just saying, you can do a ton with it, but don't kill yourself with a mySQL back end and yada yada yada if you just need a couple accounts for yourself. Postfix and Dovecot or Courier is all you need to get email up and running. Configure them as you like and make you you have the right ports open and all and that is pretty much it.

So I hope that helps you. Nothing your asking is anything hard really.

---

### Post by Peter1234123 on 2007-04-17
The full site is hosted on a server at my house, as I have 30 MBPS downstream, and 10 MBPS upstream bandwidth (buisness plan) :O

---

