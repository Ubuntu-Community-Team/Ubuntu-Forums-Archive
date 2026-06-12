---
title: "Connection dropped by IMAP server."
date: 2011-09-12
forum: Server Platforms
---

### Post by sastagi on 2011-09-12
I set up Ubuntu Server 11.04, Postfix, courier imap and Squirrel mail on an old laptop of mine. I use putty to connect to my old laptop through a new one. So as long as I am connected to my old laptop using Putty, I can check email using squirrel mail on the new laptop. If, I close the Putty session and try to access my email, I get the error:

"Connection dropped by IMAP server"

any idea how to fix this issue.

---

### Post by Dangertux on 2011-09-12
Is your mail folder in your home folder? And did you choose to encrypt your home folder?

---

### Post by sastagi on 2011-09-12
Yes, my mail folder is in my home folder and I didn't encrypt my home folder.

---

### Post by Dangertux on 2011-09-12
Two things.

Can you verify that user mail (when you're not connected via PuTTY) is actually being delivered to ~/username/mail. Also you need to check and see if it's going to /var/mail instead.

Also, can you post the results after you get the error of 

```

tail -n 15 /var/log/mail.log

```

---

### Post by sastagi on 2011-09-13
Thank you for helping out. Here is what happened:

1. When I tried to send a mail, I got a bounce back saying mail could not be delivered. I do not have a ~/username/mail folder but a ~/username/Maildir folder ( and it has the cur, tmp and new) folders.

2. I ran your command and here is what I got (replaced the name of my website with "mywebsite":

Sep 12 21:20:53 mywebsite imapd: Connection, ip=[::ffff:127.0.0.1]
Sep 12 21:20:53 mywebsite imapd: LOGIN, user=santosh, ip=[::ffff:127.0.0.1], port=[54506], protocol=IMAP
Sep 12 21:20:53 mywebsite imapd: LOGOUT, user=santosh, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=46, sent=336, time=0
Sep 12 21:20:54 mywebsite imapd: Connection, ip=[::ffff:127.0.0.1]
Sep 12 21:20:54 mywebsite imapd: LOGIN, user=santosh, ip=[::ffff:127.0.0.1], port=[54507], protocol=IMAP
Sep 12 21:20:54 mywebsite imapd: LOGOUT, user=santosh, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=419, sent=1528, time=0
Sep 12 21:20:54 mywebsite imapd: Connection, ip=[::ffff:127.0.0.1]
Sep 12 21:20:54 mywebsite imapd: LOGIN, user=santosh, ip=[::ffff:127.0.0.1], port=[54508], protocol=IMAP
Sep 12 21:20:54 mywebsite imapd: LOGOUT, user=santosh, ip=[::ffff:127.0.0.1], headers=782, body=0, rcvd=297, sent=2655, time=0
Sep 12 21:20:58 mywebsite imapd: Connection, ip=[::ffff:127.0.0.1]
Sep 12 21:20:58 mywebsite imapd: LOGIN, user=santosh, ip=[::ffff:127.0.0.1], port=[54509], protocol=IMAP
Sep 12 21:20:58 mywebsite imapd: LOGOUT, user=santosh, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=87, sent=391, time=0
Sep 12 21:22:38 mywebsite postfix/anvil[26285]: statistics: max connection rate 1/60s for (smtp:209.85.161.46) at Sep 12 21:18:45
Sep 12 21:22:38 mywebsite postfix/anvil[26285]: statistics: max connection count 1 for (smtp:209.85.161.46) at Sep 12 21:18:45
Sep 12 21:22:38 mywebsite postfix/anvil[26285]: statistics: max cache size 1 at Sep 12 21:18:45


Thank you again so much for you help. You may have figured by now, I am a complete newbie :-).

---

### Post by sastagi on 2011-09-13
Just to let you know, I have not resolved the issue. I still have the issue. any pointers as to what I need to do?

---

