---
title: "[SOLVED] POSTFIX Won't Work"
date: 2008-09-16
forum: Server Platforms
---

### Post by h3llh0l3 on 2008-09-16
Hello all,

I am trying to setup a mail server(postfix) for some testing on my LAN. The hostname of my machine is: 

```

root@lab:/etc/postfix# hostname -f
lab.test

```

The /etc/postfix/main.cf is(read the article @ [https://help.ubuntu.com/community/Postfix):](https://help.ubuntu.com/community/Postfix):)

```

root@lab:/etc/postfix# cat main.cf 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no
myorigin = /etc/mailname
mydestination = lab.test, lab, localhost.localdomain, localhost
relayhost = smtp.lab.test
mynetworks = 127.0.0.0/8 192.168.221.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/

```

Now, when I start the postfix service, the service does start but when I "ps" I don't see postfix running:

```

root@lab:/etc/postfix# /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix
   ...done.
root@lab:/etc/postfix# ps -ef | grep postfix
root      8246  6386  0 04:15 pts/2    00:00:00 grep postfix

```

When I telnet from another machine on port 25 of the mail server or if the telnet the localhost on port 25 I get the following(no SMTP banner):

```

root@lab:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
^]
telnet> quit
Connection closed.

```

Also when I do a dig, I don't see the mx record for my machine???

```

root@lab:/etc/postfix# dig mx lab

; <<>> DiG 9.4.2-P1 <<>> mx lab
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 43014
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;lab.                       IN      MX

;; AUTHORITY SECTION:
.                       6709    IN      SOA     A.ROOT-SERVERS.NET. NSTLD.VERISIGN-GRS.COM. 2008091601 1800 900 604800 86400

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Sep 17 04:20:49 2008
;; MSG SIZE  rcvd: 100

```

I am not sure where I am going wrong. Could someone point me in the correct direction.

Thanks :)

---

### Post by schettj on 2008-09-16
You could start by checking /var/log/mail.* (err, log, info) and see what clues are there.

You have to set your own mx record in your dns... that I do know.

---

### Post by h3llh0l3 on 2008-09-17
I checked the logs(mail.info, mail.err, mail.log & mail.warn) and I found that everytime I tried starting postfix the following error was generated:

```

Sep 17 20:25:11 lab postfix/master[6251]: fatal: bind 0.0.0.0 port 25: Address already in use

```

But when I do a netstat I don't see port 25 being used and nmap shows that the port 25 is open(???).
Any suggestions?

Also could you please let me know if there is anything broken in my main.cf file?

Thanks :)

---

### Post by MJN on 2008-09-17
Something is obviously using the port so you just need to find out what!
 
Post the output of **sudo lsof -i :25** (and **ps aux**).
 
Mathew

---

### Post by h3llh0l3 on 2008-09-17
> **MJN said:**
> Something is obviously using the port so you just need to find out what!
 
Post the output of **sudo lsof -i :25** (and **ps aux**).
 
Mathew
Thanks for the quick reply.
losf -i:25 showed that nepenthes was bind'd to port 25 so I shut down nepenthes and I was able to start POSTFIX with no errors(I tailed the mail.log).

But with POSTFIX running nepenthes would not bind to port 25. And I need to have both of them running for my test. Any suggestions?

Thanks :)

---

### Post by MJN on 2008-09-17
Only one process can bind to any one port.

Mathew

---

### Post by RealPSL on 2008-09-19
Like MJN said ports and IP address are a one to one mapping. It is a good thing however that a single machine can have multiple IP addresses. You can add an IP alias following the instructions [here]("http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html"). Once you have done this you can tell either postfix or the other application to bind to the port on secondary address.

---

