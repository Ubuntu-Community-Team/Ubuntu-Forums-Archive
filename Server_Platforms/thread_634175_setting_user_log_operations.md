---
title: "setting user log operations"
date: 2007-12-07
forum: Server Platforms
---

### Post by rperrones on 2007-12-07
Hi,

i have an application that execute at each 20 microseconds, and i needs to log ALL application's operations, including its values. But it is happens partially ! In /var/log/user.log each operation is logged, however if an last message entry was repeated for long time, the log service only writes the first occurence, and  follows writing a message: "The last message was repeated XX times". 
Why it is happens? When i changes the frequency of application's execution,  up to 35 microseconds, all messages are logged.
how can i setting ubuntu log service to log ALL user's application messages and prevent the occurence of this problem 

Thanks
Ricardo

---

### Post by HermanAB on 2007-12-07
20 microseconds???  That is rather fast.  To make that work, you would either need a very fast processor and disk drive and/or you need to set up some FIFOs.

If you are really serious about the 20us restriction, consider using a solid state drive/memory card for the logs.

Good luck!

Herman

---

