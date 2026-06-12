---
title: "Nagios Basics"
date: 2009-01-17
forum: Server Platforms
---

### Post by Drezard on 2009-01-17
Trying to set up a Nagios3 server. Entered this command:

```

apt-get install nagios3
htpasswd -c htpasswd.users nagios
(entered password)
reboot

```

But when I go into //localhost/nagios3 into firefox, it allows me to login (asks for HTTP authentication) I enter in the username and password and it loads the next page but the next page has a 500 internal error. 

It seems like the Nagios3 server is set up incorrectly. But I haven't set anything up as of yet. Now I know theres a per-flight check you can do (to make sure you havent screwed up any of the details) this is what happens:

```

test:/etc# nagios3 -v /etc/nagios3/nagios.cfg

Nagios 3.0.6
Copyright (c) 1999-2008 Ethan Galstad (http://www.nagios.org)
Last Modified: 12-01-2008
License: GPL

Reading configuration data...

Running pre-flight check on configuration data...

Checking services...
        Checked 7 services.
Checking hosts...
        Checked 2 hosts.
Checking host groups...
        Checked 5 host groups.
Checking service groups...
        Checked 0 service groups.
Checking contacts...
        Checked 2 contacts.
Checking contact groups...
        Checked 1 contact groups.
Checking service escalations...
        Checked 0 service escalations.
Checking service dependencies...
        Checked 0 service dependencies.
Checking host escalations...
        Checked 0 host escalations.
Checking host dependencies...
        Checked 0 host dependencies.
Checking commands...
        Checked 153 commands.
Checking time periods...
        Checked 4 time periods.
Checking for circular paths between hosts...
Checking for circular host and service dependencies...
Checking global event handlers...
Checking obsessive compulsive processor commands...
Checking misc settings...

Total Warnings: 0
Total Errors:   0

Things look okay - No serious problems were detected during the pre-flight check

```

So what the heck is wrong!

Regards,

Daniel

---

### Post by Kosmonaut on 2009-01-20
Hi!

Did you take a look at [https://help.ubuntu.com/community/Nagios2](https://help.ubuntu.com/community/Nagios2)

Perhaps you should try this:
```
sudo htpasswd -c htpasswd.users nagiosadmin
```
then
```
sudo /etc/init.d/apache2 restart
```
```
sudo /etc/init.d/nagios3 restart
```
Then try to login as "nagiosadmin" (@localhost/nagios3)

Hope this helps.

Cheers K.

---

### Post by HermanAB on 2009-01-20
Hmm, once you are tired of fighting Nagios, try Zabbix - you won't look back.

Cheers,

Herman

---

### Post by dipeshmehta on 2009-06-04
> **HermanAB said:**
> Hmm, once you are tired of fighting Nagios, try Zabbix - you won't look back.

Cheers,

Herman

Hello,

Can you please suggest me a good howto and/or tutorial for Zabbix?

Thanks in advance.

Dipesh

---

### Post by samosamo on 2009-06-04
I tried Nagios by itself, I tried Zabbix, I tried them all.  I have to suggest GroundWork Open Source.  I had a working installation in 5 minutes.

---

### Post by ballscout1 on 2012-03-09
> **dipeshmehta said:**
> Hello,
 
Can you please suggest me a good howto and/or tutorial for Zabbix?
 
Thanks in advance.
 
Dipesh
 
 
There are many available  ,here are a couple
 
 
[http://bobcares.com/blog/?p=303](http://bobcares.com/blog/?p=303)
 
[http://blog.malaya-digital.org/setup-zabbix-1-8-6-in-a-minimal-ubuntu-11-04-64-bit-server-install/](http://blog.malaya-digital.org/setup-zabbix-1-8-6-in-a-minimal-ubuntu-11-04-64-bit-server-install/)
 
[http://nitishkumar.net/2010/01/03/zabbix-the-simple-yet-ultimate-monitoring-solution-for-corporate/](http://nitishkumar.net/2010/01/03/zabbix-the-simple-yet-ultimate-monitoring-solution-for-corporate/)

---

### Post by koenn on 2012-03-09
"500 internal server error" is a message from your (apache) web server, not from nagios. check apache error logs to see what it is complaining about

---

### Post by HugoSerrano on 2012-03-09
It's just me, or this post it's from 2009??

:-D

---

### Post by koenn on 2012-03-09
oops.
It showed up at the top of the page, didn't notice the date on the OP. 

Oh well.

---

### Post by stando007 on 2012-03-30
Hi,
maybe somebody could help me with one issue regarding monitoring transmission-daemon with nagios3. I have created configuration file: /etc/nagios-plugins/config/my_own.cfg

in this file I defined this command:
```
define command{
        command_name    check_transmission
        command_line    /usr/lib/nagios/plugins/check_procs -c 1:1 --metric=PROCS -a "/usr/bin/transmission-daemon"
        }

```

then added this command into /etc/nagios3/conf.d/localhost_nagios2.cfg:

```
#Check for transmission process
define service{
        use                             generic-service         ; Name of service template to use
        host_name                       localhost
        service_description             Transmission daemon
                check_command                   check_transmission
        }

```

Everything is fine, but nagios throws CRITICAL alarm that 2 processes of transmission daemon is running. Strange, when I check for transmission by ps:
```
ps ax | grep trans
12568 ?        Ssl    0:00 /usr/bin/transmission-daemon --config-dir /var/lib/transmission-daemon/info
12680 pts/0    S+     0:00 grep --color=auto trans

```

then when I try the nagios plugin check in command line:

```
/usr/lib/nagios/plugins/check_procs -c 1:1 --metric=PROCS -a "/usr/bin/transmission-daemon"
PROCS OK: 1 process with args '/usr/bin/transmission-daemon'

```
--> nagios plugin returns OK - 1 Process. But in the nagios GUI I still have "PROCS CRITICAL: 2 processes with args '/usr/bin/transmission-daemon'"

Anyone has idea why such strange behavior?

---

### Post by Habitual on 2012-03-30
> **stando007 said:**
> ...Strange, when I check for transmission by ps:
```
ps ax | grep trans
12568 ?        Ssl    0:00 /usr/bin/transmission-daemon --config-dir /var/lib/transmission-daemon/info
12680 pts/0    S+     0:00 grep --color=auto trans

```

try ```
ps ax | grep trans | [COLOR=Red]grep -v grep[/COLOR]
```One of those hits is is the grep command grep'ing for transmission. A False positive.

HTH.

---

### Post by stando007 on 2012-04-02
Yes, I know 
```
ps ax | grep trans
```
will return 2 matches (one is the grep command itself)
But when executing
```
/usr/lib/nagios/plugins/check_procs -c 1:1 --metric=PROCS -a "/usr/bin/transmission-daemon"
```
it returns **1 PROCESS** (PROCS OK: 1 process with args '/usr/bin/transmission-daemon') from the command line, but in the nagios gui the same command lists 2 PROCS... That's the issue

---

### Post by stando007 on 2012-04-19
No ideas?

---

### Post by Habitual on 2012-04-19
Try 
```
pidof transmission-daemon
```

how many transmission-daemon processes are running?

---

