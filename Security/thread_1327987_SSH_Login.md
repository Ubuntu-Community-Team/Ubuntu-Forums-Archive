---
title: "SSH Login"
date: 2009-11-16
forum: Security
---

### Post by JimmieC on 2009-11-16
New to SSH and I'm not quite sure of it's capabilities. I have a Joomla site and I would like to Login to the Admistrator module using Public/Private key instead of password and username. I can put the public key on my server but I do not know how to go about logging in to my website's Administrator module. I can use ssh to login to the file structure of my site but so far I can't browse to my site and then login via ssh. Is this beyond the capability of ssh?

Thanks,

Jim

---

### Post by Lars Noodén on 2009-11-16
How is authentication handled in your particular instance of Joomla?

I'm not seeing any general key-based modules:
[http://extensions.joomla.org/extensions/access-a-security/authentication-external](http://extensions.joomla.org/extensions/access-a-security/authentication-external)

Yubikey is close, but that requires a dongle.  

SSH will get you the shell.  Can you do what you want to Joomla using he shell?

---

### Post by osjak on 2009-11-20
> **JimmieC said:**
> New to SSH and I'm not quite sure of it's capabilities. I have a Joomla site and I would like to Login to the Admistrator module using Public/Private key instead of password and username. I can put the public key on my server but I do not know how to go about logging in to my website's Administrator module. I can use ssh to login to the file structure of my site but so far I can't browse to my site and then login via ssh. Is this beyond the capability of ssh?

Thanks,

Jim

JimmieC, Joomla does not have key authentication capabilities, so you cannot log into the admin side of it using keys. 

There is, however, a way to avoid passing your Joomla login in the clear using SSH. You can login to your server via SSH with keys, passing X session back to your computer. Then you start a browser on your server and login to the admin area from your server browser. This is a very cumbersome way because you have to install X on your server and configure SSH to pass X sessions back to you.

I'm not an expert on SSH port forwarding, but I wonder if you can set up a clever ssh port forwarding link to your server that will connect your desktop browser through the ssh link to the web server. May be someone more knowledgeable than me can advice on this.

---

### Post by CharlesA on 2009-11-20
Could try forwarding the port that Joomla uses to yer local machine and connect over an SSH tunnel that way.

---

### Post by Lars Noodén on 2009-11-21
> **osjak said:**
> JimmieC, Joomla does not have key authentication capabilities, so you cannot log into the admin side of it using keys. 

There is, however, a way to avoid passing your Joomla login in the clear using SSH. You can login to your server via SSH with keys, passing X session back to your computer. Then you start a browser on your server and login to the admin area from your server browser. This is a very cumbersome way because you have to install X on your server and configure SSH to pass X sessions back to you.

I'm not an expert on SSH port forwarding, but I wonder if you can set up a clever ssh port forwarding link to your server that will connect your desktop browser through the ssh link to the web server. May be someone more knowledgeable than me can advice on this.

X would be an inefficient way to do it and I would hope that X is not on the server.  

It does point out another tunnelling option.  It's not terribly secure on the server end, but you can set the admin function to only be available to the local host (server).  Then tunnel from your desktop to the server and connect that way.

ssh -L 8700:localhost:80 server.example.org

In the example above, port 8700 on the desktop is connected to port 80 on the server.  From the server's perspective, it is a local connection.  You would access a web page on the server using that method using something like:  [http://localhost:8700/](http://localhost:8700/)

---

### Post by osjak on 2009-11-21
> **Lars Noodén said:**
> X would be an inefficient way to do it and I would hope that X is not on the server.  

It does point out another tunnelling option.  It's not terribly secure on the server end, but you can set the admin function to only be available to the local host (server).  Then tunnel from your desktop to the server and connect that way.

ssh -L 8700:localhost:80 server.example.org

In the example above, port 8700 on the desktop is connected to port 80 on the server.  From the server's perspective, it is a local connection.  You would access a web page on the server using that method using something like:  [http://localhost:8700/](http://localhost:8700/)
Yes, the X way is very cumbersome. I wouldn't do it, but hey, it's an option the OP may prefer, who knows. 

The tunneling idea would prevent someone from sniffing out the admin password. But, on the other hand, it will not prevent a brute force attack on the admin panel, because it will still be visible through the http port 80.

---

### Post by Lars Noodén on 2009-11-22
> **osjak said:**
> Yes, the X way is very cumbersome. I wouldn't do it, but hey, it's an option the OP may prefer, who knows. 

The tunneling idea would prevent someone from sniffing out the admin password. But, on the other hand, it will not prevent a brute force attack on the admin panel, because it will still be visible through the http port 80.

That's what [htaccess](http://httpd.apache.org/docs/2.2/howto/htaccess.html) is for.  It can be set in the web server's configuration file, or if allowed by the configuration, in the relevant directory.  In this case since Joomla is a bunch of scripts it would need to be done in the server configuration file and block anything in the admin path for access except for the local host (127.0.0.0/8 aka localnet or localhost).  Then tunnel to port 80 on the server.

---

