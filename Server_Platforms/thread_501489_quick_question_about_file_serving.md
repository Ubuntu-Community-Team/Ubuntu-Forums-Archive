---
title: "quick question about file serving"
date: 2007-07-15
forum: Server Platforms
---

### Post by stefansjs on 2007-07-15
Hello,
   I'm not sure if i'm in the right forum, so feel free to yell at me if I am in the wrong place.  I am trying to set up 2 computers right now: 1 to serve files (raid and whatnot) and the other to host mythtv.  I intend to have the file server connected to the network (on campus) and the front end connected only to the file server.  I will check out the networking talk on how to configure the network connections for this (though pointing me to some good documentation would be helpful if you know of any off the top of your head), but what I'd like to know is: If I only ever intend one computer (and one user) to have access to the files, what is the best protocol to set that up?  And is there an easy way to bind the aforementioned protocol to just the front end?
thank you

---

### Post by Frosty Cold Drink on 2007-07-15
> **stefansjs said:**
> Hello,
   I'm not sure if i'm in the right forum, so feel free to yell at me if I am in the wrong place.  I am trying to set up 2 computers right now: 1 to serve files (raid and whatnot) and the other to host mythtv.  I intend to have the file server connected to the network (on campus) and the front end connected only to the file server.  I will check out the networking talk on how to configure the network connections for this (though pointing me to some good documentation would be helpful if you know of any off the top of your head), but what I'd like to know is: If I only ever intend one computer (and one user) to have access to the files, what is the best protocol to set that up?  And is there an easy way to bind the aforementioned protocol to just the front end?
thank you

If your network is secure, you can use NFS. Its not a good idea to have NFS shares on interfaces facing networks where you do not control hosts.

---

