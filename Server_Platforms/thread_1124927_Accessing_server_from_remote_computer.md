---
title: "Accessing server from remote computer"
date: 2009-04-13
forum: Server Platforms
---

### Post by cmwslw on 2009-04-13
I just finished setting up my server. I know it works because I can go to [http://192.168.0.200/](http://192.168.0.200/) and it displays the iconic "It works!" message. Since I am a server n00b, I have no idea how to access the server from a remote computer. I don't have a domain name set up yet, but isn't there a way to access the server through your IP address? I have set up a static IP in /etc/network/interfaces, but I have heard that you need to obtain a static IP from your ISP. Any suggestions?

Thanks in advance,
Cory Walker

---

### Post by mrsteveman1 on 2009-04-13
If you don't have a static IP you don't truly need one, you merely need to setup a dyndns program of some kind to keep track of your current IP and offer you a domain name to access it with, most of them are free services.

If you do want a real domain though you will of course have to buy one, but you can even use those with some of the dynamic DNS services, or you can request a static IP from your internet provider, they are usually only a few dollars more per month.

What sort of access do you want? A bash shell? In that case you will want to install ssh.

---

### Post by mlinux on 2009-04-13
Try if you can use webmin from remote PC within your internal network (assume your server ip address set to 192.168.0.201)

[http://192.168.0.201:10000/](http://192.168.0.201:10000/)

---

### Post by hardon on 2009-04-13
I used to use the services over at dyndns.org for my ftp server, it worked pretty well. Also, not sure of your ISP but a lot of times even if you have DHCP they rarely revoke your lease, meaning you will have the same IP address for a long time...

---

### Post by amac777 on 2009-04-13
192.168.0.200 is not your external IP address. That is your server's local IP address only used on your local LAN.

Here are the basic steps you will need to follow:

1. Find out your real external IP address by going to a website like: [http://www.whatismyip.com](http://www.whatismyip.com)

2. Configure your router to forward port 80 to your server's local IP address. Every router is different but it's normally pretty easy and there is lots of help available on: [http://portforward.com/](http://portforward.com/)

3. Once you know your external IP address and you have port 80 forwarded, test it from a remote computer by using an external proxy to simulate what a remote computer would see. In other words, browse to your *external* IP address discovered in step 1 at: [http://anonymouse.org/](http://anonymouse.org/)

4. Once all that works, you can get a free domain name (even with a dynamic IP address) if you want (this step is optional): [http://www.no-ip.com/](http://www.no-ip.com/)

---

