---
title: "Web Server Lagging"
date: 2009-06-25
forum: Server Platforms
---

### Post by k33bz on 2009-06-25
Starting today I have noticed that I have to reboot my server almost everytime I submit another post to my wordpress site. As you can tell this runs as an inconvenience. This has been doing this since yesterday. After I post the website hangs for long periods of time. After I reboot it everything is back to normal.

Things are even slow when I sshPutty to my server. Can someone help with this problem please.

I am running LAMP with Wordpress.

---

### Post by philcamlin on 2009-06-25
reinstall lamp?

---

### Post by k33bz on 2009-06-25
> **philcamlin said:**
> reinstall lamp?

are you serious, is that the only fix option I have is to re-install LAMP

---

### Post by R.Bucky on 2009-06-25
No, no. Reinstall on a critical error only. take a look at your logs at /var/log. In particular, look at dmesg, your /var/log/apache2/ logs. Also, think about what changed from yesterday. did you install a new cms, change a setting, or do something else. if your server bogs down after a Wordpress post, look at possible reinstalling WP. But, what the hell? Reinstall LAMP?

---

### Post by k33bz on 2009-06-25
> **R.Bucky said:**
> No, no. Reinstall on a critical error only. take a look at your logs at /var/log. In particular, look at dmesg, your /var/log/apache2/ logs. Also, think about what changed from yesterday. did you install a new cms, change a setting, or do something else. if your server bogs down after a Wordpress post, look at possible reinstalling WP. But, what the hell? Reinstall LAMP?

Whew, glad someone had a better Idea than re-install LAMP. :popcorn: I will be taking a look at my logs. I havn't installed anything from the time it was working and from the time it started acting up. Right before it happened I had Filtered my Adsense, that is when it happened. Just don't see how that would effect my server. I could be wrong though.

in log /var/log/dmesg it has a few lines that say:
```
swsusp: Registered nosave memory region
```
There is a total of 6 lines of this each with a different list of numbers after them.

Then in my syslog I see several entries:
```
webserver postfix/master[5957]: warning: process /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
```
There was alot of dif entries that were similiar.

Everything else just looks fine.

---

### Post by cariboo on 2009-06-26
Like R.Bucky said check /var/log/apache2/error.log, it should point you to where your error is.

---

### Post by k33bz on 2009-06-26
> **cariboo907 said:**
> Like R.Bucky said check /var/log/apache2/error.log, it should point you to where your error is.

Like I said, everything else looks fine other than what I have already posted. there was nothing out of the ordinary in any of the logs in /var/log/apache2/

---

### Post by Aeonsies on 2009-06-26
This is kinda a shot in the dark but have you checked to see if your server is spiking on memory or CPU consumption during the upload?  I know you said it was working fine a few days ago but perhaps something changed and you aren't aware of it, system updates applied or something of that nature?

---

### Post by k33bz on 2009-06-26
> **Aeonsies said:**
> This is kinda a shot in the dark but have you checked to see if your server is spiking on memory or CPU consumption during the upload?  I know you said it was working fine a few days ago but perhaps something changed and you aren't aware of it, system updates applied or something of that nature?

I have not checked that, and it could be very well a good possibility, how would I do that VIA command line? I don't have any GUI on my Server.

---

### Post by Kareeser on 2009-06-26
Like others have said, logs are your best friend. Check the apache logs (located in /var/log/apache2), and the syslog.

For command line checking of CPU and memory usage, install the program "htop". The prorgam "top", which is preinstalled, works in a pinch.

---

### Post by k33bz on 2009-06-26
> **Kareeser said:**
> Like others have said, logs are your best friend. Check the apache logs (located in /var/log/apache2), and the syslog.

For command line checking of CPU and memory usage, install the program "htop". The prorgam "top", which is preinstalled, works in a pinch.

The logs like I have repeatedly have said show nothing out of the ordinary, except for what I have posted up above.

But thanks for the programs that I will need to check CPU and Memory Usage.

---

### Post by k33bz on 2009-06-26
Yup there is where the problem is, the server is gobbling up alot of my ram. I notice there is several entries (where most of my ram is at) for www-data. Understandable that it uses the most ram. But several entries all with the same command baffles me.
```

/usr/bin/apache2/ -k start
```

Are there suppose to be multiple lines of the same command? I have 10 lines of this.

---

### Post by Kareeser on 2009-06-27
Yep. That's how Apache is configured in Unix, the parent process spawns "child" processes, and they each handle individual connections.

This is different from Apache's default on a Windows install, where I believe will spawn one giant parent process with no children.

This may mean a mis-configuration of your apache server, or a rogue web script gone wrong. Tell me, do you run any customized scripts on your server? Perhaps one of your installed Wordpress plugins may be the culprit.

---

### Post by windependence on 2009-06-27
Memory is most likely NOT your problem. Linux manages memory very differently than Windoze in that it will appear to use ALL your memory, but it really isn't. 

It looks to me like you have two problems here. For the slowness problem, please post your /etc/resolv.conf

The other problem you have is with postfix. What is the output of:

```
tail -n 25 /var/log/maillog
```

-Tim

---

### Post by k33bz on 2009-06-27
> **windependence said:**
> Memory is most likely NOT your problem. Linux manages memory very differently than Windoze in that it will appear to use ALL your memory, but it really isn't. 

It looks to me like you have two problems here. For the slowness problem, please post your /etc/resolv.conf

The other problem you have is with postfix. What is the output of:

```
tail -n 25 /var/log/maillog
```

-Tim

/etc/resolv.conf
```
nameserver 192.168.1.1
```
I am not sure if that is for my router or if that is for the server itself, the server should be 192.168.1.3. Please let me know if I need to change that.

tail -n 25 /var/log/mail.log

```
Jun 27 14:23:54 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:24:54 webserver postfix/trivial-rewrite[6463]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:24:55 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6463 exit status 1
Jun 27 14:24:55 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:25:55 webserver postfix/trivial-rewrite[6464]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:25:56 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6464 exit status 1
Jun 27 14:25:56 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:26:56 webserver postfix/trivial-rewrite[6466]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:26:57 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6466 exit status 1
Jun 27 14:26:57 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:27:57 webserver postfix/trivial-rewrite[6473]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:27:58 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6473 exit status 1
Jun 27 14:27:58 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:28:58 webserver postfix/trivial-rewrite[6476]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:28:59 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6476 exit status 1
Jun 27 14:28:59 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:29:59 webserver postfix/trivial-rewrite[6477]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:30:00 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6477 exit status 1
Jun 27 14:30:00 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:31:00 webserver postfix/trivial-rewrite[6480]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:31:01 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6480 exit status 1
Jun 27 14:31:01 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun 27 14:32:01 webserver postfix/trivial-rewrite[6502]: fatal: bad string length 0 < 1: etc/postfix/mysql_mailbox.cf_dbname = 
Jun 27 14:32:02 webserver postfix/master[5958]: warning: process /usr/lib/postfix/trivial-rewrite pid 6502 exit status 1
Jun 27 14:32:02 webserver postfix/master[5958]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling

```

From htop:
[IMG]http://i703.photobucket.com/albums/ww31/creative-funds/htop.png[/IMG]

---

### Post by k33bz on 2009-06-27
-BUMP-

I really need a fix soon :)

---

### Post by R.Bucky on 2009-06-28
did i read that screenshot correctly in that you have 241MB RAM? I have never had to run a GUI web server with that low amount of RAM. I am not sure that you can operate your server with your RAM. Anyone else...?

You can check your memory via command line using ```
cat /proc/meminfo
```

---

### Post by R.Bucky on 2009-06-28
One more thing on the resolv.conf - the nameserver should be pointed to your router ip if you do not have a DNS server operating on your box. If you do not have a DNS server, that should be fine.

---

### Post by k33bz on 2009-06-28
thanks, but yes and no, you read the amount of ram right, and no, my server is all command line, there is no GUI, that is a screen shot from my dekstop going through SSH.

Ok so my nameserver is pointing in the right direction. Now what about everything from tail -n 25 /var/log/mail.log?

```
cat /proc/meminfo
MemTotal:       246900 kB
MemFree:          3908 kB
Buffers:          2512 kB
Cached:          19692 kB
SwapCached:     119536 kB
Active:         142124 kB
Inactive:        81164 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       246900 kB
LowFree:          3908 kB
SwapTotal:      722884 kB
SwapFree:       512668 kB
Dirty:              56 kB
Writeback:           0 kB
AnonPages:      192636 kB
Mapped:          10328 kB
Slab:             9872 kB
SReclaimable:     2332 kB
SUnreclaim:       7540 kB
PageTables:       2428 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:    846332 kB
Committed_AS:   476880 kB
VmallocTotal:   782328 kB
VmallocUsed:      5076 kB
VmallocChunk:   777064 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB

```

---

### Post by R.Bucky on 2009-06-28
I use Google to handle mail for my domain. I lack the expertise to advise you on this one. However, it really looks like you need more RAM. I used to consume around 250-300MB RAM operating my Wordpress server with RSS2HTML script. 

Your distribution alone can consume that much RAM. Then, consider that you are forwarding your display through SSH and then asking PHP to post a page or blog post, and that is your RAM allowance. Consider spending $30 on a 512 or 1GB stick of RAM.

---

### Post by k33bz on 2009-06-28
> **R.Bucky said:**
> I use Google to handle mail for my domain. I lack the expertise to advise you on this one. However, it really looks like you need more RAM. I used to consume around 250-300MB RAM operating my Wordpress server with RSS2HTML script. 

Your distribution alone can consume that much RAM. Then, consider that you are forwarding your display through SSH and then asking PHP to post a page or blog post, and that is your RAM allowance. Consider spending $30 on a 512 or 1GB stick of RAM.

It was running fine just a few days ago, been running it for 2 months now, never no problem, till now that is, lol. Will need to fund more than just $30 in my case, need to get a new server. Old, real old desktop converted for use as a server. Hopefully I can find RAM that will still fit it.

Thanks R. Bucky

---

