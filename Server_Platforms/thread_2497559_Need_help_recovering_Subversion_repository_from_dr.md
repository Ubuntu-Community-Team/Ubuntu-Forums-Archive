---
title: "Need help recovering Subversion repository from drive of dead server"
date: 2024-05-09
forum: Server Platforms
---

### Post by twidget on 2024-05-09
Hi All,
My problem is basically what the title says. I used to have an SVN server but unfortunately, I left it sitting for too long or maybe something got damaged during a move and the server no longer boots. I believe I have a decent chance of accessing the files on one or possibly both of the drives on which the repo was stored, but have no idea how to pull the repo out, given that the machine isn't bootable. A possible secondary problem is that I'm not sure if I remember the username/password for the actual repo. So I my questions are:
[LIST=1]
[*]Is it possible to recover the repo?
[*]Is it possible to recover the repo without credentials for the old machine?
[*]How do I best go about recovering the repo if it is doable? A link to a tutorial would be fine.
[*]
[/LIST]
The OS on the drive is likely something like Ubuntu Server 12.04 if that makes a difference. I was thinking of maybe imaging one of the drives and then trying to get the image(s) to boot in Virtualbox, if there isn't a way to just export the repository directly from the drive.

---

### Post by ajgreeny on 2024-05-10
Have you tried using a live system booted on that problem machine which may give you an option to copy files you need to another disk.
Is encryption involved? If so you may have to accept that all those files are gone for good if you really can't remember the passphrase.

---

### Post by twidget on 2024-05-10
Thank you for the reply. That was more or less what I was thinking about trying using Virtualbox. The question is, can I build myself a virtual system, install the current version of SVN, mount the partition and somehow import the old repository? 
I think the /home partition may have been encrypted, but probably not /var. I believe I remember the username and password for the system, but I'm not sure if those are the same credentials as were used when creating the repository.

---

### Post by twidget on 2024-05-11
Looks like at least one of the drives still has a functional partition. Having GParted image that to a virtualbox partition now. Is there a way to read a RAID 1 partition? Or should I build a Ubuntu Server VM and either try to have mdadm rebuild the array, or image the other drive and do the same?

---

### Post by twidget on 2024-05-14
I imaged both drives and after much fiddling got a vm of Ubuntu Server up and running. I would recommend using the first .VDI as the boot drive. Otherwise you run into issues with booting because virtualbox will try to boot off the first drive created. There is a way to change the boot order of the drives in virtualbox if you don't do this, but easier to plan ahead.
If you installed server without the raid drives attached like I did, mdadm will still try to read the array. In my case, ```
sudo fdisk -l
``` showed that my array was located at /dev/md127.
In my case mdadm said that 1 of two drives was functional, so it would seem that it should be possible to image the minimum number of drives for a functional array and still be able to access the array.
Made a directory called salvage in /home/username and mounted /dev/md127 there. This let me browse the RAID 1 array contents.
Installed subversion and apache 2 for good measure.
```
mkdir /home/username/USB_Storage
```
Mounted a flash drive to /home/username/USB_Storage.
I have run an ```
sudo svnadmin dump /repo/path > dumpfile.dump
``` successfully. 
I used ```
sudo svnadmin create /var/lib/svn/repo
sudo chown -R www-data:www-data /var/lib/svn/repo
sudo chmod -R 775 /var/lib/svn/repo
``` to create a repository on the new host machine.
Using ```
sudo svnadmin load /var/lib/svn/repo < dumpfile.dump
``` fails at revision 75 out of 586 due to a checksum error.
Does anyone know how to fix this either in the dumpfile or in the original repo before I generate the dumpfile?
So far I've found recommendations to use something like ```
sed -i '/Text-copy-source-md5/d' your.dmp
``` but with no explanations about what sed is or how to use it.

---

### Post by twidget on 2024-05-18
looks like the correct way to use the sed command is:
```
sudo sed -i '/Text-content-md5/d' svnexport.dump > cleanedfile.dump 
```
and then loading the clean file. It seems as if the output of the dump command varies for some reason. I have run six separate dumps using my VM, cleaned them all with the above command and had load terminate at a different revision with different errors. Does anyone have any clue why that would be? The command is executing on a purely virtual machine so AFAIK there should be no variation in the output unless the changes occur when I transfer the dumps to my flash drive. Running sed on the original dumpfile again and then loading the result terminates at the same spot with the same error so the issue seems to be either with svnadmin dump or the flash drive.
Currently my most promising dump file gets me to commit 548/586 so i'm close at least. The load for that file terminates with  ```
svnadmin: E140001: Dump stream contains a malformed header (with no ':') at 'Prop-content-leng   ' 
``` Does anyone know how to fix that? I'm not finding much with google.

Edit: I got to rev. 567 by doing an incremental dump:
```
sudo svnadmin dump /repo/path -r 549:HEAD --incremental > svn549.dump
```
cleaning the result as usual and then doing the load on the destination machine. This seems to be as far as I'm going to get though as no matter how many times I try dumping and loading at rev. 568 I get the following
 ```
svnadmin: E200014: Copy source checksum mismatch on copy from 'classWork/trunk/thesis/...
``` 
I think this might be an actual problem with the source repo given the consistency of this error. I don't particularly mind losing the .pdf that the error message points to, but I think actually skipping the complete revision might break the repository.
As a side note, the current repo dumps from and then loads to the same machine just fine. Maybe I'm having issues because I'm using an old version of SVN to dump an even older repo and then trying to load it with the latest version of the software?

---

