---
title: "freenas v ubuntu"
date: 2016-08-20
forum: Server Platforms
---

### Post by Vegan on 2016-08-20
I have used FreeNAS in the past, but I was wondering if Ubuntu can be run from a USB stick easily and do the same work? Maybe better motherboard support etc? More RAID cards and Wi-FI cards etc.

---

### Post by kenz71 on 2016-08-21
I don't see a install to USB Option. But installing to USB limits options / features.

Been using NAS4Free & prior to that FreeNAS for several years. While I have been quite happy with the performance I seem to have outgrown it. I am looking to implement OpenNMS, VPN, Domain Controller and the occasional torrent for classic movies I can't find anywhere else.

Anxious to see how Ubuntu stacks up - although it is not a fair comparison as NAS4Free is more of a NAS being asked to perform server functions while Ubuntu Server is well, a server OS.

---

### Post by mastablasta on 2016-08-24
> **Vegan said:**
> I have used FreeNAS in the past, but I was wondering if Ubuntu can be run from a USB stick easily and do the same work? 

it can. i run it like that in the HP Microserver box. Using Ajenti as web based user interafce.

however if you want an interafce then i suggest Openmediavault instead (OMV for short, debian based). however OMV is creating graphs (system performance monitor), so it is using disks a lot. i mean constantly. however if that doesn't bother you and i think FreeNAS does the same, then just move the VAR/logs to hard disk and log away...

A few other options in linux world that are GUI based servers are Zentyal (Ubuntu based, SBS replacement not so much NAS), Nethserver (centos based), ClearOS (centosbased)... there are a few more out there but their GUIs are not that good.

---

### Post by Vegan on 2016-08-24
looks like i need to look into this more

thanks for the idea guys

---

