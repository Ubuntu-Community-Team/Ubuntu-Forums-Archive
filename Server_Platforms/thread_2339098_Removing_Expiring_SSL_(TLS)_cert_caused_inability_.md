---
title: "Removing Expiring SSL (TLS) cert caused inability to receive mail in Thunderbird"
date: 2016-10-04
forum: Server Platforms
---

### Post by Grigoriy on 2016-10-04
Hello!

I recently switched my SSL (TLS) certificate from a regular one to Let's  Encrypt. I decided to get rid of my old expiring cert files, but I  physically removed them, I've started to have strange issues with  Thunderbird Mail. Normally after I open the application, I get a login  box. And after the old cert files removal, I stopped getting the login  and also stopped receiving mail. Sending was fine. Also the SMTP server  was working, since in a web mail access everything worked as usual. Only  after I put back files that belonged to the old cert, Thunderbird Mail  started to work as usual. I don't understand the connection between my  old cert files that I was using for HTTPS and Apache and Thunderbird  Mail, its login and receiving mail in it.

---

### Post by CharlesA on 2016-10-04
Sounds like a config issue to me.

If you want to keep using LE certs, you can just create a symlink from wherever your old certs were and leave it at that.

That is, if you don't want to dig into the config of whatever mail server you are using.

---

### Post by Grigoriy on 2016-10-04
> **CharlesA said:**
> 

If you want to keep using LE certs, you can just create a symlink from wherever your old certs were and leave it at that.



But my old cert is expiring in THREE days, regardless. I'm assuming that after that I would have the same problem I described even if I don't touch my old cert files. 
But I just don't see a connection between A and B. Those are totally different certificates. The self-signed one valid for another 9 years I myself made to use with mail servers and the one I obtained from the third party to use with Apache and HTTPS.

---

### Post by CharlesA on 2016-10-04
The problem was the mail server was referencing the old certs that were deleted, so it was unable to establish a secure connection.

Since you haven't said what mail server you are using, that's all I can tell you.

---

### Post by Grigoriy on 2016-10-04
I'm using Postfix as MTA and probably Dovecot (according to Synaptic), though I do have a directory of Courier. I have no clue how to check what MDA I'm using.

---

### Post by CharlesA on 2016-10-04
> **Grigoriy said:**
> I'm using Postfix as MTA and probably Dovecot (according to Synaptic), though I do have a directory of Courier. I have no clue how to check what MDA I'm using.

```
sudo netstat -nlp
```

That would be a good start.

---

### Post by Grigoriy on 2016-10-04
```
tcp6       0      0 :::995                  :::*                    LISTEN      1446/couriertcpd


```

So it must be Courier then? So now what?

---

### Post by CharlesA on 2016-10-04
You don't have anything listening on IPv4? Something should be on port 25, 465, and 993.

---

### Post by Grigoriy on 2016-10-04
It's really confusing. I checked with Netstat and on port 995 I see couriertcpd. But when I do this "courier restart" - I get this:
The program 'courier' is currently not installed.

---

### Post by Grigoriy on 2016-10-04
> **CharlesA said:**
> You don't have anything listening on IPv4? Something should be on port 25, 465, and 993.

I have something called master with PID 1573. And when I go to System Monitor and check that PID, it show "Master" too and when I hover my mouse pointer, I see this:
/usr/lib/postfix/master

God only knows!

---

### Post by CharlesA on 2016-10-05
> **Grigoriy said:**
> I have something called master with PID 1573. And when I go to System Monitor and check that PID, it show "Master" too and when I hover my mouse pointer, I see this:
/usr/lib/postfix/master

God only knows!

That would be postfix, your MTA. Do you see dovecot running?

---

### Post by Grigoriy on 2016-10-09
I was away for awhile. What happens is that I removed completely Dovecot from the system and now it's only Courier as MDA (I understand that it plays a role of an intermediary between Postfix and Thunderbird Mail ). My cert that I was using prior to installing Let's Encrypt has expired. I'm receiving and sending e-mail fine (while not touching the old expired cert). 
I want to ask about the process to understand how it works in general, irrespective of my particular situation. I understand well what happens when SMTP server, say Postfix contacts  remote SMTP server to send or receive mail. The connection could (and  should) be encrypted, certain ports must be used and the certificate  must be valid and accepted by all parties.
                          But when it comes to the local e-mail delivery  for me it's a grey area. Ok, let's say if we're talking about receiving  mail and Postfix already got it from the remote server. Then we have  MDA (like Courier) that takes the mail from Postfix and gives it to a  MUA (like Thunderbird Mail, for example). I'm talking about one physical  machine and one user session. What the purpose of the encryption if it  all happens inside and no third party could be present? And if it's the  case of the same computer and the same user, then does the validity of  the cert play any role for e-mail delivery process from Postfix via  Courier to Thunderbird Mail?

---

