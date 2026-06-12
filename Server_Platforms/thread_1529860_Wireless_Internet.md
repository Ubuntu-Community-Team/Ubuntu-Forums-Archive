---
title: "Wireless Internet"
date: 2010-07-12
forum: Server Platforms
---

### Post by BMorganVA on 2010-07-12
[LEFT]I just installed 10.4 LTS and the installation went fine, now when I'm on my server and try to ping somewhere, it doesn't work. I check "ifconfig" and eth0 is set and configured to a degree, but wlan0 doesn't show. Because I am logged in as "root", I don't need to use the sudo command and I type "wlan0 up". wlan0 shows up now, but it's not configured. I don't know how to configure it or know if my device is detected and what its address is. 

Is there anybody who can explain how to correctly configure wireless internet or have links with instructions?

Thanks!
[/LEFT]

---

### Post by ruffEdgz on 2010-07-12
This link seems like a good fit to what you want:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

You will want to read the beginning but the section you will be really interested in is called **"Adding it to /etc/network/interfaces"**.

Hope that helps.

---

### Post by BMorganVA on 2010-07-12
I did what it said, the only thing I did different is not open my network because I am not the administrator. I changed the mode, channel, and essid. When I pinged,  I got the message:

> connect: Network is unreachable

I changed the "inet addr" the the computers IP address and tried, and the router's IP address and tried, I got the same result as the very first one.

Is there and more help that can be offered?

---

### Post by ruffEdgz on 2010-07-13
Once you add the wlan0 interface to the /etc/network/interface file, you will need to restart your network. Once you restart it, see if wlan0 is up with an IP assigned to it by doing the command
```
ifconfig wlan0
```
If you still don't get it to work, copy and paste your /etc/network/interface configuration on this post and we can go from there. Also, please try and explain what steps you have done and any errors/problems along the way.

---

