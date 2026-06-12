---
title: "Mount remote directory over sshfs on Windows host through ubuntu guest?"
date: 2017-02-15
forum: Virtualisation
---

### Post by peter1897 on 2017-02-15
I am trying to achieve something that i am not sure if it is possible. I  have ubuntu server as virtualbox guest machine and Windows 7 host. The  shared folder between the host and guest machine is mounted in /media/sf_Shared on the ubuntu guest, the folder location on the host machine is e:\Shared. Inside the sf_Shared folder i created new folder 'mnt' and mounted the remote folder over sshfs: ```
sshfs user@xxx.xxx.xxx.xxx:/remote_folder /media/sf_Shared/mnt/
```  The remote folder was mounted successfully but if i open the folder  from the host - Windows 7, the folder is empty. Is it possible to mount  remote folder over sshfs using mount point inside the shared folder and  the mounted folder to be accessible from the host?

---

### Post by termibuntu on 2017-02-15
Hi. Can i just say, it could be the filesystem you used in ubuntu server. As always, windows cannot read linux filesystems. If you can tell us more about which filesystem you used, that would help. Also what i dont get is that windows would always say 'the drive [drive letter] needs formating. would you like to format the drive? Hope this helps.

---

### Post by peter1897 on 2017-02-15
The file system is vboxsf:
```
max@ubuntu:/media/sf_Shared$ mount | grep Shared
Shared on /media/sf_Shared type vboxsf (gid=116,rw)
```

---

### Post by termibuntu on 2017-02-15
thats a virtual box filesystem. windows cant read those filesystems

---

### Post by SeijiSensei on 2017-02-15
If this is a folder on the Win7 host, why can't you just open it natively in Windows?  Or are you trying to mount the folder on a different Windows machine?  If the latter, just export the share natively in Windows.

---

### Post by kpatz on 2017-02-15
I'm not quite sure what you're asking, but here goes...

We'll start with the Virtualbox shared folder.  It's e:\Shared on the Windows host, and mounted to /media/sf_Shared in the Ubuntu guest.  Which means any files you create in e:\shared on Windows can be seen in /media/sf_Shared in Ubuntu and vice versa.

But then, you created a mnt folder in /media/sf_Shared and mounted it to a remote server using sshfs, right?  When you do that, you'll see the mnt directory in Windows, but no files actually get placed there, since on the Ubuntu side what you're accessing under mnt is the file system on the remote server.

So, in short, you have 2 mounts:

/media/sf_Shared - mounted to E:\Shared
/media/sf_Shared/mnt - mounted to remote server via sshfs

So, you can create files and directories under /media/sf_Shared and they'll get put into E:\Shared, since that mount points there.  But when you put files into /media/sf_Shared/mnt, they don't go to E:\Shared, they go to the sshfs mount, and the files will go to the remote server.  As a result, you won't see those files from the Windows host, unless you run a sshfs client there and mount the remote location in Windows.

Clear as mud? :)

---

### Post by termibuntu on 2017-02-15
Has this been been fixed?

---

### Post by peter1897 on 2017-02-15
I tried all possible variants i can think of and i can say that what i am trying to achieve doesn't seem possible.

---

### Post by heiko_s on 2017-02-15
I'm not very familiar with VB, but IIRC you can share quite easily between host and guest by creating a shared folder on the host. But since you asked about sharing a folder on the guest, have you tried running a **Samba server** on the Ubuntu VM? Once the server is running you can share whatever folders you have on the Ubuntu VM with your Windows host. You might need to open the firewall for Samba traffic, though.

I use it vice versa - running a Windows VM on Linux (but using KVM).

---

### Post by deadflowr on 2017-02-15
Is there a 3rd machine being connected to?
> **user@xxx.xxx.xxx.xxx:/remote_folder** /media/sf_Shared/mnt/
Somehow, if I understand this, you are mounting a remote share, from an entirely different system(remotely) inside the vm, and are now trying to mount that share in the vm share folder?
Is that right?

---

### Post by peter1897 on 2017-02-16
> **heiko_s said:**
> I'm not very familiar with VB, but IIRC you can share quite easily between host and guest by creating a shared folder on the host. But since you asked about sharing a folder on the guest, have you tried running a **Samba server** on the Ubuntu VM? Once the server is running you can share whatever folders you have on the Ubuntu VM with your Windows host. You might need to open the firewall for Samba traffic, though.

I use it vice versa - running a Windows VM on Linux (but using KVM).

My goal is to share mounted remote folder on the guest machine with the host machine.

---

### Post by peter1897 on 2017-02-16
> **deadflowr said:**
> 
Somehow, if I understand this, you are mounting a remote share, from an entirely different system(remotely) inside the vm, and are now trying to mount that share in the vm share folder?
Is that right?

Yes, that is correct.

---

### Post by heiko_s on 2017-02-16
So have you looked at Samba server as an option?

---

### Post by peter1897 on 2017-02-16
> **heiko_s said:**
> So have you looked at Samba server as an option?

Yes, but it doesn't work. The mounted remote folder on the guest is not visible on the host. I did somtehing like this: i mounted the remote folder on this mount point on the guest machine - /home/mnt2/mnt. Then i set the folder /home/mnt2 as shared samba folder and mount it from the host but the 'mnt' folder is not visible from Windows.

---

### Post by SeijiSensei on 2017-02-16
I know that with NFS you cannot re-export a mounted share for security reasons. (It would be possible to grant users rights on the re-exported share that they do not have on the originating server.)  I don't know whether any of this applies to SSHFS+CIFS, but your experience suggests it might.

---

### Post by heiko_s on 2017-02-16
You need to make sure that the Ubuntu firewall doesn't block Samba traffic. Also, you need to look at the network settings of Virtualbox to see how the VM is connected to the network. If it's a bridged network, it should be fine. Unfortunately I can't help with Windows and networking - it's too complicated for my small brain. The other way round (Windows VM on Ubuntu) seems much simpler.

---

### Post by deadflowr on 2017-02-17
I'd go in an entirely different direction and install an sftp client on windows.
swish works well, as it can also generate keys.
You would need to download the installer from here:
[http://www.swish-sftp.org/]("http://www.swish-sftp.org/")
and follow the guide to generate your keys:
[http://www.swish-sftp.org/wiki/PublicKeyAuthentication]("http://www.swish-sftp.org/wiki/PublicKeyAuthentication")

Then connect the the ssh server with that and then either share the folder between the host and guest or mount the ssh server separately; one connection from windows host and one from the Ubuntu vm.

But that's what I would do.

---

### Post by peter1897 on 2017-02-17
> **deadflowr said:**
> I'd go in an entirely different direction and install an sftp client on windows.
swish works well, as it can also generate keys.
You would need to download the installer from here:
[http://www.swish-sftp.org/](http://www.swish-sftp.org/)
and follow the guide to generate your keys:
[http://www.swish-sftp.org/wiki/PublicKeyAuthentication](http://www.swish-sftp.org/wiki/PublicKeyAuthentication)

Then connect the the ssh server with that and then either share the folder between the host and guest or mount the ssh server separately; one connection from windows host and one from the Ubuntu vm.

But that's what I would do.

I installed swish-sftp and connected to the mounted remote folder on the guest machine, but how to map it? From their faq page it states that it is not possible - [http://www.swish-sftp.org/wiki/FAQ](http://www.swish-sftp.org/wiki/FAQ)

I also can connected to the mounted remote folder on the guest machine using WinSCP but i don't think WinSCP has the ability to mount folders.

---

