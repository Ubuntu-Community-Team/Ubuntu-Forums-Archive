---
title: "Change Postfix port and no more inbound mail?"
date: 2007-03-15
forum: Server Platforms
---

### Post by rth on 2007-03-15
I have tried in the past to set up a mail server on my 6.10 server and I've given up after not being able to resolve my issues. So, I saw a new tutorial on setting up Zimbra over on How To Forge ([http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)). Following the guide seems to have everything working just fine.

My problem is that my ISP blocks port 25, so while I can telnet in to 25 from my LAN, the outside is blocked of course. I change the port for Postfix to any other port and for some reason, I can't telnet to that new port from the inside or the outside. The standard response (ESMTP blah blah) is not returned.

The errors from the logs are:
```
master[7574]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smtpd: No such file or directory
postfix/master[10002]: warning process /opt/zimbra/postfix-2.2.9/libexec/smtpd pid 7574 exit status 1
postfix/master[10002]: warning process /opt/zimbra/postfix-2.2.9/libexec/smtpd: bad command startup -- throttling
...
```

As a workaround, I tried to have iptables FWD a different port (say 2525) to port 25, but that doesn't seem to work as I'm guessing when the connection comes in on 2525, iptables says go connect on port 25, which is blocked by my ISP, therefore back to square 1.
```
iptables -t nat -a PREROUTING -p tcp --destination-port 2525 -j REDIRECT --to-port 25
```
I have tried adding rules for INPUT ACCEPT on 2525 as well as FORWARD ACCEPT on 2525 in case the PREROUTING REDIRECT wasn't going to work on its own...

Anyway, anyone have any ideas?

---

### Post by Mr. C. on 2007-03-16
If your ISP blocks INBOUND 25, then the rest of the world in general will not be able to send email to you, at least not as an MX.

If your ISP allows the submission port (587), you can allow correctly configured clients to use your system to relay email.

Without 25, you are out of luck for the general case.  Find a new ISP if you need that.

If you had trouble with a basic mail server, Zimbra is quite a stretch.  Get postfix working in a simple configuration, and then upgrade as you feel comfortable.

MrC

---

### Post by MJN on 2007-03-16
Another option, albeit one likely to cost, is the use of one of the 'port redirection' services provided by dynamic DNS providers (amongst others). Here they will act as your primary mail server, accept mail, and then connect to your server on a non-standard port to deliver your mail. No-ip.com's 'Mail Reflector' is one such service that springs to mind at ~$40/yr.
 
However, as Mr C mentions, I'd suggest finding a different ISP. Sure, many of them might be blocking outgoing e-mail (not sent via their SMTP relay) which is one thing however blocking incoming is pushing it in my opinion and the best way to vote against this sort of practice is with your feet.
 
Mathew

---

### Post by rth on 2007-03-16
I have had Hula working in the past on port 2525 because I do use a mail reflector. The point here is that when switching Postfix from 25 to 2525, Postfix stops responding on the port.

---

### Post by MJN on 2007-03-16
Ah I see - sorry should've read your post properly (I blame Mr C - I was merely following his lead! ;))
 
In that case I'm not so sure.... someone with better firewall skills than I would be better placed to help (if that's where the problem lies).
 
Mathew
 
P.S. Just noticed your 'Me 0 - Postfix 1' topic tag! :lol:

---

### Post by rth on 2007-03-16
I've actually tried more than one way to get it to work. One was tell Postfix to listen on 2525 instead of 25 (or as well as 25, tried both). The other was tell iptables to NAT the traffic from 2525 to 25. Either way, Postfix is winning. ;)

I don't have a particular preference of one method over the other.

---

### Post by Mr. C. on 2007-03-16
Your point would have been clear if you asked "how do I change the postfix smtpd  listening port?"  In fact, you never asked such.

You can easily change the postfix listening port and it works fine.  The failure is your method.


```
root@mrc:/etc/postfix# telnet localhost 2525
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mrc.example.com ESMTP Postfix
EHLO example.com 
250-mrc.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-AUTH PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM:<test@example.com>                          
250 2.1.0 Ok
RCPT TO:<test@sample.net>
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
testing
.
250 2.0.0 Ok: queued as AEB6F1AB3AC
quit
221 2.0.0 Bye
Connection closed by foreign host.
root@mrc:/etc/postfix#
```

In postfix's master.cf, find the line:

```
smtp      inet  n       -       n       -       -       smtpd
```
and change it to:
```
2525      inet  n       -       n       -       -       smtpd
```
and postfix restart.

MrC

---

### Post by rth on 2007-03-16
I have changed the Postfix file to use port 2525 instead of smtp, this is where my problem is which is why I didn't ask how to change from one port to the other... Postfix has been restarted, I also rebooted the server for fun. Using your example, when it's on smtp (thus port 25) this works:
```
root@mrc:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mrc.example.com ESMTP Postfix
```
In particular the 220 part. When I change it to port 2525 (that is the only change being made):
```
root@mrc:/etc/postfix# telnet localhost 2525
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```
That's it. I can type to my heart's content, but nothing happens. I can't send an e-mail through telnet. A netstat shows that port 2525 is open and accepting connections. I can't say that I've actually tried to telnet from the server to itself, my testing has been from a computer on the same subnet. Like I said, going to 25 works, changing the Postfix config to 2525, restarting postfix, telnet to 2525 shows the above with no 220 status code and no response of any kind. A port scan from the outside puts the port to "stealth" rather than it being open or closed. Packets go in, but don't come back out...

---

### Post by Mr. C. on 2007-03-16
Work from the postfix server itself first.  Once you get that working, then go to external machines.  Try not to thrash with random tests (reboot, change this, change that).  Instead, try to understand what is going on.

First, accept the premise that it *does* work.  Next, find your mistake or misconfiguration.  We can't help you in that process if you interpret the results for us, instead of showing us the actual data.

From the host itself, lets see the output of :

```
lsof -n -i 
```

MrC

---

### Post by rth on 2007-03-16
Just to be clear, it **did** work on port 25, it **stopped** working after changing the letters "smtp" to the numbers "2525" in the Postfix config. That was the **only** change made. As per the instructions on the Zimbra site, I reloaded Postfix after changing the config file. Because the reload worked, but telnet to 2525 didn't work (see above for output of telnet to 2525), I restarted the server. The testing and config change was done from a different computer on the same LAN via SSH.

```
COMMAND    PID USER   FD   TYPE   DEVICE SIZE NODE NAME
vino-serv 4200  rth   16u  IPv4    11552       TCP *:5900 (LISTEN)
firefox-b 4614  rth   51u  IPv4 13319051       TCP ADSL.ip.address.here:50435->external.ip.address.here:www (ESTABLISHED)
```

From a netstat -ant
```
tcp        0      0 0.0.0.0:2525            0.0.0.0:*               LISTEN
tcp        1      0 192.168.2.8:2525        192.168.2.99:49065      CLOSE_WAIT
```
192.168.2.8 is the server, 192.168.2.99 is another machine on my LAN.

---

### Post by Mr. C. on 2007-03-16
Why is there no postfix listener shown in the output from the first command?

I see one CLOSE_WAIT session in netstat.

Time to start looking at your maillog and syslog's to see why postfix is failing to start.

MrC

---

### Post by rth on 2007-03-16
Errors from the logs are in my 1st post but here as well:
```
master[7574]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smtpd: No such file or directory
postfix/master[10002]: warning process /opt/zimbra/postfix-2.2.9/libexec/smtpd pid 7574 exit status 1
postfix/master[10002]: warning process /opt/zimbra/postfix-2.2.9/libexec/smtpd: bad command startup -- throttling
...
```
I can look for other errors and whatnot, but those seem to stand out.

---

### Post by MJN on 2007-03-16
rth: Use **sudo** lsof -n -i

Mathew

---

### Post by Mr. C. on 2007-03-16
The do standout, and this is the problem.

Where is your smtpd ?

Throttling indicates the daemon cannot start, so the master process stops trying so hard.

Find that binary.

MrC

---

### Post by rth on 2007-03-16
With the sudo command:
```
COMMAND     PID     USER   FD   TYPE  DEVICE SIZE NODE NAME
slapd      4643   zimbra    7u  IPv4   12720       TCP 192.168.2.8:ldap (LISTEN)
mysqld     4932   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4961   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4962   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4963   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4964   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4965   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4971   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     4971   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     4973   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4974   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4975   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     4976   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     5012   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5012   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5013   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5013   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5014   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5014   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5015   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5015   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5016   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5016   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5046   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5046   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5047   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5047   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5048   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5048   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5049   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5049   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     5054   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
java       5067   zimbra    5u  IPv6   13993       TCP *:webcache (LISTEN)
java       5067   zimbra    7u  IPv6   14042       TCP *:7071 (LISTEN)
java       5067   zimbra   16u  IPv6   14594       TCP *:pop3 (LISTEN)
java       5067   zimbra   17u  IPv6   14595       TCP *:pop3s (LISTEN)
java       5067   zimbra   18u  IPv6   14596       TCP *:imap2 (LISTEN)
java       5067   zimbra   19u  IPv6   14597       TCP *:imaps (LISTEN)
java       5067   zimbra   27u  IPv6   14630       TCP 127.0.0.1:58588->127.0.0.1:7306 (ESTABLISHED)
java       5067   zimbra   29u  IPv6   14640       TCP *:7035 (LISTEN)
java       5067   zimbra   32u  IPv6   14642       TCP *:7025 (LISTEN)
java       5067   zimbra   54u  IPv6   36176       TCP 127.0.0.1:55548->127.0.0.1:7306 (CLOSE_WAIT)
httpd      5153   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
httpd      5154   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
httpd      5155   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
httpd      5158   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
httpd      5159   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
httpd      5160   zimbra    3u  IPv6   13899       TCP *:7780 (LISTEN)
clamd      5176   zimbra    0u  IPv4   13968       TCP *:3310 (LISTEN)
mysqld     5226   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     5237   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5237   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
amavisd    5353   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5354   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5355   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5356   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5357   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5358   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5359   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5360   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5361   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5362   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
amavisd    5363   zimbra    5u  IPv4   14512       TCP 127.0.0.1:10024 (LISTEN)
mysqld     5809   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld     5820   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     5820   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
mysqld     7974   zimbra   14u  IPv4   13607       TCP 127.0.0.1:7306 (LISTEN)
mysqld     7974   zimbra   29u  IPv4   14631       TCP 127.0.0.1:7306->127.0.0.1:58588 (ESTABLISHED)
master    10002     root   11u  IPv4   57168       TCP *:2525 (LISTEN)
mysqld    11206   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
mysqld    11393   zimbra   14u  IPv4   13452       TCP 127.0.0.1:7307 (LISTEN)
```
Removed non-zimbra related stuff.

Doing a search for smtpd:
```
rth@www:~$ sudo find / -name smtpd
/opt/zimbra/postfix-2.2.9/libexec/smtpd
```
Which seems to be the correct path.

---

### Post by Mr. C. on 2007-03-16
Ok, this now shows your master process running, listening on port 2525.

So, you should now be able to telnet to that port, and the listener should connect.

If you get no answer, and the master process is still running, a firewall is likely blocking that connection.

MrC

---

### Post by rth on 2007-03-16
```
rth@tux:~/Desktop$ telnet 192.168.2.8 2525
Trying 192.168.2.8...
Connected to 192.168.2.8.
```
No status reply which I got when it was listening on 25. There is no reply and like I mentioned, no matter what I type, there is no response from the server. I am telnetting on my LAN, iptables is configured to allow **all** non ppp0 connections:
```
iptables -A INPUT -m state --state NEW -i ! ppp0 -j ACCEPT
```
Like I mentioned, when on port 25, it works. Change the port to 2525, and I get the no reply from the server yet it seems to accept the connection.

---

### Post by Mr. C. on 2007-03-16
Enable higher debug levels:

```
Enable peer = 2
debug_peer_list = 127.0.0.1
```

and restart postfix.

Then, from the localhost, connect to postfix via telnet localhost 2525.

If you get no output in your log files, your packets are not reaching postfix, and this problem is not a postfix matter at all.

If you do get debug output in your maillog, then this indicates postifx is receiving the connection, but its return response is being blocked.

MrC

---

### Post by rth on 2007-03-16
These go into main.cf?

---

### Post by Mr. C. on 2007-03-16
Sorry, yes.

If you're not sure of settings, man 5 postconf gives then entire list.

MrC

---

### Post by rth on 2007-03-16
I get:
```
rth@www:~$ man 5 postconf
No manual entry for postconf in section 5
```
Replacing 5 with another number or removing it gives the same message. Anyway, I added it to the end of main.cf and it seems like I get a bit more logging, however nothing useful shows up.

I'm going to put it back to port 25 and see if I get the same messages about the missing file.

---

### Post by rth on 2007-03-16
Well, commenting out 2525 and uncommenting smtp from master.cf makes the file not found thing go away and it works again. Hmm... Postconf 2, me 0? :)

---

### Post by Mr. C. on 2007-03-16
You have a custom install.  You need to configure your MANPATH to find the postfix man pages somewhere in your Zimbra installation.

Without seeing the actual data, I can only keep guessing as to what is working or not.  I either need to see the raw data to come to my own conclusions, or I'm forced to accept your conclusions that everything is configured correctly... but postfix doesn't work.

I gave you a test to try, but you haven't made a decision as to whether postfix is sending any data based upon the connection.

Setup one terminal window like this:

```
tail -f /var/log/maillog    # or whatever the path to your maillog is.
```

and in another terminal window, connect to postfix.  If you see ANY output from postfix immediately after that telnet connection, postfix IS getting the connection, and if no output on your telnet terminal appears, postfix's messages are not reaching you because they are blocked.

MrC

---

### Post by rth on 2007-03-16
```
Mar 16 19:21:04 www master[26657]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smptd: No such file or directory
Mar 16 19:21:05 www postfix/master[10002]: warning: process /opt/zimbra/postfix-2.2.9/libexec/smptd pid 26657 exit status 1
Mar 16 19:21:05 www postfix/master[10002]: warning: /opt/zimbra/postfix-2.2.9/libexec/smptd: bad command startup -- throttling
Mar 16 19:21:19 www postfix/postfix-script: refreshing the Postfix mail system
Mar 16 19:21:19 www postfix/master[10002]: reload configuration /opt/zimbra/postfix-2.2.9/conf
Mar 16 19:22:03 www zmtomcatmgr[26941]: status requested
Mar 16 19:22:03 www zmtomcatmgr[26941]: status OK
Mar 16 19:24:04 www zmtomcatmgr[27183]: status requested
Mar 16 19:24:04 www zmtomcatmgr[27183]: status OK
Mar 16 19:26:04 www zmtomcatmgr[27425]: status requested
Mar 16 19:26:04 www zmtomcatmgr[27425]: status OK
Mar 16 19:28:04 www zmtomcatmgr[27667]: status requested
Mar 16 19:28:04 www zmtomcatmgr[27667]: status OK
Mar 16 19:30:04 www zmtomcatmgr[27933]: status requested
Mar 16 19:30:04 www zmtomcatmgr[27933]: status OK
Mar 16 19:32:04 www zmtomcatmgr[28201]: status requested
Mar 16 19:32:04 www zmtomcatmgr[28201]: status OK
Mar 16 19:34:03 www zmtomcatmgr[28444]: status requested
Mar 16 19:34:03 www zmtomcatmgr[28444]: status OK
Mar 16 19:36:04 www zmtomcatmgr[28687]: status requested
Mar 16 19:36:04 www zmtomcatmgr[28687]: status OK
Mar 16 19:38:04 www zmtomcatmgr[28929]: status requested
Mar 16 19:38:04 www zmtomcatmgr[28929]: status OK
Mar 16 19:41:19 www postfix/smtpd[29382]: connect from unknown[192.168.2.99]
Mar 16 19:41:29 www postfix/smtpd[29382]: disconnect from unknown[192.168.2.99]
```
You can see where the reload is.

From syslog:
```
Mar 16 19:21:04 www master[26657]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smptd: No such file or directory
Mar 16 19:21:05 www postfix/master[10002]: warning: process /opt/zimbra/postfix-2.2.9/libexec/smptd pid 26657 exit status 1
Mar 16 19:21:05 www postfix/master[10002]: warning: /opt/zimbra/postfix-2.2.9/libexec/smptd: bad command startup -- throttling
Mar 16 19:21:19 www postfix/postfix-script: refreshing the Postfix mail system
Mar 16 19:21:19 www postfix/master[10002]: reload configuration /opt/zimbra/postfix-2.2.9/conf
Mar 16 19:22:01 www /USR/SBIN/CRON[26845]: (zimbra) CMD (/opt/zimbra/libexec/zmstatuslog)
Mar 16 19:22:03 www zmtomcatmgr[26941]: status requested
Mar 16 19:22:03 www zmtomcatmgr[26941]: status OK
...
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: antispam: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: antivirus: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: ldap: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: logger: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: mailbox: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: mta: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: snmp: Running 
Mar 16 19:40:07 www zimbramon[29053]: 29053:info: 2007-03-16 19:40:01, STATUS: www: spell: Running 
Mar 16 19:41:19 www postfix/smtpd[29382]: connect from unknown[192.168.2.99]
Mar 16 19:41:29 www postfix/smtpd[29382]: disconnect from unknown[192.168.2.99]
Mar 16 19:42:01 www /USR/SBIN/CRON[29387]: (zimbra) CMD (/opt/zimbra/libexec/zmstatuslog)
Mar 16 19:42:04 www zmtomcatmgr[29483]: status requested
Mar 16 19:42:04 www zmtomcatmgr[29483]: status OK
```

I'm not sure what else you want to see.

---

### Post by Mr. C. on 2007-03-16
How about the master.cf file.  That is where a problem is.

This may also be of some use to you later:

[http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html)

MrC

---

### Post by Mr. C. on 2007-03-16
Yes, and I see that you connected from 192.168.2.99
> Mar 16 19:41:19 www postfix/smtpd[29382]: connect from unknown[192.168.2.99]
Mar 16 19:41:29 www postfix/smtpd[29382]: disconnect from unknown[192.168.2.99]

Is that the IP you used in the debug_peer_list ?

If this was your connection, postfix received your connection!

MrC

---

### Post by rth on 2007-03-16
I changed the port back to 25 away from 2525. I'll put it back to 2525 and repost the relevant logs.

---

### Post by rth on 2007-03-16
```
Mar 16 20:00:33 www postfix/postfix-script: refreshing the Postfix mail system
Mar 16 20:00:33 www postfix/master[10002]: reload configuration /opt/zimbra/postfix-2.2.9/conf
Mar 16 20:02:04 www zmtomcatmgr[32158]: status requested
Mar 16 20:02:04 www zmtomcatmgr[32158]: status OK
Mar 16 20:02:31 www master[32231]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smptd: No such file or directory
Mar 16 20:02:32 www postfix/master[10002]: warning: process /opt/zimbra/postfix-2.2.9/libexec/smptd pid 32231 exit status 1
Mar 16 20:02:32 www postfix/master[10002]: warning: /opt/zimbra/postfix-2.2.9/libexec/smptd: bad command startup -- throttling
Mar 16 20:03:32 www master[32289]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smptd: No such file or directory
Mar 16 20:03:33 www postfix/master[10002]: warning: process /opt/zimbra/postfix-2.2.9/libexec/smptd pid 32289 exit status 1
Mar 16 20:03:33 www postfix/master[10002]: warning: /opt/zimbra/postfix-2.2.9/libexec/smptd: bad command startup -- throttling
Mar 16 20:04:04 www zmtomcatmgr[32389]: status requested
Mar 16 20:04:04 www zmtomcatmgr[32389]: status OK
Mar 16 20:04:33 www master[32476]: fatal: master_spawn: exec /opt/zimbra/postfix-2.2.9/libexec/smptd: No such file or directory
Mar 16 20:04:34 www postfix/master[10002]: warning: process /opt/zimbra/postfix-2.2.9/libexec/smptd pid 32476 exit status 1
Mar 16 20:04:34 www postfix/master[10002]: warning: /opt/zimbra/postfix-2.2.9/libexec/smptd: bad command startup -- throttling
```
No connection message like before.

Going to check that link you posted.

Edit:
master.cf
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the Postfix master(5) manual page.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
#smtp      inet  n       -       n       -       -       smtpd
2525      inet  n       -       n       -       -       smptd
#submission inet n      -       n       -       -       smtpd
#	-o smtpd_etrn_restrictions=reject
#	-o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps    inet  n       -       n       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#submission   inet    n       -       n       -       -       smtpd
#  -o smtpd_etrn_restrictions=reject
#  -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
#628      inet  n       -       n       -       -       qmqpd
pickup    fifo  n       -       n       60      1       pickup
cleanup   unix  n       -       n       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       n       1000?   1       tlsmgr
rewrite   unix  -       -       n       -       -       trivial-rewrite
bounce    unix  -       -       n       -       0       bounce
defer     unix  -       -       n       -       0       bounce
trace     unix  -       -       n       -       0       bounce
verify    unix  -       -       n       -       1       verify
flush     unix  n       -       n       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       n       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       n       -       -       smtp
	-o fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       n       -       -       showq
error     unix  -       -       n       -       -       error
discard   unix  -       -       n       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
scache	  unix	-	-	n	-	1	scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
#
# The Cyrus deliver program has changed incompatibly, multiple times.
#
old-cyrus unix  -       n       n       -       -       pipe
  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
cyrus     unix  -       n       n       -       -       pipe
  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=foo argv=/usr/local/sbin/bsmtp -f $sender $nexthop $recipient
#
# AMAVISD-NEW
#
smtp-amavis unix -      -       n       -       10  smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
	-o disable_dns_lookups=yes
	-o max_use=20
127.0.0.1:10025 inet n  -       n       -       -  smtpd
	-o content_filter=
	-o local_recipient_maps=
	-o virtual_mailbox_maps=
	-o virtual_alias_maps=
	-o relay_recipient_maps=
	-o smtpd_restriction_classes=
	-o smtpd_delay_reject=no
	-o smtpd_client_restrictions=permit_mynetworks,reject
	-o smtpd_helo_restrictions=
	-o smtpd_sender_restrictions=
	-o smtpd_recipient_restrictions=permit_mynetworks,reject
	-o mynetworks_style=host
	-o mynetworks=127.0.0.0/8
	-o strict_rfc821_envelopes=yes
	-o smtpd_error_sleep_time=0
	-o smtpd_soft_error_limit=1001
	-o smtpd_hard_error_limit=1000
	-o smtpd_client_connection_count_limit=0
	-o smtpd_client_connection_rate_limit=0
	-o receive_override_options=no_header_body_checks,no_unknown_recipient_checks,no_address_mappings
```

---

### Post by rth on 2007-03-16
I added a third port and reopened 25 for Postfix. I try to telnet to each port, one at a time, the log shows one (1) connection, which is to port 25. The other two (2525 and now 8025) show no connection attempts.
```
Mar 16 20:37:48 www postfix/smtpd[5537]: connect from unknown[192.168.2.99]
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: unknown: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: 192.168.2.99: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: unknown: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: 192.168.2.99: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostname: unknown ~? 127.0.0.1
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostaddr: 192.168.2.99 ~? 127.0.0.1
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: unknown: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_list_match: 192.168.2.99: no match
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostname: unknown ~? 127.0.0.0/8
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostaddr: 192.168.2.99 ~? 127.0.0.0/8
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostname: unknown ~? 192.168.2.0/24
Mar 16 20:37:48 www postfix/smtpd[5537]: match_hostaddr: 192.168.2.99 ~? 192.168.2.0/24
Mar 16 20:37:48 www postfix/smtpd[5537]: > unknown[192.168.2.99]: 220 www ESMTP Postfix
Mar 16 20:37:50 www postfix/smtpd[5537]: < unknown[192.168.2.99]: quit
Mar 16 20:37:50 www postfix/smtpd[5537]: > unknown[192.168.2.99]: 221 Bye
Mar 16 20:37:50 www postfix/smtpd[5537]: match_hostname: unknown ~? 127.0.0.0/8
Mar 16 20:37:50 www postfix/smtpd[5537]: match_hostaddr: 192.168.2.99 ~? 127.0.0.0/8
Mar 16 20:37:50 www postfix/smtpd[5537]: match_hostname: unknown ~? 192.168.2.0/24
Mar 16 20:37:50 www postfix/smtpd[5537]: match_hostaddr: 192.168.2.99 ~? 192.168.2.0/24
Mar 16 20:37:50 www postfix/smtpd[5537]: disconnect from unknown[192.168.2.99]
Mar 16 20:37:50 www postfix/smtpd[5537]: master_notify: status 1
Mar 16 20:37:50 www postfix/smtpd[5537]: connection closed
```
I added the "-v" argument to the end of the the appropriate lines for 25, 2025, and 8025 in master.cf for verbose logging.

---

### Post by Mr. C. on 2007-03-16
What are the permissions of the file, and all subdirectories above?
```

/opt/zimbra/postfix-2.2.9/libexec/smptd
```
```

ls -l /opt/zimbra/postfix-2.2.9/libexec/smptd
ls -ld /opt/zimbra/postfix-2.2.9/libexec
ls -ld /opt/zimbra/postfix-2.2.9
ls -ld /opt/zimbra/postfix-2.2.9

```

Did you intend postfix be running as user "www" ?   Did you change mail_owner to www, and all postfix directories and postfix binaries?

MrC

---

### Post by rth on 2007-03-16
```
-rwxr-xr-x 1 root root 2195197 2007-02-09 15:34 smtpd

drwxr-xr-x 2 root root 4096 2007-03-09 20:00 /opt/zimbra/postfix-2.2.9/libexec
drwxr-xr-x 7 root root 4096 2007-03-09 20:00 /opt/zimbra/postfix-2.2.9/
drwxr-xr-x 39 root root 4096 2007-03-09 20:30 /opt/zimbra/
```
www is actually the name of the machine. Couldn't think of anything creative at the time I was installing it. I thought about permissions as well, but then I couldn't logically understand why using a different port would somehow make it stop working because of file/dir permissions.

---

### Post by Mr. C. on 2007-03-17
Your problem is trivial

2525      inet  n       -       n       -       -       smptd

This line in master.cf is bad.  There is no such binary smptd.

Your claim that all you changed was smtp to 2525 is not correct, or you started with a bad master.cf.

MrC

---

### Post by rth on 2007-03-17
How can the binary not be there, when it is if I do an ls, plus if I uncomment the line that starts with smtp, it works just fine with the binary smtpd? The only change I made was copy and paste:
```
smtp      inet  n       -       n       -       -       smtpd
```
and replaced the smtp with 2525 to become:
```
2525      inet  n       -       n       -       -       smtpd
```
and added the '#' to comment out the listen on smtp (25) line.

Edit:
```
rth@www:~$ sudo find / -name smtpd
/opt/zimbra/postfix-2.2.9/libexec/smtpd
```

---

### Post by Mr. C. on 2007-03-18
The line you had in your master.cf as posted was:

2525      inet  n       -       n       -       -       sm**pt**d

The correct program is sm**tp**d [ note transposed t and p ]

You indicated that the only difference was the change from **smtp** into **2525**.  Your master.cf shows otherwise.

MrC

---

### Post by rth on 2007-03-18
Wow, I feel like an idiot. Thanks!

---

### Post by Mr. C. on 2007-03-18
You're welcome.  It happens, don't worry about it.

This is why I generally ask for "data" and not "interpretation".  Once we had the data, it was easy to spot.  I tested my theory as well, to verify that it failed in the same manner, which it did as expected.

Cheers,
MrC

---

