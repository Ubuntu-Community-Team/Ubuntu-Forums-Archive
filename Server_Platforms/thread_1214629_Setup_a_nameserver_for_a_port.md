---
title: "Setup a nameserver for a port"
date: 2009-07-16
forum: Server Platforms
---

### Post by Chetan26 on 2009-07-16
Hi,
      I  have a registered domain name mysite.com for my  webiste.

      I want to setup name server  for the website

      My website is on  [https://81.xx.xx.xx:8443/wstore](https://81.xx.xx.xx:8443/wstore)

      How can I  configure my nameserver   so that  above URL will
      
      redirect  to  [www.mysite.com](www.mysite.com).


      Can you please help me how to configure the main server.


Many thanks
Chetan

---

### Post by regala on 2009-07-16
> **Chetan26 said:**
> Hi,
      I  have a registered domain name mysite.com for my  webiste.

      I want to setup name server  for the website

      My website is on  [https://81.xx.xx.xx:8443/wstore](https://81.xx.xx.xx:8443/wstore)

      How can I  configure my nameserver   so that  above URL will
      
      redirect  to  [www.mysite.com](www.mysite.com).


      Can you please help me how to configure the main server.


Many thanks
Chetan

what are you trying to setup ? a name server or a www server ?

---

### Post by Chetan26 on 2009-07-16
I have  a registered website name [www.yyy.com](www.yyy.com) .

I have a web appication  running on port 8443.

I have  got a static Ip and I configured it to  [www.yyy.com](www.yyy.com)

I want to configure   website name to the application.


How can I do it?

Can you  please help.

Thanks
Chetan

---

### Post by Chetan26 on 2009-07-16
my  prime idea is  I have  to  replace

[https://xyz.com:8443/](https://xyz.com:8443/)

with

[https://www.xyz.com](https://www.xyz.com)

Please  help me Iam struck here .


Many thanks
Chetan

---

### Post by Cheesemill on 2009-07-16
You cannot have a domain resolve to a specific port, if everything is set up as you say then users just have to go to [www.yyy.com:8443]("http://www.yyy.com:8443") to reach your app.

If you can change the port that the app runs on to port 80 then they could just use [www.yyy.com](www.yyy.com)

---

### Post by scorp123 on 2009-07-16
> **Chetan26 said:**
>  My website is on  [https://81.xx.xx.xx:8443/wstore](https://81.xx.xx.xx:8443/wstore)

How can I  configure my nameserver   so that  above URL will redirect  to  [www.mysite.com](www.mysite.com). This has nothing to do with the name server! A name server will always resolve to complete hostnames. Always.

What you should look into is called "URL rewriting" and it is a feature of the Apache web server, for example. You'd just need to configure it.

---

