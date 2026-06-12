---
title: "bind9 config help"
date: 2007-07-22
forum: Server Platforms
---

### Post by Robx610 on 2007-07-22
I have installed Ubuntu Server Edition 6.04 on a spare computer. The services that are installed and running are: Apache2, PHP5, MYSQL, FTP, Open SSH, and finally BIND9.

I installed Bind using APT GET and began configuring it according to the documentation. My internetwork IP is 10.0.1.0 with a 255.255.255.0 mask, my server is named lamp, and I would like to have it be the authoritative DNS for the domain serowik.local and host my websites. I would also like to add my xp machine to the domain. After hours of work and fumbling around with the configs I am still unable to get this running properly.

Below are my configs, if anyone can help me out and tell me what I'm doing wrong, that would be great.

Lamp = Server name
Desk = XP machine (client)




*/etc/bind/named.conf *

// Add local zone definitions here.

zone "serowik.local" {
             type master;
             file "db.serowik.local";
             notify no;
        };




*/var/cache/bind/db.serowik.local*

;
; BIND data file for local loopback interface
;
$TTL    1D

@ 1d IN SOA lamp.serowik.local. rserowik.gmail.com. (
13              ; Serial
43200           ; Refresh
900             ; Retry
604800          ; Expire
10800           ; Negative Cache TTL
)
@ IN NS 127.0.0.1
A 127.0.0.1

www IN CNAME lamp
desk IN A 10.0.1.10
;




*/etc/bind/named.conf.local *

zone "serowik.us" {
             type master;
             file "/etc/bind/db.serowik.us";
        };

---

### Post by HermanAB on 2007-07-22
Well, you sure are courageous.  Nine times out of ten, if it won't work, it is due to a missing dot.  Nowadays I am too lazy to set up a DNS from scratch - I use Mandriva and click through their DNS wizard.  You only have to answer about 3 questions and then it works!

Here is a good DNS example which I have used in the past:
[http://tldp.org/HOWTO/DNS-HOWTO-7.html](http://tldp.org/HOWTO/DNS-HOWTO-7.html)

'Hope that helps!

Herman

---

### Post by Robx610 on 2007-07-22
Hey Herman, thanks for the response. I actually have a Mandriva disk but never installed it. The PC I'm using as my server is only a 450 P3 with 256 RAM so a GUI would kill the processor with overhead.  I read over the sample configs but I'm having a hard time seeing how my syntax is wrong.

---

### Post by darkog on 2007-07-22
try this. and watch the messages as you start up named. make sure the files exist. 

your server still needs an ip addy. so lets say servr ip = 10.0.0.5

in server, your resolv.conf make sure it has 0.0.0.0

```

zone "serowik.local" {
             type master;
             file "/etc/bind/db.serowik.local";
             notify no;
        };

```

```

$TTL    1D

@   1d       IN      SOA          lamp.serowik.local.      rserowik.gmail.com.    (
                   13              ; Serial
                   43200           ; Refresh
                   900             ; Retry
                   604800          ; Expire
                    10800           ; Negative Cache TTL
)

@                IN                        NS            ns.serowik.local.
lamp           IN                         A              10.0.0.5

www           IN                        CNAME     lamp.serowik.local.
ns              IN                        CNAME     lamp.serowik.local.

desk           IN                       A                 10.0.1.10

```

---

### Post by Mr. C. on 2007-07-22
The " rserowik.gmail.com." is the email address, where . replaces an @ sign.  There is nothing wrong with that portion of the statement.  It is typically the email address of the name server admin.

There is no point to using 0.0.0.0 as a nameserver.  If DNS is running on the local server, 127.0.0.1 is sufficient.

Here's a DNS lab and coursework notes I used to give to students. See week 8 DNS: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by darkog on 2007-07-23
different theories abound.

> A nameserver specification of 0.0.0.0 is actually a shortcut for querying a local name server
using the first IP address that was assigned to the local system. This is the loopback address,
which is usually 127.0.0.1, but is not guaranteed to be. Using the shortcut 0.0.0.0 causes your request
to be sent to an IP address that is known to be valid for the current host, whatever it may be.

---

### Post by Mr. C. on 2007-07-23
> **darkog said:**
> the first IP address that was assigned to the local system

Define "first".

MrC

---

### Post by Robx610 on 2007-07-23
thanks for your help guys, but for some reason i still can't get it to work, even with darkog's code :(

---

### Post by Mr. C. on 2007-07-23
Please don't reply with "i can't get it to work" messages - they are entirely useless.

Show your actual commands you use to test, their output, and the relevant log messages which may indicate any failure.

MrC

---

### Post by Robx610 on 2007-07-23
**To be completely honest, I am not familiar enough with linux to know which logs to read. When I did set up the configs the way darkog specified and used the bind as my dns for my xp machine It did not work properly. The dns resolves all public websites on the internet but, I tried to access my webpage by typing in my browser: [www.serowik.local](www.serowik.local), this failed, I also tried lamp.serowik.local, this also did not work. I then tried to join my domain on my XP client and received this error message:**

Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\WINDOWS\debug\dcdiag.txt.

The following error occurred when DNS was queried for the service location (SRV) resource record used to locate a domain controller for domain serowik.local:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.serowik.local

Common causes of this error include the following:

- The DNS SRV record is not registered in DNS.

- One or more of the following zones do not include delegation to its child zone:

serowik.local
local
. (the root zone)

For information about correcting this problem, click Help.

Let me know what other methods I can use to troubleshoot.

**I also ran nslookup from my XP client, here are my results:**

C:\Documents and Settings\Rob>nslookup 10.0.1.100
DNS request timed out.
    timeout was 2 seconds.
*** Can't find server name for address 10.0.1.100: Timed out
*** Default servers are not available
Server:  UnKnown
Address:  10.0.1.100

*** UnKnown can't find 10.0.1.100: Non-existent domain

C:\Documents and Settings\Rob>nslookup [www.serowik.local](www.serowik.local)
*** Can't find server name for address 10.0.1.100: Non-existent domain
*** Default servers are not available
Server:  UnKnown
Address:  10.0.1.100

Name:    lamp.serowik.local
Address:  10.0.0.100
Aliases:  [www.serowik.local](www.serowik.local)

**Let me know what other methods I can use to troubleshoot.**

---

### Post by darkog on 2007-07-23
can you opena terminal window and type this command from the ubuntu sevrver and post here.

```
sudo cat /var/log/messages | grep named 
```

try this for lookup from the xp machine. the ip address lookup wont work until you set ptr records.
```


> nslookup
> server (your dns server ip)
> lamp.serowik.local.


```

---

### Post by Mr. C. on 2007-07-23
Ok, let's get to the issue.

Use **dig** to test your DNS server from the server host itself.  Don't use a browser or other GUI like app to run your tests (some cache results!).

Go to your server, and run the command line:

```
dig lamp.serowik.local
dig serowik.local

```

What are the results.?

Check your /var/log/messages and /var/log/syslog as well.

MrC

---

### Post by Robx610 on 2007-07-23
**For Darkog:**

I executed sudo cat /var/log/messages | grep named, nothing happened. I read the log file in its entirety with pico anyway and it didn't say anything in refrence to bind or named.

I ran nslookup as you said, here are the results:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Rob>nslookup
DNS request timed out.
    timeout was 2 seconds.
*** Can't find server name for address 10.0.1.100: Timed out
*** Default servers are not available
Default Server:  UnKnown
Address:  10.0.1.100

>
>
> server 10.0.1.100
Default Server:  [10.0.1.100]
Address:  10.0.1.100

>
>
> lamp.serowik.local
Server:  [10.0.1.100]
Address:  10.0.1.100

Name:    lamp.serowik.local
Address:  10.0.0.100

>

**For Mr.C**

_Ran dig lamp.serowik.local:_

; <<>> DiG 9.3.2 <<>> lamp.serowik.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21701
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;lamp.serowik.local.            IN      A

;; ANSWER SECTION:
lamp.serowik.local.     86400   IN      A       10.0.0.100

;; AUTHORITY SECTION:
serowik.local.          86400   IN      NS      lamp.serowik.local.

;; ADDITIONAL SECTION:
lamp.serowik.local.     86400   IN      A       10.0.0.100

;; Query time: 4 msec
;; SERVER: 10.0.1.100#53(10.0.1.100)
;; WHEN: Mon Jul 23 16:40:15 2007
;; MSG SIZE  rcvd: 82

_Ran dig serowik.local_

; <<>> DiG 9.3.2 <<>> serowik.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14694
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;serowik.local.                 IN      A

;; AUTHORITY SECTION:
serowik.local.          10800   IN      SOA     lamp.serowik.local. rserowik.gmail.com. 17 43200 900 604800 10800

;; Query time: 4 msec
;; SERVER: 10.0.1.100#53(10.0.1.100)
;; WHEN: Mon Jul 23 16:43:12 2007
;; MSG SIZE  rcvd: 90

_Sys log (entry repeats)_
Jul 23 12:05:15 lamp -- MARK --
Jul 23 12:09:01 lamp /USR/SBIN/CRON[5512]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 23 12:15:15 lamp named[5259]: Cleaned cache of 7 RRsets
Jul 23 12:15:15 lamp named[5259]: USAGE 1185207315 1185182115 CPU=0.18u/0.08s CHILDCPU=0u/0s
Jul 23 12:15:15 lamp named[5259]: NSTATS 1185207315 1185182115 A=109 SRV=2
Jul 23 12:15:15 lamp named[5259]: XSTATS 1185207315 1185182115 RR=326 RNXD=35 RFwdR=125 RDupR=0 RFail=0 RFErr=55 RErr=0 RAXFR=0 RLame=0 ROpts=0 SSysQ=88 SAns=103 SFwdQ=76 SDupQ=171 SErr=15 RQ=111 RIQ=0 RFwd$
Jul 23 12:17:01 lamp /USR/SBIN/CRON[5522]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jul 23 12:39:01 lamp /USR/SBIN/CRON[5524]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 23 13:05:16 lamp -- MARK --


thats about it

---

### Post by Robx610 on 2007-07-23
by the way,  i can access my website through the browser in XP by using the addy [http://lamp](http://lamp). Thats the only way it works.

---

### Post by Mr. C. on 2007-07-23
Ok, so your nameserver is returning results :


```
;; ANSWER SECTION:
lamp.serowik.local. 86400 IN A 10.0.0.100

```

I would like to recommend that you stop wasting your time using random applications to "test" your DNS server.  Until you can reliable obtain results with dig, other apps only add additional complexity to the equation.  The dig and nslookup utilities were designed for this, but nslookup is essentially obsoleted.

Demonstrate that you can obtain all the translations you expect, using:

```
dig +short *name*
```

replacing *name* with each name you want translated.  For IP->hostname, test your PTR records with:

```
dig +short -x *IP*
```

replacing *IP* with each IP address you want translated. 

Once this is done, *then* go about configuring your other boxes to use your newly configured name server.  If you see failures on your XP box, then show the output from an XP command window of:

```
ipconfig /all
```

MrC

---

### Post by murraymca on 2007-07-23
Hi,

I had a whole lot of trouble when setting up bind for myself the first time, I wrote a paper and presentaiton on it which I can email you if you like - no matter how hard I tried I could not get anyone elses configurations to work.  By the way, big kudo's for negative caching time - seems to be a lot who don't realise that the minimum time in BIND 9 is now the negative cache time.  First off, you want to be authoritative for serowik.local but in your SOA you have lamp.serowik.local.

Am I correct in saying that will make you authoritative for the subdomain/zone lamp.serowik.local?  I would make the following changes to db.serowik.local:

$TTL 1D
@ IN SOA serokwik.local serowik.gmail.com.
;serials etc

@ IN NS lamp.serokwik.local 
localhost IN A 127.0.0.1
lamp IN A ip_address_of_map_machine
www IN CNAME lamp

I put an A record for LAMP in since I put that as the NS and since it's in your domain you need the glue record...or at least an A record (I can't remember all the talk about glue records when dealing with subdomains etc)!

With regards to logging, put this into a file and save it as say..."logging", then in named.conf use:
include "/path/to/logging";
(but not in the options section...say just above your first zone.  The "/etc/bind/bind.log" is where the log file will be written to, you should change this to where you want.

logging*{
**channel*simple_log*{
****file*"/etc/bind/bind.log"*versions*3*size*5m;
****print*time*yes;
****print*severity*yes;
****print*category*yes;
**};
**category*default*{
****simple_log;
**};
};

it should log everything, do say an rndc reload and (in my case) cat /etc/bind/bind.log.  You can tune this how you like, with instructions at:  [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)  
Or you could just reload, then tail /var/log/syslog.  By the way, [http://www.zytrax.com/books/dns/](http://www.zytrax.com/books/dns/) is an invaluable resource when starting out!

Could you please post your named.conf?  I recommend if you haven't already, add things like allow-recursion {subnet;}; and allow-query {subnet;};

With regards to adding XP, I'm thankful I'm out of my last job and dont' have to touch windows again, but I'm not sure if you can "add it to the domain" as you would like, but you will have no troubles using your DNS server with it...I think you need samba etc to 'add it to the domain' which is well beyond me.

Let me know if you would like to look at my talk and presentation, I'd love to know if it actually helps someone else or if it's as hard to follow as all the tutorials I found when starting off.

Please let me know how you go!

Hope some of this helps.

Regards.

---

### Post by Robx610 on 2007-07-23
Mr.C

dig +short -x IP
 
and dig + short name

returned no results

---

### Post by Mr. C. on 2007-07-23
Huh ?

Earlier you verified that dig returned at least one result:

> Ran dig lamp.serowik.local: ...
lamp.serowik.local. 86400 IN A 10.0.0.100

Are you using **name** and **IP** literally, or replacing those placeholders with all your possible hostname and IPs ?  If the latter, you're going to have to show all your relevant bind config files.

MrC

---

### Post by Robx610 on 2007-07-23
Mr.C

I tried:

dig +short lamp
dig +short -x 10.0.1.100

and it returned no results whatsoever, am i misinterpreting the usage of these commands?

and you are right, dig lamp.serowik.local works

Im puzzled.

---

### Post by Mr. C. on 2007-07-24
```
cat /etc/resolv.conf
```

So you only have one hostname  and IP address ?

MrC

---

### Post by Robx610 on 2007-07-24
My resolv.conf looks as such:

searchsearch serowik.local
nameserver 10.0.1.100

---

### Post by Mr. C. on 2007-07-24
Ok.

First, change the contents of your /etc/resolv.conf to the following:

```
domain serowik.local
```

You don't need a nameserver line, as when you are running bind locally, the resolver knows to query localhost.

You don't need name searching features for such a simple setup.

So here's the deal...

The dig command does not add your domain name from /etc/resolv.conf, whereas nslookup does.  You can verify this for yourself.

```
dig +short lamp
nslookup lamp
```

The first one will not provide an answer because there is no hostname in the root domain called "lamp". Tthe second command should succeed because nslookup will add your domain to the end of the unqualified hostnamel.  Other commands also use the system resolver, so they too will tack on the domain name to unqualified (eg. simple) hostnames:

```
ping lamp
ping lamp.serowik.local
```

Both of these commands should succeed with name translation.

You haven't shown much more than this, so we can't go much further until you do.  If you really want help, you have to follow through with the information requests.

MrC

---

### Post by murraymca on 2007-07-24
Hi everyone,

He was nice enough to send me his configuration files, all that was really needed was the domain entry in /etc/resolv.conf...hopefully he should be sorted now :)  I tested [www.serowik.local](www.serowik.local) on my machine and it seemed to work fine.

---

