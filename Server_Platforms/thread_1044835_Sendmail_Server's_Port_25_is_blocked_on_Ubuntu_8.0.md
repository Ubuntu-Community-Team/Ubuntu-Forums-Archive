---
title: "Sendmail Server's Port 25 is blocked on Ubuntu 8.04"
date: 2009-01-19
forum: Server Platforms
---

### Post by mfhyde on 2009-01-19
Sendmail on Ubuntu 8.04 is supposed to open port 25, both locally and remotely.  On my sendmail server, port 25 is open when viewed locally.  But as seen from other Ubuntu 8.04 boxes connected to the LAN, the sendmail server's port 25 is closed.  

Q1: Is there a way I could have configured Sendmail to produce this result?

Q2: If not through Sendmail configuration, how else could Ubuntu be blocking port 25 like this?

Other info:

On all hosts on the LAN  except at the gateway, the firewalls are set to allow all traffic.

On all hosts on the LAN, TCPwrappers is set to allow connections from all members of the LAN.

On the Sendmail server, SASL is set up to authenticate connections to the ISP's smarthost.  PAM uses the default configuration for SASL; there is no PAM module for Sendmail.

Sendmail does relay messages to the smarthost successfully.

When attempts are made to send email from a LAN box to the sendmail server, it gets bounced back saying that the service is unavailable.

Thanks in advance for your help.

---

### Post by spiderbatdad on 2009-01-19
can you telnet to local on the 8.04 machine? Try```
telnet localhost 25
ehlo localhost
quit
```If that all goes well...
Have you enabled ufw. check ```
man ufw for policies
or
sudo ufw allow 25
```

---

### Post by mfhyde on 2009-01-19
`telnet localhost 25` followed by `ehlo localhost` yields the same result:

$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 sendmail.server ESMTP Sendmail 8.14.2/8.14.2/Debian-2build1; Mon, 19 Jan 2009 21:27:19 -0500; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
ehlo localhost
250-sendmail.server Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP

---

### Post by mfhyde on 2009-01-19
My previous post came was an addon to a previous post, which got lost.  Her is the previous post:

When performed on the Sendmail server, this what I get, and I went
ahead with a ehlo command:

$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 sendmail.server ESMTP Sendmail 8.14.2/8.14.2/Debian-2build1; Mon,
19 Jan 2009 20:43:37 -0500; (No UCE/UBE) logging access from:
localhost(OK)-localhost [127.0.0.1]

ehlo ubuntu.box
250-sendmail.server Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP

When `telnet sendmail.server 25` is performed on another box, the
connection is refused.

ufw updates the firewall polices.  Since the firewall is set to accept
all traffic, I wouldn't expect any changes.  In fact, here is the
output to `iptables -Ln after running `sudo ufw allow 25`:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

(No change.)

---

### Post by spiderbatdad on 2009-01-19
do you have a sendmail.conf file or sendmail.cf?
could you please post?

also what does netstat -tna show you?

---

### Post by mfhyde on 2009-01-19
See attachment.

If this doesn't work, I'll paste it in a reply window...

---

### Post by spiderbatdad on 2009-01-19
I believe this line needs to be commented out:
```
# DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
```
Then, ```
# If you modify this file, you will have to regenerate /etc/mail/sendmail.cf
# by running this file through the m4 preprocessor via one of the following:
#	* make   (or make -C /etc/mail)
#	* sendmailconfig 
#	* m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
# The first two options are preferred as they will also update other files
# that depend upon the contents of this file.
```
Then check the sendmail.cf to see that the option is commented out.
Restart.

I hope this helps. Admittedly, I use exim4.

---

### Post by mfhyde on 2009-01-19
# netstat -tna
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
  
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN

---

### Post by spiderbatdad on 2009-01-19
mmm. maybe edit the line to look like:
dnl DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl

then run:```
m4 sendmail.mc > sendmail.cf
```restart and check sendmail.cf

---

### Post by mfhyde on 2009-01-19
I commented out the line, but `netstat -tnr` now shows no listening on port 25.

Additionally, on the sendmail server, `nmap -p25 localhost` is now showing a closed port 25.

From another box, sendmail server's port 25 is still closed.

---

### Post by spiderbatdad on 2009-01-19
ok found this: [http://www.electrictoolbox.com/article/sendmail/remote-connection-refused/](http://www.electrictoolbox.com/article/sendmail/remote-connection-refused/)

---

### Post by mfhyde on 2009-01-19
I made the change you recommended, but netstat tells me that port 25 is not listening.

---

### Post by mfhyde on 2009-01-19
I found some sendmail and tcpd related items in inetd.conf that needed to be uncommented, but I'm still having the same problems. netstat reports port 25 is listening, but nmap is telling me that from other computers, it is closed.

Does inetd need to be reloaded/restarted?

---

### Post by mfhyde on 2009-01-19
Regarding [http://www.electrictoolbox.com/artic...ction-refused/](http://www.electrictoolbox.com/artic...ction-refused/), good article, but it didn't help me.

---

### Post by mfhyde on 2009-01-20
Problem resolved.  

By default, Sendmail does not allow relaying.  This is done to make life harder for spammers.  However, my mail server is behind a firewall on the gateway, and my mailserver needs to accept email sent to it from other boxes on my LAN.  To enable sendmail to accept such email, relaying must be enabled in /etc/mail/sendmail.mc.  In sendmail 8.14, the four lines that need to be examined are:

dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=127.0.0.1')dnl

The term 'dnl' is short for 'delete until new line' and means to ignore everything that follows until after the next new line -- sendmail's way of identifying a comment.

The lines that have `Name=MTA-v6` or `Name=MSA-v6` refer to the next generation of IP, and do not apply to my LAN.

The lines that have `Name=MTA-v4` or `Name=MSA-v4` refer to the current generation of IP, and `Addr=127.0.0.1` tells sendmail to deliver mail services to the mailserver's user accounts only.  To enable the mailserver to receive mail from other hosts on my network, I put a `dnl` in from of those lines, so now they look like:

dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
dnl DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, Addr=::1')dnl
dnl DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=127.0.0.1')dnl

When relaying is turned off, then port 25 is opened to the mailserver's local users, but closed to the outside world.  When relaying is turned on, then port 25 is opened to both local (to the mailserver)  and remote (to the mailserver) users.  

Sendmail opens and closes this port independently of the firewall.

Other sendmail configuration files are used to narrow the accessibility of port 25, such as /etc/mail/access.

Thanks for the help!

---

