---
title: "How do I install a telnet server?"
date: 2005-12-03
forum: Server Platforms
---

### Post by harisund on 2005-12-03
I am trying to install a telnet server on my Ubuntu 5.10

I did both 
*apt-get install telnetd*
*apt-get install inetutils-telnetd*

This was after I searched for 
*apt-cache search telnet-server*

However, 
*netstat -an*

Doesn't show me port 23 being open. Could anyone please help me open port 23 to listen to incoming connections? Install apache2 automatically opened port 80 and openssh-server automatically opened port 22. Why not with telnet? 

Thanks !

---

### Post by jrib on 2005-12-03
I've never installed telnet but you probably need to open the port.  If you know how to use iptables, cool.  If not, ```
sudo apt-get install firestarter
``` and go to policies.  Then open port 23.  I had to do this to get ssh to work too.

---

