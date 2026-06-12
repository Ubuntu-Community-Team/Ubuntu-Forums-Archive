---
title: "Failure sudo apt-get update"
date: 2015-08-13
forum: Server Platforms
---

### Post by fernando53 on 2015-08-13
Hello, im new on this. Im installed ubuntu server 10.04, and then when i want to do a sudo apt-get udpate, i keep getting 

Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
 Temporary Failure ...<<security.ubuntu.com>>

and a lot of this with 
ar.archive.ubuntu.com

I try this in tuesday and now im tryng this today with the same results.

I do a ping to localhost and work , and do ping to 8.8.8.8 , this doesnt work.

Any help? Thx in advanced!

---

### Post by Bucky Ball on 2015-08-13
10.04 LTS is no longer supported. Please start again with 14.04 LTS and then report any issues you have in a new thread. 

You say you have installed 10.04 (where from?) but you are getting an error that concerns Trusty. That is 14.04 LTS ... :-k

Looks to me like there might be a mix up, with the repositories or with the release you have actually installed. What was on the machine previously? 

Anyway, the repos for 10.04 are no longer and that is why you will continue to get errors with 10.04. Install 14.04. Good luck. ;)

---

### Post by fernando53 on 2015-08-13
> **Bucky Ball said:**
> 10.04 LTS is no longer supported. Please start again with 14.04 LTS and then report any issues you have in a new thread. 

You say you have installed 10.04 (where from?) but you are getting an error that concerns Trusty. That is 14.04 LTS ... :-k

Looks to me like there might be a mix up, with the repositories or with the release you have actually installed. What was on the machine previously? 

Anyway, the repos for 10.04 are no longer and that is why you will continue to get errors with 10.04. Install 14.04. Good luck. ;)
My bad, i install 14.04.1 LTS, the server version ([http://old-releases.ubuntu.com/releases/14.04.2/](http://old-releases.ubuntu.com/releases/14.04.2/)) . I used that, because my boss want a server for testing some things , so i checked the system information in the liveserver and is using 14.04.1 LTS , so i tryng to replicate in the sameway . In the machine previously was a ubuntu with desktop graphics , but dont know what version , but i formated the disk, it was a clean installation.

---

