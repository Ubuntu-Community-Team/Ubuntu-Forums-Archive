---
title: "SFTP acces Client-Server"
date: 2012-09-18
forum: Server Platforms
---

### Post by hhaydoura on 2012-09-18
Hello guys, I was asked to make a client with sftp access from server, and i dont know what the steps that i should follow to accomplish this task, anyone can help me??

---

### Post by Lars Noodén on 2012-09-18
You need a server with the package [openssh-server](apt://openssh-server/) installed on it.  Then you can use clients like Dolphin or Nautilus to connect.  Press ctrl-L and then enter the URI for the server, sftp://user@xx.yy.zz.aa/, substituting your user name and the server's address.

There is also a good text-based client in the package openssh-client.

---

### Post by hhaydoura on 2012-09-18
Well, I'm working only on a cmd virtual machine, no GUI, openssh server and client are installed an working fine, next step is .... ???

---

### Post by HermanAB on 2012-09-19
Next step?  Read the ssh and scp man pages...

---

