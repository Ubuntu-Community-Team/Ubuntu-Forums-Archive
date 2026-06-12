---
title: "Snort install 2.8.5.2"
date: 2010-12-11
forum: Security
---

### Post by craneman914 on 2010-12-11
Hi,   does anyone know of a good tutorial on how to set up and configure snort 2.8.5.2 on a ubuntu 10.10 system. I have been trying to set up snort and have run into alot of problems setting up the config file and the rules. It works in sniff and packet log mode but i cannot seem to set up IDS mode correctly. There is alot of different info on the net but not much help. There seems to be alot of work involved in setting this up which i do not mind provided i can find the proper documentation to configure the set up. Thank you!

---

### Post by bodhi.zazen on 2010-12-11
This sticky at the top of the forum.

Otherwise, you will have to be more specific with your questions (or read the snort documentation) as I have no idea where you got stuck and what you do or do not understand about networking, NIDS, and snort configuration, let alone your network arch and services you are running.

---

### Post by craneman914 on 2010-12-11
I appreciate your response. I am relatively new to Linux and also to snort. My purpose for setting up snort is simply to gain knowledge of the system. I am not operating a server and my knowledge in networking and protocol is basic. I am trying set up snort on my wireless laptop and i want to be able to run all three modes of snort to see and understand how and why it works. I have read your sticky and many other documents on the subject. Snort 2.9.0.2 is the latest version and i want to know if your install and configure guide applies to the latest version or an earlier version? Does each version have a different way to configure the snort.conf file? That seems to be the hardest part of it. And lastly how do you integrate the rule package into snort so that it sees that they are there. I wonder why the program does not come with the rules built into it already. I want to learn so whatever i have to do i will do.  Thank you.

---

### Post by bodhi.zazen on 2010-12-11
> **craneman914 said:**
> I appreciate your response. I am relatively new to Linux and also to snort. My purpose for setting up snort is simply to gain knowledge of the system. I am not operating a server and my knowledge in networking and protocol is basic. I am trying set up snort on my wireless laptop and i want to be able to run all three modes of snort to see and understand how and why it works. I have read your sticky and many other documents on the subject. Snort 2.9.0.2 is the latest version and i want to know if your install and configure guide applies to the latest version or an earlier version? Does each version have a different way to configure the snort.conf file? That seems to be the hardest part of it. And lastly how do you integrate the rule package into snort so that it sees that they are there. I wonder why the program does not come with the rules built into it already. I want to learn so whatever i have to do i will do.  Thank you.

The guide should work with most any version of snort.

You might want to start by learning the basics of tcp/ip , udp, imcp and you might want to start with wireshark (to look at raw  packets).

---

### Post by craneman914 on 2010-12-12
Ok, thank you. I have wireshark set up on this system already and i have been playing around with it for a while. I have also read alot about TCP/IP as well as UDP and the OSI model. I will continue to study those subjects as well as networking as a whole. I understand that the learning curve is high and requires alot of study and reasearch. I have alot of time on my hands so it is not a problem. I will go through your setup instructions again and maybe get it right this time. Thank you for your time.

---

### Post by craneman914 on 2010-12-12
hello, I have snort up and running. I just have on one question, after following your tutorial and setting up installing and configuring snort i ran the command to download base so i get configure it as per your instructions and could not download and install for some reason. Here is the output from running the command in the terminal:

 sudo wget [http://sourceforge.net/projects/secureideas/files/BASE/base-1.4.5/base-1.4.5.tar.gz/download](http://sourceforge.net/projects/secureideas/files/BASE/base-1.4.5/base-1.4.5.tar.gz/download)
--2010-12-12 18:26:47--  [http://sourceforge.net/projects/secureideas/files/BASE/base-1.4.5/base-1.4.5.tar.gz/download](http://sourceforge.net/projects/secureideas/files/BASE/base-1.4.5/base-1.4.5.tar.gz/download)
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz?r=&ts=1292196408&use_mirror=surfnet](http://downloads.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz?r=&ts=1292196408&use_mirror=surfnet) [following]
--2010-12-12 18:26:48--  [http://downloads.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz?r=&ts=1292196408&use_mirror=surfnet](http://downloads.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz?r=&ts=1292196408&use_mirror=surfnet)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://surfnet.dl.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz](http://surfnet.dl.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz) [following]
--2010-12-12 18:26:48--  [http://surfnet.dl.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz](http://surfnet.dl.sourceforge.net/project/secureideas/BASE/base-1.4.5/base-1.4.5.tar.gz)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 958567 (936K) [application/x-gzip]
Saving to: `download.3'

100%[======================================>] 958,567      389K/s   in 2.4s    

2010-12-12 18:26:51 (389 KB/s) - `download.3' saved [958567/958567]

kevins@ubuntu:/var/www$ sudo tar xvf base-1.4.5.tar.gz
tar: base-1.4.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
kevins@ubuntu:/var/www$ sudo rm base-1.4.5.tar.gz
rm: cannot remove `base-1.4.5.tar.gz': No such file or directory
kevins@ubuntu:/var/www$ sudo mv base-1.4.5 base
mv: cannot stat `base-1.4.5': No such file or directory
kevins@ubuntu:/var/www$ sudo chown -R www-data.www-data base

When i tried to go to the base website i got a 404 page. Is base still an available app?

---

### Post by bodhi.zazen on 2010-12-12
base is available here :

[http://sourceforge.net/projects/secureideas/files/](http://sourceforge.net/projects/secureideas/files/)

---

### Post by uRock on 2010-12-12
[URL="http://www.google.com/url?sa=t&source=web&cd=2&ved=0CBoQFjAB&url=http%3A%2F%2Fwww.snort.org%2Fassets%2F125%2Fsnort_manual-2_8_5_1.pdf&rct=j&q=snort%20manual-2_8_5_2.pdf&ei=MGIFTcDpNIH4sAPm3_jJDQ&usg=AFQjCNGEyTx8fTHdluGqKukg1AOhznzCjw&cad=rja"]Snort Manual.PDF
[/URL]

---

### Post by craneman914 on 2010-12-12
Ok i have base installed. I went to address that it told me to during the install to do a manual config and i recieved this message:

**Error (p)connecting to DB : **snort@
Check the DB connection variables in *base_conf.php*                
               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
                             [COLOR=#ff0000]**Database ERROR:**Database connection failed[/COLOR]

If you could point me in the right direction as to where i can correct these errors i would most appreciate it. I follow all of your setup instructions to the letter and tested snort and i recieved the correct output:

+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.5.2 (Build 121)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 8.02 2010-03-19

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.11  <Build 17>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 2>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 8>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 12>
           Preprocessor Object: SF_Dynamic_Example_Preprocessor  Version 1.0  <Build 1>
           Preprocessor Object: SF_DCERPC  Version 1.1  <Build 5>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 2>

Snort successfully loaded all rules and checked all rule chains!
Snort exiting



Thank you for all of your help on this matter. I will read the snort pdf doc as well. I am a bit stuck with the error i recieved trying to connect to base however. Maybe i need to change some things in the snort.conf file???

---

### Post by bodhi.zazen on 2010-12-12
> **craneman914 said:**
> Ok i have base installed. I went to address that it told me to during the install to do a manual config and i recieved this message:

**Error (p)connecting to DB : **snort@
Check the DB connection variables in *base_conf.php*                
               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
                             [COLOR=#ff0000]**Database ERROR:**Database connection failed[/COLOR]

If you could point me in the right direction as to where i can correct these errors i would most appreciate it. I follow all of your setup instructions to the letter and tested snort and i recieved the correct output:

+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.5.2 (Build 121)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 8.02 2010-03-19

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.11  <Build 17>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 2>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 8>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 12>
           Preprocessor Object: SF_Dynamic_Example_Preprocessor  Version 1.0  <Build 1>
           Preprocessor Object: SF_DCERPC  Version 1.1  <Build 5>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 2>

Snort successfully loaded all rules and checked all rule chains!
Snort exiting



Thank you for all of your help on this matter. I will read the snort pdf doc as well. I am a bit stuck with the error i recieved trying to connect to base however. Maybe i need to change some things in the snort.conf file???

You need to install and configure a database (mysql / postgresql) and then configure base to use it.

---

