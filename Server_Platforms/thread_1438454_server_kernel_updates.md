---
title: "server kernel updates"
date: 2010-03-25
forum: Server Platforms
---

### Post by Mirlyn on 2010-03-25
I'm considering switching my hosting servers to ubuntu server from debian to keep up with my hardware.  I've noticed my other ubuntu desktops want me to restart for a new kernel quite often.  Is the same release frequency seen on the server side?  Can I update the server with everything but kernel images to preserve uptime (these would be NFS or SQL servers)?  I'm no stranger to compiling my own kernels, just would need to learn how ubuntu differs from debian in that department.

I have my test server running 9.01 server amd64, as LTS won't detect my SAS controllers.  Should I wait for 10 to come out and stick with the LTS platform?

Thanks! :)

---

### Post by cdenley on 2010-03-25
> **Mirlyn said:**
> I'm considering switching my hosting servers to ubuntu server from debian to keep up with my hardware.  I've noticed my other ubuntu desktops want me to restart for a new kernel quite often.  Is the same release frequency seen on the server side?  Can I update the server with everything but kernel images to preserve uptime (these would be NFS or SQL servers)?  I'm no stranger to compiling my own kernels, just would need to learn how ubuntu differs from debian in that department.

I have my test server running 9.01 server amd64, as LTS won't detect my SAS controllers.  Should I wait for 10 to come out and stick with the LTS platform?

Thanks! :)

I assume by 9.01 you mean 9.10. The versions are actually dates.
9.04 = April 2009
9.10 = October 2009
10.04 = April 20010

I would either use 9.10, then upgrade to 10.04 in a month, or simply wait for 10.04.

I believe there are security updates for the kernels just as frequently for ubuntu as there is for debian. I wouldn't ignore kernel security updates, but they are usually only exploitable with local access. If you are that desperate to keep your server running, you can check out what the update actually fixes, and decide if it is worth a reboot.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

