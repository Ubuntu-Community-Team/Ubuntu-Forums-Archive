---
title: "Dovecot-imapd+MySQL TBird/OE good O2k/2k3 bad"
date: 2007-01-31
forum: Server Platforms
---

### Post by fatgav on 2007-01-31
I am having some trouble with an email server I have been trying to set up for our office using Ubuntu Server 6.10 on x86. I am trying to set up quite a simple installation using Postfix and Dovecot with MySQL authentication. I have used the following two howto documents to help me...

[http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL]("http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL")
and
[http://postfix.pentachron.net/]("http://postfix.pentachron.net/")

plus documentation on the main postfix and dovecot sites. I have successfully managed to implement a server that is fully functional with Thunderbird and Outlook Express clients. The problem comes when trying to use Outlook 2002 as a client. The first few interactions with the server work well (EG opening the the inbox and reading the first mail item). The problem comes then when I read too many mails or open a subfolder. As for creating a new folder on the server, well that's impossible, it just keeps saying "Downloading Hierarchy..." in the status bar. The same problem happens in Outlook 2003 with an (almost) identical implementation that I created at home last night.

I have spent most of the day trying to find a solution on the web and have read much of Outlook's IMAP flakyness. Surely, this is not the only reason for my problems or I would have thought the Dovecot/Microsoft developers would have done something by now. 

Could someone please check my config files to see if I have made any obvious mistake.

/etc/postfix/main.cf
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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = vmmailserve.brockington.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = vmmailserve.brockington.com, localhost.brockington.com, localhos                                                              t
relayhost = tobit.brockington.com
mynetworks = 128.1.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

virtual_alias_maps = mysql:/etc/postfix/mysql/mysql_virtual_alias_maps.cf
virtual_gid_maps = static:1000
virtual_mailbox_base = /usr/local/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql/mysql_virtual_domains_maps.cf
virtual_mailbox_limit = 51200000
virtual_mailbox_maps = mysql:/etc/postfix/mysql/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 1000
virtual_transport = virtual
virtual_uid_maps = static:1000
# Additional for quota support
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql/mysql_virtual_mailbox_limi                                                              t_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the user's maildir has overdrawn his disk                                                              space quota, please try again later.
virtual_overquota_bounce = yes

smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

```

/etc/postfix/mysql/* - as listed in [this doc]("http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL")

/etc/dovecot/dovecot.conf
```
protocols = imap imaps # only set the services you want - the s stands for secure (ssl)
disable_plaintext_auth = no
listen = *

mail_extra_groups = postfix
verbose_proctitle = yes
first_valid_uid = 1000
first_valid_gid = 111
#umask = 0077
mbox_read_locks = fcntl
mbox_write_locks = fcntl

#ssl:
ssl_disable = yes
#ssl_cert_file = /usr/share/ssl/s/Cert.pem
#ssl_key_file = /usr/share/ssl/s/PrivateKey.pem

default_mail_env = maildir:/usr/local/virtual/%u/

protocol imap {
  imap_client_workarounds = delay-newmail outlook-idle netscape-eoh tb-extra-mailbox-sep
}

protocol lda {
  postmaster_address = postmaster@teddingtons.net
  sendmail_path = /usr/local/sbin/sendmail
}


auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@

auth_debug = yes
auth_verbose = yes

auth default {

    passdb sql {
        args = /etc/dovecot/dovecot-mysql.conf
    }

    userdb sql {
        args = /etc/dovecot/dovecot-mysql.conf
    }

    socket listen {
        client {
            user = postfix
            group = postfix
            path = /var/spool/postfix/private/auth
            mode = 0660
        }
    }
}

```

/etc/dovecot/dovecot-mysql.conf
```
# Database driver: mysql, pgsql
driver = mysql

# Currently supported schemes include PLAIN, PLAIN-MD5, DIGEST-MD5, and CRYPT.
default_pass_scheme = PLAIN

# Database options
connect = host=localhost dbname=postfix user=postfix password=*******

password_query = SELECT password FROM mailbox WHERE username = '%u' AND active = '1'
user_query = SELECT maildir, 1000 AS uid, 1000 AS gid FROM mailbox WHERE username = '%u' AND active = '1'

# eof
```

tail /var/log/mail.log
```
Jan 31 16:35:15 vmmailserve dovecot: auth(default): master out: USER^I26^Igav@teddingtons.net^Imaildir=gav@teddingtons.net/^Iuid=1000^Igid=1000
Jan 31 16:35:15 vmmailserve dovecot: imap-login: Login: user=<gav@teddingtons.net>, method=PLAIN, rip=128.1.1.161, lip=128.1.1.103
Jan 31 16:35:16 vmmailserve dovecot: IMAP(gav@teddingtons.net): Disconnected
Jan 31 16:35:16 vmmailserve dovecot: auth(default): client in: AUTH^I1^IPLAIN^Iservice=IMAP^Ilip=128.1.1.103^Irip=128.1.1.161^Iresp=<hidden>
Jan 31 16:35:16 vmmailserve dovecot: auth-worker(default): sql(gav@teddingtons.net,128.1.1.161): query: SELECT password FROM mailbox WHERE username = 'gav@teddingtons.net' AND active = '1'
Jan 31 16:35:16 vmmailserve dovecot: auth(default): client out: OK^I1^Iuser=gav@teddingtons.net
Jan 31 16:35:16 vmmailserve dovecot: auth(default): master in: REQUEST^I27^I3603^I1
Jan 31 16:35:16 vmmailserve dovecot: auth-worker(default): sql(gav@teddingtons.net,128.1.1.161): SELECT maildir, 1000 AS uid, 1000 AS gid FROM mailbox WHERE username = 'gav@teddingtons.net' AND active = '1'
Jan 31 16:35:16 vmmailserve dovecot: auth(default): master out: USER^I27^Igav@teddingtons.net^Imaildir=gav@teddingtons.net/^Iuid=1000^Igid=1000
Jan 31 16:35:16 vmmailserve dovecot: imap-login: Login: user=<gav@teddingtons.net>, method=PLAIN, rip=128.1.1.161, lip=128.1.1.103
```


Obviously, the finished system will have better security (I have disabled TLS and am using PLAIN passwords etc.), but I am just trying to get the fundamentals to work at the moment.

If anybody knows what I should be doing I will be truly grateful.

Thanks,
Gav

---

### Post by fatgav on 2007-02-02
Nobody able to help? Oh well, looks like we will have to fork out for Exchange instead. :(

---

### Post by godlike on 2007-02-16
Hey i hear your pain for email servers+ubuntu+help lol I too couldnt get one working proper with the howtos but Exchange? Id eitehr dig around more or do what i did... Switch to opensuse and use qmail easy setup if u use the qmail toaster site.

---

### Post by MJN on 2007-02-16
> **fatgav said:**
> I have spent most of the day trying to find a solution on the web and have read much of Outlook's IMAP flakyness. Surely, this is not the only reason for my problems or I would have thought the Dovecot/Microsoft developers would have done something by now.
 
Don't bet on it - Microsoft have never had any reason to improve IMAP compatibility as its usage goes against the progression of Exchange.
 
Of course, even if the problem is purely down to Outlook that's not to say Dovecot doesn't have any special handling available to cope with it. Try increasing the logging level of Dovecot and seeing at what point the problems occur i.e. *who had the last say?*
 
Mathew

---

### Post by AnRkey on 2008-05-16
Did anyone ever get this fixed? I have this exact same problem. Any help would be cool.

---

### Post by AnRkey on 2008-05-28
OK some info...

My box is a 7.10 server with Postfix, fetchmail, dovevot-imapd and dovecot-pop3d installed. (Oh and I think it's using procmail in there somewhere too)

They work just fine together with almost no fuss. The problem for me was getting outlook express to connect and work with the IMAPd. I later found out that a quick upgrade to outlook express 6 would solve the problem, it did. (BTW: Outlook Express 6 is part of IE6 so you just upgrade to IE6 and OE6 comes with it.)

Outlook 2003 did the same thing that Fatgav's Outlook 2002 was doing. I tried another Outlook 2003 box in my office and it worked fine... Hmmm. So we reinstalled Outlook 2003 on the box that was giving the problems and then presto it started working fine. 

The only problem is that I still can't create folders in any of my INBOX's through IMAP with Outlook Express 6, Outlook 2003 or Thunderbird 2.0.14. I can create folders elsewhere in the IMAP account though. It would seem that the INBOX folder is read only as far as folders go...:confused:


I think if we all share our findings, then we can fix this last annoying problem.

Fatgav: Did you switch to exchange in the end? I hope for your sake you didn't.

Later,

R

---

### Post by MJN on 2008-05-28
Increase the verbosity of Dovecot's logging and post the output.
 
Where are your user's Inboxes strored? Does Dovecot (and/or the users themselves) have full write access?
 
Mathew

---

