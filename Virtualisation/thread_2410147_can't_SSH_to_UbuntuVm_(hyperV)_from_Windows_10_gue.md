---
title: "can't SSH to UbuntuVm (hyperV) from Windows 10 guestOS"
date: 2019-01-11
forum: Virtualisation
---

### Post by b002 on 2019-01-11
A linux noob lab here:

guest OS win10pro / hyperV (192.168.5.100)
> vm01 (ubuntuSrv 18.10) (x.5.13)
> vm02 (ubuntu 18.04) (x.5.16)
> raspi3 (Paspbian) (x.5.20)
> wSrv2016 (x.5.99)
> NAS synology (x.5.101)


My analyze:
- both vm's have 1X lanAdapter connected to vSwitch (External) in hyperV
- both vm's have ip provided by my local router dhcp server, and both ping router successfully
- both vm's have an active internet connection and ping each other successfully
- both vm's ping NAS successfully, both answer ping FROM NAS cli successfully
- both vm's ping wSrv2016 successfully, both answer ping FROM wSrv cli successfully
- i can ssh vm01 to vm02 and from 02 to 01
- both vm's respond to ping from wSrv2016, and wSrv2016 respond to both vm's
- wSrv2016 ssh to vm01/vm02 > successfully

- both vm's DON'T respond to ping from win10, and win10 DON'T respond to ping from vm's
- win10 ssh to vm1/vm2 > Network error: Connection timed out
- win10pro ssh to raspi3 > successfully



I didn't touch the ufw rules for ubuntu vm's, both were installed out of the box as they come. I need to do this in hyperV not vmWare/vBox. 
Regarding the win10 feels like something is slipping between my "hyperv switch config" fingers and the mighty google doesn't help much.
Step by step configuration help will be much appreciated. 

Cheers! :KS

---

