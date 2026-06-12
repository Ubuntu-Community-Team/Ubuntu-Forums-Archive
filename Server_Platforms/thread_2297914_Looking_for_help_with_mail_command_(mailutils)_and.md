---
title: "Looking for help with mail command (mailutils) and why two configs have dif results"
date: 2015-10-07
forum: Server Platforms
---

### Post by Boktai1000 on 2015-10-07
Hello,

I'm looking for assistance as to why two hosts that have the same exact Postfix configuration are sending mail with the "mail" command, and the email address they are sending from is different on each. The username, /etc/hostname, /etc/hosts, /etc/resolv.conf, /etc/mailname, and /etc/postfix/main.cf files are all exactly the same - and I have done a postfix reload / service restart and rebooted the servers several times.

I made a post on serverfault here [http://serverfault.com/questions/726886/two-identical-postfix-main-cf-files-but-sending-mail-from-cli-appears-different](http://serverfault.com/questions/726886/two-identical-postfix-main-cf-files-but-sending-mail-from-cli-appears-different) that has a lot of the info that I've dug into so far, but right now I'm stuck investigating the mail.log and I can see that the sending as email addresses are different for whatever reason and I can't for the life of me figure out what's causing it.

For the Mail.log comparison please see below:

Mail01 (I like the way this one sends out) REMOVED_URL Mail02 (this is the one sending as mail.example.com - cant figure out why) REMOVED_URL
Mail01: uid=1000 from= Mail02: uid=1000 from=operations@mail.contoso.com Mail on mail01 is submitted with a bare username (operations), so postfix appends myorigin making [email]operations@contoso.com[/email]. Mail on mail02 looks to be submitted with the full email address as the from, so Postfix doesn't append myorigin.

These are both running on Ubuntu 14.04.3 VMs that were created fresh for this, and fully updated. Again the problem here is that one mail command sends as "username@hostname.com" and the other sends as "username@mail.hostname.com" - and I'm trying to locate what setting is causing this difference because everything I can find related to mail and hostname settings on the machine are the same (save for the IP address). Obviously there is something I'm missing - and if anyone has any ideas at all I'm all ears.

Thanks!


Including postconf -n


    alias_database = hash:/etc/aliases
    alias_maps = hash:/etc/aliases
    append_dot_mydomain = no
    biff = no
    config_directory = /etc/postfix
    inet_interfaces = all
    inet_protocols = all
    mailbox_command = procmail -a "$EXTENSION"
    mailbox_size_limit = 0
    mydestination = mail.example.com, localhost.localdomain, localhost
    myhostname = mail.example.com
    mynetworks = 10.0.0.0/8 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
    myorigin = /etc/mailname
    readme_directory = no
    recipient_delimiter = +
    relayhost = smtp-relay.gmail.com
    smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
    smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
    smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
    smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
    smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
    smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
    smtpd_use_tls = yes

Update (10/08/15): I figured it out. For whatever reason, it seems like my `/etc/mailname` wasn't getting processed, even though it was identical to the other server - and the file even had the same MD5sum - the Postfix configuration wasn't taking it. I also noticed that I was using `mailutils` on one system (the one that wasn't working and had Postfix installed after the fact) and the other was using `bsd-mailx`. I swapped this before trying the `/etc/mailname` change, and it didn't seem to make a difference but for what it's worth I'm noting it just in case. Anyways I changed my `/etc/mailname` to a bogus value like `test`, then did a `sudo postfix reload` and `sudo service postfix restart` and then switched it back to what I intended it to be (`contoso.com`) followed by the same two commands to refresh the config and service, and lo-and-behold, it was working as intended. Thanks to all that helped.

---

