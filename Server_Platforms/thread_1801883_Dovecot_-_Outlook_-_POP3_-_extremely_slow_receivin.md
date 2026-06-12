---
title: "Dovecot - Outlook - POP3 - extremely slow receiving"
date: 2011-07-11
forum: Server Platforms
---

### Post by Jarks on 2011-07-11
Hi there, 

recently I've replaced an old windows mailserver with a new one running 10.04 LTS (postfix - dovecot) but I got a strange problem with MS Outlook 2003 and 2007 on **Win XP**. These MUAs receive new messages **extremely slow**. Some of messages are received repeatedly.

All I found in /var/log/mail.log is login and then (after 1 minute) disconnection for inactivity. No errors.:

[FONT=Courier New]Jul 11 10:36:51 dovecot: pop3-login: Login: user=([EMAIL="user@domain.org"]user@domain.org[/EMAIL]), method=NTLM, rip=xxx.xxx.xxx.xxx, lip=xxx.xxx.xxx.xxx
Jul 11 10:37:07 dovecot: POP3([EMAIL="user@domain.org"]user@domain.org[/EMAIL]): Disconnected for inactivity top=0/0, retr=1/5434, del=0/12, size=954793  [/FONT]

nothing more. And outlooks wait and wait reporting "receiving". What they are waiting for? Is there something dovecot should send them?

At the same time Mozilla Thunderbird and Opera Mail on the same network with the same setup don't have any problems. I just don't get it.

Does anyone know what to do to get it work please? Thanks.

**dovecot -n :**
```
# 1.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.32-32-generic x86_64 Ubuntu 10.04.2 LTS ext4
protocols: imap pop3
ssl: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
first_valid_uid: 999
last_valid_uid: 999
first_valid_gid: 999
last_valid_gid: 999
mail_location: maildir:/var/mail/virtual/%d/%n
mbox_write_locks: fcntl dotlock
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
imap_client_workarounds(default): outlook-idle
imap_client_workarounds(imap): outlook-idle
imap_client_workarounds(pop3):
pop3_client_workarounds(default):
pop3_client_workarounds(imap):
**pop3_client_workarounds(pop3): outlook-no-nuls oe-ns-eoh**
auth default:
  mechanisms: login cram-md5 digest-md5 ntlm
  user: dovecot-auth
  passdb:
    driver: sql
    args: /etc/dovecot/mysql.conf
  userdb:
    driver: sql
    args: /etc/dovecot/mysql.conf
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth
      mode: 432
      user: postfix
      group: postfix
```

---

### Post by SeijiSensei on 2011-07-11
method=NTLM

As I recall this means that the person is authenticating using "NT Lan Manager," a Microsoft authentication method.  Have you read this:

[http://wiki2.dovecot.org/Authentication/Mechanisms/NTLM](http://wiki2.dovecot.org/Authentication/Mechanisms/NTLM)

---

### Post by Jarks on 2011-07-11
> **SeijiSensei said:**
> method=NTLM...

Thanks but it doesn't seem to be the problem. Some of the Outlooks use method=DIGEST-MD5 and they are slow too.

One more thing: when I use SSL(TLS) connection, receiving is much faster. But I don't know why. Maybe is something wrong about port 110?

---

### Post by SeijiSensei on 2011-07-11
> **Jarks said:**
> Thanks but it doesn't seem to be the problem. Some of the Outlooks use method=DIGEST-MD5 and they are slow too.

One more thing: when I use SSL(TLS) connection, receiving is much faster. But I don't know why. Maybe is something wrong about port 110?

"retr=1/5434, del=0/12, size=954793"

I've had problems with Outlook clients timing out.  Do the timeouts occur with simple text messages as well as longer ones with attachments? 

It looks like you have Outlook clients set up with POP3 and the "leave mail on server" option.  If you're using mbox folders, it can take some time for the server to rescan the entire file and transmit only the new messages.  Try switching a client to IMAP and see if that helps any, or just force the clients to download the messages and delete them from the server.  I know that's a problem in some organizations where people want to see their mail from multiple locations.  If so, you should probably be using IMAP.

I haven't a clue why using SSL should be any faster; are you using SSL with POP, or with IMAP?

---

### Post by Jarks on 2011-07-11
Outlooks don't report any errors. They are just slow. Neither does dovecot. It just disconnects Outlook for inactivity. The problem occurs with all messages even very small ones and even there is just 3 messages to download.

Clients use POP3 and messages are downloaded to the local computers (no leaving on server). Messages are stored in maildir.

The biggest mystery for me is that Thunderbird and OperaMail have no problems. So it must be something with the Outlook.

IMAP works fine both in Outlooks and RoundCube but I have no chance to convince clients to use another program or IMAP access. It's all about MS Outlook and POP3.

---

