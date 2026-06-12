---
title: "Sending mail via exim: force it to use internal IP"
date: 2013-05-07
forum: Server Platforms
---

### Post by mister_doctor on 2013-05-07
I'm attempting to configure my server to send e-mail to my company's internal exchange server. I've verified all the firewall configurations are in place and even did a telnet from the linux box to the exchange server sucessfully using it's internal IP. The trouble I'm facing is that exim appears to be doing a dns lookup and getting the external IPs for the exchange server and throwing "connection refused" errors like so. These are all internet facing IPs so I've redacted them accordingly:

```

admin@linux-box:~$ sudo exim -Mvl 1UZmLU-000CDr-HW
2013-05-07 14:10:36 Received from user@linux-box.int.mycompany.com U=batch P=local S=687
2013-05-07 14:10:36 mail2.mycompany.com [xxx.xxx.xxx.4] Connection refused
2013-05-07 14:10:36 mail4.mycompany.com [yyy.yyy.yyy.157] Connection refused
2013-05-07 14:10:36 mail.mycompany.com [xxx.xxx.xxx.5] Connection refused
2013-05-07 14:10:36 me@mycompany.com R=dnslookup T=remote_smtp defer (111): Connection refused
2013-05-07 15:26:48 mail2.mycompany.com [xxx.xxx.xxx.4] Connection refused
2013-05-07 15:26:48 mail4.mycompany.com [yyy.yyy.yyy.157] Connection refused
2013-05-07 15:26:48 mail.mycompany.com [xxx.xxx.xxx.5] Connection refused
2013-05-07 15:26:48 me@mycompany.com R=dnslookup T=remote_smtp defer (111): Connection refused
2013-05-07 15:29:14 mail2.mycompany.com [xxx.xxx.xxx.4] Connection refused
2013-05-07 15:29:14 mail4.mycompany.com [yyy.yyy.yyy.157] Connection refused
2013-05-07 15:29:14 mail.mycompany.com [xxx.xxx.xxx.5] Connection refused
2013-05-07 15:29:14 me@mycompany.com R=dnslookup T=remote_smtp defer (111): Connection refused

```

Output from nslookup

```

> mail.mycompany.com
Server:         172.25.0.37
Address:        172.25.0.37#53

Non-authoritative answer:
Name:   mail.mycompany.com
Address: xxx.xxx.xxx.5

```

Instead of trying to make it accept connections on the outside IP, I'd rather it go straight into the exchange server via the internal IP, this server isn't meant to dial out to the internets. Changing /etc/hosts did not seem to do the trick even though pinging returns the internal IP now.

Any suggestions are much appreciated.

---

### Post by mister_doctor on 2013-05-07
Looks like I fixed my own issue.

I reconfigured exim for "mail sent by smarthost; no local mail" using dpkg-reconfigure, then all messages in mailq were sent. I had originally configured it for "internet site" which I now know is incorrect.

---

