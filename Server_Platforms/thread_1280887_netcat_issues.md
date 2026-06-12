---
title: "netcat issues"
date: 2009-10-02
forum: Server Platforms
---

### Post by bhart007 on 2009-10-02
While attempting to t-shoot postfix, the article I found ([https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)) says to "netcat localhost 25" however when I do it just sits there and never returns anyhting.  Makes me think that maybe port 25 isnt responding which could be the root of my troubles.  Can anyone tell me what to check to resolve this?

thanks


> allanon@sputnik:~$ netstat -l -n | grep :25
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp6       0      0 :::25                   :::*                    LISTEN    

---

### Post by cdenley on 2009-10-02
Netcat establishes a connection, then pipes STDIN to the server, and the servers responses to STDOUT. If you're connecting to an SMTP server, you need to send it a command. The command doesn't exit until the connection is closed.
```

cdenley@ubuntu:~$ nc localhost 25
220 FGK51F1 ESMTP Postfix (Ubuntu)
EHLO myhostname
250-FGK51F1
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
QUIT
221 2.0.0 Bye

```

---

### Post by bhart007 on 2009-10-02
So all this time its sitting there waiting on a EHLO?  Nope no dice.. i thought it'd automatically give me the 220 header first.. then await commands for a short period?  EHLO hostname does nothing..

---

### Post by cdenley on 2009-10-02
> **bhart007 said:**
> So all this time its sitting there waiting on a EHLO?  Nope no dice.. i thought it'd automatically give me the 220 header first.. then await commands for a short period?  EHLO hostname does nothing..

Well if it fails to connect, I think it would time out, but maybe not by default.
```

nc -z -v -w 5 localhost 25

```

A better way to see if the server is actually listening for connections would be this command
```

sudo lsof -i :25

```

---

