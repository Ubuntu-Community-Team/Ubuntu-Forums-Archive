---
title: "Exchange 2003 and Postfix cant talk to eachother"
date: 2007-03-31
forum: Server Platforms
---

### Post by bmathis on 2007-03-31
Hey everyone,

I have an Exchange 2003 box in place at my work and have recently added a Postfix box for a subsidary of ours. Both servers have their own external IP address for the incoming mail, but share the same outgoing IP address. When sending an email from one box to the other, they time out and cannot seem to talk to each other unless I use Postfix as a smart host but I dont want to do that and I dont want to host the subsidary on the Exchange server either.

Our network is as follows

Nortel Networks Contivity - 192.168.10.2 / xxx.xxx.xxx.140
Windows 2003 w/ Exchange 2003 - 192.168.10.5 / xxx.xxx.xxx.142
Ubuntu 6.06.1 w/ Postfix - 192.168.10.10 / xxx.xxx.xxx.143

all using xxx.xxx.xxx.140 as the outgoing IP

Does anyone know of a solution or can point me in a better direction, it will be greatly appreciated.

Thank in advance,

- B

---

### Post by danpre on 2007-03-31
Do you mean that you can't send an email from postfix to exchange?

I have my own POSTFIX and company's EXCHANGE in the same WAN network, but using different domains.

I was unable to send an email from my postfix to exchange addresses.
So I had to add to "transport" file an entry:
domain_name         XXX.XXX.XXX.XXX

where XXX.XXX.XXX.XXX is an exchange address

(now I'm using postfix with mysql for domains and users so I don't remeber exact entry to transport file)

DANIeL

---

### Post by bmathis on 2007-03-31
well, I can get Postfix to send to Exchange by adding 192.168.10.0/24 to mynetworks, but Exchange still times out when trying to send to Postfix. So, I guess its just Exchange thats having the problem.

---

### Post by rsermilik on 2007-03-31
Have you told Postfix not to use DNS?
I suppose you use DNS when receiving from the world:-)
You can make an entry in master.cf with
2525    inet    n       -       n       -       -       smtpd
        -o disable_dns_lookup=yes

and tell Exchange to use port 2525 when sending to Postfix

Remember there must be spaces or tab before -o
 
regards

---

### Post by bmathis on 2007-03-31
Thanks rsermilik, that worked perfectly \\:D/

---

