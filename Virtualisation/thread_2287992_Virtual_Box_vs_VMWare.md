---
title: "Virtual Box vs VMWare ? ?"
date: 2015-07-23
forum: Virtualisation
---

### Post by shoaib2 on 2015-07-23
I know all the folks in this forums are good experts and have knowledge.
actually i m a new user, install ubuntu through VMware 7,  also using 2  windows, (window 8.1 & Linux (through VMware)). but when i run Linux through VMware, my pc get down, runs slowly. i need both OS.
although i have haier laptop, core i3, 1.7 processor, 4 GB ram.

so which is the best way, installing Linux ubuntu through Virtual Box or VMware ? ? ?
:confused::confused::confused::confused::confused::confused::confused: ?

---

### Post by v3.xx on 2015-07-23
Try a lighter desktop environment, see if that helps.  You can add "Flashback Desktop (metacity)" to your install and choose which desktop to run at the login screen by clicking on the icon in the top right of the screen.  To install..
```
sudo apt-get install gnome-panel
```
How much ram have you given it?

---

### Post by shoaib2 on 2015-07-24
1.3 GB

what u say now?

---

### Post by howefield on 2015-07-24
Thread moved to the "*Virtualisation*" forum.

---

### Post by v3.xx on 2015-07-24
> **shoaib2 said:**
> 1.3 GB

what u say now?
Try the Flashback desktop.

---

### Post by shoaib2 on 2015-07-24
using vmware(ubuntu), how can i get to know that which desktop now i am using ? and which is the best for beginners ??

---

### Post by howefield on 2015-07-24
> **shoaib2 said:**
> using vmware(ubuntu), how can i get to know that which desktop now i am using ? and which is the best for beginners ??

Try using this command in a terminal..

```
echo $XDG_CURRENT_DESKTOP
```

As to which is best for beginners, depends on the person, "best" is in the eye of the beholder. :)

---

### Post by shoaib2 on 2015-07-24
well.. so i m using UNITY !!

thanks !! 

so vmware is better or virtual box is better ? 
now I have 2gb of ram to vmware for ubuntu !!

---

### Post by howefield on 2015-07-24
> **shoaib2 said:**
> so vmware is better or virtual box is better ? 

Well, again, you have to define what you mean by "better".

Just go to each of their websites and do a feature comparison, then choose the one that suits your workflow best or try both. I used VMware several years ago and switched to Virtualbox when it was still innotek that produced it, love the snapshots feature.

---

### Post by shoaib2 on 2015-07-24
oky fine.. so i have to use vmware now, after that when i get grip, i will use another... or may b dual boot..

---

### Post by shoaib2 on 2015-07-24
so as v3.xx says, try flashback desktop, does it create any problem for me ?
as i m not good in commnds, not a user friendly !!

---

### Post by v3.xx on 2015-07-24
The reason I point you to Flashback is it uses less resources.  You do not have enough virtual resources to run Unity; as you know it is slow.

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by shoaib2 on 2015-07-24
sir v3.xx kindly tell me the step by step process by instaling and configuring the flashback environment..!!

---

### Post by v3.xx on 2015-07-24
> **shoaib2 said:**
> sir v3.xx kindly tell me the step by step process by instaling and configuring the flashback environment..!!
I did :) Post#2

Open a terminal and enter the command in post#2.  No need to configure, it works out of the box.

Its that simple :)

---

