---
title: "Access a blocked URL through my home server"
date: 2012-06-18
forum: Server Platforms
---

### Post by hipertrofia on 2012-06-18
Hi all,

We have a URL blocking service at my work place, and the IT guys cannot fix which URLs we have access to, which is a big proble at the moment because there is a work-related Google blog that I need people at work to be able to access. I have a web server at home and was wondering if there is any way of accessing the blog through my server. I'm not talking about an SSH tunnel or anything like that. A tunnel is OK for me, but I need an easy option for the rest of the staff.

What I need is that a request to an URL that points to my server will make the server download the blog and serve it to the client with the client never seeing the original blog's URL or IP.

Any ideas?

Thanks,
Miguel

---

### Post by Cheesemill on 2012-06-18
Using mod_proxy  on your Apache server would enable you to proxy requests to the blocked URL through your server.
 For example accessing [http://www.yourserver.com/googleblog](http://www.yourserver.com/googleblog) would actually return content from [http://googleblog.blogspot.co.uk/whatever]("http://googleresearch.blogspot.co.uk")

---

### Post by hipertrofia on 2012-06-20
That worked great, thanks!

---

