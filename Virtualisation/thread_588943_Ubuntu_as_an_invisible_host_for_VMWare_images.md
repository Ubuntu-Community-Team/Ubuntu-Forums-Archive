---
title: "Ubuntu as an invisible host for VMWare images"
date: 2007-10-23
forum: Virtualisation
---

### Post by geek.edu on 2007-10-23
I have a couple hundred computers split across 3 campuses that i have to manage. I often get very little notice about updating things like browser plugins and when i do get notice, the rooms are booked during my work hours. this gives me 3 choices:
1. Installing updates to all of them remotely which rarely works because I cant always get a installer file i can write into a script
2. Physically going to every machine and running the update

neither of which is ideal because both of which require me to find a time when the rooms are available (often during my "off" time)

3. remote imaging/running windows inside VMware

My question is can Ubuntu be customized so that i can:


[list=1]
[*] boot the machine from a custom liveCD
[*] Install Ubuntu to a minimal sized partition and create a blank partition with the remaining space for storage
[*] Remove the CD and reboot the system
[*] Ubuntu runs (preferably invisible or with a simple progress bar)
[*] Look at a FTP/Samba share on the network for an image file and download it to the large partition created in step 2
[*]run said image in VMware
[/list]

steps 4-6 would have to run without any user interaction and i would like to block user interaction with the linux OS as much as possible.

Id like to be able to ssh into the machines with a script and make them download newer virtual machines or have scheduled to do it themselves. (but only during off hours of course)

I have no problem doing most of this myself but i would like to know if  A) i am reinventing the wheel and somebody already did this or B)it cant be done for some reason (licensing is not an Issue we have a VLK for XP and both MAKs and a License server for XP Shiny Edition)

The live CD part would be just icing on the cake even if i had to install and configure ubuntu/vmware/ssh myself then image it to the other machines it'd still be better than my current solution


I prefer this solution because no other (free) solution will allow me to download an image in the background while the user is using the machine.

---

### Post by jusmurph on 2007-10-23
I know you could do everything there, but I have no expirence for the invisble host bit. The reason i post this is to say don't give up on it.

---

### Post by juliwoodbcn on 2008-05-09
Hi geek.edu,
I`m tryng to do the same, that you, how do you make it simple?.

I have prepared an a clean installation of ubuntu and vmware, with remastersys, and now i`ll do the testing, do you have some advice to me?
or more simple solution?

---

### Post by kcnnc on 2008-05-10
Not related to virtualization but might want to check out this solution:
[http://drbl.sourceforge.net/](http://drbl.sourceforge.net/)

---

