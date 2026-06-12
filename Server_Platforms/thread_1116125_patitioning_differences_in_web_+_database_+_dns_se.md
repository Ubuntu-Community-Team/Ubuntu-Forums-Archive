---
title: "patitioning differences in web + database + dns servers"
date: 2009-04-04
forum: Server Platforms
---

### Post by bluethundr on 2009-04-04
Hi again,

 With a little experimentation my friend and I came up with a working configuration for partitioning my web servers. Ubuntu forums got us around a gnarly problem.

 Now that web is working, I will be expected to build both a MySQL server and a DNS server. 

 What I would like to do is show you my web server configuration and ask you how you would do things DIFFERENTLY on a database server and a DNS server respectively.

 We are using machines with 250 GB scsi drives.

 Also, any editorial comments / thoughts about how things could possibly be done differently on the web server are welcome as well. All filesystems are XFS (unless there's a compelling reason to switch to another filesystem).

 Without any further ado, here's the config for the first production web machines I have ever built:
```

 /boot 25 mb
swap  (4.1 gb) 4096 mb
/ 15 gb
/var/log 25 gb
/home 50 gb
/var/ftp 25 gb
/usr 25 gb
/var/www 105.9 gb

xfs filesystem
```

---

### Post by gombadi on 2009-04-04
First of all some questions -
1 - How many 250G disks in each server?
2 - How big are the systems - number of web sites/domains etc
3 - What are these systems used for - internal company systems or public sell space to users systems?


First rule of partitioning - Everyone has their own opinion and everyone is right ;)

Disclaimer - I come from the "Why create a whole lot of little separate partitions camp"


Some thoughts on your web server -

/boot - 25M - Seems a bit small. I normally have 100M. Machine I am on now is using 39M under /boot - should clean it out sometime.

/ 15G, /usr 25G - Your choice but why separate them. I have seen systems that end up with a lot of spare disk space but it is always in the "other" partition and not where you want it.

Separate /home, /var/ftp and /var/www - again your choice and again why. What are you wanting to gain from separate partitions?

/var/log 25G - Maybe more reason than above partitions as it can fill up but at what rate will it fill up? 

The correct size often depends on how much headroom you have and how quickly your disks can fill up. If you always plan on keeping 20G of old compressed logs on the disk then you only have 5G of headroom but if you only plan on keeping one month of old logs, maybe 5G then you will have 20G of headroom. If you have a large amount of headroom then it will take a long time to fill up your partition so why not combine them and get your monitoring systems to alert you if it goes over say 66% usage.

Another thing to consider with a lot of small partitions is where are they on the actual disk?
i.e.
/dev/sdb (near the centre of the disk for logs)
/dev/sdf (near the outside for /var/www)

The disk heads will spend a lot of time moving back and forth between partitions - read from sdf, move to sdb, write to a log file, move to sdf, read a web page, back to sdb... etc
Even if it is all in one partition the heads will move but at least make sure the www and log partitions are beside each other. You are using xfs so I guess you want the best performance you can get.




MySQL server

Same sort of comments as above.
If you want performance and have two separate disks then put the database files and the logs on separate disks not just partitions.

DNS server

How many domains will you be hosting?
I have an EeePC 701 with 4G flash drive - That would be large enough to host hundreds of domains. Unless you have thousands of domains you will be using a small fraction of the available disk space.
If that is the case have a separate /boot 100M and put everything in /.
Your monitoring system could then be set to alert if disk usage goes above 5% ;) - plenty of time to action it before the disk fills up.


Just my thoughts - I am sure others have different opinions but I am off to enjoy a sunny Sunday.

---

### Post by koenn on 2009-04-05
> **gombadi said:**
> 
First rule of partitioning - Everyone has their own opinion and everyone is right ;)

Errr ... no, some people do get it wrong :)

Other than that, you have a point.

re the proposed partitioning schemes :
- I doubt you're going to have lots of (real, interactively logged on ...) users on a name server, a rdbms server or a web server, so the separate /home might be a bit silly

- /usr is for applications, and if you do it right, your server is going to do just one thing (either web, database, dns, ...) so you don't really expect uncontrollable growth here. Might as well leave it in /

- you might want /var separately, or /var/log, to separate the volatile stuff, but I often just don't bother.

- it's usually a good idea to separate data from system - it allows you to reinstall the operating system from scratch (or other recovery operations) without touching the data. Whether you do this by moving /var, or by configuring the servers to store/get their data from a custom directory mounted on a separate partition/disk/array/..., is up to you.

 - as gombadi said, separate disks make more sense than just separate partitions, because of performance, and because partitions on the same disk don't help in case of disk failure. For the latter, you probably want RAID or something as well.

---

### Post by bluethundr on 2009-04-05
gombadi.. thanks! good advice. I agree that many parting decisions are valid. But as Koenn points out, some parting decisions are just silly/bad/wrong. Such as the advice I got to put /dev on it's own part. Learned from the bloody nose I earned from that decision. 

And Koenn, thanks again for your special wisdom. I benefit greatly from your tutelage. 

Here, you say:
> 
re the proposed partitioning schemes :
- I doubt you're going to have lots of (real, interactively logged on ...) users on a name server, a rdbms server or a web server, so the separate /home might be a bit silly

Ok. While on the topic of silly.. may I propose a silly scenario? In my particular case.. we will have 20-25 developers from India logging into these machines. Let's say, that we have one nutty/non-professional guy among them who was a bad hiring choice. He will have a directory in /home like the rest.

Let's say, that at some point the guy is off his meds and goes nuts. Starts storing 50 GB of hentai pr0n in his /home directory and 100 GB of Megadeath/Metallica/GG Allin there. 

Right. So I can configure Nagios or somesuch to alert me if he goes over quota. But isn't it a more effective preventative measure in policing this directory against this sort of vandalism to allocate /home it's own part so that no matter how on the ball I may be due to Nagios monitoring I can rest easy that no one will take advantage of having free reign of home? 

As an extreme alternative, is a /home directory even needed on a production web or db or dns machine? Sure, it's nice to give people freedom where appropriate. Having your own .bashrc and .bash_profile is pretty sweet and can make one more productive in their own manner. But there is an argument to be made for uniformity. Perhaps there is a way to force these choices on our hapless development community with default versions of these files?

I'd appreciate a lack of 'comic book guy' snarkiness in any responses/evaluations of the intellectual capacity/potential of someone you've never met! ;-) :guitar:

---

### Post by bluethundr on 2009-04-06
> **gombadi said:**
> First of all some questions -
1 - How many 250G disks in each server?
2 - How big are the systems - number of web sites/domains etc
3 - What are these systems used for - internal company systems or public sell space to users systems?


First rule of partitioning - Everyone has their own opinion and everyone is right ;)

Disclaimer - I come from the "Why create a whole lot of little separate partitions camp"


Some thoughts on your web server -

/boot - 25M - Seems a bit small. I normally have 100M. Machine I am on now is using 39M under /boot - should clean it out sometime.

/ 15G, /usr 25G - Your choice but why separate them. I have seen systems that end up with a lot of spare disk space but it is always in the "other" partition and not where you want it.

Separate /home, /var/ftp and /var/www - again your choice and again why. What are you wanting to gain from separate partitions?

/var/log 25G - Maybe more reason than above partitions as it can fill up but at what rate will it fill up? 

The correct size often depends on how much headroom you have and how quickly your disks can fill up. If you always plan on keeping 20G of old compressed logs on the disk then you only have 5G of headroom but if you only plan on keeping one month of old logs, maybe 5G then you will have 20G of headroom. If you have a large amount of headroom then it will take a long time to fill up your partition so why not combine them and get your monitoring systems to alert you if it goes over say 66% usage.

Another thing to consider with a lot of small partitions is where are they on the actual disk?
i.e.
/dev/sdb (near the centre of the disk for logs)
/dev/sdf (near the outside for /var/www)

The disk heads will spend a lot of time moving back and forth between partitions - read from sdf, move to sdb, write to a log file, move to sdf, read a web page, back to sdb... etc
Even if it is all in one partition the heads will move but at least make sure the www and log partitions are beside each other. You are using xfs so I guess you want the best performance you can get.




MySQL server

Same sort of comments as above.
If you want performance and have two separate disks then put the database files and the logs on separate disks not just partitions.

DNS server

How many domains will you be hosting?
I have an EeePC 701 with 4G flash drive - That would be large enough to host hundreds of domains. Unless you have thousands of domains you will be using a small fraction of the available disk space.
If that is the case have a separate /boot 100M and put everything in /.
Your monitoring system could then be set to alert if disk usage goes above 5% ;) - plenty of time to action it before the disk fills up.


Just my thoughts - I am sure others have different opinions but I am off to enjoy a sunny Sunday.

Gombadi... GREAT advice herein. THANKS!!! and said without 'tude always a bonus! ;-)

To answer some of your questions (running out to work will answer what I can in the time I have)

1) the servers have 1 250 GB scsi drive each.
2) this is not general hosting. will host only the high volume site my company wishes me to build + one foswiki based wiki site for internal use only
3) is answered by number 2.

how was your sunny Sunday?

---

### Post by koenn on 2009-04-06
> **bluethundr said:**
> 
Ok. While on the topic of silly.. may I propose a silly scenario? In my particular case.. we will have 20-25 developers from India logging into these machines. Let's say, that we have one nutty/non-professional guy among them who was a bad hiring choice. He will have a directory in /home like the rest.
If you have a sound rationale for a separate /home, by all means go ahead and do it.
I was going by the info you provided, which mentioned a name server and a db server. you didn't mention 25 devs logging on - and the remark about 'silly' was clearly referring to a situation without interactive users, and /home would be just sitting there empty. 




> **bluethundr said:**
> 
I'd appreciate a lack of 'comic book guy' snarkiness in any responses/evaluations of the intellectual capacity/potential of someone you've never met! ;-) :guitar:
long toes, eh ?

---

### Post by bluethundr on 2009-04-06
> 
long toes, eh ?

Slightly... LOL! But seriously man.. good info and thanks for providing it!

---

