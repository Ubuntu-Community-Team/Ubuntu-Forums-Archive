---
title: "Postfix Problem"
date: 2007-03-29
forum: Server Platforms
---

### Post by demirburak on 2007-03-29
**please Help in ubuntu......**
hi i am a new ubuntu user

i install a ubuntu 7.04 server.
and i tried ubuntu 6.06 desktop. its same problem. diffrent pc's

problem:

i installed postfix. 
i send a mail other user in pc. its good.
but i try send mail gmail accounts. 
mail is not send.

i checked mail queue.

error:
(Host or domain name not found. Name service error for name=gmail.com type MX: Host not found, try again)

i ping a gmail.com. its a normal ping answers.
i checked iptables -L. everything ACCEPT. and empty.
my gateway is a modem. my ip is 192.168.1.3 my gateway 192.168.1.1

i read a ubuntu server guide and after i install same a guide.
i don't understand (Note: i try a ubuntu 6.06 desktop. its same problem)

---

### Post by Mr. C. on 2007-03-29
Review your main.cf for 

disable_dns_lookups = no

Change it to yes.  Also check that

smtp_host_lookup=dns

and restart postfix if you made changes.

It is also possible that your modem acting as a DNS server is not providing proper DNS lookups.  Don't rely on your cheap router for DNS queries - use your ISPs or your own.

MrC

---

### Post by demirburak on 2007-03-29
i checked main.cf 
but no lines.

i wrote two lines in main.cf

and restart postfix 
error is changed.
error:
(connect to gmail.com[1.0.0.0]: Connection timed out)

i dont understand.
i checked resolv.conf

nameserver 192.168.1.1

and i add this lines.
nameserver 195.175.39.39 (my ISP DNS)

i installed elinks (web browser for console)
this program not open google.com 
first: Look Up 
Second: Making Connection . and END. not open page.

but i pinging google.com gmail.com. All ping answer is normal.

---

### Post by Mr. C. on 2007-03-29
To test if your dns is reliable, and to see MX records, use the host command.  For example:

```
host gmail.com
host apple.com
host google.com
```

Please show the actual output of commands, not your interpretation of them:

```
cat /etc/resolv.conf
```

MrC

---

### Post by demirburak on 2007-03-29
host gmail.com

gmail.com has address 64.233.161.83
gmail.com has address 64.233.171.83
gmail.com has address 216.239.57.83
;; Warning: Message parser reports malformed message packet.

resolv.conf

nameserver 195.175.39.39
nameserver 195.175.39.49
nameserver 192.168.1.1

???

---

### Post by Mr. C. on 2007-03-29
Something is corrupting your DNS transactions.  This is what you should have received:

```
$ host gmail.com
gmail.com has address 64.233.161.83
gmail.com has address 64.233.171.83
gmail.com has address 216.239.57.83
gmail.com mail is handled by 5 gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt1.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt2.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 50 gsmtp163.google.com.
gmail.com mail is handled by 50 gsmtp183.google.com.
```

which shows all the MX records.

Your second nameserver listed is not responding.  Remove it from your /etc/resolv.conf list, and remove your router as a nameserver; neither is helpful.  Use only the first.

Do you have IPv6 disabled - if not, try disabling it.  Let's see if this resolves the issue, and allows your host output to look like that above.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

The command: 

```
dig mx @195.175.39.39 gmail.com
```

will give you all the MX records for gmail, using your first DNS server to make the query.  Test the same, and compare your results.  The output should look like:
```

; <<>> DiG 9.3.4 <<>> mx @195.175.39.39 gmail.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48217
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 4, ADDITIONAL: 11

;; QUESTION SECTION:
;gmail.com.                     IN      MX

;; ANSWER SECTION:
gmail.com.              746     IN      MX      10 alt2.gmail-smtp-in.l.google.com.
gmail.com.              746     IN      MX      50 gsmtp163.google.com.
gmail.com.              746     IN      MX      50 gsmtp183.google.com.
gmail.com.              746     IN      MX      5 gmail-smtp-in.l.google.com.
gmail.com.              746     IN      MX      10 alt1.gmail-smtp-in.l.google.com.

;; AUTHORITY SECTION:
gmail.com.              1534    IN      NS      ns4.google.com.
gmail.com.              1534    IN      NS      ns1.google.com.
gmail.com.              1534    IN      NS      ns2.google.com.
gmail.com.              1534    IN      NS      ns3.google.com.

;; ADDITIONAL SECTION:
gmail-smtp-in.l.google.com. 158 IN      A       209.85.135.27
alt1.gmail-smtp-in.l.google.com. 219 IN A       64.233.163.114
alt1.gmail-smtp-in.l.google.com. 219 IN A       64.233.163.27
alt2.gmail-smtp-in.l.google.com. 69 IN  A       66.249.83.27
alt2.gmail-smtp-in.l.google.com. 69 IN  A       66.249.83.114
gsmtp163.google.com.    948     IN      A       64.233.163.27
gsmtp183.google.com.    1135    IN      A       64.233.183.27
ns1.google.com.         39      IN      A       216.239.32.10
ns2.google.com.         746     IN      A       216.239.34.10
ns3.google.com.         642     IN      A       216.239.36.10
ns4.google.com.         642     IN      A       216.239.38.10

;; Query time: 274 msec
;; SERVER: 195.175.39.39#53(195.175.39.39)
;; WHEN: Thu Mar 29 16:31:48 2007
;; MSG SIZE  rcvd: 406
```


MrC

---

### Post by demirburak on 2007-03-29
ooooooo

i disabled ipv6 

and 
error is everywhere  hahaha.

i restarted ubuntu 
1. error boots on ubuntu blaklist ipv6 error 
2.error boots. i dont read its faster screen :)

3.error mailq commands. 
warning : inet_protocols: configuring for IPv4 support only

---

### Post by Mr. C. on 2007-03-29
I can't read your screen from here. 

Ignore postfix and mail for the moment.  We need to get your DNS and network functioning correctly.  Postfix won't work until then.

I have no idea what you actually did, so you'll have to work through the errors or misconfigurations of disabling IPv6.  We don't know that this will resolve the underlying problems yet, but have to start somewhere.

MrC

---

### Post by demirburak on 2007-03-29
hi 

i try send a mail.  
error is not gone :(

i am very tired offf.
i active ipv6 again.

---

### Post by kidalabama on 2007-09-26
i have got same problem. how resolve this problem. thank you.

---

