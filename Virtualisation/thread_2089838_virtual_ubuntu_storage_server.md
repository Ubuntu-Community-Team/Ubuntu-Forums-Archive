---
title: "virtual ubuntu storage server"
date: 2012-11-30
forum: Virtualisation
---

### Post by keith1684 on 2012-11-30
I would like to use ubuntu server 12.04 to create a file server for my media and pc backups. In the future I plan to build a new machine using the amd A series or intel atom for low power usage.

Until I can afford to build the new machine I was thinking of running the ubuntu server as a virtual machine. The vm will be running in vmware workstation on a windows host.

My question is will I have any trouble using the VM to create  a large storage pool using ext4 file system (4TB - 2x2tb drives) and creating samba shares?

Is the windows host going to see the drives or can I make them only accessible to the ubuntu vm?

Once I am able to build a new machine would I be able to move the drives over without losing data?

---

### Post by 2F4U on 2012-11-30
> My question is will I have any trouble using the VM to create  a large  storage pool using ext4 file system (4TB - 2x2tb drives) and creating  samba shares?

I don't think that the virtual machine will be able to create the storage pool, you probably would have to do that within your host operating system.

> Is the windows host going to see the drives or can I make them only accessible to the ubuntu vm?

No. The host operating system will see the VM as one large file. Depending on what VM software you will be using, there probably is an option to share data between host and guest through a shared folder.

> Once I am able to build a new machine would I be able to move the drives over without losing data?

You would need to connect the guest OS to the new server in some way. In general, your data will be inside the VM and you can access it in the usual ways from the host.

---

### Post by keith1684 on 2012-11-30
Okay what I don't understand is if the vm software allows you to mount a physical disk instead of creating a virtual disk shouldn't it operate as if its a real box?

---

### Post by drdos2006 on 2012-11-30
> 
My question is will I have any trouble using the VM to create a large storage pool using ext4 file system (4TB - 2x2tb drives) and creating samba shares?

Is the windows host going to see the drives or can I make them only accessible to the ubuntu vm?


Your Windows OS will not be able to see the Ubuntu shares. Windows uses NTFS file system but Ubuntu can see the NTFS files.

If you had Ubuntu as your Main OS then the server VM could see the shares and you would not have to allocate such a large storage pool for the VM.

 
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.590_all.deb

Add extra libraries with :
sudo apt-get -f install

```


regards

---

