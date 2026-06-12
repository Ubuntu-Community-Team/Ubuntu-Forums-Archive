---
title: "nx + ssh"
date: 2006-11-29
forum: Server Platforms
---

### Post by BeachBum on 2006-11-29
Hello all,

I finally have a basic idea as to how to setup nomachine nx and ssh to run correctly.  I'm trying to allow both ways of connectivity so that I can use ssh from work, where they will not allow me to install the nxclient (but they have securecrt which works just fine), and can use nx on the road, since my connection is terribly slow. 

I'm trying to setup sshd to be as secure as possible, and have managed to force only pub/private key authentication when using normal ssh.  Doing so, however, means the nxclient cannot authenticate.  If I want to continue pursing a ssh/nx setup, I think I need to run two daemons; the ssh-client only sshd will be configured to allow only pub/private key auth, and only allow certain users, and the nxclient only sshd will be configured to allow password auth, and only allow the user "nx".  

Nomachine's docs say that, "To access the server, the client uses a public RSA key. Using this public key forces the SSH server to execute the nxserver shell and prevents any possibility for the special user 'nx' to login on the machine outside NX,"(1) leading me to believe that this setup will be fairly secure.  

So my first question, is this a good idea/ secure setup?  Second, if yes, what do I need to do to run two ssh daemons at the same time?

Thanks for all help!

(1) [http://www.nomachine.com/ar/view.php?ar_id=AR02C00150](http://www.nomachine.com/ar/view.php?ar_id=AR02C00150)

---

