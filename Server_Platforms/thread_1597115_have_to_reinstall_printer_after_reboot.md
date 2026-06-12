---
title: "have to reinstall printer after reboot"
date: 2010-10-14
forum: Server Platforms
---

### Post by w1ll1am on 2010-10-14
Hello I have ubuntu 10.04 server edition installed on a desktop that I built it is acting as a file server and a print server to four computers in my house. I have no problems with the file server but every time the server gets restarted I have to reinstall the printer on the four computers that its serving can anyone help?

10.04 Ubuntu server edition
HP Laserjet P1006

---

### Post by arrrghhh on 2010-10-15
That's... weird.

So are you sharing it with samba or CUPS?

---

### Post by w1ll1am on 2010-10-15
I am using CUPS I have two Ubuntu computers and my father has two running windows. The computers can print fine but if the server is restarted i have to reinstall it is kind of ridiculous. I might end up switching to a different OS for my server if I can not get this fixed. Of course I will try the newest Ubuntu first. If anyone has any opinions on a good server OS for file and print serving let me know thanks.

---

### Post by arrrghhh on 2010-10-15
Triage it my man.  You haven't given us any info either.  I guess I'll continue to ask questions...

On the workstations, do you print to an IP printer?  This is probably the best way - you shouldn't have to ever reinstall the printers, how do you print to them from the client side?  Do they just disappear off of all client workstations - win&lin...?

---

### Post by w1ll1am on 2010-10-16
> **arrrghhh said:**
> Triage it my man.  You haven't given us any info either.  I guess I'll continue to ask questions...

On the workstations, do you print to an IP printer?  This is probably the best way - you shouldn't have to ever reinstall the printers, how do you print to them from the client side?  Do they just disappear off of all client workstations - win&lin...?

I have the printer install on the server and I go into printers on both ubuntu and windows and click add and find the printer and add it. It then asks for the model and everything so it can install the drivers for it. The printer will continue to work till the server is restated. It still shows that the printer is there in both windows and ubuntu but when i try to print nothing happens it sits and processes forever.

---

### Post by arrrghhh on 2010-10-18
So the printers stop working on both Windows & Linux client machines?  I was going to suggest setting up the printers as a "local" printer on the Windows machine, and make sure to select "Create a new port" and do "Standard TCP/IP" - that way it's a network printer that prints via IP, but the printer is local to the workstation.  That's how we do things @ work, and it works great.

---

### Post by w1ll1am on 2010-10-18
I am tired of trying to mess with it I have it shared with a windows computer that is just about always on so it works now. I may try to reinstall ubuntu and start all over but I am not sure yet. thanks for all the help.

---

