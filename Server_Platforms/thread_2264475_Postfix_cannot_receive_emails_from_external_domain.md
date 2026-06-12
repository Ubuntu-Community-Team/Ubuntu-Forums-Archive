---
title: "Postfix cannot receive emails from external domain"
date: 2015-02-07
forum: Server Platforms
---

### Post by papps2 on 2015-02-07
I know this question has been asked umpteen times, but after lot of research, it did not solve my problem, so I thought of posting it.


I've installed postfix on a server. I use ssh to log into the server and perform tasks. I can send/receive e-mails from local users and I can send e-mail to external domain using Python script. 


However, when I send email from gmail to my account on the server, I do not see anything in Maildir/new folder. Also, I do not receive any errors from gmail (such as delivery failure). Can anyone please help me out.


I've replaced my original hostname and domain name.
Here's my postconf -n output:

```

    alias_database = hash:/etc/aliases
    alias_maps = hash:/etc/aliases
    append_dot_mydomain = no
    biff = no
    config_directory = /etc/postfix
    home_mailbox = Maildir/
    inet_interfaces = all
    inet_protocols = all
    mailbox_command =
    mailbox_size_limit = 0
    mydestination = myserver, localhost.localdomain, localhost, myserver.xx.xyzw.edu
    myhostname = myserver.xx.xyzw.edu
    mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 , 192.168.0.0/24
    myorigin = /etc/mailname
    readme_directory = no
    recipient_delimiter = +
    relayhost =
    smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
    smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
    smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
    smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
    smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
    smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
    smtpd_use_tls = yes

```

Output of master.conf file:

```

    /etc/postfix/master.cf
    ::::::::::::::
    #
    # Postfix master process configuration file.  For details on the format
    # of the file, see the master(5) manual page (command: "man 5 master" or
    # on-line: [http://www.postfix.org/master.5.html](http://www.postfix.org/master.5.html)).
    #
    # Do not forget to execute "postfix reload" after editing this file.
    #
    # ==========================================================================
    # service type  private unpriv  chroot  wakeup  maxproc command + args
    #               (yes)   (yes)   (yes)   (never) (100)
    # ==========================================================================
    smtp      inet  n       -       -       -       -       smtpd
    #smtp      inet  n       -       -       -       1       postscreen
    #smtpd     pass  -       -       -       -       -       smtpd
    #dnsblog   unix  -       -       -       -       0       dnsblog
    #tlsproxy  unix  -       -       -       -       0       tlsproxy
    #submission inet n       -       -       -       -       smtpd
    #  -o syslog_name=postfix/submission
    #  -o smtpd_tls_security_level=encrypt
    #  -o smtpd_sasl_auth_enable=yes
    #  -o smtpd_reject_unlisted_recipient=no
    #  -o smtpd_client_restrictions=$mua_client_restrictions
    #  -o smtpd_helo_restrictions=$mua_helo_restrictions
    #  -o smtpd_sender_restrictions=$mua_sender_restrictions
    #  -o smtpd_recipient_restrictions=
    #  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
    #  -o milter_macro_daemon_name=ORIGINATING
    #smtps     inet  n       -       -       -       -       smtpd
    #  -o syslog_name=postfix/smtps
    #  -o smtpd_tls_wrappermode=yes
    #  -o smtpd_sasl_auth_enable=yes
    #  -o smtpd_reject_unlisted_recipient=no
    #  -o smtpd_client_restrictions=$mua_client_restrictions
    #  -o smtpd_helo_restrictions=$mua_helo_restrictions
    #  -o smtpd_sender_restrictions=$mua_sender_restrictions
    #  -o smtpd_recipient_restrictions=
    #  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
    #  -o milter_macro_daemon_name=ORIGINATING
    #628       inet  n       -       -       -       -       qmqpd
    pickup    unix  n       -       -       60      1       pickup
    cleanup   unix  n       -       -       -       0       cleanup
    qmgr      unix  n       -       n       300     1       qmgr
    #qmgr     unix  n       -       n       300     1       oqmgr
    tlsmgr    unix  -       -       -       1000?   1       tlsmgr
    rewrite   unix  -       -       -       -       -       trivial-rewrite
    bounce    unix  -       -       -       -       0       bounce
    defer     unix  -       -       -       -       0       bounce
    trace     unix  -       -       -       -       0       bounce
    verify    unix  -       -       -       -       1       verify
    flush     unix  n       -       -       1000?   0       flush
    proxymap  unix  -       -       n       -       -       proxymap
    proxywrite unix -       -       n       -       1       proxymap
    smtp      unix  -       -       -       -       -       smtp
    relay     unix  -       -       -       -       -       smtp
    #       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
    showq     unix  n       -       -       -       -       showq
    error     unix  -       -       -       -       -       error
    retry     unix  -       -       -       -       -       error
    discard   unix  -       -       -       -       -       discard
    local     unix  -       n       n       -       -       local
    virtual   unix  -       n       n       -       -       virtual
    lmtp      unix  -       -       -       -       -       lmtp
    anvil     unix  -       -       -       -       1       anvil
    scache    unix  -       -       -       -       1       scache
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
      flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
    #
    # ====================================================================
    #
    # Recent Cyrus versions can use the existing "lmtp" master.cf entry.
    #
    # Specify in cyrus.conf:
    #   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
    #
    # Specify in main.cf one or more of the following:
    #  mailbox_transport = lmtp:inet:localhost
    #  virtual_transport = lmtp:inet:localhost
    #
    # ====================================================================
    #
    # Cyrus 2.1.5 (Amos Gouaux)
    # Also specify in main.cf: cyrus_destination_recipient_limit=1
    #
    #cyrus     unix  -       n       n       -       -       pipe
    #  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
    #
    # ====================================================================
    # Old example of delivery via Cyrus.
    #
    #old-cyrus unix  -       n       n       -       -       pipe
    #  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
    #
    # ====================================================================
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
      flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
    scalemail-backend unix	-	n	n	-	2	pipe
      flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
    mailman   unix  -       n       n       -       -       pipe
      flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
      ${nexthop} ${user}

```

There are no rules in my iptables -nL, so I guess firewall is not a problem here:





```

    Chain INPUT (policy ACCEPT 15949 packets, 2260K bytes)
     pkts bytes target     prot opt in     out     source               destination         
    
    Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
     pkts bytes target     prot opt in     out     source               destination         
    
    Chain OUTPUT (policy ACCEPT 15694 packets, 2593K bytes)
     pkts bytes target     prot opt in     out     source               destination

```

 




I checked my domain on mxtools - it's not blacklisted.


port 25 listens to postfix as well.

```

    netstat -a -n -p | grep :25
    tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      16941/master    
    tcp6       0      0 :::25                   :::*                    LISTEN      16941/master

```

I can provide more information if required. Please help. Thanks.

P.S. I do not have dovecot installed on the server (Do I need that to receive emails ?? I am not sure!!)

---

### Post by Doug S on 2015-02-07
Hi and welcome to Ubuntu forums.

When you send an e-mail from your gmail account do you observe entries in /var/log/mail.log and/or /var/log/mail.err?

---

### Post by papps2 on 2015-02-07
No.. Nothing.

This is what I get when I send email from my server to gmail address
```

Feb  7 13:38:12 MYSERVER postfix/qmgr[15753]: 9DB8211E0B83: from=<troll@noob.com>, size=374, nrcpt=1 (queue active)
Feb  7 13:38:13 MYSERVER postfix/smtp[15762]: 9DB8211E0B83: to=<xyzw@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.22.26]:25, delay=0
.68, delays=0.04/0.01/0.35/0.28, dsn=2.0.0, status=sent (250 2.0.0 OK 1423334293 f110si7547484qgf.1 - gsmtp)
Feb  7 13:38:13 MYSERVER postfix/qmgr[15753]: 9DB8211E0B83: removed

```
/var/log/mail.err is empty

---

### Post by lisati on 2015-02-07
What I'm seeing in the log entries is the successful delivery *from* your server *to* gmail.

I'm wondering:
[LIST]
[*]Is the DNS entry for your domain pointing to the correct public IP address for your server?
[*]Do you have appropriate port forwarding set up on your router?
[*]Is your ISP blocking incoming connections on port 25?
[/LIST]

---

### Post by papps2 on 2015-02-07
Yes, that's what I have on log file.

1. Yes. When I do "dig" it correctly points to the mx record.

[COLOR=#000000][FONT=proxima-nova]dig mx myserver.xy.xyzw.edu
; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> mx myserver.xy.xyzw.edu
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12790
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 6
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;myserver.xy.xyzw.edu. IN MX
;; ANSWER SECTION:
myserver.xy.xyzw.edu. 21600 IN MX 0 myserver.xy.xyzw.edu.
;; ADDITIONAL SECTION:
myserver.xy.xyzw.edu. 21600 IN A "corresponding IP address"

2. Hmm.. I am not sure. I am using ssh to log into the server. Any idea where and how I can check this?

3. There are no firewall rules specified. Is it still possible that port 25 is blocked?

Also, is there any way I can private message you. I can give you real domain name and IP if you can help me out.

Many thanks.


[/FONT][/COLOR]

---

### Post by lisati on 2015-02-07
MX Toolbox have a page where you can do some simple diagnostic tests on your mail server. It can be found at [http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx)

---

### Post by Doug S on 2015-02-07
> **papps2 said:**
> 2. Hmm.. I am not sure. I am using ssh to log into the server. Any idea where and how I can check this?Well, is your server directly connected to your external IP address? Or is there a router between it and the internet? If there is a router, then you would have to check your router settings.> **papps2 said:**
> 3. There are no firewall rules specified. Is it still possible that port 25 is blocked?Yes. Some ISPs block port 80 and port 25 and such. You will have to check with your ISP, but only after the previous question is sorted out.> **papps2 said:**
> Also, is there any way I can private message you. I can give you real domain name and IP if you can help me out.There would be no value added in doing that just yet, but eventually there might be.

Edit: I was typing for awhile, and did not lisati's last reply.

---

### Post by papps2 on 2015-02-07
Looks like we're getting closer.

SMTP test failed with "Unable to connect - try after 15 secs"

I then ran Port scan operation on mxtoolbox

only port 22 and 8080 has green tick marks - all others red !!

Does this mean all other ports are closed? How can I configure them to be open??

EDIT : I'm confused !!! If port 25 is closed, why am I able to send mails to external domain???

Doug S and Lisati !! what you think?

---

### Post by Doug S on 2015-02-07
> **papps2 said:**
> Does this mean all other ports are closed? How can I configure them to be open??We don't know. Do you have a router invovled? If yes, then you need to access it's configuration stuff and enable port 25 port forwarding. There is a "how to" web site for that, but I don't recall the URL just now.> **papps2 said:**
> I'm confused !!! If port 25 is closed, why am I able to send mails to external domain???Because when you send e-mail the destination port is 25 and the source port is some high number and you initiate the connection. When you receive e-mail the external device will be trying to access port 25 and it is initiating the connection. In summary: sending and receiving e-mails are two completely different events.

---

### Post by papps2 on 2015-02-07
Thanks for clarifying. I am using the university server so I'm not really sure if I have router anywhere in between. I need to find out. I'll keep this question open for couple of days, just in case even after opening the port, if the problem is not solved. Thanks again !!

---

### Post by phs2004 on 2015-02-08
Need to change relayhost = smtp.myisp.com in main.cf. Google search your [COLOR=#000000]universitys [/COLOR] smtp (relayhost) server. Or use another port 2525.

---

### Post by SeijiSensei on 2015-02-08
> **papps2 said:**
> Thanks for clarifying. I am using the university server so I'm not really sure if I have router anywhere in between. I need to find out. I'll keep this question open for couple of days, just in case even after opening the port, if the problem is not solved. Thanks again !!

I'm not sure what you mean by "using the university server."  Your university has a server on which it allows you to install Postfix?  What policies does the university have on running servers?

I wouldn't be at all surprised that the university doesn't permit inbound SMTP traffic to random machines on campus.  Have you talked with your university's IT admins about what you're trying to do?

---

