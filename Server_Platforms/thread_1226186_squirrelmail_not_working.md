---
title: "squirrelmail not working"
date: 2009-07-29
forum: Server Platforms
---

### Post by pawan_lal on 2009-07-29
hello friends,
i  had configured postfix,. my isp has blocked port 80 so i have to run squirrelmail on diffrent port so i changed the port to 3333 

vi /etc/apache2/ports.conf

Listen 3333

<IfModule mod_ssl.c>
    Listen 443
</IfModule>


n than i did port forwarding  3333 on my router also but i am not able to access squirrelmail from outside. i am using dyndns.org in my company.   
plz guide me in squirrelmail in which file i had to edit 

thx

---

### Post by hessiess on 2009-07-29
Your ISP may have another NAT router between you and your external IP, or the company network from where you are trying to assess your server may be blocking everything besides port 80. In both cases there is nothing you can do besides changing ISP, using a server outside the network as the external acsess point, and using NAT traversal to get to your server (defeats the whole point of running a server), or try to get your ISP to give you a real/static IP.

---

