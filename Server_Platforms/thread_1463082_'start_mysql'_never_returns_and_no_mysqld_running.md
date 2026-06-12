---
title: "'start mysql' never returns and no mysqld running"
date: 2010-04-26
forum: Server Platforms
---

### Post by bretzeltux on 2010-04-26
Since /etc/rc2.d/S19mysql does not exists anymore, and then init.d/mysql uses /sbin/start, I am unable to use mysql server anymore:

me@mycomputer~#start mysql [ret]
...... for hours this command never returns so that ^C aborts...

me@mycomputer~#ps axw |grep mysql 
 ( no results, no mysql!!! ) 

me@mycomputer~#stop mysql [ret]
no returns either!!!

This upstart [start|stop] thing seems a total failure for mysql!!!
need help!

---

### Post by ghost_ryder35 on 2010-04-26
> **bretzeltux said:**
> Since /etc/rc2.d/S19mysql does not exists anymore, and then init.d/mysql uses /sbin/start, I am unable to use mysql server anymore:

me@mycomputer~#start mysql [ret]
...... for hours this command never returns so that ^C aborts...

me@mycomputer~#ps axw |grep mysql 
 ( no results, no mysql!!! ) 

me@mycomputer~#stop mysql [ret]
no returns either!!!

This upstart [start|stop] thing seems a total failure for mysql!!!
need help!


does the following command work?
```

/etc/init.d/mysql start

```

---

### Post by bretzeltux on 2010-04-26
It does the same thing

manually :
sudo /sbin/mysqld &

does works but not really the right thing to do ...

and...:
'Since /etc/rc2.d/S19mysql does not exists anymore, and then init.d/mysql uses /sbin/start, I am unable to use mysql server anymore:'

Why are you asking me to do what I've already reported that won't work ?

---

### Post by ghost_ryder35 on 2010-04-26
> **bretzeltux said:**
> It does the same thing

manually :
sudo /sbin/mysqld &

does works but not really the right thing to do ...

and...:
'Since /etc/rc2.d/S19mysql does not exists anymore, and then init.d/mysql uses /sbin/start, I am unable to use mysql server anymore:'

Why are you asking me to do what I've already reported that won't work ?

i was just trying to help troubleshoot.  perhaps you should install mysql on another server and copy the init script from that one over to the broken one.

---

### Post by bretzeltux on 2010-04-26
Sorry if I looked a bit rude -
[LIST]
[*]My Server is not 'broken'
[*]manually starting mysqld from /sbin/mysqld - does work
[*]Thus what I am totaly screwed in is with 'upstart' :/sbin/start | stop for mysql - that seems itself 'screwed/screweing mysql service'
[*]ubuntu server 9.10/10.04 behaviour are the same(I guess same failures with desktop editions as well!)...
[/LIST]

Is mysql installation scripts packages have been ever tested since 9.10 ???
In my book it does not ... rather it was 'assumed to work...'...

If I read other topics ( desktop/server editions ) it seems the same related problems occured for other users ...

---

### Post by dannyboy79 on 2010-04-26
Looking at the mysqld upstart job (/etc/init/mysqld.conf) you can see that it "start on (net-device-up". Since mysqld is configured to bind to a specific address it fails to start if the network interface isn't up yet.

I'd suggest to update mysqld upstart job to "start on (net-device-up IFACE=ethX" to start mysqld only when the correct interface is up.

found this bug here:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736)

---

### Post by bretzeltux on 2010-04-26
> **dannyboy79 said:**
> Looking at the mysqld upstart job (/etc/init/mysqld.conf) you can see that it "start on (net-device-up". Since mysqld is configured to bind to a specific address it fails to start if the network interface isn't up yet.

I'd suggest to update mysqld upstart job to "start on (net-device-up IFACE=ethX" to start mysqld only when the correct interface is up.

found this bug here:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736)



WOW! cannot see the concept or the fix behind this solution -- really - 
This solution effectively work - thank  you dannyboy79 for the link,but still non-sense bug confirmed... That means I will have to manually start mysql manually until the bug get fixed...

---

### Post by bretzeltux on 2010-04-26
Just rebooted with the suggested fix from dannyboy79 and mysqld is up and running from reboot. 
Thanks again dannyboy79, hope they will find a way to 'bind' the IFACE upon the prefered network device in the installation scripts... 
I had no means to guess this kind of deep research ...

solved...

---

### Post by dannyboy79 on 2010-04-26
> **bretzeltux said:**
> Just rebooted with the suggested fix from dannyboy79 and mysqld is up and running from reboot. 
Thanks again dannyboy79, hope they will find a way to 'bind' the IFACE upon the prefered network device in the installation scripts... 
I had no means to guess this kind of deep research ...

solved...

the power of google prevails again! what would we do without google search engine?

---

### Post by tzihad on 2010-07-15
I modified /etc/init/mysql.conf the exec line
exec /usr/sbin/mysqld &
adding & at end end of exec line fixed this for me

---

