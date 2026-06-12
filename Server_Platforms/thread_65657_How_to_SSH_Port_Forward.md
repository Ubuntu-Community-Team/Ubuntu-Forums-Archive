---
title: "How to SSH Port Forward?"
date: 2005-09-14
forum: Server Platforms
---

### Post by tuxfan99 on 2005-09-14
My web host provides for POP3 through SSL but not SMTP, so I would like to forward SMTP through ssh so that it is encrypted....but I do not know how. Can somebody help me with the exact command to run?
Also, would I just be forwarding port 25 from my local computer to port 25 on the mail server and then tell thunderbird my smtp server is 127.0.0.1:25?

---

### Post by drogoh on 2005-09-14
[QUOTE=tuxfan99]My web host provides for POP3 through SSL but not SMTP, so I would like to forward SMTP through ssh so that it is encrypted....but I do not know how. Can somebody help me with the exact command to run?
Also, would I just be forwarding port 25 from my local computer to port 25 on the mail server and then tell thunderbird my smtp server is 127.0.0.1:25?[/QUOTE]

You don't need to do that, just set up (or have the host set up) TLS for SMTP.

---

### Post by tuxfan99 on 2005-09-14
I cannot and they won't. How can I use ssh port forwarding?

---

### Post by Jussi Kukkonen on 2005-09-14
[QUOTE=tuxfan99]My web host provides for POP3 through SSL but not SMTP, so I would like to forward SMTP through ssh so that it is encrypted....but I do not know how. Can somebody help me with the exact command to run?
Also, would I just be forwarding port 25 from my local computer to port 25 on the mail server and then tell thunderbird my smtp server is 127.0.0.1:25?[/QUOTE]

You need ssh access to a machine in your hoster network (I guess you knew this already):
```
ssh -L 9999:mailserver:110 shellserver
```
where:
[list]9999 is the local port you want to use
[/list][list]mailserver is the smtp machine
[/list][list]110 is SMTP port on mailserver (probably wrong, can't remember)
[/list][list]shellserver is a machine you can ssh into in the same network as mailserver. May be same as mailserver.[/list]

Set your thunderbird  smtp settings to 127.0.0.1:9999. I haven't done this exact tunneling, but it should work...

---

