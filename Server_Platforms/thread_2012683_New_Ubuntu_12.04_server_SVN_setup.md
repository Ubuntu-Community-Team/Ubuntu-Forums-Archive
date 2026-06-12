---
title: "New Ubuntu 12.04 server SVN setup"
date: 2012-06-29
forum: Server Platforms
---

### Post by ajf412 on 2012-06-29
Decided to wipe the drives clean and start over, so I can get this set up right.  I have found this tutorial that I'll be using to set up the server:
[http://rbgeek.wordpress.com/2012/05/01/svn-server-on-ubuntu-12-04-lts-with-web-access/](http://rbgeek.wordpress.com/2012/05/01/svn-server-on-ubuntu-12-04-lts-with-web-access/)

**Going to be using this primarily as a Subversion server for team development**.  If Ubuntu allows it, we would also like to host our alpha/beta tests for the game we are developing, though at that point, we would be okay with splurging for Windows Pro if the software requires it (using CryENGINE 3 SDK).  When the game goes live, we'll splurge for real servers, and whatever software is required.  Until then, we just need to get something up and running that will make due.

We have folks from America, UK, and Mid-East.  I figure I would post here as I run into questions until I get it set up, to help keep my posts less confusing and/or garbled.

---

### Post by ajf412 on 2012-06-29
1.  What type of "Software selection" should I make when installing the server?

OpenSSH server
DNS server
LAMP server
Mail server
PostgreSQL database
Print server
Samba file server
Tomcat Java server
Virtual Machine host
Manual package selection

Does it even really matter, because I'll just be installing software as I need it?  I'm thinking start with OpenSSH and then installing apache, and moving from there.

---

### Post by ajf412 on 2012-06-29
I went with OpenSSH

---

### Post by LHammonds on 2012-06-29
OpenSSH is typically the only package I select when setting up a server.  Once the server is configured, I then add whatever packages I need.

Check my sig for examples.

LHammonds

---

### Post by ajf412 on 2012-06-29
Thank you LHammonds.  That helps clarify a lot of Ubuntu for me, actually.

---

### Post by ajf412 on 2012-07-03
That tutorial worked wonderfully.  =)

Okay, so if I'm using
[COLOR=#ff0000]sudo htpasswd -m /etc/apache2/dav_svn.passwd <username>

[COLOR=Black]to make users, what do I enter to delete users?[/COLOR]
[/COLOR]

---

### Post by arbabnazar on 2012-08-24
> **ajf412 said:**
> That tutorial worked wonderfully.  =)

Okay, so if I'm using
[COLOR=#ff0000]sudo htpasswd -m /etc/apache2/dav_svn.passwd <username>

[COLOR=Black]to make users, what do I enter to delete users?[/COLOR]
[/COLOR]

Actually, I am the writer of this tutorial :D

TO delete the user:
sudo htpasswd -D /etc/apache2/dav_svn.passwd <username>

where: 
dav_svn.passwd is the file that contain the users at /etc/apache2/ location.

-D: Delete the user

username: the user that we want to delete

---

### Post by dthury on 2012-09-12
I'm having trouble!!  This week I needed to completely rebuild my SVN server (upgraded from ubuntu 10.04 to 12.04 in the process).  I have successfully restored my subversion repository, but can't get web access working!


I've done all the steps in the tutorial.  Here's my dav_svn.conf

   <Location /home/mySvn>
   DAV svn
   SVNParentPath /home/mySvn
   SVNListParentPath On
   AuthType Basic
   AuthName "Subversion Repository"
   AuthUserFile /etc/apache2/dav_svn.passwd
   Require valid-user
   </Location> 

When I try browsing to   [http://svnserver/mySvn](http://svnserver/mySvn), I get

   The requested URL /mySvn was not found on this server.

Browsing to http:/svnserver  returns "It Works..."

What am I missing?

Thanks,
  Denny

---

### Post by HugoSerrano on 2012-09-12
Hello!

try 

**<Location /mySvn>**
   DAV svn
   SVNParentPath /home/mySvn
   SVNListParentPath On
   AuthType Basic
   AuthName "Subversion Repository"
   AuthUserFile /etc/apache2/dav_svn.passwd
   Require valid-user
   </Location>

---

### Post by dthury on 2012-09-16
That solved my immediate problem; I'm now getting an "Internal Server Error" error:

[COLOR="DarkRed"]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.22 (Ubuntu) Server at svnserver Port 80[/COLOR]

But now I have something I should be able to better troubleshoot

---

### Post by dthury on 2012-09-16
Found the problem!  Turns out it was a typo error in the AuthUserFile file name!  Corrected that, and I now can access my repository via Web (locally and remotely)

Thanks for your help.

---

