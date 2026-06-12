---
title: "cannot send emails"
date: 2013-01-08
forum: Server Platforms
---

### Post by ELMIT on 2013-01-08
I have a remote server, where I used phplist to send out emails. I did not collect the email addresses on that server and one single complaint forced me to stop sending emails there. The servers provider prevented me to send out emails from that server. We solved the problem and they "said" they have opened it again.

However, I still cannot send out any emails. I do not get any error messages. I remeber I have turned off sending emails, but after a couple of months I forgot what I did to prevent also our server to send out emails.

Of course it is also possible that they have not opened to send out emails, ...

Which tests can I make to figure out what could be the problems.

I tried from a web form to send out an email, no success. I have used a simple command line tool:
mail -s test [email]abc@example.com[/email]
just a test
.

and also no email send out, no error.

---

### Post by jonobr on 2013-01-11
Assuming your using port 25

have you tried a trace using a terminal
```
sudo tcpdump -i any -w smtp.pcap -s 1600 port 25
```

Extract smtp.pcap from your machine (or open in wireshark) 

If you want verbose output switch to 

```
sudo tcpdump -i any -vvv -s 1600 port 25
```

That should show your emails are leaving, may even show the reponse

---

### Post by lisati on 2013-01-11
Did the server's admin give you any instructions on acceptable use and any conditions they have for sending out mails?

---

### Post by ELMIT on 2013-01-11
lsati - I assume you meant hosting company, since the admin of that cloud computer is me, ;-)
I had a huge mailing list from another server and brought it to this server, but the hosting service insists that I have to collect the email addresses at their service site and cannot bring it from another site. 
Anyway the addresses were already aged and hardly used in the past years, so some of them forgot that they subscribed, even you could proof (was even included in the email) with IP, date and time. ...


I found now something in the mail.log file:
Jan 12 03:55:52 localhost postfix/qmgr[15567]: 239CE96E: from=<www-data@j8431.servers.jiffybox.net>, size=2352, nrcpt=1 (queue active)
Jan 12 03:55:52 localhost postfix/smtp[17907]: connect to ASPMX.L.GOOGLE.com[173.194.70.27]:25: Connection refused
Jan 12 03:55:52 localhost postfix/smtp[17907]: connect to ASPMX.L.GOOGLE.com[2a00:1450:4001:c02::1b]:25: Network is unreachable
Jan 12 03:55:52 localhost postfix/smtp[17907]: connect to ALT1.ASPMX.L.GOOGLE.com[2a00:1450:4010:c03::1b]:25: Network is unreachable
Jan 12 03:55:52 localhost postfix/smtp[17907]: connect to ALT2.ASPMX.L.GOOGLE.com[74.125.141.27]:25: Connection refused
Jan 12 03:55:52 localhost postfix/smtp[17907]: connect to ALT2.ASPMX.L.GOOGLE.com[2607:f8b0:400e:c00::1b]:25: Network is unreachable
Jan 12 03:55:52 localhost postfix/smtp[17907]: 239CE96E: to=<ronald@elmit.com>, relay=none, delay=96935, delays=96935/0.04/0.01/0, dsn=4.4.1, status=deferred (connect to ALT2.ASPMX.L.GOOGLE.com[2607:f8b0:400e:c00::1b]:25: Network is unreachable)

It seems it is an email that should be send to my email address, which is a google app account.

The question is now, why Google smtp is not reachable. Is it my server or is it a filter at the hosting site?

---

### Post by SeijiSensei on 2013-01-12
If you run the command "telnet ASPMX.L.GOOGLE.com 25" from the terminal prompt, you can simulate an SMTP session.  First, does the command time out, or do you get a reply from the server?  If the command fails entirely, you're being blocked upstream.  If the server replies, try this:

```

[server's SMTP banner displayed]
[COLOR="blue"]ehlo your.server.domain.name[/COLOR]
[server replies]
[color='blue']mail from: you@example.com[/color]
[reply]
[color='blue']rcpt to: someone@somewhere.com[/color]
[reply]
[color='blue']data[/color]
[reply]
[color='blue']first line of message
second line of message
.[/color]
[reply]
[color='blue']quit[/color]

```

Type the lines in blue.  Replace "your.server.domain.name" with the fully-qualified name of your server, and replace the email addresses with legitimate ones.

---

### Post by ELMIT on 2013-01-14
Hosting says, they have not blocked anymore port 25. 
So it must be my server. 

How can I check if it is the firewall? Or what else could it be?

---

### Post by ELMIT on 2013-01-16
I am not sure if that is a good test:

# nmap localhost

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-01-16 12:08 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000014s latency).
Hostname localhost resolves to 3 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
Not shown: 994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
3306/tcp  open  mysql
8088/tcp  open  unknown
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds


I also tried it to my host name and IP address on that server.

---

### Post by SeijiSensei on 2013-01-16
> **ELMIT said:**
> I am not sure if that is a good test:

Was that in reply to my posting?  The steps I outlined are intended to test whether you can reach remote SMTP servers.  Your nmap test only tells you that port 25 is open on your machine.

If you're using Postfix, what is the entry for [mynetworks]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from") in main.cf?  If the server is bound to localhost, as it is by default for security reasons, then you won't get any inbound mail.

---

### Post by ELMIT on 2013-01-16
telnet ASPMX.L.GOOGLE.com 25
Trying 173.194.70.27...
Trying 2a00:1450:4001:c02::1b...
telnet: Unable to connect to remote host: Network is unreachable


mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128


I need outbound emails (sending a contact form to me)

---

### Post by SeijiSensei on 2013-01-17
> Telnet: Unable to connect to remote host: Network is unreachable

Then something is blocking you from connecting.  I suspect it's your ISP.  What if you try 

```
telnet www.google.com 80
```

If you get back something like this:

```
Trying 173.194.75.147...
Connected to www.google.com.

```

then your ISP is probably blocking outbound port 25.  This is a common tactic that ISPs use to thwart spambots on their networks.

---

### Post by ELMIT on 2013-01-17
> **SeijiSensei said:**
> Then something is blocking you from connecting.  I suspect it's your ISP.  What if you try 

```
telnet www.google.com 80
```

If you get back something like this:

```
Trying 173.194.75.147...
Connected to www.google.com.

```

then your ISP is probably blocking outbound port 25.  This is a common tactic that ISPs use to thwart spambots on their networks.

They say, they don't and ask me to reboot the cloud server. I don't like the idea to stop my server for such a "test". Therefore I am looking for a way to make sure that is not my server in any way.


Could do:
> sudo tcpdump -i any -w smtp.pcap -s 1600 port 25

and got finally some data back:
>     myserver.net.34461 > da-in-f27.1e100.net.smtp: Flags [S], cksum 0x82a1 (incorrect -> 0xa39b), seq 290274480, win 14600, options [mss 1460,sackOK,TS val 3895864321 ecr 0,nop,wscale 5], length 0
01:26:09.028060 IP (tos 0x0, ttl 64, id 4274, offset 0, flags [DF], proto TCP (6), length 60)
    myserver.net.34461 > da-in-f27.1e100.net.smtp: Flags [S], cksum 0x82a1 (incorrect -> 0x9fb0), seq 290274480, win 14600, options [mss 1460,sackOK,TS val 3895865324 ecr 0,nop,wscale 5], length 0
01:26:12.032043 IP (tos 0x0, ttl 64, id 27822, offset 0, flags [DF], proto TCP (6), length 60)
    myserver.net.34459 > da-in-f27.1e100.net.smtp: Flags [S], cksum 0x82a1 (incorrect -> 0x2012), seq 1962364138, win 14600, options [mss 1460,sackOK,TS val 3895868328 ecr 0,nop,wscale 5], length 0
01:26:20.040796 IP (tos 0x0, ttl 64, id 49369, offset 0, flags [DF], proto TCP (6), length 60)
    myserver.net.34463 > da-in-f27.1e100.net.smtp: Flags [S], cksum 0x82a1 (incorrect -> 0xd706), seq 1366792745, win 14600, options [mss 1460,sackOK,TS val 3895876336 ecr 0,nop,wscale 5], length 0
01:26:20.041664 IP (tos 0x0, ttl 64, id 61716, offset 0, flags [DF], proto TCP (6), length 60)
    myserver.net.47065 > lb-in-f27.1e100.net.smtp: Flags [S], cksum 0x9fe6 (incorrect -> 0xab77), seq 483044325, win 14600, options [mss 1460,sackOK,TS val 3895876337 ecr 0,nop,wscale 5], length 0


Is there something we can use to proof the blocked port?

---

### Post by jonobr on 2013-01-17
The tcpdump shows your sending packets.

Nothing is being received back.

If the SMTP port number was changed you would get an application not available message back.
If the SMTP application was not on this IP address
You would get the same message.

It looks as if the only conclusion you can make (assuming you are not blocking anything on your network) is that the packets you are sending are silently being dropped somewhere outside your network.

---

### Post by SeijiSensei on 2013-01-18
> **ELMIT said:**
> They say, they don't and ask me to reboot the cloud server.

Are you sure you asked specifically about *outbound* SMTP traffic and not *inbound*?  What explanation do they give for your inability to connect to Google's mail server using telnet?

---

### Post by ELMIT on 2013-01-18
Their explanation: It is open! Thank you for your email. If you have further question, please do not hesitate to contact us, ....


They suggested to add hping ([http://www.hping.org/download.html](http://www.hping.org/download.html))
./configure and make strip  gives me:
> # make strip
gcc -c -O2 -Wall -DBYTE_ORDER_LITTLE_ENDIAN  -g  arsglue.c
In file included from ars.h:18:0,
                 from arsglue.c:5:
bytesex.h:22:3: error: #error can not find the byte order for this architecture, fix bytesex.h
make: *** [arsglue.o] Error 1


I added already -DBYTE_ORDER_LITTLE_ENDIAN  to the gcc line in the Makefile


I tried nmap instead:
nmap localhost -p25

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-01-18 23:47 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000092s latency).
Hostname localhost resolves to 3 IPs. Only scanned 127.0.0.1
rDNS record for 127.0.0.1: localhost.localdomain
PORT   STATE SERVICE
25/tcp open  smtp

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds


nmap ASPMX.L.GOOGLE.com -p25

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-01-18 23:47 CET
Nmap scan report for ASPMX.L.GOOGLE.com (173.194.70.26)
Host is up (0.0075s latency).
rDNS record for 173.194.70.26: fa-in-f26.1e100.net
PORT   STATE    SERVICE
25/tcp filtered smtp

Nmap done: 1 IP address (1 host up) scanned in 0.19 seconds



It is now a game  IT IS YOUR FAULT, no it is yours.

How to determine it?

---

### Post by ELMIT on 2013-01-18
> It looks as if the only conclusion you can make (assuming you are not blocking anything on your network) is that the packets you are sending are silently being dropped somewhere outside your network.


Exactly that I want to figure out, IF on my machine is something blocked.

---

