---
title: "a2ensite"
date: 2012-11-14
forum: Server Platforms
---

### Post by jonesyp on 2012-11-14
Hello,

I have read the documentation but I am struggling to understand the reason for a2ensite.

I have a LAMP set-up in Ubuntu 12.04 and have folders for Joomla, Wordpress, Drupal etc and have managed to install each application successfully in each sub-folder.

Some guides for installing applications such as Joomla use the a2ensite command:

For example:

[B][I]2. Configuring Joomla and Apache

Run now these commands to add a Joomla config file to Apache: 

cd /etc/apache2/

sudo cp sites-available/default sites-available/joomla

Next, enable the Joomla website with these commands:

sudo a2ensite joomla

sudo /etc/init.d/apache2 restart
[/I][/B]


Cam I ask why this is important and if I need to do it for every application I run in a separate folder. 

Many thanks

Peter Jones
Crawley
UK

---

### Post by Lars Noodén on 2012-11-14
a2ensite is for enabling different [virtual hosts](http://httpd.apache.org/docs/2.2/vhosts/).  If you run everything from one and the same host, then you only need one virtual host.  If you were going to be running several different sites from the same web server, then you could make use of port-based virtual hosts or name-based virtual hosts.

---

### Post by Wim Sturkenboom on 2012-11-14
I'm not sure what joomla exactly tries to achieve with the above as it's actually incomplete in my opinion. It will however prevent a (possible) clash of session variables.

Assume that your joomla 'site' keeps track of a userid in a session variable called userid (e.g. to allow certain operations on the site) and that your drupal 'site' also keeps track of it for the same reason.
At the moment that you login in your joomla 'site, and you navigate to your drupal 'site', you're also logged in there (maybe with an userid that allows more).

Note that I used single quotes around the word 'site' as it's actually not a site.

a2ensite is there to enable different websites on the same host (so-called virtual hosting). You can then e.g. access your joomla site using [noparse]http://joomla[/noparse] en your drupal site with e.g. [noparse]http://drupal[/noparse].

Your ...../sites-available/joomla and so on however need to be modified to indicate that the servername is joomla and the document root must point to the directory where joomla is installed. Same for drupal etc

---

