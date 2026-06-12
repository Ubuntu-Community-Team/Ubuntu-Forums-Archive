---
title: "Stunnel4 won't start on Gutsy"
date: 2007-10-25
forum: Server Platforms
---

### Post by trmentry on 2007-10-25
I just installed Stunnel4 on a bare install of Gutsy server (64bit).  

The daemon won't start up.   I changed the /etc/stunnel/stunnel.conf file to be client mode.  Then sudo /etc/init.d/stunnel4 start  and nada.  Nothing in logs.  I even changed stunnel.conf to debug and still get nothing.

Any pointers please?

---

### Post by dirk362 on 2007-10-25
To run as a Daemon you need to edit /etc/init.d/stunnel which you say you have, but also edit the default file as well.

Edit ```
/etc/default/stunnel
``` and change ```
ENABLED=1
``` as per below

```
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
```

You should then be able to run as a Daemon.

You may then hit another issue (which I have and have been unable to resolve), which is that it will fail to resolve some DNS entries and error in /var/log/stunnel4/stunnel.log with things like:-

```
2007.10.25 11:18:25 LOG5[5744:3082836880]: nntp accepted connection from 127.0.0.1:45848
2007.10.25 11:18:25 LOG3[5744:3082836880]: Error resolving '**removed**': Neither nodename nor servname known (EAI_NONAME)
2007.10.25 11:18:25 LOG3[5744:3082836880]: No host resolved
2007.10.25 11:18:25 LOG5[5744:3082836880]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
```


To fix this, you have to restart the daemon with

```
sudo /etc/init.d/stunnel4 restart
```

and then it works. I've tried everything (nssswitch etc) to fix this and can't. Seems to be specific to Gutsy as this worked fine in Feisty.

Hopefully the above will help...

---

### Post by trmentry on 2007-10-25
I completely missed that when I poking around.  I made the change and now the daemon attempts to start but still doesn't.

Barks about its pid file.  

```

root@kashyyyk-ubuntu:/etc/stunnel# /etc/init.d/stunnel4 start
Starting SSL tunnels: [Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file

```

And from the stunnel.conf file
```

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid


```

The only change to stunnel.conf I made was to make it a client and added in my nntp/s stuff.

---

### Post by trmentry on 2007-10-25
Got it figured out.

Logs was showing:

```

2007.10.24 11:01:10 LOG5[4714:46975720988816]: stunnel 4.20 on x86_64-pc-linux-gnu with OpenSSL 0.9.
8e 23 Feb 2007
2007.10.24 11:01:10 LOG5[4714:46975720988816]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:L
IBWRAP
2007.10.24 11:01:10 LOG6[4714:46975720988816]: file ulimit = 1024 (can be changed with 'ulimit -n')
2007.10.24 11:01:10 LOG6[4714:46975720988816]: poll() used - no FD_SETSIZE limit for file descriptor
s
2007.10.24 11:01:10 LOG5[4714:46975720988816]: 500 clients allowed
2007.10.24 11:01:10 LOG3[4714:46975720988816]: Error binding pop3s to 0.0.0.0:995
2007.10.24 11:01:10 LOG3[4714:46975720988816]: bind: Address already in use (98)

```

I double checked my stunnel.conf file and pop3s, imaps etc were on by deafult which threw me off.  Commented those out and stunnel is up now.  Now to see if I can get nntps to work. :)

---

### Post by dirk362 on 2007-10-25
I had the same issue, and it wasn't fixed until I created the mail.pem (even though it is commented out in the stunnel.conf file) in /etc/stunnel directory.

I have no idea why that is the case, but it fixed the problem of stunnel not starting...

You can create one via the command

```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mail.pem -out mail.pem
```

Then you have to answer a few questions. The information you provide by answering these questions will be stored in the certificate, but as its self-signed, you can put in pretty much what you like (although preferable real information)

```
Country Name (2 letter code) [GB]:
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:
Email Address []:
```

Try the above then restart and see if this helps. Also check the /var/log/stunnel4/stunnel.log file to see if this is created  (you may need to uncomment debug line in stunnel.conf)

---

### Post by dirk362 on 2007-10-25
Following on from my note above about daemon mode, I wonder if anyone can help with my issue of DNS issues with stunnel4....

On first startup (as via init scripts), stunnel4 is running as

```
ps -ef | grep stun
stunnel4  5863     1  0 11:57 ?        00:00:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
dirk      7638  7604  0 11:59 pts/0    00:00:00 tail -f /var/log/stunnel4/stunnel.log
dirk      7700  7683  0 12:06 pts/1    00:00:00 grep stun
```

At this point I'm unable to resolve correctly, and get the error messages such as

```
2007.10.25 12:00:03 LOG3[5863:3082804112]: Error resolving '**removed**': Neither nodename nor servname known (EAI_NONAME)
2007.10.25 12:00:03 LOG5[5863:3086498704]: nntp accepted connection from 127.0.0.1:53454
2007.10.25 12:00:03 LOG3[5863:3082804112]: No host resolved
2007.10.25 12:00:03 LOG5[5863:3082804112]: Connection reset: 0 bytes sent to SSL, 0 bytes sent to socket
```

Now, if I restart stunnel4 with

```
sudo /etc/init.d/stunnel4 restart
Restarting SSL tunnels: [stopped: /etc/stunnel/stunnel.conf] [Started: /etc/stunnel/stunnel.conf] stunnel.
```

and then check it again

```
ps -ef | grep stun
dirk      7638  7604  0 11:59 pts/0    00:00:00 tail -f /var/log/stunnel4/stunnel.log
stunnel4  7712     1  0 12:07 ?        00:00:00 /usr/bin/stunnel4 /etc/stunnel/stunnel.conf
dirk      7714  7683  0 12:07 pts/1    00:00:00 grep stun
```

No difference is obvious, yet it now works fine and I no longer get any DNS lookup issues.

Anyone have any ideas of where to look ?  As stunnel4 creates a group but I can't see a user, I can't add say stunnel4 to the netdev group (which is potentially where this is failing). I've tried some variations for hosts in nsswitch.conf, but nothing makes any difference.

---

### Post by dirk362 on 2007-10-25
following on with the DNS lookup issues....

stunnel4 group membership might be the issue which is then breaking file permissions.

For example, if I look at /var/log/stunnel4, the permissions are set as

```

dirk@ubuntu-lounge:/var/log/stunnel4$ ls -l
total 56
-rw-r----- 1 root     adm      27275 2007-10-25 12:07 stunnel.log
-rw-r----- 1 root     adm       9951 2007-10-25 07:35 stunnel.log.1
-rw-r----- 1 root     adm        232 2007-10-24 07:35 stunnel.log.2.gz
-rw-r----- 1 root     adm       1640 2007-10-23 07:35 stunnel.log.3.gz
-rw-r--r-- 1 stunnel4 stunnel4  4721 2007-10-22 07:35 stunnel.log.4.gz

```

checking groups, stunnel4 is a member of only stunnel4. Output from "groups stunnel4" is
```

stunnel4 : stunnel4

```

So that would mean it doesn't have permissions to the log. Yet I can see log entries exist when running via the init.d

```

2007.10.25 12:07:05 LOG5[7711:3082946224]: stunnel 4.20 on i486-pc-linux-gnu with OpenSSL 0.9.8e 23 Feb 2007
2007.10.25 12:07:05 LOG5[7711:3082946224]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2007.10.25 12:07:05 LOG5[7711:3082946224]: 500 clients allowed

```

In other areas (/etc/stunnel/* and /etc/default/stunnel4) permissions are ok with -rw-r--r-- on files

What (if anything) is the security implication of adding stunnel4 into the adm group, and does anyone think this might help fix the issue ?

Or should I just change the log file to be stunnel4:stunnel4 (and why isn't that the case anyway, as it clearly was with the very first log file before rotation).

---

### Post by dirk362 on 2007-10-25
OK. So changing stunnel.log with

```

sudo chown stunnel4:stunnel4 stunnel.log

```

Fixes this issue straight away, even without having to stop/start etc.

So either I broke the permissions at some point whilst messing around, or the log rotation changed it. This is now fixed, and I now know what to check, so can confirm if tomorrow after log rotation this is still correct.

---

### Post by dirk362 on 2007-10-28
Well following day this stopped working again. Checking the log permissions, these had been changed to
```

-rw-r----- 1 root     adm        29277 2007-10-28 11:31 stunnel.log
-rw-r----- 1 root     adm      4361393 2007-10-28 07:35 stunnel.log.1
-rw-r--r-- 1 stunnel4 stunnel4    8442 2007-10-27 07:35 stunnel.log.2.gz

```
Checking /etc/logrotate.d/stunnel4, we have:-
```

/var/log/stunnel4/*.log {
        daily
         missingok
         rotate 356
         compress
         delaycompress
         notifempty
         create 640 root adm
         sharedscripts
         postrotate
           /etc/init.d/stunnel4 restart > /dev/null
         endscript
}

```
So do you think I can just change the create line to
```

         create 644 stunnel4 stunnel4

```
And what I'm struggling to understand is why I am the only one getting these issues. I am running a pretty standard Gutsy AMD64 install, everything added via proper add/remove or apt-get (so no automatix2 or anything). Are other people not getting this issue, not using stunnel4, or have I found a bug... ?

A **default** install of stunnel4 sets the permissions on the /var/log/stunnel4/stunnel.log file to **stunnel4:stunnel4**, so surely that is what it should stay as ?

I've had to add my user to the stunnel4 group to allow me to view the log files (of course with adm I have this read access already, but then stunnel4 doesn't resolve DNS).

More than happy to tweak, but I'm guessing we need to know if this is a wider issue before I report it as a potential issue/bug with the package maintainer.

---

### Post by trmentry on 2007-10-28
I would go ahead and try the change.  I've not been running stunnel a lot so my logs have yet to rotate... plus I'm in a vmware instance testing things before install on live server.

But does seem reasonable that the logrotate script is the culprit making those changes.

---

### Post by trmentry on 2007-11-06
To revisit this... I made the changes to my

/etc/logrotate.d/stunnel4 file to have 

create 640 stunnel4 stunnel4

But that doesn't seem to work b/c at some point it was changed back to root adm.

Any ideas?

I just got bit by the DNS thing, and restarted stunnel4 and it was fine even though logs are root adm currently.

---

### Post by dirk362 on 2007-12-02
Just to follow up (as its been a while), I've never managed to sort this. The DNS issue and unable to resolve occurs almost on a whim, with some reboots it works fine, others needs a restart of stunnel4 via sudo.

The only thing I can think of is the startup scripts and ordering.
stunnel4 is at S20, along with a load of other stuff. I was wondering if this means sometimes the sequence is marginally different causing the issue ?

I am at a loss that this isn't a wider issue, unless trmentry and I have something broken in our config and are just unlucky :(

For now I run via a startup session a restart of stunnel4, which works, but its a kludge and I shouldn't need to do this.

---

### Post by trmentry on 2007-12-02
I've been debating on just having cron restart stunnel4 at midnight everynight.
Its a hack, but would prob avoid the dns thing.   I'm hoping this is fixed in 8.04

---

### Post by gomtuu on 2007-12-16
I'm having the exact same problem dirk362 described. On some boots stunnel4 doesn't work and produces an error message that appears to be DNS-related, and on other boots it works just fine. Has anyone filed a bug report for this yet?

An interesting development: stunnel4 didn't work when I booted today, but instead of restarting it, I searched Google to find out more about the problem while Pan kept trying to connect in the background. About five minutes after the first failed connection attempt, stunnel4 started working again by itself. This would also put it just over five minutes after stunnel4 (and my comptuer) started. Not sure what that means.

Anyway, I've now deleted the S20 rc*.d symlinks for stunnel added them again as S21. I'll let you know if that changes anything.

-Don

---

### Post by gomtuu on 2007-12-18
> **gomtuu said:**
> Anyway, I've now deleted the S20 rc*.d symlinks for stunnel added them again as S21. I'll let you know if that changes anything.
-Don

Update: This hasn't helped.

-Don

---

### Post by gggie on 2008-01-27
> **gomtuu said:**
> I'm having the exact same problem dirk362 described.

I'm having this same problem too.  Set up cron to restart stunnel every 12 hours to fix...

---

### Post by Penguin3D on 2008-07-22
Don't know if this pertains to this problem or not, but the "servname is not supported for ai_socktype (EAI_SERVICE)" is solved by adding the port to the server name. 

My problem was under the "connect" in the config file, I had only the server name, changing it to 'connect=<SERVER_NAME:PORT>' solved everything... :popcorn:

---

