---
title: "Amazon Web Services Beginner Help"
date: 2012-06-26
forum: Server Platforms
---

### Post by jonesyp on 2012-06-26
Hi,

I wonder if I can ask for some help with Amazon Web Services?

I have signed up for a Amazon Web Services Account, and want to use the Free Usage Tier.

I have created an instance using the EC2 'Ubuntu Server 12.04 LTS
Ubuntu Server 12.04 LTS with support available from Canonical'

I can connect to my new instance with the 'Connect from your browser using the Java SSH Client (Java Required)'

I get to 'ec2-107-22-130-97.compute-1.amazonaws.com login:   '

and login with the username Ubuntu as advised. I then get:

ec2-107-22-130-97.compute-1.amazonaws.com login: ubuntu  
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-virtual i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Jun 26 20:28:25 UTC 2012

  System load:  0.09             Processes:           58
  Usage of /:   9.7% of 7.97GB   Users logged in:     0
  Memory usage: 12%              IP address for eth0: 10.28.208.59
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

Get cloud support with Ubuntu Advantage Cloud Guest
  [http://www.ubuntu.com/business/services/cloud](http://www.ubuntu.com/business/services/cloud)
ubuntu@ip-10-28-208-59:~$ 


I know a small amount of PHP and MySQL, and also know the command line in Ubuntu and am fine with APT so I suppose I want to know what to do next?  

I found this:

[http://www.robotmedia.net/2011/04/how-to-create-an-amazon-ec2-instance-with-apache-php-and-mysql-lamp/](http://www.robotmedia.net/2011/04/how-to-create-an-amazon-ec2-instance-with-apache-php-and-mysql-lamp/)

Would this be a good place to start?  

I know I get 750 hours of usage (running the server), but will I be charged for installing software

Many thanks

Peter Jones

---

### Post by jonesyp on 2012-07-31
Any idea on this one please?  Help would be much appreciated

---

### Post by xkaliburx on 2012-07-31
I guess the 1st question is what do you want to do, create a LAMP server I would guess?

Well I currently have more than 100 EC2 instances, so if you can connect your partly there.  1st thing you really could do is start a new one, and rather than the blank ones, you can click the public AMI's and search for LAMP as there are plenty out there.

IF you wish to use yours, simply SSH in as you said, I would use a local connection and not their java one as it's much slower, but once your in, you could just apt-get install apache2, mysql-server, php5 and 'y' to the dependencies.  You will be prompted for a mysql root PW.

Start each process.  Confirm there running.   Then you will need to goto your EC2 console, security group, and allow for port 80 HTTP to 0.0.0.0 which opens up HTTP to the world (unless you want it just for you).

Next, are you administrating Mysql local or via some remote tool, if so, open 3306 (I think) to your iP only.

That alone should be enough to get you started.  You should be able to hit your ec2.... via browser and you should get your apache2 page.  

Note you are NOT charged for installing software, incoming data, (so FTP'ing files, etc.)  cost nothing.  It's the people that hit the site (outgoing traffic) is what you are charged for, but it's very minimal and the 1st gig is actually free ([http://aws.amazon.com/s3/pricing/](http://aws.amazon.com/s3/pricing/))

Once that above stuff is done, feel free to post back any more detailed questions, or if you have any problems, feel free to ask.  Just make sure you hold tight to your private key as you will need that to connect via ssh wherever you go.

---

### Post by jonesyp on 2012-08-05
Hi,

Very many thanks for such detailed instructions.  I will give these a go and feedback on how I got on.

Thanks again

---

