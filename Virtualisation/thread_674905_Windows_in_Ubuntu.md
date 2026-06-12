---
title: "Windows in Ubuntu?"
date: 2008-01-22
forum: Virtualisation
---

### Post by teejay17 on 2008-01-22
Is there a way to run or install Windows Vista in Ubuntu 7.10? 
I'm not talking about dual booting, I'm talking about virtualization to the max.

---

### Post by yota on 2008-01-22
Sure,

to name two solutions: VmWare and VirtualBox.

Have a look to this howto: [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

It's for XP, but the same ideas apply to vista too. (and on a second thought maybe xp is better anyway :-p expecially for virtualization)

---

### Post by Rhubarb on 2008-01-22
Yes, you'll need some virtualisation software like virtualbox or vmware.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Once you've got this installed, you can pop in your vista cd, and get it installed inside virtual box.

It also looks like you'll be legally able to run vista home legally on a virtual machine aswell:
[http://developers.slashdot.org/developers/08/01/22/0334240.shtml](http://developers.slashdot.org/developers/08/01/22/0334240.shtml)

---

### Post by teejay17 on 2008-01-22
Thanks. I'll go over the links that have been provided. 
One quick question: which is better suited for this project? VMWare, or VirtualBox?

---

### Post by yota on 2008-01-22
It's a matter of personal taste, best if you try both and pick your choice:

<IMHO>
vmware is the leader of the virtualization software segment, offers strong, stable corporate-quality solutions, but it's totally closed source, the free (as in beer) version lacks a lot of features and there's no native package for ubuntu (just .rpm or a generic .tar.gz for any linux).

Virtual box it the newcomer, so maybe is a bit unpolished but can be used freely for non commercial usage, it's partially open-sourced and easier to install.
</IMHO>

Hope this helps!

---

### Post by gvartser on 2008-01-22
Virtual box is free, vmware workstation is not.

So I would go for virtual box, and from my experiences it works really good.

But if you need USB support, youll have to install the non-free version. 

Check out [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

for more details..

And for 7.10 you also have do apply this workaround to get USB working inside the guest OS:
[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Best regz,
/g

---

### Post by Magzee on 2008-01-22
Hey there.  I too want to load windows as a virtual OS, no way am I letting THEM near my hard drives again (one too many BSOD!!!)  I have been using Ubuntu 7.10 on my desktop and had windows xp home on my laptop...until it crashed.  So I need to load windows on Ubuntu desktop.  I am trialling VMware Workstation and just about had it all going when this message cropped up  "Your kernel was built with "gcc" version "4.1.2", while you are trying to use "/usr/bin/gcc" version "4.1.3". This configuration is not recommended and VMware Workstation may crash if you'll continue"  Can you point me in the right direction please guys??  Oh yeah - "Newbee"

---

### Post by totalnub on 2008-01-22
hmm, don't know exactly what to say with that vmware issue. I have a couple screenshots from my laptop if anyone is interested.

I've found that I like virtualbox more than vmware server. no particular reason, just look and feel i guess.

[http://tfl.homelinux.com/images/Screenshot2.jpg](http://tfl.homelinux.com/images/Screenshot2.jpg)
(vmware server on edgy)

and 

[http://tfl.homelinux.com/images/xp.png](http://tfl.homelinux.com/images/xp.png)
(virtualbox on gutsy)

---

### Post by Jonne on 2008-01-22
use virtualbox. It works fine and at least you don't need the installer to compile anything. It'll also be upgraded along with the rest when you upgrade to Hardy, while Vmware Server tends to lag a few months with their packages.

---

### Post by Magzee on 2008-01-22
Cool  - thanks guys, I'll try virtual box :)

---

### Post by pyman on 2008-01-22
I have to use Checkpoint VPN to remote into my work machine and servers. Virtualbox works GREAT for me using 7.10 on a DELL GX620. I use the Non-Free Virtualbox version and with no tinkering I have the USB and CD working too!  :guitar:

---

### Post by pyman on 2008-01-22
I said non-free instead of FREE as in software sorry...
:(:
confused:

---

### Post by teejay17 on 2008-01-23
I have a copy of Vista Home Premium only. Does anyone know if this works well in Virtualbox? Or VMWare, for that matter (although I do think that I'm going to go with Virtualbox).

---

### Post by FrankVdb on 2008-01-23
If I recall well, Vista Home Premium does not work in a virtual machine.

You have to thank Microsoft for that. It's the freedom of paying for something (or getting it shoved down your throat, depending on your perspective) and still not being allowed to do with it what you want. Like buying a Ford and Ford telling you what you can do and not do with your car.

---

### Post by yota on 2008-01-23
> **FrankVdb said:**
> If I recall well, Vista Home Premium does not work in a virtual machine.

You have to thank Microsoft for that. It's the freedom of paying for something (or getting it shoved down your throat, depending on your perspective) and still not being allowed to do with it what you want. Like buying a Ford and Ford telling you what you can do and not do with your car.

The point was not that Vista Home did not work in a virtual machine: it was just the license preventing you to use it on a virtual machine (these are the kind of problems that arise when you use software that you don't own...)
But now they changed their mind: [http://www.techspot.com/news/28681-microsoft-to-allow-virtualization-in-vista-home.html](http://www.techspot.com/news/28681-microsoft-to-allow-virtualization-in-vista-home.html)

---

### Post by teejay17 on 2008-01-23
> **yota said:**
> The point was not that Vista Home did not work in a virtual machine: it was just the license preventing you to use it on a virtual machine (these are the kind of problems that arise when you use software that you don't own...)
But now they changed their mind: [http://www.techspot.com/news/28681-microsoft-to-allow-virtualization-in-vista-home.html](http://www.techspot.com/news/28681-microsoft-to-allow-virtualization-in-vista-home.html)
Fine. But what does that mean for me? Can I actually install it in Virtualbox now?

---

### Post by p_quarles on 2008-01-23
Well, from everything I've read, it's now legal to install Vista Home editions on a VM -- but that's just what the tech news sites say. I would check Microsoft's site to see what the exact conditions and terms are.

I'm sure you know this already, but virtualizing Vista is going to take a mighty powerful machine.

---

### Post by Victormd on 2008-01-23
Just a note when installing Vista, you'll have to setup your virtual machine to a minimum RAM of 512 (I think or 1GB, you'll have to check) otherwise Vista won't install at all.

---

### Post by p_quarles on 2008-01-23
> **Victormd said:**
> Just a note when installing Vista, you'll have to setup your virtual machine to a minimum RAM of 512 (I think or 1GB, you'll have to check) otherwise Vista won't install at all.
Correct, 512 is the minimum for running it. 1 gig is the minimum for decent performance.

---

### Post by theZoid on 2008-01-23
VirtualBox IMO is the choice....check out this link to get your USB devices working, excellent how-to:

[http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)

Let us know.

---

### Post by yota on 2008-01-24
> **teejay17 said:**
> Fine. But what does that mean for me? Can I actually install it in Virtualbox now?

The official announcement is here [http://www.microsoft.com/Presspass/press/2008/jan08/01-21VirtualizationAdoptionPR.mspx](http://www.microsoft.com/Presspass/press/2008/jan08/01-21VirtualizationAdoptionPR.mspx)

and it says:
> 
Windows Vista Home Basic and Windows Vista Home Premium are now licensed for use in a virtual machine environment, and the updated end-user license agreement is available at [http://www.microsoft.com/about/legal/useterms/default.aspx](http://www.microsoft.com/about/legal/useterms/default.aspx).


but the EULA is still not updated...

---

### Post by teejay17 on 2008-01-25
Actually, I think I'm going to wait until 8.04 is released before I delve into this project. My main reason is that I want to install Ubuntu completely on my hard-drive, then install Vista via VirtualBox. 
Right now I dual boot, and I really don't see a point in having Windows on my machine twice. 
I'll do it right the first time, then be done with it for awhile; and what better to do it with than the next LTS.

---

### Post by bajun on 2008-01-25
I like VirtualBox. Very fast and useful. It supports big variety of OS. But XP installation on version 1.5.4 can freeze after USB patch, so apply this patch after installation.
And sorry for a little offtop, but i have found very useful for virtualisation tool - nLite for xp or vLite for vista. You can reduce the size of your windows installer to make very small virtual installation only for your specific needs.
I need virtual XP only for printing and my installation take around 800 Mb place now, and can not grow anymore, has 20 sec uptime by 192 Mb base memory, when normal installation take 3 Gb place and can grow very fast. You can delete almost everything from your installer. But this works only inside windows, so first I have installed standart virtual windows, then cropped variant.

---

### Post by dpj23 on 2008-01-25
I would use VMware since it seems to provide better back end support if you need research or trouble shoot

---

### Post by rosegarden78 on 2008-01-25
I found QEMU to be most useful it includes commands to make QCOW files at the XTerminal.  While VMWare purports to have the most power, I find their website too confusing and lacking simple installation instructions when I checked about nine months ago.  I prefer using WINE with a symlimk to Common Files on my Windows drive.  But you can run Windows 3.1 and Windows XP in QEMU for sure.

---

### Post by bajun on 2008-01-26
> But XP installation on version 1.5.4 can freeze after USB patch, so apply this patch after installation.
I have checked this behavior. Only incomplete patch can hang the windows xp installation. This is also not a problem.

---

### Post by dcstar on 2008-01-26
> **teejay17 said:**
> Actually, I think I'm going to wait until 8.04 is released before I delve into this project. My main reason is that I want to install Ubuntu completely on my hard-drive, then install Vista via VirtualBox. 
Right now I dual boot, and I really don't see a point in having Windows on my machine twice. 
I'll do it right the first time, then be done with it for awhile; and what better to do it with than the next LTS.

VMware has a free (Windows) utility to make a VM of your existing Windows install, so you won't have to do a total reinstall of Windows and all your apps if you want to make it a VM.

My Windows XP runs fine in the VMware server available in the Ubuntu (Partner) repos.

---

### Post by teejay17 on 2008-01-26
> **dcstar said:**
> VMware has a free (Windows) utility to make a VM of your existing Windows install, so you won't have to do a total reinstall of Windows and all your apps if you want to make it a VM.

My Windows XP runs fine in the VMware server available in the Ubuntu (Partner) repos.
Really? Would that be difficult?

---

