---
title: "Ubuntu not working with ACPI"
date: 2012-08-10
forum: Server Platforms
---

### Post by 04blatca on 2012-08-10
I recently purchased a new server for my company and tried installing Ubuntu 12.04 server but have had numerous issues. Basically, the install process starts and the server almost instantly just restarts. The same thing happens with a windows installation which restarts when it starts to load files.

After disabling ACPI on boot, Ubuntu installed correctly. The problem with this however is that without ACPI, there is not hyper threading which I require for the applications I am running on the server. As soon as I enable the acpi=ht flag on grub, the server fails to boot and restarts.

I have tried 2 different motherboards and CPUs, as well as changing the RAM for known working sticks and replacing the PSU and video card. I have also ensured that the motherboards had the latest bios and used a different CD drive.

Server specs are:

3930K @3.2GHz (6 Core/12 Threads)
64GB DDR3 RAM @ 1333MHz
Tried 2 different motherboards (ASRock X79 Extreme6 and ASUS Sabertooth X79)
360GB SSD + 2TB HDD

Any help would be greatly appreciated.

Thanks!

---

### Post by corrosion on 2012-08-11
I have the same problem as you with my motherboard server GA-MA69VM-S2. It is updated to the last BIOS version, but no change, when booting the ubuntu server 1204 (amd64) installer with acpi support it hangs. Without ACPI it install without problems, but the CPU load goes 100% without any apparent reasons...
With Debian, anyway, it works perfect...

---

### Post by Vegan on 2012-08-11
while kernel support is usually excellent, there are lots of boards it cannot figure out

---

### Post by corrosion on 2012-08-12
Looking into the forums I found the solution for my motherboard: Disable HPET from BIOS Power Settings. Now I installed ubuntu server 1204 with ACPI without problems. Try yourself and good luck!

---

