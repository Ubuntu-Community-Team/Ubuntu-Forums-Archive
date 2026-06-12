---
title: "MRTG Help - Graphs Not Updating"
date: 2011-08-26
forum: Server Platforms
---

### Post by mruiz@ic-sa.com on 2011-08-26
I am having problems with getting my MRTG graphs to update.  I got the website to respond and pulled the first intial information, however, MRTG is not updating.  The process is running.  

Here is what I got .


root@XXXXX-VirtualBox:/etc# cat mrtg.cfg 
# Created by 
# /usr/bin/cfgmaker public@localhost


### Global Config Options

#  for UNIX
# WorkDir: /home/http/mrtg

#  for Debian
WorkDir: /var/www/mrtg

#  or for NT
# WorkDir: c:\mrtgdata

### Global Defaults

#  to get bits instead of bytes and graphs growing to the right
Options[_]:bits, growright
EnableIPv6: no
RunAsDaemon: Yes
WriteExpires: Yes

######################################################################
# System: XXXX-VirtualBox
# Description: Linux XXXX-VirtualBox 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
# Contact: Me <me@example.org>
# Location: Sitting on the Dock of the Bay
######################################################################


root@xxx-VirtualBox:/etc# 

oot@mruiz-VirtualBox:/var/www/mrtg# ls -al
total 21520
drwxr-xr-x 2 root root  69632 2011-08-26 16:53 .
drwxr-xr-x 3 root root   4096 2011-08-26 12:43 ..
-rw-r--r-- 1 root root   1454 2011-08-26 16:07 192.168.7.10_eo0_0-day.png
-rw-r--r-- 1 root root   6453 2011-08-26 16:07 192.168.7.10_eo0_0.html
-rw-r--r-- 1 root root  48231 2011-08-26 16:07 192.168.7.10_eo0_0.log
-rw-r--r-- 1 root root   1423 2011-08-26 16:07 192.168.7.10_eo0_0-month.png
-rw-r--r-- 1 root root  48198 2011-08-26 16:07 192.168.7.10_eo0_0.old
-rw-r--r-- 1 root root   1474 2011-08-26 16:07 192.168.7.10_eo0_0-week.png
-rw-r--r-- 1 root root   1744 2011-08-26 16:07 192.168.7.10_eo0_0-year.png
-rw-r--r-- 1 root root   1454 2011-08-26 16:07 192.168.7.10_fa2_11-day.png
-rw-r--r-- 1 root root   6424 2011-08-26 16:07 192.168.7.10_fa2_11.html


omit....
root@XXXX-VirtualBox:/var/www/mrtg# cat ROUTER-A.cfg | more
# Created by 
# /usr/bin/cfgmaker public@192.168.7.10


### Global Config Options

#  for UNIX
# WorkDir: /home/http/mrtg

#  for Debian
WorkDir: /var/www/mrtg

#  or for NT
# WorkDir: c:\mrtgdata

### Global Defaults

#  to get bits instead of bytes and graphs growing to the right
# Options[_]: growright, bits

EnableIPv6: no
WriteExpires: Yes
RunAsDaemon: Yes

######################################################################
# System: ROUTER-A
# Description: Cisco Internetwork Operating System Software 
#          IOS (tm) s72033_rp Software (s72033_rp-ADVIPSERVICESK9_WAN-M), Version 12.2(18)SXE5, RELEASE SOFTWARE (fc1)
#          Technical Support: [http://www.cisco.com/techsupport](http://www.cisco.com/techsupport)
#          Copyright (c) 1986-2006 by cisco Systems, Inc.
# Contact: 
# Location: 
######################################################################



### Interface 1 >> Descr: 'GigabitEthernet1/1' | Name: 'Gig1/1' | Ip: '' | Eth: '00-15-f9-1d-8e-50' ###

Target[192.168.7.10_Te1_1]: #Gig1/1:public@192.168.7.10:
SetEnv[192.168.7.10_Te1_1]: MRTG_INT_IP="" MRTG_INT_DESCR="GigabitEthernet1/1"
MaxBytes[192.168.7.10_Te1_1]: 536870911
Title[192.168.7.10_Te1_1]: Traffic Analysis for Gig1/1 -- ROUTER-A.publicans.com
PageTop[192.168.7.10_Te1_1]: <h1>Traffic Analysis for Gig1/1 -- ROUTE-A
/h1>
                <div id="sysdetails">
                        <table>
                                <tr>
                                        <td>System:</td>
                                        <td>ROUTER-A in </td>
                                </tr>
                                <tr>
                                        <td>Maintainer:</td>
                                        <td></td>
                                </tr>

Any help or configuration examples will be appreciated.  Thank you again.

---

### Post by SeijiSensei on 2011-08-26
Last time I ran MRTG it used a cron job to update its information, one that ran every five minutes.  For instance, and /etc/crontab entry like this:

```
*/5 * * * * root /path/to/mrtg /path/to/mrtg.cfg
```

As far as I can recall, it doesn't update automatically, only via cron.

---

### Post by mruiz@ic-sa.com on 2011-08-29
> **SeijiSensei said:**
> Last time I ran MRTG it used a cron job to update its information, one that ran every five minutes.  For instance, and /etc/crontab entry like this:

```
*/5 * * * * root /path/to/mrtg /path/to/mrtg.cfg
```As far as I can recall, it doesn't update automatically, only via cron.

how about this?

*/5* *** root  if [-x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]

---

### Post by SeijiSensei on 2011-08-29
> **mruiz@ic-sa.com said:**
> how about this?

*/5* *** root  if [-x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]

First, you need spaces between the stars.  Also I don't understand quite what you're trying to accomplish with this command.  Why not use just the simple command I gave above?  I don't really see any need to test for whether mrtg exists and is executable, for instance.  It should exist and be executable by default.

Have you tried running mrtg as root with sudo from the command line using the command I gave?  What happens?

---

### Post by mruiz@ic-sa.com on 2011-08-29
> **SeijiSensei said:**
> First, you need spaces between the stars.  Also I don't understand quite what you're trying to accomplish with this command.  Why not use just the simple command I gave above?  I don't really see any need to test for whether mrtg exists and is executable, for instance.  It should exist and be executable by default.

Have you tried running mrtg as root with sudo from the command line using the command I gave?  What happens?


I will try that.  That command i pulled from the cron.d directory.

---

### Post by mruiz@ic-sa.com on 2011-08-29
> **mruiz@ic-sa.com said:**
> I will try that.  That command i pulled from the cron.d directory.


root@mruiz-VirtualBox:/usr/bin# ls -al | grep mrtg
-rwxr-xr-x  1 root   root     104255 2011-01-01 00:08 mrtg
-rwxr-xr-x  1 root   root       9584 2010-10-17 05:45 mrtg-apache
-rwxr-xr-x  1 root   root       9556 2010-10-17 05:45 mrtg-ip-acct
-rwxr-xr-x  1 root   root       9540 2010-10-17 05:45 mrtg-load
-rwxr-xr-x  1 root   root       9580 2010-10-17 05:45 mrtg-sensors
root@mruiz-VirtualBox:/usr/bin# */5 * * * * root /usr/bin/mrtg /etc/mrtg.cfg
-bash: */5: No such file or directory
root@mruiz-VirtualBox:/usr/bin# cd mrtg
-bash: cd: mrtg: Not a directory
root@mruiz-VirtualBox:/usr/bin# pwd
/usr/bin
root@mruiz-VirtualBox:/usr/bin# 

This is what i got.

---

### Post by mruiz@ic-sa.com on 2011-08-29
> **SeijiSensei said:**
> First, you need spaces between the stars.  Also I don't understand quite what you're trying to accomplish with this command.  Why not use just the simple command I gave above?  I don't really see any need to test for whether mrtg exists and is executable, for instance.  It should exist and be executable by default.

Have you tried running mrtg as root with sudo from the command line using the command I gave?  What happens?

This is what is in my crontab.

I hope that helps.

Thank you. 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

---

### Post by SeijiSensei on 2011-08-29
> **mruiz@ic-sa.com said:**
> This is what is in my crontab.

# **m h dom mon dow** user command
[...]
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

Just add

```
*/5 * * * * root /usr/bin/mrtg /etc/mrtg.cfg
```

on a separate line at the bottom of /etc/crontab.  The first five entries correspond to the time codes - **m**inutes, **h**ours, day of month (**dom**), **mon**th, and day of week (**dow**).  The entry for mrtg says to run the command whenever the clock shows a number of minutes exactly divisible by five.  The stars say to run this command  on all days and times.

Before doing that, though, try running

```
sudo /usr/bin/mrtg /etc/mrtg.cfg
```

from a command prompt to make sure the command works.  What happens?

---

### Post by mruiz@ic-sa.com on 2011-08-30
> **SeijiSensei said:**
> Just add

```
*/5 * * * * root /usr/bin/mrtg /etc/mrtg.cfg
```on a separate line at the bottom of /etc/crontab.  The first five entries correspond to the time codes - **m**inutes, **h**ours, day of month (**dom**), **mon**th, and day of week (**dow**).  The entry for mrtg says to run the command whenever the clock shows a number of minutes exactly divisible by five.  The stars say to run this command  on all days and times.

Before doing that, though, try running

```
sudo /usr/bin/mrtg /etc/mrtg.cfg
```from a command prompt to make sure the command works.  What happens?

This is what happens?

mruiz@mruiz-VirtualBox:~$ sudo /usr/bin/mrtg /etc/mrtg.cfg
[sudo] password for mruiz: 
-----------------------------------------------------------------------
ERROR: Mrtg will most likely not work properly when the environment
       variable LANG is set to UTF-8. Please run mrtg in an environment
       where this is not the case. Try the following command to start:

       env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 
-----------------------------------------------------------------------
mruiz@mruiz-VirtualBox:~$ 

Thoughts ?

---

### Post by tangozopo on 2012-09-06
l am also having problems with mrtg and have tried your solution. below is the output l am getting:
root@terry:~# /usr/bin/mrtg /etc/mrtg.cfg
-----------------------------------------------------------------------
ERROR: Mrtg will most likely not work properly when the environment
       variable LANG is set to UTF-8. Please run mrtg in an environment
       where this is not the case. Try the following command to start:

       env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 
-----------------------------------------------------------------------

and:

root@terry:~# env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 
Use of uninitialized value $flags in recv at /usr/share/perl5/SNMP_Session.pm line 857.
Use of uninitialized value $flags in recv at /usr/share/perl5/SNMP_Session.pm line 857.
Use of uninitialized value $flags in recv at /usr/share/perl5/SNMP_Session.pm line 857.
Use of uninitialized value $flags in recv at /usr/share/perl5/SNMP_Session.pm line 857.
root@terry:~# 

And if follow the path to SNMP_Session line 857, this is what is there:
sub receive_response_3 {
    my ($this, $response_tag, $oids, $errorp, $dont_block_p) = @_;
    my ($remote_addr);
    my $flags = 0;
    $flags = $dont_wait_flags if defined $dont_block_p and $dont_block_p;
    $remote_addr = recv ($this->sock,$this->{'pdu_buffer'},$this->max_pdu_len,$flags);
    return $this->error ("receiving response PDU: $!")
        unless defined $remote_addr;
    return $this->error ("short (".length $this->{'pdu_buffer'}
                         ." bytes) response PDU")
        unless length $this->{'pdu_buffer'} > 2;
    my $response = $this->{'pdu_buffer'};

Please, anybody assist.

---

### Post by SeijiSensei on 2012-09-07
"env" is a c-shell command.  Ubuntu uses the bash or dash shells.  Try using 

```

# export LANG=C; /usr/bin/mrtg /etc/mrtg.cfg

```

Any better?

---

### Post by tangozopo on 2012-09-07
> **SeijiSensei said:**
> "env" is a c-shell command.  Ubuntu uses the bash or dash shells.  Try using 

```

# export LANG=C; /usr/bin/mrtg /etc/mrtg.cfg

```Any better?

Sorry, l am not a linux guru, do l have to put this in a script, and if so how do l make the script exutable. If its going to be a cron job thing how do l go about it. Please just explain in detail. Thanks in advance.

Ok. Editing this post. l did run the command manually and it still retains the same message.

---

### Post by SeijiSensei on 2012-09-07
I'm afraid I can't be much more help than that.  I've only ever used mrtg on RedHat/CentOS servers, and a long time ago at that.

You might want to take a look at [ntop]("https://help.ubuntu.com/community/Ntop") as an alternative.

---

### Post by Asator on 2013-04-24
> **mruiz@ic-sa.com said:**
> I am having problems with getting my MRTG graphs to update.  I got the website to respond and pulled the first intial information, however, MRTG is not updating.  The process is running.  

Here is what I got .


root@XXXXX-VirtualBox:/etc# cat mrtg.cfg 
# Created by 
# /usr/bin/cfgmaker public@localhost


### Global Config Options

#  for UNIX
# WorkDir: /home/http/mrtg

#  for Debian
WorkDir: /var/www/mrtg

#  or for NT
# WorkDir: c:\mrtgdata

### Global Defaults

[COLOR=#ff0000][B]#  to get bits instead of bytes and graphs growing to the right
Options[_]:bits, growright
EnableIPv6: no
RunAsDaemon: Yes
WriteExpires: Yes[/B][/COLOR]



I know this was posted a really long time ago, but I was searching for an MRTG problem and this forum came up. I can't just leave it unanswered. I'm almost positive your problem lies above in red.
You don't have an interval set up, your config should be as shown below:

#  to get bits instead of bytes and graphs growing to the right
Options[_]: growright, bits
RunAsDaemon: Yes
[COLOR=#ff0000]**Interval: 5**[/COLOR]
Logdir: /var/log/
EnableIPv6: no

This will make the graphs update every 5 minutes. I'm assuming since you have no interval set, they don't update at all. Hope this helps.

---

