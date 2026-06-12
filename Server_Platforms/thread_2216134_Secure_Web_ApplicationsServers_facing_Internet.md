---
title: "Secure Web Applications/Servers facing Internet"
date: 2014-04-10
forum: Server Platforms
---

### Post by venkata_swamy on 2014-04-10
Hi Team,

Can anybody tell me how to secure web applications configured on ubuntu 12.04 LTS, which should be accessible by clients and people working from remote locations. Web applications will not generate any certificates (like ssl http, shttp), any way configuring any proxy on the same or proxy on other generating secure certificates before connecting to web applications.


Regards
Venkat.

---

### Post by nerdtron on 2014-04-10
I think you need to determine which ports the server is listening to. Since it is a web server with no ssl or https, opening only port 80 for http traffic will be sufficient.
```
sudo ufw allow 80
```
You also need to add an entry for ssh so that you can access it remotely, but be sure to allow only your trusted LAN IPs.
```
sudo ufw allow from [192.168.x.x/24] to any port 22
```
Then you enable UFW
```
sudo ufw enable
```
Verify what you have done so far.
```
sudo ufw status verbose
```

I'm no security expect but these are just minimal setting for a web server. So far I haven't been attacked on these settings. Maybe other experts on the field can share opinions.

---

### Post by Lars Noodén on 2014-04-10
Which web applications?  They do vary quite a bit and the answer(s) depend on which ones you have.

---

### Post by Habitual on 2014-04-10
[https://www.owasp.org/index.php/Main_Page](https://www.owasp.org/index.php/Main_Page)

---

