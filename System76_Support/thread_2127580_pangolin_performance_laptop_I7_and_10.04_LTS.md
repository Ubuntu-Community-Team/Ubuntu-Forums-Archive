---
title: "pangolin performance laptop I7 and 10.04 LTS"
date: 2013-03-20
forum: System76 Support
---

### Post by rpjohns on 2013-03-20
I just bought a system 76 laptop (pangolin performance) with the I7 chip set ([LEFT][FONT=arial]ivy bridge hardware). The machine comes pre-installed with ubuntu 12.10. I need 10.04 LTS because that is the last version that has the JDE (java development env that combines with emacs) available. I really need this software and am considering scraping 12.10 and installing 10.04. Anyone done this?

Thanks[/FONT][/LEFT]

---

### Post by Cheesemill on 2013-03-20
Not a good idea.

Support for 10.04 on the desktop ends next month meaning there won't be any bug-fixes or security patches released.

What is the full name and version of the software you need to run? There may be a way to get it working on 120.4 or 12.10.

---

### Post by rpjohns on 2013-03-20
Thanks for the reply. I realize that 10.04 won't be supported going forward, but it is fairly solid and I'm thinking I could run with it for quite a while. 

The software I need was supposed to be present in 12.04, but was removed from multiverse repository: [https://launchpad.net/ubuntu/precise/+package/jde](https://launchpad.net/ubuntu/precise/+package/jde). However, it appears that it has been removed, I assume because it was broken: [https://launchpad.net/ubuntu/precise/+](https://launchpad.net/ubuntu/precise/+)[COLOR=#000000][FONT=Ubuntu]source/jde/2.3.5.1-5[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by rpjohns on 2013-03-21
The system76 support guy tells me that the ubuntu 10.04 may lack the drivers to run on the new ivy bridge hardware. I'm now thinking maybe the way to go is to run a 10.04 VM on the 12.10 host. Since I'd be basically living in the VM I'd like to give it as much  memory and disk as possible. Given that the new laptop has 16GB ram, and 500GB of disk, any suggestions for how much to give to the VM? I'll probably use Virtual Box. Thanks

---

### Post by 3Miro on 2013-03-22
Sandy Bridge graphics didn't run until 11.04 and it took 11.10 to get them to run well. 10.04 will not be able to run the newer Ivy Bridge.

For VB, it should work fine. On a 16GB machine, I would give 10.04 about 1GB. If you experience problems, you can boost it to 2GB.

---

### Post by rpjohns on 2013-03-22
"On a 16GB machine, I would give 10.04 about 1GB. If you experience problems, you can boost it to 2GB."

1 or 2 GB seems very low. I will be doing java development in the VM with a lot of data base activity. Currently, I am running 10.04 on a desktop with 8GB of ram and the VM on the new machine will basically replace it. As such, I'd like to give the VM as much room as possible without undermining the host.

---

### Post by isantop on 2013-03-22
You should safely be able to give it up to 8 GB. I wouldn't go much higher than that, as it will take RAM to manage the VM.

---

