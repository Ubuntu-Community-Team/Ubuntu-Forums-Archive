---
title: "HP proliant DL380 G7"
date: 2017-11-22
forum: Server Platforms
---

### Post by coyotekojo on 2017-11-22
Hello everyone, i am new to this forum and a basic user for Ubuntu, i have installed Ubuntu server 16.04 on a HP Proliant DL380 G7 and it runs REALLY SLOW, i have been reading about the raid controller not being compatible with 16.04, is there a workaround? i tried to disable the smart array and enable AHCI but can't find a way to do it, any help will be appreciated, regards

---

### Post by DuckHook on 2017-11-22
Welcome to the forums, coyotekojo.

I've moved your post to the Server Platforms subforum where all the server/RAID gurus reside.

---

### Post by mastablasta on 2017-11-23
if controller is the issue, just use mdadm (software raid) instead.

though i find it strange that it would not work well on Ubuntu LTS (probably it is certified), another option would be to use CentOS/Red Hat, which is very likely certified for.

---

### Post by darkod on 2017-11-23
According to quick google search it seems you can't disable the built-in raid on DL380 G7. Which I consider to be very bad case for linux use.

In most linux servers you would want to use mdadm SW raid which works best if the disks are simply presented to the OS directly, without any built-in raid. But branded servers usually do not offer such option, especially low/middle level servers.

You could double check searching on google if you might be able to flash the raid controller to IT mode (that is a mode that treats disks as simple AHCI, losing any raid capability). But again, such option probably doesn't exist for that HP controller. Although with the exact chip model, you can check if it's possible.

Apart from the above, the problem might be wrong setup somewhere, so it works slowly.

You also have the option not using HP raid to create "real" arrays but instead configuring each disk in separate raid0 array, and then build mdadm using these logical devices. But I do not consider it as real solution as you are still using the HP raid in a way, you will have multiple raid0 devices configured in it.

I would investigate which chipset the controller has and see if it can be flashed, if you're lucky. For example I was able to flash once a Supermicro MB built-in chipset to IT mode. But that was sort of easy because the chip was the same as of a well known flashable controller, IBM M1015.

---

### Post by coyotekojo on 2017-11-23
> **darkod said:**
> According to quick google search it seems you can't disable the built-in raid on DL380 G7. Which I consider to be very bad case for linux use.

In most linux servers you would want to use mdadm SW raid which works best if the disks are simply presented to the OS directly, without any built-in raid. But branded servers usually do not offer such option, especially low/middle level servers.

You could double check searching on google if you might be able to flash the raid controller to IT mode (that is a mode that treats disks as simple AHCI, losing any raid capability). But again, such option probably doesn't exist for that HP controller. Although with the exact chip model, you can check if it's possible.

Apart from the above, the problem might be wrong setup somewhere, so it works slowly.

You also have the option not using HP raid to create "real" arrays but instead configuring each disk in separate raid0 array, and then build mdadm using these logical devices. But I do not consider it as real solution as you are still using the HP raid in a way, you will have multiple raid0 devices configured in it.

I would investigate which chipset the controller has and see if it can be flashed, if you're lucky. For example I was able to flash once a Supermicro MB built-in chipset to IT mode. But that was sort of easy because the chip was the same as of a well known flashable controller, IBM M1015.


thanks for your reply, I think for now I will follow your idea of configuring multiple RAID 0 and then use mdadm, if it doesn't improve I think I will need a third party raid controller, will let you know the results of the new configuration, regards

---

