---
title: "[SOLVED] Windows Mail login to Dovecot Sever?"
date: 2008-07-03
forum: Server Platforms
---

### Post by njparton on 2008-07-03
I've just followed this guidance for setting up a Dovecot server with getmail:

[https://help.ubuntu.com/community/POP3Aggregator](https://help.ubuntu.com/community/POP3Aggregator)

However that guidance conveniently leaves out the detail of how to connect an imap email client (windows mail under vista in my case).

The test user I've created is called 'bob' with a password of 'password1'.  The server's IP address is 192.168.1.10.

The Dovecot daemon starts without error and getmail seems to be working fine.

How do I set up an imap connection to this server in Windows mail?

Using the details above via the accounts wizard in Windows Mail doesn't work.

---

### Post by njparton on 2008-07-03
Got it, didn't have the correct uid for the user mail set in the dovecot config file ](*,)

---

### Post by Bakerconspiracy on 2008-07-03
> The server's IP address is 192.168.1.10
This is an internal address, behind your router.

If you are using postfix, can you post your main.cf and master.cf, I've been having a lot of trouble getting the configuration right.

---

### Post by njparton on 2008-07-09
I've ditched the idea of a mail server as it's too complex and has screwed up my installation.  I've started again with a fresh ubuntu installation so I've lost all the config files, sorry.

---

