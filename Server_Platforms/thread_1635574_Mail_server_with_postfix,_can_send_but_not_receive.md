---
title: "Mail server with postfix, can send but not receive"
date: 2010-12-02
forum: Server Platforms
---

### Post by AtomicClock on 2010-12-02
Hello,
The last few days I've been tinkering with postfix, trying to setup a mail server at home. Here's the situation so far:

-The computer is on a residential connection from Charter
-I've got a domain mapped to my IP, using DynDNS
-I've got a router, which is forwarding various ports to the computer, including HTTP (80), POP3 (110), and IMAP (143)

I'm on Ubuntu 10.04, have set up postfix, and can connect to my server with Thunderbird (using the domain). I had to configure postfix to use Charter's SMTP server, but now I can send emails to other servers (Yahoo, Gmail) just fine.

If I telnet into port 25 locally, I can send an email to myself, and that shows up when using Thunderbird. So, postfix itself seems to be working.

Problem is, I can't receive email from outside. Postfix's logs don't show anything at all. I've forwarded the ports on my router, so I think maybe Charter has something to do with it. Using Gmail, I got this report after around a day:

```
This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

    zaven@zaven.doesntexist.com

Message will be retried for 2 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720
[zaven.doesntexist.com
 
(1): Connection timed out]
```

zaven.doesntexist.com is my domain, and I can access HTTP and SSH just fine, for example.

So, any ideas?

Here's the main.cf for postfix:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = zaven.doesntexist.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost.localdomain, localhost, zaven.doesntexist.com, doesntexist.com
relayhost = smtp.charter.net
mynetworks = 127.0.0.0/8, 192.168.1.0/255
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command = 
inet_protocols = all
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
disable_vrfy_command = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtp_tls_loglevel = 1
```

---

### Post by James78 on 2010-12-02
You've said you're using DynDNS. After thinking a bit, your problem is most likely that the DNS for your free "domain" does not have an MX record, which costs money with these services to get. Thus, any outside source cannot find the mail server in the MX record to send mail to. So, the only reason you can send email is because you're relaying through Charter.

In layman's terms, you can't receive email without paying them a fee.

---

### Post by AtomicClock on 2010-12-02
I'm not sure exactly what an MX record entails, but I wondered about that too.

DynDNS allows you to have 2 hosts for free per account, and you can specify that each host be an "MX redirect" to another domain. I had made another host, zaven.dyndns-home.com, and redirected both of my domains to each other. If you try looking up the MX record for either, it gives a listing.
For example, using [http://www.mxtoolbox.com/](http://www.mxtoolbox.com/)

I'm not sure if you were thinking of something else.

---

### Post by James78 on 2010-12-02
From my queries everything seems to be resolving fine.

So it appears you have your MX setup fine. I pinged the IP returned from the DNS queries and it's not responding. Somewhere along the way everything is getting blocked, that looks like what's causing your problem. So the question is, what's causing the external traffic to be discarded? It could be incorrectly forwarded ports, it could also be a feature similar to what my DD-WRT router has, "Block Anonymous WAN Requests (ping)". No external hosts could access me until I disabled that. Let me know, and we might be able to fix this soon.
```
toonarmy@opti-hacker:~$ ping 68.113.1.24
PING 68.113.1.24 (68.113.1.24) 56(84) bytes of data.
^C^
--- 68.113.1.24 ping statistics ---
74 packets transmitted, 0 received, 100% packet loss, time 73010ms
```

---

### Post by AtomicClock on 2010-12-02
Yep, my router did indeed have that option set. I disabled it, and attempted to email again, but still nothing.

The messages sent from my Yahoo account just timed out today. They simply state: "Mail server for "zaven.doesntexist.com" unreachable for too long"

As far as the port forwarding goes, I can only hope that it's working correctly. As I said, if I try to access the server locally, then I can connect just fine. And port 80 is forwarded the exact same way, and HTTP is working fine.

Thanks for your assistance!

---

### Post by James78 on 2010-12-02
I am now getting a reply from you, which is good. I would imagine it would work now.
Could you take a screenshot of your routers port forwarding area and attach it to your next post so I can see what is already done and make suggestions?
```
toonarmy@opti-hacker:~$ ping 68.113.1.24
PING 68.113.1.24 (68.113.1.24) 56(84) bytes of data.
64 bytes from 68.113.1.24: icmp_req=1 ttl=58 time=20.0 ms
64 bytes from 68.113.1.24: icmp_req=2 ttl=58 time=33.9 ms
64 bytes from 68.113.1.24: icmp_req=3 ttl=58 time=20.7 ms
64 bytes from 68.113.1.24: icmp_req=4 ttl=58 time=16.6 ms
64 bytes from 68.113.1.24: icmp_req=5 ttl=58 time=19.4 ms
^C
--- 68.113.1.24 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 16.624/22.145/33.913/6.048 ms
```

---

### Post by AtomicClock on 2010-12-04
Sure, I've attached a screenshot. I set up the POP3 and IMAP ports just like I would any other port. Sorry for the black box, it's hiding the SSH port (which is non standard).

---

### Post by James78 on 2010-12-04
That's quite alright. :)

Now that traffic is now reaching your computer, I believe there's only 1 more thing to do to get this to work.

The cause (now) of your problem is very likely to be that SMTP (port 25) isn't being allowed, which is the standard mail port. So, please create a rule allowing from 25 to 25.

If that does not work, it's likely that your host (Charter) blocks SMTP by default. Lucky you though, I use Charter and they're not blocking it for me, so you should be fine. :)

---

### Post by lisati on 2010-12-04
> **James78 said:**
> If that does not work, it's likely that your host (Charter) blocks SMTP by default. Lucky you though, I use Charter and they're not blocking it for me, so you should be fine. :)
Something like that was my first thought too. When I first set up my email server, I had to ask my ISP (NOT charter, and in a different country) to give me a static IP address, and also ask them to unblock port 25, before Postfix began to receive incoming mail from the outside.

---

### Post by AtomicClock on 2010-12-05
Okay, I forwarded port 25, but when I try to telnet into it externally, it seems like maybe my postfix configuration is messed up. It seems to connect, but then the connection gets closed.
```
TRACE- {zaven|zaven} Sun Dec 05 |07:53:01| ~ | telnet 68.113.1.24 25
Trying 68.113.1.24...
Connected to 68.113.1.24.
Escape character is '^]'.
Connection closed by foreign host.
```

I tried that from the actual computer with postfix running, mind you. I guess that simply using the IP causes it to route externally. If instead I try localhost, everything works fine.
```
TRACE- {zaven|zaven} Sun Dec 05 |07:53:59| ~ | telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 zaven.doesntexist.com ESMTP Postfix (Ubuntu)
ehlo zaven.doesntexist.com
250-zaven.doesntexist.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
```

If you try to connect externally, one immediately noticeable difference is that the SMTP banner (the 220 line) doesn't show. And, of course, it disconnects quickly. Sometimes, it lags, but even then it won't respond to any of your input.

Hmm.

---

### Post by James78 on 2010-12-06
Now that traffic is getting through, there might be something useful in the logs. Can you see anything of use?

---

### Post by SeijiSensei on 2010-12-06
Look at the my_networks directive in /etc/postfix/main.cf.  Only addresses and address blocks permitted here can connect.  Usually when the server accepts a connection then disconnects right away, it's because the sending IP is disallowed.

---

### Post by AtomicClock on 2010-12-06
SUCCESS!

It was strange, the logs were appearing empty. It turns out that I had removed syslogd by accident when I was fiddling with getting logging to work for my router (with syslog-ng). Once syslogd was reinstalled, the logs started showing up.

You were right, SeijiSensei, it was the "my_networks" directive. I had it set to "192.168.1.0/255", which I thought would accept all addresses in my local subnet, but I guess I thought wrong. I just set it to the router's IP, 192.168.1.1, and restarted postfix, and now I can receive emails! Huzzah!

Thanks everyone for helping, especially James for sticking through to the end. I appreciate it very much!

---

### Post by SeijiSensei on 2010-12-06
> **AtomicClock said:**
> You were right, SeijiSensei, it was the "my_networks" directive. I had it set to "192.168.1.0/255", which I thought would accept all addresses in my local subnet

You want to use 192.168.1.0/24.  The 24 means that the subnet mask consists of 24 ones followed by eight zeros.  That number corresponds to the value 255.255.255.0 which is probably why you thought 255 was the correct value.

---

### Post by AtomicClock on 2010-12-06
> **SeijiSensei said:**
> You want to use 192.168.1.0/24.  The 24 means that the subnet mask consists of 24 ones followed by eight zeros.  That number corresponds to the value 255.255.255.0 which is probably why you thought 255 was the correct value.
Ah, I see! I changed it in the config, and everything's working fine. I guess it would help if I actually understood what a subnet mask is. I'll be doing some Wikipedia reading later on.

Arigatou gozaimashita!

---

### Post by James78 on 2010-12-06
> **AtomicClock said:**
> SUCCESS!

It was strange, the logs were appearing empty. It turns out that I had removed syslogd by accident when I was fiddling with getting logging to work for my router (with syslog-ng). Once syslogd was reinstalled, the logs started showing up.

**You were right, SeijiSensei, it was the "my_networks" directive. I had it set to "192.168.1.0/255", which I thought would accept all addresses in my local subnet, but I guess I thought wrong.** I just set it to the router's IP, 192.168.1.1, and restarted postfix, and now I can receive emails! Huzzah!

Thanks everyone for helping, especially James for sticking through to the end. I appreciate it very much!
I missed that. >.<

And no problem. Glad it's working now! ;)

---

### Post by AtomicClock on 2010-12-31
Okay... new problem. I hadn't caught this issue initially because I had just tested by sending mail from a "normal" mail provider to my mail server, and then replying back from my mail server.

It turns out that if I try to write a new message to someone else, something funny happens to my email address. The message gets through, but the address comes up as "zaven@doesntexist.com" instead of "zaven@zaven.doesntexist.com". The subdomain gets stripped away for some reason, which is not good... If they try to reply, then they'll be sending a message to "zaven@doesntexist.com", which is obviously wrong and will result in an undeliverable message.

Any ideas as to why the subdomain is disappearing?

---

### Post by AtomicClock on 2010-12-31
D'oh!
I figured it out around 35 seconds after posting this.
No kidding.

It turns out that I had "masquerade_domains" set to my domain in main.cf. Removing it did the trick.

That's what I get for using configuration options that I don't understand, haha.

Everyone have a good day!

---

### Post by vabdussamad on 2012-06-12
Can you let me know what should be the mynetworks value if i have my email server running on Amazon EC2? For example if i am sending email from my yahoo.com account, what should be the mynetworks value?

---

