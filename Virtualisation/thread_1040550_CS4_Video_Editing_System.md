---
title: "CS4 Video Editing System"
date: 2009-01-15
forum: Virtualisation
---

### Post by ricochet on 2009-01-15
Need some advice.  I am about to build a video editing system and will need to use Adobe CS4 products on this machine.  I would like to have ubuntu as the main os then virtualizae windoz xp.  My main concern is that there will be a large performance loss by having CS4 running in a virtualized os.  I also understand there could be some huge gains if I can minimize windoz services.  Has anyone tried this?  I have never tried virtualizing windoz just dual booting.  What virtualization software would you recommend for this kind of setup?  Last question we were planning to use xp pro, would you recommend 32 or 64 version?

Thanks
Richie

---

### Post by Dedoimedo on 2009-01-16
Hello,

The choice of the host operating system + virtualization software will govern whether you can run 64-bit.

If you can, then by all means. However, do you have 64-bit Windows?

If you have plenty of RAM to spare, you won't get too much of an issue. I expect performance to be at 80% with sufficient RAM.

However ...

You should also consider using a second hard disk to speed things up. IO on a single hard disk fighting between host and guest will slow things down considerably. A second, non-OS disk used for virtualization will help tremendously.

See here:
[http://www.dedoimedo.com/computers/virtualization-tips.html](http://www.dedoimedo.com/computers/virtualization-tips.html)

Lastly, if you need special drivers for the video editing software or 3D acceleration, then things might not work. However, I've got a few tutorial on 3D in virtual machines, so you may want to check those out, too.

Dedoimedo

---

### Post by ricochet on 2009-01-21
Here is what I am thinking that I will try.

1st HD install linux.
2nd HD two partions 1st partion full windozs install, 2nd partion with a minimized windoz install to use when virtulizing in linux.
3rd HD will be a raid formated NTFS for the video files.

CS3 did not support multicore processing so I think if I minimize windows services that I might break even on processing power.  If it does not work I can dual boot into Linux or the full windows install.  

Do you see any problems with a setup like this that I should watch out for?  Also I do not know which virtualization software to use, I need something that is going to be pretty easy, but not sacrifice much power.  Recommendations?

---

### Post by Dedoimedo on 2009-01-22
Your setup? Do you intend to you the physical partition in the virtual machine? That can be slightly risky. If you make mistakes, you can corrupt your data ...

Something easy - VirtualBox.

Dedoimedo

---

### Post by ricochet on 2009-01-22
> **Dedoimedo said:**
> Your setup? Do you intend to you the physical partition in the virtual machine? That can be slightly risky. If you make mistakes, you can corrupt your data ... 

Perhaps I am having an off day but your answer does not make sense to me.  Do you mean running windows on a HD that is partioned is risky when virtulizing?  All of the important data would be stored on a separate NTFS raid10.  That way if anything happens to the windows os hd, all of the data should still be intact. Or do you mean creating the partion in the virtual machine?

No critical data will be used until I know that everything is running smoothly.

Thanks
Richie

---

### Post by Dedoimedo on 2009-01-22
Hello,

I understood the following: you intend to use the second windows partition in your virtual machine. This means mounting a physical partition inside the virtual machine ... and this can be risky.

The other option is: simply place the virtual machine files on this second partition and use them the 'classic' way. This has very little, if any, risk involved re data corruption.

Cheers,
Dedoimedo

---

### Post by ricochet on 2009-01-22
> **Dedoimedo said:**
> 
The other option is: simply place the virtual machine files on this second partition and use them the 'classic' way. This has very little, if any, risk involved re data corruption.


Since I have never created a virtual install of windows Im not sure what you mean by the "classic" way.  

Thanks
Richie

---

### Post by ricochet on 2009-01-29
> **ricochet said:**
> I am about to build a video editing system and will need to use Adobe CS4 products on this machine.  I would like to have ubuntu as the main os then virtualizae windoz xp.  

Has anyone tired this?

Thanks
Richie

---

### Post by Dedoimedo on 2009-01-30
Sorry for the delay ...

Classic way means the virtual machine is a file. So all data is contained in a file located somewhere on your real machine. If you ruin this virtual machine somehow, you merely delete a file and it's as if nothing ever happened.

Dedoimedo

---

### Post by gtdaqua on 2009-01-30
For video editing, you would rely heavily on 3d acceleration etc - these are not very good inside virtualized containers. Best use the host system for such operations. Use WinXP 64 bit. Adobe can max use only 2GB even if you have 64GB of memory.

Why do you want to run ubuntu? If you insist, run ubuntu inside WinXP. Anyway, ubuntu is not a resource hog and you won't notice any performance drop in ubuntu guest vm. But if XP is guest, you will definitely see a drop running CS4 or any such mighty resource consuming app.

---

### Post by psidrum on 2009-10-29
> **ricochet said:**
> Has anyone tired this?

Thanks
Richie


I tried with CS4 running on 64bit Ubuntu, you are better off running it on a regular machine and not virtualized, it is slow, im running CS4 on dual cpu,

---

