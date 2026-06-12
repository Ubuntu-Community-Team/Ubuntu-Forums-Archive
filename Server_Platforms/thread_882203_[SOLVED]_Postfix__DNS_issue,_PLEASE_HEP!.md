---
title: "[SOLVED] Postfix / DNS issue, PLEASE HEP!"
date: 2008-08-06
forum: Server Platforms
---

### Post by UzLA on 2008-08-06
Guys,

I'm stuffed.

I had Postfix running on the server for months. But all over sudden it stopped sending emails to extarnal domains.  I must fix it, but I run out of ideas. PLEASE, HELP!

Here is my sad story.

Emails are Ok on the way from client app to my server. They are actually being stuck in the queue as deffered.

So, I have checked logs:
```

Aug  6 22:01:50 www postfix/smtp[3592]: 4F0272264CF3: to=<somemail@examplemail.com>, 
relay=none, delay=386320, delays=386264/0.06/56/0, dsn=4.4.3, status=deferred 
(Host or domain name not found. Name service error for name=mamail.com type=MX: Host not found, try again)

```

"**Host not found, try again**" looks like it is a DNS issue. 

O'Reilly postfix definitive guide says: "The DNS query produced no answer. Either the DNS server is not reachable, or it is broken." It seems to be reasonable.

So I have checked /etc/resolv.conf :
```

www:/etc# cat /etc/resolv.conf
domain croup.de
nameserver 208.84.145.233
nameserver 208.84.145.155
nameserver 208.77.96.36

Then I checked  whether rimary DNS server is working:
www:/etc# man nslookup
Reformatting nslookup(1), please wait...
www:/etc# nslookup
> server 208.84.145.233
Default server: 208.84.145.233
Address: 208.84.145.233#53
> set q=mx
> googlemail.com
Server:         208.84.145.233
Address:        208.84.145.233#53

Non-authoritative answer:
googlemail.com  mail exchanger = 10 alt2.gmail-smtp-in.l.google.com.
googlemail.com  mail exchanger = 50 gsmtp147.google.com.
googlemail.com  mail exchanger = 50 gsmtp183.google.com.
googlemail.com  mail exchanger = 5 gmail-smtp-in.l.google.com.
googlemail.com  mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.

Authoritative answers can be found from:
> 

```

and also 

```

www:/etc# dig mx googlemail.com

; <<>> DiG 9.3.4 <<>> mx googlemail.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39960
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;googlemail.com.                        IN      MX

;; ANSWER SECTION:
googlemail.com.         598     IN      MX      50 gsmtp183.google.com.
googlemail.com.         598     IN      MX      5 gmail-smtp-in.l.google.com.
googlemail.com.         598     IN      MX      10 alt1.gmail-smtp-in.l.google.com.
googlemail.com.         598     IN      MX      10 alt2.gmail-smtp-in.l.google.com.
googlemail.com.         598     IN      MX      50 gsmtp147.google.com.

;; Query time: 1 msec
;; SERVER: 208.84.145.233#53(208.84.145.233)
;; WHEN: Wed Aug  6 22:08:01 2008
;; MSG SIZE  rcvd: 163

www:/etc#

```

SO, it seems that my server's DNS is working fine! (or not?:confused:)

I even restarted postfix just in case.

Now what do I have as a result:
- postfix is up and running;
- postfix accepting emails;
- ostfix sends email to localdomains;
- DNS seems to be working fine;
- and IT DOES NOT SEND EMAILS TO EXTERANL DOMAINS!

I'm really, really confused.

_Please, help!_

_Many thanks in advance!_

---

### Post by StickyStyle on 2008-08-06
Hum, I've got nothing off the top of my head with this one.  So lets turn up the verbosity of postfix to maybe get a little better idea of what is going on.

See this link [http://www.postfix.org/DEBUG_README.html#verbose](http://www.postfix.org/DEBUG_README.html#verbose) and post back the log from sending one test email.

Just for fun lets also see your postfix config, send the output of ```
$postconf -n
```

---

### Post by MJN on 2008-08-07
> **UzLA said:**
> ```

Aug  6 22:01:50 www postfix/smtp[3592]: 4F0272264CF3: to=<somemail@examplemail.com>, 
relay=none, delay=386320, delays=386264/0.06/56/0, dsn=4.4.3, status=deferred 
(Host or domain name not found. Name service error for name=mamail.com type=MX: Host not found, try again)
```

Are we to assume you have munged the destination address yet kept the domain in the error portion untouched? Please don't make us guess these things as it wastes everybody's time given we might end up running around in circles.

mamail.com does not have any MX records, although it does have an A record fallback option but there is no SMTP process listening at the address. Postfix is therefore in limbo waiting for the return of some MX from which to proceed; it will eventually give up if they do not appear in due course.

Mathew

---

### Post by UzLA on 2008-08-07
> **MJN said:**
> Are we to assume you have munged the destination address yet kept the domain in the error portion untouched? Please don't make us guess these things as it wastes everybody's time given we might end up running around in circles.

mamail.com does not have any MX records, although it does have an A record fallback option but there is no SMTP process listening at the address. Postfix is therefore in limbo waiting for the return of some MX from which to proceed; it will eventually give up if they do not appear in due course.

Mathew

Yes I have munged it, as it is (not mine!) private correspondence. So I did not want to publish someone's personal email address/domain. Sorry for that, but it is private VALID email address.  So "mamail.com" and "somemail@examplemail.com" are the things that I ammended. All the rest is untouched. 


Here is a real from my test message data:
```

Aug  7 20:28:40 www postfix/smtp[5622]: 4F51E2294CD3: to=<uzla2010@googlemail.com>, relay=none, delay=90229, delays=90064/108/56/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again)

```

hope it could give some clues.

---

### Post by UzLA on 2008-08-07
thanks you the replay StickyStyle!T
Here is the config and I'm looking at the verbose just right now.

```

www:/home/uzla32# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
inet_interfaces = all
mailbox_size_limit = 0
mydestination = www.myexamplerealFQDNsitename.com, localhost, localhost.localdomain
myhostname = www.myexamplerealFQDNsitename.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

```

---

### Post by UzLA on 2008-08-07
> **StickyStyle said:**
> Hum, I've got nothing off the top of my head with this one.  So lets turn up the verbosity of postfix to maybe get a little better idea of what is going on.

See this link [http://www.postfix.org/DEBUG_README.html#verbose](http://www.postfix.org/DEBUG_README.html#verbose) and post back the log from sending one test email.

Just for fun lets also see your postfix config, send the output of ```
$postconf -n
```


Here is verbose of qmgr, defer, smtp and virtual daemons:

```

Aug  7 20:53:31 www postfix/smtp[19533]: dns_query: googlemail.com (MX): Host not found, try again
Aug  7 20:53:31 www postfix/bounce[19705]: connection established
Aug  7 20:53:31 www postfix/bounce[19705]: master_notify: status 0
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: nrequest
Aug  7 20:53:31 www postfix/smtp[19533]: connect to subsystem private/defer
Aug  7 20:53:31 www postfix/smtp[19533]: send attr nrequest = 0
Aug  7 20:53:31 www postfix/smtp[19533]: send attr flags = 0
Aug  7 20:53:31 www postfix/smtp[19533]: send attr queue_id = C07EF2264CF3
Aug  7 20:53:31 www postfix/smtp[19533]: send attr original_recipient = uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/smtp[19533]: send attr recipient = uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/smtp[19533]: send attr offset = 544
Aug  7 20:53:31 www postfix/smtp[19533]: send attr dsn_orig_rcpt = rfc822;uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/smtp[19533]: send attr notify_flags = 0
Aug  7 20:53:31 www postfix/smtp[19533]: send attr status = 4.4.3
Aug  7 20:53:31 www postfix/smtp[19533]: send attr diag_type =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr diag_text =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr mta_type =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr mta_mname =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr action = delayed
Aug  7 20:53:31 www postfix/smtp[19533]: send attr reason = Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/smtp[19533]: private/defer socket: wanted attribute: status
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: nrequest
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: 0
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: flags
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: flags
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: 0
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: queue_id
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: queue_id
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: C07EF2264CF3
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: original_recipient
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: original_recipient
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: recipient
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: recipient
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: offset
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: offset
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: 544
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: dsn_orig_rcpt
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: dsn_orig_rcpt
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: rfc822;uzla2010@googlemail.com
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: notify_flags
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: notify_flags
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: 0
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: status
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: status
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: 4.4.3
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: diag_type
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: diag_type
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: (end)
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: diag_text
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: diag_text
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: (end)
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: mta_type
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: mta_type
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: (end)
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: mta_mname
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: mta_mname
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: (end)
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: action
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: action
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: delayed
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: reason
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: reason
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute value: Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/bounce[19705]: defer socket: wanted attribute: (list terminator)
Aug  7 20:53:31 www postfix/bounce[19705]: input attribute name: (end)
Aug  7 20:53:31 www postfix/bounce[19705]: bounce_append_proto: flags=0x0 service=defer id=C07EF2264CF3 org_to=uzla2010@googlemail.com to=uzla2010@googlemail.com off=544 dsn_org=rfc822;uzla2010@googlemail.com, notif=0x0 stat=4.4.3 act=delayed why=Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/bounce[19705]: send attr status = 0
Aug  7 20:53:31 www postfix/bounce[19705]: master_notify: status 1
Aug  7 20:53:31 www postfix/bounce[19705]: connection closed
Aug  7 20:53:31 www postfix/smtp[19533]: input attribute name: status
Aug  7 20:53:31 www postfix/smtp[19533]: input attribute value: 0
Aug  7 20:53:31 www postfix/smtp[19533]: private/defer socket: wanted attribute: (list terminator)
Aug  7 20:53:31 www postfix/smtp[19533]: input attribute name: (end)
Aug  7 20:53:31 www postfix/smtp[19533]: C07EF2264CF3: to=<uzla2010@googlemail.com>, relay=none, delay=56, delays=0.05/0.13/56/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again)
Aug  7 20:53:31 www postfix/smtp[19533]: flush_add: site googlemail.com id C07EF2264CF3
Aug  7 20:53:31 www postfix/smtp[19533]: match_hostname: googlemail.com ~? www.unlim-hosting.com
Aug  7 20:53:31 www postfix/smtp[19533]: match_hostname: googlemail.com ~? localhost
Aug  7 20:53:31 www postfix/smtp[19533]: match_hostname: googlemail.com ~? localhost.localdomain
Aug  7 20:53:31 www postfix/smtp[19533]: match_list_match: googlemail.com: no match
Aug  7 20:53:31 www postfix/smtp[19533]: flush_add: site googlemail.com id C07EF2264CF3 status 4
Aug  7 20:53:31 www postfix/smtp[19533]: deliver_request_final: send: "Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again" -1
Aug  7 20:53:31 www postfix/smtp[19533]: send attr status = 4.4.3
Aug  7 20:53:31 www postfix/smtp[19533]: send attr diag_type =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr diag_text =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr mta_type =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr mta_mname =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr action =
Aug  7 20:53:31 www postfix/smtp[19533]: send attr reason = Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/smtp[19533]: send attr status = 4294967295
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: status
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: status
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: 4.4.3
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: diag_type
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: diag_type
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: diag_text
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: diag_text
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: mta_type
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: mta_type
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: mta_mname
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: mta_mname
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: action
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: action
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: reason
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: reason
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: status
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: status
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute value: 4294967295
Aug  7 20:53:31 www postfix/qmgr[5847]: private/smtp socket: wanted attribute: (list terminator)
Aug  7 20:53:31 www postfix/qmgr[5847]: input attribute name: (end)
Aug  7 20:53:31 www postfix/qmgr[5847]: qmgr_queue_throttle: queue googlemail.com: 4.4.3 delivery temporarily suspended: Host or domain name not found. Name service error for name=googlemail.com type=MX: Host not found, try again
Aug  7 20:53:31 www postfix/qmgr[5847]: qmgr_active_done: C07EF2264CF3
Aug  7 20:53:31 www postfix/smtp[19533]: master_notify: status 1
Aug  7 20:53:31 www postfix/qmgr[5847]: wakeup C07EF2264CF3 after 1000 secs
Aug  7 20:53:31 www postfix/smtp[19533]: connection closed
Aug  7 20:53:31 www postfix/qmgr[5847]: qmgr_active_defer: defer C07EF2264CF3
Aug  7 20:53:31 www postfix/qmgr[5847]: qmgr_job_free: C07EF2264CF3 smtp

```

It looks to me that postfix can't actually use local system dns resolver, that drives me mad as it can't be, or am I missing someing?

---

### Post by UzLA on 2008-08-07
please, please, guys, help me! ANY ideas are welcome!

---

### Post by MJN on 2008-08-07
Try restarting Postfix - are there any errors/warnings?

Mathew

---

### Post by StickyStyle on 2008-08-08
We can also try seeing if postfix is in fact making the queries...
```
$sudo tcpdump -n -s 1500 -i eth0 udp port 53
```  (replace eth0 if thats not your interface).

Start that, then try to send a mail.

---

### Post by sprouty on 2008-08-09
Have you checked
```
/var/spool/postfix/etc/resolv.conf
```

this is what postfix uses has its dns server should be the same has
```
/etc/resolv.conf 
```

Hope this helps

---

### Post by ronnieredd on 2008-08-09
Has anyone changed anything in the master.cf file recently? Check the last modified date on /etc/postfix/master.cf
Also try a dig against all of the name servers. It looks like you have 3 of them all on the same ip block.
I don't know if any of this helps yet.
It kind of also sounds like dns queries are only being allowed on a originating port of 53. Modern setups are not using port 53 as originating port - just the destination has to be 53.

Go ahead and post you main.cf and we can look at it.

If you haven't already done so, sign up to and post this in the postfix mailing list. Please post back here whatever the outcome is so others can benefit too though.

---

### Post by UzLA on 2008-08-11
> **sprouty said:**
> Have you checked
```
/var/spool/postfix/etc/resolv.conf
```

this is what postfix uses has its dns server should be the same has
```
/etc/resolv.conf 
```

Hope this helps

Oh almighty SPROUTY! You can see though the Great Network and firewalls! :-) **It worked!** At least the queue is going down now! For some reason /var/spool/postfix/etc/resolv.conf  was completely different from /etc/resolv.conf .

I actually have a good guess why this happened: My hoster force-overwrote /etc/resolv.conf remotely with new servers and did not notified me. :-( But it does not matter now. It is sorted.

**Thanks **a lot to **all of you guys** for ideas and help! Obviously, special thanks to SPROUTY!

***BTW does POSTFIX follow syminks?*** (coz in this case I can just kill /var/spool/postfix/etc/resolv.conf and create a symlink to /etc/resolv.conf, so it would always work).

AFAIK Apache needs special instruction to FollowSymLinks. I can't find any evidencies for such instructions or potential issues with symlinks for Postfix, but I'm not willing to try without having at least some sort of assurance/expirience/advice as I do not want to interrupt service anymore.
Do you have any clues on that one?

---

### Post by MJN on 2008-08-11
You should one lesson from this - **check your logs**!

Every time you (re)started Postfix you would have been warned that the resolv.conf's didn't match - heed these warnings as they're there for a reason!!! (this is why you were asked to restart and check for errors)

> **UzLA said:**
> ***BTW does POSTFIX follow syminks?*** (coz in this case I can just kill /var/spool/postfix/etc/resolv.conf and create a symlink to /etc/resolv.conf, so it would always work).

No - you do not want this. The reason Postfix is not using /etc/resolv.conf is because it is running inside a chroot jail hence it must have its own copy. Linking a jailed file to one outside would negate the purpose of runnining inside a jail in the first place.

Mathew

---

