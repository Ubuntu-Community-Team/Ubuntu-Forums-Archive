---
title: "Suspicious activity or paranoia?"
date: 2011-02-16
forum: Security
---

### Post by Ozmondo on 2011-02-16
Hi all,

I have a dedicated server and have a couple of questions regarding some changes i've noticed. 

1) I sometimes use the server as a proxy from work. When i do, any search i do in google is done by google.com.hk - i asked the host company and they said that this happens when the proxy is in that country, which is odd since the hosting company is in the UK.

2) Mysql is outputting everything as XML. If i do show status, the output looks like this

 <row>
        <field name="Variable_name">Uptime_since_flush_status</field>
        <field name="Value">500725</field>
  </row>

Im also pretty sure that hasn't always done that.

I have the feeling that the server has been compromised but don't want to do a full rebuild on a "hunch" as i've just got things stable and fast.

Any advice gratefully acccepted.

---

### Post by Monotoko on 2011-02-16
Hi Ozmondo, 

As a fellow dedicated server owner, how do you manage SSH and what daemons do you run? If you manage SSH through password are all of your accounts secure, and is the MySQL root account secure? Finally is your system completly up to date?

I would also poke around /var/log and see if you can turn anything up, don't worry about attempted break ins as they happen all the time.

---

### Post by Ozmondo on 2011-02-16
Thanks for the swift reply...

I've just checked for updates and was shown the following. I'm scared to death of updating the kernel as last time the system wouldn't boot and i had to rebuild.

>     
grub-common     GRand Unified Bootloader, version 2 (common files)     New version 1.96+20080724-12ubuntu2.1     Jaunty-updates
    libpq5     PostgreSQL C client library     New version 8.3.12-0ubuntu9.04     Jaunty-security
    linux-image-2.6.28-19-generic     Linux kernel image for version 2.6.28 on x86/x86_64     New version 2.6.28-19.66     Jaunty-security
    openssl     Secure Socket Layer (SSL) binary and related cryptographic tools     New version 0.9.8g-15ubuntu3.6     Jaunty-security
    tzdata     time zone and daylight-saving time data     New version 2010m~repack-0ubuntu0.9.04     Jaunty-updates
    update-manager-core     manage release upgrades     New version 0.111.10     Jaunty-updates



I am accessing ssh using password, not sure how i ensure my accounts are secure - i have been through the users file and dont see anything out of place... I have run chkrootkit and rkhunter and they both find nothing.

My mysqldump backups are outputting in xml too :(

---

### Post by Monotoko on 2011-02-16
Hi Ozmondo,

No problem at all, do you have direct access to the machine? What I mean by secure passwords is alphanumeric passwords with symbols of more than 8 characters. You should also look at using key based authentication as it is a lot more secure. (as long as you don't hand the key out.)

Is MySQL used with any PHP websites? it could be possible that someone has done an injection attack through the website.

---

### Post by Ozmondo on 2011-02-16
> **Monotoko said:**
> Hi Ozmondo,

No problem at all, do you have direct access to the machine? What I mean by secure passwords is alphanumeric passwords with symbols of more than 8 characters. You should also look at using key based authentication as it is a lot more secure. (as long as you don't hand the key out.)

Is MySQL used with any PHP websites? it could be possible that someone has done an injection attack through the website.

Thanks again for the reply, i'll look into key based authentication. Yes, the site hosts a busy forum. How would i check for a sql injection?

---

### Post by Monotoko on 2011-02-16
You will want to check the general SQL logs, as well as the logs for the forum software: [http://dev.mysql.com/doc/refman/5.0/en/query-log.html](http://dev.mysql.com/doc/refman/5.0/en/query-log.html)

As for redirecting to the Hong Kong Google site, you might want to go to: [http://www.whatismyip.com](http://www.whatismyip.com) while you are using the proxy and ensure that it matches the server IP. (Someone could be doing something nasty and redirecting you)

If so, you will also want to do an IP lookup: [http://ip-lookup.net/](http://ip-lookup.net/) which should show you what country the IP address is registered to, and give you some whois information.

---

