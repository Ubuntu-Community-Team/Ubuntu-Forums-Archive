---
title: "Apache2 (v2.2) Restricted Access Problem"
date: 2016-02-03
forum: Server Platforms
---

### Post by raskolnik on 2016-02-03
Hello,

I'm fairly new to Apache, and I'm having some trouble getting it set up the way I would like. I'm using it to run rutorrent, an html frontend for rtorrent, but I would like to restrict access to the site by requiring a password if the connection is coming from outside my NAT network. No password should be required if I access it from inside the network. I'm using Apache 2.2.22.

Basically I have a wifi network which the entire household can access (Network1), and connected to this is a router which uses NAT to create a second network (Network2). The Apache server is connected to Network2... Network2's router is forwarding port 80 to the server. I want to be able to connect to Network1 by wifi, access the server, and have it request a password. However, if I connect to Network2 and access the server, it should not ask for a password.

Here is what I've added to /etc/apache2/apache2.conf:

```

<Directory /var/www>
  Order Deny,Allow
  Deny from all
</Directory>

<Directory /var/www/rutorrent>
  AuthType Basic
  AuthName "Restricted Access"
  # (Following line optional)
  AuthBasicProvider file
  AuthUserFile /etc/apache2/passwords

  Require user user

  Order Deny,Allow
  Deny from all
  Allow from 192.168.2
</Directory>

```

Where "user" is the user account I created with htpasswd.

192.168.1.0 is Network1.
192.168.2.0 is Network2.

Two other problems appear with this setup. First, [http://[server]/](http://[server]/) is accessible within both networks (it asks for a username/password for both). Second, if I access [http://[server]/rutorrent](http://[server]/rutorrent) and enter an incorrect password, I'm granted access to rutorrent... but it's not connected to the rtorrent session. That's baffling. I want it to access nothing if a wrong password is entered.

So I'm definitely doing something wrong here. Can anyone give me any pointers? Thanks.

---

### Post by raskolnik on 2016-02-03
I worked it out. I'll post the solution in case anyone else has a similar problem.

I posted a section of my /etc/apache2/apache2.conf file in the previous post, and here is the fixed version of that section:

```

<Directory /var/www/rutorrent>
  Options +FollowSymLinks
  AllowOverride None

  Order deny,allow
  Deny from all
  Allow from 192.168.2

  AuthType Basic
  AuthName "Restricted Access"
  # (Following line optional)
  AuthBasicProvider file
  AuthUserFile /etc/apache2/passwords
  Require user grant

  Satisfy Any
</Directory>

```

This does everything I wanted it to. I was noobing it.

As for the two other issues I mentioned at the end of my post, they ended up being pretty simple as well. The <Directory /var/www> entry was being overridden by /etc/apache2/sites-available/default. So I removed that section from apache2.conf and edited sites-available/default directly. The second minor issue ended up being my browser caching the files. Whoops!

That's it, everything works now.

---

