---
title: "Repeated failures in the server - Dell PowerEdge R610 - Ubuntu 8.04.3 LTS"
date: 2009-12-01
forum: Server Platforms
---

### Post by SupuS on 2009-12-01
Hello everyone

After purchasing Dell PowerEdge R610 Server there were frequent failures on the server .. from 1 to 2 minutes and server does not react at all. No entry in any log file during failure. After the service repairs and replacement of the motherboard problem was seemingly solved. During testing I don't find any problem. But now, when server is used as webserver, failures occurred again. This time "only" 2 to 3 per day. Dell technician found no error in the hardware (he could not find hardware problem also for the first time but by replacing the motherboard problem was almost solved). Dell technician think that an error is in the software but this version of Ubuntu in the same configuration also operate on my other 5-Dell servers without problems. Monitoring zabbix at the failure time receive no data from the server. Basically, at the time of failure server is completely dead, inaccessible from the Internet or via ssh or via the KVM and not recorded any log files. I attach an extract from the syslog and SAR when downtime:

```
Nov 27 16:54:44 s6 postfix/cleanup[23475]: 706727820CD: message-id=<000701ca6f7a$16894ab0$4a37b6d2@nbnet.nb.ca>
Nov 27 16:54:44 s6 postfix/smtpd[14249]: 5DA4678213C: client=189-11-20-179.mganm702.dsl.brasiltelecom.net.br[189.11.20.179]
Nov 27 16:54:44 s6 postfix/qmgr[12859]: 706727820CD: from=<rclundoo@nbnet.nb.ca>, size=861, nrcpt=1 (queue active)
Nov 27 16:54:45 s6 postfix/smtpd[2892]: disconnect from unknown[189.238.15.3]
Nov 27 16:54:49 s6 postfix/smtpd[14382]: connect from unknown[190.66.169.227]
Nov 27 16:54:50 s6 postfix/smtpd[14382]: setting up TLS connection from unknown[190.66.169.227]
Nov 27 16:56:02 s6 postfix/cleanup[23570]: 5DA4678213C: message-id=<000701ca6f78$9b5ad3a0$ae78a432@acapacific.com.sg>
Nov 27 16:56:02 s6 postfix/smtpd[14391]: warning: 78.128.29.46: hostname ip-30-46.powernet.bg verification failed: Name or service not known
Nov 27 16:56:02 s6 postfix/smtpd[14391]: connect from unknown[78.128.29.46]
Nov 27 16:56:02 s6 imapd: Connection, ip=[::ffff:127.0.0.1]
```

sar (syslog):
```
# sar -s 16:50:00 -e 17:00:00
Linux 2.6.24-25-server (www.example.com)  11/27/09

16:50:01        CPU     %user     %nice   %system   %iowait    %steal     %idle
16:51:01        all      4.50      0.03      2.91      0.05      0.00     92.52
16:52:01        all     19.37      0.16     30.32      0.04      0.00     50.11
16:53:01        all     22.21      0.08     32.17      0.08      0.00     45.46
16:54:01        all     24.56      0.15     37.35      0.04      0.00     37.90
16:56:02        all     19.00      0.22     28.01      0.06      0.00     52.71
16:57:01        all      8.41      0.03      7.17      0.07      0.00     84.32
16:58:01        all      5.20      0.02      2.67      0.10      0.00     92.01
16:59:01        all      6.79      0.03      3.50      0.04      0.00     89.63
Average:        all      9.11      0.05      9.40      0.06      0.00     81.38
```

Thanks for any idea

SupuS

---

### Post by apel_2804 on 2009-12-02
Hello,

are the other Dell Servers R610 too? Or also from the same generation, like R710/R410 with Intel Nehalem chipset?

It's known that the old kernel in Ubuntu 8.04 LTS may emit issues like the one you are facing.

Did you or the guys from Dell run an "offline" hardware diagnostic (named 32bit diag by Dell, boot CD or USB-Stick)? 

If not you can start and boot into "System Services" pressing F10 or F11 during POST. Which is an UEFI-"BIOS" there is an build in diagnostic, it also will gave you the output of the server internal hardware protocol.

Sometimes the new servers lockup because on an unaccessable sdx drive. This issue is often seen in VMware ESX4. There is an timeout hundreds a seconds which is causing the system to freeze or run realy slow. In that case the virtual media provided by the iDRAC/System Services is causing the issue. You can deactivate the whole system services (UEFI, Diagnostics, Virtual Media) by enteing Ctrl+E during POST (iDRAC BIOS) and set "System Services" to off.

---

### Post by SupuS on 2009-12-02
> **apel_2804 said:**
> Hello,

are the other Dell Servers R610 too? Or also from the same generation, like R710/R410 with Intel Nehalem chipset?

It's known that the old kernel in Ubuntu 8.04 LTS may emit issues like the one you are facing.

Did you or the guys from Dell run an "offline" hardware diagnostic (named 32bit diag by Dell, boot CD or USB-Stick)? 

If not you can start and boot into "System Services" pressing F10 or F11 during POST. Which is an UEFI-"BIOS" there is an build in diagnostic, it also will gave you the output of the server internal hardware protocol.

Sometimes the new servers lockup because on an unaccessable sdx drive. This issue is often seen in VMware ESX4. There is an timeout hundreds a seconds which is causing the system to freeze or run realy slow. In that case the virtual media provided by the iDRAC/System Services is causing the issue. You can deactivate the whole system services (UEFI, Diagnostics, Virtual Media) by enteing Ctrl+E during POST (iDRAC BIOS) and set "System Services" to off.

Hello apel_2804

Thank you for replay. We have only Dell PowerEdge 1850, Dell PowerEdge R200 and Dell PowerEdge 1950.

On this server is kernel 2.6.24-25-server:

```
# uname -a
Linux s6.zserver.cz 2.6.24-25-server #1 SMP Tue Oct 20 07:20:02 UTC 2009 x86_64 GNU/Linux
```

Is described issue in this kernel too?

Dell technician send mi this URL with DSET testing tool:

```
DSET
http://support.euro.dell.com/support/downloads/format.aspx?c=cz&amp;l=cs&amp;s=gen&amp;deviceid=15131&amp;libid=36&amp;releaseid=R239304&amp;vercnt=2&amp;formatcnt=0&amp;SystemID=PWE_R610&amp;servicetag=&amp;os=RH52&amp;osl=cz&amp;catid=-1&amp;dateid=-1&amp;typeid=-1&amp;formatid=-1&amp;impid=-1

```

I used this tool and sent result to Dell technician but he didn't find anything strange.

I tried run Dell Omsa Live CD from [http://linux.dell.com/files/openmanage-contributions/omsa-51-live/](http://linux.dell.com/files/openmanage-contributions/omsa-51-live/) but it fails during boot.

Hardware log from Dell Omsa omreport contains no records.

Build in diagnostic i tried too .. it was running for more than 24 hours without any problem.

In this time I have running pidstat in 1 seccond interval. There is a failure to see which ends large load because of the many running processes apache.

I am going to consult problem with iDRAC/System Services with Dell technician and than post the result.

Thanks

SupuS

---

### Post by apel_2804 on 2009-12-02
That you don't get this issue on the other servers didn't count as an argument, they have much older, well integrated chipsets. That the live CD didn't work is "normal" on the 11G Servers from dell. Has something to do with the sata optical drive and the new chipset.

Ok, diag shows no errors. ESM log is clear. Did you ever looked into the DSET report you send the dell tech? There is an .hta file which you can open in any browser. If the .zip-file is protected the password is "dell".

You also can check with top if there is an "kipmi0" module which is possibly going crazy. If so, try to deinstall OMSA or install latest version (6.1).

In wich country is the server located / or which dell support did you call (country)?

For debian there are shortly updated kernels available called vanilla kernel. If I'm not misstaken they are also available for ubuntu.

---

### Post by SupuS on 2009-12-02
> **apel_2804 said:**
> That you don't get this issue on the other servers didn't count as an argument, they have much older, well integrated chipsets. That the live CD didn't work is "normal" on the 11G Servers from dell. Has something to do with the sata optical drive and the new chipset.

Ok, diag shows no errors. ESM log is clear. Did you ever looked into the DSET report you send the dell tech? There is an .hta file which you can open in any browser. If the .zip-file is protected the password is "dell".

You also can check with top if there is an "kipmi0" module which is possibly going crazy. If so, try to deinstall OMSA or install latest version (6.1).

In wich country is the server located / or which dell support did you call (country)?

For debian there are shortly updated kernels available called vanilla kernel. If I'm not misstaken they are also available for ubuntu.

I have DSET report but I didn't find anything strange or I don't know what to search.

kipmi0 plugin is presented in top very often even directly before failure:

# pidstat 1 - failure started at 05:09:02 PM
```
05:09:00 PM       PID   %user %system    %CPU   CPU  Command
05:09:01 PM      5577   26.00    7.00   33.00     4  apache2
05:09:01 PM      6233    8.00    7.00   15.00     4  apache2
05:09:01 PM      6479    0.00    1.00    1.00    13  cleanup
05:09:01 PM      6531   13.00    4.00   17.00    14  apache2
05:09:01 PM      7077    0.00    3.00    3.00     1  kipmi0
05:09:01 PM      7199   13.00    7.00   20.00     8  apache2
05:09:01 PM      7327   22.00   35.00   57.00    14  apache2

05:09:01 PM       PID   %user %system    %CPU   CPU  Command
05:09:02 PM        52    0.00    0.99    0.99     1  events/1
05:09:02 PM      4641   21.78    8.91   30.69     0  apache2
05:09:02 PM      6615    1.98    3.96    5.94    12  apache2
05:09:02 PM      6619    6.93    4.95   11.88     8  apache2
05:09:02 PM      6836   26.73    6.93   33.66     0  apache2
05:09:02 PM      6954    0.00    1.98    1.98     8  apache2
05:09:02 PM      7153    0.00    0.99    0.99    10  dsm_sa_datamgr3
05:09:02 PM      7211    4.95    0.99    5.94     6  apache2
05:09:02 PM      7242    4.95    2.97    7.92     0  apache2
05:09:02 PM      7371    0.00    3.96    3.96     8  apache2

05:09:02 PM       PID   %user %system    %CPU   CPU  Command
05:11:15 PM      2472    0.01    0.00    0.01     0  apache2
05:11:15 PM      3108    0.00    0.01    0.01     7  kjournald
05:11:15 PM      3147    0.01    0.04    0.06     0  apache2
05:11:15 PM      3647    0.00    0.02    0.02     0  apache2
05:11:15 PM      3805    0.01    0.11    0.12     8  apache2
05:11:15 PM      4313    0.00    0.01    0.01     4  apache2
05:11:15 PM      4358    0.00    0.04    0.04     0  apache2
05:11:15 PM      4641    0.22    0.01    0.23     6  apache2
05:11:15 PM      4936    0.02    0.03    0.05     4  apache2
05:11:15 PM      4937    0.00    0.01    0.01     8  apache2
05:11:15 PM      4972    0.00    0.01    0.01     0  apache2
05:11:15 PM      4992    0.11    0.13    0.25     0  apache2
05:11:15 PM      5279    0.01    0.04    0.05     0  apache2
05:11:15 PM      5285    0.00    0.01    0.01     0  apache2
05:11:15 PM      5288    0.01    0.01    0.03     0  apache2
05:11:15 PM      5308    0.00    0.01    0.01     0  apache2
05:11:15 PM      5309    0.00    0.01    0.01     0  apache2
05:11:15 PM      5373    0.00    0.02    0.02     0  apache2
05:11:15 PM      5413    0.00    0.03    0.03    10  apache2
05:11:15 PM      5429    0.00    0.01    0.01     6  sshd
05:11:15 PM      5460    0.01    0.00    0.01     0  ossec-agentd
05:11:15 PM      5577    0.08    0.01    0.10    10  apache2
05:11:15 PM      5579    0.00    0.01    0.01    10  apache2
05:11:15 PM      5580    0.12    0.08    0.20     0  apache2
05:11:15 PM      5681    0.00    0.02    0.02     0  apache2
05:11:15 PM      5880    0.00    0.02    0.02     0  apache2
05:11:15 PM      5914    0.02    0.02    0.04     0  apache2
05:11:15 PM      6026    0.00    0.01    0.01     6  apache2
05:11:15 PM      6028    0.01    0.05    0.06     6  apache2
05:11:15 PM      6029    0.00    0.02    0.02     0  apache2
05:11:15 PM      6032    0.02    0.02    0.04     0  apache2
05:11:15 PM      6033    0.00    0.02    0.02     2  apache2
05:11:15 PM      6037    0.03    0.01    0.04     0  apache2
05:11:15 PM      6063    0.00    0.01    0.01     0  apache2
05:11:15 PM      6068    0.13    0.04    0.17     0  apache2
05:11:15 PM      6069    0.00    0.01    0.01     0  apache2
05:11:15 PM      6070    0.00    0.02    0.02     0  apache2
05:11:15 PM      6072    0.01    0.04    0.05     0  apache2
05:11:15 PM      6233    0.01    0.01    0.01    10  apache2
05:11:15 PM      6253    0.01    0.01    0.01     0  apache2
05:11:15 PM      6269    0.02    0.02    0.04     0  apache2
05:11:15 PM      6270    0.04    0.03    0.07    12  apache2
05:11:15 PM      6271    0.01    0.00    0.01     5  apache2
05:11:15 PM      6278    0.00    0.01    0.01     0  apache2
05:11:15 PM      6280    0.00    0.01    0.01     0  apache2
05:11:15 PM      6281    0.04    0.01    0.05     4  apache2
05:11:15 PM      6282    0.01    0.04    0.04     0  apache2
05:11:15 PM      6283    0.00    0.01    0.01     0  apache2
05:11:15 PM      6289    0.00    0.04    0.04     0  apache2
05:11:15 PM      6308    0.00    0.02    0.02     0  apache2
05:11:15 PM      6405    0.00    0.01    0.01     0  apache2
05:11:15 PM      6443    0.01    0.01    0.02     0  apache2
05:11:15 PM      6465    0.00    0.02    0.02     0  apache2
05:11:15 PM      6474    0.01    0.01    0.02     0  apache2
05:11:15 PM      6505    0.00    0.02    0.02     0  apache2
05:11:15 PM      6508    0.00    0.03    0.03     0  apache2
05:11:15 PM      6531    0.00    0.02    0.02     0  apache2
05:11:15 PM      6558    0.00    0.03    0.03    10  apache2
05:11:15 PM      6602    0.01    0.04    0.05     7  apache2
05:11:15 PM      6611    0.00    0.04    0.04     8  apache2
05:11:15 PM      6612    0.00    0.06    0.06     0  apache2
05:11:15 PM      6618    0.01    0.02    0.03    10  apache2
05:11:15 PM      6621    0.00    0.02    0.02     0  apache2
05:11:15 PM      6623    0.00    0.01    0.01     0  apache2
05:11:15 PM      6625    0.04    0.03    0.07     0  apache2
05:11:15 PM      6629    0.01    0.03    0.04     2  apache2
05:11:15 PM      6833    0.00    0.01    0.01     0  apache2
05:11:15 PM      6836    0.01    0.01    0.02     0  apache2
05:11:15 PM      6837    0.00    0.01    0.01    12  apache2
05:11:15 PM      6948    0.00    0.02    0.02     8  apache2
05:11:15 PM      6950    0.00    0.01    0.01     6  apache2
05:11:15 PM      6953    0.04    0.01    0.05     0  apache2
05:11:15 PM      6954    0.00    0.02    0.02     0  apache2
05:11:15 PM      6956    0.01    0.04    0.04     0  apache2
05:11:15 PM      6961    0.01    0.01    0.01     0  apache2
05:11:15 PM      6978    0.00    0.02    0.02    11  apache2
05:11:15 PM      6982    0.00    0.01    0.01     6  apache2
05:11:15 PM      6984    0.00    0.01    0.01     0  apache2
05:11:15 PM      6985    0.04    0.01    0.06     7  apache2
05:11:15 PM      6987    0.00    0.01    0.01     0  apache2
05:11:15 PM      6989    0.09    0.10    0.19     0  apache2
05:11:15 PM      6990    0.03    0.02    0.05     0  apache2
05:11:15 PM      6991    0.00    0.01    0.01    10  apache2
05:11:15 PM      7077    0.00    0.04    0.04     7  kipmi0
05:11:15 PM      7123    0.00    0.01    0.01     4  smtpd
05:11:15 PM      7153    0.00    0.01    0.01    10  dsm_sa_datamgr3
05:11:15 PM      7170    0.01    0.01    0.01     2  apache2
05:11:15 PM      7179    0.01    0.04    0.05     2  apache2
05:11:15 PM      7200    0.01    0.01    0.03    12  apache2
05:11:15 PM      7211    0.02    0.00    0.02     6  apache2
05:11:15 PM      7213    0.01    0.03    0.04     2  apache2
05:11:15 PM      7215    0.19    0.09    0.28     0  apache2
05:11:15 PM      7237    0.01    0.04    0.05     0  apache2
05:11:15 PM      7239    0.00    0.02    0.02     2  apache2
05:11:15 PM      7240    0.01    0.04    0.04     0  apache2
05:11:15 PM      7241    0.01    0.01    0.02     0  apache2
05:11:15 PM      7244    0.11    0.15    0.26     8  apache2
05:11:15 PM      7245    0.03    0.02    0.05     0  apache2
05:11:15 PM      7246    0.02    0.03    0.05     4  apache2
05:11:15 PM      7248    0.03    0.02    0.05     0  apache2
05:11:15 PM      7325    0.01    0.01    0.02     7  apache2
05:11:15 PM      7327    0.01    0.04    0.06     8  apache2
05:11:15 PM      7363    0.00    0.01    0.01     0  apache2
05:11:15 PM      7372    0.31    0.10    0.41     2  apache2
05:11:15 PM      7402    0.01    0.04    0.04     8  apache2
05:11:15 PM      7408    0.15    0.09    0.24     0  apache2
05:11:15 PM      7409    0.20    0.09    0.29     6  apache2
05:11:15 PM      7458    0.01    0.07    0.08     6  ispconfig_httpd
05:11:15 PM      7538    0.04    0.03    0.07     0  apache2
```

Server is located in Czech Republic and I called local Dell support.

I am going to search the new kernel.

Thanks
SupuS

---

### Post by SupuS on 2009-12-04
> **apel_2804 said:**
> 
You also can check with top if there is an "kipmi0" module which is possibly going crazy. If so, try to deinstall OMSA or install latest version (6.1).

I deinstall OMSA and install version 6.0.1 but problem persist.

> **apel_2804 said:**
> You can deactivate the whole system services (UEFI, Diagnostics, Virtual Media) by enteing Ctrl+E during POST (iDRAC BIOS) and set "System Services" to off.

Now I have deactivated System Services but problem is still here even worst because of presence of much more high loads than before. For example sar detected 4 minutes failure after 05:50:01:

```
# sar -s 05:45:00 -e 06:00:00
Linux 2.6.24-25-server (server.example.com)  12/04/2009

05:45:01 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
05:46:01 AM     all      1.69      0.03      0.43      0.00      0.00     97.85
05:47:01 AM     all      2.71      0.02      0.66      0.01      0.00     96.59
05:48:01 AM     all      1.59      0.03      0.50      0.06      0.00     97.82
05:49:01 AM     all      1.20      0.02      0.56      0.03      0.00     98.19
05:50:01 AM     all      2.85      0.04      1.75      0.01      0.00     95.35
05:54:21 AM     all     17.09      0.19     13.07      0.00      0.00     69.64
05:55:01 AM     all      5.84      0.00      8.15      0.11      0.00     85.90
05:56:01 AM     all      2.73      0.04      0.88      0.05      0.00     96.30
05:57:01 AM     all      2.31      0.02      0.47      0.01      0.00     97.19
05:58:01 AM     all      2.07      0.02      0.46      0.01      0.00     97.44
05:59:01 AM     all      2.34      0.02      0.67      0.06      0.00     96.91
Average:        all      2.45      0.02      1.23      0.03      0.00     96.26
```

I tested new kernel too. Just for quick testing I used kernel 2.6.31.14.27 from ubuntu karmic but I stopped testing because server crashed two times direct after restart when Dell welcome screen disappeared. On the KVM I saw black screen for the first time and blinking cursor for the second time. I had to call serverhousing technician for hard reset. Ctrl+Alt+Del in KVM didn't worked. (Server crashed exactly same way after restart when Dell technician changed motherboard but I didn't deal with it because problem disappear with next reboot.)

For third time new kernel load sucessfully but it was problem with drivers and network didn't work. I didn't tested more because of 30 minutes outage instead of 10 minute, which I planned.

Now I am waiting for an email from dell technician for the second day. But probably I have to call support and explain everything further technician again :mad:

SupuS

---

### Post by apel_2804 on 2009-12-08
I'm sorry that performing those step's didn't fixed the issue. I would like to hear what happend in last days. Did they replaced anything and is it fixed now?

---

### Post by SupuS on 2009-12-09
> **apel_2804 said:**
> I'm sorry that performing those step's didn't fixed the issue. I would like to hear what happend in last days. Did they replaced anything and is it fixed now?

Hi apel_2804

Last night, I moved all the sites hosted on this server to a backup server. Blackouts are becoming more common .. approximately 1 or 2 blackout per hour and they are from 2 to 5 minutes. Yesterday I called dell technician and he promised me to solve it today and send someone who will repair it. Unfortunately until now no one called me. Tomorrow I will call again and try to sort it out.

I tried shut down all services (apache, mysql, cron atc.) to test if some of them are causing this problem but blackouts are still present without any lines in syslog.

Now I want to try to upgrade to Ubuntu 9.10 server edition. If it is software bug it may be helps. But I don't think that it is the problem in software, because of problems with boot as I described earlier.

Last Dell technician (fourth) told me the details of the exchanged parts. It was a 1 processor, motherboard and PERC.

My technician told me that the raid controller is very hot and he thinks it's the problem. Raid controller is placed behind the processor and is not sufficiently cooled.

Now I hope for the quick repair, because I already spent a lot of time and extra money with this server :(

Thanks for any advice or direction.

EDIT: You can see what tell me zabbix monitoring (at 16:45 I stopped all services):
[[IMG]http://img697.imageshack.us/img697/9928/monitoring3.th.png[/IMG]](http://img697.imageshack.us/i/monitoring3.png/)

SupuS

---

### Post by sciric on 2009-12-11
Hi SupuS

Finally I found someone who has exactly the same problem as I do.

I'm running Ubuntu 8.04 LTS on a Dell R710 with kernel 2.6.24-24-server #1 SMP Fri Sep 18 16:47:05 UTC 2009 x86_64 GNU/Linux and experience the exact same behaviour:

- random blackouts (system is pingable, but does not start any task for a blackout period of approx 2-5 minutes total randomly). Sometimes it doesn't happen at all, sometimes it happens 2 - 3 times a day.

I have tried various things, such as:

- deactivating cron jobs
- keeping a runner open that fires a new process every second writing debug to syslog

Nothing helped - when the problem occurs all system processes just stall for a few minutes (the process that tries to log to syslog simply can't execute).

I thought it could have something to do with the PERC 6/i raid controller, so I tried various settings such as disabling writeback cache, setting it to write through. Nothing helped, also the megacli raidevent log does not reveal any information.

It would be good to know if this is a Ubuntu specific problem or if it's actually a hard/firmware related issue. I didn't try so far disabling the dell system services.

I somebody has/had a similar problem with Ubuntu 8.04 LTS on Dell Servers, please share your experiences.

Thanks a lot
Ric

---

### Post by SupuS on 2009-12-11
> **sciric said:**
> Hi SupuS

Finally I found someone who has exactly the same problem as I do.

I'm running Ubuntu 8.04 LTS on a Dell R710 with kernel 2.6.24-24-server #1 SMP Fri Sep 18 16:47:05 UTC 2009 x86_64 GNU/Linux and experience the exact same behaviour:

- random blackouts (system is pingable, but does not start any task for a blackout period of approx 2-5 minutes total randomly). Sometimes it doesn't happen at all, sometimes it happens 2 - 3 times a day.

I have tried various things, such as:

- deactivating cron jobs
- keeping a runner open that fires a new process every second writing debug to syslog

Nothing helped - when the problem occurs all system processes just stall for a few minutes (the process that tries to log to syslog simply can't execute).

I thought it could have something to do with the PERC 6/i raid controller, so I tried various settings such as disabling writeback cache, setting it to write through. Nothing helped, also the megacli raidevent log does not reveal any information.

It would be good to know if this is a Ubuntu specific problem or if it's actually a hard/firmware related issue. I didn't try so far disabling the dell system services.

I somebody has/had a similar problem with Ubuntu 8.04 LTS on Dell Servers, please share your experiences.

Thanks a lot
Ric


Hi Ric

Yesterday I upgraded to Ubuntu 9.10 and everything looks just fine. Today I did a clean install and at this time I monitor the server if everything is okay. So far it looks good.

Problems with start after reboot of the server were probably caused by a bug in the hard drive ST9146852SS Firmware. After consultation with the Dell technician I upgraded from version HT0 to HT04 that fixes these problems. Uprade is available  [here]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R236889&SystemID=pwe_r610&servicetag=DZW6D4J&os=NAA&osl=en&deviceid=20412&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=3&libid=44&typeid=-1&dateid=-1&formatid=-1&fileid=348234"). You can use this upgrade on Ubuntu too with few modifications. I can help you with this modifications if necessary.

Hope this help.

SupuS

---

### Post by Mitek on 2010-02-10
> **sciric said:**
> Hi SupuS

I somebody has/had a similar problem with Ubuntu 8.04 LTS on Dell Servers, please share your experiences.

Thanks a lot
Ric

Hello, I believe we have the same problem on a Dell PE R710
Please see my post here
[http://ubuntuforums.org/showthread.php?t=1403658](http://ubuntuforums.org/showthread.php?t=1403658)

As for now I cannot take chances since it's a production machine. Hope we'll find the answer

---

### Post by sciric on 2010-02-10
> **Mitek said:**
> Hello, I believe we have the same problem on a Dell PE R710
Please see my post here
[http://ubuntuforums.org/showthread.php?t=1403658](http://ubuntuforums.org/showthread.php?t=1403658)

As for now I cannot take chances since it's a production machine. Hope we'll find the answer


I believe the problem is kernel related. There must be a problem with Ubuntu 8.04 LTS on Dell R710.

We recently upgraded the kernel (manually compiled) to 2.6.32.7 and the freezes since then have gone.

---

### Post by rwecker on 2010-02-10
We are also having the same problem on a Dell PE R710 Ubuntu 8.04.3 any help would be appreciated.

---

### Post by rwecker on 2010-02-11
so where is the best instructions on compiling a kernel for ubuntu server (this beeing a production machine i cannot really afford to get the settings wrong.) 

thanks

---

### Post by touareger on 2010-04-01
I am having the similar issue with Dell PE R200 server running Ubuntu 9.10 Server AMD64, acted as Mysql Database Server @5.1.37. Basically, it encounters failure (both mysql transaction and ping) 1 or 2 times a day in 1-2 minutes interval. I am glad I am not alone. I have no idea how to proceed now.

---

### Post by Juergen Neumann on 2010-07-16
Hi all,

I can confirm. We have the very same issue on at least 3 servers. The system blackouts/hangs randomly once a day for about 2 to 4 minutes. Kernel is 2.6.24-28-server #1 SMP Thu May 27 00:03:15 UTC 2010 x86_64 GNU/Linux on DELL PowerEdge R710. I think these problems started by the time we switched from 32 to 64bit OS some months ago. I also think it is very likely to be a kernel issue.

vmstat just stops like most of the rest, but if you type 'date' in the console constantly during blackout the clock moves on.

---

### Post by forumID on 2010-07-16
Same issue here. System blackout at random time once almost every day. 

Any updates?

---

### Post by forumID on 2010-07-19
There is now a bug report at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607167](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607167)

---

### Post by Avada Kedavra on 2010-09-22
Same here, seen on 2 different Dell PowerEdge R710 machines with PERC 6/i RAID controller and kernel 2.6.24-24-server SMP x86_64.

---

### Post by Jiangbin Zhao on 2010-11-05
Hi all,

Any update on this issue?

We are having the same problem with three Dell r610s. The machines are running custom built 64-bit 2.6.26 kernel. They black out for about 5 minutes after a day or so. The blackouts don't seem to be caused by load. We have seen it happening with or without load.

We haven't seen this problem on other Dell models that run the same software/kernel.

Can anyone confirm whether this is kernel-related or a hardware issue?

For those who have upgraded the kernel, did the new kernel fix the problem?

Thanks in advance for any feedback.

Jiangbin

---

