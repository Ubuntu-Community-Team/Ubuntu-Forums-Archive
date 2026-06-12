---
title: "Euca web - &quot;Proxy failed to retrieve Eucalyptus credentials&quot;"
date: 2009-11-23
forum: Server Platforms
---

### Post by Druke on 2009-11-23
So I think I finally got all my eucalyptus stuff running, and I got to try and download an image through the "store" interface.

the error is just this

"Proxy failed to retrieve Eucalyptus credentials"

perhaps I have an interface misconfigured somewhere?

---

### Post by kyi on 2009-11-26
It looks like you didn't start walrus

try use this command to start on your cluster node:

*sudo start eucalyptus-walrus-registration*

Good Luck

---

### Post by schelsky on 2010-03-24
Hi There, 

I installed 10.04-beta1 server and try to install an image. 
I have the same problem "Proxy failed to retrieve Eucalyptus credentials".
There is no eucalyptus-walrus-registration startup script on the system anymore. 
I can start two servers 9.10 and 10.04 side by side and check them. 
Probably you could offer a better fix ?
Thanks

---

### Post by terazen on 2010-03-25
I've got the same issue on 10.04 beta.

---

### Post by Druke on 2010-03-25
I think the issue was that the image stores were down, and I simply needed to wait for them to come back on.

---

### Post by vorgusa on 2010-03-25
I am having the same error for 10.04 beta.  I tried it and it started downloading, but the services reset cause I was updating at the same time.. After rebooting from the update I got the error.  
If its just that the site is down, that would have to be some bad timing

---

### Post by schelsky on 2010-04-13
I downloaded an image and bundled it by hands as described in the manual. 
Then it appeared in my store. 
I was able to run this image, duplicate and do whatever I wanted with it. 

Cheers

---

### Post by mjo_se on 2010-05-09
I had the same error (using Ubuntu 10.04), but found another solution: In the WEB GUI, go to "Configuration" and set "Walrus host" to the IP of the machine running walrus.

---

### Post by pesadilla1973 on 2011-04-06
I had the same error (using Ubuntu 10.04), but found another solution: In the WEB GUI, go to "Configuration" and set "Walrus host" to the IP of the machine running walrus.

---

