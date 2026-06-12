---
title: "Weird file/directory modes"
date: 2010-05-06
forum: Server Platforms
---

### Post by martinrame on 2010-05-06
Hi, I'm using Ubuntu 9.10 Server at home, and today at work I mounted a directory from my server using sshfs (fuse ssh file system), I didn't have to change anything in the server because the ssh daemon was running. In the client side I had to install sshfs to be able to mount my network share. The client is an ArchLinux.

I successfully mounted the server share in the client PC, and used it for a couple of minutes, but suddenly I started receiving an "Permission Denied" message while trying to navigate (cd, ls) on the mounted directory. Then, unmounted it and logged in to the server using ssh, and noted the directories and files have lost its mode and user/group. This is an example when I did "sudo ls -la":

```
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? 204 - Amazed.mp3
d????????? ? ? ? ?                ? Aerosmith
d????????? ? ? ? ?                ? Alanis
d????????? ? ? ? ?                ? Alejandro Sanz
d????????? ? ? ? ?                ? Alicia Keys
d????????? ? ? ? ?                ? Amy Winehouse
d????????? ? ? ? ?                ? August Hits 2008 Vol. 1
d????????? ? ? ? ?                ? bajofondo
d????????? ? ? ? ?                ? Black Eyed Peas
d????????? ? ? ? ?                ? Calamaro

```

After seeing this, I tried to change the mode with "sudo chmod +rw DIRECTORY" but again, "Permission denied". Then did a "sudo chmod +rwx DIRECTORY and it worked.

If I change again to +rw, the the "????" appears again, so, now I'm forced to live with execution permission in this directory.

Does anyone faced the same problem, a solution?.

My server info is this:
Linux ubuntu-server 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

Thanks in advance,
Leonardo.

---

