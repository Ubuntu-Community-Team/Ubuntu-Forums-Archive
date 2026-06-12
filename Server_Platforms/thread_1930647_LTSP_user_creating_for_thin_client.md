---
title: "LTSP user creating for thin client"
date: 2012-02-24
forum: Server Platforms
---

### Post by psharmad on 2012-02-24
Hi,

I have installed LTSP on my 10.10 and its working. My thin client now are starting nicely and I can see the login screen. But I do not have any login credentials for the machine.  I tried checked on /etc/passwd for users but there are no users. How can I create users for my thin client? 
Has any body tried to manage through it?

---

### Post by HugoSerrano on 2012-02-24
Hello!

You can create a user, just like in a "normal" Ubuntu installation, in your LTSP server.

In command line:
sudo adduser userxpto

type the password twice, and you got a user to login in your Thin Client :-)

Also, you can login with your user from the server, because all you do, it's done based on server installation.

Best Regards!

---

