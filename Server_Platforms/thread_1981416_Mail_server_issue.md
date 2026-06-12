---
title: "Mail server issue"
date: 2012-05-16
forum: Server Platforms
---

### Post by rhb0js on 2012-05-16
Hi,

I'm a bit newbie to configuring servers and I have a problem with a mail server for a company.

I  followed the documentation to configure it. Features: Ubuntu 4.10.03  LTS, Postfix, Dovecot, ClamAV, SpamAssassin, Maildir and TLS with own  certificates. I tested it with telnet, nc, swaks, thunderbird.

My  ISP has provided me a public IP (with domain reverse) and a panel to  configure the domain (it has a place to put the MX record and I put my  FQDN on it mail.fiegp.com.ar) and I have to use their DNS servers to use  email.

My main.cf is the following:

[I]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_key_file = /etc/postfix/tls/mail.fiegp.com.ar.key
smtpd_tls_cert_file = /etc/postfix/tls/mail.fiegp.com.ar.cert
smtpd_tls_CAfile = /etc/postfix/tls/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_auth_enable = yes
smtpd_tls_auth_only = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_unauth_pipelining

smtpd_sender_restrictions = reject_non_fqdn_sender, reject_unknown_sender_domain
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes
disable_vrfy_command = yes

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.fiegp.com.ar
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.fiegp.com.ar, mercurio.example.org, localhost.example.org, localhost
relayhost = 
mailbox_command = 
home_mailbox = Maildir/
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
debug_peer_list = fiegp.com.ar
mynetworks = 127.0.0.0/8 190.189.88.0/24
[/I]
First,  I've tried making an own DNS caching server, then an authoritative  server but I've no idea if the configuration is necessary to send email,  apparently it is.

My /etc/bind/named.conf.local (disabled)

[I]//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "fiegp.com.ar" {
    type master;
    file "/etc/bind/db.fiegp.com.ar";
};

zone "88.189.190.in-addr.arpa" {
    type master;
    file "/etc/bind/db.190";
};
[/I]
My /etc/bind/named.conf.options (disabled)

[I]options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    forwarders {
    24.232.0.17;
    24.232.0.18;
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
[/I]
My /etc/hosts (if necessary)

[I]127.0.0.1    localhost
190.189.88.168  mercurio mail.fiegp.com.ar

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

[/I]I made many tests and frankly I can not find where is the error. /var/log/mail.log show me the following caution:

[I]warning: no MX host for fiegp.com.ar has a valid address record
0D8646C03F7: to=<castor@fiegp.com.ar>, relay=none, delay=0.07,  delays=0.04/0/0.02/0, dsn=5.4.4, status=bounced (Host or domain name not  found. Name service error for name=mail.fiegp.com.ar type=A:Host not  found)
0D8646C03F7:removed[/I]

Please help!

---

### Post by darkod on 2012-05-16
In the ISP control panel, you created the MX record with the FQDN.

But did you create an A record specifying that this FQDN (something.domain.com) points to the public IP?

For mail, you basically need MX with the FQDN, and A record which tells to what IP this FQDN is equvalent.

I'm no expert in mail servers, but this could explain the error why it says there is no valid address. It needs to know the IP to find the server, otherwise the FQDN doesn't mean anything.

---

### Post by rhb0js on 2012-05-16
Thanks Darkod :)

I forgot post the zone files for the authoritative dns:

forward:
[I];
; BIND data file for local loopback interface
;
$TTL    86400
@    IN    SOA    ns.fiegp.com.ar. hermes.fiegp.com.ar. (
             2012051604        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.fiegp.com.ar.
;@    IN    A    127.0.0.1
;@    IN    AAAA    ::1
ns    IN    A    190.189.88.168
    IN    MX    10 mail.fiegp.com.ar.
mail    IN    A    190.189.88.168
smtp    IN    CNAME    mail
imap    IN    CNAME    mail
pop    IN    CNAME    mail
[/I]
reverse:
[I];
; BIND reverse data file for local loopback interface
;
$TTL    86400
@    IN    SOA    ns.fiegp.com.ar. hermes.fiegp.com.ar. (
        2012051602    ; Serial
        604800        ; Refresh
        86400        ; Retry
        2419200        ; Expire
        604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.
168    IN    PTR    ns.fiegp.com.ar.
168    IN    PTR    mail.fiegp.com.ar.[/I]

I just send an email to test the tls/sasl as follows:

[I]swaks -tls -a -au pollux -ap passwd2 -t [EMAIL="castor@fiegp.com.ar"]castor@fiegp.com.ar[/EMAIL] -f [EMAIL="pollux@fiegp.com.ar"]pollux@fiegp.com.ar[/EMAIL]
=== Trying mail.fiegp.com.ar:25...
=== Connected to mail.fiegp.com.ar.
<-  220 fiegp.com.ar ESMTP Postfix (Ubuntu)
 -> EHLO mercurio
<-  250-fiegp.com.ar
<-  250-PIPELINING
<-  250-SIZE 10240000
<-  250-ETRN
<-  250-STARTTLS
<-  250-ENHANCEDSTATUSCODES
<-  250-8BITMIME
<-  250 DSN
 -> STARTTLS
<-  220 2.0.0 Ready to start TLS
=== TLS started w/ cipher DHE-RSA-AES256-SHA
 ~> EHLO mercurio
<~  250-fiegp.com.ar
<~  250-PIPELINING
<~  250-SIZE 10240000
<~  250-ETRN
<~  250-AUTH PLAIN LOGIN
<~  250-ENHANCEDSTATUSCODES
<~  250-8BITMIME
<~  250 DSN
 ~> AUTH LOGIN
<~  334 VXNlcm5hbWU6
 ~> cG9sbHV4
<~  334 UGFzc3dvcmQ6
 ~> cGFzc3dkMg==
<~  235 2.7.0 Authentication successful
 ~> MAIL FROM:<pollux@fiegp.com.ar>
<~  250 2.1.0 Ok
 ~> RCPT TO:<castor@fiegp.com.ar>
<~  250 2.1.5 Ok
 ~> DATA
<~  354 End data with <CR><LF>.<CR><LF>
 ~> Date: Wed, 16 May 2012 23:25:08 -0300
 ~> To: [EMAIL="castor@fiegp.com.ar"]castor@fiegp.com.ar[/EMAIL]
 ~> From: [EMAIL="pollux@fiegp.com.ar"]pollux@fiegp.com.ar[/EMAIL]
 ~> Subject: test Wed, 16 May 2012 23:25:08 -0300
 ~> X-Mailer: swaks v20061116.0 jetmore.org/john/code/#swaks
 ~> 
 ~> This is a test mailing
 ~> 
 ~> .
<~  250 2.0.0 Ok: queued as 48DE86C0411
 ~> QUIT
<~  221 2.0.0 Bye
=== Connection closed with remote host.
[/I]
and mail.log show the following:

[I]May 16 23:25:17 mercurio spamd[890]: spamd: clean message (-1.0/5.0) for mail:8 in 9.1 seconds, 539 bytes.
May 16 23:25:17 mercurio spamd[890]: spamd: result: . -1 - ALL_TRUSTED scantime=9.1,size=539,user=mail,uid=8,required_score=5.0,rhost=localhost,raddr=127.0.0.1,rport=53090,mid=<20120517022508.48DE86C0411@fiegp.com.ar>,autolearn=ham
May 16 23:25:17 mercurio spamd[888]: prefork: child states: II
May 16 23:25:17 mercurio postfix/pickup[9479]: 82F386C0787: uid=8 from=<pollux@fiegp.com.ar>
May 16 23:25:17 mercurio postfix/cleanup[11200]: 82F386C0787: message-id=<20120517022508.48DE86C0411@fiegp.com.ar>
May 16 23:25:17 mercurio postfix/pipe[11201]: 48DE86C0411: to=<castor@fiegp.com.ar>, relay=spamassassin, delay=9.2, delays=0.06/0.01/0/9.2, dsn=2.0.0, status=sent (delivered via spamassassin service)
May 16 23:25:17 mercurio postfix/qmgr[9480]: 48DE86C0411: removed
May 16 23:25:17 mercurio postfix/qmgr[9480]: 82F386C0787: from=<pollux@fiegp.com.ar>, size=853, nrcpt=1 (queue active)
May 16 23:25:17 mercurio postfix/local[11205]: 82F386C0787: to=<castor@fiegp.com.ar>, relay=local, delay=0.17, delays=0.09/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
May 16 23:25:17 mercurio postfix/qmgr[9480]: 82F386C0787: removed
[/I]
so the problem now is when I try to configure thunderbird, log show me the following:

[I]May 16 23:28:42 mercurio postfix/smtpd[11207]: warning: 190.55.1.205: hostname cpe-190-55-1-205.telecentro-reversos.com.ar verification failed: Name or service not known
May 16 23:28:42 mercurio postfix/smtpd[11207]: connect from unknown[190.55.1.205]
May 16 23:28:42 mercurio postfix/smtpd[11209]: warning: 190.55.1.205: hostname cpe-190-55-1-205.telecentro-reversos.com.ar verification failed: Name or service not known
May 16 23:28:42 mercurio postfix/smtpd[11209]: connect from unknown[190.55.1.205]
May 16 23:28:42 mercurio postfix/smtpd[11207]: lost connection after CONNECT from unknown[190.55.1.205]
May 16 23:28:42 mercurio postfix/smtpd[11207]: disconnect from unknown[190.55.1.205]
May 16 23:28:42 mercurio postfix/smtpd[11209]: lost connection after CONNECT from unknown[190.55.1.205]
May 16 23:28:42 mercurio postfix/smtpd[11209]: disconnect from unknown[190.55.1.205][/I]

I think that is closer...

---

### Post by darkod on 2012-05-17
Is there a specific reason you want it to be a DNS server too? Why don't you leave the ISP to handle the DNS?

Much simpler that way, unless I've got it wrong.

---

### Post by rhb0js on 2012-05-17
As I told you, I did only follow some guides and later the official documentation. But as you suggest, It's correct, the DNS is no necessary, then I put it down and my /etc/resolv.conf is as follows:

[I]nameserver 24.232.0.17
nameserver 24.232.0.18
search fiegp.com.ar[/I]

and the /etc/hosts:

[I]127.0.0.1 localhost
190.189.88.168 mercurio mail.fiegp.com.ar[/I]

the MX record in the ISP panel is mail.fiegp.com.ar and the test with swaks still work, so apparently everything works, but when I try connect with the email client, can't find the server, syslog show the following:

[I]mercurio postfix/smtpd[14295]: warning: 190.189.107.146: hostname 146-107-189-190.cab.prima.net.ar verification failed: Name or service not known
mercurio postfix/smtpd[14295]: connect from unknown[190.189.107.146]
mercurio postfix/smtpd[14297]: warning: 190.189.107.146: hostname 146-107-189-190.cab.prima.net.ar verification failed: Name or service not known
mercurio postfix/smtpd[14297]: connect from unknown[190.189.107.146]
mercurio postfix/smtpd[14297]: improper command pipelining after EHLO from unknown[190.189.107.146]
mercurio postfix/smtpd[14295]: disconnect from unknown[190.189.107.146]
mercurio postfix/smtpd[14297]: disconnect from unknown[190.189.107.146][/I]

Just for tests, I add 190.189.107.0 to '*mynetworks*' in the main.cf but still can't find the server :(

---

### Post by darkod on 2012-05-17
Hold on, did you create A record for mail in your ISP control panel?

You don't need to put mail.fiegp.com.ar in your /etc/hosts file. It needs to work for the whole world anyway, not just for the server. The /etc/hosts file is local and that record will be known to that machine only.

I would suggest to delete that line from /etc/hosts.

Then login in your ISP control panel in the domain manager, and create A record mail pointing to 190.189.88.168.

That's how it will know how to find mail.fiegp.com.ar because the DNS of your ISP will point it to it.

As for the email client, I guess you are trying that on another machine, not the server. And the above could be the reason why it doesn't work. You need to configure it on the ISP control panel, not in the local hosts file on every machine.

From the machine of the email client, what happens if you ping mail.fiegp.com.ar? That will show you if it is resolved correctly as 190.189.88.168 or not. If it's not, go back to the discussion above.

If the machine can't reach mail.fiegp.com.ar correctly, of course the email client will not be able to find your server at all.

PS. And what is 190.189.107.146 from the above error messages? Does that IP mean anything to you?

---

### Post by rhb0js on 2012-05-17
You're in totally right darkod!

The panel of my ISP show the following:

Domain: fiegp.com.ar [blocked]
Email destiny: Other [combo with this only useful option for me]
MX: mail.fiegp.com.ar [text, can change]
Direct destiny: Other [like the above combo]
IP: 190.189.88.168 [text, can change]

and the new A record now point to the IP 190.189.88.168, there was another A record point to other ip. By the way, with the modification in /etc/hosts the test with swaks send the email in loop. I think that's no problem.

Now with these changes, the ping from the client machine to mail.fiegp.com.ar is sucessful! resolves well :) 

Of course, I did tried to do the tests from another net, and the 190.188.107.146 sure is the gateway for that machine. But now I need to do the configuration in a client to show company people that it works. Unfortunately it does not work at this moment for ISP configuration issues.

Thanks a lot in advance for your help :)

---

### Post by rhb0js on 2012-05-17
It works!

There is a little issue with my own certificates but I'll solve it with the installation on the clients.

Thank you so much darkod :D you're the man!!

Cheers!

---

### Post by darkod on 2012-05-17
No problem, glad I could help even though I am not a server expert.

Please mark the thread Solved, you can do that in Thread Tools above the first post.

---

