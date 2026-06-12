---
title: "&quot;shim&quot; package in a limbo state inside apt"
date: 2023-10-05
forum: Ubuntu, Linux and OS Chat
---

### Post by domih2 on 2023-10-05
For several months I had the "shim" package in a limbo state inside apt.

**sudo apt upgrade -y** always returns:
.../...
The following packages have been kept back:
  shim
.../...
[B]
sudo apt install shim[/B] says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  shim-signed
The following packages will be upgraded:
  shim
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  shim-signed
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 7,152 B of archives.
After this operation, 5,230 kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

**sudo apt remove shim** says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  shim shim-signed
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  shim-signed shim (due to shim-signed)
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 5,258 kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] The following packages have been kept back:
  shim

I aborted in each case given the warning.

I have, via **apt list shim***:
.../...
shim-signed/now 1.41+15+1552672080.a4a1fbe-0ubuntu1 amd64 [installed,local]
shim/focal-updates,focal-security 15.7-0ubuntu1 amd64 [upgradable from: 15+1552672080.a4a1fbe-0ubuntu1]
.../...

**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal

---

