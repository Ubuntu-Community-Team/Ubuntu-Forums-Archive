---
title: "dhcp troubles"
date: 2009-03-11
forum: Server Platforms
---

### Post by Munkepunk on 2009-03-11
i have been working on a ubuntu server for 3 weeks now and have had no such luck finding any information or trouble shooting whats going wrong with my server set-up.  This computer is serving the purpose of dhcp server and squid to monitor bandwidth and place restrictions on file types.  my problem is that dhcp serves up ip's just fine but when it comes to actually giving them internet access they have none.  I have everything pointed in the right direction and all of my ip address's are setup correctly and same with DNS pointing.  So i guess my question is what info could i be missing.  Pulling my hair out over this any help would be great.  Think of me as a linux beginner when explaining things

---

### Post by HermanAB on 2009-03-11
It sounds like you are missing the default route.
Check the routing table with:
$ sudo route

and set a route with:
$ sudo route add default gw yourisprouter

Cheers,

Herman

---

