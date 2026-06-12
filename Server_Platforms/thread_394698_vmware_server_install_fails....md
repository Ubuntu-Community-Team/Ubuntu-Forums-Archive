---
title: "vmware server install fails..."
date: 2007-03-27
forum: Server Platforms
---

### Post by Mia_tech on 2007-03-27
I'm trying to install vmware server and it fails, got error:

jorge@5601-RM00-00:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

jorge@5601-RM00-00:/tmp/vmware-server-distrib$ 

I had vmware player previous, but I remove it before installing server, any help appreciated

thanks

---

### Post by ifeldt on 2007-03-27
This probably won't help at all but...

If you have vmware-player via APT, you should run:

```
sudo apt-get remove vmware-player
```

You can then use ```
sudo apt-get autoremove -s
``` if you have some extra packages that aren't needed anymore.

When I tried to use the online vmware-server installer after having vmware-player installed via APT, I remember running in to some of these problems.

You can then reinstall it.

If that isn't the problem, let me know and we can go on from there.

Ian Feldt

---

### Post by Mia_tech on 2007-03-27
I installed mine with Automatix and that's how I removed it, either way, I use the command you posted above and it still keeps giving me the same error

---

### Post by ifeldt on 2007-03-27
Alright, have you tried running ```
sudo /usr/bin/vmware-uninstall.pl
```?

I can't install vmware-server via Automatix because I am using feisty, but that should completely remove vmware.

Ian Feldt

---

### Post by Mia_tech on 2007-03-27
> **ifeldt said:**
> Alright, have you tried running ```
sudo /usr/bin/vmware-uninstall.pl
```?

I can't install vmware-server via Automatix because I am using feisty, but that should completely remove vmware.

Ian Feldt

I had installed vmware player, which I remove through Automatix, and just in case also did "sudo apt-get autoclean" for any remaining pkgs, after I manually remove vmware player, and reseted my session also restarted the pc, still same result...........

---

### Post by jackrobinson on 2007-03-27
> **Mia_tech said:**
> I'm trying to install vmware server and it fails, got error:

jorge@5601-RM00-00:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

jorge@5601-RM00-00:/tmp/vmware-server-distrib$ 

I had vmware player previous, but I remove it before installing server, any help appreciated

thanks

It wont work because some cruft is left over from vmware-player (config files etc)
do this:
```
sudo apt-get install vmware-player
sudo apt-get --purge remove vmware-player
```
and then try to install vmware-server

---

### Post by Mia_tech on 2007-03-27
> **jackrobinson said:**
> It wont work because some cruft is left over from vmware-player (config files etc)
do this:
```
sudo apt-get install vmware-player
sudo apt-get --purge remove vmware-player
```
and then try to install vmware-server
that was exactly the problem....
thanks

---

### Post by Mia_tech on 2007-04-06
my installation of vmware server on a new machine fails at compile time, I checked in synaptic and the C compiler shows as installed, but I'm getting this errors

make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-12-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

Thanks

---

### Post by Mia_tech on 2007-04-07
has anybody been able to get vmware server running on new version of ubuntu 7.04...........I've been trying for a while, with no luck

---

### Post by nrwilk on 2007-04-09
> **jackrobinson said:**
> It wont work because some cruft is left over from vmware-player (config files etc)
do this:
```
sudo apt-get install vmware-player
sudo apt-get --purge remove vmware-player
```
and then try to install vmware-server

I have the same problem as the OP, but this did not help me.

Any other suggestions? :)

---

### Post by primski on 2007-04-10
For installing vmware-server on feisty check [this](http://ubuntuforums.org/showthread.php?t=338305) thread.

---

### Post by Gashi on 2007-04-17
okay this is my first post and I am new to Linux compleatly but i have a suggestion for all of those that are having trouble with this...
with you installed with Automatix2 then there is a locations file that is left in the /etc/vmware/ folder and must be deleted so if this is true for your case then execute the following lines in the terminal

```
sudo apt-get install vmware-player
sudo apt-get --purge remove vmware-player
sudo rm /etc/vmware/locations
sudo rmdir /etc/vmware
```

this should get you set and on your way to installing VMware Server
thanks to nrwilk for the lead into this thought

Cheers!!

---

