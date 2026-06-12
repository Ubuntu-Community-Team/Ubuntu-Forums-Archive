---
title: "my web server is not accessible thru other network"
date: 2016-12-22
forum: Server Platforms
---

### Post by lotakoka on 2016-12-22
Hi
I have webserver installed on ubuntu 16.04 LTS. It has ip address 192.168.1.10 and my ISP router ip address 68.199.10.32 here i have port 80 forwarded to my webserver ( 192.168.1.10). If i am at 192.168.1.x network it works fine ( [http://68.199.10.32/](http://68.199.10.32/)). But if i switch to other network like ( optimum wifi ) and my laptop gets ip address 25.214.241.166 then i try to connect my webserver ( [http://68.199.10.32](http://68.199.10.32)) it does not work.
      i know they are different network. what should i do ? should i contact IINTERNET SERVICE PROVIDER and ask for ip address which is open to internet so every body can ping( get my website) ?

---

### Post by Habitual on 2016-12-22
> **lotakoka said:**
> Hi
I have webserver installed on ubuntu 16.04 LTS. It has ip address 192.168.1.10 and my ISP router ip address 68.199.10.32 here i have port 80 forwarded to my webserver ( 192.168.1.10). If i am at 192.168.1.x network it works fine ( [http://68.199.10.32/](http://68.199.10.32/)). But if i switch to other network like ( optimum wifi ) and my laptop gets ip address 25.214.241.166 then i try to connect my webserver ( [http://68.199.10.32](http://68.199.10.32)) it does not work.
      i know they are different network. what should i do ? should i contact IINTERNET SERVICE PROVIDER and ask for ip address which is open to internet so every body can ping( get my website) ?
Or  your ISP may not allow port 80 and/or port forwarding enabled at the router?

If you switch to another network on your laptop, your webserver at 68.199.10.32 is still there, unless your webserver is on your laptop,

---

### Post by lotakoka on 2016-12-22
Hi
I am able to port forward at my router and i have tested it work within my network. I have feeling my router needs public ip address so public can see it. who can help on this ?

---

### Post by SeijiSensei on 2016-12-22
Browsing to [http://68.199.10.32/](http://68.199.10.32/) brings up the Apache default page, so forwarding seems to be working properly unless there's a site that is supposed to appear at that address.

---

### Post by lotakoka on 2016-12-22
Figured out. My ISP were blocking port 80. They opened it for $4.95 monthly( nothing is free in this world ).

Thank you all

---

### Post by lotakoka on 2016-12-22
Just got opened port 80.

---

### Post by SeijiSensei on 2016-12-23
> **lotakoka said:**
> Figured out. My ISP were blocking port 80. They opened it for $4.95 monthly( nothing is free in this world ).
Actually that's remarkably cheap.  Most ISPs block inbound connections on ports like 80 and 25 to prevent residential users from running servers which they see as a business service.  Upgrading to a business-class Internet connection costs a lot more than $5/month in most cases.

---

