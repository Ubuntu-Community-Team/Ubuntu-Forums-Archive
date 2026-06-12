---
title: "Problem with Vostro wifi (iwlwifi)"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonicb00m on 2012-03-04
I just installed the new Beta and my internet connection is only 1Mb/s according to the connection information.

After some searching it appears to be a problem with the bluetooth driver, which unfortunately cannot be disabled through hardware without killing the wifi.

I added this line 

echo "options iwlwifi bt_coex_active=0" >> /etc/modprobe.d/modprobe.conf

Which now reports a wifi connection at 150Mb/s but there is no networking in reality. I cannot ping or connect to anything locally, never mind reach the internet.

---

### Post by sonicb00m on 2012-03-07
Turning off "n mode" in the modprobe.conf fixed this and the connection is stable with 54g. Not exactly an optimal solution though :(

---

