---
title: "WinXP virtualnox crash the ubuntu 11.10 server"
date: 2011-11-05
forum: Virtualisation
---

### Post by odror on 2011-11-05
OS: ubuntu 11.10 64bit
VB : 4.1.2
Hardware: 9gb ram. core i7 950 virtualization enabled.
VM machine: 4 processors, 3446mb ram, video 128MB 3D, Network: Bridge Adaptor, PCnet-Fast !!! (am79C973)

everything was fine until I installed cisco-vpn variant (possibly unrelated).

The problem is hard to track down, but when I use the virtualbox (possibly when accessing the internet), The system freeze. It may unfreeze itself if I wait, or if it does not the whole system crash. I mean the ubuntu server crash. When I reboot the system I cannot find any system error messages to help out. 

My biggest issues are:
1. how can a virtualbox client crash my computer.
2. how to identify the bug, when there is no error message.

Thanks

---

### Post by LinuxFan999 on 2011-11-12
I have 2 questions for you:
 
1. How does the Host crash? Is it a kernel panic (black screen with text, including the word "panic")?
 
2. Does it crash with other guests (if you have any)?

---

### Post by odror on 2011-11-12
> **LinuxFan999 said:**
> I have 2 questions for you:
 
1. How does the Host crash? Is it a kernel panic (black screen with text, including the word "panic")?
 
2. Does it crash with other guests (if you have any)?

I did not get any messages, I think that there are two issues.
1. Winxp guest cannot have 3GB of ram. I changed it to 2.
2. I have an i/o error in my ssd drive. I am in the process of switching drives. Because of the i/o error I was not able to clone the drive. By now I was able to copy the files to the new drive. I have issues with recreating the MPR. The new drive has an old linux MBR that I was not able to replace (using boot-repair).

 It seems that as soon as linux finds that there is a localized i/o error. it changes the drive (root file system) to read-only. This is why there are no error messages. The defect in the drive seems to be confined to the image file of winxp.

---

### Post by LinuxFan999 on 2011-11-12
> **odror said:**
> I did not get any messages, I think that there are two issues.
1. Winxp guest cannot have 3GB of ram. I changed it to 2.
2. I have an i/o error in my **ssd drive**. I am in the process of switching drives. Because of the i/o error I was not able to clone the drive. By now I was able to copy the files to the new drive. I have issues with recreating the MPR. The new drive has an old linux MBR that I was not able to replace (using boot-repair).
 
It seems that as soon as linux finds that there is a localized i/o error. it changes the drive (root file system) to read-only. This is why there are no error messages. The defect in the drive seems to be confined to the image file of winxp.
Why would you ever use an SSD in a server? SSDs are unreliable and immature. Use a mechanical hard drive instead, which is much more reliable and mature.

---

### Post by odror on 2011-11-12
> **LinuxFan999 said:**
> Why would you ever use an SSD in a server? SSDs are unreliable and immature. Use a mechanical hard drive instead, which is much more reliable and mature.

Because it is faster and I use it as a desktop as well. My best computer is the server/desktop. I have used ssd for 2 years with no problems. This new (defective) ssd is OCZ sata3.

---

