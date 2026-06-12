---
title: "Netstat and tor - detailed!"
date: 2009-12-17
forum: Security
---

### Post by zozza on 2009-12-17
Hello,

I would appreciate some help translating my netstat results using tor (port 9050) and polipo (port 8118) into language a non-technical person can understand!  The netstat copy is after the questions.

The netstat results show that I have connections from 8118, and connections to 8118, connections from 9050, and connections to 9050, and connections from locahost:random ports to the tor servers.  I understand the general idea but not the specifics. 

Here are the things I do not fully understand:

1.    localhost:8118 connects to localhost:47624 then localhost:47624 connects to localhost:8118.  I assume this is ONE polipo connection but what is the purpose of 8118 connecting to any other port.  I assumed the browser requests to send HTTP traffic through 8118 and then it is pushed through 9050.  What are all these other connections to and from 8118?  The above use of 47624 is just an example. 

2.    The next question is similar.  Tor on locahost:9050 connects to localhost:33825.  Again why does tor need to connect to these other localhost ports?

3.    Additionally, unlike with polipo there rarely seems to be a connection back to tor on 9050.  In the example above 9050 connects to 33825 but 33825 does not then initiate a contact with 9050.  Why not?  However, this does happen sometimes.  For example with localhost:33817 there are connections with ways.  This is uncommon though.

4.    What is localhost:9051 which connects only once to localhost:49280.  I realise this is the "Control Panel" but I'm not exactly clear what it is supposed to do?

Thanks - really appreciate your help. 

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:9050          localhost:33833         ESTABLISHED
tcp        0      0 localhost:9051          localhost:49280         ESTABLISHED
tcp        0      0 [my info]:34424        moria.csail.mit.ed:9005 ESTABLISHED
tcp        0      0 localhost:33783         localhost:9050          ESTABLISHED
tcp        0      0 localhost:33813         localhost:9050          ESTABLISHED
tcp        0      0 [my info]:40043        66.230.230.230:https    ESTABLISHED
tcp        0      0 localhost:9050          localhost:33827         ESTABLISHED
tcp        0      0 localhost:9050          localhost:33825         ESTABLISHED
tcp        0      0 localhost:9050          localhost:33829         ESTABLISHED
tcp        0      0 localhost:8118          localhost:47624         ESTABLISHED
tcp        0      0 localhost:9050          localhost:33790         TIME_WAIT  
tcp        0      0 localhost:9050          localhost:33834         ESTABLISHED
tcp        0      0 localhost:9050          localhost:33787         TIME_WAIT  
tcp        0      0 localhost:47624         localhost:8118          ESTABLISHED
tcp        0      0 localhost:9050          localhost:33830         ESTABLISHED
tcp        0      0 localhost:8118          localhost:47601         ESTABLISHED
tcp        0      0 localhost:33809         localhost:9050          TIME_WAIT  
tcp        0      0 [my info]:38451         inet10156.inetserv:9001 ESTABLISHED
tcp        0      0 localhost:9050          localhost:33810         ESTABLISHED
tcp        0      0 [my info]:33861        61.32.46.4:9001         ESTABLISHED
tcp        0      0 localhost:33831         localhost:9050          TIME_WAIT  
tcp        0      0 localhost:33831         localhost:9050          TIME_WAIT  
tcp        0      0 [my info]:51249        kyra.desire.se:9001     ESTABLISHED
tcp        0      0 localhost:8118          localhost:47623         ESTABLISHED
tcp        0      0 localhost:33818         localhost:9050          TIME_WAIT  
tcp        0      0 localhost:47623         localhost:8118          ESTABLISHED
tcp        0      0 localhost:9050          localhost:33817         ESTABLISHED
tcp        0      0 localhost:33817         localhost:9050          ESTABLISHED
tcp        0      0 localhost:9050          localhost:33838         ESTABLISHED

---

### Post by __p1n__ on 2009-12-17
[http://www.ssfnet.org/Exchange/tcp/tcpTutorialNotes.html#TO](http://www.ssfnet.org/Exchange/tcp/tcpTutorialNotes.html#TO)

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by BkkBonanza on 2009-12-17
Generally speaking those high port numbers are your browser conecting to 9050, 9051 or 8118. Browsers will often open multiple conenctions at a time. If you run netstat as sudo then you get the process id/name which can help with understanding what's talking to what. Usually a connection only shows up once even when traffic is bi-directional, however, there may be something different about how tor does this resulting in double connections going each way. I don't really know why tor would have them both ways.

---

