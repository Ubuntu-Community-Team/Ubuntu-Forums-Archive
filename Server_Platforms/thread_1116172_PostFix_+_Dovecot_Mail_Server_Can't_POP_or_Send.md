---
title: "PostFix + Dovecot Mail Server: Can't POP or Send"
date: 2009-04-04
forum: Server Platforms
---

### Post by azurepancake on 2009-04-04
For a little project I've decided to try and setup a little eMail sever with a spare computer I have laying around. I have Linux installed on it and have been following a guide for setting it up.

[http://www.howtoforge.com/arch-linux-mailserver-with-postfix-and-dovecot](http://www.howtoforge.com/arch-linux-mailserver-with-postfix-and-dovecot)

The above guide calls for the installation of PostFix as the MTA for handling SMTP and Dovecot as the MDA for POP and IMAP. I installed these services and followed the guide with really no problems at all. I also installed SpamAssassain and Postgrey. My domains MX-records are set to point to my server, I have forwarded ports 110 and 25 on my router and everything appears ready to work.

The issue that I am having: from Gmail I can send a eMail to a user on my mail server, 'test@mydomain.com'. I can verify that the eMail has been sent, because it arrives in that users 'Maildir/new' directory and I can read it. However, when I try to POP or send using a eMail client, it just times out. For now I've been trying to test it with telnet and the Sylpheed eMail client.

So, the eMail is arriving at the server and being written to the 'Maildir/new' directory, but it appears it can't be downloaded using POP. Due to this, I would imagine that the issue would be with the MDA, Dovecot. However, I can't send either from one of the accounts on the server, which makes me think there might be a configuration issue with PostFix as well.

Here is my */etc/dovecot/dovecot.conf* file:

```
protocols = pop3 pop3s imap imaps
disable_plaintext_auth = no
pop3_uidl_format = %08Xu%08Xv 
log_timestamp = "%b %d %H:%M:%S "
ssl_disable = no
ssl_cert_file = /etc/ssl/certs/mail.crt
ssl_key_file = /etc/ssl/private/mail.key
mail_location = maildir:~/Maildir
mail_access_groups = mail
auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@
protocol pop3 {
  listen = 110
}
protocol imap {
  imap_client_workarounds = delay-newmail tb-extra-mailbox-sep
}
auth default {
  mechanisms = plain login
  passdb pam {
  }
  userdb passwd {
  }
  user = root
  socket listen {
    client {
      path = /var/run/dovecot/auth-client
      user = postfix
      group = postfix
      mode = 0660
    }
  }
}
```
And my */etc/postfix/main.cf* file:

```
# Paths
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
mail_owner = postfix
# Domain settings
myhostname = mail.example.com
myorigin = example.com
mydestination = $myhostname, localhost.$mydomain, localhost
# Timeout settings and other limits
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
minimal_backoff_time = 300s
maximal_backoff_time = 1200s
maximal_queue_lifetime = 1d
bounce_queue_lifetime = 1d
smtp_helo_timeout = 60s
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
# SMTP settings
smtpd_tls_cert_file=/etc/ssl/certs/mail.crt
smtpd_tls_key_file=/etc/ssl/private/mail.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:/var/lib/postfix/smtpd_scache
smtp_tls_session_cache_database = btree:/var/lib/postfix/smtp_scache
smtpd_tls_loglevel = 1
smtpd_sasl_auth_enable = yes
#smtp_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,
                               permit_mynetworks,
                               reject_unauth_destination,
                               check_policy_service inet:127.0.0.1:10030
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks
smtpd_sasl_security_options = noanonymous
# SASL
smtpd_sasl_type = dovecot
smtpd_sasl_path = /var/run/dovecot/auth-client
# Network settings
inet_interfaces = all
inet_protocols = ipv4
mynetworks = 127.0.0.0/8
relayhost =
# Email and mailbox settings
alias_maps = hash:/etc/postfix/aliases
alias_database = $alias_maps
home_mailbox = Maildir/
virtual_alias_domains = example.com
virtual_alias_maps = hash:/etc/postfix/virtual
mailbox_size_limit = 0
# Misc
mailbox_command = /usr/bin/procmail
smtpd_banner = $myhostname ESMTP
biff = no
append_dot_mydomain = no
debug_peer_level = 2
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
setgid_group = postdrop
html_directory = no
manpage_directory = /usr/man
sample_directory = /etc/postfix/sample
readme_directory = no
recipient_delimiter = +
```
I of course replaced the following sections with my domains information:
[i]
myhostname
myorigin
virtual_alias_domains[/i]

I was hoping that someone might be able to set me on the right track here. I'm new to configuring eMail services and it can become quite convoluted. I hope that I have been some what clear on what my issue is, and if you need anymore information that might be pertinent to the issue, please ask and I'll be glad to supply it.

If anyone has 2 cents on the issue, I would greatly appreciate any information!

Thank you very much.

---

### Post by azurepancake on 2009-04-04
Hmm, I think I might be on to something here. I can telnet into the servers SMTP port (25) when I telnet into the servers local IP address (192.168.XXX.XXX). But, I cannot do this for POP (110):

Also, when I go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and I put in port 25, it is succesful:

```
Success: I can see your service on XXX.XXX.XXX.XXX on port (25)
Your ISP is not blocking port 25
```

However, for POP:

```
Error: I could not see your service on XXX.XXX.XXX.XXX on port (110)
Reason: Connection refused
```

So, I am guessing there is a port issue. Though, I don't see how this would effect me from locally connecting to my POP server, which makes me think there is also a Dovecot configuration issue.

Welp, to me it seems the issue is only with POP (Dovecot) and not SMTP (PostFix).

If anyone has any ideas, please share them!

Thanks.

---

### Post by azurepancake on 2009-04-04
I think I might have it working now. I reconfigured my dovecot.conf file to look like so:

```
protocols = pop3
mail_location = maildir:~/Maildir
mail_location = maildir:/home/%u/Maildir
disable_plaintext_auth = no
ssl_disable = yes

auth default {
  mechanisms = plain login
  passdb pam {
  }
  userdb passwd {
  }
  user = root
  socket listen {
    client {
      path = /var/run/dovecot/auth-client
      user = postfix
      group = postfix
      mode = 0660
    }
  }
}
```

Now I can telnet into both POP3 and SMTP locally. Now I just need to try and POP from outside of my network and make sure it works!

---

### Post by LiQuidAiR on 2009-04-11
Did you get it to work?

I've been having trouble with my Postfix and Dovecot installation.

---

### Post by ivoks on 2009-04-11
Install jaunty-server. Install dovecot-postfix package. Done. More info at: [http://blog.init.hr/?p=3](http://blog.init.hr/?p=3)

---

