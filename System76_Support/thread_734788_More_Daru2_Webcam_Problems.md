---
title: "More Daru2 Webcam Problems"
date: 2008-03-25
forum: System76 Support
---

### Post by Aug Leopold on 2008-03-25
I've been using Gutsy x64 since system76 started supporting it a while ago. Recently I noticed that my webcam stopped working, so I figured something went wrong and decided to reinstall, after installing the hardy heron beta and checking it out. So here is where I am right now: on a brand new gutsy x64 install with cheese and no drivers, P2 won't do anything, and cheese won't work. On a brand new gutsy x64 install with cheese and the system76 drivers installed, P2 opens the 'Search for file' window, but the webcam still won't work. I tried fresh installs using both the 2.1.7 driver and the 2.1.3 driver, and got the same results both times. I've reformatted like 5 times in the past 3 days and can't get anything to work. Got any ideas system76?

---

### Post by crichell on 2008-03-25
Press the P2 button near the top of the keyboard.  It will turn on your webcam.

---

### Post by Aug Leopold on 2008-03-25
I did. Without the system76 driver it does not turn on the webcam. With the system76 driver, it opens the 'Search for Files' window, but also does not turn on the webcam.

---

### Post by thomasaaron on 2008-03-25
Hi, Aug.

The System76 driver actually does nothing at all to the P2 button.

Are you using Ubuntu or Kubuntu (or some other stripe of Ubuntu). The reason I ask is that we have noticed occasional keymapping issues in other flavors of Ubuntu (particularly Kubuntu).

Also, can you please do this:
Press your P2 button and then tell me the output of this command: lsusb
The press the P2 button a second time and tell me the output of: lsusb

---

### Post by Aug Leopold on 2008-03-25
Ubuntu 7.10 Gutsy Gibbons x64 Desktop

lsusb before P2:
Bus 007 Device 002: ID 147e:2016  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

lsusb after P2:
Bus 007 Device 002: ID 147e:2016  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by thomasaaron on 2008-03-25
Thanks, Aug.

Well, you are right, the P2 key is definitely not bound to the webcam.
One more question while I'm thinking this over: Have you EVER had Windows (particularly VISTA) installed on your DarU2?

---

### Post by Aug Leopold on 2008-03-25
Nope, no Windows whatsoever. It's funny because I was thinking about installing it to make sure this wasn't a hardware issue, but no.

---

### Post by thomasaaron on 2008-03-25
Let's take this to email support.
support(at)system76.com

Please email me with the name the computer was purchased under and/or your order#.

---

