---
title: "VM's not getting past the install step."
date: 2013-03-16
forum: Virtualisation
---

### Post by Malo Kingi on 2013-03-16
Hello all, 

After selecting which .iso ( I've tried both LinuxMint 14 and Fedora 18) to create the vm with, the install seems to just freeze and nothing happens. I've researched a bit, and I haven't seen anyone with this specific problem, so I'm sure it's something I'm doing (or not doing). Any help would be appreciated. Both times, i've assigned 8gb hhd's and 2BG of base memory to the individual vm's. I'm currently using Ubuntu 12.10. I've also noticed that I don't have the "Enable 2D or 3D acceleration" boxes checked. If any additional information is needed, please let me know.

---

### Post by ibjsb4 on 2013-03-16
2 gig of ram?  How much ram (total) do you have?

---

### Post by Malo Kingi on 2013-03-16
I have a total of 8GB

---

### Post by ibjsb4 on 2013-03-16
Without any error report, Im just checking out the basics so bear with me :)

You installed the packages "dmks" and "build-essential"?

Did you install vBox from the site or the software center?

Try opening virtualbox in terminal and see if it will give you some errors.

And did you look for a virtualization option in BIOS?  Some boxes have it, some don't.

---

### Post by Malo Kingi on 2013-03-16
I believe I installed it from the software center. I ran it in a terminal, and no errors were reported. I haven't looked for a visualization option in bios, I will check to see. The packages "dmks" and "build-essential" I'm not sure if they were installed or not. Is there a way to check?

Edit: I checked the BIOS, no options for visualization (or virtualization).

---

### Post by ibjsb4 on 2013-03-16
> The packages "dmks" and "build-essential" I'm not sure if they were installed or not. Is there a way to check?

In terminal:

```
sudo apt-get install dkms build-essential
```

And reboot or logout

---

### Post by ibjsb4 on 2013-03-16
Also if you installed from the software center, make sure "virtualbox-guest-additions-iso" is installed.

What vBox version are you running?

---

### Post by Malo Kingi on 2013-03-16
Looks like they were installed. Version is 4.1.18. Virtualbox-guest-additions-iso is also installed and up to date.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
dkms is already the newest version.
dkms set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

```

---

### Post by ibjsb4 on 2013-03-16
Have you logged out since the install?

And are you trying to install the guest from a CD or your hard drive?

So far it all looks good.

---

### Post by Malo Kingi on 2013-03-16
I've logged out and restarted multiple times since the install. I'm trying to install the guest from the .iso's I have on my hdd. I thought it may have been the .iso at first, but both of them stop at the same point during the install. Thanks again for all the assistance you're giving me trying to narrow this issue down :).

---

### Post by ibjsb4 on 2013-03-16
Do you have PAE enabled?

[ATTACH=CONFIG]240249[/ATTACH]

---

### Post by ibjsb4 on 2013-03-16
Im going to be stepping out for a few hours so here's one more thought.

I seem to get better results when installing from the vBox site.  You may want to consider removing your current and trying the site.  Remove all virtualbox packages, but leave dkms and build-essentials.  Then gksudo nautilus, go to your File System and do a search on virtualbox.  Remove any leftover packages.

When installing, add it to your software sources as per the instructions under Debian-based distros.

See ya later, good luck :)

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Malo Kingi on 2013-03-16
I'll give installing from the vBox site when I get home from work in a few hrs. Where you were asking if I have PAE installed, I only have the options of 2D and 3D acceleration I believe.

---

### Post by ptm on 2013-03-27
You might verify the location listed in Virtual Box for default -
File
Preferences
General
Machine Folder

 if the drive it's using is too small or too slow (i.e. a USB stick) you will get that kind of error.

---

