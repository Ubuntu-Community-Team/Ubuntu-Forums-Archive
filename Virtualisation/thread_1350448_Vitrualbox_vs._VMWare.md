---
title: "Vitrualbox vs. VMWare???"
date: 2009-12-09
forum: Virtualisation
---

### Post by RazorV on 2009-12-09
I have searched the forms but can't find a comparison.  I'm going to install Ubuntu 9.10 64 bit on my new 160gb SSD Drive today and would like to know what VM is better?

Does anyone have any links to suggestions they could share with me.

Thanks to all and i do apologize if this has been discussed already, but i have yet to find it.

Greg

---

### Post by RazorV on 2009-12-09
Okay - I should of Googled my search instead.  For those of you looking for this answer, If I can be of any help here, try these links:

VirturalBox:
[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

Marsbox Reveiw of Vbox vs VMWare:
[http://marsbox.com/blog/reviews/vmware-vs-virtualbox-part-2/]("http://www.virtualbox.org/wiki/VBox_vs_Others")



cheers,
greg

---

### Post by memilanuk on 2009-12-09
Why post the same review three times?

---

### Post by lewisforlife on 2009-12-09
I have heard that VMWare runs a little faster, but VirtualBox has a lot more options and flexibility, and a wider range of OS support.  Personally I use VirtualBox and have no issues, and not to mention it is free, which is the best part.

---

### Post by fjgaude on 2009-12-09
From my standpoint it is hard to beat VMware Player 3.0... it does everything except permit access down the LAN. Very nice as kernels update themselves.

---

### Post by sanemanmad on 2009-12-09
I Vote VBox. I am currently running it on a headless server and never have any issues. 
```

root@alice:/etc# lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

```

As you can see I am running 4 VMS. (using a custom script to show)

```

root@alice:/etc# su - virtadmin
$ vm.sh list

phoenix
storm
callisto
openldap

```

I recommend installing an older version since the newest has excluded the bridged networking functionality (or at least the commands changed and I am more comfortable using 
```
-nic1 --bridged --bridgedapter1 bond0
```

And as previously mentioned, it's free.


...oh and the best part is i can literally build, configure, remove any VM from command line. (Makes it easy to build scripts for building vms and performing minor changes.)

---

### Post by wojox on 2009-12-09
You forgot this thread: [http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

---

### Post by BT1 on 2009-12-10
> **wojox said:**
> You forgot this thread: [http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)
 
 
LOL! Good one. :P

---

### Post by Druke on 2009-12-10
honestly, if I'd be more help if I knew what you were wanting to do with the vms.

if it is just running windows, virtualBox really does everything you need it to.

the only comparision that matters really
virtualBox = free (even the non OSE version is)
VMware = not so free (IIRC).

if you're doing linux vms, like running a server, or testing different distros, I highly recommend kvm.

---

### Post by yiran3344 on 2009-12-10
Vbox,obviously.More flexiable,easier,and free

---

### Post by RazorV on 2009-12-11
> **memilanuk said:**
> Why post the same review three times?

Okay Okay Okay - you got me.  Sorry bout that.  I was in a hurry and I guess i wasn't paying attention.

But it's fixed now.  

Cheers and sorry for the same link 3 times.

---

