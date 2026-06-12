---
title: "VMWare Svr 2.0 rebuild network"
date: 2009-08-19
forum: Virtualisation
---

### Post by nishy09 on 2009-08-19
Hey,

First post so not 100% sure this is the right area so i am posting in the general area :P

Setup: I am running Ubuntu 9.04 desktop on a Acer TravelMate 4234.[INDENT]Intel Core 2 Duo T5600, Nvidia GeForce Go 7300
1.5gb DDR2 Ram, 120gb HDD and then all the normal features

[/INDENT]Issue: After reboots my VM of XP Pro loses network connectivity. It comes up displaying limited connectivity. I found a solution but its not something i want to have to do every time i reboot my laptop which is to remove the 3 modules the configuration creates then run the "vmware-config.pl" script again so it can recreate the modules.

Has anyone seen this sort of issue before? Would anyone possibly know why the modules keep breaking?

Thanks in advance :)

---

### Post by NoBugs! on 2009-08-19
I've noticed a similar problem in the free vmware player. Have you tried it in Virtualbox? It's in the repository and it seems to have better Linux support.

---

### Post by nishy09 on 2009-08-19
Hey,

Thanks for the reply :)

No i haven't tried anything other then VMWare server.
I will give virtualbox a shot and see if it makes much difference or even if its just better then VMware =D

---

### Post by russellr on 2009-08-19
Hi,

I have seen a problem that might be related.

Basically, upon booting I cannot start any VMware guests without VMWare saying the network bridge (I use a bridge not NAT) cannot be connected.

I've determined the cause and attached a fix.

The cause is that NetworkManager on the host hasn't brought up the network interfaces before the vmware services are started (/etc/init.d/vmware).

My solution is to run a script in the /etc/network/if-up.d directory that restarts the vmware services whenever a network interface comes up.

Once a VMware guest is running, the script cannot restart the vmware services if you cycle a network interface, but that doesn't matter, as far as I can see.

The attached script should be installed in /etc/network/if-up.d and look like this:
```
-rwxr-xr-x 1 root root 379 2009-08-19 15:06 /etc/network/if-up.d/vmware
```

I hope that helps.

regards,
RR

---

### Post by nishy09 on 2009-08-19
Hey Russellr

Not completely sure thats the same sort of issue that im experiencing as mine would load the Guest it would just have limited connectivity.

I am going to try Virtualbox today to see how it performs and whether its a better replacement for VMWare Server in my situation.

THanks

---

### Post by nishy09 on 2009-08-20
Already like it better then VMWare server.
Just building up an XP guest now and ill see how it goes but thank you for the idea.

---

