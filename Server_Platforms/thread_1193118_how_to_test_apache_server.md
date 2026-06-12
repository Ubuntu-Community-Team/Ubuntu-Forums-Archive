---
title: "how to test apache server?"
date: 2009-06-21
forum: Server Platforms
---

### Post by xshadow101 on 2009-06-21
hello all,
            I installed ubuntu-server 8.10 in VirtualBox as a guest on XP host. Is there any way to check from host XP that whether the apache is up or not?

What I have tried is to start apache by the command **/etc/init.d/apache2 start** and tried to connect through brower from windows host by entering the ip of guest ubuntu-server. But it didn't work. That is all I could try as there is not GUI in ubuntu-server to use its browser.

Any useful info will be appreciated.

---

### Post by pytheas22 on 2009-06-21
What kind of networking configuration are you using in VirtualBox?  By default, I believe VirtualBox uses NAT and a virtual network to put the guest machine on a separate network from the host.  In this case, you would not be able to view web pages served from the Ubuntu VM on your Windows host, because the two machines are on different networks.

What you probably need to do is switch to host networking, which will allow your Ubuntu VM to connect directly to the same physical network as the Windows host.  I don't know how to configure VirtualBox for host networking with Windows as the host, but I'm sure there are instructions out there.

Also, to test whether the Apache server on the Ubuntu VM is working at all, you could use a text-based browser like lynx (install it with 'sudo apt-get install lynx-cur').  You could also type 'wget [http://localhost';](http://localhost';) if it returns something other than an error message, Apache is working.

---

### Post by quyvuong00 on 2012-10-31
thank for this article, i'm finding a web browser in linux server, and lynx is good choose for me. Thank.

---

### Post by coldraven on 2012-10-31
Try going to [http://192.168.2.101/](http://192.168.2.101/) in your XP browser.
If you see the default Apache web-page it will say "It works!"

---

### Post by lisati on 2012-10-31
From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

