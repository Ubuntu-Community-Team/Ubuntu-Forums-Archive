---
title: "Help me understand Ubuntu Server, please!"
date: 2012-03-26
forum: Server Platforms
---

### Post by Yoni5002 on 2012-03-26
Hi,

I need to understand apache behavior under Ubuntu Server. I have edited /etc/apache2/apache2.conf

ServerSignature Off
ServerTokens Prod

I have restarted apache, my ubuntu server few times and I have double checked my config file; still my server info is displaying!

I do not have experience with Linux and I must be looking at the wrong place. What Am I doing wrong here!?

Please help me understand...

---

### Post by iiz on 2012-03-26
Hey!

I had this problem in the past, never figured out a proper fix. But what I did was configured the default VHOST to show a blank index.htm, you could use a php script to push a 403 error on top of that.

Hope this helps and if you figure out a solution to hide the server signature please post it here.

thanks!

---

### Post by Yoni5002 on 2012-03-26
> **iiz said:**
> Hey!

I had this problem in the past, never figured out a proper fix. But what I did was configured the default VHOST to show a blank index.htm, you could use a php script to push a 403 error on top of that.

Hope this helps and if you figure out a solution to hide the server signature please post it here.

thanks!

Hey, thanks a lot for your replay.

I did actually find a solution...

I edited /etc/apache2/conf.d/security

Restarted apache and I'm all good now. Hope this helps.

---

