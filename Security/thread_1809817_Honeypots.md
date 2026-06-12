---
title: "Honeypots"
date: 2011-07-22
forum: Security
---

### Post by CNM on 2011-07-22
Hi ,

I would like to implement a honeypot on ubuntu ...
I don't have much experience in the honeypot field ... i know the idea behind it ...
I need the best (tested) open soure honeypot project available ...

Thanks

---

### Post by Chayak on 2011-07-22
Take the time and read
Virtual Honeypots: From Botnet Tracking to Intrusion Detection
ISBN-10: 0321336321

[http://www.honeynet.org/]("http://www.honeynet.org/") is also a good resource.

It's a complex topic there is no 'best' honeypot.  It depends heavily on the information you want to gather.  There are high and low interaction honeypots that vary in complexity greatly.  It can be as simple as a script that pretends to be an ssh login and then a bash shell to a remote attacker, or as complex as a virtualized enterprise network with web servers, databases, firewalls, routers, etc.

---

### Post by archolman on 2011-07-22
Project Honeypot has all sorts of resources you might be able to use without having to write anything yourself:
[https://www.projecthoneypot.org/](https://www.projecthoneypot.org/) 
  This is from their site, (reg. users view):
> 

In order to put honey pot addresses on your website you need to  register your site here. Specify the scripting language you prefer (e.g.  PHP, ASP, Perl, mod_perl, ColdFusion, Python, or Movable Type; other  language support coming soon). You may also choose the name of the  Project Honey Pot script, or allow us to generate its name randomly.         Based on your choices, we will create a customized script in your  preferred language. Through that script you can display honey pot  addresses on your site and track the spambots that harvest them. If  you'd like to see an example of the output of the script, you can find  one [here]("http://www.projecthoneypot.org/honey_pot_example.php") (the example page will open in a new window).
         If you have donated one or more MX entries, you can choose to  display honey pot addresses created using only those private domains. If  your private domain is unavailable the script will revert to select  from publicly available domains.
         After you submit your registration we will provide instructions on  how to install the Project Honey Pot page script. Please note: by  clicking the SUBMIT button you indicate that you have read and agree to  the [Service Terms]("http://www.projecthoneypot.org/terms_of_service_use.php").
         * Some people who want to participate in Project Honey Pot  don't have their own servers. To allow these folks to help out, we have  created a QuickLinks program where they can drive harvester traffic to  existing Honey Pots. Sharing your Honey Pot will increase the number of  harvesters that it catches, allow more people to participate in the  Project, and, we think, generally increase your karmic goodness.

Register & have a good look round the site, you may find exactly what you need.

---

