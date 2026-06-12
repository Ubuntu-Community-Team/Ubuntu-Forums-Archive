---
title: "Mount NTFS drive in ESXI Ubuntu Desktop"
date: 2015-08-09
forum: Virtualisation
---

### Post by don39 on 2015-08-09
Hi Guys,

I've just started playing with ESXI and Ubuntu.

I'm in the process of setting up a PLEX media server on Ubuntu Desktop which in turn is installed on ESXI 6.0.

So far I've installed Ubuntu Desktop and set it up as a Domain Controller.
I've installed Plex and would now like to mount an NTFS drive with media.

How do I go about doing that?

Thanks, 

Don

---

### Post by cj13579 on 2015-08-09
Hello and welcome to the forums! There are couple of pretty good guides for going about mounting NTFS drive in Ubuntu. One of them is even written by the friendly folk over at Plex. Take a look at the following sites:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux)

---

### Post by don39 on 2015-08-10
> **cj13579 said:**
> Hello and welcome to the forums! There are couple of pretty good guides for going about mounting NTFS drive in Ubuntu. One of them is even written by the friendly folk over at Plex. Take a look at the following sites:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux](https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux)

Hi Chris,

Thanks for the reply.

Unfortunately it appears to be an issue with ESXi. 
Any drives added need VMFS (rather than NTFS) before it will be recognised.

If I were only installing Ubuntu on the server ( and not on top of ESXi) then those links would probably have worked.

---

### Post by cj13579 on 2015-08-10
Nightmare. A quick google seems to suggest that you can use your NTFS drives by doing some Raw Device Mapping. Depending on what you read and how you do it seems to depend on whether or not it is supported though :S

---

### Post by don39 on 2015-08-10
> **cj13579 said:**
> Nightmare. A quick google seems to suggest that you can use your NTFS drives by doing some Raw Device Mapping. Depending on what you read and how you do it seems to depend on whether or not it is supported though :S

Yeah, I've seen references to Raw Device Mapping. 
What little I've read indicates its not a good idea.

I'm going to have to move the data off the drive, then copy it back on which will take a while as its a 6TB drive.

Thanks for trying to help anyway. :)

---

### Post by nlee2 on 2015-08-12
If your motherboard supports DirectPath I/O for your drive controller then that is another option.

---

