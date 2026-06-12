---
title: "UBUNTU 18.04 Server Bionic Beaver SSH Cloud access"
date: 2021-09-28
forum: Server Platforms
---

### Post by saviourmoyo on 2021-09-28
Hello Guys,

i am new in this forum. I am really in need of your help on setting up my xeon hpe server which i installed Ubuntu 18.04.5 Lts server bionic beaver i want to be able to access the server online remotely via SSH and also i want to assign a static IP to it so that users can be able to access my application at [http://mydomain.com:8080/dhis2](http://mydomain.com:8080/dhis2)

please assist me how i can go about this. I would really appreciate if there can be one who can help..

---

### Post by slickymaster on 2021-09-29
*Thread moved to **Server Platforms**.*

---

### Post by ameinild on 2021-09-29
There are a number of considerations for you here:

[LIST=1]
[*]For SSH access to your server, you need to open a port in your firewall (hardware or software) - it's also a good idea to use a non-default port, and to have access restrictions (i.e. only from certain IP ranges etc.) 
[*]Per the above, you should secure your SSH connection as good as possible - for instance see "Tweak #4" in [this video]("https://www.youtube.com/watch?v=OVsMaXQkktQ") 
[*]Getting a static IP address is a concern between you and your ISP - and that's if they offer that option at all 
[*]Alternatively, you can use Dynamic DNS (DDNS) to set [http://yourdomain.com](http://yourdomain.com) to your current IP address - this will require setup with a DNS provider 
[*]You should also consider setting up a reverse proxy with SSL certificates, so your domain will be [https://dhis2.yourdomain.com](https://dhis2.yourdomain.com) instead of [http://mydomain.com:8080/dhis2](http://mydomain.com:8080/dhis2) - for this I use [Nginx Proxy Manager]("https://nginxproxymanager.com/") 
[*]Consider running your services with Docker and Portainer - this makes everything much easier (for me at least) 
[/LIST]
Also, is there any specific reason you installed 18.04 instead of 20.04 (I'm just curious)?

---

