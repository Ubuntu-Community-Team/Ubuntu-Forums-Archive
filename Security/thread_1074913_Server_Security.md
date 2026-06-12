---
title: "Server Security"
date: 2009-02-19
forum: Security
---

### Post by ironic1122 on 2009-02-19
How can i have logs sent to me on a daily base and how would i be able to have the server tell me if random user/passwords ( bruteforce ) is happening

---

### Post by cariboo on 2009-02-19
If you have exim and logwatch setup,  you should get a daily email from your server.

Jim

---

### Post by bodhi.zazen on 2009-02-19
> **ironic1122 said:**
> How can i have logs sent to me on a daily base and how would i be able to have the server tell me if random user/passwords ( bruteforce ) is happening

You can do a few simple things to limit brute force attacks.

Most important, enforce strong passwords. Then ...

1. Change the ssh default port from 22 to almost any alternate.

2. Use keys.

3. Install denyhosts, fail2ban, or take a look at a few (dare I say simple) iptables rules.

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

All 3 of those are proactive rather then reactive and all 3 will, IMO, be superior to watching your logs.

---

### Post by ironic1122 on 2009-02-19
/usr/local/etc/logcheck.sh: 269: mail: not found i installed exim4 and its not mailing nothing out

---

### Post by bodhi.zazen on 2009-02-19
> **ironic1122 said:**
> /usr/local/etc/logcheck.sh: 269: mail: not found i installed exim4 and its not mailing nothing out

If you are looking for additional suggestions, may I suggest logwatch ?

[http://ubuntu-tutorials.com/2008/11/13/monitor-system-logs-with-logwatch/](http://ubuntu-tutorials.com/2008/11/13/monitor-system-logs-with-logwatch/)

---

### Post by ironic1122 on 2009-02-19
sorry that link isnt working :(

---

### Post by bodhi.zazen on 2009-02-19
Odd, try the site later perhaps ???

Google ??

[http://beginlinux.wordpress.com/2009/01/09/logwatch-fix-on-ubuntu-810/](http://beginlinux.wordpress.com/2009/01/09/logwatch-fix-on-ubuntu-810/)

---

### Post by ushills on 2009-02-20
If you are problems I wrote a guide here using gmail's smtp servers.

[http://www.ushills.co.uk/2009/02/ssmtp-and-logwatch-email-logs-from.html](http://www.ushills.co.uk/2009/02/ssmtp-and-logwatch-email-logs-from.html)

---

### Post by cariboo on 2009-02-20
You have to configure exim4, you have to tell it where to send the mail. To configure exim4 at the prompt type:

```
sudo dpkg-reconfigure exim4-config
```

You should get a page that looks like the screen-shot.

Jim

---

### Post by ironic1122 on 2009-02-21
thanks for all the fast reply's

---

