---
title: "Mixed LInux and Windows servers"
date: 2010-10-30
forum: Server Platforms
---

### Post by Vegan on 2010-10-30
Now that I have more computers I am looking at new solutions to manage the proliferation.

My Linux machine has been replaced and its now much more powerful than before but its still a 32-bit processor. No problem as I am not using anything unorthodox outside the LAMP stack with a few PHP add-ons to support graphics.

I use SAMBA so I can edit web sites easily with Windows tools.

So now given a Windows Server, who should be king server and have everybody on the same page so to speak.

---

### Post by CharlesA on 2010-10-30
How do you mean "king server"?

We'd need to know more about yer network setup.

---

### Post by arrrghhh on 2010-10-30
LOL @ King Server.  I love it.

So yes lots of questions... Do you want a central place for all your files?  What are your servers doing?  At our office we have several servers that do the same thing basically for load-balancing (always matching OS tho... we wouldn't try to load balance a Windows server with a Linux server, unless you had an actual load balancer that it hits first... basically determines where packets should go before they make it to the servers), but at my house I have one file server so that's where everything goes for me file/media-wise.

---

### Post by arnavk007 on 2010-10-30
king server would mean the central server doing everything
like dhcp dns file print and whatever's required
maybe it would act like a gateway

---

### Post by CharlesA on 2010-10-30
If you want just one server and the linux box is only serving web pages, you could always virtualize the Windows or Linux machine and do it that way.

I use a VM for web development myself.

---

### Post by Vegan on 2010-11-01
My current Linux appliance is a 5 year old Acer Aspire with a Celeron 335 CPU so its not exactly suitable for virtualization at the moment.

Once I find a CPU for my M2NBP-VM board I will have a 64-bit machine to use and then I am considering running Linux and Windows Server on some hypervisor or other.

Linux is my web server, but I wanted to use Win Server for other purposes.

---

### Post by CharlesA on 2010-11-01
You could probably just virtualize the Linux box on the Windows box if that was the case.

Otherwise just leave it as is, since it's not hurting anything. :P

---

### Post by Vegan on 2010-11-01
Right now I am going to use Ubuntu on bare metal. 

I was considering a hypervisor of one flavor or another but I wanted to make sure that each server could work with the other for various services.

I am more acclimated to using separate machines for each server, but in this day and age that is not so popular.

---

