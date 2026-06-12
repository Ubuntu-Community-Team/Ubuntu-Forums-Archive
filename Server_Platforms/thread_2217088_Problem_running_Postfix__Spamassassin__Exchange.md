---
title: "Problem running Postfix / Spamassassin / Exchange"
date: 2014-04-15
forum: Server Platforms
---

### Post by David_Robinson on 2014-04-15
I am trying to setup a stand alone ubuntu server box with Postfix and SpamAssassin in front of our Exchange 2010 Server.  I'm getting this error = 

```
[COLOR=#393939][FONT=arial]Apr 15 16:56:39 SpamServ postfix/postqueue[2249]: warning: Mail system is down -- accessing queue directly[/FONT][/COLOR]
```

I have been looking in to the problem with no luck so far.  I would be very thankful for any help any one is able to give me.  Here are the config files I have at the moment.

**/etc/postfix/main.cf:**
```
mydomain = .mail.companydomain.co.uk  myhostname = localhost
mydestination = companydomain.co.uk, companydomain.com, companydomain2.co.uk, companydomain2.com
mynetworks = 192.168.2.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
relay_domains = $mydestination
smtpd_recipient_restrictions = permit_mynetworks,\
    reject_unauth_destination,reject_invalid_hostname,\
    reject_unauth_pipelining,reject_non_fqdn_sender, \
    reject_unknown_recipient_domain,reject_unknown_sender_domain
transport_maps = hash:/etc/postfix/transport
local_recipient_maps =content_filter = smtp-amavis:[127.0.0.1]:10024
```

[B]/etc/postfix/master.cf:
[/B]```
pickup    fifo  n       -       -       60      1       pickup         -o content_filter=
         -o receive_override_options=no_header_body_checks
smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20


127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
```
[B]/etc/postfix/transport:

[/B]```
companydomain.co.uk smtp:[192.168.2.101]
companydomain.com smtp:[192.168.2.101]
companydomain2.co.uk smtp:[192.168.2.101]
companydomain2.com smtp:[192.168.2.101]
```

[B]Here is the full log file:

[/B]```
Apr 15 16:47:58 SpamServ amavis[979]: Perl version               5.014002
Apr 15 16:48:00 SpamServ amavis[1019]: Net::Server: Group Not Defined.  Defaulting to EGID '117 117'
Apr 15 16:48:00 SpamServ amavis[1019]: Net::Server: User Not Defined.  Defaulting to EUID '107'
Apr 15 16:48:00 SpamServ amavis[1019]: Module Amavis::Conf        2.208
Apr 15 16:48:00 SpamServ amavis[1019]: Module Archive::Zip        1.30
Apr 15 16:48:00 SpamServ amavis[1019]: Module BerkeleyDB          0.49
Apr 15 16:48:00 SpamServ amavis[1019]: Module Compress::Zlib      2.064
Apr 15 16:48:00 SpamServ amavis[1019]: Module Convert::TNEF       0.18
Apr 15 16:48:00 SpamServ amavis[1019]: Module Convert::UUlib      1.4
Apr 15 16:48:00 SpamServ amavis[1019]: Module Crypt::OpenSSL::RSA 0.28
Apr 15 16:48:00 SpamServ amavis[1019]: Module DB_File             1.821
Apr 15 16:48:00 SpamServ amavis[1019]: Module Digest::MD5         2.53
Apr 15 16:48:00 SpamServ amavis[1019]: Module Digest::SHA         5.61
Apr 15 16:48:00 SpamServ amavis[1019]: Module IO::Socket::INET6   2.72
Apr 15 16:48:00 SpamServ amavis[1019]: Module MIME::Entity        5.505
Apr 15 16:48:00 SpamServ amavis[1019]: Module MIME::Parser        5.505
Apr 15 16:48:00 SpamServ amavis[1019]: Module MIME::Tools         5.505
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::DKIM::Signer  0.4
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::DKIM::Verifier 0.4
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::Header        2.08
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::Internet      2.08
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::SPF           v2.009
Apr 15 16:48:00 SpamServ amavis[1019]: Module Mail::SpamAssassin  3.003002
Apr 15 16:48:00 SpamServ amavis[1019]: Module Net::DNS            0.74
Apr 15 16:48:00 SpamServ amavis[1019]: Module Net::Server         0.99
Apr 15 16:48:00 SpamServ amavis[1019]: Module NetAddr::IP         4.072
Apr 15 16:48:00 SpamServ amavis[1019]: Module Razor2::Client::Version 2.84
Apr 15 16:48:00 SpamServ amavis[1019]: Module Socket6             0.25
Apr 15 16:48:00 SpamServ amavis[1019]: Module Time::HiRes         1.9726
Apr 15 16:48:00 SpamServ amavis[1019]: Module URI                 1.59
Apr 15 16:48:00 SpamServ amavis[1019]: Module Unix::Syslog        1.1
Apr 15 16:48:00 SpamServ amavis[1019]: Amavis::DB code      loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Amavis::Cache code   loaded
Apr 15 16:48:00 SpamServ amavis[1019]: SQL base code        NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: SQL::Log code        NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: SQL::Quarantine      NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Lookup::SQL code     NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Lookup::LDAP code    NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: AM.PDP-in proto code loaded
Apr 15 16:48:00 SpamServ amavis[1019]: SMTP-in proto code   loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Courier proto code   NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: SMTP-out proto code  loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Pipe-out proto code  NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: BSMTP-out proto code NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Local-out proto code loaded
Apr 15 16:48:00 SpamServ amavis[1019]: OS_Fingerprint code  NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: ANTI-VIRUS code      loaded
Apr 15 16:48:00 SpamServ amavis[1019]: ANTI-SPAM code       loaded
Apr 15 16:48:00 SpamServ amavis[1019]: ANTI-SPAM-EXT code   NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: ANTI-SPAM-C code     NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: ANTI-SPAM-SA code    loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Unpackers code       loaded
Apr 15 16:48:00 SpamServ amavis[1019]: DKIM code            loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Tools code           NOT loaded
Apr 15 16:48:00 SpamServ amavis[1019]: Found $file            at /usr/bin/file
Apr 15 16:48:00 SpamServ amavis[1019]: No $altermime,         not using it
Apr 15 16:48:00 SpamServ amavis[1019]: Internal decoder for .mail
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .F   
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .Z    at /bin/uncompress
Apr 15 16:48:00 SpamServ amavis[1019]: Internal decoder for .gz  
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .bz2  at /bin/bzip2 -d
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .lzo  tried: lzop -d
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .rpm  tried: rpm2cpio.pl, rpm2cpio
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .cpio at /bin/pax
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .tar  at /bin/pax
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .deb  at /usr/bin/ar
Apr 15 16:48:00 SpamServ amavis[1019]: Internal decoder for .zip 
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .7z   tried: 7zr, 7za, 7z
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .rar  tried: unrar-free
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .arj  at /usr/bin/arj
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .arc  at /usr/bin/nomarch
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .zoo  tried: zoo
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .lha 
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .doc  tried: ripole
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .cab  at /usr/bin/cabextract
Apr 15 16:48:00 SpamServ amavis[1019]: No decoder for       .tnef
Apr 15 16:48:00 SpamServ amavis[1019]: Internal decoder for .tnef
Apr 15 16:48:00 SpamServ amavis[1019]: Found decoder for    .exe  at /usr/bin/arj
Apr 15 16:48:00 SpamServ amavis[1019]: Using primary internal av scanner code for ClamAV-clamd
Apr 15 16:48:00 SpamServ amavis[1019]: Found secondary av scanner ClamAV-clamscan at /usr/bin/clamscan
Apr 15 16:48:00 SpamServ amavis[1019]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.49, libdb 5.1
Apr 15 16:48:27 SpamServ postfix/master[1571]: daemon started -- version 2.9.6, configuration /etc/postfix
Apr 15 16:56:34 SpamServ postfix/postqueue[2132]: warning: Mail system is down -- accessing queue directly
Apr 15 16:56:37 SpamServ postfix/postqueue[2143]: warning: Mail system is down -- accessing queue directly
Apr 15 16:56:39 SpamServ postfix/postqueue[2249]: warning: Mail system is down -- accessing queue directly 
```[COLOR=#222222][FONT=Verdana]

Thanks again for any help![/FONT][/COLOR]

---

