---
title: "LMTP Authentication Error"
date: 2020-10-05
forum: Server Platforms
---

### Post by MorseCode65 on 2020-10-05
I am stuck enabling LMTP so that I can use Sieve rules. I have a postfix -> dovecot setup on Ubuntu. I am using virtual users with a SQL backend for virtual_users, password maps, and maildir. 


I have searched for a solution and implemented everything I have read. 


I do not understand why lmtp is trying to go to /var/run/dovecot/auth-userdb (file does not exist). Everything works until I uncomment "virtual_transport = lmtp:unix:private/dovecot-lmtp” in postfix/main.cf


Anyone have a solution? 


Here is the lmtp error with surrounding messages


Oct  4 00:37:29 mmp-mail dovecot: lmtp(info@domain.com)<268290><UpizKIlReV8CGAQA9daSvw>: Debug: auth-master: userdb lookup(info@domain.com): Started userdb lookup
Oct  4 00:37:29 mmp-mail dovecot: lmtp(info@domain.com)<268290><UpizKIlReV8CGAQA9daSvw>: Debug: auth-master: conn unix:/var/run/dovecot//auth-userdb: Connecting
Oct  4 00:37:29 mmp-mail dovecot: lmtp(info@domain.com)<268290><UpizKIlReV8CGAQA9daSvw>: Error: auth-master: userdb lookup(info@domain.com): connect(/var/run/dovecot//auth-userdb) failed: No such file or directory
Oct  4 00:37:29 mmp-mail dovecot: lmtp(info@domain.com)<268290><UpizKIlReV8CGAQA9daSvw>: Debug: auth-master: userdb lookup(info@domain.com): Userdb lookup failed
Oct  4 00:37:29 mmp-mail dovecot: lmtp(268290): Error: lmtp-server: conn unix:pid=268289,uid=129 [1]: rcpt [email]info@domain.com[/email]: Failed to lookup user [email]info@domain.com[/email]: Internal error occurred. Refer to server log for more information.




I do see "auth_socket_path = auth-userdb” in doveconf output


In 10-master.conf (-rw-r--r-- 1 root root  3784 Oct  4 00:26 10-master.conf)


service auth {
  unix_listener auth-userdb {
    path = /var/spool/postfix/private/auth
    mode = 0660
    user = postfix
    group = postfix
  }
}


In auth-sql-conf.ext (-rw-r--r-- 1 root root   785 Oct  3 22:39 auth-sql.conf.ext)


userdb {
  driver = sql
  args = /etc/dovecot/dovecot-sql.conf.ext
}


In dovecot-sql.conf.ext (-rw-r----- 1 root dovecot 6086 Oct  3 22:37 dovecot-sql.conf.ext)


user_query = \
  SELECT email as user, 150 AS uid, 150 AS gid  'maildir:/home/mail/'||maildir as mail \
  FROM virtual_mailbox_maps WHERE email = '%u'

---

### Post by MorseCode65 on 2020-10-06
Any help? I'm stuck and not sure where to turn. I'm also not getting a response from the dovecot mailing list.

---

