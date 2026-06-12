---
title: "Sendmail"
date: 2007-06-14
forum: Server Platforms
---

### Post by rikoshay2020 on 2007-06-14
Hi,

I am quite new to server installation and administration and am setting up an ubuntu server as a hobby project. I'm using server edition 6.10 and have managed to configure the apache 2 server with some virtual domain hosting, php, mysql and ssh with no problem. I am using webmin to configure my servers which I've found a great help. I have however got a bit stuck with sendmail and would be grateful for anyone's advice.

I've got sendmail installed and working with webmin. I've set up the domains to match those of my apache server and I've tried to make an mx record as follows. If my domain is example.com and when I type hostname at the command prompt I get ubuntuserver I've set the MX record up as ubuntuserver.example.com 10. I've port forwarded TCP 25 to the relevant local IP address as I did port 80 for the webserver - however it doesn't collect external mail. I can send and receive mail locally between users on the system and send mail externally where it appears to be sent from [email]rik@example.com[/email]. When I try to send an email to [email]rik@example.com[/email] it gets returned with a fatal error - nameserver ubuntuserver.exampe.com not found.  

Can anyone tell me where I might be going wrong?

Cheers, 

Rik

---

### Post by sih_phos on 2007-06-14
There's a reason it's called SENDmail :p  I've never done it myself, but I was told there's a line that needs to be uncommented in the config files to allow RECEIVEmail, if that makes sense.  I wish I could tell you move of where it is but I'm not sure.  Search around and best of luck.

---

### Post by jharadie on 2007-06-16
I haven't used sendmail since I left a different Linux OS, but I remember a couple of things that might help you.

In sendmail.mc, look for a line like this:
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
and change it to this:
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp')dnl
(removing the "Addr=127.0.0.1")
There are two instances of this line in the .mc file.  Then run sendmailconfig and see if that works.

Another thing: I remember having a devil of a time with DNS and Sendmail; I wound up having to install some kind of mini-DNS program to solve the problem.  I don't remember the name of it, sorry. :(  I recall that the qmail homepage had some programs that helped.

:)

---

### Post by rikoshay2020 on 2007-06-16
Thanks for your help - stupid DNS problem with the MX record which I've solved.

Thanks,

Rik

---

