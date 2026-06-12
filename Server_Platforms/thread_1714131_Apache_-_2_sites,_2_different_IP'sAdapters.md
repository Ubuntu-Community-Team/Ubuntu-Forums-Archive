---
title: "Apache - 2 sites, 2 different IP's/Adapters"
date: 2011-03-25
forum: Server Platforms
---

### Post by fenderr357 on 2011-03-25
Alright, so like the title says, I am trying to host 2 web sites - each of which have there own public IP and physical network adapter. Just fyi, one is going to be a Moodle site, and the other just a simple directory listing.

For the details, I am having problems figuring out which configuration file to place which directives.  Here is some code I found off the apache website: (I know these a private IP's but the concept should be the same)

```

Listen 80

# This is the "main" server running on 172.16.3.103
ServerName 172.16.3.103
DocumentRoot /var/www/first

# This is the other address
NameVirtualHost 172.16.3.104

<VirtualHost 172.16.3.104>
DocumentRoot /var/www/second
ServerName 172.16.3.104

# Other directives here ...

</VirtualHost>

```Does this go in httdp.conf, sites-enabled/sites-available, or somewhere else? What goes where? No matter what I get some kind of error like this:

(this one makes especially no sense because I can't find "NameVirtualHost *:80" anywhere in the conf's)
```
 [warn] NameVirtualHost *:80 has no VirtualHosts
```or
```
(98)Address already in use: make_sock: could not bind to address [::]:80
```Any help would be greatly appreciated!! Thanks

---

### Post by volkswagner on 2011-03-25
How is your DNS handled?  How is routing/port forwarding handled?

Can you forward port 80 to each card?  

What version of Ubuntu are you using?


Depending on what version you are running, newer versions have the "NameVirtualHost *:80" directive in ports.conf, older versions had it in httpd.conf.

With the above in ports.conf apache should listen on all addresses.

I prefer to setup NameVirtualHost as per the documents in the [sticky thread]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html").  Keep separate host files for each virtual host.

I'm not sure you can bind two separate NIC's to Apache.  It is worth a try.  If not you may need to set up a reverse proxy from your main site to your moodle site.


You could then try to set up two host files in /etc/apache2/sites-available.

See what is in there now:

```
ls -alt /etc/apache2/sites-available
```

If the default is still there and un-touched, you can simply copy it to your new sites and edit accordingly.  If not you can use the following for basics.

For main site

```
sudo nano /etc/apache2/sites-available/main
```

Then put the following:

```
# This is the "main" server running on 172.16.3.103

<VirtualHost 172.16.3.103:80>
ServerName mydomain.com
ServerAlias www.mydomain.com
ServerAdmin yourname@email.com
DocumentRoot /var/www/first
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/first>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

</VirtualHost>


```


Then do similar for moodle site, changing ip, servername, serveralias, documentroot, and directory info.

You can then enable each site (the following creates a sym link from sites-available to sites-enabled)

```
sudo a2ensite main
```
```
sudo a2ensite moodle
```

The restart apache2 for changes to take affect.

```
sudo /etc/init.d/apache2 reload
```

You can check enabled sites by listing site-enabled.  You may want to disable the default site, but keep the config file.

```
sudo a2dissite default
```

Then restart apache.

---

### Post by fenderr357 on 2011-03-25
> **volkswagner said:**
> How is your DNS handled?  How is routing/port forwarding handled?

Can you forward port 80 to each card?  

What version of Ubuntu are you using?


At this point, none of my addresses are named. This is for a University and we have a huge public IP space, so I don't even have to worry about port forwarding, as far as a home router would be concerned. 

> Keep separate host files for each virtual host.This was my problem! I was putting everything in httpd.conf and completely ignoring the sites enabled/available. After separating the virtual hosts into different files and setting ports.conf to "Listen 80" everything just started working (at least on the local machine, I haven't had time to get up there and try from the network).

I do have one more question though. It is about ServerName in apache2.conf - Do I need to have two of these? i.e like this:

```
ServerName 172.16.3.103
ServerName 172.16.3.104
```Or does this ServerName not matter at all? I noticed both sites work with just one or both in there.

Again, thank you for all your help.

---

### Post by volkswagner on 2011-03-25
I don't think you need the ServerName directive in apache2.conf.  It goes in each respective host file.

I have never done Name based Virtual Hosts, without names, so your mileage may vary.  Perhaps you can just assign a name, either one you know does not exist on the Web, or create a name like moodle.local.  If you decide to create a name, you may want to add it to /etc/hosts file.


Glad you're up and running.

---

### Post by fenderr357 on 2011-03-31
Okay so here's a little update - I have Moodle up and running just fine, but I am starting to think that I need to change my plan on the second site.

Basically it is going to be a way for students to upload html files and then browse to them, to test them out. I would like to do this with FTP - there is no real need for secure transactions because it is simple (almost 'hello world') type stuff.

I have found that the way to do this is by using the userdir module (users have a public_html folder in there home folders); But I don't know how to limit this to the second IP - it seems like 172.16.3.103/~jdoe and 172.16.3.104 /~jdoe both work. Is there anyway to only have requests to one of the IP's be able to pull up user dirs?

Also, if I use an FTP server like vsftpd, is there anyway to restrict the users from browsing to other directories out of their home folders (can't have cheaters..lol)?

I really appreciate all the help. Thanks!

---

### Post by volkswagner on 2011-04-01
I have no experience with UserDir.

You could try adding the following to your virtual host file for the site you don't want UserDir active.

```
UserDir disabled *
```

Add the above comment under ServerName or ServerAdmin... anywhere above DocumentRoot or <Directory>.

For ftp, look up jailed home directory.  For the FTP server you are using, there should be a directive in the .conf to jail users to /home/username.

---

