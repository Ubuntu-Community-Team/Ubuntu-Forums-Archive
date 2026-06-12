---
title: "How to trace boot process"
date: 2006-05-27
forum: Server Platforms
---

### Post by interprb on 2006-05-27
I need to know if there is anyway to trace the boot up process on a file by file level.

Thanks

---

### Post by fdoving on 2006-05-28
What is it you're trying to find out? I'm thinking 'bootchart', but that only visualizes the time it takes to boot each service.

---

### Post by interprb on 2006-05-28
I am trying to trace a rouge dns request from our web sever to our dns server for an a record request to hotmail.com. I happens in boot process and when I turn the web server firwall on and off .. like with  firestarter lock and unlock button when I lock it ok, when I unlock it the request is made. I can see this in live dns logs on our dns server.  something is not right.

---

### Post by alphaomega on 2006-05-28
[QUOTE=interprb]I am trying to trace a rouge dns request from our web sever to our dns server for an a record request to hotmail.com. I happens in boot process and when I turn the web server firwall on and off .. like with  firestarter lock and unlock button when I lock it ok, when I unlock it the request is made. I can see this in live dns logs on our dns server.  something is not right.[/QUOTE]

sounds like you need to open a port in firestarter for the dns server.

---

### Post by interprb on 2006-05-28
no, no  port 80 and 53 are open. What I was doing was testing to see why the web server is making  an "a" request to our dns server for this domain. Example, firewall lock nothing in dns records... unlock and dns records
13:31:01 Request from 192.168.2.201 for A-record for hotmail.com.
13:31:01 Sending reply to 192.168.2.201 about A-record for hotmail.com.:
13:31:01 -> Answer: A-record for hotmail.com. = 64.4.33.7
13:31:01 -> Answer: A-record for hotmail.com. = 64.4.32.7

lock nothing but unlock and...
Request from 192.168.2.201 for A-record for hotmail.com.
13:31:01 Sending reply to 192.168.2.201 about A-record for hotmail.com.:
13:31:01 -> Answer: A-record for hotmail.com. = 64.4.33.7
13:31:01 -> Answer: A-record for hotmail.com. = 64.4.32.7

192.168.2.201 is the web server. It happens everytime.

---

### Post by fdoving on 2006-05-28
You can try to search for hotmail.com in the bootscripts, in your case the firewallscripts probably.

```

grep -R hotmail.com /etc/init.d/

```

- Frode

---

### Post by interprb on 2006-05-28
Thanks fdoving No luck... Its got to be in a script somewhere. I have looked in hosts, dhcp, alow, deny firewall ect...  I do know that it is last or next to last process in boot order ](*,)  This aint funny no more.

---

### Post by interprb on 2006-05-28
YEA !!!! :p :p   php script in cms causing part of the problem. Also a bot from msnbot  on server plus external firewall rules set mths ago on paremiter firewall to kill  bots because of banwidth issue and block e-mail because of Dictionary attacks. Funny, you adjust one thing and have to do 20 to make it right.  

A Big thanks to all..

---

