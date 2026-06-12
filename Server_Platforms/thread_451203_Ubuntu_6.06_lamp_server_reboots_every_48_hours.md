---
title: "Ubuntu 6.06 lamp server reboots every 48 hours"
date: 2007-05-22
forum: Server Platforms
---

### Post by andla on 2007-05-22
Installed a LAMP server from ubuntu 6.06 server cd, running on a HP proliant server.  It all went very smooth, maybe to smooth. Hardware RIAD and monitor works flawlessly. The only problem I have is that the server keeps rebooting every 48 hour , around 06.23 and I cant find what makes it reboot. Since it seems to be happening at a specific time I'm guessing it is something that is scheduled, but I cant find out what. Do anyboy have any ideas what it can be?
/A

---

### Post by spottraining on 2007-05-22
Rebooting all server or only some services?
Also -look to Proliant server - maybe is something wrong with temperatures or voltage.
Also - how its power supply for your server - maybe is that problem.

---

### Post by falcon15500 on 2007-05-22
Nothing in the logs?  You say probably something scheduled?  Are there any cron jobs running around then?  There is almost always some clue to be found in logs somewhere...

falc

---

### Post by andla on 2007-05-22
> **spottraining said:**
> Rebooting all server or only some services?
Also -look to Proliant server - maybe is something wrong with temperatures or voltage.
Also - how its power supply for your server - maybe is that problem.

it is the server that reboots , not just some services. Do not have any control over the power-supply , the machine is located in a server room/hall run by a large provider, that has a good rep.

---

### Post by andla on 2007-05-22
> **falcon15500 said:**
> Nothing in the logs?  You say probably something scheduled?  Are there any cron jobs running around then?  There is almost always some clue to be found in logs somewhere...

falc

I'm guessing it is some scheduled job since it happens at the same time 06.23 every other day (48 hours between each reboot). I have been looking at the logs but not sure what to look for, looking at the /etc/cron.*  I can't find any jobs that seems to reboot the machine , but then again not sure what to look for.

---

### Post by spottraining on 2007-05-22
Then look to cron list. Also check your kernel versions. Maybe its automatic updates on. But I haven't seen on my Ubuntu servers anything, that can reboot server so. My servers are up very long time (months).

And - when you don't see nothing at cron jobs - then contact your service provider. Even - he as good reputation - I am thinking - something is wrong with server hardware. Its good when they can check that directly from server monitoring panel.

---

### Post by andla on 2007-05-22
> **spottraining said:**
> Then look to cron list. Also check your kernel versions. Maybe its automatic updates on. But I haven't seen on my Ubuntu servers anything, that can reboot server so. My servers are up very long time (months).

And - when you don't see nothing at cron jobs - then contact your service provider. Even - he as good reputation - I am thinking - something is wrong with server hardware. Its good when they can check that directly from server monitoring panel.

The end of my syslog before reboot looks like this: 
May 22 06:20:01 cu /USR/SBIN/CRON[2653]: (smmsp) CMD (test -x /usr/share/sendmail/sendmail && /usr/s
hare/sendmail/sendmail cron-msp)
May 22 06:25:01 cu /USR/SBIN/CRON[2672]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report
 /etc/cron.daily)
May 22 06:25:02 cu exiting on signal 15

Any ideas from that ? 
(Looking back the lohg always look like this before reboot) 
and my misstake it reboots evryday at 06:25

---

### Post by MJN on 2007-05-22
What makes you think the server is rebooting?
 
Are you sure it's not just the syslog daemon restarting? ;)
 
(post the first few lines following the snippet above)
 
Mathew

---

### Post by andla on 2007-05-22
> **MJN said:**
> What makes you think the server is rebooting?
 
Are you sure it's not just the syslog daemon restarting? ;)
 
(post the first few lines following the snippet above)
 
Mathew
Boy do I feel like a horses ...  :D
of course it is the syslog restarting , totaly missed that it was placed in the cron.daliy. A quick look at top showed that  up time has been 18 days and some hours :) 
Thank you pointing out my own stupidity :) and helping me.  
 spottraining sorry for not listetning to you in the first place, since you where right from the start.
/A

---

### Post by adza on 2007-05-27
May 26 15:17:01 adza /USR/SBIN/CRON[7472]: (root) CMD (   run-parts --report /etc/cron.hourly)
May 26 15:39:01 adza /USR/SBIN/CRON[7478]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May 26 16:05:19 adza -- MARK --
May 26 16:09:01 adza /USR/SBIN/CRON[7493]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
May 27 17:07:19 adza syslogd 1.4.1#17ubuntu7: restart.


These are lines from my syslog that looks like it's rebooting my server as well... I'm quite new to the server admin thingy and can't figure out what might be doing this? The server is definately rebooting as i've got a hardware trap (trap 3e - SPARC architecture) in the reboot... so my server goes down until i reboot through the serial terminal...? from this log, it looks my my server was down for 24 hours yesterday.... :S how do i figure out these CRON jobs, i definately didn't configure any of these to run on the server install procress....?

Also, checking the /usr/lib/php5/maxlifetime file, shows max = 1440... what is this variable? 1440 hours, minutes, days??

---

### Post by adza on 2007-06-19
***bump*** this has happened again, does anyone know what this maxlifetime variable does?

---

### Post by MJN on 2007-06-19
Post your full syslog output and we can take a look. Are you sure you're not getting tricked by the scheduled syslogd restart into thinking your whole machine is rebooting (as discussed above)?
 
Mathew

---

### Post by adza on 2007-06-19
Thanks MJN! Here's the log up until restart.....

> Jun 16 06:25:13 adza syslogd 1.4.1#17ubuntu7: restart.
Jun 16 06:39:01 adza /USR/SBIN/CRON[6007]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 07:05:13 adza -- MARK --
Jun 16 07:09:01 adza /USR/SBIN/CRON[6025]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 07:17:01 adza /USR/SBIN/CRON[6083]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 07:39:01 adza /USR/SBIN/CRON[6090]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 08:01:34 adza postfix/smtpd[6105]: connect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 08:01:34 adza postfix/smtpd[6105]: lost connection after CONNECT from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 08:01:34 adza postfix/smtpd[6105]: disconnect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 08:04:54 adza postfix/anvil[6107]: statistics: max connection rate 1/60s for (smtp:125.225.17.166) at Jun 16 08:01:34
Jun 16 08:04:54 adza postfix/anvil[6107]: statistics: max connection count 1 for (smtp:125.225.17.166) at Jun 16 08:01:34
Jun 16 08:04:54 adza postfix/anvil[6107]: statistics: max cache size 1 at Jun 16 08:01:34
Jun 16 08:09:01 adza /USR/SBIN/CRON[6111]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 08:17:01 adza /USR/SBIN/CRON[6124]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 08:39:01 adza /USR/SBIN/CRON[6131]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 09:05:14 adza -- MARK --
Jun 16 09:09:01 adza /USR/SBIN/CRON[6150]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 09:17:01 adza /USR/SBIN/CRON[6163]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 09:23:56 adza postfix/smtpd[6165]: connect from bld-mail03.adl2.internode.on.net[203.16.214.67]
Jun 16 09:23:56 adza postfix/smtpd[6165]: 816051C312: client=bld-mail03.adl2.internode.on.net[203.16.214.67]
Jun 16 09:23:56 adza postfix/cleanup[6169]: 816051C312: message-id=<jjp7m2.6b6n5@www.dfxnews.com>
Jun 16 09:23:56 adza postfix/qmgr[3480]: 816051C312: from=<SRS0+dh5f+89+dfxnews.com=dfx@internode.on.net>, size=9278, nrcpt=1 (queue active)
Jun 16 09:23:56 adza postfix/smtpd[6165]: disconnect from bld-mail03.adl2.internode.on.net[203.16.214.67]
Jun 16 09:23:56 adza postfix/local[6170]: 816051C312: to=<adza@adza.homedns.org>, relay=local, delay=0, status=sent (delivered to maildir)
Jun 16 09:23:56 adza postfix/qmgr[3480]: 816051C312: removed
Jun 16 09:27:16 adza postfix/anvil[6167]: statistics: max connection rate 1/60s for (smtp:203.16.214.67) at Jun 16 09:23:56
Jun 16 09:27:16 adza postfix/anvil[6167]: statistics: max connection count 1 for (smtp:203.16.214.67) at Jun 16 09:23:56
Jun 16 09:27:16 adza postfix/anvil[6167]: statistics: max cache size 1 at Jun 16 09:23:56
Jun 16 09:39:01 adza /USR/SBIN/CRON[6177]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 10:05:15 adza -- MARK --
Jun 16 10:09:01 adza /USR/SBIN/CRON[6194]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 10:17:01 adza /USR/SBIN/CRON[6207]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 10:39:01 adza /USR/SBIN/CRON[6215]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 11:05:16 adza -- MARK --
Jun 16 11:09:01 adza /USR/SBIN/CRON[6233]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 11:17:01 adza /USR/SBIN/CRON[6246]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 11:31:54 adza postfix/smtpd[6250]: connect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:31:54 adza postfix/smtpd[6250]: lost connection after CONNECT from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:31:54 adza postfix/smtpd[6250]: disconnect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:34:35 adza postfix/smtpd[6254]: connect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:34:36 adza postfix/smtpd[6254]: NOQUEUE: reject: RCPT from 125-225-17-166.dynamic.hinet.net[125.225.17.166]: 554 <sr2_serch@yahoo.com.tw>: Relay access denied; from=<x9k5b2s8x1g5f4c@yahoo.com.tw> to=<sr2_serch@yahoo.com.tw> proto=SMTP helo=<59.167.22.133>
Jun 16 11:34:37 adza postfix/smtpd[6254]: lost connection after RCPT from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:34:37 adza postfix/smtpd[6254]: disconnect from 125-225-17-166.dynamic.hinet.net[125.225.17.166]
Jun 16 11:37:57 adza postfix/anvil[6252]: statistics: max connection rate 1/60s for (smtp:125.225.17.166) at Jun 16 11:31:54
Jun 16 11:37:57 adza postfix/anvil[6252]: statistics: max connection count 1 for (smtp:125.225.17.166) at Jun 16 11:31:54
Jun 16 11:37:57 adza postfix/anvil[6252]: statistics: max cache size 1 at Jun 16 11:31:54
Jun 16 11:38:42 adza courierpop3login: Connection, ip=[::ffff:192.168.1.64]
Jun 16 11:38:42 adza courierpop3login: LOGIN, user=adza, ip=[::ffff:192.168.1.64]
Jun 16 11:38:42 adza courierpop3login: LOGOUT, user=adza, ip=[::ffff:192.168.1.64], top=0, retr=9186, time=0
Jun 16 11:39:01 adza /USR/SBIN/CRON[6261]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 11:44:31 adza postfix/smtpd[6272]: connect from bld-mail07.adl2.internode.on.net[203.16.214.71]
Jun 16 11:44:31 adza postfix/smtpd[6272]: 88F381C160: client=bld-mail07.adl2.internode.on.net[203.16.214.71]
Jun 16 11:44:31 adza postfix/cleanup[6276]: 88F381C160: message-id=<BAY122-F10D774866A66372168517ABF1D0@phx.gbl>
Jun 16 11:44:35 adza postfix/qmgr[3480]: 88F381C160: from=<SRS0+/zMI+0+hotmail.com=niceonekesh@internode.on.net>, size=3538008, nrcpt=1 (queue active)
Jun 16 11:44:35 adza postfix/smtpd[6272]: disconnect from bld-mail07.adl2.internode.on.net[203.16.214.71]
Jun 16 11:44:36 adza postfix/local[6277]: 88F381C160: to=<adza@adza.homedns.org>, relay=local, delay=5, status=sent (delivered to maildir)
Jun 16 11:44:36 adza postfix/qmgr[3480]: 88F381C160: removed
Jun 16 11:47:55 adza postfix/anvil[6274]: statistics: max connection rate 1/60s for (smtp:203.16.214.71) at Jun 16 11:44:31
Jun 16 11:47:55 adza postfix/anvil[6274]: statistics: max connection count 1 for (smtp:203.16.214.71) at Jun 16 11:44:31
Jun 16 11:47:55 adza postfix/anvil[6274]: statistics: max cache size 1 at Jun 16 11:44:31
Jun 16 12:05:17 adza -- MARK --
Jun 16 12:06:58 adza postfix/smtpd[6284]: connect from smtp.per.people.net.au[202.154.92.226]
Jun 16 12:06:58 adza postfix/smtpd[6284]: 9A2CD1C7BB: client=smtp.per.people.net.au[202.154.92.226]
Jun 16 12:06:58 adza postfix/cleanup[6288]: 9A2CD1C7BB: message-id=<20070616020658.9A2CD1C7BB@adza.homedns.org>
Jun 16 12:07:14 adza postfix/qmgr[3480]: 9A2CD1C7BB: from=<sam@tourismportdouglas.com.au>, size=3513545, nrcpt=1 (queue active)
Jun 16 12:07:14 adza postfix/smtpd[6284]: disconnect from smtp.per.people.net.au[202.154.92.226]
Jun 16 12:07:14 adza postfix/local[6289]: 9A2CD1C7BB: to=<adza@adza.homedns.org>, relay=local, delay=16, status=sent (delivered to maildir)
Jun 16 12:07:14 adza postfix/qmgr[3480]: 9A2CD1C7BB: removed
Jun 16 12:09:02 adza /USR/SBIN/CRON[6291]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 12:10:34 adza postfix/anvil[6286]: statistics: max connection rate 1/60s for (smtp:202.154.92.226) at Jun 16 12:06:58
Jun 16 12:10:34 adza postfix/anvil[6286]: statistics: max connection count 1 for (smtp:202.154.92.226) at Jun 16 12:06:58
Jun 16 12:10:34 adza postfix/anvil[6286]: statistics: max cache size 1 at Jun 16 12:06:58
Jun 16 12:17:01 adza /USR/SBIN/CRON[6305]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 16 12:39:01 adza /USR/SBIN/CRON[6312]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 16 13:05:17 adza -- MARK --
Jun 16 13:09:01 adza /USR/SBIN/CRON[6329]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 18 16:14:42 adza syslogd 1.4.1#17ubuntu7: restart.
Jun 18 16:14:42 adza kernel: Inspecting /boot/System.map-2.6.15-26-sparc64-smp
Jun 18 16:14:42 adza kernel: Loaded 21300 symbols from /boot/System.map-2.6.15-26-sparc64-smp.
Jun 18 16:14:42 adza kernel: Symbols match kernel version 2.6.15.

the last time it crashed, the last line in this file was also the maxlifetime php line....???

---

### Post by MJN on 2007-06-19
> **adza said:**
>                               Jun 16 06:25:13 adza syslogd 1.4.1#17ubuntu7: restart.
.
.
.
Jun 16 13:09:01 adza /USR/SBIN/CRON[6329]: (root) CMD ( [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 18 16:14:42 adza syslogd 1.4.1#17ubuntu7: restart.
Jun 18 16:14:42 adza kernel: Inspecting /boot/System.map-2.6.15-26-sparc64-smp

That first 'restart' is not a system restart - it's syslogd restarting (to roll the syslog) as instructed by the daily cron job which runs at 6:25am every day - perfectly normal.

The second restart *is* a system restart as indicated by the subsequent entries. However, this occurred over two days after the PHP cron job (which, incidentally, is a standard cron job on every system with PHP installed - it purges old session files) and so you can pretty much safely rule that cause out of the equation. To really eliminate it try commenting out the final line in /etc/cron.d/php5 and that'll stop it running.

As for what *is* causing the reboots, can you dig out more log entries that indicate when this is happening? Do **not** report '**syslogd 1.4.1#17ubuntu7: restart**' lines as these are not themselves indicative of system restarts, instead just post any mention of, say, **'Inspecting /boot/System.map-2.6.15-26-sparc64-smp'** (just do a simple **zgrep System.map-2.6 /var/log/syslog*** to look for these).

Mathew

---

### Post by netlogic on 2007-06-19
This looks like hardware problems on the board or ram. This appears to be an old machine. What kind of ram are you using? What are their speeds? What is the settings for your ram on the bios? Does your bios has a PCI latency setting? Have tried to slow clocking your ram speed and make wider pci latency setting and leave it  up for a week?

---

### Post by adza on 2007-06-19
thanks guys! i am working at the moment... so i'll have to post again later, as for the hardware issue.. this has been a concern of mine as i bought the machine on ebay cheap last year.... :S

---

### Post by adza on 2007-06-20
here is another log from when this happened... again, the last line before crashfile was this php maxlifetime variable.... 

> Jun 13 23:09:01 adza /USR/SBIN/CRON[22562]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 13 23:17:01 adza /USR/SBIN/CRON[22573]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jun 13 23:39:01 adza /USR/SBIN/CRON[22575]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun 14 06:40:24 adza syslogd 1.4.1#17ubuntu7: restart.
Jun 14 06:40:24 adza kernel: Inspecting /boot/System.map-2.6.15-26-sparc64-smp
Jun 14 06:40:24 adza kernel: Loaded 21300 symbols from /boot/System.map-2.6.15-26-sparc64-smp.
Jun 14 06:40:24 adza kernel: Symbols match kernel version 2.6.15.
Jun 14 06:40:24 adza kernel: No module symbols loaded - kernel modules not enabled. 
Jun 14 06:40:24 adza kernel: [    0.000000] PROMLIB: Sun IEEE Boot Prom 'OBP 3.11.26 1998/04/15 14:52'
Jun 14 06:40:24 adza kernel: [    0.000000] PROMLIB: Root node compatible: 
Jun 14 06:40:24 adza kernel: [    0.000000] Linux version 2.6.15-26-sparc64-smp (buildd@vivies) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Fri Sep 8 20:10:24 UTC 2006
Jun 14 06:40:24 adza kernel: [    0.000000] ARCH: SUN4U
Jun 14 06:40:24 adza kernel: [    0.000000] Ethernet address: 08:00:20:a1:65:18
Jun 14 06:40:24 adza kernel: [    0.000000] On node 0 totalpages: 260707
Jun 14 06:40:24 adza kernel: [    0.000000]   DMA zone: 260707 pages, LIFO batch:15
Jun 14 06:40:24 adza kernel: [    0.000000]   DMA32 zone: 0 pages, LIFO batch:0
Jun 14 06:40:24 adza kernel: [    0.000000]   Normal zone: 0 pages, LIFO batch:0
Jun 14 06:40:24 adza kernel: [    0.000000]   HighMem zone: 0 pages, LIFO batch:0
Jun 14 06:40:24 adza kernel: [    0.000000] Built 1 zonelists
Jun 14 06:40:24 adza kernel: [    0.000000] Kernel command line: root=/dev/sda2 ro quiet splash
Jun 14 06:40:24 adza kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
Jun 14 06:40:24 adza kernel: [    1.212452] Console: colour dummy device 80x25
Jun 14 06:40:24 adza kernel: [    1.221433] Dentry cache hash table entries: 262144 (order: 8, 2097152 bytes)
Jun 14 06:40:24 adza kernel: [    1.231132] Inode-cache hash table entries: 131072 (order: 7, 1048576 bytes)
Jun 14 06:40:24 adza kernel: [    1.352511] Memory: 2066400k available (2472k kernel code, 744k data, 184k init) [fffff80000000000,00000000bfefe000]
Jun 14 06:40:24 adza kernel: [    1.431234] Calibrating delay using timer specific routine.. 720.37 BogoMIPS (lpj=1440758)
Jun 14 06:40:24 adza kernel: [    1.431583] Security Framework v1.0.0 initialized
Jun 14 06:40:24 adza kernel: [    1.431624] SELinux:  Disabled at boot.
Jun 14 06:40:24 adza kernel: [    1.431761] Mount-cache hash table entries: 512
Jun 14 06:40:24 adza kernel: [    1.433038] checking if image is initramfs... it is
Jun 14 06:40:24 adza kernel: [    4.676094] Freeing initrd memory: 6516k freed
Jun 14 06:40:24 adza kernel: [    4.682218] CPU[0]: Caches D[sz(16384):line_sz(32)] I[sz(16384):line_sz(32)] E[sz(4194304):line_sz(64)]
Jun 14 06:40:24 adza kernel: [    4.775233] Calibrating delay using timer specific routine.. 720.02 BogoMIPS (lpj=1440053)
Jun 14 06:40:24 adza kernel: [    4.777047] CPU[2]: Caches D[sz(16384):line_sz(32)] I[sz(16384):line_sz(32)] E[sz(4194304):line_sz(64)]
Jun 14 06:40:24 adza kernel: [    4.777545] CPU 2: synchronized TICK with master CPU (last diff 1 cycles,maxerr 444 cycles)
Jun 14 06:40:24 adza kernel: [    4.777566] Brought up 2 CPUs
Jun 14 06:40:24 adza kernel: [    4.777585] Total of 2 processors activated (1440.40 BogoMIPS).
Jun 14 06:40:24 adza kernel: [    4.778827] NET: Registered protocol family 16
Jun 14 06:40:24 adza kernel: [    4.782537] PCI: Probing for controllers.
Jun 14 06:40:24 adza kernel: [    4.783673] PCI: Found PSYCHO, control regs at 000001fe00000000
Jun 14 06:40:24 adza kernel: [    4.783695] PSYCHO: Shared PCI config space at 000001fe01000000
Jun 14 06:40:24 adza kernel: [    4.795026] PCI-IRQ: Routing bus[ 0] slot[ 1] to INO[21]
Jun 14 06:40:24 adza kernel: [    4.795193] PCI-IRQ: Routing bus[ 0] slot[ 3] to INO[20]
Jun 14 06:40:24 adza kernel: [    4.795371] PCI-IRQ: Routing bus[ 0] slot[ 3] to INO[26]
Jun 14 06:40:24 adza kernel: [    4.795534] PCI-IRQ: Routing bus[ 0] slot[ 5] to INO[1c]
Jun 14 06:40:24 adza kernel: [    4.795556] PCI0(PBMB): Bus running at 33MHz
Jun 14 06:40:24 adza kernel: [    4.796524] PCI0(PBMA): Bus running at 66MHz
Jun 14 06:40:24 adza kernel: [    4.796663] ebus0: [auxio] [power] [SUNW,pll] [sc] [se] [su] [su] [ecpp] [fdthree] [eeprom] [flashprom] [SUNW,CS4231]
Jun 14 06:40:24 adza kernel: [    4.800872] power: Control reg at 000001fff1724000 ... not using powerd.
Jun 14 06:40:24 adza kernel: [    4.806097] usbcore: registered new driver usbfs
Jun 14 06:40:24 adza kernel: [    4.806327] usbcore: registered new driver hub
Jun 14 06:40:24 adza kernel: [    4.811929] audit: initializing netlink socket (disabled)
Jun 14 06:40:24 adza kernel: [    4.811976] audit(1181767178.196:1): initialized
Jun 14 06:40:24 adza kernel: [    4.812192] Total HugeTLB memory allocated, 0
Jun 14 06:40:24 adza kernel: [    4.813000] VFS: Disk quotas dquot_6.5.1
Jun 14 06:40:24 adza kernel: [    4.813156] Dquot-cache hash table entries: 1024 (order 0, 8192 bytes)
Jun 14 06:40:24 adza kernel: [    4.813531] Initializing Cryptographic API
Jun 14 06:40:24 adza kernel: [    4.813556] io scheduler noop registered
Jun 14 06:40:24 adza kernel: [    4.813599] io scheduler anticipatory registered
Jun 14 06:40:24 adza kernel: [    4.813651] io scheduler deadline registered
Jun 14 06:40:24 adza kernel: [    4.813755] io scheduler cfq registered
Jun 14 06:40:24 adza kernel: [    4.832171] Console: switching to colour frame buffer device 144x56
Jun 14 06:40:24 adza kernel: [    4.832204] ffb: FFB at 000001fc00000000 type 51 DAC 10
Jun 14 06:40:24 adza kernel: [    4.834344] ffb: AFB at 000001fa00000000 type 35 DAC 10
Jun 14 06:40:24 adza kernel: [    4.937159] rtc_init: no PC rtc found
Jun 14 06:40:24 adza kernel: [    4.937254] [drm] Initialized drm 1.0.1 20051102
Jun 14 06:40:24 adza kernel: [    4.949831] su0 at 0x000001fff13062f8 (irq = 5,7ea) is a 16550A
Jun 14 06:40:24 adza kernel: [    4.949934] su1 at 0x000001fff13083f8 (irq = 9,7e9) is a 16550A
Jun 14 06:40:24 adza kernel: [    4.950055] ttyS0 at MMIO 0x1fff1400000 (irq = 7807200) is a SAB82532 V3.2
Jun 14 06:40:24 adza kernel: [    4.950360] Console: ttyS0 (SAB82532)
Jun 14 06:40:24 adza kernel: [    4.996916] ttyS1 at MMIO 0x1fff1400040 (irq = 7807200) is a SAB82532 V3.2
Jun 14 06:40:24 adza kernel: [    5.328141] Floppy drive(s): fd0 is 1.44M
Jun 14 06:40:24 adza kernel: [    5.346581] FDC 0 is a National Semiconductor PC87306
Jun 14 06:40:24 adza kernel: [    5.350811] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 14 06:40:24 adza kernel: [    5.352140] loop: loaded (max 8 devices)
Jun 14 06:40:24 adza kernel: [    5.352260] sunhme.c:v2.02 8/24/03 David S. Miller (davem@redhat.com)
Jun 14 06:40:24 adza kernel: [    5.353446] eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet 08:00:20:a1:65:18 
Jun 14 06:40:24 adza kernel: [    5.353934] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 14 06:40:24 adza kernel: [    5.353957] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 14 06:40:24 adza kernel: [    5.354897] rtc_sun_init: Registered Mostek RTC driver.
Jun 14 06:40:24 adza kernel: [    5.354915] usbmon: debugfs is not available
Jun 14 06:40:24 adza kernel: [    5.355086] usbcore: registered new driver usbhid
Jun 14 06:40:24 adza kernel: [    5.355104] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 14 06:40:24 adza kernel: [    5.355447] mice: PS/2 mouse device common for all mice
Jun 14 06:40:24 adza kernel: [    5.355804] NET: Registered protocol family 2
Jun 14 06:40:24 adza kernel: [    5.397867] IP route cache hash table entries: 65536 (order: 6, 524288 bytes)
Jun 14 06:40:24 adza kernel: [    5.400571] TCP established hash table entries: 262144 (order: 9, 4194304 bytes)
Jun 14 06:40:24 adza kernel: [    5.420492] TCP bind hash table entries: 65536 (order: 7, 1048576 bytes)
Jun 14 06:40:24 adza kernel: [    5.425516] TCP: Hash tables configured (established 262144 bind 65536)
Jun 14 06:40:24 adza kernel: [    5.425543] TCP reno registered
Jun 14 06:40:24 adza kernel: [    5.426042] TCP bic registered
Jun 14 06:40:24 adza kernel: [    5.426141] NET: Registered protocol family 1
Jun 14 06:40:24 adza kernel: [    5.426183] NET: Registered protocol family 17
Jun 14 06:40:24 adza kernel: [    5.772528] Capability LSM initialized
Jun 14 06:40:24 adza kernel: [    6.355636] input: Sun Mouse as /class/input/input0
Jun 14 06:40:24 adza kernel: [    7.560251] SCSI subsystem initialized
Jun 14 06:40:24 adza kernel: [    7.578637] sym0: <875> rev 0x14 at pci 0001:00:03.0 irq 5,7e0
Jun 14 06:40:24 adza kernel: [    7.665339] sym0: No NVRAM, ID 7, Fast-20, SE, parity checking
Jun 14 06:40:24 adza kernel: [    7.672573] sym0: SCSI BUS has been reset.
Jun 14 06:40:24 adza kernel: [    7.672609] scsi0 : sym-2.2.2
Jun 14 06:40:24 adza kernel: [   10.950888]  target0:0:1: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 15)
Jun 14 06:40:24 adza kernel: [   10.952404]   Vendor: COMPAQ    Model: AB009322B4        Rev: A019
Jun 14 06:40:24 adza kernel: [   10.952467]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jun 14 06:40:24 adza kernel: [   10.952509]  target0:0:1: tagged command queuing enabled, command queue depth 16.
Jun 14 06:40:24 adza kernel: [   10.952579]  target0:0:1: Beginning Domain Validation
Jun 14 06:40:24 adza kernel: [   10.953200]  target0:0:1: asynchronous.
Jun 14 06:40:24 adza kernel: [   10.954618]  target0:0:1: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 16)
Jun 14 06:40:24 adza kernel: [   10.955506]  target0:0:1: Domain Validation skipping write tests
Jun 14 06:40:24 adza kernel: [   10.955526]  target0:0:1: Ending Domain Validation
Jun 14 06:40:24 adza kernel: [   12.134603]   Vendor: TOSHIBA   Model: XM6201TASUN32XCD  Rev: 1103
Jun 14 06:40:24 adza kernel: [   12.134661]   Type:   CD-ROM                             ANSI SCSI revision: 02
Jun 14 06:40:24 adza kernel: [   12.134705]  target0:0:6: Beginning Domain Validation
Jun 14 06:40:24 adza kernel: [   12.134843]  target0:0:6: asynchronous.
Jun 14 06:40:24 adza kernel: [   12.136105]  target0:0:6: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 16)
Jun 14 06:40:24 adza kernel: [   12.136948]  target0:0:6: Domain Validation skipping write tests
Jun 14 06:40:24 adza kernel: [   12.136967]  target0:0:6: Ending Domain Validation
Jun 14 06:40:24 adza kernel: [   14.490379] sym1: <875> rev 0x14 at pci 0001:00:03.1 irq 5,7e6
Jun 14 06:40:24 adza kernel: [   14.577074] sym1: No NVRAM, ID 7, Fast-20, SE, parity checking
Jun 14 06:40:24 adza kernel: [   14.584352] sym1: SCSI BUS has been reset.
Jun 14 06:40:24 adza kernel: [   14.584386] scsi1 : sym-2.2.2
Jun 14 06:40:24 adza kernel: [    4.872191] Driver 'sd' needs updating - please use bus_type methods
Jun 14 06:40:24 adza kernel: [    5.047915] SCSI device sda: 17773500 512-byte hdwr sectors (9100 MB)
Jun 14 06:40:24 adza kernel: [    5.049476] SCSI device sda: drive cache: write through
Jun 14 06:40:24 adza kernel: [    5.050211] SCSI device sda: 17773500 512-byte hdwr sectors (9100 MB)
Jun 14 06:40:24 adza kernel: [    5.051729] SCSI device sda: drive cache: write through
Jun 14 06:40:24 adza kernel: [    5.051753]  sda: sda1 sda2 sda3 sda4
Jun 14 06:40:24 adza kernel: [    5.058071] sd 0:0:1:0: Attached scsi disk sda
Jun 14 06:40:24 adza kernel: [    5.808653] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 14 06:40:24 adza kernel: [    5.808676] EXT3-fs: write access will be enabled during recovery.
Jun 14 06:40:24 adza kernel: [   10.680172] kjournald starting.  Commit interval 5 seconds
Jun 14 06:40:24 adza kernel: [   10.680237] EXT3-fs: sda2: orphan cleanup on readonly fs
Jun 14 06:40:24 adza kernel: [   10.680278] ext3_orphan_cleanup: deleting unreferenced inode 116151
Jun 14 06:40:24 adza kernel: [   10.688369] ext3_orphan_cleanup: deleting unreferenced inode 115266
Jun 14 06:40:24 adza kernel: [   10.688434] ext3_orphan_cleanup: deleting unreferenced inode 115168
Jun 14 06:40:24 adza kernel: [   10.688489] ext3_orphan_cleanup: deleting unreferenced inode 115166
Jun 14 06:40:24 adza kernel: [   10.688540] ext3_orphan_cleanup: deleting unreferenced inode 115138
Jun 14 06:40:24 adza kernel: [   10.688592] ext3_orphan_cleanup: deleting unreferenced inode 115046
Jun 14 06:40:24 adza kernel: [   10.688642] EXT3-fs: sda2: 6 orphan inodes deleted
Jun 14 06:40:24 adza kernel: [   10.688657] EXT3-fs: recovery complete.
Jun 14 06:40:24 adza kernel: [   10.783058] EXT3-fs: mounted filesystem with ordered data mode.
Jun 14 06:40:24 adza kernel: [   14.517524] sd 0:0:1:0: Attached scsi generic sg0 type 0
Jun 14 06:40:25 adza kernel: [   14.517617]  0:0:6:0: Attached scsi generic sg1 type 5
Jun 14 06:40:25 adza kernel: [   14.607742] sr0: scsi-1 drive
Jun 14 06:40:25 adza kernel: [   14.607766] Uniform CD-ROM driver Revision: 3.20
Jun 14 06:40:25 adza kernel: [   14.607933] sr 0:0:6:0: Attached scsi CD-ROM sr0
Jun 14 06:40:25 adza kernel: [   16.613822] Adding 409640k swap on /dev/sda4.  Priority:-1 extents:1 across:409640k
Jun 14 06:40:25 adza kernel: [   16.757250] EXT3 FS on sda2, internal journal
Jun 14 06:40:25 adza kernel: [   17.003553] NET: Registered protocol family 10
Jun 14 06:40:25 adza kernel: [   17.004113] lo: Disabled Privacy Extensions
Jun 14 06:40:25 adza kernel: [   17.004705] IPv6 over IPv4 tunneling driver
Jun 14 06:40:25 adza kernel: [    0.089317] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Jun 14 06:40:25 adza kernel: [    0.089339] md: bitmap version 4.39
Jun 14 06:40:25 adza kernel: [    0.767533] eth0: Link is up using internal transceiver at 100Mb/s, Full Duplex.
Jun 14 06:40:25 adza kernel: [    1.072247] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]

---

### Post by MJN on 2007-06-20
Have you tried commenting out the cron line for the php script, to rule it out from further investigation?
 
Mathew

---

### Post by adza on 2007-07-22
This has now been fixed, @andla you were right (sort of!)... it wasn't the power supply in the server, however an earth loop was occurring with the serial connection between my desktop and the server machine, everytime i rebooted my desktop, bang, down went the server. Naturally, because i use linux, i'm not forced to reboot my machine that often :) however, last week was playing around in windows with my bro and lo and behold, the server crashed several times in one day! Serial connection is now comms isolated and server hasn't crashed since... haha victory!!!! Thanks for all your help with this one guys, i learnt quite a bit along the way... Hopefully this post may help someone else in the future :P

---

