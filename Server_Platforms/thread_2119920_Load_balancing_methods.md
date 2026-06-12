---
title: "Load balancing methods"
date: 2013-02-25
forum: Server Platforms
---

### Post by Rpgglitchy on 2013-02-25
Hi there!

I am currently researching some methods on load balancing a webserver. The server has apache2, MySql and ftp services.
My knowledge is fairly limited because I am new to this phenomenon.
I found tutorials to configure load balancing but I cannot seem to find something specific. Like, I want my MySql service on a different server so the webserver will have a smaller burden to bare. An Rsync is also appreciated to share the files between the servers.

Mind you, what I'm asking is just information on how to make the setup. Not install it. I just want to know things like; How many servers are needed, or Use 4 servers with virtual IP domains, put MySql on the last server and Rsync will do the rest, Which servers should have which services or something like that. 

The installation specifics can be found allover the internet :P
Like I said, I just want to become aware of some methods I can use to obtain this webserver loadbalance :D

I thank you for reading my questions and I hope you can help me with this!

Greetings! :guitar:

---

### Post by mckenna1977 on 2013-02-25
Your load balancer needs to balance load between systems. As a load balancer you could use 'pound'. A typical set up would be that traffic would hit the load balancer and the load balancer would forward that traffic on to the server with the least number of active sessions thereby balancing load across those systems. 

Given the systems you're talking about, you might want 1 x load balancer, 2 x Apache server, 1 x mySQL database server.

The above means you'd have your NAT'd web traffic hitting the load balancer forwarding traffic to either web1 or web2 to balance the load and you'd have reduced load on the database due to the separation of functionality across systems.

---

### Post by Rpgglitchy on 2013-02-26
Thank you for the information! Now I got a clearer view on the setup :D 
I'll start my research on how to install this, right away! :D
Thanks again!

---

### Post by Rpgglitchy on 2013-02-27
I have made my setup and wanted to share my knowledge :D Just so I can close this thread and you guys know what I did :D

So. I made a server running Nginx, because pound was kinda outdated, and it bounces requests to one of my backend webservers, configured in my nginx file.
To communicate with my Sql server, I made a location in Nginx to redirect to that server with whatever I type behind my server fqdn. 
Really neat setup! Thx for the support! :guitar:

---

