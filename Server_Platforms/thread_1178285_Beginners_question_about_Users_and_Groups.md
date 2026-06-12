---
title: "Beginners question about Users and Groups"
date: 2009-06-04
forum: Server Platforms
---

### Post by rsmith.tgs on 2009-06-04
Hello

I'm new to Ubuntu and dived in at the deep end :(

I work in a school and they want a server to use as a place for students to upload webpages so they can practice creating websites.

So far I've set up the server, configured ten subdirectories in /var/www called web01, web02, web03 etc. I created 10 users web01, web02, web03 etc and set the home directories to the related directory in /var/www.

So they can go to the address of the server 10.10.10.10/web01 etc... to look at their website.

I used chown to give them right to the directories but now as my user the original account on the server I can't delete or modify anything unless I "sudo" - so I believe I need to do something with groups - I think! 

Can anybody give me a push in the right direction, it's all working but I need to create an account for the teachers to manage the accounts...

Thanks :p

---

### Post by v3xtra on 2009-06-04
Maybe you could add different groups such as web01, web02, and add each member who should own that site to that group, and yourself, and chown the correct directory to the correct group.  For instance:
```

  web01 - users:  jeremy, rsmith
  web02 - users:  timmy, rsmith

  chown web01 /var/www/web01
  chown web01 /var/www/web02


```

It might not be the NICEST way to do it, but it SHOULD work.

---

### Post by rsmith.tgs on 2009-06-04
Thanks for that, sorry to be a bit dim :confused: but I've created the users - how does one create the groups - I've spent too much of my life in GUIs :D

Thanks again

r

---

### Post by ayenack on 2009-06-04
There's a great resource The [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") For most server problems.

---

### Post by rsmith.tgs on 2009-06-05
Thank you ;)

---

