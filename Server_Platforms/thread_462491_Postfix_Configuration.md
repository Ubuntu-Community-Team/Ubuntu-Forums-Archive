---
title: "Postfix Configuration"
date: 2007-06-02
forum: Server Platforms
---

### Post by m u r on 2007-06-02
I am trying to configure postfix as per their instructions ( [https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html) ). Everything seems fine until the end when I test it. 

When I type "telnet mail.example.com 25," I get the following:

```
root@ww2:~# telnet mail.example.com 25
Trying 166.70.145.194...
Connected to mail.example.com.
Escape character is '^]'.
```

If I enter "ehlo mail.example.com" after that, it doesn't do anything.

---

### Post by CaptainMorgan on 2007-06-03
I am having the same problem. However, without a config file or two I don't know if anyone will be much help. Look for mine as I will be posting my config's too, maybe we can compare.

Anyways, what I thought about this is that after it connects it is not loading the smtp_banner found in main.cf, for whatever reason. I went exploring and really consuming the config file and trying to understand it, and of course I am stuck on this too so I got nowhere. 

Anyone have any ideas?
-Capt

PS. Also, tail your syslog and let me know what it says... I want to know if it's reporting the same thing. Do this and then reload and restart /etc/init.d/postfix a few times.
**tail -f /var/log/syslog**

---

### Post by Mr. C. on 2007-06-08
Show your master.cf file and output from postconf -n .

MrC

---

### Post by blippy on 2007-06-15
> **m u r said:**
> When I type "telnet mail.example.com 25," 

Is that the command you typed out literally? If so, then try the following instead:
```
telnet localhost 25
```

I get back
```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 <my_machine_name> ESMTP Postfix (Ubuntu)

```

---

### Post by bmathis on 2007-06-16
Check to make sure you have SASL configured correctly and that it has started and then try again. If you are on the local machine, try localhost.

---

