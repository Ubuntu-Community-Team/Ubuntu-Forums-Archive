---
title: "snort , base, ubuntu 14.04 base.iphdr' doesn't exist"
date: 2015-01-09
forum: Security
---

### Post by mike281 on 2015-01-09
Hey,

I'm not sure if it's a software conflict, or just something with my setup. I have snort running, with sudo snort, and it's spitting out what looks like packets travelling from ip's  to destinations. I need to fix the sudo snort part though later, so I can just run snort. 

I also installed base ( 1.3.9 and 1.4.5 ) however both give the same error when I finish running the base setup.

 Basic Analysis and Security Engine (BASE)
The underlying database base@localhost appears to be incomplete/invalid
Database ERROR:Table 'base.iphdr' doesn't exist
It might be an older version. Only alert databases created by Snort 1.7-beta0 or later are supported


I already tried running the mysql scripts in the sql directory of the base install folder. I also tried deleting the sql table , re-created it, ran the scripts before creating the base ag in the base setup, and ran the scripts after. however I get the same error message. 

I also broke snort by accident, than down the road I fixed snort by accident with an apt-get -f install, lolll . 

Thanks,

---

### Post by angryfirelord on 2015-01-11
When you run the create_mysql script, how are you connecting to the mysql database? I'm not as familiar with mysql terminology, but if you have the table "iphdr" created and it's returning the error, then the "base" schema doesn't exist or the table is under a different database which snort isn't connecting to. As a note:

[https://www.howtoforge.com/intrusion_detection_base_snort_p3]("https://www.howtoforge.com/intrusion_detection_base_snort_p3")
> Whichever way you create the database, make sure the 'user', 'password' and 'dbame' are the same as the one you set in the /etc/snort/snort.conf file!
Check that the user login and database name are all the same for the mysql instance.

---

### Post by mike281 on 2015-01-12
Actually. I can't seem to find the create_mysql script on my computer. It's weird though because snort runs from the terminal. However not having the create_mysql script is probably my problem. I think I'm probably going to do a fresh install of Ubuntu and try the setup again, to rule out software conflicts.  Thank you for the help. I agree with you, and yes the login and database name are all the same for the mysql instance. I thought that base and snort would create the tables itself since the account I gave to base has permission to create,and modify tables, however I guess I was wrong. 

Thank you again.

---

### Post by angryfirelord on 2015-01-13
The scripts are on github. They may or may not be included in the package.

[https://github.com/eldondev/Snort/blob/master/schemas/create_mysql]("https://github.com/eldondev/Snort/blob/master/schemas/create_mysql")

---

