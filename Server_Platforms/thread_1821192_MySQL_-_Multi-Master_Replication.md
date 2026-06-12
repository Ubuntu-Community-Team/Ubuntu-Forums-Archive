---
title: "MySQL - Multi-Master Replication"
date: 2011-08-08
forum: Server Platforms
---

### Post by JBtje on 2011-08-08
Hello :)
 
 
I have two computers (one tower, one laptop). On both the computers, I have apache & PHP & mysql running, so i can program/script anywhere I like.
 
With a simple sync'ing program, the PHP scripts are synced between the PC's, thought the databases arent...
 
Therefor I'm looking for a method to sync (replicate) the databases between the PC's.
thought after setting up some configuration, i'm stuck... now with how to, but what to :)
 
 
**Option 1)** Multi-master replication between the PC and the laptop.
With this setup, the database can ONLY sync once both the devices are turned on. Also it can only sync if they are turned on on my LAN, since they do not have an external static IP address...
 
so, if I turn on both PC's on my LAN, with static IP's (from the DHCP server), this option will work.
Thought, I basically never have both pc's turned on in my own home... cuz i can use only one at the time anyway...
 
 
So I was thinking of another setup
 
**Option 2)** Multi-master replication with: online Server, PC and Laptop.
The server basically contains the most up to date database. for example, the laptop updates the server and the server can update the PC later, once the PC is turned on. Also the other way around, the PC can update the server which can than update the Laptop.
 
There is, if i'm correct, only one problem: the only multi master replications setups I found, use a circulair setup... (1 updates 2, 2 updates 3, 3 updates 1)
 
What I need is to have the PC update the server, but ALSO have the server update the PC (same for the laptop)
 
than there is another (little) problem: the PC and laptop cannot be reached from behind the modem, nor do they have a static IP.
 
 
**My question**:
Is it possible to sync the server with the laptop (that has no static IP), the laptop with the server (that has a static IP), and the same for the PC
 
 
PC <====> Server <====> Laptop
 
Thank you!
Jeffrey

---

### Post by JBtje on 2011-09-08
just for in case anyone likes to know:
 
No, it is not possible.
 
What is possible, is placing the 3 machines in a circle.
1 is slave of 2, 2 is slave of 3, 3 is slave of 1
 
1 --- 2
  \   /
    3
 
The downsite is that all PC's needs to be turned on, in order to work.
Also, dynamical IP's are a pain in the.... so use static, or dont use MySQL replication.
 
JB

---

