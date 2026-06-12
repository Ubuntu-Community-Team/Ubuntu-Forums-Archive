---
title: "runing x programs on a remote display via ssh"
date: 2005-10-09
forum: Server Platforms
---

### Post by ssam on 2005-10-09
i have done a sever install, and installed openssh-server so i can log in remotely

i want to be able to log in with ssh -X an run an x11 application which will display on the computer i logged in from.

do i need to have x11 on both machines?

sam

---

### Post by soce_32 on 2005-10-09
You will need to have X installed on both machines, with an X server running on your local box, but do not necessarily need to run the X server on the server.  When you ssh -X to the server and launch an app, it will connect to your local X server through the ssh tunnell and open up even though X is not running on the server.

---

### Post by lakcaj on 2005-10-09
Enable X11Forwarding **on the server** (/etc/ssh/sshd_config) and install xauth (in xbase-clients) on both the client and the server. Then you can use ssh -X on the client side. Ssh will run xauth and set the DISPLAY variable automatically. Neither xhost, nor X tcp support are necessary. Hint: ssh -X root@localhost, or [http://www.linuks.mine.nu/windows/sshx.html](http://www.linuks.mine.nu/windows/sshx.html)

** This is not my info, just forwarding it, so I take no credit.

---

### Post by wylfing on 2005-10-10
The line you want to change on the server's sshd_config is called (appropriately) X11Forwarding. Change "no" to "yes" and save the file.

The bit about logging in as root isn't necessary though. I don't know why that was advised.

---

### Post by ssam on 2005-10-10
xauth seemed to do the job. thanks

---

