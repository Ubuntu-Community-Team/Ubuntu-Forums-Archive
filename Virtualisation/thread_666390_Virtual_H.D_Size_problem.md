---
title: "Virtual H.D Size problem"
date: 2008-01-13
forum: Virtualisation
---

### Post by jmclein on 2008-01-13
I have been running a virtual copy of XP under virtualbox for about a week and and I absolutely love.  I decided to install SP 2 but not I have encountered a small problem.  I am using one of the automatically expanding virtual drives (Sorry, I don't remember the name) and when I attempt to install SP2 it tells me there isn't enough space.  This makes sense as windows probably doesn't know that the drive will expand.  Is there a way to increase the size of the drive so windows sees enough space to extract SP2?  I thought about just creating another drive and extracting it there but I am thinking it has to be done on the main drive with the system files.  Any help would be greatly appreciated.   

Thanks!

---

### Post by popch on 2008-01-13
The automatically growing drives have an upper size limit. Have you made sure that the drive's current size is not already near that limit? Have you made sure that the partition which contains your virtual drive is in fact large enough to hold the increase in size needed for installing SP2?

---

### Post by jmclein on 2008-01-13
> **popch said:**
> The automatically growing drives have an upper size limit. Have you made sure that the drive's current size is not already near that limit? Have you made sure that the partition which contains your virtual drive is in fact large enough to hold the increase in size needed for installing SP2?

The partition that the virtual drive is on does have plenty of room to expand.  I am not quite sure what you mean by "Have you made sure that the drive's current size is not already near that limit" though.  The virtual drive IS close to full.  Thats why I thought that windows was thinking it was to small to hold what I was trying to extract (Not realizing what it would automatically expand.) and I was looking for a way to increase the size so windows would think there was enough space.

---

### Post by popch on 2008-01-13
I am not at the moment near a computer which has VirtualBox installed. Therefore, I can not guide you step by step.

However:

The virtual disk you are using in VirtualBox has several properties. One of those properties is the maximum size it is allowed to reach. Another property is the size it has right now, at the moment. It appears that it already has reached the size it is allowed to.

In VirtualBox there is a window showing the properties of all virtual disks. I presume that you can reach that window in the main window of VirtualBox through the menu file/virtual disks or some such. There you should see a list of all virtual disks defined within your system. Open the property editor for the virtual disk you are interested in. Check if there is an entry for 'maximum size'. Increase the number given there.

In order for that to work you have possibly to shut down your virtual XP machine (and not just freeze it).

I hope that this helps. I will be back home in a few hours and can try and look up where to find those things if you have not succeeded by then.

---

### Post by jmclein on 2008-01-13
> **popch said:**
> I am not at the moment near a computer which has VirtualBox installed. Therefore, I can not guide you step by step.

However:

The virtual disk you are using in VirtualBox has several properties. One of those properties is the maximum size it is allowed to reach. Another property is the size it has right now, at the moment. It appears that it already has reached the size it is allowed to.

In VirtualBox there is a window showing the properties of all virtual disks. I presume that you can reach that window in the main window of VirtualBox through the menu file/virtual disks or some such. There you should see a list of all virtual disks defined within your system. Open the property editor for the virtual disk you are interested in. Check if there is an entry for 'maximum size'. Increase the number given there.

In order for that to work you have possibly to shut down your virtual XP machine (and not just freeze it).

I hope that this helps. I will be back home in a few hours and can try and look up where to find those things if you have not succeeded by then.

I opened the "Virtual Disk Manager" and I see the virtual disk in questions however I can't seem to find anywhere that mentions maximum size or anyway to change any options.  The only thing I can do is add, refresh, etc.

---

### Post by popch on 2008-01-13
The virtual disk manager shows two columns containing sizes. One is labelled 'virtual size', and that's the upper limit. The other one is the virtual disk's actual size.

After a quick visit both to the VirtualBox user manual and the forum I come to the conclusions:
[LIST]
[*]that VirtualBox does not offer any way of increasing the capacity of a virtual disk
[*]that some users have found ways to copy the contents of a smaller virtual disk to a larger, empty one.[/LIST]The keyword to look for in the VirtualBox forum is VDI (presumably Virtual Disk Image).

---

