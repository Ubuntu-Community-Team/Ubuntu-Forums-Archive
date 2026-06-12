---
title: "Wpa"
date: 2007-02-25
forum: Server Platforms
---

### Post by p51d78th on 2007-02-25
I am trying to install a file/print server on a spare t42p thinkpad. I can't use the server install disk with Interrupt error thing. I have a command line only base system installed. Is it possible to get WPA working with only the command line? 

David

---

### Post by wieman01 on 2007-02-26
> **p51d78th said:**
> I am trying to install a file/print server on a spare t42p thinkpad. I can't use the server install disk with Interrupt error thing. I have a command line only base system installed. Is it possible to get WPA working with only the command line? 

David
WPA for wireless networking? Yes, it is. Take a look at the HOWTO in my signature.

---

### Post by p51d78th on 2007-03-08
I have gotten the wpa working from the command line. The only thing is i can't do anything online with it. I can ping other computers on the same router. say for instance i try and run

sudo apt-get update i get a screen full of failed to fetch then it gives the address of the file.

any ideas

(i have a command line system only using the alternate cd could that have left some needed files out)

---

### Post by wieman01 on 2007-03-09
> **p51d78th said:**
> I have gotten the wpa working from the command line. The only thing is i can't do anything online with it. I can ping other computers on the same router. say for instance i try and run

sudo apt-get update i get a screen full of failed to fetch then it gives the address of the file.

any ideas

(i have a command line system only using the alternate cd could that have left some needed files out)
Your DNS settings can be found here:
> cat /etc/resolv.conf
Is the right DNS server set? And what does "route" say?
> route
Are you using Firestarter by chance?

---

### Post by p51d78th on 2007-03-13
yeah the dns settings were setup wrong.
i have it working now thanks

---

