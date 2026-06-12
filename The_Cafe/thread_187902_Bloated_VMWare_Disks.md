---
title: "Bloated VMWare Disks"
date: 2006-06-03
forum: The Cafe
---

### Post by rcarring on 2006-06-03
Although a df showed that over 6GB was free in the 10GB hard file I was using, the size of the file on disk approached 8GB. Now, I had the hard file set to grow, and a simple install of Dapper caused it to go from 3GB when it ran Breezy, to nearly 5GB, and installing a couple of hardly-the-world's-biggest-apps such as Lyx, generated another 1GB.

I don't think the bloat is Dapper's fault, I think its the way VMware grows its hard file.

Anyway, after an unsuccessful attempt at getting IE6 installed under Crossover Office -- and the fact that the hard file was still growing even when I wasn't doing anything, I decided the best way was to create a full 10GB hard file, and see how that worked.

The advantage is that it should be faster as it won't have to grow. I am also interested in if it makes Dapper run faster.

---

### Post by paul cooke on 2006-06-03
if you are using vmware workstation then you could try defragging the volume (you have to have shut down the running image first)

go to edit virtual machine settings

select the hard disk in the hardware list

click on the degragment button

follow the prompts

NOTE: you cannot defragment a volume if you've suspended it. You have to have shut down the OS running in the VM properly first.

NOTE: you cannot defragment with the free vmware player application

I'm not sure about the vmware server being able to defragment as I haven't got it.

---

### Post by imagine on 2006-06-03
The server is also able to defragment virtual disks.

---

### Post by rcarring on 2006-06-03
I deleted the hard file and built a new config. Amazingly this time Dapper found the network card!. I haven't installed vmware tools, as I don't think I need to now. I use Windows shares to access files on my host pc and I don't need to print directly from the vm. Dapper is a lot faster.

---

### Post by jdong on 2006-06-03
I believe VMWare Tools has a shrink feature that re-organizes the virtual disk files to be more space efficient... I'm not sure if Linux VMWare tools does it, but the Windows one definitely does.

---

### Post by rcarring on 2006-06-04
I havent been able to find out much about it from the help under Windows, but I did read on after searching online that as much space as the existing hard file is required to compact it, which is why I switched to fully allocated disk space.

---

