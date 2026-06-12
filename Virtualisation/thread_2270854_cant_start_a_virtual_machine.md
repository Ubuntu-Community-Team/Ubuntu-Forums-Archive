---
title: "cant start a virtual machine"
date: 2015-03-26
forum: Virtualisation
---

### Post by shadow8 on 2015-03-26
ok so first and foremost specs
dedicated server box
64gigs ram
8 cores
tarabites of storage

running 14.4 trusty tar xfce with x2go packages(according to box provider it was the only one with a gui and x2go support)
why this version for a server well i need windows like familiarity for server staff day to day operations and linix's epic performance 

first i installed kvm(atleast i think its that) when starting up RR3(the name of the first virtual box) it got to about half way threw the initial install and just stops(doesn't stop running it just freezes no resources in use and still running in the middle of an install)
after poking kvm with a sharp stick learned that it would not work for what we need (need a cd in always it only loads it on first boot)

ok time to go to something i know better oracal vm this would be my first time running oracal on ubuntu so i did some digging
i beleve i installed it right as pur this site [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

clicked trusty's link opens application manager(atleast thats what i call it) installed then ran
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc)
sudo apt-key add oracle-vbox.asc
sudo apt-get update
sudo apt-get install virtualbox-4.3
sudo apt-get install dkms

some of this reterned with all up to date rather then install complete

opened oracle vm manager
set up rr3 once again(including set startup disk in drive)

and this is what i get
message 1
Failed to open a session for the virtual machine RR3.
The virtual machine 'RR3' has terminated unexpectedly during startup with exit code 1 (0x1).
details

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}


message 2(poped just after message one befor i actualy had a chance to read message 1)
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
atempted to execute 
'/etc/init.d/vboxdrv setup'

console says it does not exsist

i been poking at it trying to check and double check everything i even reran every sudo cmd i did they all said nothing to update this time

tryed again same error


i dont normaly use ubuntu nothing really aganst it just does not feel right for most of my computers a few years back i used it with a totally custom ui build(thats the only thing i find wrong with it is the ui)
so now i am at the end of my rope any one have any ideas what i could have done wrong or how to fix it

---

### Post by KillerKelvUK on 2015-03-26
Don't think KVM and OVB play well on the same server, you need to ensure KVM is completely removed and reboot the server so the KVM kernel modules aren't loaded.

BTW, KVM can have a CD attached to a guest as boot or otherwise device, no need to switch out to OVB for that reason.

---

### Post by shadow8 on 2015-03-26
i have never actually removed just one "program" from linix i usually format it away so how would i do that

and i need the cd after boot the cd changes day to day depending on the operation of the day and the data encryption keys also changes with the cd(with out it the server wont understand the client

---

### Post by TheFu on 2015-03-26
> **shadow8 said:**
> i have never actually removed just one "program" from linix i usually format it away so how would i do that

and i need the cd after boot the cd changes day to day depending on the operation of the day and the data encryption keys also changes with the cd(with out it the server wont understand the client

Teaching you to fish ...  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)  There is a chapter about package management. Basic stuff. 

There is a desktop guide too, but package management is usually just running synaptic.

If you really want to learn Linux, start by learning the basics, getting your mind right, then the CLI - [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
Google is NOT your friend at this stage. A little directed background now will save you hours, days, weeks, months of frustration.

---

### Post by shadow8 on 2015-03-26
Thefu THANK YOU i have been looking for that "fishing rod" for years

Update
kvm compleatly removed oricle validated(to my knowlage) rr3 gave same error still

reformated the box (just in case)
loaded oracle as pur first post and created "ginipig"

Failed to open a session for the virtual machine Ginipig.
The virtual machine 'Ginipig' has terminated unexpectedly during startup with exit code 1 (0x1).

i am still slamming into the same brick wall

again thank you fu you have already saved me hours of time for setting up the ftp on our server now i just got to get our sandbox working

---

### Post by TheFu on 2015-03-26
Please don't use plain FTP - .... ever. Use sftp.  Plain FTP should have died in 1992.

---

### Post by shadow8 on 2015-03-27
> **TheFu said:**
> Please don't use plain FTP ROFLMAO i can hack plain ftp in 60 seconds or its free (our server caters to hackers(whitehats) so i am going to have extra security on the host box)

the ftp we are using needs 2 passwords or a password and a gpg key(depending on the os conecting never found a way for winblows to use a gpg key)


bashes head on wall

i now have everything ready (should have taken me all day) except the sandbox(virtual machines we call them the sand box cause we torcher the hell out of the os on the vms but cant even get one to start still)

---

### Post by TheFu on 2015-03-27
WinSCP supports ssh-keys.
Use SSH/SFTP/SCP.  Don't use ftps, which is a relative joke since the client can decide whether to encrypt or not.

---

