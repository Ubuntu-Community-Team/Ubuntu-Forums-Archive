---
title: "Troubleshooting snort ids"
date: 2012-12-02
forum: Security
---

### Post by termvrl on 2012-12-02
hi all,

i have install snort ids on ubuntu 10.04, running on virtual box.
i follow this this guide [www.snort.org/assets/158/snortinstallguide293.pdf]("http://ubuntuforums.org/www.snort.org/assets/158/snortinstallguide293.pdf")
my problem is i have no data on my snortreport.

i have done a few troubleshooting:-
1) I able to get "Commencing packet processing" on my snort. i concluded that my snort is running well.
2)  I have done, tcpdump on my sniffing interface (eth1) and i managed  to  sniff all traffic on my LAN. There is no porblem with network   card/sniffing interface.

i think my problem is on barnyard, it cannot forward the log to database.
In  my snort.conf, i already put "output unified2: filename snort.u2,  limit  128". and i managed to get file snort.u2.xxxx in my  /var/log/snort. but  when i vi the file, its empty.
i dont know how to troubleshoot barnyard2.

Attach is my screenshot.
Need help. Thanks.

p/s: i have post this question in 'absolute beginner sect'... no response... sorry for repost..

---

### Post by OpSecShellshock on 2012-12-02
In your snort.conf file in the section toward the top where you define network variables (HOME_NET, etc.) does it say "ipvar" or "var"? If you are using IPv4 and not IPv6 you'll need to make sure it says "var" because otherwise it won't get parsed right. Only make changes after backing up the snort.conf, of course.

I noticed you didn't have a barnyard2.waldo file showing up in /var/log/snort, which means barnyard hasn't received any events to send to your database and as such has not yet had the need to "bookmark" its place in the snort logs. Is barnyard running? Is your database defined at the bottom of barnyard2.conf along with the username and password of the database? That may not be relevant if your snort logs are empty, but it's something to consider.

When listing the files in /var/log/snort it helps to use:

```
ls -lart
```

so that you can get full information, including file sizes, in reverse chronological order so that the most recently changed files are at the bottom. If any of the logs have a non-zero file size, run this:

```
/usr/local/bin/u2spewfoo /var/log/snort/[log file name]
```

which should show you a human-readable version of what it contains. If any rules matched then it will tell you which ones.

For information on warnings and errors, do one or both of these:

```
grep -i error /var/log/messages

grep -i warning /var/log/messages
```

and look for anything related to snort or barnyard.

---

### Post by termvrl on 2012-12-02
Hi OpSecShellshock,
i have edit my snort.conf, and change ipvar to var.
when i do 
ls -larti get this output.
```

/var/log/snort$ ls -lart
total 12
-rw-------  1 snort snort    0 Nov 15 23:49 snort.u2.1352994562
-rw-------  1 snort snort    0 Nov 15 23:52 snort.u2.1352994734
-rw-------  1 snort snort    0 Nov 27 07:05 snort.u2.1353971101
-rw-------  1 snort snort    0 Nov 27 19:08 snort.u2.1354014531
-rw-------  1 snort snort    0 Nov 27 20:05 snort.u2.1354017923
-rw-------  1 snort snort    0 Nov 27 20:08 snort.u2.1354018108
-rw-------  1 snort snort    0 Nov 27 20:44 snort.u2.1354020297
-rw-------  1 snort snort    0 Nov 27 20:57 snort.u2.1354021034
-rw-------  1 snort snort    0 Nov 27 21:20 snort.u2.1354022411
-rw-------  1 snort snort    0 Nov 27 23:09 snort.u2.1354028956
-rw-------  1 snort snort    0 Nov 27 23:28 snort.u2.1354030132
-rw-------  1 snort snort    0 Nov 28 18:50 snort.u2.1354099843
-rw-------  1 snort snort    0 Nov 28 19:23 snort.u2.1354101829
-rw-------  1 snort snort    0 Dec  1 14:01 snort.u2.1354341708
-rw-------  1 snort snort    0 Dec  1 14:05 snort.u2.1354341915
-rw-------  1 snort snort    0 Dec  1 15:02 snort.u2.1354345366
-rw-------  1 snort snort    0 Dec  1 16:01 snort.u2.1354348904
-rw-------  1 snort snort    0 Dec  1 16:28 snort.u2.1354350498
-rw-------  1 snort snort    0 Dec  1 16:50 snort.u2.1354351829
-rw-------  1 snort snort    0 Dec  1 23:32 snort.u2.1354375926
-rw-------  1 snort snort    0 Dec  2 14:55 snort.u2.1354431332
-rw-------  1 snort snort    0 Dec  2 20:24 snort.u2.1354451047
-rw-r--r--  1 root  root     0 Dec  2 21:47 alert
drwxr-xr-x 14 root  root  4096 Dec  2 22:24 ..
-rw-------  1 snort snort    0 Dec  2 22:24 snort.u2.1354458276
drwxr-xr-x  2 snort snort 4096 Dec  2 22:24 .
-rw-r--r--  1 snort snort 2056 Dec  2 22:26 barnyard2.waldo

```

when i do 
$ grep -i warning /var/log/messages
grep: /var/log/messages: No such file or directory

---

### Post by NadirPoint on 2012-12-02
Check this out:

[https://github.com/da667/Autosnort](https://github.com/da667/Autosnort)

---

### Post by OpSecShellshock on 2012-12-02
OK so the next couple things I'd make sure of:

Did you restart snort after changing the snort.conf file? Is the http_inspect preprocessor active? Are there rules in your /etc/snort/rules directory? Are those rules enabled in the snort.conf? Does /etc/sysconfig/snort have the interface variable set appropriately (should I think be eth1 in your case)? Does barnyard2.conf also have the interface set appropriately?

Keep in mind that barnyard won't send anything to the database if the snort.u2 files are all empty. It's entirely possible that snort just hasn't checked any traffic that has matched any rules, especially if the devices on your LAN haven't been creating much traffic to sniff in the first place. Try letting it run for a while and engage in a lot of network activity with some of your LAN devices, see if anything happens.

---

### Post by termvrl on 2012-12-02
hi all,
i try provide info based on your question.
Did you restart snort after changing the snort.conf file?
Yes

Is the  http_inspect preprocessor active?
yes.i think.because there no # infront the line.
preprocessor http_inspect: global iis_unicode_map unicode.map 1252 compress_depth 65535 decompress_depth 65535

Are there rules in your  /etc/snort/rules directory?
yes.it in my /usr/local/snort

Are those rules enabled in the snort.conf?
var RULE_PATH /usr/local/snort/rules
var SO_RULE_PATH /usr/local/snort/so_rules
var PREPROC_RULE_PATH /usr/local/snort/preproc_rules

var WHITE_LIST_PATH /usr/local/snort/rules
var BLACK_LIST_PATH /usr/local/snort/rules

Does /etc/sysconfig/snort have the interface variable set appropriately  (should I think be eth1 in your case)?
no sysconfig folder in my system.
did you mean, set the interface card to promisc mode?
i have set it to promisc mode.

Does barnyard2.conf also have the  interface set appropriately?
yes.
config hostname:  localhost
config interface:  eth1

i hope this info is sufficient for you. i will additional info if you need.
Thanks for assist me.

---

### Post by OpSecShellshock on 2012-12-02
Looks like things should be pretty much in order, but until some events start coming in due to signature matches it will be difficult to identify the problem. Engage in some network activity for a while and keep an eye on the snort.u2 files to see if anything shows up in them.

---

### Post by samiux on 2012-12-02
> **termvrl said:**
> hi all,

i have install snort ids on ubuntu 10.04, running on virtual box.
i follow this this guide [www.snort.org/assets/158/snortinstallguide293.pdf]("http://ubuntuforums.org/www.snort.org/assets/158/snortinstallguide293.pdf")
my problem is i have no data on my snortreport.

i have done a few troubleshooting:-
1) I able to get "Commencing packet processing" on my snort. i concluded that my snort is running well.
2)  I have done, tcpdump on my sniffing interface (eth1) and i managed  to  sniff all traffic on my LAN. There is no porblem with network   card/sniffing interface.

i think my problem is on barnyard, it cannot forward the log to database.
In  my snort.conf, i already put "output unified2: filename snort.u2,  limit  128". and i managed to get file snort.u2.xxxx in my  /var/log/snort. but  when i vi the file, its empty.
i dont know how to troubleshoot barnyard2.

Attach is my screenshot.
Need help. Thanks.

p/s: i have post this question in 'absolute beginner sect'... no response... sorry for repost..

Experts in this forum are just talking without hands-on experience, so sad.

If you still do not have any help in this thread, you can consider to contact me and I will give out hints.

Samiux

---

### Post by termvrl on 2012-12-03
i think that i notice, when i do a ps -ef command,
```

UID        PID   PPID  C STIME TTY    TIME         CMD
mysql     862     1  0 19:53 ?        00:00:02       /usr/sbin/mysqld
snort     1069     1  0 19:53 ?        00:00:05      /usr/local/snort/bin/snort -D -u
root      1076     1  3 19:53 ?        00:01:23      /usr/local/bin/barnyard2 -c /usr

```

the user for mysql, snort, and barnyard is different. is it normal??

---

### Post by termvrl on 2012-12-03
i google an found something on file permission in snort config folder.
i check my file on /usr/local/snort/etc folder.
using this command "ls -l /usr/local/snort/etc".

this the output:-
```
 
-rw-r--r-- 1 root root   11296 Dec  3 00:25 barnyard2.conf
-rw-r--r-- 1 1210 1210    3621 Oct 12 00:30 classification.config
-rw-r--r-- 1 1210 1210   29596 Oct 12 00:30 gen-msg.map
-rw-r--r-- 1 1210 1210    1112 Jan 20  2010 open-test.conf
-rw-r--r-- 1 1210 1210     746 Oct 12 00:30 reference.config
-rw-r--r-- 1 1210 1210 2694591 Oct 12 00:33 sid-msg.map
-rw-r--r-- 1 1210 1210   26176 Dec  3 00:44 snort.conf
-rw-r--r-- 1 1210 1210    2556 Oct 12 00:30 threshold.conf
-rw-r--r-- 1 1210 1210   53841 Oct 12 00:30 unicode.map
```

then, i changed all file permissions to snort user.
using this command 
sudo chown -R username:group directoryso, this is my new output for "ls -l /usr/local/snort/etc"
```
-rw-rw-rw- 1 snort snort   11296 Dec  3 00:25 barnyard2.conf
-rw-r--r-- 1 snort snort    3621 Oct 12 00:30 classification.config
-rw-r--r-- 1 snort snort   29596 Oct 12 00:30 gen-msg.map
-rw-r--r-- 1 snort snort    1112 Jan 20  2010 open-test.conf
-rw-r--r-- 1 snort snort     746 Oct 12 00:30 reference.config
-rw-r--r-- 1 snort snort 2694591 Oct 12 00:33 sid-msg.map
-rw-r--r-- 1 snort snort   26176 Dec  3 00:44 snort.conf
-rw-r--r-- 1 snort snort    2556 Oct 12 00:30 threshold.conf
-rw-r--r-- 1 snort snort   53841 Oct 12 00:30 unicode.map

```
i do nmap.
i check to the database, i receive the logs.
=D

Thanks everybody for assist me.
Now time to simulate the attacks and learn how to read the logs. 
:guitar:

---

### Post by Ms. Daisy on 2012-12-03
> **samiux said:**
> Experts in this forum are just talking without hands-on experience, so sad.

If you still do not have any help in this thread, you can consider to contact me and I will give out hints.

Samiux
WTH are you talking about? By suggesting that OpSecShellshock has no experience with snort, you have lost all credibility in my book.

---

### Post by lisati on 2012-12-03
> **samiux said:**
> Experts in this forum are just talking without hands-on experience, so sad.

If you still do not have any help in this thread, you can consider to contact me and I will give out hints.

Samiux

While there might be occasions where support via PM might be useful, the community usually achieves more benefit in publicly viewable threads.

---

### Post by benwi on 2013-04-26
Need HELP REALLY SOON!!

helo, i have the same problem with you, when I type ls -l /usr/local/snort/etc
it shows output like yours

-rw-r--r-- 1 root root   11296 Dec  3 00:25 barnyard2.conf -rw-r--r-- 1 1210 1210    3621 Oct 12 00:30 classification.config -rw-r--r-- 1 1210 1210   29596 Oct 12 00:30 gen-msg.map -rw-r--r-- 1 1210 1210    1112 Jan 20  2010 open-test.conf -rw-r--r-- 1 1210 1210     746 Oct 12 00:30 reference.config -rw-r--r-- 1 1210 1210 2694591 Oct 12 00:33 sid-msg.map -rw-r--r-- 1 1210 1210   26176 Dec  3 00:44 snort.conf -rw-r--r-- 1 1210 1210    2556 Oct 12 00:30 threshold.conf -rw-r--r-- 1 1210 1210   53841 Oct 12 00:30 unicode.map

but I really don't understand how to use command "sudo chown -R username:group directoryso"
when i type it, it said chown: invalid user: 'username:group'
can u help me please?? what do username and group reffer to?

---

