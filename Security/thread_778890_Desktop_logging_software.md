---
title: "Desktop logging software"
date: 2008-05-02
forum: Security
---

### Post by ramdez on 2008-05-02
Hello, I'm looking for a desktop logging software/parental control that runs on linux - particularly ubuntu.  I've found some great software for windows but feel that the opensource community has got to have an equivalent.  The best MS software that I've found so far is SpectorSoft - Spector Pro 2008 .  

Does anyone know of any opensource app that has similar functionality of this software? Myspace logging is of great importance.  Thanks!

---

### Post by rickyjones on 2008-05-02
> **ramdez said:**
> Hello, I'm looking for a desktop logging software/parental control that runs on linux - particularly ubuntu.  I've found some great software for windows but feel that the opensource community has got to have an equivalent.  The best MS software that I've found so far is SpectorSoft - Spector Pro 2008 .  

Does anyone know of any opensource app that has similar functionality of this software? Myspace logging is of great importance.  Thanks!

The only thing that I can think of is to route internet traffic through a proxy server. If I recall correctly then there is a good program, SQUID, that will accomplish URL logging and filtering if properly configured. Though I'm not sure on /how/ to configure it.

-Richard

---

### Post by meanerelk on 2008-11-20
I know this is an old post, but I had this problem a while ago too. A proxy works great for logging internet traffic, but it doesn't do much for logging other system activity.

I gave up after a while in frustration -- a multiuser OS like linux should allow this kind of logging right?

Well, I finally stumbled across the answer today: acct, which does process accounting. Looks like what you are looking for.

---

### Post by hyper_ch on 2008-11-21
why would you log the whole system activity?

---

