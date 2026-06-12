---
title: "iptables logging"
date: 2011-03-29
forum: Server Platforms
---

### Post by metalix on 2011-03-29
Good evening,

I have been trying for most of the afternoon to get iptables to log correctly.

I have followed the guide here: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo), and I just cannot seem to find any log entries:

Here are the steps I am taking:

1. Insert a rule to jump to LOG for all packets (at the bottom of rules list);
2. Restart the sysklogd service;
3. Ping my server (it isn't getting through when the firewall is enabled)
4. Read through /var/log/messages

I cannot find any log messages. What am I doing wrong here?

---

### Post by Doug S on 2011-03-29
It is hard to say what is wrong without more information.
You can observe the packets/byte counters in iptables to determine if you actually ever got to the step of trying to write any logs entries. Two ways:
 
"sudo iptables-save -c"
 
and/or
 
"sudo iptables -v -x -n -L"
 
Edited example partial outputs:
 
```
 
[66:3960] -A INPUT -i eth1 -m recent --update --seconds 5400 --hitcount 3 --name BADGUY_SSH --rsource -j LOG --log-prefix "SSH BAD:" --log-level 6
[66:3960] -A INPUT -i eth1 -m recent --update --seconds 5400 --hitcount 3 --name BADGUY_SSH --rsource -j DROP
 

```
 
```
 
      66     3960 LOG        all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source LOG flags 0 level 6 prefix `SSH BAD:'
      66     3960 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source
 

```
 
So, in my case, I know that I should have 66 entries in /var/log/syslog and /var/log/messages (or syslog.1 or syslog.2... (some hits are days old)
 
I do not think your step 2 is needed.
If your iptables rule set is thorough, you might well never have any packets getting to the end of the rule of set (I never do). For a test / sanity check, try to log packets right from the start of the rule set.

---

### Post by metalix on 2011-03-30
Thanks for replying Doug.

This is what I am getting when I list the rules:

```
Chain INPUT (policy DROP 9 packets, 440 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     368    28304 ACCEPT     tcp  --  *      *       0.0.0.0/0            109.109.129.213     tcp dpt:62501 state NEW,ESTABLISHED
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       9      440 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy DROP 18 packets, 1368 bytes)
    pkts      bytes target     prot opt in     out     source               destination
     298    78636 ACCEPT     tcp  --  *      *       109.109.129.213      0.0.0.0/0           tcp spt:62501 state NEW,ESTABLISHED
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
```

The number is going up when I try to access the HTTP service, but there are still no entries in /var/log/messages

---

### Post by Doug S on 2011-03-30
O.K. I agree you should have 9 log entries in /var/log/messages and /var/log/syslog.
Just to be sure, I changed my rule to be like yours, log level to 4 from 6 and removed my log prefix and still got the entries.
 
There maybe some configuration issue related to iptables logging, but I am not familiar with such changes. 
 
Just for completeness, below are my test outputs, the counters and the syslog entries (it is me trying to access via SSH from 209.121.28.186 to create the log entries):
 
```
 
       4      192 LOG        all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source LOG flags 0 level 4
       4      192 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 5400 hit_count: 3 name: BADGUY_SSH side: source
 

```
 
```
 
Mar 29 23:50:58 doug-64 kernel: [2876796.184883] IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:14:bf:bc:25:ee:08:00 SRC=209.121.28.186 DST=209.121.28.192 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=14532 DF PROTO=TCP SPT=3227 DPT=22 WINDOW=25200 RES=0x00 SYN URGP=0
Mar 29 23:51:01 doug-64 kernel: [2876799.105331] IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:14:bf:bc:25:ee:08:00 SRC=209.121.28.186 DST=209.121.28.192 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=14541 DF PROTO=TCP SPT=3227 DPT=22 WINDOW=25200 RES=0x00 SYN URGP=0
Mar 29 23:51:07 doug-64 kernel: [2876805.114651] IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:14:bf:bc:25:ee:08:00 SRC=209.121.28.186 DST=209.121.28.192 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=14565 DF PROTO=TCP SPT=3227 DPT=22 WINDOW=25200 RES=0x00 SYN URGP=0
Mar 29 23:51:19 doug-64 kernel: [2876817.133680] IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:00:14:bf:bc:25:ee:08:00 SRC=209.121.28.186 DST=209.121.28.192 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=14610 DF PROTO=TCP SPT=3227 DPT=22 WINDOW=25200 RES=0x00 SYN URGP=0
 

```
 
Maybe on your system your log entires go somewhere else. For example see: [http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

---

### Post by metalix on 2011-03-30
Mmm...

I did some digging around /var/log/ and could not find any logs anywhere.

This is the contents of the /etc/syslog.conf file:

```
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*          -/var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                  -/var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.info                       -/var/log/mail.info
mail.warning                    -/var/log/mail.warn
mail.err                 -/var/log/mail.err

# Logging for INN news system
#
news.crit                -/var/log/news/news.crit
news.err                 -/var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warning;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warning    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warning    |/dev/xconsole

```

Strange, eh.

I want to take another approach to setting up my firewall, using the following rules:

INPUT, FORWARD chains shall have a DROP policy
OUTPUT shall have an ACCEPT policy

INPUT
Let all packets for existing connections (is this safe?)
Let packets for SSH port
Log the rest (will it still be dropped?)

OUTPUT
Log everything (will it still be accepted?)

This should allow me to continue using apt-get and other services that I request from the server, whilst blocking everything except returns and SSH requests, right?

Right, these are the rules I have for logging and testing. Do you see anything wrong with them? Am I missing something major?

> Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       7      464 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            109.109.129.213     tcp dpt:23525
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `IPTABLES DROP (in): '

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 9 packets, 1308 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       9     1308 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `IPTABLES ACCEPT (out): '

---

### Post by Doug S on 2011-03-30
I can see from your syslog.conf file that you are using an older linux version.
I don't know when things changed, but now rsyslog.conf is used.
So, I went over to my old old Ubuntu Server 6.06 box and compared your syslog.conf with mine. While there are many differences, according to the MAN pages, they don't matter. Yours uses "warning", mine uses "warn", but MAN pages says they are the same. Yours always has "-" leading the file path and name, sometimes mine doesn't, but that only determines if the buffer is written out for every log entry or not.
 
So, I do not have an explaination for why you are not getting the log entries.
 
To try to answer the other questions:
 
Yes, after the log entry the next step will be back in the main chain ("Jump" to log is really a "Call" to log), and therefore DROP in the INPUT chain.
 
I think the OUTPUT chain questions was answered by your counters, you can see that every packet that was logged also went to the default ACCEPT.
 
If you are wanting to accept SSH connections, then I would have to guess that sshd is monitoring port 23525 instead of port 22.
 
For logging and testing they look minimal, but O.K. (I assume you are watching things closely while you test).

---

### Post by metalix on 2011-03-31
Thanks for replying.

I'm using 10.04, so I'm not sure why that file is being used.

I would certainly like to look at what's going on, but I have not logs! My thoughts are to block everything, and open things up as I need them. Is my script relatively safe?

---

### Post by metalix on 2011-09-15
I'm still having issues with this.

I am running a (nearly) free install.

Here are my rules:

```
#!/bin/sh

# Constants - settings
PUBLIC_INT="[removed]"
CLIENT_INT="[removed]"
LOOPBACK_INT="lo"
SSH_PORT=[removed]
MYSQL_PORT=[removed]

# Flush old rules
sudo ../droprules.sh

echo -n "Setting new rules..."
# Set policies
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

# Logging chain
iptables -N LOG_DROP
iptables -A LOG_DROP -j LOG --log-tcp-options --log-ip-options --log-prefix "[IPTABLES DROP] : "
iptables -A LOG_DROP -j DROP

# INPUT RULES
# Allow loopback packets
iptables -A INPUT -i $LOOPBACK_INT -j ACCEPT
# Allow packets from established and related connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow SSH packets
iptables -A INPUT -p tcp --dport $SSH_PORT -j ACCEPT
# Allow MySQL, through client IP address
iptables -A INPUT -d $CLIENT_INT -p tcp --dport $MYSQL_PORT -j ACCEPT
# Drop anything else
iptables -A INPUT -j LOG_DROP

# FORWARD RULES
# Drop everything
iptables -A FORWARD -j LOG_DROP

# OUTPUT RULES
# Allow loopback traffic
iptables -A OUTPUT -o $LOOPBACK_INT -j ACCEPT
# Allow SSH output traffic
iptables -A OUTPUT -p tcp --sport $SSH_PORT -j ACCEPT
# Allow outward MySQL packets
iptables -A OUTPUT -s $CLIENT_INT -p tcp --sport $MYSQL_PORT -j ACCEPT
# Allow outbound FTP
#iptables -A OUTPUT -p tcp --dport 80 --sport 32768:61000 -j ACCEPT
# Drop everything else
#iptables -A OUTPUT -j DROP

echo "done"

echo "New rules:\n\n"
iptables -v -L
echo "\n"

```

And here is the contents of my syslogd.conf file:

```
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*          -/var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                  -/var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info

mail.warning                    -/var/log/mail.warn
mail.err                 -/var/log/mail.err

# Logging for INN news system
#
news.crit                -/var/log/news/news.crit
news.err                 -/var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warning;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warning    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warning    |/dev/xconsole

```

It's imperative that I am able to read my iptables logs. I've gone through all of the log files in /var/log and I cannot find anything in there.

I have tried sending some HTTP packets to the server (which are blocked) and these are showing in the IPTABLES status, if I list it.

Where am I going wrong?

I am using Ubuntu 10.04.3 LTS, as a VPS hosted by WizzVPS.

---

### Post by metalix on 2011-09-15
**UPDATE**
I tried using the "dmesg" command, and the log messages are displayed! But I'm confused; they're not in the "/var/logs/dmesg" file.

I want to be able to log these into a MySQL database; what's the best method for that?

---

### Post by elico on 2011-09-15
if you dont have any log files on /var/log you might having problem with the syslog.
try to purge it and then reinstall it using:
apt-get purge sysklogd syslog-ng
and then reinstall the sysklogd using:
apt-get install sysklogd
see what you got now on the /var/log dir.
i might be wrong but this is what i understood from your information.

---

### Post by metalix on 2011-09-15
Thanks for the reply.

There's plenty of log files in the /var/log directory, it's just none of them have my IPTABLES logs in.

Is there a command line file search utility I can use, to search for where the output of "dmesg" is stored?

---

