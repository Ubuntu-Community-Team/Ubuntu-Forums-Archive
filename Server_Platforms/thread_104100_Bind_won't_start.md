---
title: "Bind won't start"
date: 2005-12-15
forum: Server Platforms
---

### Post by nimy on 2005-12-15
I have configured the files in /etc/bind to run on my network and ran 
/etc/init.d/bind9 start
I get no error on start (says bind started ok) but 
ps -ef |grep bind shows nothing, and no errors show up in /var/log/messages
I've looked for how to set up bind on ubuntu and found some pages that show how to make changes to bind so that you can run other programs that will help make it easier to manage bind and other services.  I don't want to run other programs - I just want to see if bind will run as installed.
I did chown etc/bind to bind because I would rather not run dns as root, but neither root nor bind ownership changes the fact that bind won't run.  What to do?

---

### Post by diebels on 2005-12-15
Try /var/log/syslog

---

### Post by nimy on 2005-12-15
[QUOTE=diebels]Try /var/log/syslog[/QUOTE]

Thanks, found that and then ran another post, which has already been answered, this forum is awesome :)

What I failed to check before running that post was whether dig etc actually produces a local response, given that I was using the same config as I had used for redhat.  It doesn't, and I can't find any syslog or other errors.  Here's the dig output from the server:

>dig mydomain.com

; <<>> DiG 9.3.1 <<>> mydomain.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63802
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mydomain.com.                   IN      A

;; AUTHORITY SECTION:
mydomain.com.            7200    IN      SOA     NS41.WORLDNIC.COM. namehost.WORLDNIC.COM. 2005112200 10800 3600 604800 7200

;; Query time: 44 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Dec 15 16:37:00 2005
;; MSG SIZE  rcvd: 91

---

### Post by nimy on 2005-12-19
Just to clean this up, these errors were due to a named.conf error which is now fixed :)

---

