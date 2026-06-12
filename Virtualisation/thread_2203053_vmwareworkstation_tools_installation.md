---
title: "vmwareworkstation tools installation"
date: 2014-02-01
forum: Virtualisation
---

### Post by sniper8752 on 2014-02-01
I am trying to install the tools to share a folder, but it just tells me that I cannot be logged into  the guest OS, and I need to mount the CD drive in the guest, launch a terminal, and uncompress, and execute it to install it.  how do I install this?  i am not sure where the package is.

---

### Post by bashiergui on 2014-02-02
Where are you stuck in these directions?
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1014294](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1014294)

---

### Post by sniper8752 on 2014-02-02
I am stuck here: [http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=1022525](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=1022525) - step 4.  How do I do this?  In /media, I see cdrom.  Am I in the right place?  How do I mount it?

---

### Post by bashiergui on 2014-02-02
Scroll down to the section "Ubuntu Server with only a command line interface" and it tells you how to mount it. I think the first section assumes that it automatically mounts, which it apparently didn't do for you.

---

### Post by sniper8752 on 2014-02-03
so I followed this [https://www.vmware.com/support/ws5/doc/ws_running_sharedfolder_viewing.html](https://www.vmware.com/support/ws5/doc/ws_running_sharedfolder_viewing.html) at the bottom, but I only see cdrom.  I made sure that I shared a folder with the machine.

---

### Post by bashiergui on 2014-02-03
Why are you sharing folders? Were you able to install the tools or are you sharing the folder for that?

---

### Post by sniper8752 on 2014-02-03
I am sharing the folder for that.  I would like to get the contents of a config file.

---

### Post by bashiergui on 2014-02-03
What was the result when you tried to mount the drive using the command line? Did you download the tools?

---

### Post by sniper8752 on 2014-02-04
I try mount cdrom when in /mnt, and get this error:
mount: can't find cdrom in /etc/fstab or /etc/mtab

---

### Post by bashiergui on 2014-02-04
Ok, let's back up. You never said, so I'm assuming you have an Ubuntu computer with an Ubuntu in a VMware VM. Correct me if I'm wrong.

What you should be trying to do is on your computer, open vmware, boot the VM. Then in the VMware toolbar you should click "install guest tools" which will download the vmware tools onto your host computer (not the VM). 

Then what we do is we have VMware present the downloaded file to the VM. it does this by making the file look like it's a CD in a virtual CD drive. We are not using your computer's CD drive. 

I'm not entirely certain where the problem is, I suspect that you're not understanding the process.

---

### Post by sniper8752 on 2014-02-04
> **bashiergui said:**
> Then what we do is we have VMware present the downloaded file to the VM. it does this by making the file look like it's a CD in a virtual CD drive. We are not using your computer's CD drive.

How do I do this?

---

### Post by bashiergui on 2014-02-04
To mount the CD image and extract the contents:
Power on the virtual machine.
Log into the virtual machine using an account with administrator or root privileges.
Go to Virtual Machine > Install VMware Tools (or VM > Install VMware Tools).


Note: If you are running the light version of Fusion, a version of Workstation without VMware Tools, or VMware Player, you are prompted to download VMware Tools before they can be installed. Click Download Now to begin the download.


Open the VMware Tools CD mounted on the Ubuntu desktop.
Right-click the file name that is similar to VMwareTools.x.x.x-xxxx.tar.gz, click Extract to, and select the Ubuntu Desktop to save the extracted contents.


The vmware-tools-distrib folder is extracted to the Ubuntu Desktop.

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=1022525](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=1022525)

---

