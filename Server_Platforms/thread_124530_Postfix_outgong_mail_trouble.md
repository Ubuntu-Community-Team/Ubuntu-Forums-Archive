---
title: "Postfix outgong mail trouble"
date: 2006-02-01
forum: Server Platforms
---

### Post by invalid on 2006-02-01
Hi,

I have postfix set up, and seem to be having trouble sending outgoing mail. It has worked in the past, so I do not know what is going on. It receives mail just fine.

```
Feb  1 17:17:41 MyDomain postfix/smtpd[18157]: connect from MyDomain.net[127.0.0.1]
Feb  1 17:18:23 MyDomain postfix/smtpd[18157]: 9FD4B9180A2: client=MyDomain.net[127.0.0.1]
Feb  1 17:18:33 MyDomain postfix/cleanup[18178]: 9FD4B9180A2: message-id=<20060201221823.9FD4B9180A2@MyDomain.net>
Feb  1 17:18:33 MyDomain postfix/qmgr[17377]: 9FD4B9180A2: from=<beau@MyDomain.net>, size=373, nrcpt=1 (queue active)
Feb  1 17:18:47 MyDomain postfix/smtpd[18157]: disconnect from MyDomain.net[127.0.0.1]
Feb  1 17:19:03 MyDomain postfix/smtp[18183]: connect to mx3.hotmail.com[64.4.50.179]: Connection timed out (port 25)
Feb  1 17:19:33 MyDomain postfix/smtp[18183]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Feb  1 17:20:03 MyDomain postfix/smtp[18183]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Feb  1 17:20:33 MyDomain postfix/smtp[18183]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Feb  1 17:21:03 MyDomain postfix/smtp[18183]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)
```

It does similar for mail hosts other than hotmail as well..
Does anyone know where I should start looking to debug this problem? Any help at all would be greatly appreciated.

Thanks,
Cb

---

### Post by Glut on 2006-02-01
It looks like it can't get a connection to the servers. If you telnet from the machine on port 25 (**telnet mx3.hotmail.com 25**) can you get a connection?

---

### Post by invalid on 2006-02-02
It seems I can not manually connect to the servers listed, including the ones it tried for a gmail account: ```
Feb  1 12:03:27 MyDomain postfix/smtp[15702]: connect to gmail-smtp-in.l.google.com[66.249.83.114]: Connection timed out (port 25)
```among others..

Why is this? Where is it pulling these hosts from in order to connect to them, and why can I not?

---

### Post by Horndog on 2006-02-02
Has It ever worked? If not you probibly have a residentile_Dynamic IP account. Most accounts of this nature have port 25 blocked. The only thing you can do is use you ISP smtp server as a relay.

---

### Post by invalid on 2006-02-02
It has worked in the past, yes. I am very puzzled.

---

### Post by Glut on 2006-02-02
Do you have a firewall, such as iptables, configured? (**sudo iptables -L**)
Have you checked with your ISP to make sure they haven't just changed their policy?
Has your router got a firewall inbuilt?

---

### Post by invalid on 2006-02-02
I have exceptions set up for this traffic to be allowed.

I think I will check with my ISP to see if they have made changes, as I have noticed a few other differences lately as well.

Thanks for the help.

---

### Post by Burke on 2006-02-20
I'm having exactly the same problem. If you've figured it out, could you enlighten me? I'm totally lost :confused:

---

### Post by DB Cooper on 2006-08-29
Did you ever get this fixed?

---

### Post by DB Cooper on 2006-08-30
I think I have a work around

I tried to connect to hotmail on port 25 by IP address for all ips assinged to mx1.hotmail.com.  (These are found by typing in nslookup mx1.hotmail.com for windows and dig mx1.hotmail.com in linux) and typed telnet 65.54.245.8 25 and it connects everytime.  I went on and tried all the addresses and took note which ones worked and which ones did not.  Then edited the hosts file and put in the following lines


65.54.245.8     mx1.hotmail.com
65.54.244.168   mx2.hotmail.com
65.54.244.72    mx3.hotmail.com
65.54.245.104   mx4.hotmail.com

Now I connect to hotmail everytime.

This is not with out problems, if the IPs change the mail to hotmail will stop working.

Anyway if someone finds out what the real problem is let me know.

---

