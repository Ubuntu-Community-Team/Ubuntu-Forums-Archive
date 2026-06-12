---
title: "Sharing a printer..."
date: 2008-05-05
forum: Virtualisation
---

### Post by quackquack on 2008-05-05
Hello,

I have an Olivetti Any_Way Photo Wireless Plus printer and it doesn't work in Ubuntu. I have virtualbox and i have installed windows 2000 to a virtual machine. I wondered if it would be possible to install the printer in windows 2000 and share it to ubuntu so as i can print to it while the virtual machine is running. I have tried installing the printer (the printer is set up correctly) and the install wizard doesn't detect the printer on the network (i want to install it wirelessly). I use NAT for my virtual machine and the internet works fine. I thought that maybe the problem was that NAT only gives access to a virtual network to my host and then my host connects to the internet which would explain why it can't access network resources outside of my computer. I wondered if using host interface instead would solve the problem, but i can't figure out how to do it. 

I have tried this guide:
[http://ubuntuforums.org/showthread.php?t=346185]("http://ubuntuforums.org/showthread.php?t=346185")

and changed the ip addresses and network interface names to what they are on my computer and followed the guide properly and when its done i can't start the virtual machine, I have this error message:


Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
Also, it is worth noting that when i run the commands in the thread it gives me a bunch of error messages for a lot of them. 

Is host interface what i need to set up to use the printer? Would it work in the way i explained at the top of the post? If so, can somebody please explain (or link me somewhere that explains) how to set up host interface.

Thanks in advance :)

---

### Post by quackquack on 2008-05-07
bump

---

### Post by quackquack on 2008-05-08
*yawn* bump.

---

### Post by quackquack on 2008-05-08
bump

---

### Post by quackquack on 2008-05-08
bump. Hopefully now someone will answer me :@

---

### Post by quackquack on 2008-05-08
bump

---

### Post by quackquack on 2008-05-08
bumpp

---

### Post by quackquack on 2008-05-08
Bump

---

### Post by quackquack on 2008-05-08
Bummmp

---

### Post by quackquack on 2008-05-08
bump

---

### Post by quackquack on 2008-05-08
bummp

---

### Post by quackquack on 2008-05-08
buump

---

### Post by quackquack on 2008-05-08
for the last time, bump!!!

---

### Post by quackquack on 2008-05-09
since no one has replied to my thread i am going to make a new one. grrr!!!!! :@

---

### Post by mrojas73 on 2008-05-15
Here [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

---

### Post by quackquack on 2008-05-21
oooh it just suddenly worked :lolflag:
i've yet to try share it with ubuntu yet, but hopefully that will work.
thanks to everyone who helped :D

---

