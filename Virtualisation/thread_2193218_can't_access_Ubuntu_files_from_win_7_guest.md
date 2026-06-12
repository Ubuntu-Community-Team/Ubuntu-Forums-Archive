---
title: "can't access Ubuntu files from win 7 guest"
date: 2013-12-11
forum: Virtualisation
---

### Post by cmcanulty on 2013-12-11
I have been studying this for hours and can't get so I can see my ubuntu files from the win 7 guest I have my home folder shared in VB and tried the mount I read to do but get an error. I need **simple** directions. I am trying to share my home folder and do have it marked shared in Ubuntu and added in the VB share option. As you can see below I tried 2 different commands but neither works. I do have the guest additions installed and can mount my flash drive OK once I learned I had to unmount it from Ubuntu first.

```
cmcanulty@darcytech:~$ sudo mount -t vboxsf -o uid=$UID,gid=$GID share ~/host
[sudo] password for cmcanulty: 
mount: mount point /home/cmcanulty/host does not exist
cmcanulty@darcytech:~$ sudo mount -t vboxsf -o uid=$UID,gid=$GID share ~/host/home/cmcanulty
mount: mount point /home/cmcanulty/host/home/cmcanulty does not exist
cmcanulty@darcytech:~$ 
```

---

### Post by electrohandyman501 on 2013-12-11
I can't say if this is your issue or not as I don't use VB with Linux host. I have a dual boot machine with win 7 and Ubuntu on individual paritions.

One thing that I have found is that when I am in the Windows boot I cannot see the stand alone linux partitions, because windows cannot read the linux ext file system.
I can read my windows ntfs and fat32 partitions when booted linux, but not the other way around.
If I format a thumb drive in an ext format, say for a LiveUSB, the machine may boot and read it, but if I'm already booted windows and plug it in, the drive is not reconized.

---

### Post by codenine75a on 2013-12-11
I had this problem too.  I had to understand it was a virtual or "brain in a box"  The only way to access files is to use external means.  Such as using file servers or a physical USB drive.

---

### Post by Toz on 2013-12-12
> **cmcanulty said:**
> I have been studying this for hours and can't get so I can see my ubuntu files from the win 7 guest I have my home folder shared in VB and tried the mount I read to do but get an error. I need **simple** directions. I am trying to share my home folder and do have it marked shared in Ubuntu and added in the VB share option. As you can see below I tried 2 different commands but neither works. I do have the guest additions installed and can mount my flash drive OK once I learned I had to unmount it from Ubuntu first.

```
cmcanulty@darcytech:~$ sudo mount -t vboxsf -o uid=$UID,gid=$GID share ~/host
[sudo] password for cmcanulty: 
mount: mount point /home/cmcanulty/host does not exist
cmcanulty@darcytech:~$ sudo mount -t vboxsf -o uid=$UID,gid=$GID share ~/host/home/cmcanulty
mount: mount point /home/cmcanulty/host/home/cmcanulty does not exist
cmcanulty@darcytech:~$ 
```

If you have a Windows 7 guest and you want to see your Ubuntu files, you need to do the mapping from within Windows 7.

The first thing to do is in VirtualBox (in Ubuntu), under the properties for the Windows 7 guest -> Shared folders section, click the + to create a new share and set:
- Folder Path = path to the Ubuntu folder you want to share
- Folder Name = the name you want to give your share
- check the "Make permanent" button.

Then from within the guest (Windows 7), map a network share to \\vboxsvr\share (where share is the name of the share you set up previously).

---

### Post by cmcanulty on 2013-12-12
OK I did that and get an error I put \\vboxsvr\home\cmcanulty and get in the map network drive and get an error[ATTACH=CONFIG]248541[/ATTACH]

---

### Post by Toz on 2013-12-12
> **cmcanulty said:**
> OK I did that and get an error I put \\vboxsvr\home\cmcanulty and get in the map network drive and get an error[ATTACH=CONFIG]248541[/ATTACH]

Can you show a screenshot of the folder share definition in VirtualBox? The one in Ubuntu where you specify the share?

---

### Post by cmcanulty on 2013-12-12
[ATTACH=CONFIG]248545[/ATTACH] thanks I do have the \\vboxsvr\ before what you can see as \home\cmcanulty

---

### Post by Toz on 2013-12-12
In Windows 7, map to \\vboxsvr\cmcanulty (not \\vboxsvr\home\cmcanulty).

---

### Post by cmcanulty on 2013-12-12
OK nothing seems to work, what exactly do I type in top and bottom box. When I tried your solution the ok is greyed out so can't add that folder

---

### Post by Toz on 2013-12-12
In Ubuntu's Shared Folders dialog:
- Folder Path = /home/cmcanulty 
- Folder Name = cmcanulty       <===== change this

In Windows 7:
- map a drive to \\vboxsvr\cmcanulty (you have this correct)

---

### Post by cmcanulty on 2013-12-13
sorry but what do I change cmcanulty to in folder name?

---

### Post by Toz on 2013-12-13
> **cmcanulty said:**
> sorry but what do I change cmcanulty to in folder name?

The folder name should be set to just **cmcanulty**. Its just a label, not a path.

---

### Post by cmcanulty on 2013-12-13
but you said don't set it to cmcanulty now say it is OK I have the path as /home/cmcanulty and name as cmcanulty something is wrong as it doesn't work I also tried //vboxsvr/home/cmcanulty and that doesn't work either. Now after I changed the share settings the win 7 won't boot so I am reinstalling. I think maybe the issue is ubuntu is not keeping my setting of home folder as shared so now I will try to share just docs and desktop. But there seems to be contrary advice on the path to shared folders in VB some say format is /cmcanulty and some say //vboxsvr/path to folder. After reinstall still can't share a folder. I feel as if there is something basic I am missing

---

### Post by Toz on 2013-12-13
> **cmcanulty said:**
> but you said don't set it to cmcanulty
When? 
> now say it is OK I have the path as /home/cmcanulty and name as cmcanulty something is wrong as it doesn't work I also tried //vboxsvr/home/cmcanulty and that doesn't work either
Here are my screenshots:
[[img]http://en.zimagez.com/miniature/154970c362294f2028bf3ad519f1701da.png[/img]](http://en.zimagez.com/zimage/154970c362294f2028bf3ad519f1701da.php)
[[img]http://en.zimagez.com/miniature/39f331c5d7e521b4916b2ad60e8cc88ea.png[/img]](http://en.zimagez.com/zimage/39f331c5d7e521b4916b2ad60e8cc88ea.php)

EDIT: Have you installed guest additions in Windows 7?

---

### Post by cmcanulty on 2013-12-13
[ATTACH=CONFIG]248574[/ATTACH]

no I didn't realize I needed to now I downloaded the ext pack in windows and installed it anything else I need to do?As the shares are still not visible there is a icon in the win 7 computer view that I am attaching a screenshot of but it will only open with media player

---

### Post by Toz on 2013-12-13
From the Windows 7 VirtualBox window (with the Windows 7 VM running), select "Devices" then "Install Virtualbox Additions...". A dialog should pop up to start the installation. If not, go look at your CD drive in My Computer to start it.

Here is a youtube video that shows how to do it: [http://www.youtube.com/watch?v=vi53zKcvgXU]("http://www.youtube.com/watch?v=vi53zKcvgXU").

---

### Post by cmcanulty on 2013-12-13
oh I've been down that route when I tried this last year there is no devices tab
[ATTACH=CONFIG]248577[/ATTACH]
[ATTACH=CONFIG]248578[/ATTACH]

---

### Post by Toz on 2013-12-13
Looks like you might be in scaled mode - this would cause the menu to disappear. The default host key is the **Right Ctrl** key. Assuming you haven't changed it, try pressing **Right Ctrl+C** to exit scaled mode. (that is, press and hold the Right Ctrl key and while it is depressed, press the C key).

---

### Post by cmcanulty on 2013-12-13
oh wow that was it now I see everything. Do you always have to do the guest additions in both host and guest? I never read that anywhere in all my research. Thanks very much for your time.

---

### Post by Toz on 2013-12-13
> **cmcanulty said:**
> oh wow that was it now I see everything. Do you always have to do the guest additions in both host and guest? I never read that anywhere in all my research.
You should install the guest additions, but only in the guest. No need to install it in the host. Reference: [http://www.virtualbox.org/manual/ch04.html]("http://www.virtualbox.org/manual/ch04.html"). The guest additions provide many enhancements including better video, integrated mouse and shared folders.

> Thanks very much for your time. One other question. I am putting Lubuntu as a guest on a friends win 7 would it be possible to have the Lubuntu guest with a separate home partition. I want to promote the ease of Linux and that way their settings would be stable in case of a disaster.
Sure, but both the home partition and the root partition will still be on the same virtual hard drive. When creating the virtual hard drive, specify enough space to hold both partitions and then during lubuntu install, create separate home and root partitions.

---

