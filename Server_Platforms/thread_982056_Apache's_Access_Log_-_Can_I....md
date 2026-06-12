---
title: "Apache's Access Log - Can I...?"
date: 2008-11-14
forum: Server Platforms
---

### Post by d-man97 on 2008-11-14
I am running an Apache2 server and mainly use it for personal use. It is open to the public; however, my use takes up about 90% of the logs.

Is there anyway I can remove all lines from my IP (basically static as long as I pay the bill) from the access.log?

Also, can I limit the logs by size, instead of days? Right now it holds 7 days in the main log, then 7 days in a second log, then more get compressed. If I can get my IP removed from the logs, then I will only need monthly backups to keep them readable.

Can anyone help?

Maybe setup a cron job to cat & grep out what I want to save, even on the active log? (I don't want it to only parse the old logs.) BTW, I have no idea how to setup a cron job.

Well, now I'm rambling. Any ideas?

---

### Post by hictio on 2008-11-14
What are you using to analize/ visualize your Apache logs?
There is [Webalizer](http://www.webalizer.com/), which can be easily setupt to exclude certain patterns so it won't taint your stats.

---

### Post by CrucifiedEgo on 2008-11-14
I know apache supports piping logs to a command -- perhaps you can write a shell script that grep -v's your ip, and writes to a file?  I use chronolog to write my logfiles to different days.  here's how the log setup works for my vhosts:

```
# old standard logger
# CustomLog /var/www/domain.com/log/access_ssl.log combined
# cronolog: /var/www/domain.com/log/2008-08-12_ssl.log
  CustomLog "|/usr/sbin/cronolog /var/www/domain.com/log/%Y-%m-%d_ssl.log" combined
```
I dont' see why CustomLog "|/home/user/bin/apache_log.sh domain.com" combined wouldn't work.  Start with just a script that writes the input to a file and work up from there.

---

### Post by d-man97 on 2008-11-14
Great ideas, thank you.

I currently just use the System Log viewer to visually scan for IPs that are not mine, then interpret the lines myself. I was not aware it supported piping. Nor did I remember that there are third-party log programs.

I will check out some log programs, but I think a custom script would be best for me. I will try to post it up here when I am complete.

---

### Post by d-man97 on 2008-11-17
Here's what I have so far.
```
     1	#! /bin/sh
     2	#
     3	# /var/log/apache2/a2logpipe.sh
     4	# Written by Derek White <d-man97@yahoo.com>.
     5	
     6	HEADER="[a2logpipe]:"
     7	
     8	if [ $# = 0 ]
     9	then
    10		logger "$HEADER Nothing to process."
    11		exit 1
    12	fi
    13	
    14	LOGENTRY=$*
    15	LOCALLOG="/var/log/apache2/localaccess.log"
    16	REMOTELOG="/var/log/apache2/remoteaccess.log"
    17	IP1=127.0.0.1
    18	IP2=76.18.231.30
    19	
    20	echo $LOGENTRY | grep --silent $IP1
    21	IP1RESULT=$?
    22	echo $LOGENTRY | grep --silent $IP2
    23	IP2RESULT=$?
    24	
    25	if [ $IP1RESULT != 0 -a $IP2RESULT != 0 ]
    26	then #log entry doesn't includes local ip's, so send it to the remote log
    27		if [ ! -w $REMOTELOG ] #we can't write to file
    28		then
    29			logger "$HEADER Cannot write to file: $REMOTELOG"
    30		else #we can write to file
    31			$LOGENTRY >> $REMOTELOG
    32		fi
    33	else #log entry does include local ip's, so send it to the local log
    34		if [ ! -w $LOCALLOG ] #we can't write to file
    35		then
    36			logger "$HEADER Cannot write to file: $LOCALLOG"
    37		else #we can write to file
    38			$LOGENTRY >> $LOCALLOG
    39		fi
    40	fi
```

Can I get some peer review for security and/or other concerns? (i.e. if someone passes a bad URL to apache, etc.)

---

### Post by hictio on 2008-11-17
Check the IP addresses variables, they are declared without quotes.
```

    17	IP1=127.0.0.1
    18	IP2=76.18.231.30

```

---

### Post by d-man97 on 2008-11-17
Everytime I run the script as root, I get this:
```
./a2logpipe.sh: 40: <argument 1>: not found
```
Where <argument 1> is whatever I send to it as a test.

When I run it (as a regular user) with "sh ./a2logpipe.sh <arguments>" it works perfectly. Its permissions are 640, so i have to use sh.

When run as root, I get an error no matter if I use sh or not.

What is going on?
Why can't root run it properly?

---

### Post by d-man97 on 2008-11-17
Added double quotes around the IP's, and I still get this from sudo su:
```
# ./a2logpipe.sh Test 127.0.0.1 Test Test
./a2logpipe.sh: 40: Test: not found
```

Why is line 40, "fi", trying to run a command? This is very perplexing.

---

### Post by hictio on 2008-11-17
> 
When I run it (as a regular user) with "sh ./a2logpipe.sh <arguments>" it works perfectly. Its permissions are 640, so i have to use sh.

When run as root, I get an error no matter if I use sh or not.

What is going on?
Why can't root run it properly?


What happens if, instead of as root, you execute it via 'sudo' as your plain vanilla user?

---

### Post by d-man97 on 2008-11-17
```
$ sudo ./a2logpipe.sh Test 127.0.0.1 Test Test
./a2logpipe.sh: 40: Test: not found
$ sudo sh ./a2logpipe.sh Test 127.0.0.1 Test Test
./a2logpipe.sh: 40: Test: not found
```

Adding an exit, or exit 0 at the end doesn't help anything either.

Also, I decided to try it out live, and I get this in my error.log, over and over until I a2dissite or stop apache:
```
piped log program '/var/log/apache2/a2logpipe.sh' failed unexpectedly
```
And this in syslog, over and over:
```
Nov 17 22:36:13 dereksbox logger: [a2logpipe]: Nothing to process.
```

Apparently, nothing is being sent to my script, and it exits. Even if I make it 'exit 0', instead of 'exit 1', apache still doesn't like it. Even if I comment it out completely, it still doesn't help. Does it have to be accessible by www-data, or is the directories default user: root & group: adm fine?

Here is my log info from my virtual host file:
```
LogLevel info
ErrorLog /var/log/apache2/error.log
#CustomLog /var/log/apache2/access.log combined
CustomLog "|/var/log/apache2/a2logpipe.sh" combined
```

---

