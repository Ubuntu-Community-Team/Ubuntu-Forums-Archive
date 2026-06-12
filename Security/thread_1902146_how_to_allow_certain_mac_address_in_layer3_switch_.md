---
title: "how to allow certain mac address in layer3 switch 3550 and deny rest"
date: 2011-12-30
forum: Security
---

### Post by Karthikauma on 2011-12-30
Hi 
 
I am working on mac access-list in cisco 3550 layer 3 switch.
 
Here is my config 
 
mac access-list extended ABC
permit host 0035.6983.3654 any
deny any any
 
interface FastEthernet0/23
switchport access vlan 100
switchport mode access
mac access-group ABC in
 
fastethernet 23 is connected to a router. 
 
If i give a continous ping from the mac which i have permitted i am able ping after 20 mins i am getting RTOs 
 
and if i try to add few macs to the permit list i am getting RTOs
 
can somebody help me on this
 
My requirement is to allow few macs and deny rest.

---

### Post by gsgleason on 2011-12-30
I apologize for the less than helpful reply, but this seems rather out of context for this forum.  How is this an Ubuntu security issue?

---

### Post by Ms. Daisy on 2011-12-31
You may be better off in a cisco forum, I found a few on google:
[https://supportforums.cisco.com](https://supportforums.cisco.com)
[http://homecommunity.cisco.com/](http://homecommunity.cisco.com/)

---

### Post by Reddoug on 2011-12-31
Use the ? key when in the port you want to assign mac address to. 
Switch(config-if)#? That will bring up the commands you can use to assign a mac address to the switchport without having to write an access list.

Reddoug

---

### Post by Karthikauma on 2012-01-02
Hi 
 
I have laptop users so i cannot define one mac to one port hence i need to define access-list. 
 
hence pls someone help on this?

---

### Post by gsgleason on 2012-01-03
A moderator needs to either close this thread or move it to a relevant section of the forum.

---

