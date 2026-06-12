---
title: "USB 3g Wireless in Ubuntu Server"
date: 2009-06-20
forum: Server Platforms
---

### Post by shebangs on 2009-06-20
Hi

Running Ubuntu Server 8.04.

I've used [THIS]("http://ubuntuforums.org/showthread.php?t=1147685") guide to get my MF626 connected.   I can confirm I am seeing the correct vendor and product ID in "lsusb".

However, I don't have a GUI thus no "network connections".


How do I create a ppp connection next and connect?  I tried using wvdial from a couple example configs in google, but after I execute the wvdial it literally crashes the server.  Saying "kernel timeout for 11s" or something.


So yeah, in Ubuntu Server ... how do I turn the /dev/ttyUSB3 into an automatic, 'plug it in and it'll auto connect' Network connection?

Thanks

My ISP is Telstra NextG (3g)

---

### Post by shebangs on 2009-06-20
Or let me rephrase it and explain my situation.

I've made the USB stick appear as a modem with device: "19d2:0031".  This was done via hyperterminal in Windows (found it from googling).

How do I take it to the next step now and having it connected and active?  

It comes up as /dev/ttyUSB3 (thanks to "hal-info") and I used that in my /etc/wvdial.conf

If I clean reboot Ubuntu server 8.04, wait, then insert the USB key it works fine.  wvdial connects and initiates a ppp0 connection.  HOWEVER, it doesn't have an IP and no data is tramsited.  Then 90 seconds later the connection dies with error code 16.    

If I then, try to run wvdial again immediately, it 100% guaranteed will lock the machine.



**Question 1:** When wvdial does connect, why doesn't it get an IP?
**Question 2:** Why is wvdial locking my system?
**Question 3:** Is there any other options outside of wvdial I can use?  Ideally I want it automated, put the key in, and wait few seconds and I'm online via command line.

---

### Post by GeorgeVita on 2009-06-22
Hi **shebangs**,
the info on "Using wvdial to connect with a ZTE mobile broadband modem" is at:
[http://ubuntuforums.org/showpost.php?p=6511814&postcount=2](http://ubuntuforums.org/showpost.php?p=6511814&postcount=2)

Note that if you boot with or without the ZTE modem, system creates /dev/ttyUSB0-1-2-3 **or** /dev/ttyUSB0-1-2 (test it with **ls /dev/ttyU***).

The usable port is the higher number and the /etc/wvdial.conf parameter should match. Also an APN must be set (most providers use "internet"). This can be done with an Init command (AT+CGDCONT=...").

Post here your full /etc/wvdial.conf and a copy of "errors" reported into terminal to check.

Regards,
George

---

