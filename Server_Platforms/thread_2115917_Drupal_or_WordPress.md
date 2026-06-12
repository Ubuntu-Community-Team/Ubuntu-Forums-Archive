---
title: "Drupal or WordPress"
date: 2013-02-14
forum: Server Platforms
---

### Post by satimis on 2013-02-14
Hi all,

Recently I start running WordPress org building websites instead of using html editor. It is quite convenient. Drupal is another tool similar to WordPress. To build finance websites which of them shall I use? TIA

B.R.
satimis

---

### Post by kr651129 on 2013-02-14
I've not had much experience with wordpress but I LOVE drupal.  It's the only CMS I use if I don't have to build from sctrach.

---

### Post by tgalati4 on 2013-02-14
Check out the plug-in's for both.  Drupal has an extensive plug-in library to add functionality.  So if your websites need ecommerce or time-tracking or special statistics reporting--there's a Drupal plug-in for it.

There's also an extensive developer community for Drupal, so you can modify existing plug-ins or write your own.  If the website content is static--no changing then Wordpress is simpler.  If the content is dynamic--changing daily or weekly, with special actions required, then Drupal.

---

### Post by satimis on 2013-02-14
Hi all,

Thanks for your advice.

I started using WordPress for about 2~3 weeks. It is easy to learn. But I found not many themes relating to "Finance". For such a reson I started searching on Internet discovering Drupal. To my finding Drupal is NOT easy to learn. This is not a problem to me. But I expect to know whether Drupal is more suitable for developing "Finance" website. Once finalizing my decision I would use the software for long run.

How about Joomla?  Thanks

satimis

---

### Post by tgalati4 on 2013-02-14
All of these frameworks have a learning curve.  Some are easier than others.  You can install them easily as a "stack" to test them out using:

[http://bitnami.org](http://bitnami.org)

Or you can install them natively on your machine using the install guides provided by each framework.  I also search google for blogs about Drupal installation--for instance.  This gives you some personal insight into installing these frameworks and work-arounds when things don't work as you expect.  The installer guides are generally good, but sometimes there is a key step that is missing or slightly different in your situation.

I have not used Joomla, so I can't comment.

---

### Post by satimis on 2013-02-14
> **tgalati4 said:**
> All of these frameworks have a learning curve.  Some are easier than others.  You can install them easily as a "stack" to test them out using:

[http://bitnami.org](http://bitnami.org)

Or you can install them natively on your machine using the install guides provided by each framework.  I also search google for blogs about Drupal installation--for instance.  This gives you some personal insight into installing these frameworks and work-arounds when things don't work as you expect.  The installer guides are generally good, but sometimes there is a key step that is missing or slightly different in your situation.

I have not used Joomla, so I can't comment.

Thanks for your advice and link.

It won't be too difficult for me starting Drupal here.  I have an Oracle VirtualBox PC running with 1.5TB capacity.  There are at least 5 WordPress running, each with different installation method.

I'm prepared to have a go on Drupal.  Googling brought me many installation methods.  I'll follow;
How To Install Drupal 7 on Ubuntu Server 12.04
(Ubuntu Server Guide)
[http://ubuntuserverguide.com/2012/08/how-to-install-drupal-7-on-ubuntu-server-12-04.html](http://ubuntuserverguide.com/2012/08/how-to-install-drupal-7-on-ubuntu-server-12-04.html)

to preceed.

Usually the version of Drupal/WordPress on repo is NOT the latest.  I also found following guide;
Installer Guide - Community Documentation
[http://drupal.org/documentation/install](http://drupal.org/documentation/install)

Which of them shall I follow first?  TIA

B.R.
satimis

---

### Post by MrKaliman on 2013-02-18
It all depends for which purpose you want this website.
Drupal has a complicated backend interface for non technical content administrators.

Drupal is kind a heavy cms. If possible install varnish (reverse proxy caching) in front of the drupal webserver.
In Drupal you are able to install the varnish and expire module to administer the cache.

Have fun!

---

