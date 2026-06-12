---
title: "Slow web browsing in Ubuntu"
date: 2010-05-08
forum: System76 Support
---

### Post by ifwillems on 2010-05-08
I have a Bonobo with 64bit Ubuntu 10.04 installed. The following was already a problem when I ran 9.10, and I still have it with 10.04:

I hook up my bonobo to my home LAN (wired), and I hook up an old Thinkpad with Windows XP to the same home Lan (also wired). On both machines I start up Firefox or Chrome (it doesn't matter, results are the same). Almost all the time the Windows browser is faster with bringing up a web page than the Ubuntu machine. It seems as if the browser on Ubuntu takes longer to find the page, and then displays it as fast as the browser in XP.

I also tried to compare Chromium in Ubuntu with Firefox in Ubuntu, and I see no difference. 

Based on the above I assume there is nothing wrong with my router (DNS) settings, but that it has to do something with the Ubuntu settings in my OS. Anyone any idea what to look for?

Ivo

---

### Post by jdb on 2010-05-09
> **ifwillems said:**
> I have a Bonobo with 64bit Ubuntu 10.04 installed. The following was already a problem when I ran 9.10, and I still have it with 10.04:

I hook up my bonobo to my home LAN (wired), and I hook up an old Thinkpad with Windows XP to the same home Lan (also wired). On both machines I start up Firefox or Chrome (it doesn't matter, results are the same). Almost all the time the Windows browser is faster with bringing up a web page than the Ubuntu machine. It seems as if the browser on Ubuntu takes longer to find the page, and then displays it as fast as the browser in XP.

I also tried to compare Chromium in Ubuntu with Firefox in Ubuntu, and I see no difference. 

Based on the above I assume there is nothing wrong with my router (DNS) settings, but that it has to do something with the Ubuntu settings in my OS. Anyone any idea what to look for?

Ivo

Just a wild guess but I had a similar problem once.

I had an extra entry in /etc/resolv.conf that was bogus.
It spent time looking for the bogus DNS (Domain Name Server) before it used the real one.

I don't know how it got there but when I removed it the sky turned blue.

jdb

---

### Post by ifwillems on 2010-05-11
Yes, that did the trick. I now have the same DNS servernames in the file as I have in my router. Performance problems have now been resolved.

Thanks!

Ivo

---

### Post by fossum_13 on 2011-02-02
I had the same issue and that will fix it, but if you're like me you want to know why.

Here's how:
1. Use dig to test your current results
    dig will list at the bottom who is supplying the info (eg. ;; SERVER: 192.168.1.1#53(192.168.1.1)) and how long (eg. ;; Query time: 74 msec)
    these are ACTUAL results from my test and could be considered the norm if you run this test from a home network. Query returned in 64 ms from google's 8.8.8.8 server.

The funny thing is I removed google's DNS and it worked just fine for me. Even though it added itself again later, it still had a fast response...

Any new info I'll post :p

---

