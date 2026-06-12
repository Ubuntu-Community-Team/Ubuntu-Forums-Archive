---
title: "am I safe?"
date: 2008-10-14
forum: Security
---

### Post by cosine352 on 2008-10-14
Hi friends,
This is the output of nmap for my Ubuntu laptop. I have ran it from the same box.
> Not shown: 1711 closed ports
PORT    STATE SERVICE
25/tcp  open  smtp
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.145 seconds

I have windows in the virtual box. 

Is it secure to keep those port open? I am not a master in computer. So asking you friends. 

Thanks.

---

### Post by Dr Small on 2008-10-14
Are you behind a router, or directly connected to the internet?

---

### Post by cosine352 on 2008-10-14
I am connected directly to the internet.

---

### Post by jerome1232 on 2008-10-15
Are you running a mail server? If I remember correctly those are all used by mail servers (25 smtp, 139 pop? 445 secure pop tls,ssl)

---

### Post by cosine352 on 2008-10-15
> Are you running a mail server? If I remember correctly those are all used by mail servers (25 smtp, 139 pop? 445 secure pop tls,ssl)

I am not using any mail server

---

### Post by patrickballeux on 2008-10-15
Is your Windows running the mail server?

Port 139 is for netbios (often use my Windows), and 25 and 445 are mail server port.

Make sure that postfix is not installed on your ubuntu setup (look in synaptic), and have a look on your Windows setup (If it is Windows 200x)...

You should not have 25 and 445 open if there is not mail server.

For your Windows Virtualbox, you should use NAT instead of Bridged network access...  This make Windows see the internet, but not the other way around.

---

### Post by jerome1232 on 2008-10-15
What did you run nmap on localhost?

Should probably find out what is opening those ports and get it shutdown. Can you run 'sudo netstat -ltp' on the (I'm guessing Ubuntu host) and 'netstat' on the Windows guest (i'm not sure what if any switches for netstat you would need under windows)?

How is the Windows guest connecting to the internet, is it nat'd or is it connected to a tap interface? 

If it's nat'd then you get the same affect as if the Windows guest were behind a router, shouldn't be accessible from the outside world. 

Best test is to just run nmap on this computer from another computer over the internet, it'll tell you for sure what ports are open to the internet.

---

### Post by cosine352 on 2008-10-15
I was using "postfix" and samba. I have stoped the services form System --> administration --> services. Now all my ports are closed. Thanks for the help my friends.

---

### Post by Dr Small on 2008-10-15
> **cosine352 said:**
> I was using "postfix" and samba. 

Then that's why the mailserver ports where open, along with netbios ones for samba and windows to communicate.

---

