---
title: "Getting Started"
date: 2005-12-19
forum: Server Platforms
---

### Post by drosetti on 2005-12-19
Well, this is my first post here on the ubuntu forums. I just installed the OS about a week ago. 

I was reading through this: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and I saw that I could easily setup an HTTP server, so I did. So now that I have Apache2 setup, as well as PHP4 and MySQL, I want to be able to view my files in /var/www/ on the web. I tried to just put [http://myipaddress/](http://myipaddress/) but nothing showed up.

I am behind a router, but I'm not really sure about how I am supposed to configure it to accept connections from port 80. My router is a D-Link DI-524. If anyone can help me out, that would be great!:) 

DRosetti

Edit: I also noticed that the /var/www/ folder had special permissions on it, so I couldn't put files in there with the GUI. Just wondering how I can get access to that, too.

---

### Post by 23meg on 2005-12-19
Take a look at this: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by invalid on 2005-12-19
You can always bypass the router and visit by

[http://localhost](http://localhost)

---

### Post by drosetti on 2005-12-20
Alright. I have everything setup right and I still can't get the [http://111.222.3.4/](http://111.222.3.4/) thing with my ip to work. I can access it through [http://localhost/](http://localhost/) but what good is that?
I also went into my routers settings and found the port 80 and enabled it. The thing about that is that I wasn't sure what IP it wanted. It says Private IP and I'm not sure which one to put there, my router given one, or the one I get when I go to [www.whatismyip.com](www.whatismyip.com).
The last problem that I can think of is my ISP blocking port 80. My ISP is Direcway. Does anyone know if they block port 80?

Thanks 
DRosetti

---

### Post by biggyfries on 2005-12-21
you will need to check with your ISP, maybe on their support site or by calling.  some ISP's block port 80 coming in, so your router will need to redirect port 80 traffic to a differnt port you specify.  If that is done, then you will need to include the port after the IP address seperated by a colon, for example [http://12.34.56.78:5678](http://12.34.56.78:5678).

remember, if you are behind a router, your PC IP address will be different from what your ISP gave you.

hope this helps.

d

---

