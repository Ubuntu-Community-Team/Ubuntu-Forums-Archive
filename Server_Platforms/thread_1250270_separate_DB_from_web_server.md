---
title: "separate DB from web server"
date: 2009-08-26
forum: Server Platforms
---

### Post by zeek333 on 2009-08-26
Hi 
I have 2 web servers in web farm (both server got same data on it) I would like to make another server which will hold all data from 2 webservers. 

is it possible to like this DocumentRoot "//10.0.0.100/www" 

Any idea about this. 

Thanks

---

### Post by compiledkernel on 2009-08-26
You wish to have a seperate DB server to host the data there used on webserver 1 and 2?

---

### Post by zeek333 on 2009-08-26
yes but not just msql data but also all www direstory. Both web servers should take data form one resource which will be separate pc. 

I just got an idea just don't know will it work: If for example on storage pc make one dir of a map network drive and share on both web servers. Is that will  work?

Better could be some solution trought IP.

---

