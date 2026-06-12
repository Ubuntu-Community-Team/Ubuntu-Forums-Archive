---
title: "Strange process"
date: 2014-05-28
forum: Security
---

### Post by kurogane2 on 2014-05-28
I'm wondering the the process ".flush" its part of ubuntu because always i boot my server start this process

```
  647 root      20   0    7120    260    132 S  0.0  0.0   0:00.69 .flush
  648 root      20   0    7120    260    132 S  0.0  0.0   0:00.32 .flush
  649 root      20   0    7120    260    132 S  0.0  0.0   0:00.71 .flush
  650 root      20   0    7120    260    132 S  0.0  0.0   0:00.16 .flush
  651 root      20   0    7120    260    132 S  0.0  0.0   0:00.69 .flush

```

```

# lsof -p 647
COMMAND PID USER   FD   TYPE   DEVICE SIZE/OFF     NODE NAME
.flush  647 root  cwd    DIR     0,24     4096 51904513 /
.flush  647 root  rtd    DIR     0,24     4096 51904513 /
.flush  647 root  txt    REG     0,24   550448 51905654 /tmp/.flush
.flush  647 root  mem    REG      8,4          51905654 /tmp/.flush (path dev=0,24)
.flush  647 root    0u   CHR      1,3      0t0 30401832 /dev/null
.flush  647 root    1u   CHR      1,3      0t0 30401832 /dev/null
.flush  647 root    2u   CHR      1,3      0t0 30401832 /dev/null
.flush  647 root    3r  FIFO      0,8      0t0 30403964 pipe
.flush  647 root    4w  FIFO      0,8      0t0 30403964 pipe
.flush  647 root    5u  IPv4 30678977      0t0      UDP *:45939
.flush  647 root    7u  IPv4 30403967      0t0      UDP *:40772

```

I delete /tmp/.flush i reboot and that file appears again

---

### Post by Habitual on 2014-05-28
```
less /tmp/.flush
```
and if that looks funny, use
```
strings /tmp/.flush
```
and show us the output.

---

### Post by kurogane2 on 2014-05-28
What interesting thing I found.


```
strings /tmp/.flush
```


[https://www.dropbox.com/s/9j97kyq1z2tzeec/flush.txt](https://www.dropbox.com/s/9j97kyq1z2tzeec/flush.txt)


The most important of that file is


```

/etc/init.d/bluetoothdaemon
#!/bin/sh
/usr/bin/btdaemon
/etc/rc1.d/S90bluetooth
/etc/rc2.d/S90bluetooth
/etc/rc3.d/S90bluetooth
/etc/rc4.d/S90bluetooth
/etc/rc5.d/S90bluetooth
/etc/rc6.d/S90bluetooth
/tmp/.flush
/var/log/.flush

```


I just remove those files and i not have issue but i'm not sure if i miss files to remove also not sure how they access my server

---

### Post by Habitual on 2014-05-28
/tmp/.flush  is suspect and leads me to wonder if you have a forward-facing website hosted on this same box?
Inspect your /tmp directory.

Also, this as root:
```
sudo stat -c%x /var/log/.flush /usr/.flush /tmp/.flush /tmp/helloworld
``` and report the output?

Highly suspicious.

I'd install rkhunter from repo and run it using
 ```

sudo rkhunter --update && rkhunter -c -sk
```
and have a look at /var/log/rkhunter.log
for "Warning" messages in that log file using
```
less /var/log/rkhunter.log
``` after it runs.

On the other hand, the output at that link *could be* innocuous, but the http: links in the strings suggest it's not.

You could also nuke them to orbit with 
```
sudo rm /var/log/.flush /usr/.flush /tmp/.flush 
```

Other more knowledgeable folks here may have more to add.

---

### Post by andor3 on 2014-05-29
I've found that file too on a clients server, and it's very, very suspicious.

I've found it because my ntpd binaries where disapearing every once in a while. I monitored them with auditctl and found this:
```

type=SYSCALL msg=audit(29/05/14 12:02:31.120:68) : arch=i386 syscall=unlink success=yes exit=0 a0=0xff3f7fc0 a1=0x9 a2=0x80be5e0 a3=0xff3ffbe0 items=2 ppid=7508 pid=7509 auid=unset uid=root gid=root euid=root suid=root fsuid=root egid=root sgid=root fsgid=root ses=unset tty=(none) comm=.flush exe=/tmp/.flush key=ntpd
```

WHAT! syscall=unlink by executable .flush ? Who are you?

Let's check proccesses:

```
~$ ps aux|grep flush
root       198  0.0  0.0      0     0 ?        S<   12:31   0:00 [kdmflush]
root       201  0.0  0.0      0     0 ?        S<   12:31   0:00 [kdmflush]
root      1565  0.0  0.0   7168   136 ?        Ss   12:32   0:00 [flush-242:0]
root      1566  0.0  0.0   7168   136 ?        S    12:32   0:00 [flush-242:0]
root      1567  0.0  0.0   7168   136 ?        S    12:32   0:00 [flush-242:0]
root      1568  0.0  0.0   7168   136 ?        S    12:32   0:00 [flush-242:0]
root      1569  0.0  0.0   7168   136 ?        S    12:32   0:00 [flush-242:0]
```

```
~$ ps -e -T|grep flush
  198   198 ?        00:00:00 kdmflush
  201   201 ?        00:00:00 kdmflush
 1565  1565 ?        00:00:00 .flush
 1566  1566 ?        00:00:00 .flush
 1567  1567 ?        00:00:00 .flush
 1568  1568 ?        00:00:00 .flush
 1569  1569 ?        00:00:00 .flush
```

I uploaded it to VirusTotal and, right now, it shows nothing suspicious:

[https://www.virustotal.com/en/file/15d9ec2edc86b54a7497c89b44a7125fb079d9871a51a5363b345afbc73d697d/analysis/1401379742/](https://www.virustotal.com/en/file/15d9ec2edc86b54a7497c89b44a7125fb079d9871a51a5363b345afbc73d697d/analysis/1401379742/)

File type is funny, because it's static, which might be usual on rootkits, to be able to run everywhere, and also, it's 32bit (80386, not even pentium optimized), while my clients machine is 64.

```
~$ file /tmp/.flush
/tmp/.flush: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.2.5, not stripped
```

Lets compare it to one regular system binary:

```
~$ file /bin/ls
/bin/ls: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=64d095bc6589dd4bfbf1c6d62ae985385965461b, stripped

```

I've deleted it and it **appears again on reboot**. Although I was auditing the file to find who created it, it appears that it's created before auditctl process started, so it doesn't appear.

```

$ sudo stat -c%x /tmp/.flush 
2014-05-29 13:53:47.723794621 -0400
$ sudo stat -c%y /tmp/.flush 
2014-05-29 13:50:17.388910913 -0400
$ sudo stat -c%w /tmp/.flush 
-

```
13:50 was, approx, my reboot time.

I'm asking the client for an immediate shutdown and deleteion of the machine, as it was fairly clean and not in production, but I'm asking also for a virtual image I can analize...
Do you have any other ideas to check this machine?

---

### Post by andor3 on 2014-05-29
And mine also has weird urls inside...
```
$ strings /tmp/.flush |grep http
http://103.20.195.254
http://115.23.172.31
http://61.33.28.194/
http://kill.et2046.com
http://sb.et2046.com
http://
```

And some other ips appart from that:
```

$ strings /tmp/.flush |awk '{match($0,/[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/); ip = substr($0,RSTART,RLENGTH); print ip}'|grep -v '^$'
61.33.28.194
115.23.172.47
103.20.195.254
103.20.195.254
115.23.172.31
61.33.28.194
```

---

### Post by unspawn on 2014-05-29
> **Habitual said:**
> I'd install rkhunter from repo Actually due to [http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/rkhunter?revision=1.508&view=markup](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/rkhunter?revision=1.508&view=markup) and [http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/signatures/RKH_iptablex.ldb?revision=1.1&view=markup](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/signatures/RKH_iptablex.ldb?revision=1.1&view=markup) (which this is about) you'd have to get it from CVS ([http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/?view=tar](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/?view=tar)) until we release again.    > **kurogane2 said:**
> # lsof -p 647 Thanks for the 'lsof' output, I completely overlooked the "flush" process!   That said, in your SysV start up directory you should find references to "IptabLex" and "IptabLes" and you should be able to find the following files:  ```
/IptabLes /.IptabLex /boot/.IptabLex /boot/.IptabLes /boot/IptabLes /tmp/IptabLes /etc/rc.d/init.d/IptabLex  /etc/rc.d/init.d/IptabLes /etc/rc.d/rc0.d/S55IptabLex /etc/rc.d/rc1.d/S55IptabLex /etc/rc.d/rc2.d/S55IptabLex  /etc/rc.d/rc3.d/S55IptabLex /etc/rc.d/rc4.d/S55IptabLex /etc/rc.d/rc5.d/S55IptabLex /etc/rc.d/rc6.d/S55IptabLex  /var/lib/update-rc.d/IptabLex /delallmykkk /usr/.IptabLes /usr/IptabLes
```   *Note these files were dropped there by somebody with root privileges so please don't ask how to "fix" this but isolate the machine, investigate and replace it with a known clean and properly managed (access restrictions, updates, auditing and hardening) one.  //EDIT: actually that was a bit daft. The 'strings' clearly show different files (same problem BTW): ```
/getsetup.rar /kill.txt /run.txt /tmp/helloworld /etc/init.d/bluetoothdaemon /usr/bin/btdaemon /etc/rc1.d/S90bluetooth /etc/rc2.d/S90bluetooth /etc/rc3.d/S90bluetooth /etc/rc4.d/S90bluetooth /etc/rc5.d/S90bluetooth /etc/rc6.d/S90bluetooth /tmp/.flush /var/log/.flush /usr/.flush .flush
```

---

### Post by bashiergui on 2014-05-29
```
$ strings /tmp/.flush |grep http
http://103.20.195.254
http://115.23.172.31
http://61.33.28.194/
http://kill.et2046.com
http://sb.et2046.com
``` If you look up all those IPs they come back to Seoul, Korea and Hong Kong.


Your strings output is interesting. TencentTraveler is in the user agent string, which is a Chinese browser. Can't think of a legitimate reason to run an executable out of the /tmp  directory. It also looks like it starts the bitTorrent daemon (btdaemon) which is suspicious. Not sure what it's doing with the bluetooth stuff, that would be interesting to look into.


I personally would conclude you have been compromised at this point. I would pull the machine off the wire. If you can keep it running without being connected to the internet then you can do some digging.


Check if you have anything in /var/logs. If you do look for users created and authenticating. Grep the firewall logs for the IP addresses from the strings output. Get a time stamp for those events and then check the logs for other odd stuff happening at those times. 


If the logs are gone that's a pretty solid indicator of compromise. If you've got a router in front of the machine then look through its logs for connections to the IPs from your strings output.


You could list the recent users and their bash histories, see what they've been up to. The attackers could have cleared the histories, which is another good indicator of compromise.


If you can't be down for analysis then reinstall and restore files from backup. Look at the stickies in this forum for some advice on securing the services after reinstallation so you're not compromised again.

---

### Post by unspawn on 2014-05-30
> **bashiergui said:**
> If you can't be down for analysis then reinstall and restore files from backup. Unless it was investigated and the infection vector known FCOL don't. They'll be exposing the same loophole again.

---

### Post by bashiergui on 2014-05-30
> **unspawn said:**
> Unless it was investigated and the infection vector known FCOL don't. They'll be exposing the same loophole again.Hopefully the OP comes back to tell us if there are any logs to investigate.

---

### Post by bob54 on 2014-06-17
Hello,
Glad to find this. I thought I was the only one with the problem and a /tmp/.flush file

Not sure that I can add anything helpful, but I have the same /tmp/.flush file on my Centos 6.5 machine. It is also erasing my ntpd file as well as my /usr/sbin/httpd file. The machine has only been operational a few weeks. It was accessible to the net via an IP pinhole.

Odd, this is a server that I'm setting up to replace the main server, and the main server shows no sign of a problem.

It's started at boot by
/etc/init.d/bluetoothdeamon

which in turn calls 
/usr/bin/btdeamon

In addition to having files erased, it may be doing something to the network, as we experience horrible slow downs when that machine is allowed on the network.

I've removed the startup deamons and I'm going to restart the machice and see it /tmp/.flush stays away.

HTH.
Bob

---

### Post by unspawn on 2014-06-18
> **bob54 said:**
> Not sure that I can add anything helpful, but See the "flush" process to check in the OP's post and the list of files to check for in my earlier post.    > **bob54 said:**
> I've removed the startup deamons and I'm going to restart the machice and see it /tmp/.flush stays away. If you find those files and processes then they're run by root.  Which means a root compromise. I suggest you act accordingly.

---

### Post by bob54 on 2014-06-18
Thought I'd posted some of this yesterday, but don't find it today.

I've had the same problem on Centos 6.5. A program /tmp/.flush would delete /usr/sbin/httpd and /usr/sbin/ntpd [maybe others].

After I managed to get wireshark installed, I found there were also two programs in /boot/.IptabLes and /boot/.IptabLex that were flooding my network with packets headed to what appeared to be IP located in China.

These programs were started as services via files in /etc/init.d

This happened on a newly installed server that DID have an ip pinhole open. Whoever got in had root access.  [Oddly enough the main server seems unaffected]

Seems more prank-like than malacious: deleting files like httpd and ntpd is bound to get somebody's attention. But the prank extracted its cost in time and $$.

Here's a list of files implicated:
 /boot/.IptabLes            
 /etc/init.d/ptabLes   
 /usr/bin/btdaemon
 /boot/.IptabLex            
 /etc/init.d/IptabLex
 /etc/init.d/bluetoothdaemon   
 /tmp/.flush

HTH.
Bob

---

### Post by unspawn on 2014-06-18
> **bob54 said:**
> Whoever got in had root access. That's what I said already, please act accordingly.   > **bob54 said:**
> Seems more prank-like than malacious: deleting files like httpd and ntpd is bound to get somebody's attention.  There's three servers discovered with this software in this thread alone. And there's many more servers on the 'net poorly maintained or left completely unattended.   *BTW thanks but I already posted the file list in [http://ubuntuforums.org/showthread.php?t=2226673&p=13036778#post13036778](http://ubuntuforums.org/showthread.php?t=2226673&p=13036778#post13036778).

---

### Post by Patricia_Konarski_ on 2014-06-23
Bob54 is surely on to something.  I would seriously review those--I'm going to check that against my own server.


Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

### Post by realmkeeper on 2014-08-02
Came here on a search from google. 

Though as much that .flush was part of this IptabLes/x mess. Been trying to swat the thing for 2 days on a samba file-server in the office. Everytime I clean the server it comes back a couple of hours later. I even found a guy in china complaining about the IptabLes/x mess. Another thing is that I found samba, cron, and my firewall and apache were broken and they fail to start at boot, this after running with a 200 day uptime :-(

[http://www.ebel-computing.de/JSPWiki/Wiki.jsp?page=VServer%20Trojan](http://www.ebel-computing.de/JSPWiki/Wiki.jsp?page=VServer%20Trojan)

Following [malwearmustdie ]("http://blog.malwaremustdie.org/2014/06/mmd-0025-2014-itw-infection-of-elf.html")it's a DDOS and as such is a heap of trouble if you don't squash it. My ISP runs automated DDOS/spam software and I got throttled to death before I caught the problem. 

I am going to run sysdig over night and see how they get in or what else has been infected.

---

### Post by unspawn on 2014-08-03
> **realmkeeper said:**
> (..) Another thing is that I found samba, cron, and my firewall and apache were broken and they fail to start at boot,  This may or may not be related but since you didn't post any verification results and error output there is not much one can say about this...            > **realmkeeper said:**
> (..) Been trying to swat the thing for 2 days on a samba file-server in the office.  As I said in my previous post ([http://ubuntuforums.org/showthread.php?t=2226673&p=13036778#post13036778](http://ubuntuforums.org/showthread.php?t=2226673&p=13036778#post13036778)) this is a root compromise so now is the time to act immediately and decisively. Isolate the machine so it can't be used by others but can be investigated, warn all users, mark credentials and backups as tainted, check adjacent machines, prepare and harden a new machine and only migrate data that is verified clean. If unsure: ask but do act according to the gravity of the situation.

---

