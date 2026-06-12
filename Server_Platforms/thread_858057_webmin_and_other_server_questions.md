---
title: "webmin and other server questions"
date: 2008-07-13
forum: Server Platforms
---

### Post by sirdeltalot on 2008-07-13
Hi,
I am a total linux noob, and coming from mac it's a real plunge into the deep end. I have installed ubuntu server 8.04 and now i need to ask a few questions.
Firstly, can i install all tasks-dns, email, lamp etc, then use webmin with them?
Also, when connecting to webmin, where do i find out my ip-what url do i type in?
Lastly, and least importantly, is it a good idea to install a gui?
Thanks
Iz

---

### Post by shizakapayou on 2008-07-15
Webmin should be accessible by browsing to the IP of the server on port 10000.  For example, if your server's IP is 192.168.1.1, then Webmin would be at [https://192.168.1.1:10000](https://192.168.1.1:10000).

I know you can administer DNS via Webmin, in addition to user mail.  It should support most everything you need.

GUI is a very divided subject here.  Personally, I say if you really need it, go for it.  Apart from using extra resources it shouldn't be a big deal.  On the other hand, I'd encourage learning to operate without it.

---

### Post by davidshq on 2008-07-15
Webmin does handle just about everything. I agree, stay away from the GUI if possible. Lot lighter load on your server.
David.

---

