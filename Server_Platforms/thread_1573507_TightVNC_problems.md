---
title: "TightVNC problems"
date: 2010-09-12
forum: Server Platforms
---

### Post by Z.K. on 2010-09-12
I have set up a print server and SSH is running, but I cannot connect to it from my windows machine with TightVNC client.  I can connect using putty.  Anyone know why?

---

### Post by HermanAB on 2010-09-13
Yes, try connecting to it using Xming and PuTTY instead.

---

### Post by CharlesA on 2010-09-13
> **Z.K. said:**
> I have set up a print server and SSH is running, but I cannot connect to it from my windows machine with TightVNC client.  I can connect using putty.  Anyone know why?
Try Herman's suggestion.

Are you trying to use VNC for a specific reason?

---

### Post by arrrghhh on 2010-09-13
Xming & Putty would be a better solution, because it would forward X.  You have to make sure that X is forwarded in the settings for Putty...

For TightVNC to work to your server, you need to have a vncserver installed... which doesn't do a lot of good unless you have X installed on the server & run a DE.  Which I would not recommend on a server.

---

### Post by Z.K. on 2010-09-18
> **arrrghhh said:**
> Xming & Putty would be a better solution, because it would forward X.  You have to make sure that X is forwarded in the settings for Putty...

For TightVNC to work to your server, you need to have a vncserver installed... which doesn't do a lot of good unless you have X installed on the server & run a DE.  Which I would not recommend on a server.

Ah, that is the answer I was looking for.  I used to use it and it worked fine, but the server I just set up does not have a desktop which I guess is why TightVNC does not work.  Thanks for answering my question.

---

### Post by Bachstelze on 2010-09-18
Obviously, if you want to connect to your server using VNC, you must have a VNC server running on it...

---

