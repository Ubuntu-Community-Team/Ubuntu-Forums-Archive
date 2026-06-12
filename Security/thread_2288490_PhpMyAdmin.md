---
title: "PhpMyAdmin"
date: 2015-07-27
forum: Security
---

### Post by dan138 on 2015-07-27
I have an Ubuntu 14.04 installed on a server.  I did a standard apt-get install of PhpMyAdmin a while back.  I was digging through the Appache logs today and noticed someone was requesting the page  domain.com/phpmyadmin/js/messages.php  

This is viable on the web.  Did I make a mistake? Is there a problem with the default install of PhpMyAdmin? 

Other than this oddity there is no evidence of someone hacking into my server.

---

### Post by SeijiSensei on 2015-07-27
Automated scanners attempt to exploit all kinds of things like this.  You should restrict phpmyadmin to only accept requests from IP addresses you trust: [http://httpd.apache.org/docs/2.4/howto/access.html](http://httpd.apache.org/docs/2.4/howto/access.html)

---

### Post by QIII on 2015-07-27
I don't even have phpmyadmin installed on my web server.  I administer MySQL remotely over SSH.

Still, there are hundreds  of attempts to find it.

---

### Post by dan138 on 2015-07-27
> **SeijiSensei said:**
> Automated scanners attempt to exploit all kinds of things like this.  You should restrict phpmyadmin to only accept requests from IP addresses you trust: [http://httpd.apache.org/docs/2.4/howto/access.html](http://httpd.apache.org/docs/2.4/howto/access.html)

That would be fine if I had a dedicated IP and didn't need to access it when I travel. 

> **QIII said:**
> I don't even have phpmyadmin installed on my web server.  I administer MySQL remotely over SSH. 

Still, there are hundreds  of attempts to find it.

Yeah, I assumed it was automated. I checked a few sites that I figured were running a LAMP stack and found this page visible on several.  It appears to me to dump a lot of data, but heck if I know what it means.  The actual script is on gethub:  [https://github.com/phpmyadmin/phpmyadmin/blob/master/js/messages.php](https://github.com/phpmyadmin/phpmyadmin/blob/master/js/messages.php)

---

### Post by TheFu on 2015-07-27
Someone requesting those pages **is** a hacking attempt.  Php and some of the easier-admin-webapps have code errors that allow people to break in and gain control of the server.

IMHO, 

* Using a web administration tool is an issue.
* Making a tool like that available to any internet address is another issue.
* Allowing **any** remote access to *php on a webserver (admin.php, install.php, setup.php and others) is an issue.

To mitigate the issues, there are a few choices:
a) don't allow remote access (only use localhost)
b) don't install those tools - especially when you are new and don't know all the ramifications.

So - if you do "a" - use an ssh tunnel for access. Be certain that ssh uses key-based authentication for anything internet facing.  Never use passwords over the internet. Be certain to secure the ssh tunnel too. If the hosting provider doens't support ssh - **FIRE THEM IMMEDIATELY!!!!**  The days of telnet and FTP-only access ended in 1994.

Now you need a way to validate that nothing has been harmed on the box.  I would compare all the current files on the box to a known-good backup from before these attempts happened.  That backup would NOT be stored on the same machine. Daily, automatic, versioned backups are the #1 security tool.  For high-risk servers (i.e. those that are internet facing), having 120 days of backups makes sense.

IMHO.

---

### Post by CharlesA on 2015-07-27
+1 to TheFu.

I don't use any web-admin tools for that reason, but if I did, I would set them up so they are only accessible via VPN. That way you can whitelist one IP and then reject all other traffic to it.

---

### Post by dan138 on 2015-07-27
> **TheFu said:**
> Someone requesting those pages **is** a hacking attempt.  Php and some of the easier-admin-webapps have code errors that allow people to break in and gain control of the server.

IMHO, 

* Using a web administration tool is an issue.
* Making a tool like that available to any internet address is another issue.
* Allowing **any** remote access to *php on a webserver (admin.php, install.php, setup.php and others) is an issue.

To mitigate the issues, there are a few choices:
a) don't allow remote access (only use localhost)
b) don't install those tools - especially when you are new and don't know all the ramifications.

So - if you do "a" - use an ssh tunnel for access. Be certain that ssh uses key-based authentication for anything internet facing.  Never use passwords over the internet. Be certain to secure the ssh tunnel too. If the hosting provider doens't support ssh - **FIRE THEM IMMEDIATELY!!!!**  The days of telnet and FTP-only access ended in 1994.

Now you need a way to validate that nothing has been harmed on the box.  I would compare all the current files on the box to a known-good backup from before these attempts happened.  That backup would NOT be stored on the same machine. Daily, automatic, versioned backups are the #1 security tool.  For high-risk servers (i.e. those that are internet facing), having 120 days of backups makes sense.

IMHO.

I really and truly appreciate your comments. Sincerely. I generally agree with you. Nothing on this server is critical -- it's my learning server.

a) sftp is painfully slow. How do you feel about ftp over TLS?

b) So much sh*t does have *php web-facing!  There are about 70 million Wordpress sites all with wp-admin facing the public web. As much as I hate this stuff I want to learn how to deal with it as best possible. 

c) What i'd like to know is where the screwup happend: Was it me? Is the PhpMyAdmin team incompetent? Does Ubuntu check packages out for these kind of problems or do they just make sure all the dependencies are satisfied? 

Concerning versionded backups for security, can you elaborate on this a little? I'm assuming you are thinking to check diff of various files to see if somersetting was compromised? Is there a way to automate this (Checking the integrity of files not backups). I've read about Tripwire, but never used it. I don't know if that is worth looking into.

---

### Post by CharlesA on 2015-07-27
> **dan138 said:**
> I really and truly appreciate your comments. Sincerely. I generally agree with you. Nothing on this server is critical -- it's my learning server.

a) sftp is painfully slow. How do you feel about ftp over TLS?

What do you mean sftp is painfully slow? I'd rather use it than a random ftp server, even with TLS enabled. sftp should work out of the box since it is included in openssh-server.

> b) So much sh*t does have *php web-facing!  There are about 70 million Wordpress sites all with wp-admin facing the public web. As much as I hate this stuff I want to learn how to deal with it as best possible. 

The way everyone else does it is not necessarily the proper way. I don't use wordpress, but I'll apply the same logic I do with SSH - where I whitelist my main IP and the IP of my VPN and block everything else. The same could be done for wordpress via the web server's access controls.

> c) What i'd like to know is where the screwup happend: Was it me? Is the PhpMyAdmin team incompetent? Does Ubuntu check packages out for these kind of problems or do they just make sure all the dependencies are satisfied? 

The default settings for phpmyadmin is to be accessibly to all since it is a web frontend. It is up to the user to lock it down. This might help a bit:
[https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)

> Concerning versionded backups for security, can you elaborate on this a little? I'm assuming you are thinking to check diff of various files to see if somersetting was compromised? Is there a way to automate this (Checking the integrity of files not backups). I've read about Tripwire, but never used it. I don't know if that is worth looking into.

Mostly so you can revert to a known good backup in the event your server gets owned. If you aren't running versioned backups, you are pretty much screwed if your server gets owned since you cannot restore from a known good backup set.

FTIW, I have been running CSF for a while as an IDS, but it doesn't do eveything.

---

### Post by SeijiSensei on 2015-07-28
> **dan138 said:**
> There are about 70 million Wordpress sites all with wp-admin facing the public web.
If you go to my site (marked "Blog" in my signature) and try to access /wp-admin, you'll get a login page.  Now I suppose there are some bozos who don't use a password to limit access to the admin console on WordPress, but the installer makes that difficult. 

Many WP exploits take advantage of the fact that the web server needs to write into some directories below the DocumentRoot during updates.  I handle that by granting the server write permissions, updating the software, and turning off those permissions when I'm done.  The only directory WP requires continuous write access to is wp-content/uploads/2015 and its subdirectories where objects like graphics are stored.  All the other content is stored in the back-end database.

---

### Post by TheFu on 2015-07-28
> **dan138 said:**
> I really and truly appreciate your comments. Sincerely. I generally agree with you. Nothing on this server is critical -- it's my learning server.

a) sftp is painfully slow. How do you feel about ftp over TLS?

b) So much sh*t does have *php web-facing!  There are about 70 million Wordpress sites all with wp-admin facing the public web. As much as I hate this stuff I want to learn how to deal with it as best possible. 

c) What i'd like to know is where the screwup happend: Was it me? Is the PhpMyAdmin team incompetent? Does Ubuntu check packages out for these kind of problems or do they just make sure all the dependencies are satisfied? 

Concerning versionded backups for security, can you elaborate on this a little? I'm assuming you are thinking to check diff of various files to see if somersetting was compromised? Is there a way to automate this (Checking the integrity of files not backups). I've read about Tripwire, but never used it. I don't know if that is worth looking into.

I don't have all the answers.  I've been hacked a few times, but none of my servers  since 2002 (as far as I know). Until you are hacked and need to figure out the root cause, it is hard to explain.  You will learn a bunch going through this exercise.  I was hacked last fall when at a hacker conference running a KOTH contest. While not expected, I was prepared for this with a clean system BEFORE attending.  It was on a completely patched, freshly installed, Ubuntu system.  Just sayin'.

a) sftp can use different encryption. You should select the encryption level required that makes you comfortable. No, I would not trust ftps.  IMHO, ftps is broken. Nothing is free. If sftp encryption is slow, get better CPUs. If that isn't it, get a better network.

b) I didn't say to stop running php. I said to not make it clear that php was being used by having *.php shown. Use a reverse proxy to block undesired attempts and strange requests.

c) Incompetence generally starts by looking in the mirror. ;) We all are incompetent in different needed skills. Linux and Unix are extremely flexible. That is a core value. With that flexibility, comes responsibility.  The admin is responsible to secure his system.  If this isn't something you are comfortable doing, perhaps paying a service to handle it would be desired?

d) versioned backups are a basic thing for any computer system. It has been discussed at length in these forums.

e) I travel too.  I only use ssh with key-based authentication to access my systems.** NEVER PASSWORDS!!!**

---

### Post by iulian X on 2015-09-10
> **dan138 said:**
> I have an Ubuntu 14.04 installed on a server.  I did a standard apt-get install of PhpMyAdmin a while back.  I was digging through the Appache logs today and noticed someone was requesting the page  domain.com/phpmyadmin/js/messages.php  
This is viable on the web.  Did I make a mistake? Is there a problem with the default install of PhpMyAdmin? 
Other than this oddity there is no evidence of someone hacking into my server.

Unistall the PhpMyAdmin and use a alternative like Adminer  [https://www.adminer.org/](https://www.adminer.org/)

---

### Post by TheFu on 2015-09-10
> **iulian X said:**
> Unistall the PhpMyAdmin and use a alternative like Adminer  [https://www.adminer.org/](https://www.adminer.org/)

Or just do it with CLI access through ssh.  When only ssh access is used, that is 1 port to be secured.  Every other open port is a liability.

Trading 1 attack vector for another is a zero-sum game. 

There are ways to have these GUIs/webapps on the machine and to secure them from outside use by using an ssh-tunnel and specific firewall rules, but when that becomes easy, you won't need the webgui anymore.

It is the **principle if least privilege** required to do the job.
[https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)  If you have that at the network layer, then at the DBMS layer, then for the webapp layer and for shell access layers and for ... any other layer, THAT is how you secure a system.

---

### Post by QIII on 2015-09-10
If a GUI is desireable, you can use MySQL Workbench over SSH to administer MySQL.

That keeps all the "working parts" on your local machine and you can remove phpmyadmin from your server.

---

### Post by CharlesA on 2015-09-10
> **TheFu said:**
> Or just do it with CLI access through ssh.  When only ssh access is used, that is 1 port to be secured.  Every other open port is a liability.

Trading 1 attack vector for another is a zero-sum game. 

There are ways to have these GUIs/webapps on the machine and to secure them from outside use by using an ssh-tunnel and specific firewall rules, but when that becomes easy, you won't need the webgui anymore.

It is the **principle if least privilege** required to do the job.
[https://en.wikipedia.org/wiki/Principle_of_least_privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)  If you have that at the network layer, then at the DBMS layer, then for the webapp layer and for shell access layers and for ... any other layer, THAT is how you secure a system.

Indeed. If I needed to have phpmyadmin installed, I'd lock it down so I can only connect to it from a VPN or via SSH. Better than leaving it open to the entire internet, especially when there is no way to do two factor auth with it. You can lock it down via Apache access rules, though, so it isn't accessible to everyone.

But anyway, I prefer SSHing in and running any queries or whatever from the mysql client itself. Less work/less mess for me to deal with.

---

