---
title: "Postfix and Gmail"
date: 2006-02-19
forum: Server Platforms
---

### Post by Burke on 2006-02-19
I posted this in the general support forum and came to the conclusion that it was a poor decision, so I'm reposting here -- sorry!

So anyway, I'm trying to use Postfix to send mail -- through Gmail. I've followed the directions here: [http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html) , and It works about 70%. When I try to actually send mail (using mutt), it doesn't work. Here's the output from my /var/log/mail.info:

```
Feb 19 19:45:28 burke postfix/pickup[12963]: E38D275034B: uid=1000 from=<xxxxxxxxxxxxxx@gmail.com>
Feb 19 19:45:28 burke postfix/cleanup[13899]: E38D275034B: message-id=<20060220014527.GA13891@burke.fake.com>
Feb 19 19:45:28 burke postfix/qmgr[10635]: E38D275034B: from=<xxxxxxxxxxxxxx@gmail.com>, size=416, nrcpt=1 (queue active)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to gmail-smtp-in.l.google.com[72.14.205.27]: Connection timed out (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt2.gmail-smtp-in.l.google.com[66.249.83.27]: No route to host (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt1.gmail-smtp-in.l.google.com[64.233.167.27]: No route to host (port 25)
Feb 19 19:45:58 burke postfix/smtp[13901]: connect to alt2.gmail-smtp-in.l.google.com[66.249.83.114]: No route to host (port 25)
Feb 19 19:46:19 burke postfix/qmgr[10635]: B25037500C7: from=<root@burke.fake.com>, size=434, nrcpt=1 (queue active)
```

I'm not really sure what's going on here -- I'm pretty sure my ISP blocks outbound connections to :25. Should I be trying to connect to :25, or should it be 587 or 465, because of the TLS/SSL?

Maybe if I could route this traffic through TOR (which I already have installed)? 

I would greatly appreciate any help.


EDIT:  I forgot my main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = xxxxxxxxxxxxxxxxxxxxxxxxx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


readme_directory = no
sample_directory = /etc/postfix
sendmail_path = /usr/sbin/sendmail
html_directory = no
setgid_group = postdrop
command_directory = /usr/sbin
manpage_directory = /usr/local/man
daemon_directory = /usr/libexec/postfix
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
queue_directory = /var/spool/postfix
mail_owner = postfix
unknown_local_recipient_reject_code = 450




    ## TLS Settings
    #
    # For no logs set = 0
    smtp_tls_loglevel = 1
    #
    # smtp_enforce_tls = yes
    # Above is commented because doing it site by site below
    smtp_tls_per_site = hash:/etc/postfix/tls_per_site
    #
    smtp_tls_CAfile = /etc/postfix/cacert.pem
    smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
    smtp_tls_key_file = /etc/postfix/FOO-key.pem
    smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
    smtp_use_tls = yes
    smtpd_tls_CAfile = /etc/postfix/cacert.pem
    smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
    smtpd_tls_key_file = /etc/postfix/FOO-key.pem
    smtpd_tls_received_header = yes
    smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
    smtpd_use_tls = yes
    tls_random_source = dev:/dev/urandom

    ##  SASL Settings
    # This is going in to THIS server
    smtpd_sasl_auth_enable = no
    # We need this
    smtp_sasl_auth_enable = yes
    smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
    smtpd_sasl_local_domain = $myhostname
    smtp_sasl_security_options = noanonymous
    #smtp_sasl_security_options =
    smtp_sasl_tls_security_options = noanonymous
    smtpd_sasl_application_name = smtpd


    ## Gmail Relay
    relayhost = [smtp.gmail.com]

    ## Good for Testing
    # sender_bcc_maps = hash:/etc/postfix/bcc_table

    # Disable DNS Lookups
    disable_dns_lookups = yes
    #
    # Great New feature Address Mapping
    smtp_generic_maps = hash:/etc/postfix/generic
    #
    #
    transport_maps = hash:/etc/postfix/transport

```


again, thank you.

---

### Post by heimo on 2006-02-20
I'm afraid I can't help you, but this bit of information may be helpful. As you doubted that your ISP may be blocking outbound 25 connections, try it using telnet.
**[SIZE=2][/SIZE]**```
telnet 72.14.205.27 25
```

This should not timeout. If you get a reply, just write *quit *[enter].

---

### Post by Burke on 2006-02-20
burke@burke:~$ telnet 72.14.205.27 25
Trying 72.14.205.27...
telnet: Unable to connect to remote host: No route to host

burke@burke:~$ telnet minnedosa.com 25
Trying 216.180.238.52...
telnet: Unable to connect to remote host: No route to host

burke@burke:~$ telnet burke.area526.net 25
Trying 69.50.171.194...
telnet: Unable to connect to remote host: No route to host


...I guess it's definitely blocked! ;)

---

### Post by heimo on 2006-02-20
*no route to host *seems like something else. My experience is that if port is blocked, it'll just timeout. Your first post shows how the connection timeouts and then there's just no route to other alternative hosts. That's weird, could be somekind of higher level (talking about TCP/IP / OSI-model) block, more "intelligent". Or I'm just missing something. 

Your network connection is otherwise working properly? Can you ping those ip addresses? I just checked that at least 72.14.205.27 should reply to pings. Be aware that that's only one of Googles email servers, you can run *dig google.com mx *to see couple more addresses (lines with smtp*)

But anyway. It could very well be that your ISP blocks outbound connections to 25 (that's pretty common practise these days), it may well be documented on your ISPs support pages.

---

### Post by Burke on 2006-02-20
My connection is working flawlessly overall, and I can ping the address without issue.

Here is someone else with the same problem: [http://ubuntuforums.org/showthread.php?t=124530](http://ubuntuforums.org/showthread.php?t=124530)

I'm inclined to think this is all caused by my ISP blocking :25 (which I've just confirmed is the case).

So, now I need to find out how to route postfix traffic through TOR. I already have both TOR and Postfix installed, so if anyone's reading and happens to be a postfix guru, could you let me know how to do this?

Thank you for your time, Heimo, and anyone else who can help.

---

### Post by LordHunter317 on 2006-02-20
I'm pretty sure you can't, and even if you could, you wouldn't want to.  The mail would likely be universally rejected on the other side.

Send your mail through your ISP's email servers, like you're supposed to.

---

### Post by eviltwin on 2006-02-20
it should be port 587 or 465. You also need to set up the connectivity in your gmail account under settings (where it has full details on ports/addresses). Have fun. ;)

---

### Post by Burke on 2006-02-20
nevermind, I finally figured it out.

options in main.cf have to start at the start of the line -- not indented. I fixed that and it more or less ran right away. 

Even though 25 outgoing is blocked, Gmail uses 587, which avoids that little problem ;)  

Thanks for the help guys!

---

