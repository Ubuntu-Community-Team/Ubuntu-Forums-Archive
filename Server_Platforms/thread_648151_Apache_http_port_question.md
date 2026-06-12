---
title: "Apache http port question"
date: 2007-12-23
forum: Server Platforms
---

### Post by pizzavortex on 2007-12-23
I have installed apache2 on my laptop (just for a bit of fun.)  I got it to work by using 8080 as my http port instead of 80.  however, to access my webpage I must type [http://localhost:8080](http://localhost:8080).  Is there any way of getting around this so i only have to type [http://localhost](http://localhost).  I can't use port 80 either because of my router or my isp so i would very much like to be able to use 8080 without having to specify it at the end of the URL.

---

### Post by Bachstelze on 2007-12-23
Even if your router blocks port 80, you can very well use it to connect to your server locally, since the traffic does not cross your router.

Of course, if you wish to access it from the outside world, this will be more of a problem. In that case, there is no straightforward way to avoid having to type the port number in the URL. You could just for example ask a friend with some web hosting space to host a script that would redirect users to your server using port 8080. No-ip also has a service for that, which is available with their free DNS redirections.

---

