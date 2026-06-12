---
title: "Gust OS (windows 7) has no Internet access after switching form Wi-Fi to Ethernet"
date: 2010-06-22
forum: Virtualisation
---

### Post by sathitth on 2010-06-22
Hello, 

I have Ubuntu 10.04 with Virtual Box (Windows 7 as guest OS). 

After switching (remove Wi-Fi H/W) network access of Ubuntu from Wi-Fi (192.168.1.21) to Ethernet (192.168.1.22), Windows 7 has no Internet access.

Prior to that when I used Wi-Fi
- Windows 7 (192.168.1.23) had Internet access
- Windows 7 could ping Ubuntu and Vice Versa (but not now).

Thanks.
Sathitth

---

### Post by JustinR on 2010-06-23
So what do your network settings in VirtualBox look like?

---

### Post by sathitth on 2010-06-23
Network Adapter - 1:
- Enable Network Adapter: CHECKED
- Attached to: NAT
- Name: BLANK
Advanced:
- Adapter Type: Intel PRO/1000 MT Desktop (82540EM)
- MAC Address: 0800271B8563
-- Cable connected: CHECKED

====================
Other Network Adapter: UNUSED

---

### Post by JustinR on 2010-06-23
Okay that looks good, what are you doing to try to connect to the internet in Windows 7?

---

### Post by sathitth on 2010-06-23
Under Windows 7 (192.168.1.23 / 255.255.255.0):
1. I open IE and got the message and got the message:
"Internet Explorer cannot display the webpage"

2. I open command prompt
c:\ping localhost => is O.K.
c:\ipconfig => IPv4 address: 192.168.1.23; subnet...
c:\ping 192.168.1.22 => Destination host unreachable

Under Ubuntu (192.168.1.22):
3) 
#ping [www.google.co.th](www.google.co.th) => O.K.
# ping 192.168.1.23 => Destination host unreachable

==========

All of the above worked in last week. The only changed was removing wi-fi h/w.

---

### Post by JustinR on 2010-06-23
You said your virtual network hardware was a NAT adaptor? Shouldn't that give an IPv4 something for example, 10.43.42.10, instead of an IP address more similar to a bridged connection?

---

### Post by sathitth on 2010-06-23
I changed Adapter 1 to
- Attached to: Bridge Adapter
then it work.

Thank you 
Sathit T.

---

