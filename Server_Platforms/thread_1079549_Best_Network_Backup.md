---
title: "Best Network Backup"
date: 2009-02-24
forum: Server Platforms
---

### Post by broken sword on 2009-02-24
I have a slight problem ( nothing new ).  I'm an IT consultant, I work with various networks.  My current client is an all Windows network ( W2k3 and W2k servers ), and this client doesn't have a backup solution in place.  And, as they're not profit they don't have the funds to purchase an "enterprise solution".  I was wondering if anyone could recommend a good program?  I have been researching a few options, but I'm leary of testimonials.  I'm looking for a program that can work with various types of storage media ( tape, SAN ), maybe one that can work on a Windows computer.  Preciate any help that I can get.

---

### Post by wirelessmonkey on 2009-02-24
There are several very good OSS network backup solutions. The most popular of which is AMANDA, which I have not used.
Bacula, which I have used, is probably the hardest to configure, but has tons of great features (native Volume Shadow Copy!!)

I currently us BackupPC, in a mixed linux/windowsxp/Server 2003/8 environment. The pooling and hardlinking features mean I can keep a whole lot of backups, with minimal space constraints. I added some VSS scripts and rsync to our Winboxes, and get high quality backups.

---

### Post by mansonthomas on 2009-02-24
Hi,

  I advise you Bacula ([http://www.bacula.org](http://www.bacula.org)).

  I've considered many backup solution, and it's the one that match entreprise requirement the best imho.

  I've setup bacula to backup some servers over a ssh tunnels on harddrive, but the main purpose of bacula is to backup local servers on tape (it handle tape autochanger).

these article might help : [http://www.bacula.org/articles/articles.en.html](http://www.bacula.org/articles/articles.en.html)


  If you install it on ubuntu, two advice that may save you some time : 


* upon install, it will ask for the password of your mysql bacula user to create it in your mysql database. this password won't be set in bacula-dir.conf file (Catalog section), so you have to do it yourself.
* Replace all 127.0.0.1 in the configuration files found in /etc/bacula/ by the actual ip of your machine (192.168.x.x or 10.X.X.X) .

After this have been set, you'll be able to start bacula and get the status of all components (storage daemon, file daemon ...).

Note, that the password (for between daemon communication) set in the configuration file are some generic one from ubunut (ie the same for all ubuntu user) so you should consider to change it 'after' you get something working and understand how all daemon works together.

 The bacula mailing list is a great place to find help too. 
[http://www.bacula.org/en/?page=maillists](http://www.bacula.org/en/?page=maillists)

 I'll publish on my blog a post on bacula, but I don't have time right now.


Thomas.

---

### Post by freerkkalsbeek on 2009-02-24
In the past I've use boxbackup. Quite a good solution. I believe it's in the Ubuntu repo's.
There's linux server and client package and a windows client as well.

Regards,
Freerk

---

### Post by Slim Odds on 2009-02-24
Bacula must be good with a motto like:> It comes by night and sucks the vital essence from your computers.

---

### Post by mansonthomas on 2009-02-24
Yeah, I love this quote too ;)

---

### Post by broken sword on 2009-02-24
Thank you for all your suggestions.  I'll be testing everything mentioned, hopefully I find one that works for me.

Question, do any of these programs work with SAN devices?

---

### Post by joeinbend on 2009-03-12
Hey guys, just wondering if you have had a chance to test some of these solutions? Maybe a short review of the good/bad/ugly? I'm mostly interested in a solution that will be self-contained on a Ubuntu Server (no GUI), and therefore straightforward to configure and monitor via command-line.

---

### Post by Dublee on 2009-04-22
I recommend Bacula, as well, which I've deployed both in my work and home environments.

At work, I backup three Windows servers and a number of CentOS servers.  I use a dual slot SATA dock and bare (1TB) hard drives instead of tapes.

Indeed, Bacula has a high learning curve, but once it's set up correctly, it'll hum along smoothly.

One can install a Bacula console management on either a Windows or Linux client, allowing one to restore or manage the Bacula system remotely.

As mentioned earlier, VSS for Windows is supported.  I'm still testing out native Exchange backup on W2K3/Exch2k7.  For now, Bacula initiates before and after scripts that invoke NTBACKUP on the client server to back up the System State and Exchange, and then Bacula backs up the .bkf files.

---

