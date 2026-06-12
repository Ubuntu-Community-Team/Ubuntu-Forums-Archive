---
title: "can't find /etc/postfix/sasl/smtpd.conf"
date: 2008-08-10
forum: Server Platforms
---

### Post by gishaust on 2008-08-10
hi everyone,

I have been following this howto on setup up postfix, and I am using ubuntu server 8.04 text prompt only.

```
https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto

```

Everything went well except the following  file I cannot find
```
 /etc/postfix/sasl/smtpd.conf 
```

If I 

```
find / -name smtpd.conf 
```

I get no response.

I have smtpd installed I think. I do the following command and I get response I am assuming that this is the smtpd daemon!
```

 /etc/init.d/saslauthd restart
* Stopping SASL Authentication Daemon saslauthd              [ OK ]
* Stopping SASL Authentication Daemon saslauthd              [ OK ]

```


So does anyone know where smtpd.conf is??

gishaust

---

### Post by gishaust on 2008-08-11
the answer to this that you have to create the file yourself. It seems that some tutorials don't tell you this. I used the following url

[HTML]
http://www.jimmy.co.at/weblog/?p=52
[/HTML]

---

