---
title: "Courier 993 connection closed problems"
date: 2015-07-22
forum: Server Platforms
---

### Post by Heeter on 2015-07-22
Hi all,

I am currently running a 14.04 LAMP with postfix and courier. This setup has been working flawlessly since I built it when 14.04 came out, other than server updates, I haven't changed anything in the configuration since building the server.

But, alas, I started having issues with my Android device using K9 mail last Friday. It wasn't connecting to the server and retrieving any mail.

The is the result when I run telnet:
```

root@server1:/home/adminpc# telnet localhost 993
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
Connection closed by foreign host.
root@server1:/home/adminpc# 

```

And this is the result when I run opensslclient:
```

root@server1:/home/adminpc# openssl s_client -connect localhost:993
CONNECTED(00000003)
write:errno=104
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 0 bytes and written 295 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
---
root@server1:/home/adminpc# 

```

I have deleted the "/etc/courier/imapd.pem" & the "/usr/lib/courier/imapd.pem" files and recreated the keys a few times already:
```

root@server1:/home/adminpc# mkimapdcert
/usr/lib/courier/imapd.pem already exists.
root@server1:/home/adminpc# 

```

I restarted courier imap a few times as well
```

root@server1:/home/adminpc# service courier-imap restart
 * Stopping Courier IMAP server imapd                                    [ OK ] 
 * Starting Courier IMAP server imapd                                    [ OK ] 
root@server1:/home/adminpc# service courier-imap-ssl restart
 * Stopping Courier IMAP-SSL server imapd-ssl                            [ OK ] 
 * Starting Courier IMAP-SSL server imapd-ssl                            [ OK ] 
root@server1:/home/adminpc# 

```

but the connection to 993 is always closed (refused)

I am at a loss right now,

Any help would be greatly appreciated,

Regards

Heeter

---

