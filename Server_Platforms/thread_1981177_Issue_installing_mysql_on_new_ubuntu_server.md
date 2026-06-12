---
title: "Issue installing mysql on new ubuntu server"
date: 2012-05-16
forum: Server Platforms
---

### Post by mjfroggy on 2012-05-16
I just setup a ubuntu apache2 tomcat server and now I am needing to install mysql. So on the command line when I type in
sudo apt-get install mysql-server

I get a line that reads
E: Couldn't find package mysql-server

Also when I do a 
sudo apt-get update

I see a bunch of "failed to fetch" error lines all seem to be from a 404 for ip address 91-189-88-22-80 which is a ubuntu server 

I also thought maybe the mysql package was called something else so when I did a 
sudo apt-cache search mysql
I get the followingerror ???
rsyslog - enhanced multi-threaded syslog

So any suggestions? 
I posted this on another forum and was told to follow this (which did not help anything at all) and I want to install mysql not peconia server
[http://www.percona.com/doc/percona-s.../apt_repo.html](http://www.percona.com/doc/percona-s.../apt_repo.html)


Suggestions?

---

### Post by darkod on 2012-05-16
Try to select another server in the Updates options? If it can't find the one it tries, try another one.

---

### Post by mjfroggy on 2012-05-16
Well their seems to be no karmic directory in the ubuntu archive anymore ?? I get a bunch of 404 not found when doing a apt-get update for example one of the urls is

us.archive.ubuntu.com/ubuntu/dist/karmic-updates/multiverse/source/Sources.gz   

So how would I change what repo I use?

---

### Post by darkod on 2012-05-16
Is this a server edition or desktop acting as server?

Karmic was released 10/2009. Since the desktop version has 18 months of support for none-LTS releases, the desktop is end of life. But the server versions have 3 yrs support and still should be supported until 10/2012.

This should help locating the EOL repositories. Basically you need to use old-releases.ubuntu.com instead of archive.ubuntu.com.
[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

But if you are running the server version I am still confused because it should be supported until October.

On another note, you might wanna consider upgrading to a more recent version, even better if it's LTS, like 10.04 or the latest 12.04. If you are still not sure in the latest 12.04, you can go for 10.04.

---

### Post by SeijiSensei on 2012-05-16
This is a good example of why you only want to run releases with long-term support on production servers.

If this is a new server, then start over with the 12.04 server edition.

---

### Post by LHammonds on 2012-05-16
> **SeijiSensei said:**
> This is a good example of why you only want to run releases with long-term support on production servers.

If this is a new server, then start over with the 12.04 server edition.
QFT

However, if this is a production server that must absolutely be reliable, go with 10.04 LTS.  It has been around the block and you can easily find solutions to just about any problem you run across.  I think even the makers of Ubuntu do not recommend 12.04 LTS until a couple of revisions have been made to make it more stable.

The servers I depend upon are running 10.04 LTS right now.  New servers that are not mission-critical are starting off as 12.04 LTS (such as my MediaWiki server)

LHammonds

---

### Post by SeijiSensei on 2012-05-16
It depends on what you're using a server for, I guess.  The packages I use -- bind9, apache2+php, PostgreSQL, sendmail -- have been around a long time.  Most upgrades for those are pretty uneventful.  PostgreSQL had some binary data compatability issues between major versions, but I always rebuild the databases from a good plain-text dump.  

I upgraded a server from 11.04 to 12.04 recently using "do-release-upgrade" twice.  Everything survived intact.  (I wasn't responsible for the original 11.04 installation; I would have used 10.04 LTS, of course :))

---

### Post by mjfroggy on 2012-05-17
Thank you all

So I just burned the latest Ubuntu (v12) to a disk and installed it on the server. Now my issue is I selected to install openssh and tomcat   when I went through the install.

So now my issue is I am able to reach the server via ssh and using its ip address however when I type in the ip address in my browser I can not reach the server its not found. I made sure I started tomcat6 which shows as running and I also tried to go to [http://myip:8080](http://myip:8080)

and still get a not found error? So I am thinking maybe I didnt install something that I was suppose to. I dont see httpd or apache2 in the etc/init.d folder should I have installed hpptd or somthing aside from having selected the tomcat and openssh options during the install wizard?

This needs to be a java server that will serve up jsp pages on my office LAN 

thanks all

---

### Post by LHammonds on 2012-05-18
How did you install Tomcat?  Did you type **aptitude install tomcat6**?

If you do not install apache2, you will not get any response on port 80 (I think).  Tomcat operates on port 8080 by default (unless you changed the config).  So immediately after install, you should be able to see the main Tomcat page at IP:8080

If you make a helloworld.jsp page, you would access it by typing IP:8080/helloworld.jsp

After you check your tomcat config file and verify the service is running, check to see if your firewall is enabled and blocking that port.

LHammonds

---

