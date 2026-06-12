---
title: "postfix, postfixadmin, and a brick wall"
date: 2008-06-25
forum: Server Platforms
---

### Post by brokenshadows on 2008-06-25
please bear with me as I've been using linux for a grand total of four days now...when it comes to setup (and really anything else) I know about as much as my pet fish knows about making sushi

In a nutshell, I am trying to setup a server (8.04) that will allow me to host Trellis (a web based ticket tracking system) and Moodle (web based educational CMS).  

I am working in a primarily windows environment (all of our servers here aside from the call managers are MS Server 2003)

We are currently using MS Exchange 2000 but will soon be upgrading to 2007 (not sure if that's relevant, but I figured the more info the better)

I want my Ubuntu server to only be accessible from our internal network.

I want my Ubuntu server to be able to send e-mail to internal addresses.

What I've got working so far is the core LAMP server (Hardy, apache2, mysql, php), myphpadmin, ISPConfig, and Trellis.  All of it is accessible to the internal network only.

What doesn't work so far is Bind9 (I keep getting a permission error that I can't seem to get rid of), postfix, and postfixadmin.

I've gone through various postfix tutorials, but the problem I'm running into is that all of them seem to be written assuming there is no previously existing mail server.  I don't even know if I need postfix...but I do know that I need Trellis (and soon Moodle) to be able to send e-mails to internal addresses. There will be NO need for the server to be sending e-mail outside of the network as the only thing it will be used for is the internal ticketing system and the "on-line class" system.

I know...I got all the easy stuff up (apache, mysql, etc) and got lost at the intermediate stuff...

I blame MS and the Winblows environment which I've been supporting for the past 12 years and using for longer than that...they've made me technically inept... ](*,)

---

### Post by hortimech on 2008-06-27
A bit more info would be nice:)
what do the clients run?
If windows, do they use outlook?
this sort of thing

You will also need an MDA (mail delivery agent) such as courier, postfix will pass mail to this and this will deliver to clients mailbox

for a DNS howto go here [http://www.faqs.org/docs/Linux-HOWTO/DNS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/DNS-HOWTO.html)

follow this and you should get bind9 running

---

### Post by windependence on 2008-06-27
He doesn't need an MDA here. Postfix can do smtp just fine. I have it configured on my forum to send outgoing mail. Just do a search for postfix smtp on google and there are some tutorials out there. Most CMS does this through the php mail function.

-Tim

---

### Post by hortimech on 2008-06-28
I am no expert, but he does not want to send out any mail, it all wants to go internally. Yes Postfix will send out mail but will it put into internal mailboxes?
As for the clients, do they already have email set up? if so how are they sending mail, exchange was mentioned and I think Outlook can only send mail by one server (unless somebody knows differently). He may be better setting up some form of webmail for the internal mail, with this, all the set up is on his server and clients connect from a browser.

---

