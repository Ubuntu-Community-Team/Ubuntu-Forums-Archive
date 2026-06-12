---
title: "Problems with DAHDI (Asterisk) Error inserting wcfxo module"
date: 2011-08-17
forum: Server Platforms
---

### Post by mkmoot on 2011-08-17
Hi! I have and asterisk with a x100p card as FXO on ubuntu  server. A few days ago, I begin to update the 10.04 to 11.04 system version. After that, asterisk runs ok, but now I have problems with  Dahdi. When I load the module with "modprobe wcfxo" I see the error:
```
FATAL:  Error inserting wcfxo  (/lib/modules/2.6.32-24-generic-pae/updates/dkms/wcfxo.ko): Unknown  symbol in module, or unknown parameter
```and if I see dmesg, I obtain:```
[ 1394.243357] wcfxo: disagrees about version of symbol dahdi_alarm_notify
[ 1394.243364] wcfxo: Unknown symbol dahdi_alarm_notify
[ 1394.243616] wcfxo: Unknown symbol dahdi_transmit
[ 1394.243775] wcfxo: disagrees about version of symbol dahdi_register
[ 1394.243778] wcfxo: Unknown symbol dahdi_register
[ 1394.243945] wcfxo: disagrees about version of symbol dahdi_hooksig
[ 1394.243948] wcfxo: Unknown symbol dahdi_hooksig
[ 1394.244127] wcfxo: Unknown symbol dahdi_receive
[ 1394.244260] wcfxo: disagrees about version of symbol dahdi_unregister
[ 1394.244264] wcfxo: Unknown symbol dahdi_unregister
[ 1394.244531] wcfxo: Unknown symbol dahdi_ec_chunk
```In the process of system boot I see some errors releated with Dahdi on dmesg
```

[   15.260218] wcopenpci: Unknown symbol dahdi_transmit
[   15.260350] wcopenpci: disagrees about version of symbol dahdi_register
[   15.260353] wcopenpci: Unknown symbol dahdi_register
[   15.260499] wcopenpci: disagrees about version of symbol dahdi_qevent_lock
[   15.260501] wcopenpci: Unknown symbol dahdi_qevent_lock
[   15.260599] wcopenpci: disagrees about version of symbol dahdi_hooksig
[   15.260601] wcopenpci: Unknown symbol dahdi_hooksig
[   15.260767] wcopenpci: Unknown symbol dahdi_receive
[   15.260863] wcopenpci: disagrees about version of symbol dahdi_unregister
[   15.260866] wcopenpci: Unknown symbol dahdi_unregister
[   15.261169] wcopenpci: Unknown symbol dahdi_ec_chunk
```and
```
[   17.769904] dahdi_dummy: Unknown symbol dahdi_transmit
[   17.770000] dahdi_dummy: disagrees about version of symbol dahdi_register
[   17.770003] dahdi_dummy: Unknown symbol dahdi_register
[   17.770106] dahdi_dummy: Unknown symbol dahdi_receive
[   17.770199] dahdi_dummy: disagrees about version of symbol dahdi_unregister
[   17.770202] dahdi_dummy: Unknown symbol dahdi_unregister
[   17.914242] dahdi_transcode: disagrees about version of symbol dahdi_transcode_fops
[   17.914247] dahdi_transcode: Unknown symbol dahdi_transcode_fops
```After  that mesh I tried to donwload the lastest version of the dahdi and  compile and install it, and the errors still here. I have no problem  during compilation, the whole process is successful.

The versions of the softwares I use are:
Kernel: Linux 2.6.32-24-generic-pae #43-Ubuntu (ubuntu 11.04)
Asterisk: Asterisk 1.6.2.19
Dahdi: dahdi-linux-complete-2.5.0 (but the errors already existed with the previous version that was installed 2.4.1)

The PBX runs ok, I can make SIP calls and other, the only flaw is the FXS card. Because the problem in Dahdi.

Any ideas? Any pointers? 

Many thanks in advance!

---

