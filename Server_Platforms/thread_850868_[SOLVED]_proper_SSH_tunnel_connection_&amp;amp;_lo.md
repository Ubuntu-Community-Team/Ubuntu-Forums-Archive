---
title: "[SOLVED] proper SSH tunnel connection &amp;amp; logout/exit"
date: 2008-07-06
forum: Server Platforms
---

### Post by skunkbad on 2008-07-06
I've specified access denied to all, allowed to 127.0.0.1, for my phpmyadmin directory, and am using SSH tunneling to connect with Firefox. My issue is, when I am done, I can't logout. I have to use Ctrl-C to kill the SSH tunnel.

This is what I'm using to connect:

ssh -N -p 2222 -c 3des [email]user@domain.com[/email] -L 1234/localhost/80

Am I missing a flag or something? Am I logging out correctly by using Ctrl-C?

---

### Post by windependence on 2008-07-06
Try typing exit in the ssh session.

-Tim

---

### Post by skunkbad on 2008-07-06
When the SSH session is started, nothing can be typed. It is only this way because it is tunneling/port forwarding at the server's SSH server to localhost. The normal SSH connection is fine. I'm guessing Ctrl-C is the proper way to close the connection, but I just wanted to see how other people are doing it.

---

### Post by cariboo on 2008-07-06
Actually Ctrl-d works just as well.

Jim

---

