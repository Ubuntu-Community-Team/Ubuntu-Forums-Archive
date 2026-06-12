---
title: "IS this the firewall blocking my mail"
date: 2012-08-10
forum: Server Platforms
---

### Post by Nixforce on 2012-08-10
Hi,I have my server running now, only problem im having is my email client is not connecting to the server.

In my incredimail client, i get this error : 

Port: 110, Protocol: POP.No connection could be made because the target machine actively refused it.

Is this the firewall on the server blocking me? I have installed webmin and virtualmin to help me.. All else seems 100%.

Thanks

Glenn

---

### Post by darkod on 2012-08-10
How are you accessing the server, is it on your local LAN?

Did you activate any firewall on the server (by default it's disabled)?

---

### Post by Nixforce on 2012-08-10
Hi,

It on a live domain running at a datacentre , i have moved my one domain onto the new server, and thats the domain the email belongs to.

---

### Post by darkod on 2012-08-10
OK, and how about the second question. Did you activate any firewall on the server yourself?

I doubt a datacentre would block ports used by mailservers, so unless you activated your own firewall, something is strange.

---

### Post by Nixforce on 2012-08-10
Hi,

I think my firewall is ok on the server,  as ran an nmap on the IP (the live ip address), and get the folowing ports as open.

21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
143/tcp  open  imap
443/tcp  open  https
465/tcp  open  smtps
587/tcp  open  submission
993/tcp  open  imaps
995/tcp  open  pop3s
3306/tcp open  mysql

Im still new at some of this, and do read ups on how to check, im hoping its correct.

---

### Post by darkod on 2012-08-10
I noticed something comparing the refuse message you posted in your first post and the nmap results.

The nmap says port open for 110 and tcp protocol.
The message in your first post says connection refused on port 110 protocol POP.

Not sure if it has anything to do with it, I am not familiar with any pop protocols.

Apart from that, it seems you answered your original question. Port 110 doesn't seem blocked so it might be some setting on the server refusing the connection (as the refuse message literary says). But I'm not expert enough with mailserver setups, so I doubt I could help more.

---

### Post by SeijiSensei on 2012-08-10
What error message do you see in /var/log/mail.log when you try to log in?  It doesn't look like a problem with the port being blocked, but an authentication problem of some kind.

Try logging in manually with telnet like this:

```

$ telnet server.example.com 110
[dovecot banner]
user username
[should return OK]
pass password
[should return OK]

```

Your server also exposes the IMAP port 143.  What happens if you log in using:

```

$ telnet server.example.com 143
[banner]
1 login username password

```

---

