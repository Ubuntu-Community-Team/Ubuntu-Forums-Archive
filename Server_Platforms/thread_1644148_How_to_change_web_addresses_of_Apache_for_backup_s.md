---
title: "How to change web addresses of Apache for backup system"
date: 2010-12-12
forum: Server Platforms
---

### Post by draperdt on 2010-12-12
EDIT: Looks like I posted it in security section. I wanted to start this in server platforms forums. Can some one move the thread please.

I know that this question is aimed more at Apache server and maintenance but I was hoping some one could guide me here. I have tried several places for help but I am getting no where :( ....Here is my background.

Hi,

I have spent all weekend to replicate my development server back at home. I have an Apache remote server with 3 IP based virtual hosts pointing to

1.2.3.4 /var/www/www.a.com
1.2.3.5 /var/www/www.b.com
1.2.3.6 /var/www/www.c.com

Now I have been able to set up a VM on my desktop, installed the OS, the applications, the db server, apache etc. Everything is looking good so far.

So right now I have,

192.168.0.111 at /var/www/www.a.com
192.168.0.112 at /var/www/www.b.com
192.168.0.113 at /var/www/www.c.com
So when I go to 192.168.0.111, I go to [www.a.com](www.a.com) so I guess apache is working aswell.

What I want to do is, instead of going to [www.a.com](www.a.com) I want to change it to another address such as a.me.add1

How can I do this? I am looking through the virtual hosts section, I have changed server name entry etc but its not working.

Can you tell me in big picture what I would need to do to set that up? My current set up doesnt really help me much once the site get the www address.

Sorry if I am not explaining it right. I can provide my conf files if you need them. I have webmin installed.

Or could you tell me if Document Root of IP address 192.168.0.111 points to /var/www/www.a.com, will it always resolve into that webaddress. That is if I enter 192.168.0.111 the browser will redirect it to [www.a.com](www.a.com). What effect does Server Name has in this regard then?
 
I know I havent explained my problem clearly but I guess thats my problem. I just dont know how to articulate my problem either :(

---

### Post by CharlesA on 2010-12-12
You'd need to change yer dns settings to point to the new domain name.

If you are only working on one machine, add the ip to the /etc/hosts file.

---

### Post by draperdt on 2010-12-12
> **CharlesA said:**
> You'd need to change yer dns settings to point to the new domain name.

If you are only working on one machine, add the ip to the /etc/hosts file.

Hi, I have not edited /etc/hosts file yet. 

In apache 192.168.0.111 points to [www.a.com](www.a.com)
In /etc/hosts if I add 192.168.0.111 a.me.z

When I enter the Ip address, will I go to a.me.z or the .com address?

---

### Post by CharlesA on 2010-12-12
It would go to a.me.z.

You'd have to set the virtual host to point there as well, otherwise you can just throw [www.a.com](www.a.com) into the hosts file and leave it at that.

---

