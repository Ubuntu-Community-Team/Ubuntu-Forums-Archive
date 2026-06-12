---
title: "[SOLVED] Cannot update, DNS Issue?"
date: 2008-06-06
forum: Server Platforms
---

### Post by pacrep on 2008-06-06
The problem:
Running ubuntu server 8.04 as LAMP and ssh server
Cannot update ubuntu sever 8.04 I get the following error:

```
Err http://archive.ubuntu.com/ hardy Release.gpg
	 Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/hardy/main Translation-en_US
	 Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/hardy/restricted Translation-en_US
	 Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/hardy-updates Release.gpg
	 Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/hardy-updates/main Translation-en_US
	 Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/hardy-updates/restricted Translation-en_US
	 Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W:Failed ot fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2
Could not resolve 'archive.ubuntu.com'
W:Failed ot fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2
Could not resolve 'archive.ubuntu.com'
W:Failed ot fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg
Could not resolve 'archive.ubuntu.com'
W:Failed ot fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2
Could not resolve 'archive.ubuntu.com'
W:Failed ot fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2
Could not resolve 'archive.ubuntu.com'
W: Some index files failed to download, they have neen ignored, or old ones used instead.
w: You may want to run apt-get update to correct thes problems
```

Notice I removed the "us" from archive.ubuntu.com, I commented out "deb cdrom" and there is no "web" at the end of the address in the /etc/apt/source.list

I can ping my linksys router running dd-wrt 192.168.1.1 also my ISP address, also my laptop.
How ever I cannot ping [www.google.com](www.google.com) I get, unknown host [www.google.com](www.google.com).

I can ping googles ip address, so I'm guessing my server is having a DNS problem? My laptop has no problem updating so the router is not the problem.

any help is appreciated.

---

### Post by quelx on 2008-06-06
what does ```
cat /etc/resolv.conf
``` show?

---

### Post by pacrep on 2008-06-06
Thanks for fast reply,
 cat /etc/resolve.conf

nameserver 192.168.1.2


I am using the ddwrt router as a client bridge hooked up to another AP that why the nameserver is 192.168.1.2

AP wrt150n = 192.168.1.1
dd-wrt - client bridge = 192.168.1.2

---

### Post by quelx on 2008-06-06
So is *192.168.1.2* running **dnsmasq** or some such dns service?

If not that should be your router, 192.168.1.1.  Better yet (for testing at least) your ISPs DNS server.

From the server what does ```
dig apple.com
``` give you?

---

### Post by pacrep on 2008-06-06
```
dig apple.com

```


```
; <<>> DiG 9.4.2 <<>> apple.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 58489
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;apple.com.			IN	A

;;Query time 6 msec
;;SERVER: 192.168.1.2#53(192.168.1.2)
;;When Fri Jun 6 17.27.47 2008
;;MSG SIZE rcvd: 27
```

---

### Post by quelx on 2008-06-06
edit */etc/resolv.conf*

change ```
nameserver 192.168.1.[COLOR="Red"]2[/COLOR]
``` to ```
nameserver 192.168.1.[COLOR="Red"]1[/COLOR]
``` and try **apt-get** again

---

### Post by pacrep on 2008-06-06
ok will try, thx for your help I have to run right now. Will post back later. Again thx

---

### Post by pacrep on 2008-06-07
Thanks :guitar: got it to work!

---

### Post by ovidiu_b13 on 2011-05-07
Thank you, I had the sameproblem, found out i confused the nameserver with my url. oups. question: nameserver stands for gateway? because i've entered my router's gateway in that file and it works now.

---

