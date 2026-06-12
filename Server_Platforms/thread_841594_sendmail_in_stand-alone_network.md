---
title: "sendmail in stand-alone network"
date: 2008-06-26
forum: Server Platforms
---

### Post by serialbumpy on 2008-06-26
I installed a LAMP (linux apache mysql php) package onto my server machine (Solaris actually). That's all up and running fine.

Trying to send mail from a php script via the 'mail()' method to a Windows 2003 Pop3 Mail Server. I'm quite sure the php script is working ok, but the sendmail executed by the server always bombs out with the message:

> ...unable to resolve my own domain name

then

> ...using short name

I've checked /etc/hosts and /etc/inet/ipnodes for possible problems, but both of these contain the line:

```
MY_IP     MY_HOST_NAME   Loghost
```

where MY_IP and MY_HOST_NAME are stand for their corresponding real values.

I've tried at the command line:

```
sendmail USER@WINDOWS_IP
test
test
test
.
```



This is a stand-alone network; no internet access or DNS. Any suggestions?

---

### Post by Titan8990 on 2008-06-26
I do not know much about php but I do know that you can not "send" mail via POP3. POP3 is the protocol used to download email from a server. You need to use SMTP or one of its varients.

---

