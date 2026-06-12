---
title: "/var/tmp over 60GB"
date: 2010-07-29
forum: Server Platforms
---

### Post by chrislynch8 on 2010-07-29
HI,

Strange problem, my /var/tmp directory on Ubuntu is over 66GB in size, I have only 74GB Hardrive so you can imagine my situation.

What is the /var/tmp directory for and should it be deleted on each boot of the File Server?

Rgds
Chris

---

### Post by noway2 on 2010-07-29
The directory is used for applications to create temporary files.  For example, I am working on a web application that sends an ecrypted email and it uses temporary files to hold some of the data.  These files are created in /var/tmp and then unlinked which removes them.  This is kind of a general unsecured storage area where the permissions are set to 777.  

It sounds like you have an application that has gone haywire and is creating files and not cleaning them up.  You may be able to do a find on ones that are older than a certain date and delete them to reclaim space, but you will need to find out which application is causing this behavior.

---

### Post by chrislynch8 on 2010-07-29
Thanks,

Found that all the files in there where related to squid. I managed to delete them all now its just a case of getting squid to work correctly.

Rgds
Chris

---

### Post by chrislynch8 on 2010-07-29
This is now resolved - squid was failing to run correctly so it was failing to remove the cache in /var/tmp

I have the incorrect IP address in the squid.cong for the server I had it configured on so it was unable to open the port.

Rgds
Chris

---

