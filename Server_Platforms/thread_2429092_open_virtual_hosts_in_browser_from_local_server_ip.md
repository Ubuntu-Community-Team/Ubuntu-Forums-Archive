---
title: "open virtual hosts in browser from local server ip address?"
date: 2019-10-13
forum: Server Platforms
---

### Post by Heeter on 2019-10-13
Hi all

I think that I am having WAN/firewall issues. for the last couple of days, cannot connect to the webserver from outside. Have about 6 virtualhosts running

Would like to access the apache2 virtual hosts from my laptop browser. Server is Ubuntu16.04 LAMP

How do I access the virtual hosts from my laptop webbrowser? I type in:

```

https://192.168.1.105   <----local server address

```

and only one of the vhosts opens up.

Regards

---

### Post by SeijiSensei on 2019-10-13
Create an entry in /etc/fstab with the virtual hosts as aliases:
```

192.168.1.105    www.vhost1.com  www.vhost2.com www.vhost3.com etc.

```

---

### Post by TheFu on 2019-10-13
Virtualhosts require that the client request the "name", not the IP, to know which HTTP/S virtual host is being requested.
[http://vhost1.example.com/](http://vhost1.example.com/)
[http://vhost2.example.com/](http://vhost2.example.com/)
[http://vhost3.example.com/](http://vhost3.example.com/)

Name resolution is up to you to resolve.  Using the /etc/hosts as SeijiSensei suggests inside each client machine is how I'd do it internally, but you might be running an internal-only DNS which could be configured instead.

This assumes the web server is setup correctly for each virtual host. Hard to tell that from the data provided.  The web server log files usually will show if the expected virtual host is being used/found.  I don't use Apache for this, but with nginx, you can get a listing of all the different settings as parsed by the program using **sudo nginx -T**. nginx cannot be running when this option is used.  Handy to save the output to a file to go over carefully - use redirection.

---

### Post by Heeter on 2019-10-13
Great News

Thank you guys, that really helped.

Regards

---

