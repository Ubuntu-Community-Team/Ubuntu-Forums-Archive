---
title: "Apache2 httpd configuration"
date: 2012-03-24
forum: Server Platforms
---

### Post by Greyvend on 2012-03-24
Hello, I've installed apache2 on Oneric Ocelote, httpd.conf has only one line: ScriptAlias /cgi-bin/ /home/serj/workspace/cgi/ (I need the server only for developing some CGI-apps, it's just university task)
When I try to start the server with *sudo apachectl start*, httpd seems to be ignored, the standard cgi-bin directory isn't mapped to /home/serj/workspace/cgi/.
When I use 
```
sudo /usr/sbin/apachectl -f /etc/apache2/httpd.conf
```
there is an error: 
```

Invalid command 'ScriptAlias', perhaps misspelled or defined by a module not included in the server configuration
Action '-f /etc/apache2/httpd.conf' failed.
The Apache error log may have more information.

```
I've tried another directives from standard modules (such as AddHandler), but it says the same.
mods-enabled/ directory contains alias.load and alias.conf

---

### Post by dharmavir on 2012-03-24
Hi Greyvend,

You should not force start Apache2 using httpd.conf as by default when you setup apache2 as apache package or Ubuntu server's lamp-server tasksel it stores it's config file in /etc/apache2/apache2.conf.

At the end of /etc/apache2/apache2.conf, httpd.conf is included which is empty by default on initial setup. So if you want to extend or add any config options you can do that in httpd.conf but most of the primary parameters will be setup in apache2.conf.

I hope this helps.

---

### Post by SeijiSensei on 2012-03-24
> httpd.conf has only one line

On Ubuntu, httpd.conf is empty and largely deprecated. You need to place the [ScriptAlias]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html#scriptalias") inside of a server definition.

The default configuration on Ubuntu consists of the contents of /etc/apache2/apache2.conf and the server defined in /etc/apache2/sites-available/000-default.  Edit the latter file and insert your ScriptAlias directive there.

---

### Post by Greyvend on 2012-03-24
> **SeijiSensei said:**
> On Ubuntu, httpd.conf is empty and largely deprecated. You need to place the [ScriptAlias]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html#scriptalias") inside of a server definition.

The default configuration on Ubuntu consists of the contents of /etc/apache2/apache2.conf and the server defined in /etc/apache2/sites-available/000-default.  Edit the latter file and insert your ScriptAlias directive there.

Thank you, /etc/apache2/sites-available/default and .../default.ssl were those files, where ScriptAlias was already written. I've changed directories and it is ok now. But I still do not understand, why changing httpd.conf  doesn't affect the server configuration? (BTW I've tried to edit apache2.conf - again with no result). And what configuration files supposed to be modified to configure server in other situations?

---

### Post by SeijiSensei on 2012-03-24
Most of the time you'll leave apache2.conf untouched and create or modify virtual host definitions in /etc/apache2/sites-available.  apache2.conf contains the "server-level" directives like the port on which apache listens, while the directives that apply to each virtual host reside in sites-available.  To create a new virtual host, copy 000-default to a new name, edit it as you see fit, then create a symlink to it in sites-enabled.  You can use the a2ensite command for this, or just create the symlink manually by running

```

cd /etc/apache2/sites-enabled
sudo ln -s ../sites-available/filename
sudo service apache2 restart

```

Each virtual host requires a unique ServerName directive, like "www.example.com" and "www2.example.com".  You'll need to have DNS or /etc/hosts configured to point these various names to the server's IP address.

---

### Post by Greyvend on 2012-03-25
Ok and what about httpd.conf? Isn't it supposed to be filled with some configurations?

---

### Post by Doug S on 2012-03-25
> **Greyvend said:**
> Ok and what about httpd.conf? Isn't it supposed to be filled with some configurations?
 
Not for Ubuntu systems. Several versions ago httpd.conf was used a lot. Debian linux, from which Ubuntu is derived, does it different now and as Seiji described. httpd.conf is now almost always an empty file. This can be confusing, as there are lots of intructions on internet, including at apache.org, that say to edit stuff into the httpd.conf file. One has to be careful to find up to date instructions that relate to the actual version of of linux they are using.

---

