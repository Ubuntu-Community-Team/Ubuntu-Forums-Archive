---
title: "ubuntu 13 inaccessible"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2013-02-16
I can't run software center or software updater

 I can't run apt-get or oneconf from terminal


 I get multiple random system errors 


 [https://www.youtube.com/watch?v=rGAKy_yjYQ0](https://www.youtube.com/watch?v=rGAKy_yjYQ0)


 it started when I removed some software from software center and connected a external usb HFS+ hard drive



 would like to try to salvage this install before formatting the partition...


 any terminal commands that I can run?

---

### Post by TenPlus1 on 2013-02-16
Try holding down SHIFT while booting and go into Recovery Mode, Enable Networking and Repair Broken Packages...  This should help fix everything and allow you to download any new packages that might help remedy the situation...

---

### Post by nomenkultur on 2013-02-20
I have grub2 installed with windows partitions etc...


 regardless of holding down the shift key it always boots me to the grub menu where I can pick

ubuntu

 ubuntu advanced options 

 and e or c to edit the command line

 in C

 I can write 'boot' I think

 but to boot into recovery mode with grub what is the easiest way?

---

### Post by ventrical on 2013-02-20
ubuntu advanced options

then

recovery mode

---

### Post by sgage on 2013-02-20
> **nomenkultur said:**
> I can't run software center or software updater

 I can't run apt-get or oneconf from terminal


 I get multiple random system errors 


 [https://www.youtube.com/watch?v=rGAKy_yjYQ0](https://www.youtube.com/watch?v=rGAKy_yjYQ0)


 it started when I removed some software from software center and connected a external usb HFS+ hard drive



 would like to try to salvage this install before formatting the partition...


 any terminal commands that I can run?

Your computer is not "bricked" - bricked means totally inaccessible, nothing. You turn it on and nothing happens. This usually happens when people mess around with BIOS or other firmware, or when a BIOS flash fails.

Your computer is merely "borked"  :lolflag:

---

### Post by albandy on 2013-02-20
Can you show us the result of typing this:
sudo apt-get install -f

---

### Post by ventrical on 2013-02-20
> **sgage said:**
> Your computer is not "bricked" - bricked means totally inaccessible, nothing. You turn it on and nothing happens. This usually happens when people mess around with BIOS or other firmware, or when a BIOS flash fails.

Your computer is merely "borked"  :lolflag:
I had this happen a few weeks back  but it did not completely 'brick' my system .. but came real close. :)

---

### Post by nomenkultur on 2013-02-21
I apply the term to anything that can't be salvaged...  like my ubuntu install :(

 I'm able to fix broken packages but then running software updater immediately results in system problem detections and freezes and crashes... if I run it multiple times I think I'm able to get some updates in but then it crashes when 'waiting for file prompt' and it's a carousel of errors and freezes.


 at least it lets me report stuff now, so here's that... I should really do a new install but updates or no updates I'm riding this one until at least the beta shows up

---

### Post by ventrical on 2013-02-21
> **nomenkultur said:**
> I apply the term to anything that can't be salvaged...  like my ubuntu install :(

 I'm able to fix broken packages but then running software updater immediately results in system problem detections and freezes and crashes... if I run it multiple times I think I'm able to get some updates in but then it crashes when 'waiting for file prompt' and it's a carousel of errors and freezes.


 at least it lets me report stuff now, so here's that... I should really do a new install but updates or no updates I'm riding this one until at least the beta shows up


That kind of downtime would equal to a 'bricked' system. When the time taken to restore is greater than time for fresh install .. then equals bricked. depends?

---

### Post by philinux on 2013-02-21
> **nomenkultur said:**
> I apply the term to anything that can't be salvaged...  like my ubuntu install :(

 I'm able to fix broken packages but then running software updater immediately results in system problem detections and freezes and crashes... if I run it multiple times I think I'm able to get some updates in but then it crashes when 'waiting for file prompt' and it's a carousel of errors and freezes.


 at least it lets me report stuff now, so here's that... I should really do a new install but updates or no updates I'm riding this one until at least the beta shows up

Dont use software updater.

sudo apt-get update && sudo apt-get upgrade

see what it wants to do. Then replace upgrade with dist-upgrade and again see what it wants to do.

Post back.

---

### Post by jpeddicord on 2013-02-21
> **ventrical said:**
> That kind of downtime would equal to a 'bricked' system. When the time taken to restore is greater than time for fresh install .. then equals bricked. depends?

"bricked" means that your device is as useful as a brick. If it still boots, it is not a brick. :)

OP: Do you remember *what* things you removed from software center when this started happening?

---

