---
title: "help me some a minor quirk in my daily email reports"
date: 2007-08-19
forum: Server Platforms
---

### Post by James79 on 2007-08-19
I've setup my server to send me daily email reports. Every morning (via cron) the following script will be executed:

```


echo "System" > /root/report.txt
echo "------" >> /root/report.txt
date >> /root/report.txt
uptime >> /root/report.txt
echo >> /root/report.txt

apt-get update

echo "Available Updates" >> /root/report.txt
echo "-----------------" >> /root/report.txt
echo `apt-show-versions -u | sort` >> /root/report.txt
echo >> /root/report.txt

echo "Failed Login Attempts" >> /root/report.txt
echo "---------------------" >> /root/report.txt
cat /var/log/auth.log | grep -i "Invalid user" >> /root/report.txt
cat /var/log/auth.log | grep -i "Failed password for" >> /root/report.txt
echo >> /root/report.txt

echo "Drive Status" >> /root/report.txt
echo "------------" >> /root/report.txt
df >> /root/report.txt

cat /root/report.txt | ssmtp -s test myemail@isp.com

rm /root/report.txt

```

Here is a sample email:

```

System
------
Mon Jul 30 06:00:01 EDT 2007
 06:00:01 up 46 days,  9:31,  0 users,  load average: 0.32, 0.07, 0.02

Available Updates
-----------------
linux-server/edgy upgradeable from 2.6.17.11 to 2.6.17.12.1 libkrb53/edgy upgradeable from 1.4.3-9ubuntu1.2 to 1.4.3-9ubuntu1.3 libisccfg1/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 liblwres9/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 dnsutils/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 linux-libc-dev/edgy upgradeable from 2.6.17.1-11.38 to 2.6.17.1-12.39 php5-common/edgy upgradeable from 5.1.6-1ubuntu2.5 to 5.1.6-1ubuntu2.6 iptables/edgy upgradeable from 1.3.5.0debian1-1ubuntu2 to 1.3.5.0debian1-1ubuntu2.1 php5-mysql/edgy upgradeable from 5.1.6-1ubuntu2.5 to 5.1.6-1ubuntu2.6 libbind9-0/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 libisccc0/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 tcpdump/edgy upgradeable from 3.9.4-4ubuntu0.1 to 3.9.4-4ubuntu0.2 libisc11/edgy upgradeable from 1:9.3.2-2ubuntu3.1 to 1:9.3.2-2ubuntu3.2 libapache2-mod-php5/edgy upgradeable from 5.1.6-1ubuntu2.5 to 5.1.6-1u

Failed Login Attempts
---------------------

Drive Status
------------
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             38092968   7591896  28566048  21% /
varrun                   63020       148     62872   1% /var/run
varlock                  63020         0     63020   0% /var/lock
procbususb               10240        84     10156   1% /proc/bus/usb
udev                     10240        84     10156   1% /dev
devshm                   63020         0     63020   0% /dev/shm

```

The problem is under "available updates"... the newlines aren't being interepreted correctly, and the entirety of the output appears on a single line. Can anyone think of a fix ?

---

### Post by Mr. C. on 2007-08-20
The problem is newlines are replaced by spaces when you run a command in backquotes or assign the output of a command to a variable.

This:

```
echo `apt-show-versions -u | sort` >> /root/report.txt
```

should be:

```
apt-show-versions -u | sort >> /root/report.txt
```

There is no reason to echo the output of a command that already writes to STDOUT.

MrC

ps. do you know about logwatch ?

---

### Post by James79 on 2007-08-20
Ok, well that both solved and didn't solve my problem :)

Using my ISP's webmail interface I was able to determine that your suggestion did in fact solve the newline problem (as it does in fact now look ok from there). However, outlook still doesn't display it properly.

So I guess it has become an email client issue now. Unless you can think of a way of getting outlook to interpret the newlines properly? The output from "df" for instance does appear correct.

I'll look into logwatch. I needed to figure out how to send myself emails from the command line anyways, and this script you see was just an experiment that grew out from those test. It's crude, yes, but it does work for me :)

Thanks for your help!

---

### Post by Mr. C. on 2007-08-20
Outlook has the ability to squeeze and remove blank lines.  I think at the top of the message, there should be a control to enable/disable this removal.

I no longer run Outlook, and don't recall if that will solve the problem.  You may need to mime-encode the message.

Try adding:

```
echo "MIME-Version: 1.0\n" > /root/report.txt
echo "Content-Type: text/plain; charset=\"iso-8859-1\"\n\n" >> /root/report.txt
```

to the top of your script, before any output.  Don't forget to change your (current) first > redirection into >>

MrC

---

### Post by James79 on 2007-08-21
I found a way to permanently disable the automatic removal of "extra" line breaks in text emails in the options menu. Everything is perfect now and looks great, thanks a million!

---

