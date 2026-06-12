---
title: "Samba install without disk"
date: 2006-06-27
forum: Server Platforms
---

### Post by ExMachina on 2006-06-27
I burned ubuntu on a cdrw. 
That cdrw is not here. Is there away to install samba without it?

i used:
sudo apt-get install samba 

and it ask for me to install the cd.
](*,)

---

### Post by breezyfox on 2006-06-27
[QUOTE=ExMachina]I burned ubuntu on a cdrw. 
That cdrw is not here. Is there away to install samba without it?

i used:
sudo apt-get install samba 

and it ask for me to install the cd.
](*,)[/QUOTE]
hi
You need to edit your sources.list and comment the first line where it shows cd.
uncomment other sources list. samba is in universe repository. this repository should be uncommented i.e. removing # sign at the begining of the line.
then 
sudo apt-get update
sudo apt-get install samba

it should work.
To edit sources list use "sudo gedit  /etc/apt/sources.list
bz

---

### Post by ExMachina on 2006-06-27
Im getting an error.
i editedotu the CD line and uncommented the universal lines.

E: Could not get lock /var/lib/dpkg/lock - open ( 11 resource temp. unavailavble)
E: Unable to lock the admin directory (/var/lib/dpkg) is another process using it?

---

### Post by breezyfox on 2006-06-28
[QUOTE=ExMachina]Im getting an error.
i editedotu the CD line and uncommented the universal lines.

E: Could not get lock /var/lib/dpkg/lock - open ( 11 resource temp. unavailavble)
E: Unable to lock the admin directory (/var/lib/dpkg) is another process using it?[/QUOTE]
 
hi
just restart the pc.it normally happens when we try to install programme through other resources. make sure cd is not included. go to synaptic package manager and be sure cd is not included and you are connected to internet.

 hope this will help

bz

---

