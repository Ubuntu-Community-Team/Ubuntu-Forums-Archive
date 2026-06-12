---
title: "Wich Virtualization is Most compatible with 7.10?"
date: 2007-12-27
forum: Virtualisation
---

### Post by denz97 on 2007-12-27
hi all!

i'd like to be able to run different OS on top of Ubuntu and i'm not interested in multi-boot OS just virtualization so just like what the title says, which virtualization software (vmware, xen, virtualbox) works best with 'gutsy gibbon' (7.10)?

thanks!

---

### Post by popch on 2007-12-27
I used VMWare Workstation 5.x for a while, tested Virtualbox and now use Virtualbox only.

I do not need very advanced or complicated features, just basic Windows XP or even 2k. 

I don't use VMWare any more because I had to renew some parts of it whenever the Linux kernel was updated. Also, the configuration of the VMWare stuff took a few more steps than the installation of VirtualBox. Those differences were not insurmountable but Virtualbox just proved to be more convenient.

I now prefer Virtualbox also because the complete product is freely available, while VMWare offers only VMWare Server and VMWare Player for free.

There were some issues about using bridged networks over the wireless NIC, but I believe those issues are resolved by now.

---

### Post by rickycodie on 2007-12-27
virtualbox is the best, comes in a deb file, easy configuration and the support is ok.

---

### Post by lvleph on 2007-12-27
My biggest problem with VirtualBox is that there is no 3d virtualization. But I am not sure if any of the others have 3d virtualization.

---

### Post by rickycodie on 2007-12-27
you can try to get it enabled in vmware, but it is unstable and can crash your virtual system.

---

### Post by denz97 on 2007-12-27
thanks for the replies!  I'll give virtualbox a try tonight.

so i take it you guys are also using 71.0/gutsy gibbon and that there wasnt any installation issues at all?

sorry, currently time is a critical resource and not ready to spend much troubleshooting.

---

### Post by seanc7 on 2007-12-27
I've been running VirtualBox for a couple of weeks now, no problems with it.

---

### Post by popch on 2007-12-27
> **denz97 said:**
> thanks for the replies!  I'll give virtualbox a try tonight.

so i take it you guys are also using 71.0/gutsy gibbon and that there wasnt any installation issues at all?

sorry, currently time is a critical resource and not ready to spend much troubleshooting.

Installation went without a hitch by just doing ***add application*** in the application menu.

I've had to add my userid to a group. VMBox produced an error message on first start that the user was not member of that group. Took all of some five minutes to find.

Nonetheless, if you never have used any virtualization software, be prepared to spend some time learning to use it and do some fiddling until everything runs that's needed.

---

### Post by rickycodie on 2007-12-27
virtualbox is virtually painless, just remember to install guest additions.

---

### Post by dpj23 on 2007-12-27
I'm running VM workstation 6...  No problems in 7.10... I haven't tried other products simply because VMware has been running great since I installed it...

---

### Post by theZoid on 2007-12-27
I installed VMware Server through the Synaptic Pkg Manager and it works like a dream (running XP Pro VM).  I haven't used VirtualBox.

---

### Post by lvleph on 2007-12-27
But is anyone playing games that need 3d?

---

