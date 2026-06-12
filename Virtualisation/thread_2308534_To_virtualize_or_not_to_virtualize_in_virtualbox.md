---
title: "To virtualize or not to virtualize in virtualbox"
date: 2016-01-04
forum: Virtualisation
---

### Post by saitoh183 on 2016-01-04
Im thinking of virtualizing my current ubuntu 14.04 setup but im not sure if its a good idea and if it would make performance significantly poorer. The reason i want to P2V is that i would be able to snapshot the machine for quick restoring if something goes wrong or if i have hardware failures like loose a drive. Let me start by what the machine is for:

This is my disk setup and Hardware

[IMG]http://snag.gy/QlX6j.jpg[/IMG][IMG]http://snag.gy/5pn6W.jpg[/IMG]

I have 2 disk that are ntfs because i have windows 7 machine that uses sdb1 as a mounted physical disk and sdc2 as a shared location. My System disk is a SSD

Applications running at all times:

- Sonarr
- Sabnzbd
- Xampp (MySQL, Apache(Owncloud,plexpy,plexRequest,PhpVirtualbox))
- Sickrage
- Teamviewer
- Deluge Deamon
- Teamspeak Server
- Couchpotato
- Virtualbox
- Emby server (No really used..more for testing)
- xRDP

My virtual Windows machine needs at least 4GB of ram all the rest of the ram could go to ubuntu. both machines would run side by side

My questions:

Is it a good idea?
if it is a good idea, will the performance impact be noticeable?
What host OS to use? (just another ubuntu desktop?)
What to use to do the P2V?
How would my disk setup translate to the VM? (things are on different partitions)
Would it be better to mount physical disk for everything except system disk? Or create vdi's all around?
Any other things i should consider?

If this was your setup what would u do? Also is virtualbox with phpvirtualbox the best choice? 

Im still learning the linux world and im loving it! I have only started using ubuntu for 2 weeks now and my linux knowledge is very limited and coming from a windows world, conversion is slow but steady :)

Thanks in advance :)

---

### Post by ajgreeny on 2016-01-04
You have very adequate hardware for running VBox so in that respect there should be no major problems.

I am not certain of the advantages of using Windows 7 as a VM, but I do still have WinXP running extremely effectively and fast on my quad-core, 8GB ram machine with Xubuntu 14.04 64bit as host, which I need to run very occasionally to update a GPS stanav device.

You want to use Ubuntu as a VM, not Windows, and I also use VBox as a way of trying the development versions of the *ubuntu family, all of which seem to run very well with no real speed penalty that I notice; I have read that the unity desktop of Ubuntu does not run well in VBox but I have had no problems with any of the OSs.

I agree there is an advantage to using a VM as you can have a good snapshot up and running in minutes if something major should go wrong in the VM.  However, one possible problem of using an OS in VBox as a VM rather than a hard-metal installation might be the reduced 3D graphics ability of the VM but only you will know when you try it whether that is a problem for you; as I said the unity desktop, which does need good 3D works fine on my VBox installation so it is perhaps a case of try it out before making a final decision.

---

### Post by saitoh183 on 2016-01-04
> **ajgreeny said:**
> You have very adequate hardware for running VBox so in that respect there should be no major problems.

I am not certain of the advantages of using Windows 7 as a VM, but I do still have WinXP running extremely effectively and fast on my quad-core, 8GB ram machine with Xubuntu 14.04 64bit as host, which I need to run very occasionally to update a GPS stanav device.

You want to use Ubuntu as a VM, not Windows, and I also use VBox as a way of trying the development versions of the *ubuntu family, all of which seem to run very well with no real speed penalty that I notice; I have read that the unity desktop of Ubuntu does not run well in VBox but I have had no problems with any of the OSs.

I agree there is an advantage to using a VM as you can have a good snapshot up and running in minutes if something major should go wrong in the VM.  However, one possible problem of using an OS in VBox as a VM rather than a hard-metal installation might be the reduced 3D graphics ability of the VM but only you will know when you try it whether that is a problem for you; as I said the unity desktop, which does need good 3D works fine on my VBox installation so it is perhaps a case of try it out before making a final decision.

Thanks for the response. I have a windows 7 vm because I have windows only app that I need. This is not my main machine. It's a sort of server. 3d is not necessary. All I don't want is a performance hit. 

What about my other questions? Like how to proceed and what to use to convert

---

### Post by ajgreeny on 2016-01-04
Sorry but I have no idea how to do a conversion from VM to hard-metal install, or vice-versa.

Have you looked in the VBox forums at [https://forums.virtualbox.org/](https://forums.virtualbox.org/)?

---

### Post by ian-weisser on 2016-01-04
There is no way to 'convert' a Win7 bare-metal application to an Ubuntu VM application. You migrate.
Install an Ubuntu VM Guest, install each service one-by-one, mirror your data across, and switch over.

Since performance is important to you, check performance after migrating each service.
You have two decisions to make:
1) Do you want a GUI for admin (Lubuntu or Xubuntu), or will you go the more common shell-only route (Ubuntu Server)? This is easily changed if you change your mind.
2) Should you install 14.04 (supported until 2019) or 15.10-upgradeable-to-16.04 (supported until 2021)? This is hard to change. Changing releases off the tested upgrade path may require a complete reinstall.

---

### Post by saitoh183 on 2016-01-04
> **ian-weisser said:**
> There is no way to 'convert' a Win7 bare-metal application to an Ubuntu VM application. You migrate.
Install an Ubuntu VM Guest, install each service one-by-one, mirror your data across, and switch over.

Since performance is important to you, check performance after migrating each service.
You have two decisions to make:
1) Do you want a GUI for admin (Lubuntu or Xubuntu), or will you go the more common shell-only route (Ubuntu Server)? This is easily changed if you change your mind.
2) Should you install 14.04 (supported until 2019) or 15.10-upgradeable-to-16.04 (supported until 2021)? This is hard to change. Changing releases off the tested upgrade path may require a complete reinstall.


Right now i have a bare-metal Ubuntu tha runs a win7 vm. Switching the bare metal to vm would just mean win7 vm would run side by side with the Ubuntu VM. i will stick with 14.04 since by the time 2019 rolls around, i will probably re-evaluate needs. Yes i would want a GUI since im not comfortable enough with linux yet to only work via shell-only.

---

