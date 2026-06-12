---
title: "Low memory IMAP server for use with PHP mail()"
date: 2013-10-07
forum: Server Platforms
---

### Post by wolfgentleman on 2013-10-07
I am looking for an IMAP server that I can limit/runs on 100MB of ram or less, integrates easily with the PHP mail function, and will support: 2 Thunderbird clients and 2 K9Mail clients. I would also like a tutorial on setting it up (I'm a n00b in the mail server department :P). I know I need a mail relay and I get one free with my server, but that's the extent of my knowledge when it comes to running a mail server. Any and all suggestions, links, and help is greatly appreciated.

---

### Post by SeijiSensei on 2013-10-26
The two most common IMAP servers are dovecot and the much older UW-imap.  I'm running dovecot on one server.  The total footprint is 2 MB, but only 572 of that is unique to dovecot.  There are a couple of helper programs like dovecot-auth, but they are pretty tiny.

I don't know what your provider supplies in terms of a "mail relay," but you'll also need an SMTP server like Postfix or sendmail.  Dovecot just provides delivery services for existing messages.  (It's called a "Mail User Agent" in the parlance; something like sendmail is a "Mail Transfer Agent.")

---

### Post by wolfgentleman on 2013-10-28
> **SeijiSensei said:**
> The two most common IMAP servers are dovecot and the much older UW-imap.  I'm running dovecot on one server. Yeah, I was looking at dovecot...
> **SeijiSensei said:**
> The total footprint is 2 MB, but only 572 of that is unique to dovecot.  There are a couple of helper programs like dovecot-auth, but they are pretty tiny.

When you say "total footprint is 2 MB" do you mean entire server? and when you say "only 572 of that is unique to dovecot" do you mean 572 KB? I just don't see how you can get it so low... Granted I am running apache, mysql, sks, ssh, and a few other things but I don't see how it's possible...
> **SeijiSensei said:**
> 
I don't know what your provider supplies in terms of a "mail relay,"
Rackspace provides a mail relay free of charge (for 50,000 mesages per month) and I think it's mailgun, but I don't remember...
> **SeijiSensei said:**
> but you'll also need an SMTP server like Postfix or sendmail.  Dovecot just provides delivery services for existing messages.  (It's called a "Mail User Agent" in the parlance; something like sendmail is a "Mail Transfer Agent.")
Ok, that should be easy enough... Can I get a few links for some tutorials?

---

### Post by SeijiSensei on 2013-10-28
For documentation I'd start with the [Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/").

Yes, I mean the total footprint of the dovecot server is 2 MB with a unique 576K segment.  The rest of the code is shared, largely via libc.  Most servers run in small memory segments since they don't have to interface with many parts of the operating system.  Basically all the server does is act on IMAP commands after authentication.  It reads the commands and spits back output to your mail reader.  

I've run text-based servers in as little as 64MB even in recent years.  [The first servers]("http://www.thefreelibrary.com/DELL+FIRST+TO+SHIP+SYSTEMS+WITH+NEW+PENTIUM+PROCESSOR+Reduces+Dell...-a016835682") I built and sold were on i386 platforms with, maybe, 16 MB of memory total. I could build a combined web/DNS/dialup/email server on one of these in the mid 1990s.

---

### Post by wolfgentleman on 2013-10-29
> **SeijiSensei said:**
> For documentation I'd start with the [Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/").

Yes, I mean the total footprint of the dovecot server is 2 MB with a unique 576K segment.  The rest of the code is shared, largely via libc.  Most servers run in small memory segments since they don't have to interface with many parts of the operating system.  Basically all the server does is act on IMAP commands after authentication.  It reads the commands and spits back output to your mail reader.  

I've run text-based servers in as little as 64MB even in recent years.  [The first servers]("http://www.thefreelibrary.com/DELL+FIRST+TO+SHIP+SYSTEMS+WITH+NEW+PENTIUM+PROCESSOR+Reduces+Dell...-a016835682") I built and sold were on i386 platforms with, maybe, 16 MB of memory total. I could build a combined web/DNS/dialup/email server on one of these in the mid 1990s.
Ok, the link you provided was a bit confusing but I found [this]("http://ubuntuguide.org/wiki/Mail_Server_setup") and these: [UserDatabase]("http://wiki2.dovecot.org/UserDatabase#Userdb_settings"), [AuthDatabase/PasswdFile]("http://wiki2.dovecot.org/AuthDatabase/PasswdFile"), and [BasicConfiguration]("http://wiki2.dovecot.org/BasicConfiguration") and now dovecot & postfix is running, however I cannot connect.

Here is my main DNS records and the mailing system records:[SIZE=1]
[/SIZE][TABLE="class: grid, width: 500"]
[TR]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]A[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]50.56.177.159[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]NS[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]dns1.stabletransit.com[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]NS[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]dns2.stabletransit.com[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]MX[/SIZE][/TD]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]Priority: 10[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]www.twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]CNAME[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]twprogrammers.com[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]TXT[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]v=spf1 include:mailgun.org ~all[/SIZE][/TD]
[/TR]
[TR]
[TD][SIZE=1]krs._domainkey.twprogrammers.com[/SIZE][/TD]
[TD][SIZE=1]TXT[/SIZE][/TD]
[TD="colspan: 2"][SIZE=1]REMOVED[/SIZE][/TD]
[/TR]
[/TABLE]

Output of [HIGHLIGHT]dovecot -n[/HIGHLIGHT]:
```
# 2.0.19: /etc/dovecot/dovecot.conf# OS: Linux 3.2.0-24-virtual x86_64 Ubuntu 12.04.3 LTS
mail_location = maildir:~/Maildir
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = imap pop3 sieve
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
protocol imap {
  imap_client_workarounds = tb-extra-mailbox-sep
  mail_max_userip_connections = 10
}
protocol pop3 {
  mail_max_userip_connections = 10
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol lda {
  deliver_log_format = msgid=%m: %$
  mail_plugins = sieve
  postmaster_address = postmaster
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}
```

Passwd File:
```
admin@twprogrammers.com:{PLAIN}REMOVED
```

---

### Post by SeijiSensei on 2013-10-29
For security purposes dovecot, like most Ubuntu daemons, is bound to the localhost interface by default.  Try adding "listen=*" as described [here](https://help.ubuntu.com/community/Dovecot#Accessing_from_Outside).

You can see if this is the problem right away by trying "telnet localhost 143" and "telnet your.external.ip.addr 143".  If the first works, and the second does not, you need to add the "listen".

---

### Post by wolfgentleman on 2013-10-31
> **SeijiSensei said:**
> For security purposes dovecot, like most Ubuntu daemons, is bound to the localhost interface by default.  Try adding "listen=*" as described [here]("https://help.ubuntu.com/community/Dovecot#Accessing_from_Outside").

You can see if this is the problem right away by trying "telnet localhost 143" and "telnet your.external.ip.addr 143".  If the first works, and the second does not, you need to add the "listen".
Ok, I did it as well as a few other tweaks and it still does not connect. Here is the output of [HIGHLIGHT]dovecot -n[/HIGHLIGHT]:
```

# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-24-virtual x86_64 Ubuntu 12.04.3 LTS ext3
auth_debug = yes
auth_debug_passwords = yes
auth_mechanisms = plain login digest-md5 cram-md5
auth_verbose = yes
auth_verbose_passwords = plain
debug_log_path = /etc/dovecot/logs[ATTACH]247405[/ATTACH]/dovecot-debug.log
disable_plaintext_auth = no
info_log_path = /etc/dovecot/logs/dovecot-info.log
log_path = /etc/dovecot/logs/dovecot-error.log
mail_attachment_dir = /home/twp/Maildir/.attachments
mail_attachment_hash = %{sha1:16}%{size}%{md4:16}
mail_attachment_min_size = 1 B
mail_location = maildir:/home/twp/Maildir
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
protocols = imap
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
service imap-login {
  inet_listener imap {
    address = *
    port = 143
  }
  inet_listener imaps {
    address = *
    port = 993
  }
}
service imap {
  process_limit = 10
  vsz_limit = 100 M
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
protocol imap {
  imap_client_workarounds = tb-extra-mailbox-sep
  mail_max_userip_connections = 10
}

```

I am attaching the log files.
[ATTACH]247405[/ATTACH]

---

### Post by SeijiSensei on 2013-10-31
You have "address = *" where I believe the syntax should be "listen = *".

The error log complains about not being able to connect to the authentication service.  I just create local accounts on the machine and authenticate against /etc/passwd.  If you're using some other mechanism like MySQL in the back end, maybe the problem lies in the interface between them.

---

### Post by wolfgentleman on 2013-10-31
> **SeijiSensei said:**
> You have "address = *" where I believe the syntax should be "listen = *".


When I use [HIGHLIGHT]listen = *[/HIGHLIGHT] I get:
```

# 2.0.19: /etc/dovecot/dovecot.conf
doveconf: Fatal: Error in configuration file /etc/dovecot/dovecot.conf line 54: Unknown setting: listen
doveconf: Error: managesieve-login: dump-capability process returned 89
doveconf: Fatal: Error in configuration file /etc/dovecot/dovecot.conf line 54: Unknown setting: listen

```

> **SeijiSensei said:**
> 
The error log complains about not being able to connect to the authentication service.  I just create local accounts on the machine and authenticate against /etc/passwd.  If you're using some other mechanism like MySQL in the back end, maybe the problem lies in the interface between them.

I am using passwd file
```
passdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
userdb {
  args = /etc/passwd.dovecot
  driver = passwd
}
```
Here is the contents of /etc/passwd.dovecot
```
admin@twprogrammers.com:{PLAIN}REMOVED
```

EDIT:
I fixed half the problem [HIGHLIGHT]driver = passwd[/HIGHLIGHT] is supposed to be [HIGHLIGHT]driver = passwd-file[/HIGHLIGHT]. Now the problem is the passwd.dovecot, I did not realize that the rest of the line was required [S]because [this]("http://wiki2.dovecot.org/AuthDatabase/PasswdFile") said otherwise[/S] - misinterpreted... Looking to fix it now...

```

Oct 31 19:34:49 auth: Error: passwd-file /etc/passwd.dovecot: User admin@twprogrammers.com is missing userdb info
Oct 31 19:34:49 imap(admin@twprogrammers.com): Error: user admin@twprogrammers.com: Couldn't drop privileges: User is missing UID (see mail_uid setting)
Oct 31 19:34:49 imap(admin@twprogrammers.com): Error: Internal error occurred. Refer to server log for more information.

```

UPDATE:
I got IMAP login working now, just need to setup SSL/TLS, postfix login, IMAP folders, and a more secure passwd file but I will need help there as well. Thank you for all the help you have provided.


[RIGHT]Happy Halloween!!!
[/RIGHT]

---

### Post by wolfgentleman on 2013-11-02
IMAP is working now but the folders are not setup. Postfix however is... malfunctioning. It won't connect on the SSL/TLS port and when I try to connect through port 25 it barks on thunderbird and k-9, but mutt seems to work fine - connects, reads, and sends mail. I think it doesn't like port 25 because I have it set to only allow SSL/TLS. I am attaching the configs.
[ATTACH]247483[/ATTACH]

---

### Post by SeijiSensei on 2013-11-02
SMTP over SSL/TLS uses port 465.

Here are the other relevant SSL ports from /etc/services:
```

imaps           993/tcp               # IMAP over SSL
imaps           993/udp               # IMAP over SSL
pop3s           995/tcp               # POP-3 over SSL
pop3s           995/udp               # POP-3 over SSL
urd             465/tcp       smtps   # URL Rendesvous Directory for SSM / SMTP over SSL (TLS)

```

---

### Post by wolfgentleman on 2013-11-02
> **SeijiSensei said:**
> SMTP over SSL/TLS uses port 465.

Here are the other relevant SSL ports from /etc/services:
```

imaps           993/tcp               # IMAP over SSL
imaps           993/udp               # IMAP over SSL
pop3s           995/tcp               # POP-3 over SSL
pop3s           995/udp               # POP-3 over SSL
urd             465/tcp       smtps   # URL Rendesvous Directory for SSM / SMTP over SSL (TLS)

```

That's why I am so confused. Postfix refuses to accept connections on 465 and because I have [HIGHLIGHT]smtpd_tls_auth_only = yes[/HIGHLIGHT] set it refuses non-TLS connections and gets confused when I try to connect with TLS on port 25. The server has an open firewall so all ports are accessible from the outside world.

---

### Post by wolfgentleman on 2013-11-05
bump

---

### Post by wolfgentleman on 2013-11-09
bump

---

### Post by wolfgentleman on 2013-11-11
bump

---

### Post by SeijiSensei on 2013-11-13
I, for one, cannot help more with this I'm afraid, Patrick.  I rarely use Postfix since I have been using sendmail for decades now.

I suggest you start a new thread for this specific problem.  The current thread title no longer pertains the problem you are having.

---

