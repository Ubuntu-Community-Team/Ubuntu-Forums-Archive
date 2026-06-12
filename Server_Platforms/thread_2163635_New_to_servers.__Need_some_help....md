---
title: "New to servers.  Need some help..."
date: 2013-07-19
forum: Server Platforms
---

### Post by SmartGoober on 2013-07-19
I have a few questions....

1) I have a desktop computer, I am trying to move it into another room. I have an old netgear wifi adapter. Can I use the adapter with my server?

2) I am trying to set up webmin, it told me that it was compleated. Now it is giving me this error code...

[COLOR=#ff0000]The requested URL /10000 was not found on this server.[/COLOR]

---

### Post by SeijiSensei on 2013-07-19
To launch webmin point your browser to [https://server:10000/](https://server:10000/) not [s][https://server/10000](https://server/10000)[/s].

---

### Post by SmartGoober on 2013-07-19
I was trying to access it through 192.168.0.XX/10000.

---

### Post by SmartGoober on 2013-07-19
> **SeijiSensei said:**
> To launch webmin point your browser to [https://server:10000/](https://server:10000/) not [s][https://server/10000](https://server/10000)[/s].

Ok, I tried to log in through [https://www.jordan-greenwood-server-ubuntu:10000/](https://www.jordan-greenwood-server-ubuntu:10000/). It gives me this error. 

Unable to connect
      
      
      
      
      
        
        
          Firefox can't establish a connection to the server at jordan-greenwood-server-ubuntu.
        

        
        

  The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.

---

### Post by SeijiSensei on 2013-07-19
Edit (as root with sudo) the file /etc/webmin/miniserv.conf.  Make sure the IP subnet addresses are included in the "allow" directive for any machine you might wish to use.

Did you read [the documentation](http://www.webmin.com/docs.html)?  In particular, [http://doxfer.webmin.com/Webmin/WebminConfiguration?](http://doxfer.webmin.com/Webmin/WebminConfiguration?)

---

