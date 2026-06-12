---
title: "virtual hosting"
date: 2008-11-11
forum: Server Platforms
---

### Post by kennedy7 on 2008-11-11
Here is a basic virtual host setup.. First you open a terminal, then type "sudo gedit /etc/apache2/httpd.conf"
then you type in httpd.conf "NameVirtualHost *:80" , with no quotes.
Save that, then type "sudo gedit /etc/apache2/sites-available/site.conf".
Then copy this into it.....

NameVirtualHost *:80>

#if you want to setup example.site1.com use the folwing line in this (omit this line)

<VirtualHost *:80>
ServerName  example.site1.com
DocumentRoot /var/www/site1/example
</VirtualHost>

<VirtualHost *:80>
ServerName site1.com
DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost *:80>
ServerName site2.com
DocumentRoot /var/www/site2
</VirtualHost>


Site1 and Site2 are the domain names that you have to own, both in which are pointing to the ip adrress that is hosting your site.

Then in the terminal type "sudo a2dissite default"
then type "sudo /etc/init.d/apache2 reload"
Then to enable the other site type "sudo a2ensite site.conf"
Then type "sudo /etc/init.d/apache2 reload"
Then you will have a working virtualhost setup.


If this helps any1 please give thanks.


to show you that it works here are my 2 sites plus other examples...
[http://tyspage.doesntexist.com]("http://tyspage.doesntexist.com")
[http://tysite.doesntexist.com]("http://tysite.doesntexist.com")
and for the example. befor the domain
we have[http://example.tyspage.doesntexist.com]("http://example.tyspage.doesntexist.com")

---

### Post by oneloveamaru on 2008-11-11
I'm not sure why you have <NameVirtualHost *:80> so many times. You only need it once and it should already be in a file. Either Apache2.conf, ports.conf or the default site conf. Also, you don't need to put anything in httpd.conf as it's not really used in Debian/Ubuntu. It's there for the people coming from the RPM based distros.

You also only need to specify port 80 when you have other virtual hosts running on other ports. If they all run on port 80, you don't need it in there but would save you typing later down the road if you started using SSL or something like that.

And last, to keep things simple, don't put more than 1 site in the same config. When you have 15 sites in one config file, it gets big and bloated, especially if you start adding lots of options for each virtual host. I keep one domain in each file under /etc/apache2/sites-available/ named the site name, and then enable as you please, reload, to get them running.

---

### Post by CrucifiedEgo on 2008-11-12
Dead on. Oneloveamaru has it perfect.  In fact, i believe apache won't start if you define namevirtualhost *:80 more than once.

---

### Post by kennedy7 on 2008-11-12
My bad, i type that wrong, thanks guys for telling me.

---

### Post by kennedy7 on 2008-11-12
> **oneloveamaru said:**
> I'm not sure why you have <NameVirtualHost *:80> so many times. You only need it once and it should already be in a file. Either Apache2.conf, ports.conf or the default site conf. Also, you don't need to put anything in httpd.conf as it's not really used in Debian/Ubuntu. It's there for the people coming from the RPM based distros.

You also only need to specify port 80 when you have other virtual hosts running on other ports. If they all run on port 80, you don't need it in there but would save you typing later down the road if you started using SSL or something like that.

And last, to keep things simple, don't put more than 1 site in the same config. When you have 15 sites in one config file, it gets big and bloated, especially if you start adding lots of options for each virtual host. I keep one domain in each file under /etc/apache2/sites-available/ named the site name, and then enable as you please, reload, to get them running.

Its much easier placing it all in one file
but i do keep things like tyspage.doesntexist.com
and the example.tyspage.doesntexist.com
things like that i keep seperate but domains i keep in one file

And you do have to add "NameVirtualHost *:80" to httpd.conf.

But thank you.

---

### Post by oneloveamaru on 2008-11-13
I am a linux admin for roughly 30 servers and 300 domains running virtually in Apache, Tomcat and Java. The ONLY place I have "NameVirtualHost *:80" is in ports.conf. The only reason I have the :80 on it is because I also run an SSL site. Otherwise, it would not be needed.

If you read the apache2.conf file, it reads ALL of the config files in the /etc/apache directory. You could delete httpd.conf and it would have no bearing on apache. AS LONG as you didn't put anything important in it. Everything can go into apache2.conf or ports.conf.

root@server:/etc/apache2# grep -R NameVirtual *
ports.conf:NameVirtualHost *:80

But thank you.

---

### Post by kennedy7 on 2008-11-13
Thank you I have also read things telling me to put Namevirtualhost into ports.conf and apache2.conf, but those just didnt work for me. But a friend who has been in Linux since its been here has given me some howto's from apache's site that said to put Namevirtualhost into the httpd.conf file.
And i just thought it was easier.LOL
Thanks!

---

### Post by oneloveamaru on 2008-11-13
Right and those directions are not based on DEBIAN distributions. httpd.conf is still used in ALL Red Hat based distributions. You are on an UBUNTU forum that is based off of Debian.

In Red Hat based distro's there is a file called virtualhosts.conf, which they set up for people to put ALL virtual domains into. This does NOT exist on Debian based distros.

Nothing you said is technically wrong bro. Everything you said WILL WORK. It's just not the norm with Ubuntu.

---

### Post by kennedy7 on 2008-11-13
Oh, well i got an Ubuntu 8.10 server running all mine. Its works great.
Also would you know anything about making an irc bot for ircd-hybrd
Here is my irc im working on tyspage.doesntexist.com/6667 channel #ty

---

### Post by oneloveamaru on 2008-11-13
Sorry dude, i know nothing about IRC. Haven't even opened an IRC program in years.

---

### Post by kennedy7 on 2008-11-13
Oh, well thanks for your help man.

---

### Post by kennedy7 on 2008-12-03
Bump Bring up my post so that people can see the virtual hosting stuff.

---

