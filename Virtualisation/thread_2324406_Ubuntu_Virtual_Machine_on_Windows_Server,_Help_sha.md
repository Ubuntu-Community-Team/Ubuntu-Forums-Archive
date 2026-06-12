---
title: "Ubuntu Virtual Machine on Windows Server, Help sharing files."
date: 2016-05-13
forum: Virtualisation
---

### Post by Chase_Juda on 2016-05-13
I followed this guide to permanently mount my Windows Host Machine as a Network Drive for my Ubuntu VM to transfer files to.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Now the drive was setup to mount under Root.
And my regular user is unable to migrate files freely between both systems. 
I've tried using chmod to transfer ownership back to my regular user but to no avail.
Anything I can try next?

[ATTACH=CONFIG]269023[/ATTACH]

---

### Post by QDR06VV9 on 2016-05-13
Just to be sure did you make sure that you have installed [I]Guest Additions
And then run:[/I]
```
*sudo VBoxLinuxAdditions.run*
```
and then reboot your VirtualBox.
And I have moved your thread to Virtualisation for better support.
Edit: This is how I setup my shared folders with either Windows as a host or Ubuntu as a Host.
[http://www.htpcbeginner.com/setup-virtualbox-shared-folders-linux-windows/](http://www.htpcbeginner.com/setup-virtualbox-shared-folders-linux-windows/)

---

### Post by Chase_Juda on 2016-05-13
I guess I should clarify that a little bit.

So I'm using Hyper-V for my Virtualization.
I have an existing share folder on the host machine (windows server.)
I'm just wanting to perma-mount this share folder in Ubuntu so that I can freely migrate files between the two systems.
Unfortunately, Hyper-V lacks that share feature that VirtualBox has.

Any other suggestions?

---

### Post by SeijiSensei on 2016-05-13
Try sharing the file on the Windows side and mounting it in the Linux VM with smbfs.  You'll probably want to use a reference like //10.0.8.1/myshare if 10.0.8.1 is the IP address of the host's adapter that points to the VM.

---

### Post by jmgangemi on 2016-05-15
Another way you can share files with your Ubuntu Virtual Machine is to use SFTP (FTP over SSH).

Install the Ubuntu package SSH on your virtual machine and use a utility like Filezilla to login via SFTP to transfer files between the host and the Virtual Machine.

---

### Post by jmgangemi on 2016-05-15
> **Chase_Juda said:**
> I followed this guide to permanently mount my Windows Host Machine as a Network Drive for my Ubuntu VM to transfer files to.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Now the drive was setup to mount under Root.
And my regular user is unable to migrate files freely between both systems. 
I've tried using chmod to transfer ownership back to my regular user but to no avail.
Anything I can try next?

[ATTACH=CONFIG]269023[/ATTACH]


Use chown not chmod to change the ownership of the folder back to your regular user instead of root.

---

### Post by MAFoElffen on 2016-05-17
Besides the permssions ...
+1 with SeijiSensei

Why, because the guide you used was very dated. Notice that it mentioned Ubuntu 9.04? CIFS went out of style / favor around 2008, and was almost universally replaced by using SMB shares via SAMBA and Samba Client. Current Ubuntu Desktop (itself) does it's own SMB shares , and has scripts setup to instyall, configure and use Samba Client. (by default) That, in itself, should be enough of a recommendation. Last time I used cifs-utils was 2007, while supporting Sun's OpenSolaris and Solaris 9... and Windows Vista.

---

