---
title: "Just introducing and explaining why i'm here."
date: 2013-03-05
forum: Server Platforms
---

### Post by Lieuwke on 2013-03-05
Hi everyone, 
my name is Martin and I’m planning on my first server that is running Linux. 
I've played around a bit with Ubuntu in the past and also set up a 3cx box at work as a PABX system. Until now i am running a few websites on my Windows Small Business 2012 server. This box also handles my mail with MS Exchange en i use it as a home file server and FTP server. It's not real server hardware, but an Intel Q6600 machine on an Asus P5Q mainboard with 8Gb's of RAM and a bunch of disks connected to it. I actually was a bit disappointed by the performance of this setup, so i installed Ubuntu on an old Core2 6300 machine with 1Gb of RAM i had. This was just for testing how to set up things. But now I’ve come to notice that in everything the test setup outruns the windows machine. WOW! that's nice. How would this run on the better hardware was my first thought. I'm seriously considering to switch to Ubuntu Server. I also tried webmin which made some tasks very simple, but I’m not really afraid of using the console/SSH when necessary.
 
So basically this is what I’m trying to achieve:

[LIST=1]
[*]Webserver to put my websites on. (mainly Joomla sites)
[*]MySQL server for databases (again mainly for the Joomla sites)
[*]Samba fileserver for my windows machines on home network
[*]FTP server
[*]Mailserver wich handles different domains and can support my clients through IMAP (postfix/dovecot?)
[*]SSH
[*]Webmin for easy management.
[/LIST]
 
I Actually got the above working on my test rig for a test domain i own, but i’ve got some questions.

[LIST=1]
[*]How good/bad is Webmin. I come accross some posts on the internet claiming webmin wasn’t any good. I like what it does, and when it’s safe to use i’ll keep it.
[*]Om my live server i’m currently using 3 1TB disks in RAID5,
but is sucks in both performancy aswel as reliability. Also, it’s no replacement for back-ups
[/LIST]
So: What’s a good back-up and recovery strategy for this kind of system. A daily overnight back-up would be just fine for me. Would ben ice to receive a mail notification every day with the result of the back-up.
  I

---

