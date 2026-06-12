---
title: "Apt-get Anything will not work"
date: 2009-10-24
forum: Server Platforms
---

### Post by harrisonk on 2009-10-24
[SIZE=4]Hello

My problem is when I type sudo apt-get install xxxx or sudo apt-get update OR sudo apt-get upgrade, It goes through but Ubuntu will not download the files from the repositories.

I am using Ubuntu 9.04 server edition on a Intel Celeron 699MHz processor with (I'm not exactly sure) 256-512 MB of memory and a 20 GB hard disk.

Another thing is I tried sticking two network cards in my computer so I could connect my desktop to the Internet. The problem started after that.

Harrison
12, Hemmingford Quebec, Ubuntu 9.04 user (and loving it!) 
[/SIZE]

---

### Post by Vegan on 2009-10-24
Better is to get a Linksys box, and use get rid of the 2 cards. a PC Linux machine is not a suitable replacement.

---

### Post by harrisonk on 2009-10-24
I have removed the card I installed and I have a computer else where to reply but my main problem is I can't get new software for my home server from the Ubuntu repositories.

Harrison

---

### Post by harrisonk on 2009-11-04
[SIZE=4]I think I will install ubuntu 9.10 server and see if that will fix my problems.

I will not mark this as solved right now because if someone else has a similar problem they might get an answer here.
[/SIZE]

---

### Post by BQAggie2006 on 2009-11-04
> **harrisonk said:**
> [SIZE=4]I think I will install ubuntu 9.10 LTS server and see if that will fix my problems.
[/SIZE]


9.10 is not an LTS release. The latest LTS release is 8.04.3.

---

### Post by windependence on 2009-11-04
> **Vegan said:**
> Better is to get a Linksys box, and use get rid of the 2 cards. a PC Linux machine is not a suitable replacement.

BS. A Linux or BSD firewall can be much more secure than a simple SOHO router.

Your problem with apt is likely a dns problem. I'll post a possible solution in a few minutes.

-Tim

---

### Post by harrisonk on 2009-11-05
> **BQAggie2006 said:**
> 9.10 is not an LTS release. The latest LTS release is 8.04.3.

[SIZE=4]I thought that ubutnu 9.10 was a LTS but I guess I am wrong.

What exactly is a DNS?
[/SIZE]

---

### Post by rickyjones on 2009-11-05
> **harrisonk said:**
> [SIZE=4]Hello

My problem is when I type sudo apt-get install xxxx or sudo apt-get update OR sudo apt-get upgrade, It goes through but Ubuntu will not download the files from the repositories.

I am using Ubuntu 9.04 server edition on a Intel Celeron 699MHz processor with (I'm not exactly sure) 256-512 MB of memory and a 20 GB hard disk.

Another thing is I tried sticking two network cards in my computer so I could connect my desktop to the Internet. The problem started after that.

Harrison
12, Hemmingford Quebec, Ubuntu 9.04 user (and loving it!) 
[/SIZE]

Are you fully connected to the internet? In the terminal type the following command and please post the results.

```

ping www.google.com

```

This will tell us if you are connected to the internet, can resolve hostnames, and can talk to internet hosts.

Thanks,
Richard

---

### Post by harrisonk on 2009-11-05
[SIZE=4]On my server when I type: ping [www.google.ca](www.google.ca) it says:

ping: unknown host [www.google.ca](www.google.ca)

I have setup a router for my desktop and home server and I think I may have to re configure the default gateway.

Harrisonk
[/SIZE]

---

### Post by harrisonk on 2009-11-06
[SIZE=4]I think I have found the problem, in a file called sources.list where ubuntu gets information on the urls of the repositorys the file was empty.

I will post again if this works.

Harrisonk
[/SIZE]

---

### Post by kpholmes on 2009-11-06
make sure that the ubuntu cd isnt in that list, it was with mine and apt-get wasnt working. kept asking me to put in a cd :lolflag:

took me 2 hours to figure out what was going on

---

### Post by harrisonk on 2009-11-06
[SIZE=4]I tried to type in the sources.list from the perfect ubuntu server on [www.howtoforge.net](www.howtoforge.net) and it didn't work so I will be installing 9.10 and see if that fixes my problem.

Thanks to everyone who took the time to try and fix my problem.

harrisonk
[/SIZE]

---

### Post by harrisonk on 2009-11-10
[SIZE=4]I have found the problem!:D

The file /etc/network/interfaces has a line in it to tell it wheter to configer the network with dhcp or a static IP address.

My problem was that you can't install software on ubuntu sever 9.04 with a static IP set.

Harrisonk
[/SIZE]

---

### Post by mandarin77 on 2009-11-15
My problem is similar.
I have a working setup of 9.04 Server. I upgraded from 8.04 using apt-get dist-upgrade. No problems.
 
Then, i had a few packages that would not auto install with an apt-get upgrade. It would tell me that the packages were held back. I had to apt-get install {specific package} to install those 4 packages.
 
Now, I am trying to apt-get dist-upgrade to go to 9.10, and nothing happens, like it doesn't find the new distro version.
 
Help.
 
 
Off-hand, I might be getting my Desktop and Server setups confused, is there a difference in the apt-get dist-upgrade command for Server?
 
OKAY - UPDATE: I installed Server 9.04 from CD. I installed Desktop 8.04 from CD and apt-get dist-upgraded at least once from command line, one distro upgrade from GUI and now run 9.10 Desktop.
Still no luck with upgrading Server to 9.10 from command line.

Thanks,
mandarin

---

### Post by mandarin77 on 2010-04-27
Okay, after much ado in the apt-get department, I have discovered [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes)
going from 9.04 to 9.10 is not done the usual apt-get dist-upgrade way.
try:
sudo do-release-upgrade
 
and a special note, it says upgrading over ssh is not recommended... which sucks!
I'll give it a go anyway! That is how I am set up!
 
see ya on the flip side!
mandarin

---

### Post by arrrghhh on 2010-04-27
> **harrisonk said:**
> My problem was that you can't install software on ubuntu sever 9.04 with a static IP set.


You CAN use a static IP to update your system and do anything really... but since it's static, you also have to define your DNS servers in the resolv.conf file - otherwise there's no DNS lookup capabilities (DNS is provided via DHCP.  If you're static, you must configure yourself :D)

[quote=mandarin77]and a special note, it says upgrading over ssh is not recommended... which sucks!
I'll give it a go anyway! That is how I am set up![/quote]

Really?  That's how I always update... My server just has a power & network cable attached, not sure how else they expect me to update!!

---

