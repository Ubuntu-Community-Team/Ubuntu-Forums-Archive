---
title: "What is Accessing the Internet?"
date: 2010-10-21
forum: Security
---

### Post by nah40 on 2010-10-21
I am running Ubuntu 10.10.
something is constantly accessing the net and I cannot find what it is.
Is there any application that will assist.
Stopping the items listed in the System Monitor, do not stop it.

---

### Post by uRock on 2010-10-21
Wireshark will show all incoming and outgoing packets.

What makes you think something is connecting to the net?

---

### Post by nah40 on 2010-10-21
I can see the traffic on my router, and on Network Traffic Manager.
It is constant.

---

### Post by uRock on 2010-10-21
Wireshark will show everything going to and from the host. Have you installed a print server or anything like that, which would be sending out CUPS packets? I have noticed ubuntu doesn't send out ARP packets very frequently, so I doubt that is the issue. It could also be a dying NIC that doesn't stop broadcasting. Snort would be overkill at this point for finding the culprit application, unless you are good at writing rules.

BTW, Is the Network Traffic Manager you are using for Linux or Windows? Sounds like a fun toy to have.

---

### Post by nah40 on 2010-10-21
nothing new installes.
IT is a constant 500-700 bytes in and out.
Just started Wireshark, will have to see if that helps.
Thanks

---

### Post by techunit on 2010-10-21
Hi you should be checking the System Monitor... it will tell you the sending/receiving of your computer. Have you considered that someone may be accessing your router remotely via wireless?

Another question how are you determining which processes are accessing the network? Ill see what I can do....

---

### Post by uRock on 2010-10-21
Moved to the Security Discussions, as someone here may know of a good tool to find what is connecting.

---

### Post by nah40 on 2010-10-21
Wireshark found it.
It is deluge, although I have not had that on for hours.

---

### Post by uRock on 2010-10-21
Cool, glad you found it.

---

### Post by HermanAB on 2010-10-22
Another way to see what is going on is with ntop.  Like top, but for network connections.

---

### Post by wojox on 2010-10-22
> **nah40 said:**
> Wireshark found it.
It is deluge, although I have not had that on for hours.

If you shut down Deluge by pressing the x window control, it will actually send it to the background. You need to open the file menu and select quit. (Been there, done that).

---

### Post by The Cog on 2010-10-22
> sudo lsof -i -nwill tell you which program is using the internet.

---

