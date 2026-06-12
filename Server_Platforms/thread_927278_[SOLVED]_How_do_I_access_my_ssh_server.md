---
title: "[SOLVED] How do I access my ssh server?"
date: 2008-09-22
forum: Server Platforms
---

### Post by Eto_Demerzel on 2008-09-22
I installed open-ssh server on my home computer to be able to access my files at home through the internet. 

To check if it was installed properly, I tried

```
ssh localhost
```
and I saw it was working.

I tried logging into the server from another computer on the same wireless network

```
ssh my_username@192.168.0.14
```
and I was able to access my files. (192.168.0.14 was the address assigned to me by the router at that time)

Now, how do I access my files through the internet? I'm guessing the command is of the form

```
ssh something1@somthing2 
```
Can you tell me what something1 and something2 would be? How can I find out them? And should I set up some port forwarding on my computer?

Thanks.

---

### Post by baudday on 2008-09-22
Find out what your server's ip is. Just go to google and type in what is my ip and the first site tells you what your global ip or whatever is. And then you just use that. So for instance,

ssh [email]user@your.external.ip[/email]

---

### Post by cariboo on 2008-09-22
If you want to access your computer from the Internet, you will have to set up port forwarding in your router. It would be best to set a static ip address on your server, as dhcp addresses keep changing. Then forward port 22 from your server to the router. then open [canyouseeme]("http://www.canyouseeme.org/") in your browser and check if port 22 is open on your router. Then to access your server from anywhere:

```
ssh user@external_address
```

Where external_address is the external ip address of your router.

Jim

---

### Post by Eto_Demerzel on 2008-09-23
Great! It worked! 

Thanks a lot!

---

