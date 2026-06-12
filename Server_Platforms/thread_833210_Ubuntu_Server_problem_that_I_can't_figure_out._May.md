---
title: "Ubuntu Server problem that I can't figure out. May need someone to consult."
date: 2008-06-18
forum: Server Platforms
---

### Post by theonegod on 2008-06-18
I have a Ubuntu Server running in a VM. It used to be in a GG but it developed an issue and I moved everything to a HH VM. This new VM has recently begun to develop the same issue. 

Intermittantly throughout the day, mostly from 5pm - 7am. Every 2-4 hours this servers web sites go down. This is a basic LAMP installation with a PHP backend business application. What will happen is that the server is running well and I get a page telling me the sites are inaccessible. I SSH into the server (SSH continues to work luckily) and use top or htop and see that none of the PIDs are using any CPU at all. I try to manually stop apache2 but whn I go to start it again it says it is still running. I try to manually stop mysql and it hangs trying to do so.  I try to execute a reboot and the server hangs as well trying to stop mysql. 

I have to go to the host OS and power cycle the VM. It comes back up with no trouble and everything works. Until the next time that is. 

Now, I don't know an awefull lot about Ubuntu Server environment. I am learning as I go and I just can't for the life of me figure out what is causing this. Any ideas? Or are there any Ubutnu Server experts out there that would be willing to offer their services to SSH in and see if they can tell me what exactly is hanging apache when this is occurring?

Oh, and this server ran perfectly for 2 weeks before this occurred after I moved everything from the old VM. On the old VM it ran for over a month before it began to happen.

---

### Post by firecat53 on 2008-06-18
What platform and which vm product are you using? I had terrible results running a vm ubuntu server using both vmware and virtualbox on a vista host. I finally gave up and fired up my trusty old PII in the garage :) I don't have any experience running a vm server on a linux host, but XP runs great in a vm on ubuntu host.

Good luck!
Scott

---

### Post by theonegod on 2008-06-18
This VM is running on a Windows Server 2003 Host inside VMware Server. The CPU and memory use is never a problem on the ubuntu machine though I am not sure if there aren't issues resulting from the compressed drive image. 

The hardware is an IBM blade with 3.5gigs of ram and a xeon 2 core cpu. Both cores are available o the VM and 2 gigs of memory are allocated to the VM.

My next step is to install this on a standalone server and not in a vm. I would rather not do this in a blade as I am not familiar with setting up vlans in linux and that is what you have to assign in a blade.

---

### Post by windependence on 2008-06-18
Just me, but I would never run a VM on a Windoze host.


-Tim

---

### Post by theonegod on 2008-06-18
I agree. This is not ideal. I am working right now to install Ubuntu Server on one of the blades nativly. 

I have a question in regard to this. I would like to rsync the entire vm to this new ubuntu installation. Does anyone have any thoughts on this or can anyone tell me the most efficiant manner in which this can be done?

---

### Post by theonegod on 2008-06-18
I installed HH natively on one of the blades today and migrated everything to it. I also made some changes to the default settings in the apache2.conf that I hope will optimize it alittle. 

No one is interested and qualified to go into my companies rolodex as a linux consultant in case I need more help? Come on people easy money!

---

### Post by loell on 2008-06-18
> **theonegod said:**
> 
No one is interested and qualified to go into my companies rolodex as a linux consultant in case I need more help? Come on people easy money!

you can post a brief job ad in [the community market]("http://ubuntuforums.org/forumdisplay.php?f=38")

---

