---
title: "Laptop on battery power will not read from M.2 SSD"
date: 2019-01-29
forum: Ubuntu, Linux and OS Chat
---

### Post by simon-baguley on 2019-01-29
Guys
I have installed many flavours of Linux over the years on many chassis - but this response from a laptop retailer has me scratching my head. 

I purchased a laptop recently with a 256 M.2 SSD and proceeded to install Linux. Everything was working great until I removed the power cable to run the laptop off battery. Well the OS stopped reading anything from the SSD...if that part of the OS was already loaded into RAM no problem, but if I loaded another piece of software (and the OS would have have to go to the SSD to get it) the OS started to throw error messages about "cannot access xxxxx".

So I throw the laptop back to the retailer and tell them exactly what the issue is and how to re-create it. Here is their response ...

"Thank you for getting in touch. I have spoken with the technician and he  is currently still testing the system. So far he has tested the laptop  woth a new M.2 SSD with Windows installed and it booted and everything  was working fine, so then he installed the Linux software onto the new  M.2 and the problem re-occured. After which he tried the old and new  M.2's with Linux on in a completely different laptop chassis and the  problems occured. He is currently still testing however at this time **_we  believe the issue is caused by the Linux software_** as this is generally  not supported by these chassis' eventhough we do have customer that have  sucess installing it."

Yep, they blame the fault on Linux. 

Anyone want to comment on this, please feel free to vent.

Simon.

---

### Post by Dennis N on 2019-01-29
Does the laptop support both SATA and NVMe type m.2 drives? Did you test both types?

---

### Post by simon-baguley on 2019-02-04
Yes @Dennis, it does

---

### Post by Geoffrey_Arndt on 2019-02-04
Perhaps this thread will help - - via modifying standard boot parameter (see section on nvme load).

[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

