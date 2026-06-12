---
title: "Zenoss and SUDO"
date: 2006-10-31
forum: Server Platforms
---

### Post by Beernut on 2006-10-31
Hi All

Wondering if anyone has been able to run Zenoss on Ubuntu?  I have it partially running using the the howto at the following site.  
[http://www.howtoforge.com/zenoss_network_monitor_ubuntu](http://www.howtoforge.com/zenoss_network_monitor_ubuntu) 

I thought I followed the directions exactly but I am getting the following error.

```
zenoss is not allowed to run sudo on zenoss.  This incident will be reported.
```

I have to be doing something wrong in steps 12 or 13 which I think is stopping zenping, zensyslog, and zentrap from starting.  Anyone have a similar experience?  ](*,)

---

### Post by Beernut on 2006-11-05
I am at a loss.  Does it matter where in the bash script these lines are added?

```
nano  .bashrc
  (add these lines)
 export ZENHOME=/usr/local/zenoss
 export PYTHONPATH=$ZENHOME/lib/python
 export PATH=$ZENHOME/bin:$PATH
```

Also does it matter where these lines are added in Sudo editor?

```
 zenoss monitor = NOPASSWD: /usr/local/zenoss/bin/*,/bin/kill
Defaults env_keep += "PYTHONPATH ZENHOME"
```

---

### Post by SuperMike on 2006-12-04
Yeah, I tried to install Zenoss and it failed for me too. I bailed on it. I also had the same trouble with Hypernic. Some people suggested Nagios, but man the interface sucks and has very little visual selling power with upper management.

If I could just get Zenoss installed on Ubuntu, and point it at some of my SLES9 servers in the server room, boy, that would really turn some heads. It's an attractive product.

Meanwhile, I think it would be a good thing to throw a portal in front of a product like this and let the dashboard gadgets scrape the Zenoss content. That way, you can create users, groups, roles, and assign gadgets only to those groups by roles. Plus, you could then screenscrape other items from other web management products in your server room (like your big honking UPS if you have one, or perhaps your building generator) and hook them into gadgets too.

---

### Post by Gulan on 2006-12-06
Hi, I'm also trying this, altough I'm a newbee to Linux :)

So in step 16 in the guide I'm completley lost.
"apt-get svn-buildpackage" it says, but it seems like the file doesn't exist, getting this error:

"Package svn-buildpackage is not available, but is refered to by another package ..... n so on .... Has no installation candidate"
:confused: 
plz help me get further

thx n regards
Kennet

---

### Post by snowman386 on 2006-12-06
I too was having a similar problem. In step 14 where it says add this line: zenoss monitor = NOPASSWD: /usr/local/zenoss/bin/*,/bin/kill

replace "monitor" with the hostname of your computer. After doing this, all processes launch correctly.

---

### Post by snowman386 on 2006-12-06
> **Gulan said:**
> Hi, I'm also trying this, altough I'm a newbee to Linux :)

So in step 16 in the guide I'm completley lost.
"apt-get svn-buildpackage" it says, but it seems like the file doesn't exist, getting this error:

"Package svn-buildpackage is not available, but is refered to by another package ..... n so on .... Has no installation candidate"
:confused: 
plz help me get further

thx n regards
Kennet

Insead of doing this, just ftp and untar the latest version from the zenoss website. run the install.sh file after you untar the package.

---

### Post by Beernut on 2006-12-09
Well I did finally get version 0.23.0 and version 1.0.0 running.  The howto is pretty bad if you ask me, I am going to write one with notes from my new installation that I'll probably be doing tonight. Once I get the howto finished I'll be sure to post it.  I lost the latest install because I had a hard drive go bad on me.  It was running great while it was up I was able to scan my network for devices, generate graphs, monitor disks it was pretty cool.

---

### Post by Beernut on 2006-12-13
> **snowman386 said:**
> I too was having a similar problem. In step 14 where it says add this line: zenoss monitor = NOPASSWD: /usr/local/zenoss/bin/*,/bin/kill

replace "monitor" with the hostname of your computer. After doing this, all processes launch correctly.

Well step 14 worked fine with version 1.0.0 but now I just rebuilt the server installed version 1.0.1 and it doesn't work.  I even tried replacing "monitor" with the hostname no luck.  ](*,)

---

### Post by snowman386 on 2006-12-13
> **Beernut said:**
> Well step 14 worked fine with version 1.0.0 but now I just rebuilt the server installed version 1.0.1 and it doesn't work.  I even tried replacing "monitor" with the hostname no luck.  ](*,)

What is the error you are receiving?

---

### Post by Beernut on 2006-12-13
Not getting any error just when the daemons start it asks for a password.  I added: ```
zenoss ALL=ALL 
```  and everything starts up without a password of course but I don't really want to leave it this way for security even though I have strong passwords.

---

### Post by golfing22 on 2006-12-16
Zenoss seemed to install fine for me, but when I browse to "http://localhost:8080/zport/dmd" I recieve the error:

> Site error

An error was encountered while publishing this resource. The requested resource does not exist.

I've tried everything I can think of and it still doesn't work.  I'm really excited to get Zenoss to work but the tutorial on howtoforge (which is the same one on their homepage), is just horrible.  It would be really cool if there was an apt-get package for zenoss too.

---

