---
title: "Unable to ssh to server after server reboot"
date: 2010-08-22
forum: Server Platforms
---

### Post by ekaqu on 2010-08-22
Hi, so I have been able to ssh into the server but the server was acting slow, so it was restarted.  After the restart, no one has been able to ssh, not even locally on the box.

ssh localhost -v
...
ebug1: Authentications that can continue: publickey,password
Permission denied, please try again.
ekaqu@localhost's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

when I telnet into port 22 to see if the deamon is running, I see that it is (same message if you do this remotely):


telnet localhost 22
Trying ::1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2

I have been reading over the forums and have been unable to find anything related.  If anyone could help, I would be very thankful.

---

