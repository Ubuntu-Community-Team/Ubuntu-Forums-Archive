---
title: "apt-cacher"
date: 2005-06-08
forum: Server Platforms
---

### Post by luluguegue on 2005-06-08
hi, 
i'm just install ubuntu on our 20 desktop in our office.  i want package installed on one machine could also be installed on other local machines without Apt downloading it all over agaain, so i follow [http://www.debianuniverse.com/readonline/chapter/19](http://www.debianuniverse.com/readonline/chapter/19) 

but got nothing when i'm open [http://10.10.3.99/apt-cacher/](http://10.10.3.99/apt-cacher/)

trying with lynx , i got some error message :
Connection to 10.10.3.215 closed.
jalu@Lobster:~$ lynx 10.10.3.99/apt-cacher/

Looking up 10.10.3.99 first
Looking up 10.10.3.99
Making HTTP connection to 10.10.3.99
Sending HTTP request.
HTTP request sent; waiting for response.
Alert!: HTTP/1.1 403 Access to cache prohibited
Data transfer complete
more '/tmp/XXXXxULss7/L6161-76TMP.txt'

lynx: Start file could not be found or is not text/html or text/plain
      Exiting...
what should i do?

thanks alot,
sorry for my bad english :)

---

### Post by LordHunter317 on 2005-06-08
I've never heard of apt-cacher so I don't know if it even works.

Install and use apt-proxy, which I know works, and does what you want.

---

### Post by luluguegue on 2005-06-09
just workin :) 

just edit  /etc/apt-cacher/apt-cacher.conf  
in line "allowed_hosts " , this default value is not workin in our ip netwoking configuration.

thanks alot.

---

