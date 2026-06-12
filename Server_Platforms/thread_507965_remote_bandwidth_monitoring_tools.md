---
title: "remote bandwidth monitoring tools"
date: 2007-07-23
forum: Server Platforms
---

### Post by rbprogrammer on 2007-07-23
ok, my problem is that my ISP provider (probably like many) have bandwidth limits.. but then i also have a web server and an ftp server up and running, so what i need is a program that will allow me to monitor my bandwidth through my eth0 device.

i have checked out [this thread]("http://ubuntuforums.org/showthread.php?t=215754"), but the tools there (ie bom, ibmonitor, etc..) do not allow me to **remotely** monitor my bandwidth consumption.

what i really need is some program that runs in the background that is recording my bandwidth consumption, then maybe through one of my servers that are set up i can just view a graph or something.  i dont need anything that administers anything, i just need to monitor it.

---

### Post by rbprogrammer on 2007-07-23
also, if at all possible, would i be able to monitor the bandwidth of all the computers in my home network??

---

### Post by darkog on 2007-07-23
try ntop

---

### Post by Mr. C. on 2007-07-23
The ifconfig utility reports gross byte transfers:

```
ifconfig eth0
```

or 

```
ifconfig eth0 | grep bytes
```

to just see the byte counts.  You can ssh to your server and run:

```
ssh myserver ifconfig eth0  grep bytes
```

MrC

---

### Post by gombadi on 2007-07-24
vnstat will allow you to monitor bandwidth usage.

apt-get install vnstat is all it takes.

You can run it from cron and get it to email reports like below whenever you want.

```

bob@bob:~$ vnstat -h
 eth0                                                                     17:50 
  ^                                          t                                  
  |                              t           t                                  
  |                              t     t     t                                  
  |                              t  t  t     t  t                               
  |                        t  t  t  t  t  t  t  t     t  t                      
  |                  t     t  t  t  t  t  t  t  t     t  t                      
  |               t  t  t  t  t  t  t  t  t  t  t     t  t  t     t             
  |      t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t          
  |   t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t       
  |   t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t  t    
 -+---------------------------------------------------------------------------> 
  |  18 19 20 21 22 23 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 16 17    
                                                                                
 h   rx (kB)    tx (kB)      h   rx (kB)    tx (kB)      h   rx (kB)    tx (kB) 
18      30029     772453    02      48741    1629634    10      54576    1636419
19      51733     919344    03      67957    2456856    11      52273    1664437
20      34508     927839    04      85458    1878589    12      36166    1248453
21      33797     920875    05      76950    2182181    13      28416     803424
22      42741    1263026    06      51767    1805522    14      40598    1140795
23      46445    1355250    07      78428    2604065    15      34745    1032360
00      41509    1186449    08      50033    1950760    16      25058     602981
01      49203    1566503    09      36354     966357    17      18087     485988

bob@bob:~$ vnstat -d

        eth0

            day         rx      |     tx      |  total
        ------------------------+-------------+--------------
           25.06.      1310 MB  |   32269 MB  |   33579 MB
           26.06.      1201 MB  |   39001 MB  |   40202 MB
           27.06.      1098 MB  |   31251 MB  |   32350 MB
           28.06.      1305 MB  |   39730 MB  |   41036 MB
           29.06.      1223 MB  |   33272 MB  |   34496 MB
           30.06.      1036 MB  |   30418 MB  |   31454 MB
           01.07.      1155 MB  |   35509 MB  |   36664 MB
           02.07.      1089 MB  |   34876 MB  |   35966 MB
           03.07.      1239 MB  |   38974 MB  |   40214 MB
           04.07.      1073 MB  |   32318 MB  |   33391 MB
           05.07.    975.68 MB  |   31341 MB  |   32317 MB
           06.07.      1122 MB  |   34920 MB  |   36042 MB
           07.07.      1038 MB  |   29782 MB  |   30820 MB
           08.07.      1129 MB  |   33227 MB  |   34357 MB
           09.07.    942.60 MB  |   26853 MB  |   27796 MB
           10.07.      2136 MB  |   29575 MB  |   31711 MB
           11.07.      1262 MB  |   37661 MB  |   38923 MB
           12.07.      1271 MB  |   38430 MB  |   39701 MB
           13.07.      1019 MB  |   32770 MB  |   33790 MB
           14.07.    959.62 MB  |   28774 MB  |   29734 MB
           15.07.      1633 MB  |   35794 MB  |   37428 MB
           16.07.      1213 MB  |   36485 MB  |   37698 MB
           17.07.      1000 MB  |   30089 MB  |   31090 MB
           18.07.    991.50 MB  |   30273 MB  |   31265 MB
           19.07.      1278 MB  |   39340 MB  |   40619 MB
           20.07.      1244 MB  |   37471 MB  |   38716 MB
           21.07.      1226 MB  |   35847 MB  |   37074 MB
           22.07.      1085 MB  |   33078 MB  |   34164 MB
           23.07.      1069 MB  |   31848 MB  |   32917 MB
           24.07.    855.78 MB  |   26212 MB  |   27068 MB
        ------------------------+-------------+--------------
         estimated     1147 MB  |   35177 MB  |   36324 MB

bob@bob:~$ vnstat -m

        eth0

           month        rx      |       tx      |    total
        ------------------------+---------------+---------------
          Apr '07     39085 MB  |    872782 MB  |    911868 MB
          May '07     50574 MB  |   1438978 MB  |   1489552 MB
          Jun '07     53183 MB  |   1258327 MB  |   1311511 MB
          Jul '07     28015 MB  |    801459 MB  |    829474 MB
        ------------------------+---------------+---------------
        estimated     36631 MB  |   1047953 MB  |   1084584 MB



```

---

### Post by kvonb on 2007-07-24
> **gombadi said:**
> vnstat will allow you to monitor bandwidth usage.

apt-get install vnstat is all it takes.

You can run it from cron and get it to email reports like below whenever you want.


Wow, nice one gombadi :)

You wouldn't be a complete gentleman/lady and tell us the commands for the cron job that emails those reports out would you?  Or give us a copy of the script you use?

That would be really nice :).

---

### Post by gombadi on 2007-07-24
This is the crontab entry I use to email the report to my mailbox every day just after midnight.

bob@bob:~$ crontab -l
04 00 * * * /home/bob/bin/traff.sh


And here is the script - Adjust to suit your requirements :)

```

#!/bin/bash

{
# display daily total
vnstat

echo
echo "**************************************************"
echo "Hourly data"
echo
vnstat -h

echo
echo "**************************************************"
echo "Daily data"
echo
vnstat -d

echo
echo "**************************************************"
echo "Weekly data"
echo
vnstat -w

echo
echo "**************************************************"
echo "Monthly data"
echo
vnstat -m

echo
} | mail -s "vnstat data from $(hostname)" user@domain.com


```

---

### Post by kvonb on 2007-07-24
Thankyou very much gombadi, I'll attempt to get that working later :)

---

### Post by Mr. C. on 2007-07-24
Nice little tool.

It doesn't quite meet the OPs requirement, as the OP wants to measure not bandwidth used on one computer, but bandwidth available on the network.  Two different task, requiring two different methods.

MrC

---

### Post by rbprogrammer on 2007-07-25
MrC, when i do:
> **Mr. C. said:**
> 
```
ssh myserver ifconfig eth0  grep bytes
```

i get this error:
```
ssh: connect to host 192.168.2.37 port 22: Connection refused
```
do i have to install or do anything special to get the server to have port 22 enabled??

also, gombadi, it looks like script you supplied us with uses a "mail" command, when i tried to use the mail command i got:
```
$ mail
The program 'mail' can be found in the following packages:
 * mailx
 * mailutils
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: mail: command not found

```
i was just wondering which package you have installed..

thanks for all the help everybody :) ..

---

### Post by gombadi on 2007-07-25
Either mailx or mailutils will give you the mail command - I think I installed mailutils.

To get port 22 working you will need to install the ssh server on 192.168.2.37 so you can connect to it and run commands or login.

As root on 192.168.2.37 type - apt-get install openssh-server

---

### Post by Mr. C. on 2007-07-26
Do you have an SSH server running on the remote host ?  That is necessary for the command I supplied.

MrC

---

### Post by rbprogrammer on 2007-07-30
> **gombadi said:**
> This is the crontab entry I use to email the report to my mailbox every day just after midnight.

bob@bob:~$ crontab -l
04 00 * * * /home/bob/bin/traff.sh


And here is the script - Adjust to suit your requirements :)

```

#!/bin/bash

{
# display daily total
vnstat

echo
echo "**************************************************"
echo "Hourly data"
echo
vnstat -h

echo
echo "**************************************************"
echo "Daily data"
echo
vnstat -d

echo
echo "**************************************************"
echo "Weekly data"
echo
vnstat -w

echo
echo "**************************************************"
echo "Monthly data"
echo
vnstat -m

echo
} | mail -s "vnstat data from $(hostname)" user@domain.com


```

i was wishing i was able to monitor bandwidth on my whole network, but pondering that situation a little bit more, i realized i would probably need to set up a program to work with my router, since my router cannot already monitor bandwidth.  or i can make all computers connected to the internet connect through my server.  but both situations would be way too much work for something that is not that big of a deal.

but, for monitoring my server, this works damn good \\:D/
nice work gombadi

---

### Post by rbprogrammer on 2007-08-01
ok, now there is a little problem, the script does not email me anything.. :confused:

i have had it up for a couple of days and i set it so that it should execute at 12:00a, but i have not received any emails.  just to be clear, i want to emails to be sent to my [http://www.mail.com/](http://www.mail.com/) account.  that is possible with the script you supplied, right gombadi??

---

### Post by Mr. C. on 2007-08-01
Run the script manually.  Check your logs for mail messages to determine what has occurred.  Check /var/log/maillog and /var/log/syslog after you run the script.

MrC

---

### Post by rbprogrammer on 2007-08-01
in [FONT="Courier New"]/var/log/maillog[/FONT], its just a blank file..

in [FONT="Courier New"]/var/log/syslog[/FONT] i have this:
```
Aug  1 07:35:48 SERVER-DURSO syslogd 1.4.1#20ubuntu4: restart.
Aug  1 07:35:48 SERVER-DURSO anacron[18503]: Job `cron.daily' terminated
Aug  1 07:39:01 SERVER-DURSO /USR/SBIN/CRON[18737]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 07:40:01 SERVER-DURSO anacron[18503]: Job `cron.weekly' started
Aug  1 07:40:01 SERVER-DURSO anacron[18752]: Updated timestamp for job `cron.weekly' to 2007-08-01
Aug  1 07:40:01 SERVER-DURSO /USR/SBIN/CRON[18756]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 07:40:02 SERVER-DURSO syslogd 1.4.1#20ubuntu4: restart.
Aug  1 07:40:02 SERVER-DURSO anacron[18503]: Job `cron.weekly' terminated
Aug  1 07:40:02 SERVER-DURSO anacron[18503]: Normal exit (2 jobs run)
Aug  1 07:45:01 SERVER-DURSO /USR/SBIN/CRON[18932]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 07:50:01 SERVER-DURSO /USR/SBIN/CRON[18953]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 07:55:01 SERVER-DURSO /USR/SBIN/CRON[18973]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:00:01 SERVER-DURSO /USR/SBIN/CRON[18998]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:05:01 SERVER-DURSO /USR/SBIN/CRON[19030]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:08:54 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 08:08:54 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 08:08:54 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 08:08:54 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3217 seconds.
Aug  1 08:09:01 SERVER-DURSO /USR/SBIN/CRON[19071]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 08:10:01 SERVER-DURSO /USR/SBIN/CRON[19084]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:15:01 SERVER-DURSO /USR/SBIN/CRON[19110]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:17:01 SERVER-DURSO /USR/SBIN/CRON[19126]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 08:20:01 SERVER-DURSO /USR/SBIN/CRON[19145]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:25:01 SERVER-DURSO /USR/SBIN/CRON[19169]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:30:01 SERVER-DURSO /USR/SBIN/CRON[19201]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:35:01 SERVER-DURSO /USR/SBIN/CRON[19229]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:39:01 SERVER-DURSO /USR/SBIN/CRON[19255]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 08:40:01 SERVER-DURSO /USR/SBIN/CRON[19267]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:45:01 SERVER-DURSO /USR/SBIN/CRON[19297]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:50:01 SERVER-DURSO /USR/SBIN/CRON[19323]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 08:55:01 SERVER-DURSO /USR/SBIN/CRON[19352]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:00:01 SERVER-DURSO /USR/SBIN/CRON[19383]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:02:31 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 09:02:31 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 09:02:31 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 09:02:31 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 2954 seconds.
Aug  1 09:05:01 SERVER-DURSO /USR/SBIN/CRON[19429]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:09:01 SERVER-DURSO /USR/SBIN/CRON[19456]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 09:10:01 SERVER-DURSO /USR/SBIN/CRON[19468]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:15:01 SERVER-DURSO /USR/SBIN/CRON[19501]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:17:01 SERVER-DURSO /USR/SBIN/CRON[19517]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 09:20:01 SERVER-DURSO /USR/SBIN/CRON[19534]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:25:01 SERVER-DURSO /USR/SBIN/CRON[19563]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:30:01 SERVER-DURSO /USR/SBIN/CRON[19594]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:35:01 SERVER-DURSO /USR/SBIN/CRON[19624]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:39:01 SERVER-DURSO /USR/SBIN/CRON[19643]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 09:40:01 SERVER-DURSO /USR/SBIN/CRON[19653]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:45:01 SERVER-DURSO /USR/SBIN/CRON[19675]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:50:01 SERVER-DURSO /USR/SBIN/CRON[19701]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 09:51:45 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 09:51:45 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 09:51:45 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 09:51:45 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3478 seconds.
Aug  1 09:55:01 SERVER-DURSO /USR/SBIN/CRON[19740]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:00:01 SERVER-DURSO /USR/SBIN/CRON[19764]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:05:01 SERVER-DURSO /USR/SBIN/CRON[19786]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:09:01 SERVER-DURSO /USR/SBIN/CRON[19808]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 10:10:01 SERVER-DURSO /USR/SBIN/CRON[19818]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:15:01 SERVER-DURSO /USR/SBIN/CRON[19839]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:16:01 SERVER-DURSO ddclient[5116]: WARNING:  cannot connect to checkip.dyndns.org:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.org'
Aug  1 10:17:01 SERVER-DURSO /USR/SBIN/CRON[19848]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 10:20:02 SERVER-DURSO /USR/SBIN/CRON[19860]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:25:01 SERVER-DURSO /USR/SBIN/CRON[19881]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:26:21 SERVER-DURSO ddclient[5116]: WARNING:  cannot connect to checkip.dyndns.org:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.org'
Aug  1 10:30:01 SERVER-DURSO /USR/SBIN/CRON[19902]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:35:01 SERVER-DURSO /USR/SBIN/CRON[19923]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:39:01 SERVER-DURSO /USR/SBIN/CRON[19940]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 10:40:01 SERVER-DURSO /USR/SBIN/CRON[19950]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:45:01 SERVER-DURSO /USR/SBIN/CRON[19971]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:49:43 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 10:49:43 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 10:49:43 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 10:49:43 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3409 seconds.
Aug  1 10:50:01 SERVER-DURSO /USR/SBIN/CRON[20006]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 10:55:01 SERVER-DURSO /USR/SBIN/CRON[20027]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:00:01 SERVER-DURSO /USR/SBIN/CRON[20049]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:05:01 SERVER-DURSO /USR/SBIN/CRON[20070]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:09:01 SERVER-DURSO /USR/SBIN/CRON[20088]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 11:10:01 SERVER-DURSO /USR/SBIN/CRON[20098]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:15:01 SERVER-DURSO /USR/SBIN/CRON[20119]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:17:01 SERVER-DURSO /USR/SBIN/CRON[20131]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 11:20:01 SERVER-DURSO /USR/SBIN/CRON[20143]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:25:01 SERVER-DURSO /USR/SBIN/CRON[20163]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:30:01 SERVER-DURSO /USR/SBIN/CRON[20185]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:35:01 SERVER-DURSO /USR/SBIN/CRON[20207]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:39:01 SERVER-DURSO /USR/SBIN/CRON[20225]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 11:40:01 SERVER-DURSO /USR/SBIN/CRON[20235]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:45:01 SERVER-DURSO /USR/SBIN/CRON[20256]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:46:32 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 11:46:32 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 11:46:32 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 11:46:32 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 2958 seconds.
Aug  1 11:50:01 SERVER-DURSO /USR/SBIN/CRON[20291]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 11:55:01 SERVER-DURSO /USR/SBIN/CRON[20312]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:00:01 SERVER-DURSO /USR/SBIN/CRON[20331]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:05:01 SERVER-DURSO /USR/SBIN/CRON[20349]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:09:01 SERVER-DURSO /USR/SBIN/CRON[20365]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 12:10:01 SERVER-DURSO /USR/SBIN/CRON[20374]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:15:01 SERVER-DURSO /USR/SBIN/CRON[20392]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:17:01 SERVER-DURSO /USR/SBIN/CRON[20403]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 12:20:01 SERVER-DURSO /USR/SBIN/CRON[20413]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:25:01 SERVER-DURSO /USR/SBIN/CRON[20434]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:30:01 SERVER-DURSO /USR/SBIN/CRON[20456]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:35:01 SERVER-DURSO /USR/SBIN/CRON[20476]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:35:50 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 12:35:50 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 12:35:50 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 12:35:50 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 2888 seconds.
Aug  1 12:39:01 SERVER-DURSO /USR/SBIN/CRON[20508]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 12:40:01 SERVER-DURSO /USR/SBIN/CRON[20518]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:45:01 SERVER-DURSO /USR/SBIN/CRON[20541]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:50:01 SERVER-DURSO /USR/SBIN/CRON[20561]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 12:55:01 SERVER-DURSO /USR/SBIN/CRON[20582]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:00:01 SERVER-DURSO /USR/SBIN/CRON[20603]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:05:01 SERVER-DURSO /USR/SBIN/CRON[20624]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:09:01 SERVER-DURSO /USR/SBIN/CRON[20642]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 13:10:01 SERVER-DURSO /USR/SBIN/CRON[20652]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:15:01 SERVER-DURSO /USR/SBIN/CRON[20672]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:17:01 SERVER-DURSO /USR/SBIN/CRON[20684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 13:20:01 SERVER-DURSO /USR/SBIN/CRON[20696]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:23:58 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 13:23:58 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 13:23:58 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 13:23:58 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3175 seconds.
Aug  1 13:25:01 SERVER-DURSO /USR/SBIN/CRON[20731]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:30:01 SERVER-DURSO /USR/SBIN/CRON[20752]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:35:01 SERVER-DURSO /USR/SBIN/CRON[20773]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:39:01 SERVER-DURSO /USR/SBIN/CRON[20791]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 13:40:01 SERVER-DURSO /USR/SBIN/CRON[20801]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:45:01 SERVER-DURSO /USR/SBIN/CRON[20822]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:50:01 SERVER-DURSO /USR/SBIN/CRON[20842]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 13:55:01 SERVER-DURSO /USR/SBIN/CRON[20863]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:00:01 SERVER-DURSO /USR/SBIN/CRON[20885]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:05:01 SERVER-DURSO /USR/SBIN/CRON[20906]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:09:01 SERVER-DURSO /USR/SBIN/CRON[20924]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 14:10:01 SERVER-DURSO /USR/SBIN/CRON[20934]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:15:01 SERVER-DURSO /USR/SBIN/CRON[20954]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:16:53 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 14:16:53 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 14:16:53 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 14:16:53 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3041 seconds.
Aug  1 14:17:01 SERVER-DURSO /USR/SBIN/CRON[20980]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 14:20:01 SERVER-DURSO /USR/SBIN/CRON[20992]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:25:01 SERVER-DURSO /USR/SBIN/CRON[21013]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:30:01 SERVER-DURSO /USR/SBIN/CRON[21035]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:35:01 SERVER-DURSO /USR/SBIN/CRON[21053]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:39:01 SERVER-DURSO /USR/SBIN/CRON[21069]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 14:40:01 SERVER-DURSO /USR/SBIN/CRON[21079]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:45:01 SERVER-DURSO /USR/SBIN/CRON[21097]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:50:01 SERVER-DURSO /USR/SBIN/CRON[21115]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 14:55:01 SERVER-DURSO /USR/SBIN/CRON[21132]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:00:01 SERVER-DURSO /USR/SBIN/CRON[21150]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:05:01 SERVER-DURSO /USR/SBIN/CRON[21170]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:07:34 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 15:07:34 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 15:07:34 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 15:07:34 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3548 seconds.
Aug  1 15:09:01 SERVER-DURSO /USR/SBIN/CRON[21202]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 15:10:01 SERVER-DURSO /USR/SBIN/CRON[21212]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:13:17 SERVER-DURSO kernel: [166887.390355] usb 1-1: USB disconnect, address 3
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.679433] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if0').
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.684682] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if1').
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.687306] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial').
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.707186] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if0_logicaldev_input').
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.715110] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if1_logicaldev_input').
Aug  1 15:13:17 SERVER-DURSO NetworkManager: <debug info>^I[1185995597.750157] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_usbraw').
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.334331] usb 1-1: new low speed USB device using uhci_hcd and address 4
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.516039] usb 1-1: configuration #1 chosen from 1 choice
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.533066] input: Logitech USB Receiver as /class/input/input6
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.533112] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.567046] input: Logitech USB Receiver as /class/input/input7
Aug  1 15:14:34 SERVER-DURSO kernel: [166964.567124] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.050904] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial').
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.145744] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if0').
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.244042] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if1').
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.332621] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_usbraw').
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.367193] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if0_logicaldev_input').
Aug  1 15:14:35 SERVER-DURSO NetworkManager: <debug info>^I[1185995675.400803] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c509_noserial_if1_logicaldev_input').
Aug  1 15:15:01 SERVER-DURSO /USR/SBIN/CRON[21302]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:17:01 SERVER-DURSO /USR/SBIN/CRON[21314]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 15:20:01 SERVER-DURSO /USR/SBIN/CRON[21326]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:25:01 SERVER-DURSO /USR/SBIN/CRON[21347]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:30:01 SERVER-DURSO /USR/SBIN/CRON[21368]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:35:01 SERVER-DURSO /USR/SBIN/CRON[21389]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:39:01 SERVER-DURSO /USR/SBIN/CRON[21406]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 15:40:01 SERVER-DURSO /USR/SBIN/CRON[21416]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:45:01 SERVER-DURSO /USR/SBIN/CRON[21438]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:50:01 SERVER-DURSO /USR/SBIN/CRON[21464]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 15:55:02 SERVER-DURSO /USR/SBIN/CRON[21487]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:00:01 SERVER-DURSO /USR/SBIN/CRON[21509]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:05:01 SERVER-DURSO /USR/SBIN/CRON[21529]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:06:42 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 16:06:42 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 16:06:42 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 16:06:42 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 3228 seconds.
Aug  1 16:09:01 SERVER-DURSO /USR/SBIN/CRON[21561]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 16:10:01 SERVER-DURSO /USR/SBIN/CRON[21571]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:15:01 SERVER-DURSO /USR/SBIN/CRON[21592]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:17:01 SERVER-DURSO /USR/SBIN/CRON[21604]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  1 16:20:01 SERVER-DURSO /USR/SBIN/CRON[21615]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:25:01 SERVER-DURSO /USR/SBIN/CRON[21636]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:30:01 SERVER-DURSO /USR/SBIN/CRON[21658]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:35:01 SERVER-DURSO /USR/SBIN/CRON[21679]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:39:01 SERVER-DURSO /USR/SBIN/CRON[21697]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug  1 16:40:01 SERVER-DURSO /USR/SBIN/CRON[21707]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:45:01 SERVER-DURSO /USR/SBIN/CRON[21779]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): starting (version 2.18.0.1), pid 21895 user 'mike'
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): Resolved address "xml:readwrite:/home/mike/.gconf" to a writable configuration source at position 1
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  1 16:46:17 SERVER-DURSO gconfd (mike-21895): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  1 16:50:01 SERVER-DURSO /USR/SBIN/CRON[21920]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 16:55:01 SERVER-DURSO /USR/SBIN/CRON[21959]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 17:00:01 SERVER-DURSO /USR/SBIN/CRON[22021]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
Aug  1 17:00:30 SERVER-DURSO dhclient: DHCPREQUEST on eth0 to 192.168.2.1 port 67
Aug  1 17:00:30 SERVER-DURSO dhclient: DHCPACK from 192.168.2.1
Aug  1 17:00:30 SERVER-DURSO NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  1 17:00:30 SERVER-DURSO dhclient: bound to 192.168.2.37 -- renewal in 2933 seconds.

```
but i have check it before and after i ran the script manually, i dont see any change :confused: 

i even tried to change the email account but i still did not receive anything.

---

### Post by rbprogrammer on 2007-08-01
i noticed yesterday but didnt remember till now, that when i [FONT="Courier New"]ssh[/FONT]ed onto that computer, i got a message saying that i had new mail..

but i have no idea if that has anything to do with my problem or how to check that mail

EDIT:
 when i typed in the terminal [FONT="Courier New"]mail[/FONT], i got:
```
$ mail
"/var/mail/mike": 7 messages 7 new
>N   1 Mail Delivery Syst Mon Jul 30 20:16 114/4785  Mail delivery failed: returning message to sender
 N   2 Mail Delivery Syst Mon Jul 30 20:18 114/4785  Mail delivery failed: returning message to sender
 N   3 Mail Delivery Syst Tue Jul 31 00:05 116/4887  Mail delivery failed: returning message to sender
 N   4 Mail Delivery Syst Wed Aug  1 00:05 118/5015  Mail delivery failed: returning message to sender
 N   5 Mail Delivery Syst Wed Aug  1 16:59 118/4995  Mail delivery failed: returning message to sender
 N   6 Mail Delivery Syst Wed Aug  1 17:01 118/4995  Mail delivery failed: returning message to sender
 N   7 Mail Delivery Syst Wed Aug  1 17:04 118/5003  Mail delivery failed: returning message to sender
&  
```
and i was able to view them, and one of them looks like:
```
From: Mail Delivery System <Mailer-Daemon@SERVER-DURSO>
To: mike@SERVER-DURSO
Subject: Mail delivery failed: returning message to sender
Date: Mon, 30 Jul 2007 20:16:01 -0400

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  <myemailaddress>
    Mailing to remote domains not supported

------ This is a copy of the message, including all the headers. ------

Return-path: <mike@SERVER-DURSO>
Received: from mike by SERVER-DURSO with local (Exim 4.63)
        (envelope-from <mike@SERVER-DURSO>)
        id 1IFfP7-0001nX-DX
        for <myemailaddress>; Mon, 30 Jul 2007 20:16:01 -0400
Subject: vnstat data from SERVER-DURSO
To: <rmyemailaddress>
X-Mailer: mail (GNU Mailutils 1.1)
Message-Id: <E1IFfP7-0001nX-DX@SERVER-DURSO>
From: mike durso <mike@SERVER-DURSO>
Date: Mon, 30 Jul 2007 20:16:01 -0400

Database updated: Mon Jul 30 20:15:01 2007

        eth0

           received:          11.54 MB (61.1%)
        transmitted:           7.35 MB (38.9%)
              total:          18.89 MB

                        rx     |     tx     |  total
        -----------------------+------------+-----------
            today     11.54 MB |    7.35 MB |   18.89 MB
        -----------------------+------------+-----------
        estimated        13 MB |       8 MB |      21 MB


etc ...

```

now why cant i send the messages to remote hosts??

---

### Post by gombadi on 2007-08-01
Do you have any email server installed and running?

If not then you will need something to pickup the messages and send them off.

Some options are postfix or nullmailer.

nullmailer is a small server that just sends everything it gets out through an email relay server (i.e. isp mail server). It does not even listen on any interfaces for incoming messages.

If you need to install postfix then it would be best to make it listen on localhost only. Have not needed it till now so no need to make it open to the world. Set inet_interfaces = 127.0.0.1 in /etc/postfix/main.cf

You can test the setup to make sure it is working by -
```

ls -l | mail -s "A test message from $(hostname)" person@domain

```

---

### Post by rbprogrammer on 2007-08-01
i'm installing it now, but i'm confused as to which configuration option is best for me..

all i need is it to take the mail from the [FONT="Courier New"]mail[/FONT] program and send it to a remote host so that i can view it on that email account.

---

### Post by Mr. C. on 2007-08-01
It appears in your mail message that you had Exim installed, but it wasn't configured correctly:

```
Received: from mike by SERVER-DURSO with local (**Exim 4.63**)
        (envelope-from <mike@SERVER-DURSO>)
```

How you configure your MTA depends upon how you want to send your mail.  Is it being sent via your ISP's mail servers ?  Do they require authentication, or can anyone one their networks send email?

More details are necessary...
MrC

---

### Post by rbprogrammer on 2007-08-02
> **Mr. C. said:**
> It appears in your mail message that you had Exim installed, but it wasn't configured correctly:

```
Received: from mike by SERVER-DURSO with local (**Exim 4.63**)
        (envelope-from <mike@SERVER-DURSO>)
```

How you configure your MTA depends upon how you want to send your mail.  Is it being sent via your ISP's mail servers ?  Do they require authentication, or can anyone one their networks send email?

More details are necessary...
MrC

sorry, but i'm still a bit of a noob, i dont remember installing [FONT="Courier New"]exim[/FONT] so it was probably needed for another program or it was installed by default.

with that said, i dont know what a MTA is.  and i dont do anything with my ISP except connect to the internet.

when i was installing the [FONT="Courier New"]mail[/FONT] program, i used the "internet" option.  then in [FONT="Courier New"]/etc/postfix/main.cf[/FONT] i modified the one line to look like this inet_interfaces = 127.0.0.1

sorry again, but still a noob and i dont know what else to post :confused: ..

---

### Post by rbprogrammer on 2007-08-02
after re-reading your reply, and noticing the "MailHop Outbound" feature that [http://www.dyndns.com/](http://www.dyndns.com/) has, i thought, "would i be able to use this?" i already have an account there, so would this be something that might help??

---

### Post by Mr. C. on 2007-08-02
So you want the script to send you email, but you are unable to explain *where* you want the mail to go?  Hmmm, maybe I'm confused.

If you want your box to send email, you need to figure out *where* it will be sent.  Then, and only then, can you work out *how* it should be sent.

MrC

---

### Post by rbprogrammer on 2007-08-03
i guess what i'm saying is that i just want the mail to go from my server at home to the remote host [http://www.mail.com/](http://www.mail.com/)

i would prefer not to have to do anything with my ISP because they are a pain to work with, and they charge $$$ for anything.  i mean they even blocked port 80 and it would cost money to open it.

all i'm saying it that i'm a noob, but i just need the mail from my computer to somehow to get to my email account..

by the way, your awesome for helping me this far :) ..

---

### Post by Mr. C. on 2007-08-03
Ok, so you have an email address at mail.com, and you want a simple setup that forwards your email to that address.  And you have no desire to generally send email to other's via your server or mail.com.

I presume you are able to connect to mail.com with some mail client (eg. Eudora, Outlook, Outlook Express, Thunderbird, etc.) to receive your email, and possibly to send.  Is this correct ?

For your server to send email to mail.com, your ISP must allow port 25 outbound connections.  An alternative is port 587 *if* your mail provider supports this port (its called the submission port), but mail.com does not appear to support this.

From your Ubuntu box, in a command window, enter the following:

```
telnet mail-com.mr.outblaze.com 25
```

It should respond with :

```
Trying 208.36.123.74...
Connected to mail-com.mr.outblaze.com.
Escape character is '^]'.
220 spf16.us4.outblaze.com ESMTP Postfix

```

If you do not get a response, your ISP is blocking this connection.  You can type Control-RightBracket to exit, as mentioned above.

If you do receive the Postfix greeting, then you are able to connect.  Just type **quit** to exit the connection.

Report your findings, and we'll go from there.
MrC

---

### Post by rbprogrammer on 2007-08-03
this is what i got:
```

$ telnet mail-com.mr.outblaze.com 25
Trying 208.36.123.68...
Connected to mail-com.mr.outblaze.com.
Escape character is '^]'.
220 spf8.us4.outblaze.com ESMTP Postfix
421 spf8.us4.outblaze.com Error: timeout exceeded
Connection closed by foreign host.

```
does this mean my ISP is blocking port 25??
if so, what are my options??

---

### Post by Mr. C. on 2007-08-03
This is good; it means you can connect.

Now, you have to configure an MTA (mail transfer agent) to deliver the mail to your mail provider.

The simplest method would be to install **ssmtp** and replace your mail command in your script with ssmtp, as in:

```
ssmtp -s "*Subject here*" *user@example.com*
```

where you fill in the subject and email address appropriately.

I believe ssmtp is in the repositories; use apt-get install to install it.

MrC

---

### Post by rbprogrammer on 2007-08-03
in TrafficMonitor.sh i have:
```
#!/bin/bash
{
    # display daily total
    vnstat

    #display hourly total
    echo
    echo "**************************************************"
    echo "Hourly data"
    echo
    vnstat -h

    # display daily total
    echo
    echo "**************************************************"
    echo "Daily data"
    echo
    vnstat -d

    # display weekly total
    echo
    echo "**************************************************"
    echo "Weekly data"
    echo
    vnstat -w

    # display monthly total
    echo
    echo "**************************************************"
    echo "Monthly data"
    echo
    vnstat -m

    echo
} | ssmtp -s "vnstat data from $(hostname)" email@address.net

```
and then when i manually execute it i get:
```

$ ./TrafficMonitor.sh
ssmtp: Cannot open mail:25

```
or when i just execute ssmtp i get nothing, it just waits there:
```
$ ssmtp -s "some subject" email@address.net
```
i thought after i install [FONT="Courier New"]ssmtp[/FONT], my MTA would be configured??

---

### Post by Mr. C. on 2007-08-03
Two different things here.

1. Did you configure the ssmtp.conf file ?  See:

man ssmtp.conf
man ssmtp

ssmtp needs a From address, and needs to know which mailhost to use.

2. The second test you did is waiting for you to enter an email message.  ssmtp reads from STDIN.

MrC

---

### Post by rbprogrammer on 2007-08-03
my [FONT="Courier New"]/etc/ssmtp/ssmtp.conf[/FONT]:
```

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=SERVER-DURSO

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

```
now doing a [FONT="Courier New"]man ssmtp.conf[/FONT] i _think_ i need to change the one line to:
```
mailhub=mail-com.mr.outblaze.com:25
```
and probably the [FONT="Courier New"]rewriteDomain[/FONT], but i'm not sure

:lolflag: i think it it blatantly clear that i dont understand how email is sent/received.. so thanks again for the help

---

### Post by Mr. C. on 2007-08-03
Set :
```

mailhub=mail-com.mr.outblaze.com
```

MrC

---

### Post by rbprogrammer on 2007-08-05
with this in my script:
```

#!/bin/bash

{
    # display daily total
    vnstat

    #display hourly total
    echo
    echo "**************************************************"
    echo "Hourly data"
    echo
    vnstat -h

    # display daily total
    echo
    echo "**************************************************"
    echo "Daily data"
    echo
    vnstat -d

    # display weekly total
    echo
    echo "**************************************************"
    echo "Weekly data"
    echo
    vnstat -w

    # display monthly total
    echo
    echo "**************************************************"
    echo "Monthly data"
    echo
    vnstat -m

    echo
} | ssmtp -s "vnstat data from $(hostname)" emailacc@mail.com

```
and this as my [FONT="Courier New"]/etc/ssmtp/ssmtp.conf[/FONT]
```

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mmail-com.mr.outblaze.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=SERVER-DURSO

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

```

i get this error:
```

$ ./TrafficMonitor.sh
ssmtp: Cannot open mmail-com.mr.outblaze.com:25

```

is this configuration right?  i mean i tried looking at [FONT="Courier New"]man ssmtp[/FONT], and googling variations of [FONT="Courier New"]ssmtp[/FONT], but i did not understand what i should do next :confused: ..

---

### Post by Mr. C. on 2007-08-05
I personally spell mail with one m

```
mailhub=[color=red]m[/color]mail-com.mr.outblaze.com
```

MrC

---

### Post by rbprogrammer on 2007-08-05
> **Mr. C. said:**
> I personally spell mail with one m

```
mailhub=[color=red]m[/color]mail-com.mr.outblaze.com
```

MrC

yup, me too.. i always make mistakes like that :lolflag: 

but when i took out that extra **[FONT="Courier New"]m[/FONT]**, i got another error:
```

$ ./TrafficMonitor.sh
ssmtp: RCPT TO:<vnstat data from SERVER-DURSO@SERVER-DURSO> (501 Bad address syntax)

```

---

### Post by Mr. C. on 2007-08-05
I was mistaken earlier about how you call ssmtp; sorry.

Once you've installed ssmpt, you just use the mail program, and it will send via ssmpt.

Try

```
 mail -s "subject" emailaddress
```

MrC

---

### Post by rbprogrammer on 2007-08-05
this feels like a dumb question, but when i do that command, and i press enter, i get:
```

$ mail -s "subject" rarebreed@programmer.net
Cc:

```
and it waits for input, how do i escape from that so that i dont have to enter in any [FONT="Courier New"]Cc[/FONT]??

because when i get it working, i want the shell script to do everything, not wait for input for a [FONT="Courier New"]Cc[/FONT]

---

### Post by Mr. C. on 2007-08-05
You pipe your input to mail, just like you were doing.
MrC

---

### Post by rbprogrammer on 2007-08-05
> **Mr. C. said:**
> You pipe your input to mail, just like you were doing.
MrC

not sure what "pipe" means, but but it sounds like i am doing something right..

yet i still do not get the mail in my mail.com account.. i changed the [FONT="Courier New"]ssmtp[/FONT] to [FONT="Courier New"]mail[/FONT] in the script, and when i run it i do not get any errors, but i still dont get any emails

---

### Post by Mr. C. on 2007-08-05
Replace "ssmtp" in your script with "mail".

See if you can send mail first:

```
echo Hello | mail -s "Test" emailaddr
```

MrC

---

### Post by rbprogrammer on 2007-08-07
> **Mr. C. said:**
> Replace "ssmtp" in your script with "mail".

See if you can send mail first:

```
echo Hello | mail -s "Test" emailaddr
```

MrC

when i do that command, it waits a few seconds for it to complete then it is done without errors. but i dont get any emails in my mail.com account :confused: ..

---

### Post by Mr. C. on 2007-08-07
Without being able to see your log messages, there's not much we can do.  Do you find any log message in your logs under /var/log ?

MrC

---

### Post by rbprogrammer on 2007-08-07
based on the fact that i did not get an error in the terminal window when i executed the command, [FONT="Courier New"]echo Hello | mail -s "Test" emailaddr[/FONT], i didnt even bother to look there, :oops: ...

but under [FONT="Courier New"]/var/log[/FONT], i found a few files
[LIST]
[*]mail.err
[*]mail.log
[*]mail.info
[*]mail.warn
[/LIST]
and they all look the same, at the very bottom i had this in all of the files:
```

Aug  7 16:07:59 SERVER-DURSO sSMTP[14741]: RCPT TO:<addres> (504 <mike@SERVER-DURSO>: No thank you rejected: need fully-qualified address)
Aug  7 16:09:22 SERVER-DURSO sSMTP[14769]: RCPT TO:<address> (504 <mike@SERVER-DURSO>: No thank you rejected: need fully-qualified address)

```

EDIT:

this probably doesnt help but i figured i should mention it..
i keep getting a file "[FONT="Courier New"]/home/me/dead.letter[/FONT]" that keeps showing up. i delete it then it would show up the next day.  i open it up and it is full with my mail that i am supposed to be getting but never do..

i guess i havent disabled my cron job

---

### Post by Mr. C. on 2007-08-08
Mail servers require fully qualified names when you are sending to non-local sites.

The mail server is telling you that you need to use fully qualified host names. Mail could not possible be delivered to an unqualified name, as the mail server does not know where to deliver the email.  Fully qualified email addresses are required so that mail that cannot be delivered can be bounced back to the sender.  Both sender and recipient must be fully qualified.

I see: **RCPT TO:<address>** in the error message.  I presume you obfuscated **address**, so I can't help with this.

I also see **mike@SERVER-DURSO**.  This too is not a fully qualified name.  How can the remote server bounce the message back to you>  The remote mail server has no idea where server-durso resides on the big internet.

The dead.letter is created with a mail session is killed before the mail is successfully delivered.  The mail program creates this.

MrC

---

### Post by rbprogrammer on 2007-08-08
yes, you are correct in that i just changed my actual email address to "address" for the post on the forums..

so i went back and changed a line in [FONT="Courier New"]/etc/ssmtp/ssmtp.conf[/FONT] :
```

# The full hostname

hostname=SERVER-DURSO
       **to**
hostname=rbprogrammer.is-a-geek.net

```
which is the cheesy name i picked when i created my [http://www.dyndns.com/](http://www.dyndns.com/) account

after doing that i figured i would check the logs again, and i got:
```

Aug  8 16:44:05 SERVER-DURSO sSMTP[8352]: RCPT TO:<address> (554 EMail from mailserver at 24.115.49.85 is refused. See http://spamblock.outblaze.com/24.115.49.85)

```
24.115.49.85 is my ip address

and again i changed my email address to [FONT="Courier New"]address[/FONT] for this post,.. then i checked out that spam website and it thinks that my computer (or computers near by with relatively the same ip address) is a spamming computer.  so i sent an email to the supplied email address on the site saying that the only mail coming from that computer is mail that is going straight to my account, no where else. i will just have to wait x number of days to get a reply.

so based on the error message, i'm assuming that everything is working fine on my end, its just that i have to get this "spam" thing figured out.. right?

oh please tell me i'm right [-o<

---

### Post by Mr. C. on 2007-08-09
Mail servers are configured to not allow anyone to "relay" mail through their servers without specific permission.  Your mail server is mail.com.  Unless you have a mail.com email address, or you have an account with mail.com and use an email address they recognize as beloning to them, they are likely not to allow you to relay mail through their servers.

Furthermore, residential IPs or dynamic IPs are often placed on blacklists; you are unlikely to be removed in such a case, especially since your IP is dynamic.

Best of luck,
MrC

---

### Post by rbprogrammer on 2007-08-09
so if i dont get removed, would you recommend anything else that would get my "mail" to the email account?

are there any programs that would act as the email server?

---

### Post by Mr. C. on 2007-08-09
Earlier you had said you were trying to send email to *your* mail.com account.  But the address you showed didn't seem like a mail.com address.  Was that email address a mail.com email address ?

ssmtp is an MTA (mail transfer agent), albeit a simple one.  If you want mail to go to a remote host, an MTA is what you use.

If the remote mail server does not accept your email when the server is the final destination, changing to another MTA won't solve that problem.

So, either mail.com is *not* the final destination mail server for your email address, or they require some form of authentication that ssmpt is not configured to use.

What server have you been using to send email, and how do you configure your email client to connect to that server?  Perhaps we are long overdue for you to clarify your email sending situation.

MrC

---

### Post by rbprogrammer on 2007-08-09
first off you were right,
> Furthermore, residential IPs or dynamic IPs are often placed on blacklists; you are unlikely to be removed in such a case, especially since your IP is dynamic.
this is the email i received
```

Hi

The block is because your IP is dynamic.  Please set your mailserver to
smarthost through your dsl ISP's server, or [B]through the server your dynamic
dns provider offers you[/B] (using smtp auth)

http://nillepill.blogspot.com/2007/06/ssmtp-outbound-mail-in-freebsd.html
should help you as your bounce looks like you're running sSMTP.

```
does the bolded statement say i should work through [http://www.dyndns.com/](http://www.dyndns.com/) ?  because i have a domain name and account there and i have ddclient set up so that it will update my dyndns.com account with my new ip address every so often.
also, that [http://nillepill.blogspot.com/2007/06/ssmtp-outbound-mail-in-freebsd.html](http://nillepill.blogspot.com/2007/06/ssmtp-outbound-mail-in-freebsd.html) website does not seem to help me, since it seems that FreeBSD has a different setup than linux (kubuntu).  and i dont understand how to translate their directions into something that would help me.

> 
What server have you been using to send email, and how do you configure your email client to connect to that server?

i just open firefox and go to [http://www.mail.com/](http://www.mail.com/) and sign in with my email address and password.  it's exactly like a gmail or yahoo mail account only from a  different organization.

> 
Perhaps we are long overdue for you to clarify your email sending situation.

basically i just want to be able to send an email to that account from my computer (server).  however possible, thats what i want to happen.

so with this setup for /etc/ssmtp/ssmtp.conf:
```

#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=mike

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail-com.mr.outblaze.com

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname - **my http://www.dyndns.com/ name**
hostname=rbprogrammer.is-a-geek.net

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

```
everytime i execute the command:
```

echo Hello | mail -s "Test" rarebreed@programmer.net

```
i get this error in my /var/log/mail.log:
```

Aug  9 15:45:05 SERVER-DURSO sSMTP[7172]: RCPT TO:<*my mail.com account address*> (554 EMail from mailserver at 24.115.49.85 is refused. See http://spamblock.outblaze.com/24.115.49.85)

```

---

### Post by Mr. C. on 2007-08-09
mail.com is not accepting email from your IP range.  They require you to use an "official" mail server.  You will have to find another mail server that will allow your IP range to directly send email.

MrC

---

### Post by rbprogrammer on 2007-08-09
this seems like so much work..

i think i can work around this though.  i wont send an email, but i could just create a script, whether web based or a shell script, that will create a simple log file that i will view on my web site.

thanks anyway for the tremendous help.  unfortunately it lead me to a dead end (at least with my abilities) but thanks anyway.

---

