---
title: "piix4_smbus host smbus controller not enabled"
date: 2009-03-18
forum: Server Platforms
---

### Post by scope006 on 2009-03-18
I have an installation of Ubuntu Server 8.04 on VMWare ESX 3.5 that is set to use 1vcpu and 1gig of memory.  I powered down or stopped the vm and changed this to 2vcpus and 2gigs of memory.

Now on boot I get "piix4_smbus host smbus controller not enabled" as an error.
1) everything seems to be working just fine.  Ubuntu sees both cpus.
2) no matter if i change back to 1vcpu or flip it yet again back to 2vcpus, the error remains there.
3) i have found nothing on the net where anyone has found a solution to this.

Can anyone provide some insight into correcting the error, convincing me not to worry about the error, or telling me that I goofed and I should rebuild the vm.

Thanks much community for any help that you can provide!

---

### Post by windependence on 2009-03-18
You are making a very common mistake. VMware does not recommend using more than one VCPU per server unless you have a specific reason to do so. It does not work the way you think it does. Even if your VM machine has one VCPU, it will STILL use CPU cycles from both CPU's since they are pooled in VMware. Doing what you are doing has the exact opposite effect on your VM than you would expect and causes all kinds of problems unless you need a core dedicated to a certain VM which is rare.

> Virtual machines in an SMP system should be configured to use multiple CPUs only if they are
running applications that are multi-threaded or implemented to use multiple processes. [B]Also, as
mentioned earlier, single-threaded workloads cannot make use of the second virtual processor
in a virtual machine. Depending on the guest operating system scheduling behavior, the
second virtual CPU may still consume resources and reduce the flexibility of the ESX Server
scheduler, without enhancing application performance.[/B]
This best practice recommendation differs from the common practice of configuring physical
enterprise servers with at least two CPUs. While in typical business environments such a practice
normally enables standardization and the possibility of system reuse, in virtual infrastructure,
where provisioning is virtually free, having the second CPU just in case, does not carry similar
benefits. In addition, virtual infrastructure changes the nature of the trade-off between scaling
up and scaling out your platforms. In many cases, ESX Server running a combination of SMP and
single-virtual CPU virtual machines can utilize the physical CPUs most efficiently. 

[www.vmware.com/pdf/vsmp_best_practices.pdf](www.vmware.com/pdf/vsmp_best_practices.pdf)


-Tim

VMware Partner

---

### Post by scope006 on 2009-03-18
> **windependence said:**
> You are making a very common mistake. VMware does not recommend using more than one VCPU per server unless you have a specific reason to do so. It does not work the way you think it does. Even if your VM machine has one VCPU, it will STILL use CPU cycles from both CPU's since they are pooled in VMware. Doing what you are doing has the exact opposite effect on your VM than you would expect and causes all kinds of problems unless you need a core dedicated to a certain VM which is rare.



[www.vmware.com/pdf/vsmp_best_practices.pdf](www.vmware.com/pdf/vsmp_best_practices.pdf)


-Tim

VMware Partner

Tim,

Are you essentially saying if you have an ESX box that has 8 physical cpus it really doesn't boost your individual vms performance by having it run with 2 vcpus vs 1 vcpu, since vmware is designed to provide as much power from the host box as possible?

aka, let vmware do it's thing unless you have some very specific reason your server or software needs more than 1 core/cpu on the vm?

Thanks for the quick response!

---

### Post by scope006 on 2009-03-18
Can anyone address this part of my question in regards to the specific "piix4_smbus host smbus controller not enabled" error my ubuntu virtual machine is throwing?:

> 
Can anyone provide some insight into correcting the error, convincing me not to worry about the error, or telling me that I goofed and I should rebuild the vm.


Thanks much!

---

### Post by scope006 on 2009-03-18
Tim What do you think of this article?

[http://communities.vmware.com/thread/165286](http://communities.vmware.com/thread/165286)

It is leading me to believe that setting up things like apache web servers and mysql database servers as virtual machines with 2cpus is a good default; and also that it is supported/safe to bump an existing vm from 1cpu to 2cpus even though there is a disclaimer near where you do it, warning the machine could become unstable.

Keep in mind 2 things:
1) the linux kernel installed by default even with only 1vcpu is SMP
2) my host box has 8 cpus

---

### Post by scope006 on 2009-03-18
Ok guys and gals!

It turns out that shutting down a linux vm that is using the smp kernel by default anyway and increasing or decreasing the number of vcpus is perfectly safe.  The error I got seems to not cause any issues whatsoever and happens even on a fresh install of 8.04.2.

Also it IS best practice to use 1vcpu and only increase if you specifically need it.  If you assign 4vcpus to a box barely doing anything; when it runs 1 process it ties up all 4 cpus during that cycle on the host box.

Hope that all made sense.

- scope006

ps
if anyone does find a way to get rid of that crazy error though that would be stellar, just cuz it annoys me.  =)

---

### Post by windependence on 2009-03-18
Exactly! That is the point I was trying to make. Unless you are rendering high end graphics or something that needs 2 CPUs simultaneously, it's best practice to give the VM 1 VCPU. It will still have all the power of the 8 cores IF it needs them.

-Tim

---

### Post by scope006 on 2009-03-19
Hopefully this thread will be useful for others with my same issue / question.  It is good to see the recommendations, the thought process, the verification, and reassurance of the/a best practice.

Cheers!

---

### Post by bprof on 2010-01-20
I had the same exact problem. Switching to one process fixed it.

Thanks to both of you for this informative post.

---

### Post by bsh on 2010-07-01
> **scope006 said:**
> Can anyone address this part of my question in regards to the specific "piix4_smbus host smbus controller not enabled" error my ubuntu virtual machine is throwing?:

Thanks much!

hello
i'm using virtualbox and not vmware, but i think this doesn't matter at all.
since the vm has no smbus, but ubuntu seems to always load the smbus module at boot, the fix is straightforward:

```
lsmod | grep i2c_piix4
```

and if you see the module is loaded, just blacklist it in */etc/modprobe.d/blacklist.conf*, by adding:

```
blacklist i2c_piix4
```

at the end of the file (or anywhere). (eventually update your initramfs too: *update-initramfs -u -k all*)
that's all.

---

