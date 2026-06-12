---
title: "* Reloading /etc/samba/smb.conf smbd only"
date: 2009-04-27
forum: Server Platforms
---

### Post by mrwolf on 2009-04-27
Hi everyone,

I installed jaunty on my server with LAMP and SAMBA.
since the first boot every minute I get this message in the console:

* Reloading /etc/samba/smb.conf smbd only

I readed in a 1 year old post to put interfaces = eth0 in the smb.conf
I tried it without success

can anyone help me with this

Thanks

---

### Post by capscrew on 2009-04-27
> * Reloading /etc/samba/smb.conf smbd only

This is a comment from the /etc/init.d/samba script. You can see the line by looking at the script:```
more /etc/init.d/samba
``` You should see it around line 88 or so. 

It looks as if you have a cron job invoking the script.

---

### Post by PinkFloyd102489 on 2009-04-28
Im getting the same thing on mine.

When it does reload the samba config, it kills all networking on my box.

---

### Post by amadeus79 on 2009-04-28
I can confirm this to. Pretty annoying thing. Same message but with me it comes aproximately every 5 seconds. In console of course. It is not a cron job. If I'm not mistaken I don't have any cronjobs at all. I used "crontab -e" to check.

---

### Post by capscrew on 2009-04-28
Hmmmmm.  I would look in the logs for suspicious activity.  Here is what I found in /var/log/samba/log.samba  when I manually ran "samba reload"```
[2009/04/28 08:34:13, 1] smbd/server.c:open_sockets_smbd(491)
  Reloading services after SIGHUP

```

If not a cron job (and remember cron jobs do not have to be owned by you), then I would look for a process that is running in the background that calls the /etc/init.d/samba script.

Does anyone run webmin, ebox, etc?  All are capable causing  this.

---

### Post by mrwolf on 2009-04-28
i got a lot of this in my log.smbd:
```
[2009/04/28 20:07:05,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/04/28 20:36:49,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/04/28 20:59:28,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/04/28 21:26:10,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/04/28 21:54:38,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP

```

I don't have anything special in my crontab, I'm the only user of the server right now and I got this since the first boot after the install, before any change or setting

---

### Post by capscrew on 2009-04-29
The smb daemon is run by root.  It is only when a user requests smb services that the smbd (daemon) spawns (forks) a new child process.  See below:

>  A session is created whenever a client requests one. Each client gets a
        copy of the server for each session. This copy then services  all  con&#8208;
        nections  made  by the client during that session. When all connections
        from its client are closed, the copy of the server for that client ter&#8208;
        minates.
 

You can see this behavior by opening a share and then checking the processes, like so:
```
ps -ef|grep smbd
```
When no shares are being browsed we have:
```
root      7936     1  0 20:15 ?        00:00:00 /usr/sbin/smbd -D
root      7940  7936  0 20:15 ?        00:00:00 /usr/sbin/smbd -D

```

If I browse a share as a guest the smbd is owned by a guest account I defined as *smbguest*.  If I browse a share where I am the only valid user then smbd is owned by *capscrew*. See below
```
root      8075     1  0 20:45 ?        00:00:00 /usr/sbin/smbd -D
root      8079  8075  0 20:45 ?        00:00:00 /usr/sbin/smbd -D
smbguest  8128  8075  0 20:48 ?        00:00:00 /usr/sbin/smbd -D
capscrew  8143  8075  0 20:50 ?        00:00:00 /usr/sbin/smbd -D

```

So we can have may users even if you are the only logged in user.

How did you install Samba?  How have you made the shares?  The reason I asked is the following excerpt from the smbd man pages:

> The  configuration  file, and any files that it includes, are automati&#8208;
        cally reloaded every minute, if they change.

**Edit**: The following is a listing of the daily cron jobs on my server.  See the one for Samba?
```
root@malibu:/home/bruce# ls -l /etc/cron.daily
total 60
-rwxr-xr-x 1 root root  311 2007-03-04 22:38 0anacron
-rwxr-xr-x 1 root root  219 2007-10-06 05:30 apport
-rwxr-xr-x 1 root root 8101 2009-04-17 09:30 apt
-rwxr-xr-x 1 root root  314 2007-09-15 02:25 aptitude
-rwxr-xr-x 1 root root  502 2007-05-15 02:47 bsdmainutils
-rwxr-xr-x 1 root root  473 2007-10-03 11:36 find
-rwxr-xr-x 1 root root  473 2007-12-12 05:19 find.notslocate.dpkg-new
-rwxr-xr-x 1 root root   89 2006-06-19 11:21 logrotate
-rwxr-xr-x 1 root root  954 2008-03-12 06:24 man-db
-rwxr-xr-x 1 root root  183 2008-03-08 10:22 mlocate
[COLOR="Red"]-rwxr-xr-x 1 root root  383 2007-12-17 23:28 samba[/COLOR]
-rwxr-xr-x 1 root root  453 2008-02-14 04:51 slocate
-rwxr-xr-x 1 root root 3295 2008-04-08 11:02 standard
-rwxr-xr-x 1 root root 1309 2007-09-17 13:54 sysklogd

```

In this case it is owned by root.  Are you positive that there are no spurious cron jobs?  They are all located at:
```
 ls -l /etc/ |grep cron

```

Especially```
 /etc/crontab
```

---

### Post by amadeus79 on 2009-04-29
Thanks for helping. 

Here is the output form my /etc/crontab file:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

And I checked my anacron fil at gedit /etc/anacrontab to. # /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

I can't see anything about samba here. Yes I have tried as both user and root. I have only used synaptic to install samba. And I mostly use places -> network in gnome. pretty standard ubuntu setup. I have not set any samba shares in smb.conf, since i use ssh a lot to.

Another output: 

root@amadeus-laptop:/home/amadeus# ps -ef|grep smbd
root      3047     1  0 11:18 ?        00:00:00 /usr/sbin/smbd -D
root      3063  3047  0 11:18 ?        00:00:00 /usr/sbin/smbd -D
root     24461 24363  0 12:05 pts/1    00:00:00 grep smbd

and:

amadeus@amadeus-laptop:~$ ls -l /etc/ |grep cron
-rw-r--r--  1 root root       395 2008-09-03 01:37 anacrontab
drwxr-xr-x  2 root root      4096 2009-04-24 13:35 cron.d
drwxr-xr-x  2 root root      4096 2009-04-27 19:48 cron.daily
drwxr-xr-x  2 root root      4096 2009-04-24 13:33 cron.hourly
drwxr-xr-x  2 root root      4096 2009-04-24 13:33 cron.monthly
-rw-r--r--  1 root root       724 2008-09-09 21:46 crontab
drwxr-xr-x  2 root root      4096 2009-04-24 13:39 cron.weekly

and at last: 

amadeus@amadeus-laptop:~$ ls -l /etc/cron.daily
total 60
-rwxr-xr-x 1 root root  311 2008-09-03 01:37 0anacron
-rwxr-xr-x 1 root root  219 2008-10-24 08:10 apport
-rwxr-xr-x 1 root root 8686 2009-04-17 06:27 apt
-rwxr-xr-x 1 root root  314 2008-09-02 14:50 aptitude
-rwxr-xr-x 1 root root  502 2007-12-12 14:59 bsdmainutils
-rwxr-xr-x 1 root root   89 2008-10-09 09:11 logrotate
-rwxr-xr-x 1 root root  954 2008-07-11 17:02 man-db
-rwxr-xr-x 1 root root  646 2008-06-26 16:17 mlocate
-rwxr-xr-x 1 root root 2149 2008-11-17 10:52 popularity-contest
-rwxr-xr-x 1 root root  383 2009-01-05 15:53 samba
-rwxr-xr-x 1 root root 1142 2009-02-26 07:23 spamassassin
-rwxr-xr-x 1 root root 3349 2008-09-09 21:46 standard
-rwxr-xr-x 1 root root 1309 2008-08-30 02:40 sysklogd

---

### Post by mrwolf on 2009-04-29
I installed samba from the install screen (I checked the box "samba").

even when I stop samba (sudo service samba stop) the message continue to appear each minute. before I had chance to configure anything in samba.

---

### Post by herda05 on 2009-04-29
This is happening to me on a fresh install with no configuration of samba or cron whatsoever.

The machine is a virtual running in vmware using NAT, so I don't think it's coming from anything trying to connect as the machine is essentially behind a firewall.

This has to be local to the machine, and since I didn't make any changes to cron, it would be something in the default install of samba on Ubuntu server 9.04

---

### Post by PinkFloyd102489 on 2009-05-03
It has to be something in cron, because it always happens at 12:25am for me.

Samba attempts to reload and it just kills all networking on the box until networking is restarted.

Here is cron.daily:
```

brandon@ubuntu-server:/etc/cron.daily$ ls
apache2  aptitude      logrotate  mlocate             samba     sysklogd
apt      bsdmainutils  man-db     popularity-contest  standard

```

And here's the contents of that samba file:
```

#!/bin/sh
#
# cron script to save a backup copy of /etc/samba/smbpasswd in /var/backups.
#
# Written by Eloy A. Paris <peloy@debian.org> for the Debian project.
#

BAK=/var/backups

umask 022
if cd $BAK; then
        # Make sure /etc/samba/smbpasswd exists
        if [ -f /etc/samba/smbpasswd ]; then
                cmp -s smbpasswd.bak /etc/samba/smbpasswd || cp -p /etc/samba/s$
        fi
fi

```


I chmodded that file -x, yet it seems to still be running, so I dont know if this is the cause or what.

---

### Post by protomucca on 2009-05-03
Hi, i have the same problem, my smbd restart (SIGHUP) after about 20 minuts (not ever the same interval). What can i do?

---

### Post by capscrew on 2009-05-04
How about tracking the cron jobs in syslog?  This can be done with the following command -```
grep cron /var/log/syslog | grep May
```
This displays all cron jobs for the month of May.  I get this -```
May  3 19:05:23 malibu anacron[4943]: Anacron 2.3 started on 2009-05-03
May  3 19:05:23 malibu anacron[4943]: Will run job `cron.daily' in 5 min.
May  3 19:05:23 malibu anacron[4943]: Jobs will be executed sequentially
May  3 19:05:24 malibu /usr/sbin/cron[4972]: (CRON) INFO (pidfile fd = 3)
May  3 19:05:24 malibu /usr/sbin/cron[4973]: (CRON) STARTUP (fork ok)
May  3 19:05:24 malibu /usr/sbin/cron[4973]: (CRON) INFO (Running @reboot jobs)
May  3 19:10:23 malibu anacron[4943]: Job `cron.daily' started
May  3 19:10:23 malibu anacron[5079]: Updated timestamp for job `cron.daily' to 2009-05-03
May  3 19:17:01 malibu /USR/SBIN/CRON[5112]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  3 20:51:33 malibu anacron[4942]: Anacron 2.3 started on 2009-05-03
May  3 20:51:33 malibu anacron[4942]: Normal exit (0 jobs run)
May  3 20:51:34 malibu /usr/sbin/cron[4971]: (CRON) INFO (pidfile fd = 3)
May  3 20:51:34 malibu /usr/sbin/cron[4972]: (CRON) STARTUP (fork ok)
May  3 20:51:34 malibu /usr/sbin/cron[4972]: (CRON) INFO (Running @reboot jobs)
May  3 21:17:01 malibu /USR/SBIN/CRON[5429]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  3 22:17:01 malibu /USR/SBIN/CRON[5701]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

@ PinkFloyd102489,

You should be able to confirm the specific cron activity by the time stamp in the syslog.  You should note that this could be be in the form of cron.daily /cron.hourly/or some such, or a script run by cron.

@ All,

How about an informal poll?  I have 2 Samba servers. What **exactly** are you running?   Version? Desktop or Server?  LAMP or not?  DHCP or manually configured IP addresses?

  I do not have this phenomenon with either of my Hardy (8.04) samba servers.  One is running on a desktop install and one is with a server install (with no other services).  I use it as a NAS.

**Edit**:  I have done some research and it seems there is an interrelationship between DCHP failing and the smbd daemon being reloaded.  I hate to use the term bug as it appears to be caused by misconfiguration.  I would never use Samba with DHCP and I only configure using the 
/etc/samba/smb.conf file.

So I would look to this as a solution.  Manual configuration of IP addressing ie:**NO DHCP** with Samba.  See the following [[COLOR="Blue"]**bug report**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/312157") and note the references to the smbd being reloaded.

I would also check the syslog for DHCP remarks at the time of the smbd reload.

---

### Post by PinkFloyd102489 on 2009-05-07
Here's what I get.

```


brandon@ubuntu-server:~$ grep cron /var/log/syslog | grep May
May  6 07:17:01 ubuntu-server /USR/SBIN/CRON[22184]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 08:17:01 ubuntu-server /USR/SBIN/CRON[22821]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 09:17:01 ubuntu-server /USR/SBIN/CRON[23300]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 10:17:01 ubuntu-server /USR/SBIN/CRON[23775]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 11:17:01 ubuntu-server /USR/SBIN/CRON[24322]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 12:17:01 ubuntu-server /USR/SBIN/CRON[24858]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 13:17:01 ubuntu-server /USR/SBIN/CRON[25394]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 14:17:01 ubuntu-server /USR/SBIN/CRON[25930]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 14:49:02 ubuntu-server /USR/SBIN/CRON[26192]: (root) CMD (/etc/webmin/cron/tempdelete.pl)
May  6 15:17:01 ubuntu-server /USR/SBIN/CRON[26482]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 16:17:01 ubuntu-server /USR/SBIN/CRON[26958]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 17:17:01 ubuntu-server /USR/SBIN/CRON[27433]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 18:17:01 ubuntu-server /USR/SBIN/CRON[27908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 19:17:01 ubuntu-server /USR/SBIN/CRON[28383]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 20:17:02 ubuntu-server /USR/SBIN/CRON[28858]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 21:17:01 ubuntu-server /USR/SBIN/CRON[29336]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 22:17:01 ubuntu-server /USR/SBIN/CRON[29896]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 23:17:05 ubuntu-server /USR/SBIN/CRON[30452]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 00:17:06 ubuntu-server /USR/SBIN/CRON[31028]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

The server was originally configured with DHCP, though I changed it to static. Since you mentioned DHCP, I killed of dhclient3, so I'll see how that does.

It's a LAMP server with Samba installed for NAS purposes.

---

### Post by capscrew on 2009-05-07
> 
The server was originally configured with DHCP, though I changed it to static. Since you mentioned DHCP, I killed of dhclient3, so I'll see how that does...


Is it wireless by any chance?

> Does anyone run **webmin**, ebox, etc? All are capable causing this.  I see you are running webmin.  Webmin scripts can fundamentally alter the Ubuntu distro.  This is why I asked.  Look for a webmin perl script running that would cause your problems. If this turns out to be the problem you will have hack the script to cure your problem.

---

### Post by PinkFloyd102489 on 2009-05-09
> **capscrew said:**
> Is it wireless by any chance?

  I see you are running webmin.  Webmin scripts can fundamentally alter the Ubuntu distro.  This is why I asked.  Look for a webmin perl script running that would cause your problems. If this turns out to be the problem you will have hack the script to cure your problem.

The samba problem was happening before I installed webmin. My server isnt wireless either.

---

### Post by gizm0 on 2009-05-10
I have the same problem. I keep getting "Reloading /etc/samba/smb.conf smbd only" every ~5 minute. I tried stopping samba service, but I still got the "error" message.

I installed samba during the install of Ubuntu server 9.04.

Anybody got ideas how to fix this problem?

---

### Post by cbrunet on 2009-05-12
This is caused by the script located in /etc/dhcp3/dhclient-enter-hook.d/samba . If you don't use a dynamic IP address, you probably can suppress that file without hurts.

---

### Post by capscrew on 2009-05-12
> **cbrunet said:**
> This is caused by the script located in /etc/dhcp3/dhclient-enter-hook.d/samba . If you don't use a dynamic IP address, you probably can suppress that file without hurts.

Interesting.  I have no experience with a server using dhcp.  Even with a reserved address.  You point out some unintended consequences.  That being said my desktop host has always been manually configured with a static IP address, but does have that very script installed.  I'm betting it's never been run.  :-)

On my server I see that same script.  I'm surprised.  I have manually configured the IP here too.  never a thought of DHCP.

To me this looks like another attempt by the Ubuntu dev' trying to provide "all things to all people".

I will say that whenever someone runs a server, and by that I mean server services they should be mindful of the fallout of convenience (dhcp).  

NO DHCP!  DHCP is for clients only.

Edit:  Now that that's been said.  I'll bet these problems are due to intermittent connections.  Since the script only runs as a preamble to requesting a new IP address.

---

### Post by Gimpy_Rob on 2009-05-13
> **capscrew said:**
> 
NO DHCP!  DHCP is for clients only.


Not true.

I run my server under DHCP, but I hand out static releases to them based on MAC.  It's a bit odd, but it really works well for me, as I only have to mess with the DHCP to change my entire IP layout, not mess with each server.

That said, I was having the EXACT same issue, not as often, but probably on par with ever hour?  It is annoying because sometimes I leave something on the screen I want to come back to, but these messages will fill up the display.

So I checked my DHCP server, and, leases are an hour long! Imagine that!
I changed the leases for static IPs to 24 hours, but I;d still get the message once a day, so...

I added > /dev/null to the reload call, making it:
[ -x /etc/init.d/samba ] && /usr/sbin/invoke-rc.d samba reload > /dev/null

Problem fixed.  Somebody MIGHT want to mention this to the proper dev though, as it's new in 9.04, and annoying.


To all the people complaining about this killing the network on your server, this is a symptom, not the cause of the problem.  If the frequency does not match your DHCP lease, you have another problem, look into that first.

---

### Post by capscrew on 2009-05-13
> **Gimpy_Rob said:**
> Not true.

@ Gimpy_Rob,

I think you took my statement out of context and for sure *not* as I meant it.  I understand your position completely.  It was not a true or false statement, it was more a subjective stance.  Why; because the less that can go wrong the better off the sysadmin will be in the long run.  As evidenced by your having to modify the system to resolve the issue. > 

I run my server under DHCP, but I hand out static releases to them based on MAC.  It's a bit odd, but it really works well for me, as I only have to mess with the DHCP to change my entire IP layout, not mess with each server.
Actually its not as odd as you would think.  I have rebuilt many classroom subnets at the end of each semester.  The mandate from the university was to retain the same IP address on all workstations. I used DHCP for the exact same reason way as you.  

> 

That said, I was having the EXACT same issue, not as often, but probably on par with ever hour?  It is annoying because sometimes I leave something on the screen I want to come back to, but these messages will fill up the display.

So I checked my DHCP server, and, leases are an hour long! Imagine that!
I changed the leases for static IPs to 24 hours, but I;d still get the message once a day, so...

I added > /dev/null to the reload call, making it:
[ -x /etc/init.d/samba ] && /usr/sbin/invoke-rc.d samba reload > /dev/null

Problem fixed.  Somebody MIGHT want to mention this to the proper dev though, as it's new in 9.04, and annoying.

I think it is great that you found a *cure for the symptom*.  But even having a problem like this supports my notion. No more processes than what is needed.  In the long run,  how many times do you reconfigure your IP addressing structure?  I have installations that have the same IP schema that they started with 15 or so years ago.
> 

To all the people complaining about this killing the network on your server, this is a symptom, not the cause of the problem.  If the frequency does not match your DHCP lease, you have another problem, look into that first.

So let me rephrase my initial statement.  Use only what you need to to get the job done.  remember 2 things; just because you can do something doesn't mean you should do it and KISS.

-Cappy

---

### Post by PinkFloyd102489 on 2009-05-14
Killing off dhclient3 fixed the problem for me.

---

### Post by gedinbangkok on 2009-05-26
Killing off the DHCB processes worked for me after having this problem. 

On a server I had to first review the active processes, to get the PID and then kill the two processes that were running.

So it was 

ps -e |more

Then review the list for dhcp, and I observed two 

sudo kill 2137 2139

where 2137 and 2139 were the PID's of the processes.

Now I no longer have the recurring message "Reloading /etc/samba/smb.conf smbd only"

:D:D

---

### Post by spacepickle on 2009-05-29
I kept getting this message too. My issue was related to the fact that I had disconnected network interfaces and was starting dhclient without specifying the interfaces that were to use dhcp. By doing this, dhclient tries to work dhcp magic on ALL interfaces. Obviously it can't on the disconnected ones but would retry every five minutes.

The solution was to specify the interface: i.e. dhclient wlan0

It seems you can also specify the interfaces in the /etc/dhcp3/dhclient.conf file but I haven't gotten round to this yet.

This may be specific to my config as the wlan0 interface is using wpa_supplicant which seems to create a wmaster interface (I have no idea what this is and as it all works for the moment I have little desire to go figure).

Don't know if this is related to the original post or if they were talking about a much less frequent message. Every five minutes is just enough to irritate. If it did it once a day, I can live with that. And I haven't experienced network drops.

Hope it helps though.

Cheers.

---

### Post by LRT on 2009-06-09
this is also happening to me on a fresh install of 9.04 server. the only software i selected to be installed during the OS installation was samba and ssh. this message (*Reloading /etc/samba/smb.conf smbd only) is happening every 3-5 minutes.. this message began occurring as soon as the install was finished and i logged in for the first time. i have also ran all software upgrades but the message is still occurring.

so far this posting has not provided any real solutions.. does anyone else have an idea on how to fix this?

---

### Post by LRT on 2009-06-09
i believe this problem has something to do with dhclient. upon further investigation i found that dhclient requests are happening at the EXACT same time that the smbd reloading occurs. /var/log/samba/log.smbd shows reloading at the EXACT same time as /var/log/syslog shows dhclient requests... 

obviously the two are related and one is causing the message "*Reloading /etc/samba/smb.conf smbd only" to appear on the command line every 5 minutes.

this is why killing dhclient probably solves the problem, but this is hardly a solution...

does anyone have any ideas?

---

### Post by spacepickle on 2009-06-11
As I mentioned before, dhclient will operate across all interfaces that it can. If one of the interfaces can't get a dhcp result, it will repeatedly try again. Samba will reload it's config on any change to the machines network connections, including a non-result from dhclient. 

These are the right behaviours. You want dhcp to retry obtaining an address oninterfaces that  previously didn't work. And samba needs to be reconnected on interfaces that change.

If you set dhclient to run against the specific interfaces that WILL use dhcp, the frequency of the message will be reduced to once each time the dhcp lease is renewed (for me, once a day). I can't provide help on where to achieve this as I manually start dhclient and instead of just running "dhclient",I now run "dhclient wlan0". 

If even once a day is too much, or you cant specify the interfaces that will always get a dhcp result, then the message needs to be directed somewhere other than the stdout. 

If you want a distribution-based fix, i have no idea. 

However, if you want a quick hack to get rid of the message: A bit of debug work finds that the message is produced in /etc/lsb-base-logging.sh There is a function called log_daemon_msg starting on line 71. On line 108 it says 
   echo " * $@"

I've changed it to:
   echo " * $@" >> /var/log/daemon.log 2>&1

(that is, append the message, along with any errors, to the daemon log)

This is a total hack: i probably shouldn't write this stuff (at least in this format) to this log file but I would rather not try to create a specific log for this or send it to the void with /dev/nul (other daemon proccesses may use this function for stuff I DO care about).

Let me know if this works for you or if you want a more complete solution?

---

### Post by LRT on 2009-06-11
> As I mentioned before, dhclient will operate across all interfaces that it can. If one of the interfaces can't get a dhcp result, it will repeatedly try again. Samba will reload it's config on any change to the machines network connections, including a non-result from dhclient.

These are the right behaviours. You want dhcp to retry obtaining an address oninterfaces that previously didn't work. And samba needs to be reconnected on interfaces that change.

i only have 1 interface (eth0) and its IP address is set using DHCP, however, it is assigned statically through its MAC address by a separate DHCP server machine. this address should never change which is why i still don't understand why samba decides to reload after each dhcp lease request.

> If you set dhclient to run against the specific interfaces that WILL use dhcp, the frequency of the message will be reduced to once each time the dhcp lease is renewed (for me, once a day). 

i don't know how or where to do this :( do i have to setup an alias{} in dhclient.conf ?

> If you want a distribution-based fix, i have no idea. 
I think a distribution-based fix is what we need because this is happening off a fresh installation!

> 
However, if you want a quick hack to get rid of the message: A bit of debug work finds that the message is produced in /etc/lsb-base-logging.sh There is a function called log_daemon_msg starting on line 71. On line 108 it says
echo " * $@"

I've changed it to:
echo " * $@" >> /var/log/daemon.log 2>&1

this DOES suppress the message from stdout and i can see that daemon.log is in fact logging the message. however, i'm curious if this constant reloading of smbd has an effect on connectivity with the samba shared folders??? that would be a bad thing.

---

### Post by Jim Darrough on 2009-07-04
Ok folks, for an inexperienced person. I installed 9.04 server, and used ebox to set up Samba. And I have exactly the same problems with periodic samba reload. I have set up my router to always supply the server with the same IP address. I killed dhclient process. 

All I want is a fileserver (nas), and nothing more. Is 8.04 as comes with the ebox iso install disk a better idea for this? I would rather NOT put all the extra stuff that I am not going to use on this box, and I read in the ebox forums that the installer installs 8.04 with the latest ebox with ALL options "turned on".

At this point it would seem to me that going to 8.04 server with ebox is a better idea. What say you?

---

### Post by petersk on 2009-07-04
Been watching the thread for a "real" solution... Does anyone have one yet?   I tried apt-get remove dhcp-client and it turns out that supposedly it wasn't installed.  So that didn't help.
Kurt

---

### Post by capscrew on 2009-07-04
> **Jim Darrough said:**
> Ok folks, for an inexperienced person. I installed 9.04 server, and used ebox to set up Samba.
This problem is not a Samba problem.  It is a DHCP problem.>  

And I have exactly the same problems with periodic samba reload.
Are your sure?  I would check the system logs (as described in this thread) for confirmation.> 

I have set up my router to always supply the server with the same IP address. I killed dhclient process. 
This can't be.  If you have truly "set up my router to always supply the server with the same IP address", then by definition it is a DHCP server and will only give out an address (reserved or not) when the client requests an address. That's the protocol.> 

All I want is a fileserver (nas), and nothing more. Is 8.04 as comes with the ebox iso install disk a better idea for this? I would rather NOT put all the extra stuff that I am not going to use on this box, and I read in the ebox forums that the installer installs 8.04 with the latest ebox with ALL options "turned on".
I run 8.04 with Samba as a NAS and it works great.  I have manually configured the static IP address at /etc/network/interfaces.  I believe that 9.04 would work fine too.  

If you have a DHCP server supplying the IP address, then it is leased via DHCP from a pool or a reserved address (permanently the same).  This is what is causing your symptom.> 

At this point it would seem to me that going to 8.04 server with ebox is a better idea. What say you?
I feel you will be best served by removing Network Manager (nm-applet), the dhcp client on your Samba/NAS and  manually configuring the IP address.

---

### Post by windependence on 2009-07-05
I agree with Cappy here. I almost never use DHCP on my servers, and even sometimes not on my clients when I don't want users just plugging in devices on the network but don't want port security turned on.

As to Jim's question about eBox, I'm not tryin to be funny or nasty here but this IS the server forum so I'm going to say the correct solution is to learn the command line pure and simple. If you want to monitor the server via GUI, you can certainly run Nagios or something similar, but IMHO config should be done via CLI. You don't need to use VI, I myself use Pico or Nano, but CLI knowledge is critical if you are properly running a server.

-Tim

---

### Post by Terc on 2009-09-11
Alright, so here's my situation

I'm using a 3G data card on a "portable file server".  This server must acquire a dhcp lease from the 3g card, which is only used for internet access.

Clients connect through 4 other NICs which are all handing out dhcp leases.  The internal IP of the file server is static, but obviously killing dhclient3 is not an option for me.

Getting this error every 5 minutes or so.  Obviously this is bad since the clients lose their connection to a working file server.

So.. what can I do?  Please, please help!

---

### Post by capscrew on 2009-09-11
> **Terc said:**
> Alright, so here's my situation

I'm using a 3G data card on a "portable file server".  This server must acquire a dhcp lease from the 3g card, which is only used for internet access.
What's a "portable file server"? and why would it need internet access?> 

Clients connect through 4 other NICs which are all handing out dhcp leases.  
NIC's don't hand out DHCP leases.  IP addresses can be assigned to NIC's by a DHCP server.  Do you have a DHCP server somewhere in your LAN?> The internal IP of the file server is static, but obviously killing dhclient3 is not an option for me.
If the "IP of the file server is static", why do you need the dhclient3?  Do you mean that the IP is always the same.  Is that a MAC filtered, reserved address handed out by the DHCP server?  Static implies that the IP address is manually configured.> 

Getting this error every 5 minutes or so.  Obviously this is bad since the clients lose their connection to a working file server.
The reload is due to the lease time being so short.>   

So.. what can I do?  Please, please help!

Have you thought of increasing the lease time?  I believe this has been mentioned by earlier posters in this thread

---

### Post by muellmaen on 2009-09-23
> **capscrew said:**
> What's a "portable file server"? and why would it need internet access? 

Why portable ? In some regions it is cheaper to use a UMTS (3G) access when using a fixed broadband or you might only have UMTS but nothing else. 

This bug even gets on you if your server is connected to a ISP who only offers a dynamic IP. In that case, you have no chance to change lease times.

In such a case this bug seems to me to be critical as most servers run samba and until now we could not find here a solution. In the case that your server is getting his IP from a local DHCP, this problem is at least annoying.

---

### Post by capscrew on 2009-09-23
> **muellmaen said:**
> Why portable ? In some regions it is cheaper to use a UMTS (3G) access when using a fixed broadband or you might only have UMTS but nothing else. 

I'm not familiar with UMTS as an WAN connection.  But, nerver the less, the connection should only be the the WAN (ISP) side of the router, not the LAN side.    
> 

This bug even gets on you if your server is connected to a ISP who only offers a dynamic IP. In that case, you have no chance to change lease times.

This does not sound like a "bug" to me.  Rather a misapplication or misconfiguration of technology.  I run 2 Samba servers on a small LAN that is serviced by a DHCP served WAN side connection with no problems at all.  Both servers have manually configured static IP addresses.> 

In such a case this bug seems to me to be critical as most servers run samba and until now we could not find here a solution. 

That does not mean there isn't one.
> 

In the case that your server is getting his IP from a local DHCP, this problem is at least annoying.

Local DHCP in itself is not really the problem.  Have you considered a "reserved" address?  This and infinite lease times should mitigate the problem.  Once again, if it is truly a "local" DHCP server, the the systems/network administrator should be able to configure the servers IP address manually for a static IP address on the local subnet.

Are you using "network-manager" (NM-applet) to manage your connections?  Are you using Ubuntu Server?  How have you configured Samba?  What is the topology of the network?

---

### Post by muellmaen on 2009-10-02
Hi,

seems to be on its way.

Chuck Sort is working on it !

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/435061](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/435061)

hopefully it is fixed with final Karmic.

Thanks Chuck !

---

### Post by aaronchall on 2009-11-15
> **muellmaen said:**
> Hi, seems to be on its way. Chuck Sort is working on it !
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/435061](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/435061)
hopefully it is fixed with final Karmic.
Thanks Chuck !
 
It seems like this hasn't been fixed, since I'm seeing this bug on my new box.  The link gives two workarounds, but I don't know how to implement them.  Any help for a noob who's trying to set up his own network attached storage (NAS)?

Thanks

Aaron

---

### Post by capscrew on 2009-11-16
> **aaronchall said:**
> It seems like this hasn't been fixed, since I'm seeing this bug on my new box.  The link gives two workarounds, but I don't know how to implement them.  Any help for a noob who's trying to set up his own network attached storage (NAS)?

Thanks

Aaron

All of the answers are in this thread.  See posts 20, 22, 31, 31.

No DHCP (or NM) on any server hosting Samba.  The fact that the DHCP release times are NOT compatible with how Samba operates is not even on Samba.org's radar.

---

### Post by aaronchall on 2009-11-16
> **capscrew said:**
> All of the answers are in this thread.  See posts 20, 22, 31, 31.

No DHCP (or NM) on any server hosting Samba.  The fact that the DHCP release times are NOT compatible with how Samba operates is not even on Samba.org's radar.

So, and again, total noob here, how do I not use DHCP (I suppose I statically assign an IP address, and would i do that at the server, or the router, or... how? and what parameters?)?  Or Kill dhclient3?  And post 20, where he says he edited something or other, how do you do that?

---

### Post by capscrew on 2009-11-16
> **aaronchall said:**
> So, and again, total noob here, how do I not use DHCP...
The proper (and most elementry) way is to manually configure the interface (the NIC (e.g the Ethernet card).  This is not as hard as you would think.> 
... (I suppose I statically assign an IP address, and would i do that at the server, or the router, or... how? and what parameters?)?  Or Kill dhclient3?  And post 20, where he says he edited something or other, how do you do that?

Let me explain why DHCP is a bad idea, then what to do will be a little clearer.  

The box that is hosting Samba needs to have a fixed (always the same) IP address.  When clients of Samba look for it (make or continue connectivity) it is at the same IP address.  

In addition Samba (smbd) internally needs to know the IP address it is listening on.  When it changes the Samba must reload to use the new IP address.  Imagine what it would be like if every time you wanted to go to your bank you found it had moved.  That would make it harder for you to stay in contact with the bank.

The box (host) asks (is the client) for the address from the DHCP server (typically the router) and the DHCP server responds by issuing an IP address.  If you manually configure the IP address on the interface then there will be no request.  Now with no need a DHCP request you can turn off the dhclient3.  In addition you don't need to modify anything as mentioned in post #20.

All of this is basic TCP/IP networking.  I would Google the terms "*TCP/IP networking"*.  There is plenty of information out there.

Now we are down to; *"how do I do that?"*  The first thing is to decide what the parameters for the network should be.  What address is the DHCP server handing the host (your box) now?  This will give you the parameters of the network.  To get this information do this from the CLI (terminal)```
ifconfig -a
```Here is what I get.```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:04:76:cd:54:e0  
          [COLOR="Red"]inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::204:76ff:fecd:54e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1474342 (1.4 MB)  TX bytes:128334 (125.3 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43900 (42.8 KB)  TX bytes:43900 (42.8 KB)

```The important parts are in red.

The config file for the interface is ```
/etc/network/interfaces
```To view it use```
cat /etc/network/interfaces
``` This is the file you need to configure the static IP address.  Mine looks like this.```
cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# [COLOR="Red"]The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1[/COLOR]

```One last piece of information needed is the IP address of the DNS server for you network.  This is described in the file ```
/etc/resolv.conf
```Here is mine```
cat /etc/resolv.conf
 
# Local DNS
nameserver 192.168.1.1

```

The steps are harder to write out than they are to configure.  Here is a condensed list:

1. Find out the IP addressing scheme, default gateway, and DNS server you are using right now.

2. Configure the **/etc/network/interfaces** file 

3. Configure the **/etc/resolv.conf** file

For a noob this is a lot of information to digest and understand.  Find you network information and post it here.  I will help you configure the interface.

One last question, and I hate to ask; is this a desktop OS or a server OS we are talking about (i.e Does it have a GUI interface)?

---

### Post by aaronchall on 2009-11-17
Thank you so much for the detailed reply!  It's the server OS, so no GUI, and anything that slightly resembles a GUI is crashing almost immediately, since it only has 256 megs of RAM.  

I won't have time for a couple of days to do this, BUT I will be right back at it come Thursday, with all likelihood.  Thank you so very very very much!

Aaron

---

### Post by capscrew on 2009-11-17
> **aaronchall said:**
> Thank you so much for the detailed reply!  It's the server OS, so no GUI, and anything that slightly resembles a GUI is crashing almost immediately, since it only has 256 megs of RAM. 
Hmmmmm, I have a Hardy (8.04) desktop that runs Gnome.  It's a P3 with 352 MB of RAM.  The system is slow but it works,  Your Server with no GUI should be fine.>  

I won't have time for a couple of days to do this, BUT I will be right back at it come Thursday, with all likelihood.  Thank you so very very very much!

Aaron

I'll be here if you need help.

---

### Post by aaronchall on 2009-11-20
Capscrew, thanks so much for offering to help me.
 
ifconfig -a 
gives: 
...
inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
...
 
cat /etc/network/interfaces 
gives:
...
# The primary network interface
auto eth0
iface eth0 inet dhcp
 
cat /etc/resolve.conf
gives:
nameserver 192.168.2.1
 
So how do I edit that file?  VIM?  I'm not very good with VIM, but I'll try...
 
Once again, no GUI, just command line.
 
Aaron

---

### Post by capscrew on 2009-11-20
> **aaronchall said:**
> Capscrew, thanks so much for offering to help me.
 
ifconfig -a 
gives: 
...
inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
...
 
cat /etc/network/interfaces 
gives:
...
# The primary network interface
auto eth0
iface eth0 inet dhcp
 
cat /etc/resolve.conf
gives:
nameserver 192.168.2.1
 
So how do I edit that file?  VIM?  I'm not very good with VIM, but I'll try...
 
Once again, no GUI, just command line.
 
Aaron

We don't need to use VIM if you don't want to.  I'll bet that the editor NANO is installed.  In VIM we have modes.  One to view the text and one to edit the text.  This is what drives user nuts.  I have been using it for yers and I don't even think about it.  but nano is a simple editor and the basic commands are always at the bottom of the screen.

To check if nano is installed try this (always at the CLI)```
type nano
``` This is what I get```
type nano
nano is /usr/bin/nano

```

If you get this response then NANO is installed.

Do you know where your dhcp server is?  is it on the router?  We need to determine how many addresses (the range) are in the pool of addresses available.  We need to avoid this range or reduce the range.

---

### Post by aaronchall on 2009-11-21
I have nano, type nano gives 
nano is hashed (/usf/bin/nano)
 
I have no idea where my dhcp server is, but I assume it's the router, a US Robotics Wireless MAXg Router, to which my desktop server is connected by wire, which then connects to the cable modem and out... do I need to login to my router to do it?
 
Aaron

---

### Post by capscrew on 2009-11-21
> **aaronchall said:**
> I have nano, type nano gives 
nano is hashed (/usf/bin/nano)
 
I have no idea where my dhcp server is, but I assume it's the router, a US Robotics Wireless MAXg Router, to which my desktop server is connected by wire, which then connects to the cable modem and out... do I need to login to my router to do it?
 
Aaron

I'm pretty sure that this is were it is.  I would log into it and look for a section that has the DHCP setings (automatic IP addressing or some such).  Just look (DON"T CHANGE ANYTHING).  We need to know the range.  Only to avoid manually configuring the server with an address that is in the DHCP pool.

The work is in the prep (design) not in the actual editing of the files.  :-)

Edit:  I found it.  From the manual```
IP range: The IP range of DHCP server also depends on the LAN subnet mask of the router. 
The default range is 192.168.2.2 to 192.168.2.31.

To specify a different range for IP addresses, 
select IP address range and enter the starting 
and ending IP address.
```

See [**_[COLOR="DarkSlateGray"]this web page[/COLOR]_**]("http://www.usr.com/support/5465/5465-ug/lan.html") for more complete information.  This section is for the configuration tab >>LAN settings.

---

### Post by aaronchall on 2009-11-21
I verified, I have the defaults 192.168.2.2 to 192.168.2.31. I could easily narrow this, since my wife and my laptop are the only ones accessing wirelessly, in fact, maybe I should narrow it for security?
 
Going to bed, wife is insisting... :)

---

### Post by capscrew on 2009-11-21
> **aaronchall said:**
> I verified, I have the defaults 192.168.2.2 to 192.168.2.31.  I could easily narrow this, since my wife and my laptop are the only ones accessing wirelessly, in fact, maybe I should narrow it for security?

No need to.  We have 254 IP addresses that we can use.

I usually pick something memorable.  Such as: *all servers must be in the .100 range*.  So I would make your server 192.168.2.100.

First thing to do is make a copy of the /etc/network/interfaces file.  To do this we will issue this command ```
sudo cp /etc/network/interfaces /etc/network/interfaces.original
```

Note: there is a space between /etc/network/interfaces and /etc/network/interfaces.original.

You can check your work with this command ```
ls -l /etc/network
```

Do you see the copy?

---

### Post by aaronchall on 2009-11-21
I see the copy!
 
Aaron
 
PS EDIT 
Because I'm presuming we're editing the interfaces file, I typed in 
nano /etc/network/interfaces
 
I now have nano up with the file open...
 
PPS Edit
So I'm commenting out the last two lines so they read 
"# auto eth0
# iface eth0 inet dhcp"
and putting below them:"
iface eth0 inet static
address 192.168.2.32" (the last number could be 100 or any number from 32 to 255? this is the server, right?)"
netmask 255.255.255.0
gateway 192.168.2.1 " (is the last number here right? did I transpose them? is this supposed to be the router?)
 
PPPS edit
and I'm reopening the file with sudo since it won't let me save... and reediting as described...
and saving with ctrl-O,
saved and exited...
 
now on the command line... I'll report if I keep seeing the error...
 
PPPPS edit (boy, that a lot of post scripts...)
I'm testing the internet connection with "ping google.com" and it seems to be working...
 
PPPPPS AUGGHHHH!!!!
"
* Reloading /ect/same/smb.conf smbd only
"
So now I'm opening /etc/samba/smb.conf with nano just to look at it and see what I can learn...

---

### Post by capscrew on 2009-11-21
> **aaronchall said:**
> I see the copy!
 
Aaron
 
PS EDIT 
Because I'm presuming we're editing the interfaces file, I typed in 
nano /etc/network/interfaces
 
I now have nano up with the file open...

This this a root owned file so you need to open it with ```
sudo nano <file>
```> 
 
PPS Edit
So I'm commenting out the last two lines so they read 
"# auto eth0
# iface eth0 inet dhcp"
and putting below them:"
iface eth0 inet static
address 192.168.2.32" (the last number could be 100 or any number from 32 to 255? this is the server, right?)"
netmask 255.255.255.0
gateway 192.168.2.1 " (is the last number here right? did I transpose them? is this supposed to be the router?)
You can't use the .255 number.  Any number beyond .31 up to .254 is appropriate.> 

 
PPPS edit
and I'm reopening the file with sudo since it won't let me save... and reediting as described...
and saving with ctrl-O,
saved and exited...
Uh huh...> 
 
now on the command line... I'll report if I keep seeing the error...

The network parses the configuration file ***before ***the interface comes up.  This is how the system knows what the parameters are.  You need to RESTART the networking with this command ```
sudo /etc/inid.d/networking restart
```Now we will check to see if the configuration is what we want.  This is the command to see if it is correct```
ifconfig -a
``` 
> 
 
PPPPS edit (boy, that a lot of post scripts...)
I'm testing the internet connection with "ping google.com" and it seems to be working...
 
PPPPPS AUGGHHHH!!!!
"
* Reloading /ect/same/smb.conf smbd only
"
So now I'm opening /etc/samba/smb.conf with nano just to look at it and see what I can learn...

Don't do that.  There is nothing in Samba that needs changing for this problem.

---

### Post by aaronchall on 2009-11-21
> **capscrew said:**
>  ```
sudo /etc/inid.d/networking restart
``` 
 
I'm assuming this is 
```
 
sudo /etc/init.d/networking restart

```
?
 
> **capscrew said:**
> 
Now we will check to see if the configuration is what we want. This is the command to see if it is correct```
ifconfig -a
``` 
 
So when I did the restart command as I noted, I got an error after > *Reconfiguring network interfaces... and I don't remember what it said, because it scrolled off when I did ```
ifconfig -a
```
 
which gives 
> eth0 _ Link encap: Ethernet HWaddr 00:d0:e8:0f:06:bd
[INDENT]inet addr: 192.168.2.4 Bcast:192.168.2.255 Mask:255.255.255.0
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:2721 errors:0 dropped:0 overruns:0 frame:0
TX packets:1633 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2290472 (2.2 MB) TX bytes:187308 (187.3 KB)
Interrupt:17 Base address:0x3000
[/INDENT]lo __ Link encap:Local Loopback
[INDENT]inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16437 Metric:1
RX packets:400 errors:0 dropped:0 overruns:0 frame:0
TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes 24000 (24.0 KB) TX bytes:24000 (24.0 KB)
[/INDENT]and ping gives> 
$ ping google.com
ping: unknown host google.com


---

### Post by aaronchall on 2009-11-21
[quote=capscrew]
 
Aaron,
 
I think we should work out the errors here rather than at the public page. It will just add extra pages of chit chat not relevant to the original smb reload problem.
 
The interface has not been updated with the new configuration.
 
Post me here the results of these 2 commands```

cat /etc/network/interfaces
 
route

```[/quote] results are >  #The loopback network interface
auto lo
iface lo inet loopback
 
#The primary network interface
# auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.2.32
netmask 255.255.255.0
gateway 192.168.2.1
 
route 
 
Kernal IP routing table
Destination __Gateway ____Genmask ____Flags__ Metric Ref Use Iface
192.168.2.0 __* __________255.255.255.0 _U____ 0 ____0 __0 __eth0
default ___192.168.2.1 ____0.0.0.0 ______UG ____100 __0 __0 __eht0

 
> We also need the error messages from the reload. This will take multiple commands if you can't read the data.
 
These are (with #comments)from your home directory --```
touch reload  #this creates the reload file
# The following puts the errors in the file
sudo /etc/init.d/samba reload > /home/<your_login>/reload
 
cat reload   #puts the data on the screen

```
 
PM me if you do not understand
 
-Bruce
 
I think I understand, but the thread lets me see what you're saying while I'm responding, so can we continue to use the thread? Also, those commands didn't seem to do anything, and whenever I reload samba, it doesn't give the error from the first time I did it, but pings still don't work.
 
I'm going to put this back on the thread so I can see it all...

---

### Post by capscrew on 2009-11-21
un-comment the this ```
# auto eth0
``` in the /etc/network/interfaces and reload.

---

### Post by aaronchall on 2009-11-21
> **capscrew said:**
> un-comment the this ```
# auto eth0
``` in the /etc/network/interfaces and reload.
 
OK, did it, saved, and did```
sudo /etc/init.d/samba reload
* Reloading /etc/samba/smb.conf smbd only
``` and on ```
sudo /etc/init.d/networking restart 
*Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory 
```
 
This is the missing error message I got earlier. 
 
Aaron
 
PS, still getting the * Reloading /etc/samba/smb.conf smbd only message every so often.
It seems to be coming more frequently than the router's lease period, which is 1 hour, if that makes any difference, though it just turned 10:00.  Maybe time is passing faster than I'd like...

---

### Post by capscrew on 2009-11-21
> **aaronchall said:**
> OK, did it, saved, and did```
sudo /etc/init.d/samba reload
* Reloading /etc/samba/smb.conf smbd only
``` and on ```
sudo /etc/init.d/networking restart 
*Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory 
```
 
This is the missing error message I got earlier. 

This has to do with your email.  I'm interested only in the IP address settings on the Ethernet interface at this point. 

If the */etc/networking/interfaces* is correct (re-post the settings here) then when we restart the networking it should get the IP address we have supplied via that file.  We can check by issuing the *ipconfig a* command.  So what are we getting now?  There is no need to wait to see if you are getting the ** Reloading /etc/samba/smb.conf smbd only* message.

The drilis is:
edit the /etc/network/interfaces file
reload networking 
check settings with the ifconfig -a command

This should be a 5 minute routine.

If you wish you can reboot the server and check the settings.  
> 
 
Aaron
 
PS, still getting the * Reloading /etc/samba/smb.conf smbd only message every so often.
It seems to be coming more frequently than the router's lease period, which is 1 hour, if that makes any difference, though it just turned 10:00.  Maybe time is passing faster than I'd like...

---

### Post by aaronchall on 2009-11-22
OK, I rebooted, and it seems to be working now! At least it's pinging google.com.
 
 
But that doesn't really make sense, because Linux is supposed to be configurable without rebooting. What's up with that?
 
PS ifconfig -a gives me 
 
inet addr:192.168.2.32 
 
I think that's what we were going for?  What else should I do?
 
Aaron

---

### Post by capscrew on 2009-11-22
> **aaronchall said:**
> OK, I rebooted, and it seems to be working now!  At least it's pinging google.com.
 
 
But that doesn't really make sense, because Linux is supposed to be configurable without rebooting.  What's up with that?

At this point we need to be pragmatic.  Who cares why we needed to reboot.

So now we need to STILL...confirm the settings.  What is the output of the command```
ifconfig -a
```

Use the # symbol at the top right of the advanced screen to wrap the data in code brackets for easier reading.

BTW -- I'll bet your mail server doesn't work now.

Edit:  It would be good to ping the server from another machine on your network to see if it will respond too.

---

### Post by aaronchall on 2009-11-22
> **capscrew said:**
> At this point we need to be pragmatic. Who cares why we needed to reboot.
 
So now we need to STILL...confirm the settings. What is the output of the command```
ifconfig -a
```
 
Use the # symbol at the top right of the advanced screen to wrap the data in code brackets for easier reading.
 
BTW -- I'll bet your mail server doesn't work now.
 
Edit: It would be good to ping the server from another machine on your network to see if it will respond too.
 
Ping from another machine shows it is there!  I don't know anything about mail... I just want to use the machine as network attached storage, and perhaps remotely accessible storage.
 
ifconfig a- 
eth0 Link encap:Ethernet HWaddr 00:d0:e8:0f:06:bd
inet addr:192.168.2.32 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::2d0:38ff:fe0f:6bd/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:32 errors:0 dropped:0 overruns:0 frame:0
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4423 (4.4 KB) TX bytes:12335 (12.3 KB)
Interrupt:17 Base address:0x3000

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes 480 (480.0 B) TX bytes:480 (480.0 B)

---

### Post by capscrew on 2009-11-22
Then we are good to go; right?

If you installed any server packages then postfix might have gotten installed without you realizing it.

Now the only question you should need to check out is the DNS listing for this machine.  Before it was most likely automatically picked up by the router based DNS server.  Now you will need to add it manually to the DNS database.

This VERY off topic, so I would start another thread (and PM me with the title).

---

### Post by aaronchall on 2009-11-23
Thanks Cap, I would have had to read 2 or 3 books to figure this out on my own.

Woo hoo! static IP!

Aaron

---

### Post by noblow91 on 2009-11-24
It seems that if you don't want to see the message any more all you have to do is comment out 2 lines in /etc/init.d/samba

the 2 lines that need to be commented are:

log_daemon_msg "Reloading /etc/samba/smb.conf" "smbd only"

and...

 log_end_msg 0

---

### Post by capscrew on 2009-11-24
> **noblow91 said:**
> It seems that if you don't want to see the message any more all you have to do is comment out 2 lines in /etc/init.d/samba

the 2 lines that need to be commented are:

log_daemon_msg "Reloading /etc/samba/smb.conf" "smbd only"

and...

 log_end_msg 0

Right you are **noblow91**.  But this only suppresses the console messages.  It does nothing to mitigate the effects of the smbd daemon reloading.  Users have complained about dropping large file backups and streaming dropouts.  My guess is that the daemon reload is the culprit.

---

### Post by noblow91 on 2009-11-25
Ok, I added a new hard drive to my server last night and was forced to reinstall Ubuntu Server. After installation I noticed that my wireless was pre-configured with a static IP and for the past 13 hours I haven't gotten a single "Reloading /etc/samba/smb.conf smbd only" message. Maybe, going into your interfaces file and changing your default device from dhcp to static will help.

EDIT: sorry. I failed to read the previous page...

---

### Post by Uber-n00b on 2010-02-26
just wanted to chime in as I'm battling with same issues...

I'm running 9.10 Server, fresh install was DHCP and I had set up router to reserve an IP just for the particular machine. Was getting the **[FONT="Courier New"]* Reloading /etc/samba/smb.conf smbd only[/FONT]** about every 5-10 mins or so and it kept interfering with my SSH connections. Setting up /etc/network/interfaces file with static IP definitely changed the frequency with which that error msg was popping up. 

Also, I installed webmin. Couldn't identify problem though until I hooked up a monitor to box. When I came back from being away ~4 hrs and saw entire screen covered in this error msg, that's when I started hunting forums for help. So there's my system & symptoms if anybody's keeping score.

---

### Post by capscrew on 2010-02-27
> **Uber-n00b said:**
> just wanted to chime in as I'm battling with same issues...

I'm running 9.10 Server, fresh install was DHCP and I had set up router to reserve an IP just for the particular machine. Was getting the **[FONT="Courier New"]* Reloading /etc/samba/smb.conf smbd only[/FONT]** about every 5-10 mins or so and it kept interfering with my SSH connections. Setting up /etc/network/interfaces file with static IP definitely changed the frequency with which that error msg was popping up.

Did you turn off the DHCP client?  Is the [FONT="Courier New"]/etc/network/interfaces [/FONT]file being overwritten?  Are you running this host with wireless connection?  If you are you getting the error at any time you need look into remedies.
>  

Also, I installed webmin. Couldn't identify problem though until I hooked up a monitor to box. When I came back from being away ~4 hrs and saw entire screen covered in this error msg, that's when I started hunting forums for help. So there's my system & symptoms if anybody's keeping score.

What is the exact error message?

---

### Post by Uber-n00b on 2010-02-28
Lost ssh to server sometime in last 24 hrs. I'm sure its another **[FONT="Courier New"]* Reloading /etc/sabma/smb.conf smbd only[/FONT]** issue, but can't tell for sure right now since box is headless for time being. 

I changed server to static IP by first editing **[FONT="Courier New"]/etc/network/interfaces[/FONT]** and then executing following command:
```
sudo apt-get remove dhcp-client
```Got back something like, 'wasn't installed, so removing 0 packages.' Think i should have used [FONT="Courier New"]sudo apt-get remove dhcp-client**3**[/FONT] instead. Won't know for sure if etc/network/interfaces is being overwritten till I get a monitor and keys hooked up to it again, but will do ASAP.

> Are you running this host with wireless connection?Long story: Was trying to with a PCI wireless card. That was a nightmare and didn't work out. Pulled card out, set up a wireless repeater and plug in via ethernet to that now. Problem is, no matter if I'm plugged into the repeater (downstairs where I need it) or into the base station (upstairs in the neighbors' place) I'm getting the same [FONT="Courier New"]*** Reloading ... smbd only**[/FONT] mess. I can say that frequency is about 1 per day with only 1 network interface installed as opposed to 1 per 5 mins when I had the PCI card in too though. (This may be because of Static IP configuration though. Side Q: is it possible to set lease renew = never for static IP's? Do static IPs *ever* get renewed by definition? I ask because I'm wondering if that's why I'm still getting error, but at a lower frequency.)> What is the exact error message?**[FONT="Courier New"]* Reloading /etc/samba/smb.conf smbd only[/FONT]**.

---

### Post by capscrew on 2010-02-28
> **Uber-n00b said:**
> Lost ssh to server sometime in last 24 hrs. I'm sure its another **[FONT="Courier New"]* Reloading /etc/sabma/smb.conf smbd only[/FONT]** issue, but can't tell for sure right now since box is headless for time being. 
The Samba reloading thing could be simultaneous, but it has not direct bearing on SSH.  The message is displayed when the smbd (samba daemon) detects a change (in this case the renewal of the DHCP lease) and reloads the daemon.  When smbd is initially loaded it reads the smb.cof file.  This sets all of the parameters.  If there is a change in those parameters (or it thinks there might be a change) it reloads.

The original thought was to notify the computer operator.  When I first started out in the data center, my job was to watch for those changes and notify the systems operators.  If you were to suppress the output the reload would still be the same and you would not be bothered.  This was mentioned in earlier replies to this thread.

Once again your SSH problem may indeed have to do with the DHCP lease renewal, but it has nothing to do with the Samba daemon reloading.> 


I changed server to static IP by first editing **[FONT="Courier New"]/etc/network/interfaces[/FONT]** and then executing following command:
```
sudo apt-get remove dhcp-client
```Got back something like, 'wasn't installed, so removing 0 packages.' Think i should have used [FONT="Courier New"]sudo apt-get remove dhcp-client**3**[/FONT] instead. Won't know for sure if etc/network/interfaces is being overwritten till I get a monitor and keys hooked up to it again, but will do ASAP.

Long story: Was trying to with a PCI wireless card. That was a nightmare and didn't work out. Pulled card out, set up a wireless repeater and plug in via ethernet to that now. Problem is, no matter if I'm plugged into the repeater (downstairs where I need it) or into the base station (upstairs in the neighbors' place) I'm getting the same [FONT="Courier New"]*** Reloading ... smbd only**[/FONT] mess. I can say that frequency is about 1 per day with only 1 network interface installed as opposed to 1 per 5 mins when I had the PCI card in too though. This may be because of Static IP configuration though. 
If you are connected to a wireless connection anywhere in the chain (anywhere between the host and the LAN side of the router) you may have trouble with a dropped connection.  Ethernet is designed to be stable with intermittent interruptions.  In common wire (hub based) LAN's collisions causing interruptions were normal.  But a dropped connection of any length is problematic.  That's why I asked about wireless.  It does not have to be the problem, but it *can be* a problem.> 

Side Q: is it possible to set lease renew = never for static IP's? Do static IPs *ever* get renewed by definition? 
Static IP addresses by definition are manually configured ONLY in the /etc/network/interfaces (or something like it) file.  Never by DHCP.  The reserved address (with a unchanging IP address) is still a DHCP leased address.  So the answer to you question is yes, all leases are renewed based upon their stated lease time.  Rather than never you can set the lease to infinite.  This lease will never be renewed.  But remember it is still a DHCP leased IP address and not a static IP address.

Here is my /etc/network/interfaces file.```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static   [COLOR="Red"]<--This makes it a static IP address[/COLOR]
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0       [COLOR="Red"]<-- this brings the interface up when booting[/COLOR]

```
> 
I ask because I'm wondering if that's why I'm still getting error, but at a lower frequency.)**[FONT="Courier New"]* Reloading /etc/samba/smb.conf smbd only[/FONT]**.

You should read the logs.  They are located at [FONT="Courier New"]/var/log/samba[/FONT]

---

### Post by Uber-n00b on 2010-03-01
Well now, its been almost 24 hrs and things are seemingly working out just fine. I'd post my [FONT="Courier New"]**/etc/network/interfaces**[/FONT] but its almost identical to previous post.

I'm having a few issues with Samba getting the shared directories to 'show up' when browsing network from other machines though. Is this related to Static IP declaration? (Is it my router that is handling DNS and keeping track of computer names & IP addys?)

I checked [FONT="Courier New"]**/var/log/samba/log.nmbd**[/FONT] (sometimes a nmbd error was getting thrown with the * Reloading... and SSH Server msgs too.)Its full of entries like this one:
```
[2010/03/01 07:05:24,  0] nmbd/nmbd_serverlistdb.c:354(write_browse_list)
  write_browse_list: Fatal error - cannot find my workgroup ECKCITE

```
I'm guessing that's pointing to the problem... too bad I don't know anything about nmbd or much about DNS at all. Can anybody suggest a thread or even what to 'google' to learn more? Tnx.

---

### Post by capscrew on 2010-03-01
> **Uber-n00b said:**
> Well now, its been almost 24 hrs and things are seemingly working out just fine. I'd post my [FONT="Courier New"]**/etc/network/interfaces**[/FONT] but its almost identical to previous post.

Good deal.  So I assume the the interface is configured manually.
> 

I'm having a few issues with Samba getting the shared directories to 'show up' when browsing network from other machines though. Is this related to Static IP declaration?
No.  Browsing has to do with a consistent workgroup being declared.  That's why you are having the nmbd error you describe below.  > 
Is it my router that is handling DNS and keeping track of computer names & IP addys?

Typically the router handles DNS mapping.  DNS is the mapping of hostnames to IP addresses.  NetBIOS is the mapping of of COMPUTER NAME to IP address.  They are different (but as some say "the same"). 

The nmbd daemon is for nameservice resolution either by DNS or NetBIOS.  If nmbd can't find a netBIOS COMPUTER name it will look for the DNS hostname.   The nmbd daemon also handles the workgroup name used in network browsing.
> 

I checked [FONT="Courier New"]**/var/log/samba/log.nmbd**[/FONT] (sometimes a nmbd error was getting thrown with the * Reloading... and SSH Server msgs too.)Its full of entries like this one:
```
[2010/03/01 07:05:24,  0] nmbd/nmbd_serverlistdb.c:354(write_browse_list)
  write_browse_list: [COLOR="Purple"]Fatal error - cannot find my workgroup ECKCITE[/COLOR]

```
I'm guessing that's pointing to the problem... too bad I don't know anything about nmbd or much about DNS at all. Can anybody suggest a thread or even what to 'google' to learn more? Tnx.

Try searching on "nmbd +workgroup" or "nmbd +samba +naming"

The documentation is available at samba.org.  You could search all of the samba site with any query.  Search on the terms above and add "site:samba.org" to the end.  The quotes are not needed in the above searches.

---

