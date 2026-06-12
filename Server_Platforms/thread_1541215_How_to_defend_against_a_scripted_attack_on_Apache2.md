---
title: "How to defend against a scripted attack on Apache2?"
date: 2010-07-28
forum: Server Platforms
---

### Post by someoney3000 on 2010-07-28
I have a LAMP server that has been up for a month or so before I get stuff like this:

```
60.12.233.54 - - [24/Jul/2010:22:46:07 -0400] "GET /w00tw00t.at.blackhats.romanian.anti-sec:) HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:10 -0400] "GET /scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:16 -0400] "GET /admin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:19 -0400] "GET /admin/pma/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:21 -0400] "GET /admin/phpmyadmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:24 -0400] "GET /db/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:27 -0400] "GET /dbadmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:29 -0400] "GET /myadmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:32 -0400] "GET /mysql/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:35 -0400] "GET /mysqladmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:41 -0400] "GET /phpadmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:44 -0400] "GET /phpMyAdmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:47 -0400] "GET /phpmyadmin/scripts/setup.php HTTP/1.1" 404 881 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:49 -0400] "GET /phpmyadmin1/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:55 -0400] "GET /pma/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:46:58 -0400] "GET /web/phpMyAdmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:00 -0400] "GET /xampp/phpmyadmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:06 -0400] "GET /php-my-admin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:12 -0400] "GET /websql/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:19 -0400] "GET /phpmyadmin/scripts/setup.php HTTP/1.1" 404 881 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:22 -0400] "GET /phpMyAdmin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:29 -0400] "GET /phpMyAdmin-2/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
60.12.233.54 - - [24/Jul/2010:22:47:35 -0400] "GET /php-my-admin/scripts/setup.php HTTP/1.1" 404 895 "-" "ZmEu"
Etc.
```

Is this a scripted attack?  If it is, are there any ways to defend against it?  What are the dangers of this attack?

I didn't think a simple web server could be hack through url manipulation.

Thank you for your time.

---

### Post by llamabr on 2010-07-28
Besides the fact that they're annoying, and slow down your network in the middle of a work day, I usually ignore them.

Interestingly, although unsurprisingly, you're getting attacked from china.  It'll stop around 5PM or so, china time, when they leave work for the day:
```

% [whois.apnic.net node-1]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

inetnum:      60.12.0.0 - 60.12.255.255
netname:      UNICOM-ZJ
descr:        China Unicom Zhejiang province network
descr:        China Unicom
country:      CN
admin-c:      CH1302-AP
tech-c:       JQ16-AP
remarks:      service provider
mnt-by:       APNIC-HM
mnt-lower:    MAINT-CNCGROUP-ZJ
mnt-routes:   MAINT-CNCGROUP-RR
status:       ALLOCATED PORTABLE
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
remarks:      This object can only be updated by APNIC hostmasters.
remarks:      To update this object, please contact APNIC
remarks:      hostmasters and include your organisation's account
remarks:      name in the subject line.
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
changed:      hm-changed@apnic.net 20040629
changed:      hm-changed@apnic.net 20060124
changed:      hm-changed@apnic.net 20090507
changed:      hm-changed@apnic.net 20090508
source:       APNIC

route:        60.12.0.0/16
descr:        CNC Group CHINA169 Zhejiang Province Network
country:      CN
origin:       AS4837
mnt-by:       MAINT-CNCGROUP-RR
changed:      abuse@cnc-noc.net 20060118
source:       APNIC

person:       ChinaUnicom Hostmaster
nic-hdl:      CH1302-AP
e-mail:       abuse@chinaunicom.cn
address:      No.21,Jin-Rong Street
address:      Beijing,100140
address:      Beijing,100140
address:      P.R.China
phone:        +86-10-66259940
fax-no:       +86-10-66259764
country:      CN
changed:      abuse@chinaunicom.cn 20090408
mnt-by:       MAINT-CNCGROUP
source:       APNIC

person:       Jianhuaq Qian
nic-hdl:      JQ16-AP
e-mail:       chenrenhai@china-netcom.com
address:      No 1,Hangzhou University Road,Hangzhou, Zhejiang,China
phone:        +86-571-28868063
fax-no:       +86-571-28868069
country:      CN
changed:      wuhong@china-netcom.com 20050421
mnt-by:       MAINT-CNCGROUP-ZJ
source:       APNIC
```

---

### Post by lisati on 2010-07-28
I've had similar "attacks" on my system, but haven't noticed any damage so far. 

One of the things I've done is to install mod-defensible on my server. It won't keep out all the rogues, but it can help.

There are also PHP scripts available that can be used on pages where you might want a slightly different set of criteria to what mod-defensible uses.

---

### Post by someoney3000 on 2010-07-29
> **llamabr said:**
> 
Interestingly, although unsurprisingly, you're getting attacked from china.  It'll stop around 5PM or so, china time, when they leave work for the day:


Funny.  Is attacking web servers their job?

Thank you for all your comments.  I took a look at mod-defensible before, but wasn't sure if that was the solution for Ubuntu.

Thanks!

---

### Post by jmuggins on 2010-09-13
> **someoney3000 said:**
> Funny.  Is attacking web servers their job?


I have every netblock (that I know of) from China and Korea blocked, because it **does** appear to be their goal in life.

I also block requests based on the UA string. If it uses IE6 or lower, they don't get in. Too bad some IT departments are so wedded to MS's broken products, but that's tough if I lose a few hits. Most attack or spam attempts on my site are robots, and that stops them for the most part.

---

### Post by endotherm on 2010-09-13
> **someoney3000 said:**
> Funny.  Is attacking web servers their job?

Thank you for all your comments.  I took a look at mod-defensible before, but wasn't sure if that was the solution for Ubuntu.

Thanks!
it at the very least appears to be a popular hobby, if not a day job.
[http://www.foreignpolicy.com/articles/2010/03/03/china_s_hacker_army](http://www.foreignpolicy.com/articles/2010/03/03/china_s_hacker_army)

---

### Post by junke1990 on 2010-09-13
or you could check out fail2ban and make it dynamic so only the bad guys get blocked?

---

