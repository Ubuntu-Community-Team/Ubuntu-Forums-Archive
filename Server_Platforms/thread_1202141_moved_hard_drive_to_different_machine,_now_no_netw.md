---
title: "moved hard drive to different machine, now no network"
date: 2009-07-01
forum: Server Platforms
---

### Post by gareth40 on 2009-07-01
Heres the situation, have installed Ubuntu server and configured it as a LAMP webserver with static lan ip address, I took hard drive out to move everything across to a different machine, I plugged the same hard drive into the new machine. It boots up fine and everything loads correctly except for the network, the network seems to be down. Could anyone provide a solution for me, im new to linux. Im assuming its a driver problem. the motherboard model# of the new machine is MS-7030, K8N Neo. its using the onboard lan which is powered by the nVidia chipset. The procesor is a amd 64 athlon 3200+ with 512mb ddr-400. the hard drive I pulled out of the other machine is a seagate 200gb sata. im assuming there is a command I have to type to tell it to download and install the nvidia network drivers?

---

### Post by Bachstelze on 2009-07-02
This is not a driver problem. Most likely, the name of your network intervace changed (for example from eth0 to eth1) and you need to either update your network configuration accordingly, or reset your udev rules to reset the interfaces numbering.

---

### Post by jwatte on 2009-07-02
It could be a few things.
First, it may be as HymnToLife says: your network device got re-numbered.
Second, it may be that your scripts are configured to look for a specific kind of network card (whatever was in the old machine).
Third, it may be that the network chip is turned off in the BIOS.
Fourth, it may be that you really don't have an nForce network driver installed, but that seems unlikely.

You can look at what modules are loaded with "lsmod," which will tell you what drivers the kernel tries to use, if you have a dynamically linked kernel. Otherwise, you have to look through dmesg after boot to see what it's trying to load.

---

### Post by trundlenut on 2009-07-02
I had to change the motherboard in my laptop which had a built in NIC and I kept the original wireless card so the ID of the wireless didn't change but the ethernet did exactly as HymnToLife says.

---

### Post by gareth40 on 2009-07-03
thanks for the help, but i still woudlnt have a clue how to get this up and running again. i cant even use sudo apt-get to install any packages, just get error unable to resolve dns when it tries to download so im assuming the network really is dead, and it is enabled in bios. I typed the command "lsmod" but it scrolls up the page and i dont see half the information it gives. sorry but as i said before im new to linux and ubuntu and have limited knowlegde. is there some kind of command i can use so instead of the info scrolling off the top of the screen it pauses and i hit a key to see the next lot? the same as using this command in msdos "dir /p" which will show the dir listing but pause untill i hit a key to continue. Iknow how to install and configure a lamp server in ubuntu and setup ftp access and change permissions etc, so if i cant get the network thing sorted i might just bite the bullet and do a clean install from the cd and setup the lamp server again, will just take a bit of time thats all, will have to backup all my sql databases and htdocs etc...  shold i be downloading the linux drivers from the manufactures site for my motherboard?

---

### Post by trundlenut on 2009-07-03
try this command: sudo lshw -C network

it should show you what you network interface is and what it has been assigned to, eth0, eth1 etc.  Look for "logical name".  Assuming it has been detected and is enabled of course.

---

### Post by gareth40 on 2009-07-03
ok did that and came a one line message flashed then went, then after said PCI and something else, however i thought id install a pci lan card with the Realtek chipset and give that a try, booted up and it recognised it, typed that command again "sudo lshw -C network" and its showing as disabled "*-network DISABLED" is the exact message then a whole lot of other stuff under neath with the chipset name etc...  how do i enable it? thanks for the help

---

### Post by gareth40 on 2009-07-03
please disregard last post, i managed to get the pci lan card up and running by editing the network interfaces file "sudo nano /etc/network/interfaces " and duplicating eth0 and then changing to eth4 which is the pci lan card, then did restart on networking and it works "sudo /etc/init.d/networking restart"
 
But still would like to know how to get the onboard nForce networking adaptor up and running, but if i cant will just leave pci lan card in.

---

### Post by trundlenut on 2009-07-03
can you post the output of that command, does it recognise that the onboard networking adaptor is there?  If not have you checked in the bios that it is enabled?

---

