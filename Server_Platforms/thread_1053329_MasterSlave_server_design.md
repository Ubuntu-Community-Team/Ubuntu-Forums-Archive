---
title: "Master/Slave server design"
date: 2009-01-28
forum: Server Platforms
---

### Post by adam35413 on 2009-01-28
I am trying to design a website that I will be able to scale.  The main purpose of the server is to stream flash.  To do this, my primary tools will be:
[LIST]
[*]Lighttp
[*](mod_flv_streaming)
[*]MySQL
[/LIST] 

Conceptually, this is what I would like to happen:
- User 1 connects to server A.  
- A either services the connection or transfers the user to Server B based on load
- User uploads a video to either A or B.
- Database that is shared across the servers is updated with the new video information
- User 2 connects to Server A, and is redirected based on load
- User 2 requests the new video to stream.

So the trick is load balancing, and also streaming the video no matter where it resides amongst the servers  I would love other peoples' input on this.

---

### Post by HermanAB on 2009-01-28
The easiest way to do this is to make multiple identical servers (kept the same using rsync) and distributing the load with round-robin DNS.  Any other method will be a lot more complicated and won't necessarily work any better.

Hope that helps!

Herman

---

### Post by adam35413 on 2009-01-28
Who would have control over the round robin DNS though?  That would have to be on one of the servers right?

I agree that this would be a great solution for a semi-static site, but if we are talking about several TB of videos, that would be a horrific waste of money to have the videos copied over to each instance.  I was trying to find a way to avoid propagation of the videos across all of the servers.

---

### Post by redroad55 on 2009-01-28
It seems to me that some sort of LVM would be best suited .. Read this
[http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")

---

