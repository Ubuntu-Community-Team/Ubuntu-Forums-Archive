---
title: "a question about ports"
date: 2008-08-24
forum: Security
---

### Post by Kain000 on 2008-08-24
Hey everyone, 
I was just wondering about FTP connections and why most clients prefer to use passive mode.   Is this because you can only have one connection per port?  Or just to keep speeds form bogging down?  

Also another question about computer ports, even tho a certian port is specified for a certian task ie: port 21 open to the world for FTP traffic, can it be used just like an opening to my computer or just for FTP traffic?

---

### Post by mellowd on 2008-08-24
Anything can come in on port 21, as long as there is something listening. Generally this will only be your ftp daemon though. If 2 applications try to use the same port, it'll cause problems for both, but I'm sure a well written trojan could hide this still.

---

### Post by Kain000 on 2008-08-24
alright then whats to stop anyone from trying to get into my server via port 21 because it's open.   Is it open but only the FTP daemon works on it and thus other traffic is null?

---

### Post by mellowd on 2008-08-24
Exactly. They'll only be able to get into that port if something is responding to it in the first place. There is little risk. The riskiest part is making sure your ftp daemon itself can't be compromised.

---

### Post by Kain000 on 2008-08-24
Alright thankyou very much.  for helping me clear this up, so if I were to open a large range of ports to allow the FTP clients that like to use passive mode, as long as those ports are being listened to by my FTP daemon it would be relatively safe?  The problem I was having was that most connections to my server (anyone who's client wanted to use passive mode by default) would be blocked, but I was worried about opening a large range of ports to accommodate those clients. And I didnt want to have everyone using active mode because that would cause traffic jams on port 21.

---

### Post by mellowd on 2008-08-24
It wouldn't cause traffic jams, as it doesn't quite work that way. This is is a good quick description on the 2 modes:

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

In particular, I've quoted this part ---


> The following chart should help admins remember how each FTP mode works: 

 Active FTP :
     command : client >1023 -> server 21
     data    : client >1023 <- server 20

 Passive FTP :
     command : client >1023 -> server 21
     data    : client >1023 -> server >1023

A quick summary of the pros and cons of active vs. passive FTP is also in order: 

Active FTP is beneficial to the FTP server admin, but detrimental to the client side admin. The FTP server attempts to make connections to random high ports on the client, which would almost certainly be blocked by a firewall on the client side. Passive FTP is beneficial to the client, but detrimental to the FTP server admin. The client will make both connections to the server, but one of them will be to a random high port, which would almost certainly be blocked by a firewall on the server side. 

Luckily, there is somewhat of a compromise. Since admins running FTP servers will need to make their servers accessible to the greatest number of clients, they will almost certainly need to support passive FTP. The exposure of high level ports on the server can be minimized by specifying a limited port range for the FTP server to use. Thus, everything except for this range of ports can be firewalled on the server side. While this doesn't eliminate all risk to the server, it decreases it tremendously. See Appendix 1 for more information. 

---

