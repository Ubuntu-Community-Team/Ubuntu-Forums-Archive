---
title: "Remote ssh"
date: 2006-03-30
forum: Server Platforms
---

### Post by stabface on 2006-03-30
Hi, I work at a small company and I set up  a Ubuntu file server  to share the files around the office I control the server from my desk through SSH. 

I am rather New to all of this after much searching. i decided to ash. 

I would like to SSH into the server form my ubuntu laptop at home. I have full admin rights of everything what do i need to do?

---

### Post by wthanna on 2006-03-30
[QUOTE=stabface]Hi, I work at a small company and I set up  a Ubuntu file server  to share the files around the office I control the server from my desk through SSH. 

I am rather New to all of this after much searching. i decided to ash. 

I would like to SSH into the server form my ubuntu laptop at home. I have full admin rights of everything what do i need to do?[/QUOTE]

You will need to forward port 22 (or whatever port ssh is listening on) on your router to port 22 of the machine you are trying to ssh into..  That should do it.  Then ssh into the ip address of your router that the server connects to the internet with from your laptop.

---

### Post by arkopII on 2006-03-30
[QUOTE=stabface]Hi, I work at a small company and I set up  a Ubuntu file server  to share the files around the office I control the server from my desk through SSH. 

I am rather New to all of this after much searching. i decided to ash. 

I would like to SSH into the server form my ubuntu laptop at home. I have full admin rights of everything what do i need to do?[/QUOTE]

Hello, 

What you need is:

1. Configure your router to redirect the port 22 of public ip to the port 22 of your server ip.
In fact, the number of ports is optional you can choose 3400 to be the public port or 2834 to be the private port.

2. Try to login with ssh using your public ip.
To know what's your public ip check [http://www.whatismyip.org/](http://www.whatismyip.org/) 

3. If your public ip is dynamic (or if you don't want to have to remember numbers) try [www.no-ip.com](www.no-ip.com).

I hope this helps.
If you need more details about any step, don't hesitate to ask. ;-)

---

### Post by stabface on 2006-03-30
ok i had already forwarded the correct port so what you are saying is 
i just need to find out what the ipaddress to my modem is and then i just do something like

ssh XXX.XXX.XXX.XXX:22?

---

### Post by arkopII on 2006-03-30
[QUOTE=stabface]ok i had already forwarded the correct port so what you are saying is 
i just need to find out what the ipaddress to my modem is and then i just do something like

ssh XXX.XXX.XXX.XXX:22?[/QUOTE]


Yes, or if you have a domain name:

ssh yourhost.yourdomain:22

Although :22 is not necesary as it's already the default port.

---

