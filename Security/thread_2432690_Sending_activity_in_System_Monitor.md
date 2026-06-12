---
title: "Sending activity in System Monitor"
date: 2019-12-06
forum: Security
---

### Post by pme 72 on 2019-12-06
My System monitor on 18.04 is showing what appears to be regular periods of continual Sending activity. Total sent is now reading 19.8MiBs. 

"That means it will take about 500 pages of text to equal one megabyte." -from [https://pc.net](https://pc.net) &#8250; helpcenter &#8250; answers &#8250; how_much_text_in_one_megabyte

1 MiB =500 pages
20 MiB = 10,000 pages? 

Should I be concerned?

---

### Post by crip720 on 2019-12-06
Depends, how long of a time frame, and what programs have you got open.  Also how much is receiving amount?

---

### Post by uRock on 2019-12-06
It also depends on what you're doing. TCP connections require responses. Your system is also constantly communicating with the router. Wanna see what's going communicating? Install and run wireshark. Launch it while all browsers and internet facing applications are closed/disabled. You'll see the constant activity.

There is the option in Gnome settings, under networking, to restrict background communications.

---

### Post by pme 72 on 2019-12-07
20 MiBs over the period of perhaps half an hour or so. My notes do not indicate what I was working on at the time but there were probably some updates and other activity, perhaps 300+MiBs downloaded during that period. 
I'm thinking that I probably accepted the "Yes, send system info to Canonical&#8221; option when 18.04 was installed.

---

