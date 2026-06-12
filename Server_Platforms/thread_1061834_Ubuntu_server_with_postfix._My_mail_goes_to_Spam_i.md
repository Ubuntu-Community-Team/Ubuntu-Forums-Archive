---
title: "Ubuntu server with postfix. My mail goes to Spam in Gmail and Yahoo Mail. Ideeas?"
date: 2009-02-06
forum: Server Platforms
---

### Post by trileru808 on 2009-02-06
Hello guys! I would like to thank you in advance for your help. I am really stuck here and have a deadly deadline  I have to take over the mail from my company (they have a contract atm with another company for mail services) and I am stuck. I have a Dell R300 server witch has Ubuntu Server installed. I also added Postfix for mail, configured it, everything runs smooth but!...all of my mail ends up in Spam at gmail and yahoo.

Let's say my domain is "mydomain.com" and my ip is 89.xxx.yyy.zzz 

I shall put here all the config maybe you can help me.

First of all...i talked to my ISP and had them put reverse dns on mydomain.com. I checked it with some utilities and it really shows mydomain.com.

Now with my config:

postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 102400000
mydestination = /etc/postfix/local-host-names
mydomain = mydomain.com
myhostname = mail. mydomain.com
mynetworks = 89.xxx.yyy.0/30, 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

cat /etc/postfix/local-host-names

###################################
#
# ISPConfig local-host-names Configuration File
# Version 1.0
#
###################################
localhost
server1
localhost.server1
localhost.localdomain
[www.mydomain.com](www.mydomain.com)
webmail.mydomain.com
mydomain.com
#### MAKE MANUAL ENTRIES BELOW THIS LINE! ####

cat /etc/hosts
127.0.0.1 localhost
89.xxx.yyy.zzz server1

cat /etc/resolv.conf
search mydomain.com
nameserver 89.xxx.yyy.zzz


dig mydomain.com

; <<>> DiG 9.5.0-P2 <<>> mydomain.com
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58678
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;mydomain.com. IN A

;; ANSWER SECTION:
mydomain.com. 86400 IN A 89.xxx.yyy.zzz

;; AUTHORITY SECTION:
mydomain.com. 86400 IN NS ns1.mydomain.com.
mydomain.com. 86400 IN NS ns2.mydomain.com.

;; Query time: 0 msec
;; SERVER: 89.xxx.yyy.zzz#53(89.xxx.yyy.zzz)
;; WHEN: Fri Feb 6 13:57:06 2009
;; MSG SIZE rcvd: 83


nslookup 89.xxx.yyy.zzz
Server: 89.xxx.yyy.zzz
Address: 89.xxx.yyy.zzz#53

Non-authoritative answer:
zzz.yyy.xxx.89.in-addr.arpa name = mydomain.com.


cat /etc/bind/named.conf
options {
pid-file "/var/run/bind/run/named.pid";
directory "/etc/bind";
auth-nxdomain no;
/*
* If there is a firewall between you and nameservers you want
* to talk to, you might need to uncomment the query-source
* directive below. Previous versions of BIND always asked
* questions using port 53, but BIND 8.1 uses an unprivileged
* port by default.
*/
// query-source address * port 53;
};

//
// a caching only nameserver config
//
zone "." {
type hint;
file "db.root";
};

zone "0.0.127.in-addr.arpa" {
type master;
file "db.local";
};


zone "mydomain.com" {
type master;
file "pri. mydomain.com";
};

//// MAKE MANUAL ENTRIES BELOW THIS LINE! ////

zone "zzz.yyy.xxx.89.in-addr.arpa" {
type master;
file "rev.yyy.xxx.89.in-addr.arpa";
};


cat /etc/bind/rev.yyy.xxx.89.in-addr.arpa

@ IN SOA ns1.mydomain.com. [www.mydomain.com](www.mydomain.com). (
2006081401;
28800;
604800;
604800;
86400 )


IN NS ns1.mydomain.com.
zzz IN PTR mydomain.com.



cat /etc/bind/pri.mydomain.com

$TTL 86400
@ IN SOA ns1. mydomain.com. xxx.gmail.com. (
2009013002 ; serial, todays date + todays serial #
28800 ; refresh, seconds
7200 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;
NS ns1. mydomain.com. ; Inet Address of name server 1
NS ns2. mydomain.com. ; Inet Address of name server 2
;

MX 10 mail. mydomain.com.

mydomain.com. A 89.xxx.yyy.zzz
www CNAME mydomain.com.
webmail CNAME mydomain.com.
mail CNAME mydomain.com.
ns1 CNAME mydomain.com.
ns2 CNAME mydomain.com.
ftp CNAME mydomain.com.





;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;

---

### Post by dro0g on 2009-02-06
The metrics used by all the free mail providers are something of a blackbox - they don't really provide any sort of decent way of determining why particular messages are being filtered. That having been said, here's a couple other things to try:

You've got a PTR which is good but you may be running into some issues because it doesn't point back to the host name of the sending server. I would change the PTR to point to mail.mydomain.com. You might consider setting mail.mydomain.com as an A record instead of a CNAME, but I don't know if that's really an issue.

I would also create an SPF record for the domain:
[http://old.openspf.org/wizard.html](http://old.openspf.org/wizard.html)

Next, do some checking on the IP and domain. the dnsstuff.com site used to be awesome for this but they're a pay site now. Still you can do some lookups to verify that the IP isn't on an RBL and isn't in a dial-up netblock (If it's in a dial-up netblock you'll have to relay mail through the ISPs mailserver to not get it filtered all over the place) Another good place to lookup information on the IP and domain is [http://www.senderbase.org/](http://www.senderbase.org/) - this is the rating service used by Ironport spam filters.

Good luck!

---

### Post by hyper_ch on 2009-02-06
do you have a static ip?

---

### Post by trileru808 on 2009-02-06
> **hyper_ch said:**
> do you have a static ip?


Yes, I do have a static IP. I just pointed PTR to mail.mydomain.com changed mail to A record instead of CNAME and ill try to make a SPF record right now.

Thank you very much for your answers. I'll keep you posted if my problem is solved.
Have a nice day

---

### Post by trileru808 on 2009-02-07
Well....after i made a SPF record that looks like this: "mydomain.com. IN TXT "v=spf1 ip4:89.xxx.yyy.zzz a mx ~all" and after making an A record of mail.domain.com my mail goes to Inbox in Gmail but still in spam at Yahoo Mail. Should I buy a security certificate? Because it keeps asking me when I try to send mail. Maybe that should solve the problem?

Have a nice day

---

### Post by hyper_ch on 2009-02-07
can you post an email with full headers that gets marked as spam?

---

### Post by trileru808 on 2009-02-09
> **hyper_ch said:**
> can you post an email with full headers that gets marked as spam?


From My Name Sat Feb  7 01:16:43 2009
Return-Path: <office@mydomain.com>
Authentication-Results: mta373.mail.mud.yahoo.com  from=mydomain; domainkeys=neutral (no sig)
Received: from 89.xxx.yyy.zzz  (EHLO mail.mydomain.com) (89.xxx.yyy.zzz)
  by mta373.mail.mud.yahoo.com with SMTP; Sat, 07 Feb 2009 01:16:47 -0800
Received: from diversity (unknown [213.xxx.xxx.xxx])
	(using TLSv1 with cipher RC4-MD5 (128/128 bits))
	(No client certificate requested)
	(Authenticated sender: office)
	by mail.mydomain.com (Postfix) with ESMTPSA id 3F59C594056;
	Sat,  7 Feb 2009 11:16:40 +0200 (EET)
From: "My Name" <office@mydomain.com>
To: <someID@yahoo.com>
Cc: <someotherID@yahoo.com>,
	<someID@hotmail.com>
Subject: FW: this is a commercial offer
Date: Sat, 7 Feb 2009 11:16:43 +0200
Message-ID: <000501c98904$ce7ec9e0$6b7c5da0$@ro>
MIME-Version: 1.0
Content-Type: multipart/alternative;
	boundary="----=_NextPart_000_0006_01C98915.920799E0"
Thread-Index: AcmJA8F9vCLDlFAmSKm0kkDwcRsBaAAAPnBw
Content-Language: ro
Content-Length: 3205

---

