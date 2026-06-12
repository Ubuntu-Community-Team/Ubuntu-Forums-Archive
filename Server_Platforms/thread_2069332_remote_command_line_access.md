---
title: "remote command line access"
date: 2012-10-10
forum: Server Platforms
---

### Post by DonTommy on 2012-10-10
Hey
I got an ubuntu server up running, no GUI.
How can I access it from my other computers in the commandline so that I can add users etc etc?

Thanks

---

### Post by mikewhatever on 2012-10-10
Ssh is probably the most common way.
[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

---

### Post by DonTommy on 2012-10-10
Just what I was looking for thanks :)

---

### Post by chadk5utc on 2012-10-10
I thought I would also add to your reading a little, things to think about. One suggestion I would make is to change the default ssh port it can and will likely save you some headaches, especially if your server is open to the internet.
[https://help.ubuntu.com/11.10/serverguide/security.html](https://help.ubuntu.com/11.10/serverguide/security.html)
[http://ubuntuforums.org/showthread.php?t=831372](http://ubuntuforums.org/showthread.php?t=831372)

---

