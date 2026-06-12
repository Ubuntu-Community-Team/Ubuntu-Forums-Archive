---
title: "need help Un able to open port 80 and open my site from other country globally"
date: 2013-05-14
forum: Server Platforms
---

### Post by fasy0007 on 2013-05-14
[COLOR=#000000]hi this is fasy here and first of all im sorry idnt know where i have to post my question so im just new here i m facing a problem actual i installed ubuntu server 12.04 and i configure it i already upload my site to www folder ands its working fine on my local network i saw so many tutorials for port forwarding and with the help of them i did port forward for acces my website globally i did 22 and 21 port forward and chek them on [/COLOR][http://www.yougetsignal.com]("http://www.yougetsignal.com/")[COLOR=#000000] those 2 ports (22 and 21 ) showing open in that site but when i try with same way port 80 its shows me close i did router setting for port forwarding i have linsys router when i tack test in ubuntu router with ufw status it shows me To [/COLOR]

[COLOR=#000000]80 ALLOW Anywhere22 ALLOW Anywhere[/COLOR]
[COLOR=#000000]21 ALLOW Anywhere[/COLOR]
[COLOR=#000000]80 ALLOW Anywhere (v6)[/COLOR]
[COLOR=#000000]22 ALLOW Anywhere (v6)[/COLOR]
[COLOR=#000000]21 ALLOW Anywhere (v6)[/COLOR]
[COLOR=#000000]so i dont know where the problem i did some more search so it says may b ur service provider block port 80 if they block it so can i use an other port for http or i have to install or reconfigure my server for to get the http server im tottaly new user of ubuntu server so please help me out in detail for this thanks in advance[/COLOR]

---

### Post by CharlesA on 2013-05-14
If you don't see port 80 open and you have verified the forwarding rules are correct, your ISP might be blocking it.

---

### Post by fasy0007 on 2013-05-15
thanks for reply but how do i conform that my isp block is and if they block it so is there any other solution that i can use http on my other port or is there any other solution for that

---

### Post by mlinux on 2013-05-15
It will be easier if you install webmin to manage the server. From there, you can change the apache server port to other number. Bear in mind that external access via http will require to add the new port number at the end of the url since it is not the standard http port number.

---

### Post by CharlesA on 2013-05-15
> **fasy0007 said:**
> thanks for reply but how do i conform that my isp block is and if they block it so is there any other solution that i can use http on my other port or is there any other solution for that

You would need to contact your ISP and ask. Generally most residential ISPs block port 80 and usually port 25 as well.

---

