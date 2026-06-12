---
title: "VMware Workstation crashes [i just upgraded to Hardy Heron]"
date: 2008-04-24
forum: Virtualisation
---

### Post by ChromeKaldra on 2008-04-24
Well i upgraded, but now my VMware Workstation doesn't work. I click the icon, it cycles [booting up] then crashes and i'm left with nothing, not even an error window. Did the upgrade remove some files or something? 

Kinda critical as all my work is done in the VM [Wine doesn't run my Windows progs very well]

---

### Post by Az_135r on 2008-04-25
try 

[http://www.nowhere.dk/archives/2008/03/21/running_vmware_workstation_6_0_3_on_ubuntu_hardy_herron/index.php](http://www.nowhere.dk/archives/2008/03/21/running_vmware_workstation_6_0_3_on_ubuntu_hardy_herron/index.php)

---

### Post by Az_135r on 2008-04-25
in fact, i just downloaded the 6.0.3 version and it works off the bat (script version)

alien rpm version doesnt work

---

### Post by ChromeKaldra on 2008-04-25
> **Az_135r said:**
> try 

[http://www.nowhere.dk/archives/2008/03/21/running_vmware_workstation_6_0_3_on_ubuntu_hardy_herron/index.php](http://www.nowhere.dk/archives/2008/03/21/running_vmware_workstation_6_0_3_on_ubuntu_hardy_herron/index.php)

No go. I think i'm missing something called C scripter or something? I kept asking me the same questions over and over again when it tried to build the missing modules...everytime i said yes after the first time it said all the work had already been done, but i was still missing the module.

---

### Post by Az_135r on 2008-04-25
try a clean install vmware... your right, that patch didnt work for me either (i was in the middle of testing when i posted that)

$sudo vmware-uninstall.pl (iirc)

then assuming you have v.6, go to vmware if you havent already, and download 6.0.3 tar package (not rpm!)

run the script, and all should be well, worked for me anyways on a clean install of hardy

---

### Post by andresz on 2008-04-25
[http://communities.vmware.com/thread/141611?tstart=0](http://communities.vmware.com/thread/141611?tstart=0)

Here is the solution I found : 

    * unpack VMware-workstation-6.0.3
    * go to vmware-distrib/lib/modules/source
    * untar the file vmmon.tar (tar xvf vmmon.tar)
    * cd vmmon-only/include
    * edit the file vcpuset.h
    * go to line 75
    * change #include “asm/bitops.h” to #include “linux/bitops.h” (Because there are some changes made to the 2.6.24 kernel, it’s not possible to include bitops.h from asm and you will have to include it from the linux directory)
    * go back to vmware-distrib/lib/modules/source
    * remove the old vmmon.tar file (rm vmmon.tar)
    * repack de new vmmon.tar file (tar cvf vmmon.tar vmmon-only)
    * remove vmmon-only directory (rm -rf vmmon-only)

---

### Post by Az_135r on 2008-04-25
well, im an idiot

for some reason i thought this was in the 64bit forum!

just tried to do a 32bit installation, and lo and behold, it wouldnt compile

andresz - nice first post! worked perfectly!

---

### Post by markiehill on 2008-04-25
just wanted to thank andresz for his post, this worked perfectly on upgrading from 7.10 to hardy heron.

Mark

---

