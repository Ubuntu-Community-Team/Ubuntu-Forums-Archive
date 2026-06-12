---
title: "Auth Failure with Courier/IMAP/POP"
date: 2008-02-28
forum: Server Platforms
---

### Post by Poleh on 2008-02-28
Hi

I recently installed "the perfect Gutsy server" as per this how-to: [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

**I did not install the ISPConfig part of it**

everything seemed to work perfectly in that I received no error messages, the expected daemons are running etc. I cannot however, authenticate to either the IMAP or POP servers at all.

tail /var/log/syslog reveals the following:
```

root@ubuntu-server1:/home/duncan# tail /var/log/syslog 
Feb 28 20:23:08 ubuntu-server1 imapd: Connection, ip=[::ffff:192.168.1.13]
Feb 28 20:23:08 ubuntu-server1 imapd: LOGIN FAILED, user=duncan, ip=[::ffff:192.168.1.13]
Feb 28 20:23:36 ubuntu-server1 imapd: Connection, ip=[::ffff:192.168.1.13]
Feb 28 20:23:36 ubuntu-server1 imapd: LOGOUT, ip=[::ffff:192.168.1.13], rcvd=34, sent=456
Feb 28 20:23:36 ubuntu-server1 imapd: Connection, ip=[::ffff:192.168.1.13]
Feb 28 20:23:36 ubuntu-server1 imapd: LOGOUT, ip=[::ffff:192.168.1.13], rcvd=34, sent=456
Feb 28 20:23:36 ubuntu-server1 imapd: Connection, ip=[::ffff:192.168.1.13]
Feb 28 20:23:36 ubuntu-server1 imapd: LOGOUT, ip=[::ffff:192.168.1.13], rcvd=34, sent=456
Feb 28 20:23:37 ubuntu-server1 imapd: Connection, ip=[::ffff:192.168.1.13]
Feb 28 20:23:38 ubuntu-server1 imapd: LOGIN FAILED, user=duncan@example.com, ip=[::ffff:192.168.1.13]

```

I am trying to use Evolution to test the server and getting nowhere.

On an aside, where do I need to start reading to get information on creating users and configuring their e-mail addresses for a system like this using MailDir/ format? I understand the basics, but am not sure how to configure the user/mail address accounts ...

Thanks in advance

---

### Post by faulkes on 2008-02-28
The official documentation and community documentation on the ubuntu sites
are always the best places to start.

In particular for courier, 

[https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier)

For the official server and other community documentation, please see
my attached signature.

Thanks,

Faulkes

---

### Post by Poleh on 2008-02-28
Hi

I managed to work out why I couldn't authenticate - the user account didn't have any of the /Maildir folders created/configured as it was an existing user and IMAP wouldn't authenticate until they were created.

I created the folders as per this page: [https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier) and now everything authenticates fine.

Thanks for pointing me in the right direction! Now to work out the virtual domain / POSTFIX thing... :eek:

---

