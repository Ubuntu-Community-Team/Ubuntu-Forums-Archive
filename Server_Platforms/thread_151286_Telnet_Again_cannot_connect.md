---
title: "Telnet Again cannot connect"
date: 2006-03-27
forum: Server Platforms
---

### Post by webfoot0 on 2006-03-27
Yes you will all wish to tell me it is insecure.
The server is only acessible on the local network and is an old laptop locally hosting apache and php for development.

Why not ssh - dont know it and requires configuring and from an attempt to use it a while ago cannot easily connect from Mr Gates Box !

Anyway the problem:
installed telnetd
telnet localhost - Unable to connect to remote etc.

/usr.sbin/in.telnetd -debug 
now I can connect but this is only a test mode.

So there is nothing wrong with the files, I guess the service is not being made available by inetd.

the line in /etc/inetd.conf
telnet stream tcp nowait telnetd /usr/sbin/tcpd /usr/sbin/in.telnetd

Is there a problem with the Ubuntu configuration as I am not the first with this problem ?

Any usefull hints 

Keith

---

### Post by jaakan on 2006-04-20
Make sure /etc/inetd exists

if it doesn't do an:
sudo apt-get install netkit-inetd

---

