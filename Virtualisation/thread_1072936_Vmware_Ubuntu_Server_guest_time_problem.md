---
title: "Vmware Ubuntu Server guest time problem"
date: 2009-02-17
forum: Virtualisation
---

### Post by tinny on 2009-02-17
Hello

I have installed vmware server 2 on a Windows XP machine. I have a Ubuntu Server 8.04 guest VM running on this machine and I am having some problems with the guest time. The Ubuntu server time is all over the place, it doesnt want to sync with the host time.

Any tips? 

(Ive tried ntp and also enabling “Synchronize guest time with host” and I have vmware tools installed)

Thanks

---

### Post by rouben on 2009-02-18
> **tinny said:**
> Hello

I have installed vmware server 2 on a Windows XP machine. I have a Ubuntu Server 8.04 guest VM running on this machine and I am having some problems with the guest time. The Ubuntu server time is all over the place, it doesnt want to sync with the host time.

Any tips? 

(Ive tried ntp and also enabling “Synchronize guest time with host” and I have vmware tools installed)

Thanks
Generally it's not a good idea to enable both, as they will fight each other. According to VMware, you should use their method of syncing time, but from my experience NTP works quite well... as long as you don't turn both on at the same time. If decide to you use NTP, disable the drift file.

[LIST=1]
[*]**sudoedit /etc/ntp.conf** or **gksudo gedit /etc/ntp.conf** if you run the GUI in your guest.
[*]Comment out the line starting with the word *driftfile*.
[/LIST]

Good luck!

---

### Post by tinny on 2009-02-18
> **rouben said:**
> Generally it's not a good idea to enable both, as they will fight each other. According to VMware, you should use their method of syncing time, but from my experience NTP works quite well... as long as you don't turn both on at the same time. If decide to you use NTP, disable the drift file.

[LIST=1]
[*]**sudoedit /etc/ntp.conf** or **gksudo gedit /etc/ntp.conf** if you run the GUI in your guest.
[*]Comment out the line starting with the word *driftfile*.
[/LIST]

Good luck!

Im using ntp with the drift file commented out and I have turned off the vmware time synchronization. The VM has been running all day and it seems to be keeping good time now.

Thanks, 

ill keep monitoring it.

---

### Post by rouben on 2009-02-18
If you really want to stress-test the time sync, try running something CPU intensive on the VM and then let it idle for a while, then repeat. The dynamic reallocation of CPU resources (really the ratio between idle and busy CPU cycles) is what plays tricks with the guest's clock. If you have NTP running, you shouldn't notice too much of a lag, however, if you don't have any kind of time sync, you should notice a considerable time discrepancy after a while.

---

