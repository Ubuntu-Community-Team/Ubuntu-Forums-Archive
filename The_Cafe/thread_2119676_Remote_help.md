---
title: "Remote help"
date: 2013-02-24
forum: The Cafe
---

### Post by Aesculus on 2013-02-24
Let's supose (it's the real case btw) that you have a friend that crashed his Windows systems. That person is not an advanced user and think that lost everything (maybe not but he is not able to recover). You (I would like be my case but is not entirelly) want to help and at time convince him to work with Ubuntu or at least in a dual system.

My goal is perform the following steps, keeping in mind that I want to recover files probably deleted (not formatted low level) and ask from him as less as possible things to do locally:
- He was able to create a Ubuntu live CD in another computer, and his pc starts from CD.

- Start the cd and instruct him to do whatewer is needed to give you remote control thought internet.

-You create a bootable USB with the Ubuntu distro and the tools you will need. Even prepare the USB pendrive to start the programs you need to remotelly take control again and complete the next steps.

- Ask your friend from restart. Here you can face a problem if the pc doesnt boot from USB. I think the only solution here is intruct your friend to change the boot and can be a difficult task beind "blind".

- Once you have the control you should be able remotely to recover files copying into another system like CD, pendrive or the own bootable USB in case of enoguh space. You will need to think in the tools yuo want to use to recover files and or hd.

- Repartitioning disk. I prefer three partitions. One free for windows, one to install Uuntu 
and one for Data (ntfs to be visible in any case). swap can be managed at installation process

- Install Ubuntu in second partition and restart system from hd. I would like to point the Users folder into the Data partition to better have a part system different than personal data.

- Give your friend the chance to install Windows in first partition and awaring him about the problems you will have to solve when booting (grub) will crash for that effect.

My questions are: 
- Do these steps seem coherent and logical or I missed something important or is better do in another way (I'm very far to visit my friend's house unfortunatelly)?
- In such case what are the detailed steps to follow? I can make the whole tuturial copying and pasting from others but not sure which ones are the better, clear ones.

Thanks in advance for your comments.

---

### Post by Branimir on 2013-02-24
Sounds complicated? Especially windows install part.
Why not just tell him to reinstall Windows without
partitioning hdds?

---

### Post by Aesculus on 2013-02-24
Well, first of all he think he has lost all his data files (docs, photos...). I don't think so. For that reason I prefer not install any other OS in the hd till try to recover them. Probably, I'm not sure, the live CD of Ubuntu doesnt have the proper tools inside to perform the recovery. For that reason I think create the bootable USB and install the tools on it is better. 

After the recovery process (if possible) I think it's a good opportunity to "evangelize" him in Linux, but giving him still the chance to use Windows.

However, the target is to recover files and have a OS working after that.

---

### Post by mamamia88 on 2013-02-24
> **Aesculus said:**
> Well, first of all he think he has lost all his data files (docs, photos...). I don't think so. For that reason I prefer not install any other OS in the hd till try to recover them. Probably, I'm not sure, the live CD of Ubuntu doesnt have the proper tools inside to perform the recovery. For that reason I think create the bootable USB and install the tools on it is better. 

After the recovery process (if possible) I think it's a good opportunity to "evangelize" him in Linux, but giving him still the chance to use Windows.

However, the target is to recover files and have a OS working after that.

Well if the harddrive is still in tact then copy the files he needs to another medium like flash drive or external drive.  if the drive has gone bad there really isn't much you can do.  the windows partition should show up in the live envirnment just like an external drive if it's working

---

