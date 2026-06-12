---
title: "Postfix/Dovecot: Can't recieve email from outside (+DNS questions)"
date: 2017-06-09
forum: Server Platforms
---

### Post by kalinda2 on 2017-06-09
Hey everyone,

After three days worth of struggle, I finally managed to get my mail server (mostly) working. It's running on a virtual cloud server I bought on the cheap so I could learn web/email/sysadmin stuff. It also has apache (I know, I know, not a great idea, but it's not a production environment) and is hooked up to my domain name from GoDaddy.

Anyway, using the command line I am able to send emails to the outside successfully. I can also use this method to send emails to myself, which show up in my Maildir. So far so good, but the problem now is that I can't receive any emails from outside addresses like gmail or hotmail or whatever. The test emails I send don't bounce back, so clearly they must go somewhere, I just don't know where.

Before I paste the -n outputs for Postfix/Dovecot and all that, I just have a simple and probably stupid question that none of the howtos seem to take into account - Do I need to setup DNS on my server with an MX record and name servers I can input to GoDaddy for this to work? Is that why the test emails disappear into the internet ether instead of reaching their destination? Because right all I've done is change the GoDaddy DNS server settings, the cheapo server I bought doesn't come with name servers, all I got was a public IP and some other basic stuff, it's very do-it-yourself.

I've included a screencap of my GoDaddy DNS settings, if that helps. I managed to get Apache working and using my domain name this way without the need for an NS, although GoDaddy thinks my domain name isn't doing anything lol.

Anyhow, I'll provide config files if you guys tell me I don't need DNS for this, but I kinda suspect I do. It's just another complicated thing to setup and I don't want to do it if I don't actually have to. Plus I'm not even sure it's possible to make nameservers out of a domain name from GoDaddy and then give them to GoDaddy @.@ But that's mostly because I am a newbie and still learning how all of this works.

Apologies for my ignorance, any help is greatly appreciated.

Thanks!

---

### Post by darkod on 2017-06-09
The two MX records should have different priority ideally. It goes from lower to higher, so the lowest priority is sent to first.

It seems you have it set correctly. You can also delete the MX record pointing to @ and keep just the MX record pointing to mail. You have only a single server anyway... No need for two records.

Have you tested if dns is working correctly externally (from the internet)?

I assume you set Postfix to receive emails for your domain name, right?

---

### Post by kalinda2 on 2017-06-09
Thanks for the reply! I've followed your advice and deleted the @ MX record and I'll remember the thing about the priority in the future. DNS is indeed working correctly since I can ping and navigate to my domain in a web browser from outside my server and when I SSH into my server I can use my domain name. I recently set the server's hostname to mail.domain.com, but it probably should just be domain.net so my emails get sent as [EMAIL="user@domain.net"]user@domain.net[/EMAIL] instead of @mail.domain.net.

I should also mention that I just found [this]("https://ca.godaddy.com/help/add-my-own-host-names-as-nameservers-12320") guide from GoDaddy about adding your own hostnames as name servers through them (if that is needed, it seems like maybe a good idea anyway). I went with ns1.domain.net and ns2.domain.net and pointed them both at my server's public IP. Not sure if that'll work or not since I've not set up anything on the server for them, but we'll see.

Yup, I set Postfix to receive emails from my domain name, I think. Here's the output for postconf -n:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
home_mailbox = Maildir/
inet_interfaces = localhost PublicIPIsHere
inet_protocols = all
mailbox_size_limit = 0
mydestination = mail.domain.net, domain.net, localhost.domain.net localhost
mydomain = domain.net
myhostname = mail.domain.net
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 PublicIPIsHere
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

And now doveconf -n, just in case:
```
# 2.2.22 (fe789d2): /etc/dovecot/dovecot.conf
# Pigeonhole version 0.4.13 (7b14904)
# OS: Linux 4.4.0-78-generic x86_64 Ubuntu 16.04.2 LTS
auth_mechanisms = plain login
auth_verbose = yes
imap_client_workarounds = tb-extra-mailbox-sep
log_path = /var/log/dovecot.log
mail_debug = yes
mail_location = maildir:~/Maildir
namespace inbox {
  inbox = yes
  location =
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix =
}
passdb {
  driver = pam
}
protocols = pop3 imap
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0600
    user = postfix
  }
}
service imap-login {
  inet_listener imap {
    port = 143
  }
  inet_listener imaps {
    port = 993
    ssl = yes
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 110
  }
  inet_listener pop3s {
    port = 995
    ssl = yes
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  driver = passwd
}
```

There's nothing in my logs to indicate that the test emails arrived, unless I missed something.

ETA: Ahah, ok, nevermind about the name server thing, I understand it better now. No need to provide your own, GoDaddy is already doing it all for me and I am using theirs.

---

### Post by kalinda2 on 2017-06-09
...

.....

LMAO Oh god, I can't believe this didn't occur to me - I had SMTP's port 25 closed since I set up ufw for my firewall. I opened it and then used
```
sudo ufw allow [profilename]
```
and enabled all the Postfix and Dovecot app profiles, in case anyone else has this issue and stumbles on this thread. You can use the ufw app list command to show you a list of all the app profiles it has.

Anyway, I am receiving email now! Of course the simplest solution is the right one.

I do still have other questions though - [s]I only receive mail if it's sent to [EMAIL="user@mail.domain.net"]user@mail.domain.net[/EMAIL] and I'd rather it not include the mail part. I know I can achieve this if I change my hostname back to domain.net, but is there another way? I told Postfix that mail.domain.net was my hostname.[/s] Annd nevermind, I got emails going to domain.net, my server is just slow on the uptake and its receive time is not the best.

Also I guess Dovecot/Postfix is automatically is set up to use mail.domain.net for SMTP/POP3/IMAP servers when you add them in clients, eh? None of the howtos I saw really said I had to do anything to make it work.

Right now I get this in my server logs when attempting to add the account in Thunderbird, so they are at least talking to each other:
```
pop3-login: Info: Aborted login (no auth attempts in 0 secs): user=<>, rip=MyHomePCPublicIP, lip=ServerPublicIP, session=<FhUqIo9RGNgY1MPG>
```

I'll look around to see what I can do about it, but if anyone has any advice that or general mail server recs I'm happy to hear them. Also gonna set up Roundcube for webmail.

---

