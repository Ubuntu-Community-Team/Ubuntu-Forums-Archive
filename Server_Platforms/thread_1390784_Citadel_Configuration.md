---
title: "Citadel Configuration"
date: 2010-01-26
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-26
I've installed Citadel on my local web server.  I've forwarded port 25, 143, 465 and 993 on my router to the server box's local ip and opened them up in my firewall from Webmin.  My ISP blocks port 25, so I setup a smarthost to relay all outbound messages thru my ISP's smtp server (smtp.comcast.net).

I setup my MX records to point to mydomain.com and can send mail to myself internally.  I can't send or receive externally/outbound though -- it says connection timed out in the citadel smtp queue.  Any thoughts?

---

### Post by volkswagner on 2010-01-26
Did you include your username:password in the smarthost directive.

From Citadel Docs:
> Furthermore, if your relay server requires authentication, you can specify it using username:password@host or username:password@host:port syntax; i.e. “jsmith:pass123@relay99.myisp.com:25” 

Is there any information in logs?

/var/log/mail.info, /var/log/mail.error or /var/log/mail.log

---

### Post by trentscott4 on 2010-01-26
I setup a smarthost as myuser:mypass@smtp.comcast.net:25 and all outbound messages send from Webcit still sit in the que.  Moreover, I still can't send any email to [email]user@mydomain.com[/email] from say a gmail account.

Here's what I've done:

1. Under 'Administration' in Citadel, I hit 'Domain names and Internet mail configuration' and added 'mydomain.com' as a local host alias (domain for which this host receives mail).  I also setup the smart host as described above.
2. Under 'Administration' in Citadel, I hit 'Edit site-wide configuration' and added 'mydomain.com' under 'Fully Qualified Domain Name'.
3. My firewall is off (all ports open), and the router forwards port 25, 143, 465, 587 and 993 to this machine.
4. My etc/network/interfaces looks like:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.5.115
netmask 255.255.255.0
gateway 192.168.5.1

```

5. /etc/resolv.conf looks like:

```

domain hsd1.comcast.net.
search hsd1.comcast.net

nameserver 68.87.69.150
nameserver 68.87.85.102

```

Shound this instead just read the address of my gateway/router?  Like:

```
nameserver 192.168.5.1
```

6. Under /var/log/mail.info, it says:

```
server Citadel: Can't connect to smtp.comcast.net:25: Connection timed out
```

---

### Post by trentscott4 on 2010-01-26
UPDATE: I'm able to send mail -- had to use myuser:mypass@smtp.comcast.net:587 instead.  Can't receive though, changed users email alias to [email]admin@mydomain.com[/email] and internet mail address to [email]admin@mydomain.com[/email] and still cant receive anything from outside.

My node name, fqdn and human readable name are all mydomain.com and I still have the localhost alias set to mydomain.com

---

### Post by volkswagner on 2010-01-26
what is the output of 

```
host yourdomain.com
```

---

### Post by volkswagner on 2010-01-26
> **trentscott4 said:**
> UPDATE: I'm able to send mail -- had to use myuser:mypass@smtp.comcast.net:587 instead.  Can't receive though, changed users email alias to [email]admin@mydomain.com[/email] and internet mail address to [email]admin@mydomain.com[/email] and still cant receive anything from outside.

My node name, fqdn and human readable name are all mydomain.com and I still have the localhost alias set to mydomain.com


Your node name should be your host/server name.
Your Domain name should be yourdomain.com
Your FQDN should be host name plus domain name ie: server1.mydomain.com or mail.mydomain.com or you could leave it as mydomain.com, but node name and FQDN should not be the same.

---

### Post by trentscott4 on 2010-01-27
Ok, I've set my node name to 'server' which is this machines' hostname.  I have an A record pointing server.trentscott.com to my external IP -- so server.trentscott.com is my FQDN.  Under 'Domain names and Internet mail configuration' I have 'trentscott.com' listed as a local mail alias.  On my router, I've forwarded ports 587 and 995 to my local server IP 192.168.5.115.  I've also created rules in my firewall to accept traffic with destination ports 587 & 995 (but not source ports).

I can send mail to external addresses just fine, using myuser:mypass@smtp.comcast.net:587 but still can't reply.  My MX record points to server.trentscott.com, which I've created an A record for.

Any ideas why this wouldn't work?

---

### Post by volkswagner on 2010-01-27
You still may need to open port 143 for IMAP or/and port 110 for POP3.

See if that works.

Does the mail ever get returned to sender w/error?  Anything in the logs?

---

### Post by trentscott4 on 2010-01-27
Ok done, still nothing.  I assume I only need to open them in my firewall as destination ports (not source)? No return mail to sender and logs are completely clean.

---

### Post by AntiBodies on 2010-01-28
yeah I think your ISP is blocking port 25 by default to any of its subscribers IP addresses.

a good way to test is to use a telnet client on outside connection somewhere (anywhere where you arent outgoing blocked on port 25).. you should be able to do a command such as this:

telnet yourserverexternalip 25  (eg telnet 123.123.123.123 25)

and you should get a response.. in this case I think you are not

you can use a telnet client to check for open ports like this.. in the case of a mail server you can actually send an email using telnet commands (google it)

anyway you will have to request from you ISP to unblock port 25 for your IP address which will most likely require getting a static IP which will most likely cost more money 8)

cheers

---

### Post by trentscott4 on 2010-01-28
Yea Comcast blocks port 25.  I think I'm able to get around that using a Smart Host in Citadel with myuser:mypass@smtp.comcast.net:587 which is a secure port instead of 25.  Still no luck on the receiving end though, but I can send.

---

### Post by Lars Noodén on 2010-01-28
> **trentscott4 said:**
> Yea Comcast blocks port 25.  I think I'm able to get around that using a Smart Host in Citadel with myuser:mypass@smtp.comcast.net:587 which is a secure port instead of 25.  Still no luck on the receiving end though, but I can send.

Could you point the MX record to the smart host on the outside?  You might be able to set it to spool the incoming mail and then have the blocked machine (which can access out) connect periodically and get the incoming mail.

---

### Post by trentscott4 on 2010-01-28
Interesting idea... Comcast has two separate servers for their mail --- smtp.comcast.net and mail.comcast.net.  Which of these should I set?  My blocked machine can send outbound using the smarthost, I just can't receive.  Can you explain spooling a little further... sounds like a good idea?

---

### Post by Lars Noodén on 2010-01-28
Look into how MX works.  It's designed for failover so that you can have several machines, either peers or some with priority, receiving mail.  That way if part of the net is down or one machine is down the mail still goes through.  The machines would have to have STMP servers running and keeping the mail until the blocked machine is available.  

The blocked machine could contact outside machines with SMTP, or create a reverse tunnel and the outside machines could then contact the blocked machine 'directly'.  

Fetchmail is probably **not** the right tool for the job in this particular instance, but a look through the  [Fetchmail FAQ](http://fetchmail.berlios.de/fetchmail-FAQ.html) might help give an idea about what is going on behind the scenes.  


```

                        =
            +-----------=----->  STMP
           /            =
imaps<--citadel         =
          | \           =
          |  +----------------<  SMTP (MX 0)
          |             =
          +-------------=-----<  SMTP (MX 10)
                        =

```

Citadel is a composite of many programs including a mail server.  Which mail server (MTA) have you chosen to run inside?  Postfix?

---

### Post by AntiBodies on 2010-04-29
Mainly in respose to "Yea Comcast blocks port 25. I think I'm able to get around that using a Smart Host in Citadel...". Like you have noticed smart hosting is great for sending mail which I expect to work fine.

How are all the mail servers out there supposed to know where to send your email eg [email]username@mydomain.com[/email]?? they use a MX record which is part of your DNS zone file for the mydomain.com domain. this has to point to a server that is ready to recieve mail for mydomain.com and knows what to do with it (put it in a mailbox etc). unfortunately you pointing the MX to comcast servers etc isnt going to do jack unless they know what to do with mail sent to mydomain.com.

IF mydomain.com is purchased from them and they manage the mail already for mydomain.com for you then they do know what to do with it. they will put it in a mailbox (on their servers) and expect you to access it from either IMAP or POP. This is where fetchmail can be used to give the illusion of a local mail server while using another service (in this case comcast as the ISP) as the mail receiver, as fetchmail on a regular basis can go out to another mailbox and retrieve the mail by POP and put it in the local server mailbox (which probably is then accessed via IMAP).

if no mail server knows about mydomain.com you have no choice you need some server on the outside to receive this email or request to get port 25 (incoming) opened by Comcast so then you can point the MX record directly at you local server for receiving the mail.

---

