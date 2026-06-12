---
title: "Partitioning: rule of thumb"
date: 2008-10-10
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-10
Hi guys,

I'm in the process of setting up a small-office Ubuntu server that will mainly do the following:

- Act as a dev server for the inhouse web developers (apache, php, mysql).
- Act as a gateway/router, between the LAN and the WAN (ADSL).
- Act as a cache proxy.
- Act as an interim mailserver, as in, it polls the employee POP addresses at the ISP, downloads the mails to the Ubuntu server, and from there gets downloaded by the computers in the LAN.

Now, with some of these things I'll probably need a little help setting it up and optimising it for performance, but in the meantime, here's my question:

How should I partition this box's drive? What's the logical way to approach this? I have a 40GB drive available at the moment, and I thought of maybe partitioning it as follows:

/root: 23GB
/home: 15GB
/swap: 2GB (I've got 1GB of RAM in that box)

I'm making the /root rather big, since I believe squid uses the /root partition for it's cache folder, and would probably be the one process that uses the most disk space in this server. Also, I envisage that the web developers would store their stuff in the www folders in the /root partition as well. I think /home would only be used for emails, unless I'm missing something.

Can someone with more experience please confirm if this is a wise thing to do?

---

### Post by promodus on 2008-10-10
Well... working backwards...

To use squid you need to install it.
```
sudo apt-get install squid
```

Easy enough.

To find the configuration for squid
```
dpkg -L squid
```
From that list I see /etc/squid so i assume the configuration is in there...

well, lets cat the file and grep for keywords.
Lets try "cache", lets try "dir" and we don't want comments so lets exclude "#"
```
sudo cat /etc/squid/squid.conf | grep -v "#" | grep cache | grep dir
```
and the output:
> cache_dir ufs /var/spool/squid 51250 16 256


So there you have it...
Squid caches the file in /var/spool/squid

---

### Post by Aeros84 on 2008-10-10
Thanks for your reply :) 

Yes, squid saves the data in /var/spool/squid, which is in the /root partition of the hard drive, isn't it?

Any advice on the general partitioning question?

---

### Post by promodus on 2008-10-10
Don't confuse /root with / 

For clarity's sake it can be done where the user "root" could actually be renamed "Administrator"

the translation above would be
/Administrator = "Administrators home directory"
/ = root directory. 
"root directory" was used as it's the best way to describe it as it is similar to a tree that root is at the bottom of it all...

I hope that explains it.

---

### Post by dperfors on 2008-10-10
I think I should say something about that /root thing... If you type in the console as root: cd /root, you are comming in the home directory of root..
the root directory you mean is "/" (also called the root directory)

For the rest of the question, I think I should do something like:
/ -> duh, this is always there :)
SWAP -> duh, also (almost) always there :)
/home -> usefull, do you put your dev projects here? or the mail directories?
/var/spool/squid -> usefull, if squid doesn't remove the cache, you system will keep running.

So as a rule of thumb I would make the / partition as small as is needed for the system to run properly.
Create a /home partition for the home directories.
/usr could be used for applications (but since configs are writen in /etc, I would just put it all on /)
make a seperate partition for /var (most of the times used for logs, caches and some important data such as databases and mail.
/tmp could get a small partition.

by doing this, it is hardly possible to lockdown the system because / is full.

Hope this helps :)

---

### Post by Idefix82 on 2008-10-10
I agree with dperfors. Your system will run much more smoothly if you create a separate /var partition and give it a couple GB. This way, your main partition won't get fragmented so quickly by the ever changing log files.
I think a separate /tmp partition is kind of a luxury with only 40GB unless you have an application which you know will use /tmp heavily.

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> Thanks for your reply :) 

Yes, squid saves the data in /var/spool/squid, which is in the /root partition of the hard drive, isn't it?

Any advice on the general partitioning question?

If I'm building a server I always create a separate partition for /var - a runaway process can generate enough logfiles to trash the filesystem and if /var is on its own partition it doesn't put any other data at risk.

How I'd do it -

/: 8GB
/swap: 2GB
/var:  10GB
/home: 20GB

---

### Post by promodus on 2008-10-10
```
du -sh /*/ 2> /dev/null
```

Rule of thumb? Partition it to your needs.

Do you have just one hard drive? Is this a RAID system?
How many users are going to be connecting?
Any idea of load?

I wouldn't make / limited. 
You want room for /etc to grow if needed, or if you need to add future tools which may reside in /bin or /sbin

---

### Post by hyper_ch on 2008-10-10
I'd also use just / and swap...

---

### Post by dperfors on 2008-10-10
> **promodus said:**
> 
I wouldn't make / limited. 
You want room for /etc to grow if needed, or if you need to add future tools which may reside in /bin or /sbinI agree, the reason I mantioned this is because of my background with BSD, where you have the base system on / and everything else on /usr or /usr/local (including configuration)
As I mentioned I would put /usr /etc and / on the same partition.

With the rule of thumb I gave I assumed a single drive system, with not much users. and I didn't want to mention any numbers of size, they depend on the situation :)

@Idefix82: you are right, I didn't look to the size of the harddrive... I always did it, but that where for single user test machines :)

---

### Post by Aeros84 on 2008-10-10
Thanks guys.

Yes, only one drive at this time, no RAID. Small office, so only about 5 admin workers and 3 developers will connect to it. The developers will probably store their php/sql work in the / partition, not the /home partitions.

These people do, however, browse a LOT of multimedia sites in their line of work. Flash, animations, jpegs - the works. It gets loaded on a daily basis, and a lot of it is repetitive. So a big cache for squid would be wise. If I make the /var a seperate partition, how much space can be set aside for squid in there? In other words, say the partition is 10GB, what cache size can I set squid to use that won't hog the entire partition and cause problems?

Furthermore, unless I'm missing something, the /home directories would only be used to store emails temporarily, and the /home partition can be small, maybe 5GB? Less probably? Or is there something I'm not seeing here, some other service or something that would reside in the /home directories?

Therefore, maybe partitioning like this would work:

/: 20 GB
/swap: 2 GB
/home: 5 GB
/var: 13 GB (With squid's cache size set to 7gb, leaving 6gb for the rest of the var stuff. Overkill? Or okay?)

What do you think?

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> 
/: 20 GB
/swap: 2 GB
/home: 5 GB
/var: 13 GB (With squid's cache size set to 7gb, leaving 6gb for the rest of the var stuff. Overkill? Or okay?)

What do you think?

I think that works fine.  If you don't need the space for /home there's no reason to give users that much space.

You could move a little more space from / to /var if you want - my root directory uses less than 4GB of space and this is a desktop workstation - a server should require less space.  Might as well use it for logfiles, web content and squid cache  :)

---

### Post by Aeros84 on 2008-10-10
Oh right, the www root folder also resides in /var, doesn't it? Or does it sit in /usr? I can never remember.

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> Oh right, the www root folder also resides in /var, doesn't it? Or does it sit in /usr? I can never remember.

Yup - web content lives in /var as well ;)

---

### Post by Aeros84 on 2008-10-10
That makes things simpler. Thanks! :)

Just one more thing, that might actually affect this a bit. I've got the Ubuntu Desktop CD here with me, instead of Ubuntu Server (yes, I know, someone requested the wrong one :(). Now, apparently, you can install the Desktop and then just install the servers/services that you need, and disable X. This'll result in pretty much the same thing as Ubuntu Server. Correct so far?

If so, is there anything special I should look out for to remove? Something that'd either hog resources in the form of RAM/CPU, or hard drive space?

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> That makes things simpler. Thanks! :)

Just one more thing, that might actually affect this a bit. I've got the Ubuntu Desktop CD here with me, instead of Ubuntu Server (yes, I know, someone requested the wrong one :(). Now, apparently, you can install the Desktop and then just install the servers/services that you need, and disable X. This'll result in pretty much the same thing as Ubuntu Server. Correct so far?

If so, is there anything special I should look out for to remove? Something that'd either hog resources in the form of RAM/CPU, or hard drive space?

X can be handy even on a server - I usually build servers with the desktop CD and just disable gdm (I use GNOME) so X doesn't start unless I start it.

Easiest way I know of to disable the junk is with sysv-rc-conf, which doesn't require X but does require root access.  You can pick services there and then just uncheck the boxes if you don't want the service to load.  I think it's better than either bum or the services applet that comes with Ubuntu.

You should be able to shut off

acpi-supp$
alsa-utils
apmd
apparmor
atd
bluetooth
bootclean
bootlogd
brltty
console-s$
cryptdisks
cryptdisk$
etc-setse$
gdm (this will require you to type 'startx' to start an X session)
hotkey-se$
laptop-mo$
powernowd (unless you have an AMD processor)
powernowd$ (see above)
preload (but I use it)
stop-boot$

At least that's what I have shut off - your list will vary  :)

Disk space shouldn't be an issue.  As long as you're not running the daemon or program all it does is sit on the disk.  You've got enough disk space to do what you need to do, I think.

---

### Post by Aeros84 on 2008-10-10
Ah, that's helpful, the list of processes one can consider shutting down. I agree with you that X can be handy at times, so just stopping it from running (by disabling gdm) should be the ideal solution.

Thank you :)

---

### Post by Aeros84 on 2008-10-10
> **wizard10000 said:**
> I think that works fine.  If you don't need the space for /home there's no reason to give users that much space.

You could move a little more space from / to /var if you want - my root directory uses less than 4GB of space and this is a desktop workstation - a server should require less space.  Might as well use it for logfiles, web content and squid cache  :)

Actually, one more question here - what happens when the /var partition is full? Does it start to overwrite logfiles?

Maybe it would be better to clear all logfiles on a regular basis? Like an automated task wiping all logs once every 7 days or so. What would you recommend.

---

### Post by lykwydchykyn on 2008-10-10
There is a daemon called logrotate that is automatically set up.  It manually archives, compresses, and deletes old logs.  You can tweak the settings if you want to, but usually the defaults are good enough for me.

BTW, if I were setting this up, I would not leave the web root under /var if my users were doing web development.  I'd redirect it to something like /home/www or just make users use their ~/public_html folders so that important data would all be under /home.  Same goes for the mysql files.   Otherwise /var becomes a mix of useless data you don't need to back up (squid cache) and extremely important data that you need to backup (web development files).

Just a thought.

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> Actually, one more question here - what happens when the /var partition is full? Does it start to overwrite logfiles?

As lykwydchykyn mentioned above logrotate will do what you ask but out of the box it only runs once a day and a bad process can trash a filesystem a heck of a lot quicker than that  ;)

To answer your other question if a partition fills up the results can be pretty nasty and no, it doesn't overwrite logfiles (logrotate does that) but continues to append to logfiles until the filesystem pukes on you.

I sorta agree with lykwydchykyn - I think that production web stuff should stay in /var but development web stuff could and probably should go in the user's home directory.  A squid cache can be excluded from whatever backup strategy you choose to implement, though.

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> ...The developers will probably store their php/sql work in the / partition, not the /home partitions.

Just saw this.  Bad idea  ;)

Unprivileged users don't have write access to / and giving them privileges isn't a grand idea either - user-created files should go either in /home or /var.  There's a method to all this, honest.  Looky here -

[http://www.ahinc.com/linux101/structure.htm](http://www.ahinc.com/linux101/structure.htm)

---

### Post by Aeros84 on 2008-10-10
> **wizard10000 said:**
> Just saw this.  Bad idea  ;)

Unprivileged users don't have write access to / and giving them privileges isn't a grand idea either - user-created files should go either in /home or /var.  There's a method to all this, honest.  Looky here -

[http://www.ahinc.com/linux101/structure.htm](http://www.ahinc.com/linux101/structure.htm)

Yeah, that was before I realised /var should be in a separate partition though :)

The problem with putting the web development stuff in the home directories (at least, according to my Linux-barren logic, so I'm most likely wrong :P) is that several developers would work on one site at the same time, therefore a central development space in the /var partition would be advantageous, not so?

Also, unrelated question (sorry, I'm just stacking this thread with new questions, I know) - is it possible to do traffic shaping (or should I say, limiting) via squid and/or iptables? For instance, I want PC1 to reach a max bandwidth transfer rate of only 10kbps to the WAN (ADSL), but unlimited to the rest of the LAN. And maybe PC2 can have a maximum transfer rate of 20kbps to the WAN, but also unlimited to the LAN. Hope this actually makes sense :) Not really interested at THIS stage in HOW to set it up, just want to know if it's possible, because it's definitely necessary in the office.

(Just to give you an idea of how I intend to set this up, physically: The PC's would all plug in to the switch hub, which in turn goes to eth0 on the Linux box. Then there's a cable running from the Linux box's eth1 to the ADSL router. Thus, all traffic between the PC's and the Internet HAVE to travel through the Linux box.)

---

### Post by wizard10000 on 2008-10-10
> **Aeros84 said:**
> Yeah, that was before I realised /var should be in a separate partition though :)

The problem with putting the web development stuff in the home directories (at least, according to my Linux-barren logic, so I'm most likely wrong :P) is that several developers would work on one site at the same time, therefore a central development space in the /var partition would be advantageous, not so?

Also, unrelated question (sorry, I'm just stacking this thread with new questions, I know) - is it possible to do traffic shaping (or should I say, limiting) via squid and/or iptables? For instance, I want PC1 to reach a max bandwidth transfer rate of only 10kbps to the WAN (ADSL), but unlimited to the rest of the LAN. And maybe PC2 can have a maximum transfer rate of 20kbps to the WAN, but also unlimited to the LAN. Hope this actually makes sense :) Not really interested at THIS stage in HOW to set it up, just want to know if it's possible, because it's definitely necessary in the office.

(Just to give you an idea of how I intend to set this up, physically: The PC's would all plug in to the switch hub, which in turn goes to eth0 on the Linux box. Then there's a cable running from the Linux box's eth1 to the ADSL router. Thus, all traffic between the PC's and the Internet HAVE to travel through the Linux box.)

I think putting the development space in /var is probably the best idea.

I'm afraid I can't help you on the traffic shaping, though - maybe starting a new thread is a good idea?

cheers -

---

### Post by Aeros84 on 2008-10-10
Yup, about to.

Server is finally up and running, just finished the installation and set up sshd so as to prep it for the more serious work to start.

Thanks again for the help :)

---

### Post by lykwydchykyn on 2008-10-10
You can create a shared folder under /home, I think I mentioned that.  My logic in moving it from /var is that /var contains a lot of non-important stuff that isn't user data.  I like keeping my user data in one place for easy backup and to manage permissions consistently.  But that's me.  I have never seen the logic in putting the webroot under /var, it doesn't jive with the FHS.  But that's what Debian decided, and Ubuntu followed suit.  

That's my reasoning, anyway.  You won't hurt my feelings if you ignore it.

---

### Post by chrisj_0 on 2008-10-10
Partitioning for servers can be tricky.
It really depends on what it's to be used for. There's no perfect partitioning solution for all types of servers.

I typically start with something like this.

/boot 512 MB
/ 1GB
/usr 3GB
/tmp 1GB
/var 2GB
SWAP 2 to 4GB

If your installing X and a big window manager they you'll want to put /usr to at least 5GB. 

Now you need to customize it for use.
if it's a file server or development server add home partition
/home 10GB

mail, web, squid server start adding partitions specific for those
mail: 
/var/spool/mail 5 to 15GB
/var/log (if the server is very active) 2 to 8 GB

www,
/var/www 

etc...

If this is going to be a development machine I highly recommend not putting production services on it. any server that developers have access to will go down. They do all kinds of crazy things when troubleshooting code that "they know should work". Also look at CVS or SVN for maintaining software releases.

---

### Post by ilrudie on 2008-10-10
[Traffic Shaping.]("http://lartc.org/")

I'm not sure if you are aware but any path can be a separate partition.  

Partitioning the old fashioned way can be a little tricky when you are not sure about how each partition will need to be sized. In many cases LVM2 (Logical Volume Manager) can be a life saver.  Its definitely worth looking into.  Essentially it allows you to have pools of disk(s) called volume groups from which you can make logical volumes instead of hard partitions.  Got a user who just filled up /var?  Don't sweat it.  Just grow var's logical volume.  If you run out of hard disk space you can simply add a new drive to the server, add it to the volume group and use it for and filesystem built off that volume group.  If you are interested in it read up on the subject because there are several paths that should not be managed by LVM2 yet.  /boot, /etc, /root, /sbin, /dev.... probably a few more I'm forgetting.  Good news here is that these shouldn't be getting a lot of user garbage so growing them probably won't ever be necessary.  /usr, /var and /home would be great places to use LVM2 though.  Good luck.

Sorry the post was a little late (looks like you already built the box) but I thought it might be good for you to know about anyway.

---

### Post by Stason on 2008-11-07
[HOWTO/Bandwidth-Limiting]("http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html")

---

