---
title: "http server security??"
date: 2008-01-17
forum: Server Platforms
---

### Post by ambush_xx on 2008-01-17
I am thinking about hosting a personal homepage home computer running apache http server. Problem is that i am a totally  ignorant about security
I read article about closing ports etc but no real step-by-step instructions..

So, what are the basic security measures that i need to take???

---

### Post by Dr Small on 2008-01-17
Well, port 80 would need to be open, if you plan to host your own website, but make sure you have a nice wad of bandwidth.

When dealing with HTTP, there isn't much to lock out. Just make sure you have strong passwords and stuff, and make sure you don't have different services like FTP or SSH running that someone could exploit and get into your system.

Dr Small

---

### Post by ambush_xx on 2008-01-17
> **Dr Small said:**
> Well, port 80 would need to be open, if you plan to host your own website, but make sure you have a nice wad of bandwidth.

When dealing with HTTP, there isn't much to lock out. Just make sure you have strong passwords and stuff, [SIZE="4"]and make sure you don't have different services like FTP or SSH running[/SIZE] that someone could exploit and get into your system.

Dr Small

sorry but how do i know if these are running and how do i shut it down

---

### Post by HermanAB on 2008-01-17
If you use Apache with a default install, serving up static pages, then you are quite secure.  Things become tricky when you add dynamic things, scripts, Perl and PHP with database back-ends.

---

### Post by ambush_xx on 2008-01-17
ITs just a few html pages and few pics etc.
so guess its ok to go ahead... :)

---

### Post by ambush_xx on 2008-01-17
But still wont they know my ip address..
Ive heard you can open cd drives and stuff with just the ip address...is it just for windows..

---

