---
title: "How many connections can XAMPP handle?"
date: 2010-07-23
forum: Server Platforms
---

### Post by syb3ria on 2010-07-23
Hello all, i would like to know how many connections per sec/min/hour, xampp can handle. I'm going to run SMF forum on my box, because i'm not ready yet with real server solution. System stats are: G31M-S2C; 2x2GB Kingston@920Mhz; E5200@3500Mhz; 500GB@7200 Seagate, all powered by Lucid x64. In a time i will migrate to a quad, mobo with raid support, etc. but at that point i'm want to know how much connections can xampp handle. Because of the forum nature, i think of auto deleting topics witn no new replys in 5 days for saving place (there will be minimum 1 and maybe max 5 photos per thread, maximum size 2Mb for each). Thank you in advance for your time :)

---

### Post by clrg on 2010-07-23
XAMPP? I hope you mean LAMPP.

Apache can handle as much connections as the hardware supports. There is no magic formula to calculate this based on your hardware; it depends on what the user does. If every user runs a SELECT in your database, the load will be very high. If everyone just requests some KBs of HTML, the load will be lower. 

The best way to estimate the performance is to test it.

---

### Post by syb3ria on 2010-07-23
I run XAMPP, not linux poweruser, actually i just left behind win7 like an month :) I know there is no magic formula but asked hoping someone might have/had an observation on situation close to mine. In the begginng around 40% of all users will use the database, rest will be just browsing. So you recommend me remove xampp and manually install and configure Apache etc?

---

### Post by clrg on 2010-07-23
Nope. I'm no expert for webservers, but LAMPP means Linux, Apache, MySQL, PHP and Perl. XAMPP is the same, without the Linux part. That's what confused me.

I don't think you'll have any performance issues (as long as you don't have hundreds of thousands of requests per minute). If you do, you'll find out soon enough (have a look at iostat, vmstat, /proc/loadavg and top).

---

### Post by annavlad on 2010-08-03
this will help you [http://www.edonline.ro/mod/resource/view.php?id=69](http://www.edonline.ro/mod/resource/view.php?id=69)

---

