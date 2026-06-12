---
title: "how to active ip address for my server?"
date: 2010-05-08
forum: Server Platforms
---

### Post by bilgee0629 on 2010-05-08
I installed LAMP server at my debian lenny. So people can't view my webpage via my ip address. How to active my ip address?:lolflag:

---

### Post by volkswagner on 2010-05-08
Well, I'm not sure if this is a joke or  just poorly worded, but it sounds like youo need to forward port 80 on your router to your servers internal ip address.

You can find your servers internal ip address by running:

```
ifconfig
``` 

You should also set your servers ip address to static so it wont change.

---

### Post by Iowan on 2010-05-08
If you don't get a static IP address from your ISP, you may need a service like [dyndns.com]("http://www.dyndns.com/") or [no-ip.com]("http://www.no-ip.com/")

---

### Post by bilgee0629 on 2010-05-09
sorry for my english, 
inet addr:10.202.111.53
my ip address. So I've sent my ip address to my friend. My friend couldn't connect my webpage, but I'm seeing my page. I just wanted to ask about this.

---

### Post by cariboo on 2010-05-09
If 10.202.111.53 is your external ip address, you don't have any ports open on your router. You will have to port forward port 80 on your computer to your router, and open port 80 to the world.

I would suggest that you check what other servers you are running, especially check to make sure remote desktop is turn off, or protected by a very strong password, as that is the way that many new users get their system cracked.

---

