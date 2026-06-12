---
title: "[SOLVED] mail server configuration issues"
date: 2008-07-03
forum: Server Platforms
---

### Post by ub007 on 2008-07-03
I'm installing a mail server and these are the steps which I followed:

sudo apt-get install postfix
sudo apt-get install mailx

sudo useradd -m -s /bin/bash fmaster
sudo passwd fmaster

testing it -all works fine: telnet localhost 25......(...su - fmaster
mail....)

Step 2)

sudo postconf -e "home_mailbox = Maildir/

sudo postconf -e "mailbox_command 

sudo  /etc/init.d/postfix restart

Step 3)
sudo apt-get install courier-pop
sudo apt-get install courier-imap

sudo postconf -e "mydestination = mail.ubuntu.surrey.ac.uk, localhost.localdomain, localhost, ubuntu.surrey.ac.uk"

sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.1.0/24"
sudo postconf -e "inet_interfaces = all
sudo postconf -e "inet_protocols = all"
sudo  /etc/init.d/postfix 

telnet mail.yourdomain.com 25
***error msg:couldnot resolve mail.ubuntu.surrey.ac.uk/25: Name or service....

What could be wrong here?

Info on my network:
Its an intranet-6 pcs connected to a dell 5424 switch
Got Ubuntu server installed on 1 machine and thats where I have set up the mail server....For installing purposes I have unplugged this comp from the switch and plugged it into the uni n/w which got internet connection:

I have used surrey as an example.Also the ip that i get leased when i plug into the uni n/w is "131.'.'.'

could anyone tell me what configuration changes I need to make...

Cheers
David

---

### Post by ub007 on 2008-07-03
this is the output for
$dig mx ubuntu.surrey.ac.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 2742
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.surrey.ac.uk.		IN	MX

;; AUTHORITY SECTION:
surrey.ac.uk.		86400	IN	SOA	agate.surrey.ac.uk. postmaster.surrey.ac.uk. 2008070305 7200 900 604800 86400

;; Query time: 0 msec
;; SERVER: 218.127.1.100#53(158.125.1.100)
;; WHEN: Thu Jul  3 12:39:34 2008
;; MSG SIZE  rcvd: 93

---

### Post by MJN on 2008-07-03
> **ub007 said:**
> telnet mail.yourdomain.com 25
***error msg:couldnot resolve mail.ubuntu.surrey.ac.uk/25: Name or service....Is that copied verbatim? If not, do so because you're not going to get much help by introducing any typos/errors in the transcript. What's the domain you're trying to telnet to? The fact the error doesn't match the target suggests you've either got the copy-and-paste wrong or there's something seriously wrong.

> I have used surrey as an example.What do you mean by this?

Seriously David, when it comes to diagnosing anything involving DNS you make it infinitely harder to troubleshoot if you hide the domain (even more so when you don't do it consistently).

Mathew

---

### Post by ub007 on 2008-07-04
Thanks MJN,i included ubuntu.lboro.ac.uk in the /etc/hosts file and it works fine now....


> David, when it comes to diagnosing anything involving DNS you make it infinitely harder to troubleshoot if you hide the domain (even more so when you don't do it consistently)

though its a test intranet,i had plugged into the uni n/w for installing stuff and was wary of posting the mail server ips and domain in public...However,I get what ur saying(specially the latter part of it),would definetlty take that into account the next time i post something....

Cheers

---

