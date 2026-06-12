---
title: "Forward a Web server behind firewall to a remote server"
date: 2016-08-03
forum: Server Platforms
---

### Post by john524 on 2016-08-03
I currently have a webserver that is behind a workplace firewall (so I cant access anything if im not behind that network). Currently this server (lets call it ServerA) has a website configured at port 8080, so if i got to ServersA local ip address when im behind the workplace firewall (localip:8080) I get served the webpage and everything is good. 

Now I want to access this webpage when im at my home network. My home network has a ServerB sitting on it which I want to use as a relay. Currently I have successfully SSHed into ServerA this way by doing the following on ServerA 

ssh -f -N -T -R 2828:localhost:22 user@my_public_home_ip

so when i ssh into ServerB I simply do 

ssh -p 2828 ServerA_username@localhost

and I succesfully SSH into ServerA behind the firewall. 

So I essentially want to do the same thing but for the webserver. So on my home network router I have opened port 8888 to direct to ServerB, and on ServerA I try this

ssh -f -N -T -R 8888:localhost:8080 user@my_public_home_ip

but when i try to go to my_public_home_ip:8888 it does not show the webpage on ServerA and simply shows dropped connection in the browser. 

My guess is that ServerB is not configured to handle the HTTP request being fowarded to it on port 8888, so im guessing some magic has to be done on serverB to send the HTTP request through the SSH tunnel to ServerA and back?

Any help is appreciated!

---

### Post by papibe on 2016-08-03
Hi john524.

A few thoughts:

If the goal is to access the web server from your LAN, you don't need deal with your 'my_public_home_ip'. First, you don't need it, as a requisite, to access the web server, and second you would be exposing the private web server to the Internet (I imagine that's not your goal).

Unless several LAN machines are going to access the web server, you don't really need ServerB. You can map the ports locally in your Linux desktop, and access the server.

In any case, you should be able to access the web server by going to 'home_localip:8888'.

Does that help? Let us know how it goes.
Regards.

---

### Post by volkswagner on 2016-08-04
I'm not sure why you need/want to use serverB as a middle man.
I suggest directly ssh from your workstation to the webserver, then access the site on your workstation.
This won't require any ports to be opened on your home router.

```
ssh user@public_IP -L 8080:web_server_private_ip:8080
```

This will allow you to got to [http://localhost:8080](http://localhost:8080) on your workstation to see web content on the remote server. The above
assumes ssh on remote server is on default port. If the web server ssh is listening on -p 2828, the command will be as follows.

```
ssh -p 2828 user@public_IP -L 8080:web_server_private_ip:8080
```

---

