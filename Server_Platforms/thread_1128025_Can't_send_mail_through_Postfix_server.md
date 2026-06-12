---
title: "Can't send mail through Postfix server"
date: 2009-04-17
forum: Server Platforms
---

### Post by botfish on 2009-04-17
I have setup Postfix by following the instructions at
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

How do I send mail from a remote client (i.e. Thunderbird) through my Postfix server?

The following is working ok:
I can send mail from the local machine ($ netcat localhost 25 ...) and download that mail using remote POP
I can send mail from the local machine ($ netcat mydomain.com 25 ...) and download that mail using remote POP
I can send mail from gmail to [email]me@mydomain.com[/email] and download that mail using remote POP

But: I can't send mail from Thunderbird to my Postfix server for delivery.

From a remote machine:
$ netcat mydomain.com 25
mydomain.com [xxx.xx.xxx.xxx] 25 (smtp) : Connection timed out

~$ ping -c 1 mydomain.com
1 packets transmitted, 1 received, 0% packet loss, time 0ms

$ ping -c 1 mail.mydomain.com
1 packets transmitted, 1 received, 0% packet loss, time 0ms

$ ping -c 1 mail.mydomain.com 25
1 packets transmitted, 0 received, 100% packet loss, time 0ms


My Postfix configuration files:

/etc/postfix/main.cf
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

myhostname = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomain.com, mail.mydomain.com, localhost, lo
calhost.com
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_recipient_limit = 500
smtp_recipient_restrictions =
 check_recipient_access hash:/etc/postfix/recipient_access

/etc/postfix/recipient_access
mydomain.com OK

---

### Post by botfish on 2009-04-17
Additional information that I should have included in the original post:

$ netstat -l -n | grep :25
tcp        0      0 0.0.0.0:25              0.0.0.0:*             LISTEN

It stands out to me that there is no network address listed. Not sure of the significance.

---

### Post by wkulecz on 2009-04-17
What is your smtp server setup in Thunderbird for outgoing mail?

Is Thunderbird running on the same computer as the postfix smtpd?

--wally.

---

### Post by botfish on 2009-04-17
Thunderbird is on a remote computer. I have used the same settings in Thunder bird as I used in the failed netcat.

Thunderbird Outgoing Server (SMPT) settings:
Servername: mail.mydomail.com
Port: 25
Username: me
Use secure connection: None

Result: Hangs as dit the remote 
$ netcat mail.mydomain.com 25

---

### Post by gombadi on 2009-04-17
> 
From a remote machine:
$ netcat mydomain.com 25
mydomain.com [xxx.xx.xxx.xxx] 25 (smtp) : Connection timed out

> 
Result: Hangs as dit the remote
$ netcat mail.mydomain.com 25 


Basic connectivity issue.

Things to check -
- Firewall somewhere dropping packets
- If mail.mydomain.com is on an adsl line then is the router configured to forward port 25 to the internal machine.
- DNS - How many times have I had connection issues only to find dns was sending me to the wrong machine. Is the dns for mail.mydomain.com pointing to the correct ip address.

---

### Post by botfish on 2009-04-17
mail.mydomain.com is on a virtual private server (VPS) I have just purchased.
Would my hosting company need to configure their router?
My first setup did have a problem with the DNS records ([http://my.ip.add.xxx](http://my.ip.add.xxx) worked but [http://mydomain.com](http://mydomain.com) name did not) but a call to support fixed that.

From my home computer I can netcat smtp.gmail.com 587 no problem
$ netcat smtp.gmail.com 587
220 mx.google.com ESMTP u8sm1933267tia.26


My DNS records:

Name	TTL	Type	Priority	Value
mail.mydomain.com.	3600	A	my.ip.add.xxx
mydomain.com.	3600	SOA		ns1.hostxxx.net.nz
mydomain.com.	3600	NS		ns1.hostxxx.net.nz.
mydomain.com.	3600	NS		ns2.hostxxx.net.nz.
mydomain.com.	3600	NS		ns3.hostxxx.net.nz.
ftp.mydomain.com.	3600	CNAME	mydomain.com.
[www.mydomain.com](www.mydomain.com).	3600	CNAME	mydomain.com.
mydomain.com.	3600	MX	10	mail.mydomain.com.
mydomain.com.	3600	A		my.ip.add.xxx

Thanks for your assistance.

---

### Post by gombadi on 2009-04-18
> 
I can send mail from gmail to [email]me@mydomain.com[/email] and download that mail using remote POP

> 
Thunderbird is on a remote computer. I have used the same settings in Thunder bird as I used in the failed netcat.


> 
From a remote machine:
$ netcat mydomain.com 25
mydomain.com [xxx.xx.xxx.xxx] 25 (smtp) : Connection timed out


From this I am guessing that some parts of the world (at least Gmail) can connect to the VPS on port 25 but the remote computer, where ever that is, can not.

I also guess that the remote machine has a GUI as it is running Thunderbird.

Is the remote computer on an adsl line? Some ISP's block access to external servers on port 25 to reduce spam - Is that the case here?

Can you connect from the remote computer to any system on port 25? Try you ISP, some other ISP, Gmail, any other system you can think of. That will give you an indication of what may be blocked from the remote computer.

---

### Post by botfish on 2009-04-18
My remote computer is permenatly connected to the internet so I guess it must be ADSL.

I'll contact my ISP and hosting company tomorrow and ask if are blocking port 25.

Thanks for your help.

---

### Post by rompstar on 2009-04-19
I am no pro, just seen postfix today, but I tried everything here and mail never went out, and I figured it out why, read this, apply it and then it worked for me atleast.. Still have lots of reading and learning to do:

In my example, I have a valid domain registered and pointing to my host for apache, but I do not have a valid MX entry in DNS and I do not run a DNS server, my domain register forwards traffic to a static IP address that I have.

Full document here:

[http://www.postfix.org/SOHO_README.html#fantasy](http://www.postfix.org/SOHO_README.html#fantasy)

Solution 1: Postfix version 2.2 and later

Postfix 2.2 uses the generic(5) address mapping to replace local fantasy email addresses by valid Internet addresses. This mapping happens ONLY when mail leaves the machine; not when you send mail between users on the same machine.

The following example presents additional configuration. You need to combine this with basic configuration information as discussed the first half of this document.

    1 /etc/postfix/main.cf:
    2     smtp_generic_maps = hash:/etc/postfix/generic
    3 
    4 /etc/postfix/generic:
    5     [email]his@localdomain.local[/email]             [email]hisaccount@hisisp.exampl[/email]e
    6     [email]her@localdomain.local[/email]             [email]heraccount@herisp.exampl[/email]e
    7     @localdomain.local                hisaccount+local@hisisp.example

When mail is sent to a remote host via SMTP:

    *

      Line 5 replaces [email]his@localdomain.local[/email] by his ISP mail address,
    *

      Line 6 replaces [email]her@localdomain.local[/email] by her ISP mail address, and
    *

      Line 7 replaces other local addresses by his ISP account, with an address extension of +local (this example assumes that the ISP supports "+" style address extensions).

Specify dbm instead of hash if your system uses dbm files instead of db files. To find out what lookup tables Postfix supports, use the command "postconf -m".

Execute the command "postmap /etc/postfix/generic" whenever you change the generic table.

---

### Post by rubal on 2011-09-26
Hi

I am trying to work with virtual mailboxes using postfix and mysql. i had followed the steps similar to

[http://workaround.org/ispmail/sarge](http://workaround.org/ispmail/sarge)

But after setting up all i am not able to send the mails to any outside domain. I can recieve mail from other domains and can send/recieve mail on my local domain only.when i try to send mail using telnet i get

mail from:<test@abc.com>
250 2.1.0 Ok
rcpt to:<xyz@gmail.com>
554 5.7.1 <xyz@gmail.com>: Relay access denied

Please help me to resolve the problem.

Thanks in advance
Rubal

---

