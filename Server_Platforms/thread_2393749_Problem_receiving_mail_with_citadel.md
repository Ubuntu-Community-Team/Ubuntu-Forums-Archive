---
title: "Problem receiving mail with citadel"
date: 2018-06-07
forum: Server Platforms
---

### Post by delfiler on 2018-06-07
so i have a ubuntu server 16.04 with a fiewall, DNS and DHCP all working perfectly fine, now i have installed citadel and everything is still fine added it where it was needed and opened (for so far i know) all the required ports for it but i still can't recieve mail from external e-mail adresses, internal everything is working fine. and i have no clue what i am doing wrong anyone have an idea how to get citadel to recieve the mail?

---

### Post by SeijiSensei on 2018-06-07
Start with /var/log/mail.log. Do you see mail arriving from outside?  If so, what errors do you see?  Your question as it stands is unanswerable.

---

### Post by delfiler on 2018-06-07
that is a no, i do't see anything ariving as i used my personel e-mail from hotmail (currently called outlook but i still call it hotmail)

---

### Post by SeijiSensei on 2018-06-08
Well, there are now dozens of possible answers.  Let's start with these:

1) Do you have your own domain?  If you don't have a domain, how is inbound email addressed?
2) Does your domain's MX record point to the publicly-facing IP address of the server?
3) Is the server behind a firewall router or directly on the Internet?  If it's behind a router, is port 25 open and port forwarding set up?  If on the Internet, is port 25 open?
4) If this is a residential connection, are you sure your ISP allows inbound SMTP traffic at all?  Many providers block inbound ports like 25 and 80 to prohibit people from running servers on residential connections.

---

### Post by lensman3 on 2018-07-01
From your mailserver machine in a test window enter:

telnet localhost 25                   #You should get an answer from your server. Port 25 is the mail port.  
                                                # See the file "/etc/services" for the ports.
ehlo localserver.net                 # Server should answer
                                                # ehlo is extended hello and should report the commands that are permitted.


From a linux machine _outside_ your firewall do:

telnet <ip-address> 25   
If your email server doesn't answer the,
1) a firewall blocks port 25
2) your ISP is blocking port 25 because of mail spam and your IP number is not whitelisted.
3) the telnet from Internet side of your firewall can be done on a windows machine with windows telnet

---

