---
title: "Apache catch all or redirectmatch or wildcard or something"
date: 2012-02-01
forum: Server Platforms
---

### Post by BenWuan on 2012-02-01
Hey all-

I have (2) web-servers

server1 is meant to be on all the time.
server2 is off, and only meant to be plugged in if\when server1 needs fixing.

server2 and server1 have the same mac address, so that the network wont know the diff. Same port, same cable, just when server1 needs fixing will server2 be dusted off and plugged in.

How can i make a friendly "temporary" redirect (302 i think) in apache that will catch all website requests when server1 is taken offline for fixing.

server2 has an index.html file in /var/www thats says "im offline for fixing"

that works but i want it so that if someone goes to any subfolder like 

[http://example.com/photos](http://example.com/photos)

and or 

[http://example.com/photos/somefile.html](http://example.com/photos/somefile.html)

they get redirected to  /var/www/index.html

and 302 friendly, so google knows my site is only temporarily down, and not gone for good or moved.

thanks, all the apache config edits i try get stuck in a loop.

this probably sounds like overkill for a temp webpage, but server2 will also be doing much more in server1's place, they both act as routers \ dhcp servers, ect. But to keep this question on topic, try and ignore that im wasting a spare computer for this task.

thanks

---

### Post by shumifan50 on 2012-02-01
A simple way of dong this would be to make the /var/www on the second server empty and provide a specialised 404 response which is like your index.htm on server2.

---

### Post by BenWuan on 2012-02-01
Thats a really good idea, i will look into how to do that, thanks!

---

### Post by BenWuan on 2012-02-01
Do you think that would hurt my google rankings at all? reporting back 404 to search engines that my home page is missing? Or is the fact that a custom 404 is present enough to let them know the problem is being addresses.

---

### Post by BenWuan on 2012-02-01
Solved, that 404 works great, thanks

---

### Post by BenWuan on 2012-02-01
side note for people wanting to do the same thing.
 
i did need to leave /var/www/index.html there, because if typed right they get no error, and the 404 doesnt load.
 
but a combo of /var/www/index.html and a 404 .htaccess pointing to /var/www/off/off.html worked.
 
maybe i did something wrong, but it took both for me. Great solution, thanks.

---

