---
title: "Webmin and Squid"
date: 2009-07-21
forum: Server Platforms
---

### Post by expatCM on 2009-07-21
I am just setting up my server again and seem to have messed up Squid.  

I am using Webmin and see that the Webmin page refers to Webmin 2.7.  I have two sets of log files, for Squid and Squid3.  I get the general idea that I may have been putting settings through using Webmin but the active version is Squid3 and the settings are taking effect on Squid 2.7

Why I think I have messed up is that if I change the settings in Firefox to use the manual proxy configuration then access is denied.  If I use no proxy or automatically detect then Firefox works.  I guess this may suggest that the ACL is set in the Squid 2.7 configuration but it is Squid 3 that is in use (and I have not changed the settings there).

So could someone please tell me how to test whether or not Squid is working and what I should do about having two versions of Squid on the server …

---

### Post by NewbieNik on 2009-07-21
First off, you will probably only have the one version of Squid and that'll be Squid3.
Webmin by default is set to use the conf and lof files in the /etc/squid directory.
Change the module config for webmin squid to point to the relevant files in Squdi3 (It usually is just a case of changing files and folders list as squid to squid3), but double check the setting against the folders.
Easiet test is to move the Deny all directive to the top (Although this will usually stop your webmin access so ensure you know how to undo your change by bash command)

---

### Post by expatCM on 2009-07-21
There are two separate log files and each has different activity.  There are also two separate items which may be started and stopped through Webmin.

Not sure how to proceed since strange things are happening ....   generally there are errors where websites do not load.  For example [http://www.google.com/news](http://www.google.com/news) will not load.  An error appears saying the URL is malformed ... "/news" is not correct, the address should start "http" or similar ... This may be the ISP since there are general problems but it may be something I have got very wrong in setting things up ....

I also find that "problems" are restricted only to browsing.  Skype and email both work, browser activity does not .... But what I simply cannot figure is that if I select No proxy / direct connection in firefox there are still problems .......

---

### Post by expatCM on 2009-07-21
I have just been exploring and found two installs of Squid.  One, 2.7 and the other 3.0.  I uninstalled both and then put the 2.7 back.   As if by magic the problems have all disappeared.

Only one challenge now remains.  Since it is best to run the latest release of Squid, how can I upgrade what is there rather than end up with a second install?

---

### Post by jaimerosario on 2012-04-20
Install all Squid3:

> 
sudo apt-get install squid3^


Edit /etc/webmin/squid/config

Make the following changes:

> 
squidclient=squidclient
cache_dir=/var/spool/squid3
log_dir=/var/log/squid3
pid_file=/var/run/squid3.pid
squid_path=squid3
squid_conf=/etc/squid3/squid.conf
cachemgr_path=/usr/lib/cgi-bin/cachemgr3.cgi
squid_restart=squid3 -k reconfigure
squid_start=service squid3 start
squid_stop=service squid3 stop


And then, check the Squid module in webmin.

---

