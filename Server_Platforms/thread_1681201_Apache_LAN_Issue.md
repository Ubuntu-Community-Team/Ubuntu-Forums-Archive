---
title: "Apache LAN Issue"
date: 2011-02-03
forum: Server Platforms
---

### Post by wgwwm34 on 2011-02-03
So I'm doing some testing with apache and messing around with some web pages but I"m on a rather large lan and would rather not have apache broadcast while I'm testing. I know how to deny all access to users except myself but I was wondering if there was a way to simply have apache not broadcast but still be capable of locally testing. Thanks.

---

### Post by brettg on 2011-02-03
I'm not sure what you mean by "broadcast". Apache doesn't do this. It does however "listen" for incoming connections. 

What is it you are trying to do? 

If you just want to stop people from browsing the site, you can use htaccess to require a password or alternatively you could put a firewall on the host that blocks people coming in except from an authorised address.

The best way is to do all your "mucking about" on a dedicated dev LAN. This keeps everything segregated and you can easily shift stuff to production when you are ready to go live. 

If you mean "local testing" to mean a browser on the same machine you can simply tell apache to listen on the localhost address (127.0.0.1) only.

---

### Post by wgwwm34 on 2011-02-04
Thanks you solved my problem. I clearly don't know what I'm doing but I did mean listen and I just changed listen in ports.conf from 80 to 127.0.0.1:80.

Thanks again.

---

