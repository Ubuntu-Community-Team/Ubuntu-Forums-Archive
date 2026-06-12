---
title: "User www-data runs ./stealth on external IP port 53"
date: 2009-02-20
forum: Security
---

### Post by jmkemp on 2009-02-20
My ubuntu box (8.10, server + desktop because it runs apache2 and postfix with mailman) is showing some odd behaviour. 

Every day or so I realise that it isn't listening out for new web server of mail server connections because there are three instances of a process called stealth with the executable path ./stealth [followed by an external IP address - this varies e.g. 212.117.164.98:53]. One of the processes is usually in zombie mode and the wired network card is going like the clappers uploading data. 

Naturally I kill the process, using command line because if you try in the system monitor it just closes the system monitor. Wireshark tells me next to nothing I didn't already know (I'm sending loads of packets to the aforementioned IP address). 

The external firewall (a Netgear DG834GT) is set to reject all protocols from outside except http (on 80) and SMTP (on 25). I configured ufw to do the same as well. 

Using rkhunter suggests that there is nothing it knows about installed on the machine. I've made sure all the packages are the latest version (which I do as a matter of course). I've done all the suggested things on both the apache and postfix websites for increasing security and still this damn thing comes back.

Any ideas:
a) what it is?
b) how to stop it?

---

### Post by cdenley on 2009-02-20
Did you install the package "stealth"? Have you located the file which is running?
```

locate stealth

```

The next time you notice it running, you can get the pid with
```

sudo lsof -n -i

```
then find out more about the process, like the full command.
```

sudo ps -f -p [pid]

```

Were you saying that your web and mail servers weren't listening for connections while the "stealth" script was running?
```

sudo netstat -tlnp

```

---

### Post by jmkemp on 2009-02-20
locate stealth just gives me a command prompt back, even with sudo. 

I'll try the next lot the next time I notice it though. Have stopped apache to see if that makes a difference. When I did it left behind httpd as well as three 'stealth' processes.

---

### Post by jmkemp on 2009-02-22
OK, it did it again earlier today. Here's an extract from my terminal session:

james@sternhammer:~$ sudo ps -fc 17410 
UID        PID  PPID CLS PRI STIME TTY      STAT   TIME CMD 
www-data 17410     1 TS   19 10:28 ?        R    178:36 ./stealth 69.43.42.42 53 
james@sternhammer:~$ sudo ps -fc 17411 
UID        PID  PPID CLS PRI STIME TTY      STAT   TIME CMD 
www-data 17411 17410 TS   19 10:28 ?        T      0:00 ./stealth 69.43.42.42 53 
james@sternhammer:~$ sudo ps -fc 17412 
UID        PID  PPID CLS PRI STIME TTY      STAT   TIME CMD 
www-data 17412 17411 TS   19 10:28 ?        Z      0:00 [stealth] <defunct> 
james@sternhammer:~$ sudo ps -fc 15133 
UID        PID  PPID CLS PRI STIME TTY      STAT   TIME CMD 
www-data 15133     1 TS   19 10:04 ?        Ss     0:01 httpd 
james@sternhammer:~$ sudo locate "./stealth 69.43.42.42 53" 
james@sternhammer:~$ sudo locate stealth 
james@sternhammer:~$ sudo kill 17410 
james@sternhammer:~$ sudo kill 17411 
kill: No such process 
james@sternhammer:~$ sudo kill 17412 
kill: No such process 
james@sternhammer:~$ sudo kill 15133 
james@sternhammer:~$

I also did a wireshark on it and it informed me that the packets were malformed DNS requests, but that might just be because it expected DNS on port 53 and it wasn't DNS. 

Still in the dark on this.

---

### Post by brian_p on 2009-02-22
> **jmkemp said:**
> 

Still in the dark on this.

This may offer a glimmer of light. It is not intended to be alarmist but it could suggest other avenues for exploration.

[http://www.webhostingtalk.com/showthread.php?p=5489671](http://www.webhostingtalk.com/showthread.php?p=5489671)

---

### Post by jmkemp on 2009-02-22
That is interesting. I also run roundcube and a PHP based wiki (dokuwiki). Will make a point of getting both of those updated to the latest version (the update manager isn't offering me updates for roundcube and dokuwiki is a manual install, but I know that there is a newer release candidate out now). Even if it isn't either of those packages it can't do any harm to put newer versions in place. 

Thanks for the pointer.

---

### Post by jmkemp on 2009-02-28
OK. I upgraded dokuwiki to the latest stable release (dated 14th Feb 09) and since then I've had no further instances of this behaviour. Not saying it won't ever happen again, but it looks like there was some sort of exploit somewhere in the package that was being used. 

All I need to remember for the future is keeping the web apps updated as well as the various ubuntu packages.

---

### Post by bodhi.zazen on 2009-02-28
You can run automatic updates with a cron job :

[http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/)

You can do this via synaptic as well if you have X installed.

---

### Post by mrkennie on 2009-12-10
I found the same process running on my machine today. I thought I was careful but it was actually uploaded using a zencart exploit. I had stupidly left and forgotten about a copy of zen (unpatched) in www root. I feel very bad because it must have been there for a couple of months going by the access logs. It seems it was used as part of a phishing attempt through the same exploit as well. Basically, I only noticed because router's LED's were going mad. The culprits in my case were found in images/.web with a bunch of other files which looked like IRC scripts etc.

Needless to say, I've taken the machine off-line and will be reinstalling tomorrow just to be sure. Fortunately it's a development machine but I should have been more careful, we all should!

I guess the lesson here is be very careful what you install on your server (or leave behind in my case). I was very stupid indeed.

---

