---
title: "Easiest way to PHP mail()-capable mail server"
date: 2008-12-12
forum: Server Platforms
---

### Post by kepardue on 2008-12-12
I've been able to get most things up and running with 8.04LTS pretty well so far, but the only thing that I'm missing in my server configuration is PHP's mail function.  I don't necessarily need a full blown mail server for each of the several domains that I have on the server, but I do need something for PHP's mail function to work.

What is the most drop-dead easy way of making PHP's mail() function work on a relatively vanilla 8.04LTS server box?

Thanks!

---

### Post by cdenley on 2008-12-12
```

sudo apt-get install nullmailer

```
You also have other options, such as postfix, sendmail, or exim4.

---

### Post by lykwydchykyn on 2008-12-12
I'll second the recommendation for nullmailer.  Stay away from sendmail.  
You also need to make sure your SMTP server allows relaying from the web server.

---

### Post by Dr Small on 2008-12-12
> **lykwydchykyn said:**
>  
You also need to make sure your SMTP server allows relaying from the web server.

Most do, unfortunately

---

