---
title: "Connection to Windows printing server"
date: 2012-04-12
forum: Server Platforms
---

### Post by Maxence on 2012-04-12
Hello,
I want to connect myself to the printer server of my organization which is working with windows. The IT service gave me an ip address to which i am not able to connect. Apparently, i should be able to connect to it even from a external connection.
Here is the ip address: [http://193.137.112.17/](http://193.137.112.17/)
Firefox says "server not found".
Thanks for the help! :D

---

### Post by papibe on 2012-04-12
Hi Maxence.

My guess is that address is the one you need to set up a network printer, and it is not for web browsing (firefox).

Right now I'm in 10.04. To add a network printer you go to:
```
System -> Administration -> Printing -> Add -> Network Printer -> Internet printer protocol.
```
I image it is very similar in later versions.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by SeijiSensei on 2012-04-12
```
[seiji@host ~]$ nmap -P0 -sT 193.137.112.17

Starting Nmap 5.00 ( http://nmap.org ) at 2012-04-12 22:39 EDT
Interesting ports on 193.137.112.17:
Not shown: 997 filtered ports
PORT     STATE  SERVICE
445/tcp  open   microsoft-ds
515/tcp  open   printer
9100/tcp closed jetdirect

```

It offers SMB (Windows) printing on port 445, LPR/LPD on port 515, and may let you use HP JetDirect, even though it looks closed to nmap.

I find it easier to use the browser-based configurator for CUPS printing.  Open Firefox and point it to [http://localhost:631/](http://localhost:631/).  Choose Administration > Add a Printer and enter your username and password when prompted.  Choose the LPD option and enter lpd://193.137.112.17/ in the box that follows.  Choose the appropriate driver and see if that works.  If not, you'll need to ask the IT guys what the name of the "queue" is and rewrite the URL to lpd://193.137.112.17/queuename/.

I also tried connecting to the SMB service on port 445 by using Dolphin on KDE and entering smb://193.137.112.17:445/ in the address box.  (I'm pretty sure Nautilus supports this as well.)  I was prompted for a username and password.

---

### Post by Maxence on 2012-04-23
Thank you very much for the help. It helped a lot: I could understand how it works and also establish a connection! :D
Although according to the IT service, the server is not compatible with computers who are not working on windows...
Thanks again!

---

