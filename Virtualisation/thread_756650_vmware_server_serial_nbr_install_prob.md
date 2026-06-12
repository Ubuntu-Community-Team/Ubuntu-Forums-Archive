---
title: "vmware server serial nbr install prob"
date: 2008-04-16
forum: Virtualisation
---

### Post by luckyme2 on 2008-04-16
I have this problem during vmware-install.pl :

[I] In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines]
The path "/var/lib/vmware/Virtual Machines" does not exist currently. This
program is going to create it, including needed parent directories. Is this
what you want? [yes]
sh: /usr/lib/vmware/bin/vmware-vmx: not found
Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:
[/I]  
I know reading here and everywhere on the net that the solution should be :

[I] root@UCLABVMSVR:/tempy/vmware-mui-distrib# sudo apt-get install ia32-libs
[/I] 
But when I do that I get this :

[I] root@UCLABVMSVR:/tempy/vmware-mui-distrib# sudo apt-get install ia32-libs
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
Pakket ia32-libs is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
Echter, de volgende pakketten vervangen dit:
  lib32z1
E: Pakket ia32-libs heeft geen installeerbare kandidaat
[/I] 
Sorry for the Dutch lingo but nicely translated it means that ia32-libs is unavailable as it has been replaced by lib32z1. The is no candidate for ia32-libs.

Now I am stuck cause I cannot force the install of ia32-libs.

Any idea ? 

ps: I use vmware server 1.0.5 with Ubuntu 7.10 Server amd64 (64bit)

---

### Post by fjgaude on 2008-04-16
I see the ia32-libs in the Hardy repos... strange you can't install them. I know they were also in Gutsy.

---

### Post by luckyme2 on 2008-04-16
> **fjgaude said:**
> I see the ia32-libs in the Hardy repos... strange you can't install them. I know they were also in Gutsy.

That's what I expected. :confused:
Anyway thanks for looking into this Frank.

I already installed the same config in a vmware session and there it is working smoothly. 
I will start doing a new install of the system and let's keep the fingers crossed. :)

---

### Post by fjgaude on 2008-04-16
I do wish you luck, but not much is actually required... when Hardy is released it will be the best OS yet.

---

