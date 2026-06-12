---
title: "Which one is the fastest  virtualization software?"
date: 2008-06-11
forum: Virtualisation
---

### Post by hopelessone on 2008-06-11
Hi I have the CPU CoreDuo E4600 with 4gb Ram, Graphics Card 512mb Asus.. I installed KVM from the Community Docs and it's still choppy and slow for XP...

Unfortunately my CPU doesn't have Visualization built in to it Doh!!

I was thinking of trying VirtualBox..Any others where i can speed up XP?

1. Which Virtual Software would you use if you had my Processor...
2. Do i have to uninstall KVM to use other Virtual Software?
3. Thanks..!!

---

### Post by vishzilla on 2008-06-11
Virtualbox is good. You should try it

---

### Post by lizzard on 2008-06-11
> **vishzilla said:**
> Virtualbox is good. You should try it
+1
VirtualBox works quite flawless and fast for me. I tried Vmware once but it didn't convince me.

---

### Post by ChameleonDave on 2008-06-11
I too have had good results with VirtualBox.

---

### Post by hopelessone on 2008-06-11
Where's the HowTo: on Uninstall KVM? I followed [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) 

But theres no Uninstall?

---

### Post by hopelessone on 2008-06-11
Without hardware support, KVM falls back to the considerably slower QEMU-based software virtualization. In this case, it makes more sense  to use the qemu package, possibly with the kqemu package for better performance.

 qemu package - might look into this one...?

---

### Post by dpj23 on 2008-06-11
I would suggest using vmware products... hands down the best virtualization software available...  

However, everyone has there on preference and always should be respected...

I believe that no matter what product you use you should configure your vm guests to only run with 1 processor... ( even if your host has multiple processors)  This has been noted to increase performance in the vmware world and should apply across the board to others since all operate essentually the same way... 

So this might be the answer to your question... you might not even have to switch you just have too to make a configuration change to improve your performance...

---

### Post by digerati on 2008-06-12
I've used VMware Server and it did the job quite well.  My only real problem with it is that it's slow starting up.  Otherwise it's OK. I tried the VMware server 2 beta to see if it offered any improvements.  Better interface (web based) for management but quite unstable. Reverted to 1.5 eventually.

I'm now running VirtualBox 1.6 and the performance is quite impressive. So far my main problem is that I cannot install 64-bit OSes even though I have a 64bit processor (AMD64) and kernel.

---

### Post by hopelessone on 2008-06-12
I switched to VirtualBox and Boy what a difference !! lightning speed if you don't have the built in Visualization into your CPU Recommend PEUL Version..

---

### Post by techstop on 2008-06-13
Yet another vote for virtualbox. I tried it a while back (6 months ago?) and thought it was a dog. It ran *extremely* slowly when I enabled the VT-x hardware extensions on my CPU.

I recently installed the latest version (1.6) and I am very, very impressed. It is blazingly fast, and mouse integration and guest display resizing work perfectly. I thoroughly recommend it, it's a top quality product.

---

### Post by nsilva on 2008-06-16
One ignorant questions, if switch from Vmware to VirtualBox, Do I need to reinstall Windows?? I really dont want to wait those 2 hours again!!!

---

### Post by vishzilla on 2008-06-16
Yes, unfortunately you've to reinstall Windows.

---

### Post by hopelessone on 2008-06-16
What !

No you don't just convert it... google and he shall find..

[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

[http://forums.virtualbox.org/viewtopic.php?t=104](http://forums.virtualbox.org/viewtopic.php?t=104)

---

### Post by gtdaqua on 2008-06-16
How is VirtualBox faring in Server-based environments? I see the discussion is purely relating to virtualization in desktops. Guess VMWare server edition is more popular in server farms or enterprise-production-networks.

---

