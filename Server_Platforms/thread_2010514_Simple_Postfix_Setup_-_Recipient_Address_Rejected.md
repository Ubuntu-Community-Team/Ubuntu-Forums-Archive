---
title: "Simple Postfix Setup - Recipient Address Rejected"
date: 2012-06-25
forum: Server Platforms
---

### Post by BLaZuRE on 2012-06-25
Alright, so I only got Postfix for a PHP contact form.  I only want it to send out mail to some external address (***foo@example.com***).  I have domain ***sub1.sub2.domain.com***.  I installed Postfix out of the repo, with minimal config changes.  I cannot get Postfix to send mail externally (though it succeeds for internal accounts, which is unnecessary).

The email simply bounces if I generate an email using PHP mail().  If I try to form my own in telnet, right after ***rcpt to: [EMAIL="foo@example.com"]foo@example.com[/EMAIL]***, I get a 
```
postfix/smtpd[31606]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 5.1.1 <foo@example.com>: Recipient address rejected: example.com; from=<root@localhost> to=<foo@example.com> proto=ESMTP helo=<localhost>

```What can the problem be?

My main.cf
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = sub1.sub2.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = sub1.sub2.domain.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error

```

---

### Post by volkswagner on 2012-06-26
You do have a simple config file.  It appears there are no restrictions on sending.

Check out this[ thread]("http://ubuntuforums.org/newreply.php?do=newreply&p=11877908").  You may want to comment out the two lines as did the original poster.


> **brunojcm said:**
> I got the same error several times, and I fixed it commenting the following lines:

#default_transport = error
#relay_transport = error

I was following the instructions here:

[http://serverfault.com/questions/119278/configure-postfix-to-send-relay-emails-gmail-smtp-gmail-com-via-port-587](http://serverfault.com/questions/119278/configure-postfix-to-send-relay-emails-gmail-smtp-gmail-com-via-port-587)

---

### Post by BLaZuRE on 2012-06-26
I did comment out those lines.  However, I now currently get my emails deferred when attempting to send (tried AOL, Gmail, and Yahoo).  Am I incorrectly sending emails, is my config incorrect, or does some type of spam-prevention stop me from sending?

```

Jun 26 14:33:00 sub1 postfix/smtp[12191]: 2DA06F88206A: to=<bar@gmail.com>, relay=none, delay=514, delays=409/0.01/105/0, dsn=4.4.1, status=deferred (connect to aspmx3.googlemail.com[74.125.127.27]:25: Connection timed out)

Jun 26 14:36:36 sub1 postfix/smtp[12225]: connect to mta7.am0.yahoodns.net[98.139.175.224]:25: Connection timed out

Jun 26 14:38:00 sub1 postfix/smtp[12225]: 22952F88208E: to=<foo@yahoo.com>, relay=none, delay=655, delays=550/0.01/105/0, dsn=4.4.1, status=deferred (connect to mta5.am0.yahoodns.net[67.195.168.230]:25: Connection timed out)


```

---

### Post by Vishal Agarwal on 2012-06-27
There should be some IP for your machine also.

> 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.1


Or some public IP

---

### Post by BLaZuRE on 2012-06-28
> **Vishal Agarwal said:**
> There should be some IP for your machine also.



Or some public IP

I added the forward-facing ip and nothing has changed after reload.

postconf -d output remains the same:
```
mynetworks = 127.0.0.0/8 10.x.x.x/23
```

---

### Post by BLaZuRE on 2012-06-29
Also, a **dig sub1.sub2.domain.com MX** returns:
```

; <<>> DiG 9.7.0-P1 <<>> sub1.sub2.domain.com MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4853
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;sub1.sub2.domain.com.    IN    MX

;; AUTHORITY SECTION:
sub2.domain.com.    600    IN    SOA    sub2.domain.com. sub5.domain.com. 2012062915 7200 600 1209600 600

;; Query time: 0 msec
;; SERVER: x.x.x.x#53(x.x.x.x)
;; WHEN: Fri Jun 29 16:35:00 2012
;; MSG SIZE  rcvd: 84


```**lsof -i** returns empty
**netstat -t -a | grep LISTEN** returns
```
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN   
```

---

### Post by BLaZuRE on 2012-07-09
Well, I still haven't found a reason for this.  Any ideas anyone?

---

### Post by SeijiSensei on 2012-07-10
Ask your ISP if they are blocking outbound port 25.

---

### Post by BLaZuRE on 2012-07-20
Thanks, that was it.  Port 25 was blocked by another server :).

---

