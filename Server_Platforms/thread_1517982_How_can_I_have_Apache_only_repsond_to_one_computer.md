---
title: "How can I have Apache only repsond to one computer?"
date: 2010-06-25
forum: Server Platforms
---

### Post by SlaughterDog on 2010-06-25
So I've got a netbook that I'm running Apache on, and I only want it to serve and talk to my desktop. I don't know much about securing a server, and don't want others able to access it. 

So, how might I accomplish this?

---

### Post by Bachstelze on 2010-06-25
> **SlaughterDog said:**
> So I've got a netbook that I'm running Apache on, and I only want it to serve and talk to my desktop. I don't know much about securing a server, and don't want others able to access it. 

So, how might I accomplish this?

If you really want to prevent all other computers on the network from talking to Apache, you can use hosts.allow to block them on port 80. Another option is to have Apache deny them access to al webpages with Allow/Deny.

---

### Post by SlaughterDog on 2010-06-27
How would I set it to allow connections with my desktop?

---

### Post by GreenN00b on 2010-06-27
Create a file named .htaccess in your document root.
Add the following lines to that file:
```

Order Deny,Allow
Deny from all
Allow from desktop_computer_ip

```
Replace desktop_computer_ip in the code above with the ip address of your desktop computer.

More info on this here: [http://httpd.apache.org/docs/1.3/mod/mod_access.html]("http://httpd.apache.org/docs/1.3/mod/mod_access.html")

---

