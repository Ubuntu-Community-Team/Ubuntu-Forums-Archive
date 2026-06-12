---
title: "External clients and postfix - very annoying problem"
date: 2009-12-17
forum: Server Platforms
---

### Post by keyslapper on 2009-12-17
Hello everyone,

Let me try to be as concise as possible here:

**What *does* work:**
Incoming mail to my users is handled properly
Reading IMAP mail, either through Squirrelmail or an external client works
Sending mail out through Squirrelmail works

Note that Courier-IMAP is configured to authenticate through the MySQL DB, as is Apache for some directories.

**What does *not* work:**
Sending email through external clients times out on the connection attempt.  This is configured (badly, it would seem) to authenticate to the same mysql database as Courier and Apache via saslauthd and the pam_mysql plugin.

Note that I did have this working at one time.  Unfortunately, an upgrade made it go wrong, and since I couldn't see the problem (I seem to have been kept in the cache longer than any of the other users) I've been sitting on this for some time.

Here's my main.cf:
```

soft_bounce = no
biff = yesappend_dot_mydomain = yes
readme_directory = /usr/share/doc/postfix
data_directory = /var/lib/postfix
mydomain = domain1.net
myhostname = domain1.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain1.net, domain2.net,
                     domain1.com, domain2.com,
                     domain1.org
content_filter=smtp-amavis:[127.0.0.1]:10024  
local_recipient_maps = unix:passwd.byname $alias_maps
relay_domains = $mydestination                
relayhost = 
mynetworks_style = subnet
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 1000000000
recipient_delimiter = +
inet_interfaces = all
unknown_local_recipient_reject_code = 550                                       
unknown_address_reject_code = 554
unknown_hostname_reject_code = 554                                              
unknown_client_reject_code = 554
home_mailbox = .Maildir/
disable_vrfy_command = yes                   
strict_rfc821_envelopes = yes
mailbox_command = /usr/bin/procmail -a "$EXTENSION"
header_checks = regexp:/etc/postfix/header_checks
smtpd_helo_required = yes
smtpd_sender_restrictions =    permit_mynetworks,
                                             permit_sasl_authenticated
smtpd_recipient_restrictions =  permit_mynetworks,
                                              permit_sasl_authenticated,
                                             reject_unauth_destination,
                                             reject_non_fqdn_sender,
                                             reject_non_fqdn_recipient
tls_random_source = dev:/dev/urandom                 
smtpd_use_tls=yes
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_key_file = /etc/ssl/courier-imap/cert.net.key
smtpd_tls_cert_file = /etc/ssl/courier-imap/cert.net.crt
smtpd_tls_CAfile = /etc/ssl/courier-imap/cert.crt
smtpd_tls_loglevel = 3
smtp_use_tls = yes
smtp_tls_loglevel = 3
smtp_tls_note_starttls_offer = yes
smtpd_sasl_type = cyrus
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
html_directory = /usr/share/doc/postfix/html

```And /etc/postfix/sasl/smtpd.conf:
```

pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: mailuser
sql_passwd: mypasswd
sql_database: passwords
sql_select: select clear from passwd where id = '%u'

```Note that this is a sym link to /usr/lib/sasl2/smtpd.conf

I know the relayhost is empty.  This is intentional, and does not seem to be causing issues with mail sent via Squirrelmail.

The problem is that when trying to connect to postfix with a mail client like Thunderbird, Apple Mail, Outlook, etc. the connection times out.  Same with telnetting in to port 25.  I have verified that port 25 is open in the firewall and that the port is listening.  When trying to connect, I can even see the SYN_RECV state on the server, but *nothing whatsoever* shows in any of the logfiles.

I've followed every bloody tutorial I could find, going back to 2002.  Nothing seems to help.  This configuration is based on one written by falko on HowTo.net ( [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10) )

I am reasonably certain I do have TLS support in postfix:

```

# /etc/postfix# ldd /usr/lib/postfix/master
        linux-vdso.so.1 =>  (0x00007fff125ff000)
        libpostfix-global.so.1 => /usr/lib/libpostfix-global.so.1 (0x00007f34318ac000)
        libpostfix-util.so.1 => /usr/lib/libpostfix-util.so.1 (0x00007f3431677000)
        libssl.so.0.9.8 => /lib/libssl.so.0.9.8 (0x00007f3431429000)
        libcrypto.so.0.9.8 => /lib/libcrypto.so.0.9.8 (0x00007f34310a2000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00007f3430e88000)
        libdb-4.7.so => /usr/lib/libdb-4.7.so (0x00007f3430b26000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x00007f343090c000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x00007f34306f3000)
        libc.so.6 => /lib/libc.so.6 (0x00007f3430384000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007f3430180000)
        libz.so.1 => /lib/libz.so.1 (0x00007f342ff69000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007f342fd4d000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f3431ae5000)

```My frustration level at this is reaching its peak.  :confused:  Any suggestions that might resolve this would be greatly appreciated.

Thanks in advance.
Lou

---

### Post by oneloveamaru on 2009-12-17
If it was working before an upgrade, look at your old configs and see what is different and/or downgrade to the old version. If it isn't the configs, the new version may have some syntax that changed. I would roll back to begin with. Hopefully you have backups of all of these files in question....

---

### Post by keyslapper on 2009-12-17
> **oneloveamaru said:**
> ... Hopefully you have backups of all of these files in question....

Wouldn't you know it ... I don't.  

Actually, I don't think it was an update.  Of course, I can't say for sure.  Like I said, it was working fine for me, so I was fixated on a config issue for the one user that experienced the issue first.  For over a month it was just one user.  Then another.  Another month or two and it finally hit me too.

As soon as it hit the second user, I started trying to find the problem, but I didn't really change anything in the configs until just recently when I started searching out the updated how-to pages online.  Didn't see much sense in saving a config I knew was broken.

Thank you for the suggestion.

---

### Post by TheFuturian on 2009-12-17
Is it anything to do with your "MyNetworks" option within '/etc/postfix/main.cf'?

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

```

I think I had to add in external network ranges to allow the ability to relay mail messages through from external locations.. i.e.:-

```
mynetworks = 127.0.0.0/8, 81.100.0.0/16, 81.101.0.0/16, 192.168.1.0/24
```

I think the easiest way to find out what is going on is to tail the mail log whilst a transmission attempt is made..

```
tail -f /var/log/mail.log
```

---

### Post by keyslapper on 2009-12-17
> **TheFuturian said:**
> Is it anything to do with your "MyNetworks" option within '/etc/postfix/main.cf'?

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```I think I had to add in external network ranges to allow the ability to relay mail messages through from external locations.. i.e.:-


I wouldn't think so.  This should only refer to trustable networks, and from this host, the localhost is the only such host.  The values I have are the IPv4 and IPv6 localhost addresses.  This is why I have:
```
smtpd_sender_restrictions =    permit_mynetworks,
                               permit_sasl_authenticated
```> 
```
mynetworks = 127.0.0.0/8, 81.100.0.0/16, 81.101.0.0/16, 192.168.1.0/24
```This would be fine if you have full control of the subnets specified, and if you don't have to relay mail from anywhere else.  I only have a few users, but they are spread quite far and wide.  It would be impossible to add every network my brother connects from, since he connects from hundreds of different locations when he travels.

> 
I think the easiest way to find out what is going on is to tail the mail log whilst a transmission attempt is made..
```
tail -f /var/log/mail.log
```Thought of that.  Like I said, nothing whatsoever in the logs.  The SYN_RECV is the only sign that anything is happening.

Thank you for the suggestion

---

### Post by keyslapper on 2009-12-18
Problem solved!

Turns out port 25 was being blocked by my ISP.  I had gotten into the habit of using webmail when I changed my home ISP and didn't notice the problem until I was past the association.  My other users didn't notice it at the same time because my brother was traveling and connecting through hotspots that were not blocking that port.

The fix was to uncomment the submission configuration in master.cf and open port 587 in the firewall.

Other things I had to remember:
* Open the submission port in the firewall. 
* Update the Squirrelmail configuration to use the correct port. 
* Set the -o smtpd_tls_security_level=may in the master.cf submission config to allow Squirrelmail to connect without TLS, as well as external clients that may not be able to use it. 
* Add the following to the master.cf submission: 
   -o mynetworks=127.0.0.0/8 
* And change the smtpd_client_restrictions setting to include mynetworks. 
 
Without these changes, I'd have had to jump through hoops to get Squirrelmail to go through the SMTP authentication as well as the IMAP authentication. Didn't seem worthwhile. 
 
So, now I'm on to the next problem. It seems the postfix - sasl - pam - mysql authentication chain is not quite right. But at least I'm actually getting useful information there.

I hope this helps someone else avoid the frustration I went through.

---

