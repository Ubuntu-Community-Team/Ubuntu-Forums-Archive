---
title: "Anybody familiar with Snort installation?"
date: 2008-04-22
forum: Security
---

### Post by blkmax on 2008-04-22
I'm running Kubuntu and not Ubuntu.

I'm trying to get snort up and running and logging in to Mysql without any success. I Keep getting the error in my syslog file

snort[9870]: database: must enter database name in configuration file  .

I verified that my snort.conf file in /etc/snort has the following line

output database: log, mysql, user=snort password=mypassword dbname=snort host=localhost

I can log in to mysql using this user name and password, and as well show the tables for the snort database.

I'm not finding any solution on snort.org. I was hoping someone here has done an install that they could share their experience.


Regards

Marc

---

### Post by Monicker on 2008-04-23
> **blkmax said:**
> I'm running Kubuntu and not Ubuntu.

I'm trying to get snort up and running and logging in to Mysql without any success. I Keep getting the error in my syslog file

snort[9870]: database: must enter database name in configuration file  .

I verified that my snort.conf file in /etc/snort has the following line

output database: log, mysql, user=snort password=mypassword dbname=snort host=localhost

I can log in to mysql using this user name and password, and as well show the tables for the snort database.

I'm not finding any solution on snort.org. I was hoping someone here has done an install that they could share their experience.


Regards

Marc


Did you install the snort or the snort-mysql package?  

Also, did you follow the instructions for creating the mysql table for snort to use?  That information can be found in the /usr/share/doc/snort-mysql directory.

---

### Post by blkmax on 2008-04-23
I installed the snort-Mysql. If you have snort and try to install snort-mysql, it will remove snort.

I installed with the instructions from the snort web-site docs. I will look at the one you mentionned now. I imported the schemas into mysql as well. I can log into mysql using that username and password. I can use the snort database created during the setup process and show the snort database tables.


regards

Marc

---

### Post by Monicker on 2008-04-23
> **blkmax said:**
> I installed the snort-Mysql. If you have snort and try to install snort-mysql, it will remove snort.

I installed with the instructions from the snort web-site docs. I will look at the one you mentionned now. I imported the schemas into mysql as well. I can log into mysql using that username and password. I can use the snort database created during the setup process and show the snort database tables.


regards

Marc


Hmm. Not sure then.  I've never run in that error myself when using snort under Ubuntu or Debian.  You might try manully running snort -v, to enable verbose output.  Maybe something there would give more insight.

---

### Post by blkmax on 2008-04-24
Not sure if this can be the problem but Kubuntu installs snort version 2.7.0 and the schema I imported were from a wrong directory for version 2.8.1..

1) can this cause my problem of "snort[9870]: database: must enter database name in configuration file"

2) how can I remove or change it with the right schema in /usr/share/doc/snort-mysql/ ?

thanks

Marc

---

### Post by Monicker on 2008-04-24
I don't know what differences there might be in the schema betwen those versions, but its possible that is an issue.

I would drop the database,and recreate it using the proper schema.

---

### Post by kutjara on 2008-04-25
> **blkmax said:**
> I'm running Kubuntu and not Ubuntu.

I'm trying to get snort up and running and logging in to Mysql without any success. I Keep getting the error in my syslog file

snort[9870]: database: must enter database name in configuration file  .

I verified that my snort.conf file in /etc/snort has the following line

output database: log, mysql, user=snort password=mypassword dbname=snort host=localhost

I can log in to mysql using this user name and password, and as well show the tables for the snort database.

I'm not finding any solution on snort.org. I was hoping someone here has done an install that they could share their experience.


Regards

Marc

I used this HOWTO to configure snort, mysql, and BASE to construct a nice intrusion detection and logging system on Hardy.

[http://ubuntuforums.org/showthread.php?t=145641](http://ubuntuforums.org/showthread.php?t=145641)

---

### Post by blkmax on 2008-04-28
Wow, this is great. much simpler. I was able to get snort to install and updated my oinkmaster.conf file with the proper input with my oinkcode and version 2.7 of the rules gz.

I get the following error when running oinkmaster -o /tmp

[http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.7.tar.gz](http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.7.tar.gz)           => `/var/run/oinkmaster/oinkmaster.Tl459GEYxy/url.PDph9PCaZ7/snortrules.tar.gz'
Resolving [www.snort.org](www.snort.org)... 68.177.102.20
Connecting to [www.snort.org|68.177.102.20|:80](www.snort.org|68.177.102.20|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
16:07:12 ERROR 403: Forbidden.


Oink, oink. Exiting...

I'm running as root. Not sure if there is a username and password that needs to be set in some file for this?

Marc

---

### Post by kutjara on 2008-04-28
> **blkmax said:**
> Wow, this is great. much simpler. I was able to get snort to install and updated my oinkmaster.conf file with the proper input with my oinkcode and version 2.7 of the rules gz.

I get the following error when running oinkmaster -o /tmp

[http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.7.tar.gz](http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.7.tar.gz)           => `/var/run/oinkmaster/oinkmaster.Tl459GEYxy/url.PDph9PCaZ7/snortrules.tar.gz'
Resolving [www.snort.org](www.snort.org)... 68.177.102.20
Connecting to [www.snort.org|68.177.102.20|:80](www.snort.org|68.177.102.20|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
16:07:12 ERROR 403: Forbidden.


Oink, oink. Exiting...

I'm running as root. Not sure if there is a username and password that needs to be set in some file for this?

Marc

You have to set a password in snort and mysql, so that snort can login to the mysql db and record data (the details are in the HOWTO, but are a little vague until you realize what he's saying).

I had a problem getting info from BASE, but then realized that was because I'd disabled Apache a few weeks before. DOH!

---

### Post by blkmax on 2008-05-01
The issue was that you can only download the new rules from snort once every 15 minutes. I ran the command that downloads and tests it but does not save it. I tried to download it and update the actual rules before this 15 minute mark. 

I tried the next morning and all was well.

Simple rules when not known can cause a lot of grief.


Regards

Marc

---

### Post by kutjara on 2008-05-01
> **blkmax said:**
> The issue was that you can only download the new rules from snort once every 15 minutes. I ran the command that downloads and tests it but does not save it. I tried to download it and update the actual rules before this 15 minute mark. 

I tried the next morning and all was well.

Simple rules when not known can cause a lot of grief.


Regards

Marc

That is very useful to know. I had no idea about the 15 minute limit. Thinking about it, it explains a few bits of odd behavior I noticed when I was setting Snort up.

---

### Post by strada on 2009-03-24
Just a note on the first problem of blkmax ("database: must enter database name in configuration file"):

I had the same problem and finally it turned out to be caused by a comma in the mysql-password...

Sounds strange I know, but a comma in the password seems to be interpreted as separater in the config-file hiding the database-name:

output [...]: log, mysql, user=snort_usr password=some,what dbname=snort_db

---

