---
title: "Is it possible to install Xen PVH in Ubuntu 14.04 LTS?"
date: 2015-08-05
forum: Virtualisation
---

### Post by sethanath2 on 2015-08-05
Hi,

Is it possible to install Xen PVH in Ubuntu 14.04 LTS?
I would like to install Windows 10 as a guest operation system by using Xen PVH.
According to the post here -> [http://www.brendangregg.com/blog/2014-0 ... r-xen.html]("http://www.brendangregg.com/blog/2014-05-07/what-color-is-your-xen.html"), it says "In the future (Xen 4.4+), the fastest mode will be PVH". 

If it is impossible, would it be right to just use Xen PV?
Do you think that PVH option is too new at this time for Ubuntu 14.04 LTS?

I  am thinking that the two choices above would be best for me since I  have so many computers. Some has AMD -V, and some does not.
I want to  treat all my machine the same. I want to install Xen the same way on  all my machines.With PVH, Xen should take advantage of AMD -V  automatically, if it can right?

I also found another post on the internet mentions that Xen PVH only works with intel vt for now. Is this true?
[http://stackoverflow.com/questions/2823 ... ualization]("http://stackoverflow.com/questions/28231819/does-xen-pvh-mode-requires-intel-vt-x-or-amd-v-hw-virtualization")
All of my machines are from AMD, so please let me know your opinion.

One more question, if I use Xen tools, would that considered to be PV? 

Thank you.

---

### Post by TheFu on 2015-08-06
If you want to run a Windows GUI desktop in a GUI VM and want all the systems to be the same, you need to use virtualbox, not Xen.  At least that was how it worked with Xen previously. HVM was required for Windows and HVM requires VT-x support (or the equiv from AMD).

Plus vbox has the best GUI support for desktops.

---

### Post by sethanath2 on 2015-08-06
I want to try Xen, though. I do not mind not having any graphical interface.
Virtualbox is way too slow for me as I tried it before.

Now, when I mentioned treating all my machine the same, I meant I want to just pick one of the Xen options.
I don't want to have too many setting :)
I thought PVH might be good, but I heard it only works with intel vt for now. Is this true?

If my information is correct, I think I will have to try Xen PV.

I also tried KVM on one of my machines that have AMD-V, but it would not work with CPU that does not have virtualisation.
 I use "Virtual Machine Manager" for that KVM, and it is quite friendly enough.

I hope someone can give me some suggestion to start with Xen PV.

---

