---
title: "Postfix Problems"
date: 2008-07-01
forum: Server Platforms
---

### Post by Bakerconspiracy on 2008-07-01
Alright, so I've been working on this postfix - dovecot server all day now. I've seemed to get the pop connection working correctly (without encryption for now), but I cannot seem to get postfix to receive mail or send mail externally. I accessed a system mail from cron on an email client (evolution) enabled with pop [I guess the system just sent it too me, my alias for root is my user acct]:

----------------------------------------------------------------------
Subject: 	Anacron job 'cron.daily' on alienware
Date: 	Tue,  1 Jul 2008 07:35:44 -0700 (PDT) (10:35 EDT)

/etc/cron.daily/logrotate:
error: alamin-server:8 unknown user 'alamin'
run-parts: /etc/cron.daily/logrotate exited with return code 1
---------------------------------------------------------------------

I'm assuming this means the pop side (MDA) is working right? I can telnet into the smtp port (which I know isn't blocked by my isp -- obviously), but I honestly have no idea what's going wrong, evolution can't use it. Here's my main.cf: 

andrew@alienware:/etc/init.d$ cat /etc/postfix/main.cf
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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = alienware
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydomain = 70.*******
mydestination = alienware localhost $mydomain
relayhost =
relay_domains =
mynetworks = 127.0.0.0/8 192.168.1.0/255
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
---------------------------------------------------------------------
---------------------------------------------------------------------
My master.cf is straight out of the box, only the port is changed so it's not blocked by the ISP.

My goal here is to be able to send and receive emails from a client, from anywhere. Please let me know if you have any suggestions, I'm beating my head against the wall on this one.

---

### Post by rabble on 2008-07-02
Sorry.  This isn't a solution to your problem.  I just have the same or maybe a similar problem.  I have installed postfix and both coriur imap and courier pop.  Both seem to sorta work using terminal but nothing happens when I try to access my mail through evolution.  I'm scratching my head wondering what's up.

Can anybody help?

---

### Post by MJN on 2008-07-02
> **Bakerconspiracy said:**
> mydomain = 70.*******
 
As an aside, this really should be your domain name it will prove highly unworkable to be using your IP address as your e-mail domain.
 
> My master.cf is straight out of the box, only the port is changed so it's not blocked by the ISP.
 
Explain exactly what you mean by this as it is ambiguous. Better still, also post the modified line from master.cf.
 
'It doesn't work' really doesn't help - if you can post your logs and a description of exactly what you are doing and trying to do that would help enormously.
 
Note that without an IP address or real domain name we are severely limited with regards to fault finding from our side(s).
 
Mathew

---

### Post by Bakerconspiracy on 2008-07-03
Alright. MJN let's do a recap... 

> I've seemed to get the pop connection working correctly (without encryption for now), but I cannot seem to get postfix to receive mail or send mail externally.

By pop connection, I mean I can grab messages that are already distributed by the system. I think this is a characteristic of it working because I can get these using a evolution mail client. Overall what I am trying to say is: it's not dovecot that is not configured correctly, it's plain and simply postfix.

> My goal here is to be able to send and receive emails from a client, from anywhere.

----- Where does it say, "It doesn't work" in these two quotes?

Anyways, here is the master.cf file change:

> 587        inet  n       -       -       -       -       smtpd

I changed the smtp port to the submission port. 

As far as the logs, there are no entries for /var/log/mail.err, /var/log/mail.info and /var/log/mail.warn .

I have fear of just plain posting my IP, I don't have a strong firewall setup and a pretty open mail system right now. If you could help me by using my IP, I would gladly give it to you, but I just don't want to give it to everyone looking at this forum. 

Thanks for your help,
Andrew

---

### Post by MJN on 2008-07-03
> **Bakerconspiracy said:**
> Where does it say, "It doesn't work" in these two quotes?I didn't mean literally but rather the absence of any 'evidence' of what is/isn't happening. The lack of such info means we're flying blind.

> I changed the smtp port to the submission port.Doing that means you will never receive any e-mail for your domain from the Internet. I'm not sure that was your intent but that's the effect. This explains the lack of incoming e-mail.

> As far as the logs, there are no entries for /var/log/mail.err, /var/log/mail.info and /var/log/mail.log ./var/log/mail.log is what's required - does it not contain *anything*?

> I have fear of just plain posting my IP, I don't have a strong firewall setup and a pretty open mail system right now. If you could help me by using my IP, I would gladly give it to you, but I just don't want to give it to everyone looking at this forum. There's no need now as we know why Internet-sourced e-mail is not reaching you (they are only ever going to connect to port 25. Only your own clients will get any joy with the submission port).

Mathew

---

### Post by Bakerconspiracy on 2008-07-03
> I didn't mean literally but rather the absence of any 'evidence' of what is/isn't happening. The lack of such info means we're flying blind.
I knew what you meant, but I thought I provided clear enough evidence. I apologize for this, I was extremely frustrated. I gave "the problem" 4-5 consecutive hours of my time.

/var/log/mail.log doesn't have anything in it. Although, postfix did grab onto the syslogd daemon automatically. Should be some sort of log there...

> There's no need now as we know why Internet-sourced e-mail is not reaching you (they are only ever going to connect to port 25. Only your own clients will get any joy with the submission port).

As for this, I'm surprised I didn't think about this / find this info in my research. Thank you for helping me, you solved my problem.  Just a few more things if you are willing though....

Cox (my ISP) blocks port 25. Should I still be able to log into the smtp sever and send a piece of mail through port 587 (As long as the IP I'm using is added to the mynetworks parameters of main.cf)? Any ideas on how to route all the traffic from port 25 to 587 before my ISP blocks it?

Thanks again.
Andrew

---

### Post by MJN on 2008-07-03
> **Bakerconspiracy said:**
> Cox (my ISP) blocks port 25.Are you sure they block *incoming* port 25? Some do, to stop you running servers, but many only block outgoing 25 in order to cut down on spam originating from their networks.

> Should I still be able to log into the smtp sever and send a piece of mail through port 587 (As long as the IP I'm using is added to the mynetworks parameters of main.cf)?Sure - you'll have no problem. Indeed you could use any (non-blocked) port you liked just as long as you have an SMTPD daemon listening on it.

Note that there's no need to add your IP to mynetworks as presumably you will be using SMTP authentication in order to stop others from using your server for their spam? If not, then I suppose adding the IP will suffice assuming it won't change and/or you won't be having other (authorised) users also wishing to use the server.

> Any ideas on how to route all the traffic from port 25 to 587 before my ISP blocks it?Assuming you mean in order to receive e-mail from other domains I'm afraid your options are very limited. You would have to employ a 3rd party solution that will accept mail for your domain on your behalf and then relay it to your server on a custom port of your choice. I'm not familiar with who offers this, although I do know that no-ip.org does provide it (whether that be for domains from them, or your own, I don't know).

Mathew

---

