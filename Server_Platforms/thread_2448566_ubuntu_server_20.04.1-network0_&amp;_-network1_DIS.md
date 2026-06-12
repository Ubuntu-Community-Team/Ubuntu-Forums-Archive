---
title: "ubuntu server 20.04.1*-network:0 &amp; *-network:1 DISABLED"
date: 2020-08-10
forum: Server Platforms
---

### Post by math492m on 2020-08-10
hi im running ubuntu server 20.04.1 and i have a networking problem 

i cant get connection to the internet with ethernet cable 

so i cant install if config 

i can see the network cards is disabled

usually i just enable with ifconfig up command 

but i dont have ifconfig installed 

and cant install it either becouse of no net

help!

---

### Post by dino99 on 2020-08-10
some useful hints  [https://linuxconfig.org/how-to-restart-network-on-ubuntu-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-restart-network-on-ubuntu-20-04-lts-focal-fossa)

[https://computingforgeeks.com/how-to-install-ifconfig-on-ubuntu-focal-fossa/](https://computingforgeeks.com/how-to-install-ifconfig-on-ubuntu-focal-fossa/)

---

### Post by slickymaster on 2020-08-10
Thread moved to **Server Platforms** for a better fit

---

### Post by math492m on 2020-08-10
hi im kinda new to ubuntu server 

and i am using it without GUI 

and i didnt get much out of the links you send me

---

### Post by math492m on 2020-08-11
my server running 20.40 dosnt have internet 
and the netplan fails to deploy

---

### Post by coffeecat on 2020-08-11
Threads merged. Please do not post duplicates.

If you don't get a response to your thread after about 12-24 hours, you are very welcome to bump it. Simply post the word "bump".

---

### Post by darkod on 2020-08-11
Usually you would set up the networking details during OS installation. Did you do that? If you did, that means the OS can detect the network card, which is the first step.

You can also check which network cards the OS can see with:
```
sudo lshw -C network
```

Please post the content of the netplan yaml file here, inside CODE tags. That will make it easier for reading.

Another important thing, did you have internet during installation? I think it downloads a lot of packages during the installation so if you didn't have internet then you might be missing a lot. That might explain why you can't use ifconfig. I never needed to install it manually, it was always there as part of the OS. But I always install the OS with internet connection active.

---

### Post by LHammonds on 2020-08-12
I don't think ifconfig is part of the base install of 20.04.

To see your IP address settings, you can type this command:
```
ip address
```
or this for short:
```
ip a
```

Networking in 20.04 uses Netplan and its configuration file can be located in /etc/netplan/*.yaml

When you make a change to your network config file, make sure you run this command and check to see if it says "configuration is valid"
```
sudo netplan --debug generate
```

Once you have a valid configuration, only then do you apply it:
```
sudo netplan --debug apply
```

If you have never setup an Ubuntu server before, you can find some useful information in [setup guide](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273) which I tend to refer to it for various things on a regular bases (such as adding a hard drive, expanding volumes, etc.)

LHammonds
LHammonds

---

