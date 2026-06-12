---
title: "IMAP doesn't exist?!?!"
date: 2010-06-30
forum: Server Platforms
---

### Post by handy-man on 2010-06-30
Hi,
I'm having an issue trying to install osticket [osticket.com]
 
The install went well, but I'm trying to get emails into the system but I've had two issues, firstly as I'm using a GUI (Matrix) I'm not allowed to forward emails to a pipe script, so I was just going to pop them into osticket...
 
When I tried to pop them, I got the error 'IMAP doesn't exist'
 
I had a look on some forums and found some saying that I just needed to un comment the IMAP line in php.ini in /etc/php5/apache2/
BUT I can't find it in there at all...
 
Can anyone help me with if and where I can just insert something about imap that will make this work???
 
 
Thanks in advance
 
 
Handy
 
I'm Using:
Ubuntu/6.06
Apache/2.0.55 (Ubuntu) 
PHP/5.1.2 
mod_ssl/2.0.55 
OpenSSL/0.9.8a 
MySQL/5.0.22

---

### Post by iponeverything on 2010-06-30
do you have imap installed?

```
dpkg -l |grep imap
```

---

### Post by handy-man on 2010-06-30
Hi 
 
I think so :|
 
When I did the grep I got these:
 
ii courier-imap
Courier Mail Server - IMAP server
 
as well as 
 
3.0.8-13ubuntu5.1

---

### Post by iponeverything on 2010-06-30
the next thing to look at is if it running.

```
ps uaxwww|grep imap


```
if it is, is it listening on port 143

```
telnet localost 143

```
if it is, are you filtering ports?

```
iptables -L -n 

```

---

### Post by handy-man on 2010-06-30
Looked like this...
 
> **iponeverything said:**
> 
the next thing to look at is if it running.
```
ps uaxwww|grep imap
```
```
root      3949  0.0  0.0   1832   488 ?        S    Apr03   0:00 /usr/sbin/couri                                       ertcpd -address=0 -stderrlogger=/usr/sbin/courierlogger -maxprocs=40 -maxperip=2                                       0 -pid=/var/run/courier/imapd.pid -nodnslookup -noidentlookup 143 /usr/lib/couri                                       er/courier/imaplogin /usr/lib/courier/authlib/authdaemon /usr/bin/imapd Maildir
root      3953  0.0  0.0   1608   312 ?        S    Apr03   0:00 /usr/sbin/couri                                       erlogger imaplogin
root      8361  0.0  0.1   2884   824 pts/1    S+   14:08   0:00 grep imap
```
 
 
if it is, is it listening on port 143
```
telnet localost 143
```
```

```
 
if it is, are you filtering ports?
```
iptables -L -n
```
```

iptables NO Error in IMAP command received by server.
Connection closed by foreign host.
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:69 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:69 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:110 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:143 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:123 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:3306 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:5555 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8002 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:9001 state NEW
DROP       all  --  0.0.0.0/0            0.0.0.0/0
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED

```


---

### Post by iponeverything on 2010-06-30
Well imap exist, it is listening and the port is not being filtered. 

You need to explore other avenues other than imap as being the cause.


Maybe install a pop3 server?

---

### Post by handy-man on 2010-06-30
Hmmmm... Indeed
 
Is it possible to 'hard code' behind the GUI to forward an email account to a 'pipe.php' script? i.e. sends emails for a email management script grab them from.
 
Also where to do this so that it doesn't interfere with the GUI and the GUI doesn't interfere with it??
 
Handy

---

### Post by kevin11951 on 2010-06-30
Ok, Lets look at this from a different angle... Are you connecting to a remote imap server, and osticket is giving you that error?  If you are running Debian/Ubuntu Try this either way:
```
apt-get install php5-imap
```

Do that on the web server running osticket...

Then:
```
apache2ctl restart
```

Now try connecting again, and see what happens.

---

### Post by handy-man on 2010-07-01
Kevin,
 
You are a star!!!
 
 
Handy:popcorn:

---

