---
title: "Ubuntu Software not working!"
date: 2016-08-09
forum: Virtualisation
---

### Post by Citta on 2016-08-09
Hi,

clicking an icon or "updates" results in an animated circle, clicking "Categories-Audio" nothing displayed-some empty rectangles....16.04 runs as a VM in VMware Workstation 12 Player. Autohide of the launcher not working, too, in spite of switching. Disappointing! Via terminal I could at least update the OS. But that method is outdated, nowadays.
What might be the problem and the solution?

---

### Post by MAFoElffen on 2016-08-10
On updates, a system, whether VM or physical, needs access to the internet and a valid DNS.

Are your network settings NAT or bridged? 
Are your VM Guest net setting dhcp or static?
In a terminal session:
```

ping -c 3 8.8.8.8
ping -c 3 www.google.com

```
If you have no ping on the first command, then you have no internet access. If you have success with the first and not the second, then you have no valid DNS mapping.

---

### Post by Citta on 2016-08-25
As I did not get an email I assumed no answer, in spite of having all boxes checked. Therefore I logged in  and found your reply-thanks! Before applying your advice I updated the system-worked. Software installation worked, too. Mentioned problem existed with internet access, watching "Intro to Linux" vids worked, browser, etc., too. A little enigma....

---

