---
title: "Help: Serious Ubuntu  Security Flaw"
date: 2012-02-01
forum: Security
---

### Post by Jasonx86 on 2012-02-01
Note to admin/mods: Please do not delete this post or move it to a category where it won't get the attention it deserves.

We have a secure remote Ubuntu 10.04 desktop which has been compromised.

ISSUE: the system has been compromised as it is being used as a name server for the following 46 domains:

46 Nameservers seen on 88.208.229.248:
NS1.GOOGLE-STA.COM
-  google-sta.com

NS1.GOOGLE-STA.NET
- google-sta.net

NS1.GOOGLE-STS.COM
-  google-sts.com

NS1.GOOGLE-STS.NET
- google-sts.net

NS1.MICROSOFT-BS.COM
-  microsoft-bs.com

NS1.MICROSOFT-BT.COM
- microsoft-bt.com

NS1.MICROSOFT-BX.COM
-  microsoft-bx.com

NS1.MICROSOFT-ID.COM
- microsoft-id.com

NS1.MICROSOFT-NB.COM
-  microsoft-nb.com

NS1.MICROSOFT-NI.COM
- microsoft-ni.com

NS1.PAYPAL-ES.COM
-  paypal-es.com

NS1.PAYPAL-ES.NET
- paypal-es.net

NS1.POSTBANK-BX.COM
-  postbank-bx.com

NS1.POSTBANK-DL.COM
- postbank-dl.com

NS1.POSTBANK-ED.COM
-  postbank-ed.com

NS1.POSTBANK-EF.COM
- postbank-ef.com

NS1.POSTBANK-EL.COM
-  postbank-el.com

NS1.POSTBANK-FH.COM
- postbank-fh.com

NS1.POSTBANK-FN.COM
-  postbank-fn.com

NS1.POSTBANK-IN.COM
- postbank-in.com

NS1.POSTBANK-OQ.COM
-  postbank-oq.com

NS1.POSTBANK-VJ.COM
- postbank-vj.com

NS1.POSTBANK-VR.COM
-  postbank-vr.com

NS2.GOOGLE-STA.COM
- google-sta.com

NS2.GOOGLE-STA.NET
-  google-sta.net

NS2.GOOGLE-STS.COM
- google-sts.com

NS2.GOOGLE-STS.NET
-  google-sts.net

NS2.MICROSOFT-BS.COM
- microsoft-bs.com

NS2.MICROSOFT-BT.COM
-  microsoft-bt.com

NS2.MICROSOFT-BX.COM
- microsoft-bx.com

NS2.MICROSOFT-ID.COM
-  microsoft-id.com

NS2.MICROSOFT-NB.COM
- microsoft-nb.com

NS2.MICROSOFT-NI.COM
-  microsoft-ni.com

NS2.PAYPAL-ES.COM
- paypal-es.com

NS2.PAYPAL-ES.NET
-  paypal-es.net

NS2.POSTBANK-BX.COM
- postbank-bx.com

NS2.POSTBANK-DL.COM
-  postbank-dl.com

NS2.POSTBANK-ED.COM
- postbank-ed.com

NS2.POSTBANK-EF.COM
-  postbank-ef.com

NS2.POSTBANK-EL.COM
- postbank-el.com

NS2.POSTBANK-FH.COM
-  postbank-fh.com

NS2.POSTBANK-FN.COM
- postbank-fn.com

NS2.POSTBANK-IN.COM
-  postbank-in.com

NS2.POSTBANK-OQ.COM
- postbank-oq.com

NS2.POSTBANK-VJ.COM
-  postbank-vj.com

NS2.POSTBANK-VR.COM
- postbank-vr.com

I am the only one who has ever accessed this server. How could this happen?

How do we correct this issue? Better yet, how do we remove the name server functionality of Ubuntu?

Any help is appreciated.

---

### Post by bluexrider on 2012-02-01
I fail to understand how this is a Ubuntu problem? Next, isn't a 'name server' just that, a name server? 

If you have a server processing that IP then you could block it.

---

### Post by TheFu on 2012-02-01
Without breaking laws, I can't look at your system from here to help diagnose anything. If you don't need to run a name server (DNS), turn that service off.  However, that probably isn't your security issue.  Someone probably used some other service to hack into your server and has probably owned you for some time.  I'd plan on a complete system rebuild with following best practices for every service that you install and run.  If you have daily backups, you should be able to pinpoint when the break in happened. With that you may be able to determine how much data has been corrupted, if any.

It could be that you are running a name service called "bind". There are other DNS servers too, but bind9 is the most popular. It isn't usually needed for most servers.

This has setup instructions for bind, so you should be able to remove it.
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

I would run a complete port scan on this server if I were you to see what other services you may be providing.  'nmap' is the tool for that - run it from an external machine.

Good luck.

---

### Post by coffeecat on 2012-02-01
> **Jasonx86 said:**
> Note to admin/mods: Please do not delete this post or move it to a category where it won't get the attention it deserves.

Well - I **am** moving it to a more suitable forum where it is **more** likely to get the attention it deserves, and where members expert in security matters are more likely to notice it.

*Thread moved to **Security Discussions**.*

Which has the heading:

> Discuss security flaws/updates/notices in the various Ubuntu releases.

---

### Post by Jasonx86 on 2012-02-01
Thanks for replying.

It's an Ubuntu issue because there are rogue processes responding to dns requests on non standard port numbers i.e. outside port range 6660-7000.

How could this happen and whats the resolution?

---

### Post by rg4w on 2012-02-01
If this happened because of the way Ubuntu server is configured out of the box, it *might* be an Ubuntu problem.

But if the attacker gained control of the system through weak passwords or exploiting anything that was done while setting up the server, it probably isn't an Ubuntu problem.

I'm no expert on such things, but I'd start with the auth.log to see what's been happening.

---

### Post by Dangertux on 2012-02-01
There are a number of ways that this could have happened. They could range from anything from an exploited service, to stolen/harvested/weak credentials. I tend to lean toward weak credentials as there is not much publicly available exploit code that works on 10.04. It is still possible that someone could have found a 0 day vulnerability and developed an exploit however, that doesn't really coincide with the fact that your system is being used as a nameserver for a phishing scam.

If you want more help on HOW your system was compromised, you could start by giving us a list of services that are running (besides the obvious named). Though I tend to believe you probably have weak SSH credentials, VNC or FTP running. Any of that sound accurate?

As far as stopping the DNS server

```

sudo service named stop

```

That being said the individual(s) who compromised the system have root access and yo ureally just need to wipe it and start over.

Best of luck.

---

