---
title: "ubuntu stops responding to requests from the internet"
date: 2009-02-20
forum: Server Platforms
---

### Post by yolk on 2009-02-20
Hi.

I have installed openssh and pptpd and correctly set the router up so I can log in to my computer from the internet. It works perfectly as long as I am logged in. After log out and after some time (random) of inactivity the services seem to freeze.

I have tried it on two different machines using hardy, interpid and jaunty alternative CLI only, server and desktop options.

Has anyone experienced anything similar?

Thanks.

---

### Post by cdenley on 2009-02-20
> **yolk said:**
> Hi.

I have installed openssh and pptpd and correctly set the router up so I can log in to my computer from the internet. It works perfectly as long as I am logged in. After log out and after some time (random) of inactivity the services seem to freeze.

I have tried it on two different machines using hardy, interpid and jaunty alternative CLI only, server and desktop options.

Has anyone experienced anything similar?

Thanks.

Are you having problems with openssh or pptpd? I've never had problems with openssh, and I'm currently running a few hardy servers. I've never used pptpd. Is the entire system hanging? Have you ruled out hardware problems?

---

### Post by yolk on 2009-02-20
> **cdenley said:**
> Are you having problems with openssh or pptpd? I've never had problems with openssh, and I'm currently running a few hardy servers. I've never used pptpd. Is the entire system hanging? Have you ruled out hardware problems?

Thank you for the reply. The entire system works great, but it is not accessible from the internet for some reason. When I will do restart is solves the problem. BUT then again after some time I cannot log in. I have tried two different PC's and the problem still exists.

I am starting to think that it may be something wrong with the router configuration but... I have not done anything with it apart from opening some ports. 

Regards.

---

### Post by cdenley on 2009-02-20
When you are unable to connect to the server, is the server able to connect to other hosts over the internet?
```

nc -z -v ubuntu.com 80

```
Is the problem for both WAN and LAN connections?

---

### Post by yolk on 2009-02-20
> **cdenley said:**
> When you are unable to connect to the server, is the server able to connect to other hosts over the internet?
```

nc -z -v ubuntu.com 80

```
Is the problem for both WAN and LAN connections?

When it 'hangs' I can for example open an website and it works great. ubuntu --> internet works great and internet --> ubuntu 'miraculously' is starting to work fine. Also I have noticed that when I will leave it for few hours it 'repairs' itself. To connect to ubuntu I am using an mobile network operator as isp which is in some ways restricted. For example I cannot go to some websites. I am wondering if this could be a problem too?

---

### Post by Yashiro on 2009-02-21
Maybe your network card has some form of power management going on. Hence shutting itself down.

---

### Post by yolk on 2009-02-22
> **Yashiro said:**
> Maybe your network card has some form of power management going on. Hence shutting itself down.

It is possible. It is a shame that it cannot be woken up by the request from the lan. If i'll sort this problem out I'll post the solution. Thanks you all.

---

### Post by yolk on 2009-02-22
I think I found the problem. Computer does not resume connection after my router restarts. Not sure what to do now. I need to ask (but in another post) how to check the interface status and how bring it up if down using scripts.

---

### Post by yolk on 2009-02-22
So I added a very simple script which is starting the interface every few minutes. Seems very primitive but it works :)

---

### Post by yolk on 2009-02-22
> **yolk said:**
> So I added a very simple script which is starting the interface every few minutes. Seems very primitive but it works :)

Just in case if anyone needs it:

create a file for example:

/user/local/bin/file_name

```
#!/bin/bash
# /usr/local/bin/check_wlan0

ifdown wlan0
ifup wlan0

exit
```

chmod +x /user/local/bin/file_name

added line to /etc/crontab

```
*/1 *   * * *   root /usr/local/bin/file_name &> /dev/null
```

and it should connect to AP after router restart.

---

