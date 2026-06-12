---
title: "how do I set up http server with ftp access for modifing my site?"
date: 2005-10-28
forum: Server Platforms
---

### Post by pabc on 2005-10-28
Morning,

I've read through the howtos and cant find this answer.

Basically on a small office network I want a breezy install running a web server and I want to be able to ftp into it to make changes to the site.

I'm guessing I can just do a standard breezy install then choose via synaptic to install apache and a ftp server? I dont need php or msql. Just ssi which I believe apache will handle.

Are there any guides around to help me through the process of configuring apache and whatever FTP server I find in the repos?

Cheers for any advise or links offered.

P

---

### Post by Appolusionist on 2005-10-28
[quote=pabc]
 
Are there any guides around to help me through the process of configuring apache and whatever FTP server I find in the repos?
[/quote]
 
Maybe this [guide]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") is what you are looking for. It is more than what you are looking for, but maybe you edit the portions out you don't need.

---

### Post by pabc on 2005-10-28
OK, now I'm scared.

I've got as far as installing apache on but on pointing my browser @ 127.0.0.1 but I get connection refused from the default configuration.

I dont know which bits of that guide I need ignore. Its a tad initimidating for a complete novice.

Is there anything other than apache I need to install for a basic web server to work?

On reading through the .conf files it seems to me that the defaults should result in listening to requests on :80 as soon as the apache service is started.

edit: Netstat -tup doesnt list anything like apache listening so I'm guessing it doesnt work with the default confs and I need to go find whats wrong.

P

---

### Post by herrpoon on 2005-10-28
Hi, which guide have you been following?  When I set up apache I used the following one: [https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29)

To install apache you should run the following command: ```
sudo apt-get install apache2
```

This will install apache for you, and you shouldn't have to do anything more than that to get it running.  Then to view the default webpage (will be some debian/apache page) you need to make sure you're using the right internal address for your ubuntu machine.  For example, to access my websever internally, I'd type http:192.168.2.5 into my browser.  It may be that 127.0.0.01 or whatever isn't the right internal address and hence why it's not wroking.  To find out your internal address type this into console: "ifconfig" then the top bit should tell you what your internal address is.

Also what does ```
ps ax | grep apache
``` spit out?

---

### Post by pabc on 2005-10-28
cheers for that reply - youve just confirmed what I finally figured out.

Instead of starting the service from gnome gui I did it from bash and got an error saying line 80 no file etc.

looking through the apache2ctl script line 80 sets up the var for the location of httpd binary which is missing.

Id installed apache2common rather than apache2. I have no net access yet so the only repo I have is a breezy CD and apache2 isnt there.

I'll hook it up to the net, add the repos and I'll be good to go.

Cheers

P

---

### Post by mcewen98 on 2005-10-28
[QUOTE=pabc]cheers for that reply - youve just confirmed what I finally figured out.

Instead of starting the service from gnome gui I did it from bash and got an error saying line 80 no file etc.

looking through the apache2ctl script line 80 sets up the var for the location of httpd binary which is missing.

Id installed apache2common rather than apache2. I have no net access yet so the only repo I have is a breezy CD and apache2 isnt there.

I'll hook it up to the net, add the repos and I'll be good to go.

Cheers

P[/QUOTE]

apache2 should be on the breezy cd.

---

### Post by pabc on 2005-10-28
Hmm,

I opened synaptic and searched for apache in name & description and apache2 wasnt there. I'm assuming that the CD is set up correctly as a repo by default.

I've grabbed the apache source off a net eneable pc and compiled it anyway. Netstat now shows it as listening on :80 so its good to go.

Sadly I cant actually get it to work as I always get "no response from server" on attempting [http://localhost/](http://localhost/) (and all variants) and pinging localhost or 127.0.0.1 results in no echo.

I'm a tad stumped. I'm guessing it's something to do with not having connect the LAN to the intranet yet and the connection is missing it's DHCP. I've configured all the setting manually (but not plugged in a cable) and still no ping.

By contrast, as an experiment, I got apache up and running in <1 min on my home machine which has all the repos and a live net connection. I've since removed it.

P

---

### Post by billy314159 on 2005-11-09
awesome guide

---

### Post by grendelkhan on 2005-11-10
Did you enable it in inetd and then restart inetd?

---

### Post by LordHunter317 on 2005-11-10
Apache doesn't normally run in inetd and you shouldn't ever do that anyway.

Anyway, on Debian and Ubuntu, you shouldn't use apache2ctl more or less ever.

---

### Post by tonym on 2005-11-13
[QUOTE=pabc]and I want to be able to ftp into it to make changes to the site.[/QUOTE]

Rather than using ftp to upload your site,  you might be better of using ssh.  As well as letting you log on,  it supports scp (secure copy) and sftp (secure FTP).  Konqueror supports sftp,  don't know about Firefox.

Regards

Tony.

---

