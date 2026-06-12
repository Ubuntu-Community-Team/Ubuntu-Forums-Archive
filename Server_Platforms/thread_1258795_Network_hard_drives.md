---
title: "Network hard drives?"
date: 2009-09-05
forum: Server Platforms
---

### Post by hockey97 on 2009-09-05
Hi, I am planning to start a website. I am hosting the website from my house. 

I would like to know whats the best setup to host your own website? This meaning how do you manage storage? I was told that I should get network hard drives and have a ethernet or hub switch to keep expanding storage space. 

I just would like to know whats the best system that is easy to expand and handel huge loads of storage space. 

I plan to buy a file cabinet and just put these network hard drives on the selfs. I will make holes for the wireing and will have holes for fans to exahust heat. 

Is this a good setup?

---

### Post by cariboo on 2009-09-05
A website doesn't take up a lot of hard drive space, I would suggest you get three identical hard drives, place one in the computer and the other two in enclosures, use the drives in enclosures for back ups, and keep one off site at all times.

---

### Post by hockey97 on 2009-09-05
> **cariboo907 said:**
> A website doesn't take up a lot of hard drive space, I would suggest you get three identical hard drives, place one in the computer and the other two in enclosures, use the drives in enclosures for back ups, and keep one off site at all times.

I forgot to tell you what the website is about. It's a social network site. 

So I allow photos,messages to be stored on my hard drive. When someone registers on my website. I use php to straight out make the user folder on my hard drive. I then create subfolders for the user for images they upload to messages they upload and their mailbox. I am trying to config postfix to allow users to have a e-mail address with my website.  I will also have iming stuff. 

I am just saying that if the site gets more traffic in the years to come what system is easy enough that if I see the traffice and registrations rise and lots of data be stored on my hard drives I can just quickly buy a hard drive and plug it in. I want it to sync so that like if users add more things it will still be under their user folder but any data that can't fit on that particiular hard drive it will overflow to the next hard drive that has space.

---

### Post by phantasmik on 2009-09-05
I would suggest not making local users for each person using the website. I would go with something along the lines of pureftpd and have virual users listed under one linux user (example: webuser)

---

### Post by hessiess on 2009-09-05
For a social network site where you have a lot of media your upstream bandwith is going to become your bottleneck way before storage space becomes a problem. If you are on a `home' internet connection you need to check that your ISP isnt blocking port 80 and that they don't mind customers running servers.

What makes your sotial networking site different from the already existing and popular serveces which already exist, unless it is truly unique, it will not gain any users. becouse of this it is unlickly that you will need more than a few gigs of storage.

Anyway, for storage, you could just use a RAID5 array and add drives when needed.

---

