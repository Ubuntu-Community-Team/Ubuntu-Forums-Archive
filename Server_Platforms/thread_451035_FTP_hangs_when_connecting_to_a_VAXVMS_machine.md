---
title: "FTP hangs when connecting to a VAX/VMS machine"
date: 2007-05-21
forum: Server Platforms
---

### Post by skelooth on 2007-05-21
It takes ftp about one minute to connect to the server. Once it's connected it's speedy as it should be. All of the windows computers on the network can ftp in just fine with no hang. There is also shorter pause when connecting to ssh on a redhat box of about 20 seconds.

Any ideas what may be causing this, or how to fix it?

---

### Post by Mr. C. on 2007-05-22
This sounds like a DNS problem.  Are your forward and reverse DNS lookups working quickly ?

MrC

---

### Post by skelooth on 2007-05-22
A coworker tells me it's definitely a DNS issue and that it's a runaway ftp session. Most likely reverse look up issues like you said.

Do you know how to remedy this problem? I'm banned from FTP until it's solved. Let's not tell them that ssh  to my other linux box does it too...

---

### Post by Mr. C. on 2007-05-22
I can't remedy without seeing data.  What does the **host ** or **dig** commands report from the machine having troubles: 

```
host *<VAX/VMS machine>*
dig *<VAX/VMS machine>*
```

replacing the <VAX/VMS machine> with the hostname you use to connect.  If you know how to take the IP address found above to convert to a reverse name in the in-addr.arpa space, show that host or dig report as well.

Which nameservers is your system configured to use:

```
cat /etc/resolv.conf
```


MrC

---

### Post by skelooth on 2007-05-22
Thank you very much for your help Mr. C

Here is the output from running those commands

```
$ host 10.0.0.1
Host 1.0.0.10.in-addr.arpa not found: 3(NXDOMAIN)
$ dig 10.0.0.1

; <<>> DiG 9.3.4 <<>> 10.0.0.1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57577
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;10.0.0.1.                      IN      A

;; ANSWER SECTION:
10.0.0.1.               655360  IN      A       10.0.0.1

;; Query time: 3 msec
;; SERVER: 66.109.38.250#53(66.109.38.250)
;; WHEN: Tue May 22 14:57:34 2007
;; MSG SIZE  rcvd: 42

$ cat /etc/resolv.conf
nameserver 66.109.38.250

```

On the note of the DNS, I'm not sure if 66.109.38.250 is even physically located here.

---

### Post by Mr. C. on 2007-05-22
You need to run host and dig with the hostname, not IP address.  We're trying to see what your DNS server is returning.

Regardless, the DNS server in /etc/resolv.conf appears to be your ISPs nameserver :

```
host 66.109.38.250
250.38.109.66.in-addr.arpa domain name pointer cache-ns1.tvc-ip.com.
```

It will never resolve a hostname to a private IP address such as 10.0.0.1.  If you use private IP space, you will need your own DNS server to return valid internal private IP addresses.  Perhaps you are using the wrong DNS server for your organization.  You'll have to contact your admins to determine what the correct DNS server is for your organization.

MrC

---

### Post by skelooth on 2007-05-27
I just wanted to add the conclusion of this situation to the thread. Mr. C thank you again as you were correct, it was a DNS issue. Once we added entries to all of the hosts files involved it worked as expected.

---

