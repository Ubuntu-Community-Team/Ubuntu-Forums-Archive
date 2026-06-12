---
title: "Gazelle wireless"
date: 2013-03-16
forum: System76 Support
---

### Post by Oliphant on 2013-03-16
Had my Gazelle since June of 2012.  Love it.  Since I've received it I continue to have wireless connection issues but they are temporary.  I'll be in the middle of a download or just searching and either it is slow or I get an error message saying no connection.  Wait about 10-15 seconds and a refresh gets it going again.  

Now, I've reset my router a few times and I just recently received a new one from Comcast.  It still occurs.  When I have my Gazelle at work it occurs there also with that wireless.  My neighbor allowed me to use their wireless to test connectivity.  I will try to report by the end of the weekend how that worked out.  

None of my other wireless devices in the house, tablets or smartphones do not have any connectvity issues.  I don't want to point my finger completely at Gazelle yet but I'm curious if anyone else has similar issues or if its a known issue or if there is something else aside from my ISP?

---

### Post by vect1rx on 2013-03-16
Greetings,

I am here for, quite possibly, the same problem as yourself.      My gazelle wifi works and will, without warning, start to lag all of my network activity out, very quickly coming to a full halt -- but without any nautilus/bus notification of my wireless interface actually being down.

Between an android phone, two android tablets, and a win7 desktop I have no similar problems over the same wireless AP.

To fix, I can fit Fn + F11 once to drop and then once again to re-start the wireless driver and it will connect up to my router without issue.   If I catch it fast enough, my SSH sessions will still be intact.   

But this is not a problem that I've had with other latptops (primarily Dells on which I had Ubuntu, Mint, or dual-boot with Ubuntu) that I've used over linux.

Current wifi router: TPLINK WNDR4300 over the 5Ghz SSID using WPA/WPA2 Personal (AES encryption).

Would love to have things work without having to disable/re-enable wireless networking.

---

### Post by Oliphant on 2013-03-16
Ok my update for the day is I messed around with my neighbors wifi and my router hardwired and encountered the same issue.  THe disconnects last like above a few seconds and return and this is what I noted between Home, neighbor and work connections.  So I can feel comfortable and say I believe it is something with the laptop itself. 

I have another PC in the house running Win7 with a wifi USB on the other side of the house and hasn't had an issue. :(

---

### Post by isantop on 2013-03-18
This sounds like a dud card to me. Go ahead and open a support ticket on our website, and we'll get you a replacement card.

---

### Post by @tomic on 2013-03-22
I have a System76 Gazelle. I chose the Intel Centrino Advanced-N 6235 wireless card.

However, I noticed that I kept on having disconnect problems and timeouts.

This appears to be a problem with the intel driver.

First check your wireless card:
```
lspci |grep -c 6235
```

If it returns 1, you are using this wireless chip

Wireless N can persistently be disabled with:
```
echo options iwlwifi 11n_disable=1 | sudo tee /etc/modprobe.d/51-disable-6235-11n.conf 
```
Courtesy [this thread]("https://bbs.archlinux.org/viewtopic.php?id=146518")

To System76:
I am very happy with my laptop so far, however, I would recommend that you don't ship an adaptor with known issues with the linux kernel.

---

### Post by Oliphant on 2013-03-23
@tomic

Thanks for the info.  It returned a 0 for me.  :)

---

