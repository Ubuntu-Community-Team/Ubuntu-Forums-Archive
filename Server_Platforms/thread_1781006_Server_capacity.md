---
title: "Server capacity"
date: 2011-06-12
forum: Server Platforms
---

### Post by ikartz on 2011-06-12
Hi, If I want to have a server being accessed by... let's say about 300 people, what could be the requirements ? I suppose that the main requirement would be the download/upload rates ? or something like that ? a normal host plan would be fine ?

The server is only a website with php and mysql.

Thanks

---

### Post by BkkBonanza on 2011-06-13
It really is impossible to say without some analysis of the application you intend and how much load it puts on the server. Some apps barely use much cpu/disk and some make heavy use - without even a ballpark idea, and some idea of how much each of your 300 users use the app, you would just be making a random guess.

A couple things though: upload/download is not not a heavy use of the server. Most servers can fill a connection continuously without even sweating. Even an old low powered cpu can fill a 100 mbit connection, which is probably much more than you need. So while the net connection you get may have bearing on how much traffic you expect the server itself is going to be determined by how much work (probably database work) your particular app does.

If you can provide more info about how users will use your site and what type of site it is then you may be able to get some ballpark responses from people running similar sites. That may help with an initial choice of hosting plan, and from there you decide based on actually seeing how it works for you. A good rule of thumb for sites is to start small at first, because you have no users, and just adjust as the traffic builds, keeping your options open. ie. don't commit to something or narrow your options.

I've seen companies buy server racks and dedicated connections before even having one user and a finished site, and a year later they are out of business because they never opened the site and spent all their money on servers. Hopefully you won't feel the need to do that. Using something like Amazon EC2 can help with starting small and scaling on demand.

---

