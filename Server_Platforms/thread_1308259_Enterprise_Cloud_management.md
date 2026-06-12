---
title: "Enterprise Cloud management?"
date: 2009-10-31
forum: Server Platforms
---

### Post by jondecker76 on 2009-10-31
I just installed Enterprise Cloud on my EeeBox to start playing with.  The install went fine, and I can go to the IP address of the EeeBox and I get the default webpage, so I know its up and running.

I tried <ip_address>:8443/  to get to the management page but all I get is a small 9kb binary download. (i was expecting a web-based management utility)

So my question is, how do I manage the cloud now?  If I can get this working, I'm going to set up a few nodes on some spare EeeBoxes and start experimenting a bit.


Thanks for any help!

---

### Post by cariboo on 2009-10-31
What kind of file does it want you to download? I assume it is a php file, so make sure you have libapache2-mod-php5 installed.

---

### Post by joeinbend on 2009-11-02
I had this same issue: My bet is you did not prefix the web address with https://

---

### Post by ythe1300 on 2009-11-02
> **joeinbend said:**
> I had this same issue: My bet is you did not prefix the web address with https://

I agree with joe.

---

### Post by dixon1e on 2009-12-27
Having done this same mistake, I am now getting the screen with the login request.  However, according to the documentation, the default is admin/admin.  When I try to use this I get:

Error: Username 'admin' not found

What gives?  I am using UEC 1.6.

---

