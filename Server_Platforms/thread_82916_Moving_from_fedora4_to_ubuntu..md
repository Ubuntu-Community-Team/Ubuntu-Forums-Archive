---
title: "Moving from fedora4 to ubuntu."
date: 2005-10-27
forum: Server Platforms
---

### Post by vinjvinj on 2005-10-27
I'm in thr process of moving a grid of 15 fedora servers to ubuntu server. I'm very impressed with my expereince on the first server. Things have gone super smooth. My application is python and uses a lot of python packages and I was able to find most of them. The only one which I have not been able to find is psycopg2. This was not a problem since I just reverted back to psycopg. Also it would be great if you could add matplotlib for python aswell. Luckily I was able to find a package for ubuntu from the lead developers site. 

I also feel much better about my ubuntu server knowing none of the standard ports are open. Its a great feeling to know that I'm somewhat secure.

Question 1
----------
I'm trying to do things right this time around. I was previously using the root account to run the application daemon. I would like to create a user and also a user group for the application. The application runs in daemon mode and there is nothing else running on the server. How should I configure user/group account for the server?

Question 2
----------
I have to configure about 15 such servers. Is there a simple way to have them be built from a image on the network. Is there a how to on this? How difficult would it be to build a pixie server?

Question 3
----------
During setup I just used one large partition? Is this the correct thing to do or should I break it into multiple partitions.

---

### Post by Pygi on 2005-10-27
[QUOTE=vinjvinj]
Question 3
----------
During setup I just used one large partition? Is this the correct thing to do or should I break it into multiple partitions.[/QUOTE]

Try to split to several (at least) two partitions.
If you have more partitions with different mount points,
it will just help your security, loading time, etc.
One of them will should be used for /home directory.

---

### Post by makhand on 2005-12-23
[QUOTE=vinjvinj]Also it would be great if you could add matplotlib for python aswell. Luckily I was able to find a package for ubuntu from the lead developers site. 
[/QUOTE]

I'm trying to do the same. I added the extra repositories as the website said. However, when i try to run the demos, i get complaints about pyGTK not being of a correct version or something. It seems like these packages want to run under python2.3, but my pyGTK seems to only be available for python2.4 under ubuntu breezy. Did you run into these problems?

---

