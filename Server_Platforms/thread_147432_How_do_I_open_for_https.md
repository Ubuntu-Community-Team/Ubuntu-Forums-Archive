---
title: "How do I open for https?"
date: 2006-03-20
forum: Server Platforms
---

### Post by StonePiano on 2006-03-20
Hi,

How do I open my machine for https?  I have apache2 running.  I'm serving web pages fine.  However, I can't connect for https.

Please see the output below when I connect fine on port 80, but am refused when I try to connect on port 443.  I'm kinda hoping this is really silly and obvious to you knowledgible types...

```

rhys@granite:~$
rhys@granite:~$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.

Connection closed by foreign host.
rhys@granite:~$
rhys@granite:~$
rhys@granite:~$ telnet localhost 443
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
rhys@granite:~$
rhys@granite:~$

```

---

### Post by gmclachl on 2006-03-20
[http://ubuntuforums.org/showthread.php?t=4466](http://ubuntuforums.org/showthread.php?t=4466) 
 should point you in the right direction. Scroll down until you reach jBilbo and there is a how to there. 

 George

---

