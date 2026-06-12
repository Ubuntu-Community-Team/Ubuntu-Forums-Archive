---
title: "Best virtual machine?"
date: 2008-07-23
forum: Virtualisation
---

### Post by worx101 on 2008-07-23
Hello,

I am looking to try out different distributions and Windows OSes, but I don't want to reformat/dual-boot/tri-boot whatever as I am perfectly happy with Ubuntu as it is.

So my question is, what is the best virtual machine?  Curious about vmware, but not sure what I should need or if that is even what I should be looking at.

tried qemu, but that was a major headache and I would prefer not to try it again.

Thanks

---

### Post by iaculallad on 2008-07-23
Take a look at the "Complete" comparison of Virtual Machines at [Wiki]("http://en.wikipedia.org/wiki/Comparison_of_virtual_machines").

---

### Post by sdennie on 2008-07-23
Moved to Virtualization.

---

### Post by dross_kuh on 2008-07-23
I use virtualbox(1.6), never tried any of the others for the simple reason that it was the first i tried and it did everything i wanted/needed and was fairly simple to install/setup :)

---

### Post by Jon Monreal on 2008-07-23
> **dross_kuh said:**
> I use virtualbox(1.6), never tried any of the others for the simple reason that it was the first i tried and it did everything i wanted/needed and was fairly simple to install/setup :)

Plus an open source version is available in Synaptic. It lacks USB support and a couple other things, but otherwise, it works great.

---

### Post by tamoneya on 2008-07-23
if you just want to play around with stuff and test things out I recommend virtual box.  VMWare is better for companies and servers and things like that.

---

### Post by Virtua-Touch on 2008-07-23
By far, VBox (VirtualBox) is the best. I tried VMWare and couldn't get it to work.

---

### Post by tesna on 2008-07-24
I've tried both (vmware workstation 6.0.4 & virtualbox 1.6.2), each has its own advantages and disadvantages. 

Speed wise almost the same (I haven't test it with any benchmarks, but from general experiences when working with large excel 2007 files)

Vbox pros:
-Good performance
-Free
-correctly registers mouse and keyboard movement when working inside the vm so the screen does not dim
-correctly compiles vbox modules on custom build 2.6.26 kernel

vbox cons:
-high cpu usage (50% according to top) when the running guest at idle, making my laptop computer quite hot, because high cpu demand and forcing my cpu to use full clock when set to ondemand gorvernor.
-usb not enabled by default, and needs some tweaking to get it work
-quite hard to setup bridged networking

vmware pros:
-easy install, networking (nat & bridged easy to setup), usb enabled by default
-low cpu usage when guest is idle (7-8% according to top) so it will not force cpu clock to full power and resulting much cooler operation.
-good performance

vmware cons:
-didn't correctly registers my mouse and keyboard movement in host OS, so when working in guest VM, my screen dims after a while, I need to scroll my mouse outside the VM guest window to make it undim. This is so annoying
-vmware modules doesn't compile on 2.6.26 kernel, there's a patch though but I havent tried it.

Just a quick questions to vbox users, how much cpu usage of virtual box when running one vm at idle? does mine normal?

My specs:
Ubuntu Hardy 64 bit with all latest updates
Thinkpad T61, C2D 7300 2ghz, 4 GB ram, 250GB sata hdd

---

### Post by dross_kuh on 2008-07-26
vbox is using 38% of one core on an AMD X2 6000 : 
i would`nt call it @idle tho... i have numerous programs running in it 
...  
cctv monitoring 4 live feeds, 
googletalk, 
ventrillo, 
nokia pc suite, 
clamwin antivirus,
dds (stacker unit),
tiny personal firewall :)

i`m using the non-oss version with the usb (guest additions installed)

---

### Post by siepo on 2008-07-26
The high cpu usage of vbox can be cured with a boot parameter nohz=off added on kernel lines in /boot/grub/menu.lst.
Don't ask me what it means.

---

### Post by Jon Monreal on 2008-07-27
> **siepo said:**
> The high cpu usage of vbox can be cured with a boot parameter nohz=off added on kernel lines in /boot/grub/menu.lst.
Don't ask me what it means.

If you're interested in finding out more about that nohz option, it has to do with dynamic ticks. I managed to find a pretty good article [here]("http://www.phoronix.com/scan.php?page=article&item=651&num=1"), just in case you are curious.

---

### Post by Yuki_Nagato on 2008-07-27
Check out Derek's guide to Virtual Box.  He will set you up!

(Check the signature)

---

### Post by boblemur on 2008-07-27
not exactly on topic but you should check out xplite(their is an open source one) that less than 1/2ed the size of my xp install and it runs ALOT faster.... so if you are looking to vm xp (without using a native partition of windows) then i sugest you trim ur xp down before installing :)

---

