---
title: "Connection to Server time out"
date: 2012-06-28
forum: Server Platforms
---

### Post by r3dm4n89 on 2012-06-28
Hello, I have just recently set up a home server running ubuntu 12.04 and I have been able to fix all of my problems so far with the help of google but now I am stuck. 

I have set my server up and for the last week have been able to ssh into it from work and friend's houses without a problem. I have forwarded all the necessary ports and again have been able to connect to all my services apache, ventrilo, minecraft, and ssh from my public ip for a little over a week now. I have also set the server to use a static IP address 

But this morning when I woke up I was no longer able to connect over public ip. I restarted the router and was able to connect to everything for a few minutes before timing out. I can still connect to the server locally and the server is still online but I can only access it from the public ip for a few minutes after restarting the router.

The last thing I did was setup gitolite and gitweb which I dont think would effect this but i'm not 100% sure.

I'm really stuck on what could have changed that could have caused this problem so any input would be greatly apperciated.


thank you

---

### Post by kennethconn on 2012-06-28
Is your IP from your ISP dynamic? Could be that. Your Internet connection at home may still work because the router is successfully reconnecting with ISP automatically, but the IP has changed.

---

### Post by r3dm4n89 on 2012-06-28
I dont think that is the case since I am able to connect to my public ip after I reset the router, 2-5mins after resetting the router my connection times out.

---

### Post by kennethconn on 2012-06-28
"I am able to connect to my public ip after I reset the router"
 
Are you connecting while at home (although by public IP)?

---

### Post by r3dm4n89 on 2012-06-28
Yes I am but I was able to do it before and I also have a friend trying to connect from outside my local network using my public ip and he was also timing out.

Just to add here I just went to my router settings and changed the name of where I was opening ports to just a random other name and now I am able to connect. So i'm assuming its something with my router although I don't know what would cause it to block the ports after a certain amount of time.

---

