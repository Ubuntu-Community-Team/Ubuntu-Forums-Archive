---
title: "inetd vs xinetd vs nothing"
date: 2009-06-01
forum: Server Platforms
---

### Post by HDave on 2009-06-01
It's been many years since I've messed around with inetd, and I see now that there is this new fangled xinetd.  I need a little education on what the difference is?  

And if all I am running from a server perspective is sshd, samba, and/or vmware server then do I really need either of these at all?  Don't these services all have their own daemons anyway?

---

### Post by iponeverything on 2009-06-01
Your a bit out of touch. xinetd has was released ages ago to addresses some security shortcomings of inetd. The only time I use it now is for tftp.

[http://www.xinetd.org/faq.html](http://www.xinetd.org/faq.html)

---

### Post by HDave on 2009-06-01
Thanks for the pointer.  How come Ubuntu still uses inetd by default?

Also, unless I am need to provide a particular service, should I just disabled it anyway?

---

### Post by iponeverything on 2009-06-02
> Thanks for the pointer. How come Ubuntu still uses inetd by default?

I have no idea why inetd is the default. 


> Also, unless I am need to provide a particular service, should I just disabled it anyway? 


Yes just keep it disabled unless you actually need it.

It does provide different mechanism to control access and offers the ability to run programs or scripts when a service in invoked through xinetd.  (ie. send a notification via email.. attempted ssh login from "IP", or to run ident, finger or to fingerprint the host ) 

It is quite useful if you want keep a close eye your machine.

---

