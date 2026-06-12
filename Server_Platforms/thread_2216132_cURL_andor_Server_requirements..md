---
title: "cURL and/or Server requirements."
date: 2014-04-10
forum: Server Platforms
---

### Post by ||0BL1v10N|| on 2014-04-10
Hi Guys,

Apologies in advance if this is in the incorrect forum but I'm having a server issue at present which is bizarrely preventing me from interacting with my Amazon AWS bucket. I'm using AWS S3 PHP SDK v1.6.2 and have created some basic functions to create a bucket, return bucket size etc. I've uploaded the project to a server in work and it works fine on my development environment there. However on my personal ubuntu image I kept getting the error below:

**```
Fatal error: Uncaught exception 'cURL_Exception' with message 'cURL resource: Resource id #42; cURL error: Failed connect to...**
```

From my research it looked like I had been missing (or had issues with) cURL so I purged what was there and re-installed php5-curl. Now All I get is a blank screen with nothing returned when I run my functions. The error message is gone but now I have nothing. The PHP works fine as the rest of the project works as normal. 

Long story short, it looks like I'm missing something from my Ubuntu server which is preventing me from viewing the AWS response. Any help would be kindly appreciated...

Thank you, Niall

---

### Post by Kirboosy on 2014-04-10
Is your computer missing some sort of DNS entry that is present on the AWS instance? Or perhaps a firewall is blocking the traffic between you and the AWS? It looks like wherever the target is its not getting a response. 


Hope that helps!
~Caboose

---

### Post by ||0BL1v10N|| on 2014-05-02
Nop. All DNS entries are fine. I was getting the above error message and now I am not getting any. Really don't want to have to create a new image however I am no closer to finding the source of the problem... :(

---

### Post by ||0BL1v10N|| on 2014-05-06
I'm using PHP:5.5.9 on my server (14.04) apparantly this might be causing the issue. I will downgrade and see if that works.

---

