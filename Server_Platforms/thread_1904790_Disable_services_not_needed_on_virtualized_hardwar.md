---
title: "Disable services not needed on virtualized hardware?"
date: 2012-01-05
forum: Server Platforms
---

### Post by vfclists on 2012-01-05
Is there a way of knowing and disabling services that are not needed on virtualized hardware, such as KVM and Xen HVM?

/vfclistsGUY

---

### Post by jerrrys on 2012-01-06
You can kill processes with your "System Monitor" to see the effect it will have on your system.  This is temporary and will restore to default after reboot.

[ATTACH]210356[/ATTACH]

---

### Post by Vegan on 2012-01-06
Linux is pretty lean already compared to Windows Server. Much more so. I estimate I can use 4x more Linux installs for every Server 08R2 install for RAM use alone.

My Ubuntu VM has more RAM allocated to it so that it can run better with the load imposed.

---

### Post by vfclists on 2012-01-08
I'm more interested in a guide which tells what those programs are and whether they are meaningful on virtual servers like OpenVZ, VServer etc

/vfclistsGUY

---

### Post by rsvancara on 2012-01-08
You can turn off everything if you want.  Or leave a few things on.  There are no hard and fast rules.  Unlike windows where you "NEED" services on, Linux does not care. If you need networking, turn it on, but you are not required to turn it on.  Sure, if you want Apache to work, yes, you will need it, but otherwise no.  This is why Linux runs on everything from the largest super computers to the smallest hand held devices, you can choose what you need to run.  

Your problem is more of a philosophical problem, not a technical one.  

Thanks

---

### Post by HermanAB on 2012-01-08
No, the OPs problem is that he has to do a whole lot of Googling to find out what the services are used for and then he has to actually think about whether they are needed.  So he wants someone else to do his homework for him.

---

### Post by elico on 2012-01-08
to see the processes that are running on the system you can use htop and you will see that almost nothing is running so in almost in any case i have seen you dont need to turn off anything off.

---

### Post by vfclists on 2012-01-10
Don't jump to hasty conclusions. What I am asking is if there is a way of telling whether a service is meaningful or not, not based on the documentation (which may have nothing to say about virtualization), but its relevance to a virtualized system if it uses or expects hardware in a way that is not relevant.

> **HermanAB said:**
> No, the OPs problem is that he has to do a whole lot of Googling to find out what the services are used for and then he has to actually think about whether they are needed.  So he wants someone else to do his homework for him.

---

