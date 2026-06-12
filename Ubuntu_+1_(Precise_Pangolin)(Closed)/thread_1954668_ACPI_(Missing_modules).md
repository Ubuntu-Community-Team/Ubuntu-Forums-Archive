---
title: "ACPI (Missing modules?)"
date: 2012-04-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by buttugly on 2012-04-08
HP DV7-6c20us Pavilion Laptop

Any idea where the thermal/fan and processor modules went, or how to get them short of recompiling?  

I tried to ask a smart question with relevant info, if I fell short please educate me.

Thanks!
buttugly

kevin@hpcrap:~$ sudo acpitool -e -v
[sudo] password for kevin: 
  Kernel version : 3.2.0-22-generi   -    ACPI version : 20110623
  -----------------------------------------------------------
  Battery #1     : present
    Remaining capacity : 96016 mWh, 100.0%
    Design capacity    : 98235 mWh
    Last full capacity : 96015 mWh, 97.74% of design capacity
    Capacity loss      : 2.260%
    Present rate       : 0 mW
    Charging state     : charged
    Battery type       : rechargeable 
    Model number       : 960 mWh
    Serial number      : 8850

  AC adapter     : on-line 
  Could not open directory : /proc/acpi/fan/
  function Do_Fan_Info() : make sure your kernel has ACPI fan support enabled.

  CPU type               : AMD A8-3520M APU with Radeon(tm) HD Graphics 
  Min/Max frequency      : 800/1600 MHz
  Current frequency      : 800 MHz
  Frequency governor     : ondemand 
  Freq. scaling driver   : powernow-k8 
  Cache size             : 800.000 KB
  Bogomips               : 3194.32 
  Bogomips               : 3194.10 
  Bogomips               : 3194.12 
  Bogomips               : 3194.10 
  Function Show_CPU_Info : could not read directory /proc/acpi/processor/
  Make sure your kernel has ACPI processor support enabled.

  Could not open directory : /proc/acpi/thermal_zone/
  function Do_Thermal_Info() : make sure your kernel has /proc/acpi/thermal_zone support enabled.

   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PB2      S5    *disabled  
  2. PB3      S4    *disabled  
  3. PB4      S5    *disabled  pci:0000:00:04.0
  4. XPDV      S5    *enabled   pci:0000:01:00.0
  5. PB5      S5    *disabled  pci:0000:00:05.0
  6. PB6      S5    *disabled  pci:0000:00:06.0
  7. PB7      S5    *disabled  
  8. SPB0      S4    *disabled  
  9. SPB1      S4    *disabled  
  10. SPB2      S4    *disabled  
  11. SPB3      S4    *disabled  
  12. GEC      S4    *disabled  
  13. OHC1      S3    *enabled   pci:0000:00:12.0
  14. OHC2      S3    *enabled   pci:0000:00:13.0
  15. OHC3      S3    *disabled  
  16. OHC4      S3    *disabled  
  17. EHC1      S3    *enabled   pci:0000:00:12.2
  18. EHC2      S3    *enabled   pci:0000:00:13.2
  19. EHC3      S3    *disabled  
  20. XHC0      S3    *enabled   pci:0000:00:10.0
  21. XHC1      S3    *enabled   pci:0000:00:10.1
  22. P2P      S5    *disabled  pci:0000:00:14.4

kevin@hpcrap:~$ ls -l /lib/modules/$(uname -r)/kernel/drivers/acpi
total 160
-rw-r--r-- 1 root root 11416 Apr  3 14:13 acpi_ipmi.ko
-rw-r--r-- 1 root root 12952 Apr  3 14:13 acpi_memhotplug.ko
-rw-r--r-- 1 root root 20752 Apr  3 14:13 acpi_pad.ko
drwxr-xr-x 2 root root  4096 Apr  4 23:15 apei
-rw-r--r-- 1 root root  7808 Apr  3 14:13 ec_sys.ko
-rw-r--r-- 1 root root 13776 Apr  3 14:13 pci_slot.ko
-rw-r--r-- 1 root root 13184 Apr  3 14:13 sbshc.ko
-rw-r--r-- 1 root root 28304 Apr  3 14:13 sbs.ko
-rw-r--r-- 1 root root 34280 Apr  3 14:13 video.ko

---

### Post by dino99 on 2012-04-08
i'm using psensor, but conky is much more complete.

---

