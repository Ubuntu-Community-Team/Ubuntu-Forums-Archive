---
title: "Intranet Server - Web CMS, Helpdesk, Monitoring Ideas"
date: 2010-01-06
forum: Server Platforms
---

### Post by quietas on 2010-01-06
I've tried several and I have been using GLPI for a while. Recently the server I had been using as our helpdesk and intranet server was re-purposed in an emergency to get a critical server replaced immediately.

This causes a problem of not having my trouble ticket system in place, but it also gives me the opportunity to replace it with something better.

The needs for this machine are to act as a network homepage with our intranet Wordpress site with the internal blog, monthly newsletter, various department information, corporate forms, and whatnot. Also this unit runs the GLPI helpdesk software. Various other bits like ZenOss and Groundworks are there as well.

Needs:
[LIST]
[*]Web CMS (Wordpress, Drupal, Joomla, ...)
[*]Helpdesk (GLPI, ORTS, eTicket, osTicket, ...)
[*]Monitoring (Nagios, ZenOss, Groundworks, ...)
[*]Active Directory Integration
[/LIST]

Wants:
[LIST]
[*]CMS with integrated helpdesk and seemless theme support
[*]Easy enduser access
[*]Easy admin access
[*]Custom trouble ticket forms
[*]IDS would be nice
[/LIST]

We already have two AD servers with DNS, DHCP, WINS, RADIUS, Print Queus and whatnot, no need to duplicate any of that. Also all of our custom apps are housed elsewhere.

Any ideas are welcome, especially if you are using them. If so, how well do they work and what is missing.

---

### Post by Thirtysixway on 2010-01-06
I pretty much point everyone to Drupal.  I've had nothing but good experiences with it and writing modules for it.  There are so many modules, you can probably find one for a helpdesk.  I haven't really looked but I'm sure there are plenty of people trying to integrate a helpdesk with drupal (or have it as a part of drupal.) [http://drupal.org](http://drupal.org)

---

### Post by quietas on 2010-01-06
I was looking at a couple of the Drupal modules which look like they might work. Has anyone used Storm or Support. I had found a decent summary of what Drupal has here: [http://groups.drupal.org/node/17948](http://groups.drupal.org/node/17948)

---

