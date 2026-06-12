---
title: "ubuntu server lts 6.06 setup with tomcat and virtualhost support"
date: 2007-01-20
forum: Server Platforms
---

### Post by webellusion on 2007-01-20
1) I have been browsing + searching many websites [including this forum] for a good tutorial on setting up a webserver on ubuntu server LTS 6.06 with apache + tomcat + mysql + php and allowing the support for name-based virtualhosts [i.e. more than one site].

For security reason the machine is behind a firewall and has ONLY port 80 forwarded to the outside world on the main firewall [outside my control]. It will be nice to see a tutorial that covers all of that (i.e. how to change default tomcat port 8080 to 80).

2) Recently I have bumped into [Glassfish]("https://glassfish.dev.java.net/") tutorial at [http://weblogs.java.net/blog/cayhorstmann/archive/2006/07/installing_glas.html]("http://weblogs.java.net/blog/cayhorstmann/archive/2006/07/installing_glas.html")  which explains setting up Glassfish [something new to me] under ubuntu but 1] its for PostgreSQL 2) it doesnt explain setting up virtualhost support

3) I would like to follow either of the above, whichever is more suitable (upon recommendation) and would like advice/tutorial on setting it up. All I am after is to be able to run Java Server Pages on multiple domains [which I already have] using the easiest methods available [Tomcat or GlassFish] and at the same time have support for MySQL and PHP.

Any Recommendation or Tutorials as I am a noob to all of this?

---

### Post by mssever on 2007-01-21
When it comes to Apache, PHP, and MySQL, just install them from Synaptic or aptitude. If you enable the universe repository, you can also get tomcat5 from there--at least in Edgy (Ubuntu 6.10). Synaptic/aptitude/apt-get is the preferred method of installation in Ubuntu.

To set Apache up for virtual hosts, see the Apache manual: 
[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

In Ubuntu, virtual host configuration lives in /etc/apache2/sides-available. The file default contains the default configuration (for when none of the virtual hosts match). For each vhost, create a file in that directory to hold that vhost's config. Then, for any vhost you want to have enabled, create a symlink to /etc/apache2/sites-enabled. For example: ```
cd /etc/apache2/sites-enabled
sudo ln -s ../sites-available/foo.com 01-foo.com
```Remember that every time you make a change to Apache's configuration, you have to tell Apache to re-read its configuration:```
sudo /etc/init.d/apache2 graceful
```

---

