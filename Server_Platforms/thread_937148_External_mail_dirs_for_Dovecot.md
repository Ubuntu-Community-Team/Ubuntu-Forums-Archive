---
title: "External mail dirs for Dovecot"
date: 2008-10-03
forum: Server Platforms
---

### Post by pmcewan on 2008-10-03
I've installed Ubuntu 8.04 as a mail server, and it's working very well.  However, I need to put the mail directories on an external Windows file server.  When I try to do this by moving the mail root to the external file server using samba and symbolic links, it gives a lot of errors in Dovecot.log.  The errors are below, but is there another to do this?  Can the email be pushed into MySQL instead somehow?  The Windows share has all rights granted to everybody for now.  Thanks -- Paul

dovecot: 2008-10-02 23:34:07 Info: auth(default): client in: AUTH	1	PLAIN	service=POP3	lip=192.168.100.33	rip=192.168.5.27	resp=<hidden>
dovecot: 2008-10-02 23:34:07 Info: auth-worker(default): sql(pmcewan@somewhere.com,192.168.5.27): query: SELECT id as user, clear as password FROM users WHERE id = 'pmcewan@somewhere.com'
dovecot: 2008-10-02 23:34:07 Info: auth(default): client out: OK	1	user=pmcewan@somewhere.com
dovecot: 2008-10-02 23:34:07 Info: auth(default): master in: REQUEST	27	21728	1
dovecot: 2008-10-02 23:34:07 Info: auth-worker(default): sql(pmcewan@somewhere.com,192.168.5.27): SELECT home, uid, gid FROM users WHERE id = 'pmcewan@somewhere.com'
dovecot: 2008-10-02 23:34:07 Info: auth(default): master out: USER	27	[email]pmcewan@somewhere.com[/email]	home=/var/spool/mail/virtual/pmcewan@somewhere.com	uid=5000	gid=5000
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): Effective uid=5000, gid=5000
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): maildir: access(/var/spool/mail/virtual/pmcewan@somewhere.com/Maildir, rwx): failed: No such file or directory
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): maildir: couldn't find root dir
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): mbox: root exists (/var/spool/mail/virtual/pmcewan@somewhere.com/mail)
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): mbox: INBOX: access(/var/mail/pmcewan@somewhere.com, rw) failed: No such file or directory
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): mbox: INBOX: access(/var/spool/mail/pmcewan@somewhere.com, rw) failed: No such file or directory
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): mbox: INBOX defaulted to /var/spool/mail/virtual/pmcewan@somewhere.com/mail/inbox
dovecot: 2008-10-02 23:34:07 Info: POP3(pmcewan@somewhere.com): mbox: root=/var/spool/mail/virtual/pmcewan@somewhere.com/mail, index=/var/spool/mail/virtual/pmcewan@somewhere.com/mail, inbox=/var/spool/mail/virtual/pmcewan@somewhere.com/mail/inbox
dovecot: 2008-10-02 23:34:07 Info: pop3-login: Login: user=<pmcewan@somewhere.com>, method=PLAIN, rip=192.168.5.27, lip=192.168.100.33
dovecot: 2008-10-02 23:34:07 Error: POP3(pmcewan@somewhere.com): mkdir_parents(/var/spool/mail/virtual/pmcewan@somewhere.com/mail/.imap/INBOX) failed: Permission denied
dovecot: 2008-10-02 23:34:07 Error: POP3(pmcewan@somewhere.com): open() failed with mbox file /var/spool/mail/virtual/pmcewan@somewhere.com/mail/inbox: Permission denied
dovecot: 2008-10-02 23:34:07 Error: POP3(pmcewan@somewhere.com): Couldn't init INBOX: Can't sync mailbox: Messages keep getting expunged
dovecot: 2008-10-02 23:34:07 Error: POP3(pmcewan@somewhere.com): Sending log messages too fast, throttling..
dovecot: 2008-10-02 23:34:08 Info: auth(default): new auth connection: pid=21780
dovecot: 2008-10-02 23:34:08 Info: POP3(pmcewan@somewhere.com): Mailbox init failed top=0/0, retr=0/0, del=0/0, size=0

---

