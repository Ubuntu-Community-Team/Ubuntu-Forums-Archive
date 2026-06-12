---
title: "[SOLVED] Hobbit on Hardy"
date: 2008-06-10
forum: Server Platforms
---

### Post by luccom on 2008-06-10
I am trying to install Hobbit on a new Ubuntu 8.04 installatio running on a vmware server.

After installing Ubuntu Server I setup the server with a static IP.
I did a apt get update and upgrade then I installed apache2 and hobbit with apt-get.

When i try to access [http://server/](http://server/) I get the It works!`
When i try to access the hobbit page [http://server/hobbit/bb.html](http://server/hobbit/bb.html) I get Forbidden

In the apache log i found this:
[Tue Jun 10 06:03:42 2008] [error] [client 172.30.66.2] client denied by server configuration: /var/lib/hobbit/www/bb.html

What should I check next ?

---

### Post by mbeach on 2008-06-10
I've never used hobbit, but I'd suspect that you may need to change some ownership of the /var/lib/hobbit/www folder and files within.  I suspect, and it's a guess, that your apache runs as www-data, and your /var/lib/hobbit/www folder is not readable by www-data.

OR (more likely this...)

in your conf file it is restricted to deny from all for that folder.  I'd look in /etc/apache2/apache2.conf to see if there is a specific <Directory /var/lib/hobbit/www > directive, and adjust as necessary.  Not knowing how hobbit is installed, you may also find the file you need adjust in /etc/apache2/sites-available/
Since hobbit may contain some sensitive info about your network, the installation may be quite restrictive with respect to access, and you'll need to open it up likely for your particular IP, or from localhost or whereever you need to access it from.

---

### Post by luccom on 2008-06-10
Thanks mbeach ! you were right !

in /etc/apache2/apache2.conf I have the line:
Include /etc/apache2/conf.d/

in the file /etc/apache2/conf.d/hobbit i had this for my directory:
Allow from localhost ::1/128

and I changed it to this:
Allow from all

---

### Post by mbeach on 2008-06-10
glad that worked out.

from a security perspective, you may want to allow from a specific range of ips, or networks.  For example if you are only ever going to connect from your home network, you may use something like:
allow from 192.168
or whatever your network looks like.  If you would also like to connect from work (assuming this machine is at your home) you could also use something like 
allow from 192.168
allow from workdomainname.ca

anyways, just a thought - if you're just tinkering around with hobbit, and its working as intended, then good stuff, 'allow from all' it is.

some good reading on the 'allow' directive:
[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html)

---

### Post by hommeentete on 2008-10-26
This worked for me to show [http://server/hobbit/bb.html](http://server/hobbit/bb.html) but not any of the other pages.  For example, I bring up the main hobbit page and I click on one of my statuses (conn, cpu, disk, etc...) and I get:


Forbidden

You don't have permission to access /hobbit-cgi/bb-hostsvc.sh on this server.


All users have read and execute permissions on the bb-hostsvc.sh file and I made the same changes in my config as luccom did. I also restarted hobbit and apache after making those changes.  

This is an internal web server with me as the only person on the network most of the time so I'm not worried about allowing all.

Any ideas?

---

### Post by luccom on 2008-10-27
Can you post what is in your /etc/apache2/conf.d/hobbit ?

---

### Post by hommeentete on 2008-10-31
Here it is: (And like I said, this is an internal web server and I'm the only one on the network usually so security isn't much of a deal -- Thanks!)
=====================================================================

# This file is for Apache 1.3.x and Apache 2.0.x
#
# Add this to your Apache configuration, it makes
# the Hobbit webpages and cgi-scripts available in the
# "/hobbit" and "/hobbit-cgi" URLs.


# NB: The "Alias" line below must NOT be used if you have
#     the Hobbit webfiles as the root URL. In that case,
#     you should instead set this:
#
#          DocumentRoot /var/lib/hobbit/www

Alias /hobbit/  "/var/lib/hobbit/www/"
<Directory "/var/lib/hobbit/www">
    Options Indexes FollowSymLinks Includes MultiViews
    Order allow,deny
    Allow from all
</Directory>

ScriptAlias /hobbit-cgi/ "/usr/lib/hobbit/cgi-bin/"
<Directory "/usr/lib/hobbit/cgi-bin">
    AllowOverride None
    Options ExecCGI Includes
    Order allow,deny
    Allow from localhost ::1/128
</Directory>

ScriptAlias /hobbit-seccgi/ "/usr/lib/hobbit/cgi-secure/"
<Directory "/usr/lib/hobbit/cgi-secure">
    AllowOverride None
    Options ExecCGI Includes
    Order allow,deny
    Allow from localhost ::1/128

    # Password file where users with access to these scripts are kept.
    # Create it with "htpasswd -c /etc/hobbit/hobbitpasswd USERNAME"
    # Add more users / change passwords with "htpasswd /etc/hobbit/hobbitpasswd USERNAME"
    #
    # You can also use a group file to restrict admin access to members of a
    # group, instead of anyone who is logged in. In that case you must setup
    # the "hobbitgroups" file, and change the "Require" settings to require
    # a specific group membership. See the Apache docs for more details.

    AuthUserFile /etc/hobbit/hobbitpasswd
    AuthGroupFile /etc/hobbit/hobbitgroups
    AuthType Basic
    AuthName "Hobbit Administration"

    # "valid-user" restricts access to anyone who is logged in.
    Require valid-user

    # "group admins" restricts access to users who have logged in, AND
    # are members of the "admins" group in hobbitgroups.
    # Require group admins

</Directory>

---

### Post by luccom on 2008-11-03
Try replacing all the :
Allow from localhost ::1/128
to:
Allow from all

---

### Post by hommeentete on 2008-11-05
Nope - didn't work. :/

---

### Post by hommeentete on 2009-01-07
By the way, I just said screw it with hobbit and went to Nagios.  Nagios gave me 0 errors and I was up and running in 20 minutes.  They have a fantastic Ubuntu quick start guide on their site.

---

