---
title: "How to redirect X11 Display to Cygwin on Windwos machine"
date: 2009-10-09
forum: Server Platforms
---

### Post by bemar on 2009-10-09
Hello,

Ive installed 9.04 Server and now I want to install Oracle 10g for linux.
For that I'm using the HowTo at [http://ubuntuforums.org/showthread.php?t=1182687]("http://ubuntuforums.org/showthread.php?t=1182687")
Oracle wants to start a Window but on the command line server its not possible.

I ve set the DISPLAY variable to "192.168.62.112:0.0". The destination machine is a windows machine on that I've installed Xcygwin and the Cygwin XServer is running. When I try "telnet 192.168.62.112 6000" from my ubuntu machine I can connect so firewall/network reasons are impossible.

When I try
```

oracle@finweb:/etc/X11$ xclock &

```
I get this error
```

[1] 15896
oracle@finweb:/etc/X11$ No protocol specified
Error: Can't open display: 192.168.62.112:0.0

```

Whats the problem?

Thank you 

Regards 
Ben

---

### Post by mpsii on 2010-05-14
Use ```
xhost +
``` to "unlock" the display and allow forwarding.

---

