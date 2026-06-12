---
title: "Loading ubuntu partition from windows in VirtualBox"
date: 2008-04-29
forum: Virtualisation
---

### Post by etiennebr on 2008-04-29
Hi,

I have Ubuntu and Windows in dual boot and I would like to load that Ubuntu partition when I am on Windows, without the need to reboot. Is it possible ? Is VirtualBox ok for that ?

Thanks for your help,

---

### Post by Sand Lee on 2008-04-29
Definitely possible. You will have to install the closedsource virtualbox in ubuntu to make a .vmdk of your hard drive (if you haven't already). A bug does not allow you to do this in Windows.

```

sudo VBoxManage internalcommands createrawvmdk -filename UbuntuHH.vmdk -rawdisk /dev/sda -partitions 1,2 
```

Change the partition numbers to fit the ones you'd like to boot. I recommend making a .vmdk of the entire HD and another one specifying certain partitions to get rid of the risk of running the currently running OS/partition. 

If you want to make the file as a normal user use this command prior to running the one above (without sudo):
```
sudo usermod -G disk,vboxusers -a USERNAME_HERE
```

---

### Post by etiennebr on 2008-04-29
Thanks, I will try it.

> You will have to install the closedsource virtualbox in ubuntu to make a .vmdk of your hard drive (if you haven't already). A bug does not allow you to do this in Windows.

Are you supposed to see the Ubuntu partition running VirtualBox on windows ?

> I recommend making a .vmdk of the entire HD and another one specifying certain partitions to get rid of the risk of running the currently running OS/partition.

Which partition you think I should exclude ? My dual-boot is using two physically separate HD.

---

### Post by Sand Lee on 2008-04-29
Oh, I meant to say that Windows VBox currently can't specify linux partitions. You technically aren't supposed to "see" the partition, but windows will know it is there. I think you should exclude your windows partition since you will be running virtualbox on windows - this would prevent any chance of corruption by the method I mentioned earlier - loading a currently running partition.

---

### Post by etiennebr on 2008-04-29
Once I have my .vmdk, there is a problem (in Windows).
> 
VD: error opening image file 'D:\UbuntuHH.vmdk' (VERR_PATH_NOT_FOUND).


Code de résultat : 
E_FAIL (0x80004005)
Composant :
HardDisk
Interface : 
IHardDisk {fd443ec1-000f-4f5b-9282-d72760a66916}
Fonction called:
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

 
Linux
> 
VD: error opening image file '/home/etienne/UbuntuHH.vmdk' (VERR_ACCESS_DENIED).


Code de résultat : 
0x80004005
Composant :
HardDisk
Interface : 
IHardDisk {fd443ec1-000f-4f5b-9282-d72760a66916}
Fonction Appelée :
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}
 
Is it the partition path that is not found ? It did the same when I was in Ubuntu, but I taught it was because it was the actual operating system.

---

### Post by Sand Lee on 2008-04-29
hmm that's odd. Did you try making the .vmdk as a regular user? Don't forget to run the usermod command to add yourself to the disk group. That would probably fix the access problem.

Ohh, I almost forgot! For the file to work in windows, you've got to make some minor changes with gedit. It is saying path not found because the harddisk naming scheme is still in linux format (/dev/sda) and you've got to change it the windows format. I forget what it is though, I'll get back to you on that later... You could probably find it in the usermanual.

EDIT: The change proposed above is not without doubts. I remembered that linux has a method of reading hard disk geometries (what ever that means), so I'm not really sure what affect that will have.

Also you could still try making the .vmdk in windows, however you won't be able to specify partitions. You'll need the usermanual Part 9.9

---

### Post by etiennebr on 2008-04-30
Thanks Sand Lee,

I can't hide much to you, I did not add myself to the disk group ! I wanted to keep only the root as the one making dangerous things. But I will add myself to the disk group, but i do not understand what it will change on Windows side. As this is a lot of rebooting (where virtualization will come handy !) it is pretty slow to try things while staying productive. 

I've take a look at the usermanual, but they always gives examples in linux. I'm not tight enough to translate these to Windows. And every one is doing exactly the opposite than me, using an existing  windows partition in Ubuntu, but I need Ubuntu when I am in Windows !

---

### Post by Wake Rider on 2008-05-01
> **Sand Lee said:**
> Definitely possible. You will have to install the closedsource virtualbox in ubuntu to make a .vmdk of your hard drive (if you haven't already). A bug does not allow you to do this in Windows.

```

sudo VBoxManage internalcommands createrawvmdk -filename UbuntuHH.vmdk -rawdisk /dev/sda -partitions 1,2 
```

Change the partition numbers to fit the ones you'd like to boot. I recommend making a .vmdk of the entire HD and another one specifying certain partitions to get rid of the risk of running the currently running OS/partition. 

If you want to make the file as a normal user use this command prior to running the one above (without sudo):
```
sudo usermod -G disk,vboxusers -a USERNAME_HERE
```

I am interested in doing the same sort of thing. Can you please elaborate a bit more on how it is done, particularly the part about making the .vmdk of the entire harddrive and of the partitions you want to boot?

---

### Post by Sand Lee on 2008-11-22
Please see this tutorial for more information [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

