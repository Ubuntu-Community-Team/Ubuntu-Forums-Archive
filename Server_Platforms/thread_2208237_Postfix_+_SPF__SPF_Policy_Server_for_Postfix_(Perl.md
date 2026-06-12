---
title: "Postfix + SPF : SPF Policy Server for Postfix (Perl implementation)"
date: 2014-02-27
forum: Server Platforms
---

### Post by snikende-kanelboll on 2014-02-27
Hi,


i tryed following this guide but i can't for the life of me figure out why it does not work.
[https://help.ubuntu.com/community/Postfix/SPF](https://help.ubuntu.com/community/Postfix/SPF)


Log does not show any SPF messages or checks.


Same thing with this guide:
[http://www.howtoforge.com/postfix_spf](http://www.howtoforge.com/postfix_spf)


The perl skript is working.
I started this manually: policyd-spf-perl


Used the commands that the last guide shows:


    request=smtpd_access_policy
    protocol_state=RCPT
    protocol_name=SMTP
    helo_name=h****forge.com
    queue_id=8045F2AB23
    sender=
    recipient=falko.timme@*******.de
    client_address=81.169.1**.**
    client_name=h****.server*********.net
    [empty line]


and this showed in the logg.




Im guessing there is a problem with the implementation in to Postfix.
My config is here:






Master.cf:


```
    #
    # Postfix master process configuration file.  For details on the format
    # of the file, see the master(5) manual page (command: "man 5 master").
    #
    # Do not forget to execute "postfix reload" after editing this file.
    #
    # ==========================================================================
    # service type  private unpriv  chroot  wakeup  maxproc command + args
    #               (yes)   (yes)   (yes)   (never) (100)
    # ==========================================================================
    smtp      inet  n       -       -       -       -       smtpd
      -o smtpd_tls_security_level=may
      -o smtpd_sasl_auth_enable=yes
      -o smtpd_tls_auth_only=no
      -o smtpd_sasl_type=dovecot
      -o smtpd_sasl_path=private/auth
    
      -o smtpd_sasl_auth_enable=yes
      -o s mtpd_recipient_restrictions=permit_mynetworks,permit_sasl_authenticated,
    reject_unauth_destination
    
      -o smtpd_sasl_security_options=noanonymous
    
    
    
    
    #Kunder utfor nettet vart kan sende e-post
    587     inet    n   -   n   -   -   smtpd
    
    pickup    fifo  n       -       -       60      1       pickup
    cleanup   unix  n       -       -       -       0       cleanup
    qmgr      fifo  n       -       n       300     1       qmgr
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
    # When relaying mail as backup MX, disable fallback_relay
    # to avoid MX loops
    relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=


    showq     unix  n       -       -       -       -       showq
    error     unix  -       -       -       -       -       error
    retry     unix  -       -       -       -       -       error
    discard   unix  -       -       -       -       -       discard
    local     unix  -       n       n       -       -       local
    virtual   unix  -       n       n       -       -       virtual
    lmtp      unix  -       -       -       -       -       lmtp
    anvil     unix  -       -       -       -       1       anvil
    scache    unix  -       -       -       -       1       scache


    # maildrop. See the Postfix MAILDROP_README file for details.
    # Also specify in main.cf: maildrop_destination_recipient_limit=1
    #
    maildrop  unix  -       n       n       -       -       pipe
        flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}


    uucp      unix  -       n       n       -       -       pipe
    flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
    #
    # Other external delivery methods.
    #
    ifmail    unix  -       n       n       -       -       pipe
    flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
    bsmtp     unix  -       n       n       -       -       pipe
       flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
    scalemail-backend unix  -       n       n       -       2       pipe
       flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store
     ${nexthop}    ${user} ${extension}


    mailman   unix  -       n       n       -       -       pipe
    flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
    ${nexthop} ${user}


    submission inet n - - - - smtpd
    -o smtpd_tls_security_level=may
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_tls_auth_only=no
    -o smtpd_sasl_type=dovecot
    -o smtpd_sasl_path=private/auth


    -o smtpd_sasl_auth_enable=yes
    -o    smtpd_recipient_restrictions=permit_mynetworks,permit_sasl_authenticated,
    reject_unauth_destination


    -o smtpd_sasl_security_options=noanonymous
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    -o smtpd_recipient_restrictions=reject_unknown_recipient_domain,
    reject_non_fqdn_recipient,permit_sasl_authenticated,reject








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
        -o content_filter=
        -o receive_override_options=no_header_body_checks




    spfcheck  unix  -       n       n       -       0       spawn
                   user=policyd-spf argv=/usr/sbin/postfix-policyd-spf-perl



```

Main.cf


```
        
        queue_directory = /var/spool/postfix
    command_directory = /usr/sbin
    daemon_directory = /usr/lib/postfix
    
    
    myhostname = (removed)
    mydomain = (removed)
    myorigin = /etc/mailname
    
    inet_interfaces = all
    inet_protocols = ipv4
    
    mydestination = $myhostname, localhost.localdomain, localhost
    
    unknown_local_recipient_reject_code = 550
    
    
    mynetworks =  127.0.0.0/8, etc......(removed)
    
    smtpd_banner = $myhostname ESMTP $mail_name
    
    
    # Ikke tillat Verify, siden det kan misbrukes av spammere
    disable_vrfy_command = yes
    
    mailbox_size_limit = 100000000
    message_size_limit = 35600000
    
    home_mailbox = Maildir/
    mailbox_command =
    
    transport_maps=mysql:/etc/postfix/mysql_transport_maps.cf
    
    setgid_group = postdrop
    mail_owner = postfix
    
    virtual_gid_maps = static:8
    virtual_minimum_uid = 500
    virtual_uid_maps = static:500
    
    virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
    virtual_mailbox_base = /var/spool/mail
    virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
    virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
    
    smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps.cf
    
        smtpd_sasl_type = dovecot
    smtpd_sasl_path = private/auth
    
    smtpd_sasl_local_domain =
    smtpd_sasl_auth_enable = yes
    smtpd_sasl_security_options = noanonymous
    broken_sasl_auth_clients = yes
    smtpd_tls_security_level = may
    smtpd_tls_auth_only = no
    smtpd_tls_key_file = /etc/ssl/private/smtpd.key
    smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
    smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
    smtpd_tls_loglevel = 1
    smtpd_tls_received_header = yes
    smtpd_tls_session_cache_timeout = 3600s
    tls_random_source = dev:/dev/urandom
    
    
    
    # SPF
    
    #policy-spf_time_limit=3600s
    spfcheck_time_limit = 3600
    
    
    smtpd_recipient_limit = 30
    
    smtpd_hard_error_limit = 100
    smtpd_soft_error_limit = 50
    smtpd_error_sleep_time = 30s
    
        # HELO
    
    smtpd_helo_required = yes
    
    strict_rfc821_envelopes = yes
    
    
    
    unknown_address_reject_code  = 554
    
    unknown_hostname_reject_code = 554
    
    unknown_client_reject_code   = 554
    
    
    # rate control
    anvil_rate_time_unit = 540s
    anvil_status_update_time = 600s
    
    smtpd_client_message_rate_limit = 30
    smtpd_client_connection_rate_limit = 10
    smtpd_client_event_limit_exceptions = etc. (removed)
    
        smtpd_recipient_restrictions =
     permit_mynetworks,
     permit_sasl_authenticated,
     reject_invalid_hostname,
     reject_unauth_pipelining,
     reject_non_fqdn_sender,
     reject_unknown_sender_domain,
     reject_non_fqdn_recipient,
     reject_unknown_recipient_domain,
     reject_unauth_destination,
     check_policy_service unix:private/spfcheck,
     reject_rhsbl_client blackhole.securitysage.com,
     reject_rhsbl_sender blackhole.securitysage.com,
     reject_rbl_client relays.ordb.org,
     reject_rbl_client blackholes.easynet.nl,
     reject_rbl_client cbl.abuseat.org,
     reject_rbl_client proxies.blackholes.wirehub.net,
     reject_rbl_client bl.spamcop.net,
     reject_rbl_client sbl.spamhaus.org,
     reject_rbl_client opm.blitzed.org,
     reject_rbl_client dnsbl.njabl.org,
     reject_rbl_client list.dsbl.org,
     reject_rbl_client multihop.dsbl.org,
     permit
    
    
    smtpd_sender_restrictions = permit_mynetworks, reject_sender_login_mismatch, reject_authenticated_sender_login_mismatch, reject_unauthenticated_sender_login_mismatch
    
        smtpd_sender_restrictions = permit_mynetworks, reject_sender_login_mismatch, reject_authenticated_sender_login_mismatch, reject_unauthenticated_sender_login_mismatch
    
    
    relayhost =
    
    
    #amavis
    content_filter = smtp-amavis:[127.0.0.1]:10024

```

---

