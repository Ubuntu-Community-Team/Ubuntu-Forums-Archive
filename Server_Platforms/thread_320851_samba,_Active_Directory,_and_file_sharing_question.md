---
title: "samba, Active Directory, and file sharing question"
date: 2006-12-18
forum: Server Platforms
---

### Post by MystaMax on 2006-12-18
Hello, I need help configuring samba. 

I've got a dapper server that i have apache and mysql running. I need to back up /var/www and the mysql db. We currently have BackupExec running on a windows 2k3 server, and have a netapp mounted on the server. I want to smbmount the backup folder on the dapper server so the win2k3 server can R/W with the dapper server. To my understanding I need samba to do this.

I've installed samba after reading [this guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server")[ubuntuguide.org], but ran into one issue. My windows server is apart of a Active Directory domain. The ubuntuguide.org article only talks about working with windows workgroups.
[B]
Do I have to/want to make the dapper server apart of the domain for me to access it via windows?[/B] Does [this ubuntuforums.org guide]("http://ubuntuforums.org/showthread.php?t=202605") accomplish what I'm looking for? I would test it, but I don't have the resources. 

I also found this help.ubuntu.com [wiki article]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"). They all seem similar, but I'm not sure which one fits my situation.

I appreciate all comments, thanks.

---

### Post by Iowan on 2006-12-18
[https://wiki.ubuntu.com/DomainAuthenticationUtility]("https://wiki.ubuntu.com/DomainAuthenticationUtility")
Here's another to  look at.  I didn't check it in depth, but it appears to have a section on logging into an existing domain.

---

### Post by MystaMax on 2006-12-18
Thanks for the reply Iowan.

It looks like a team of folks began building a utility, but it isn't complete. Also, the article referenced inside the wiki page is in I believe dutch, which google couldn't translate for me. That may not be suitable for me at this time. At first glance, it looked like a W-I-P, and not stable?

I wondering if I want my windows 2k3 server (apart of domain and not workgroup) to read/write with my dapper web server, do I have to join the dapper server to the domain, or is there another way? 

The ubuntuguide.org article only speaks of joining a windows workgroup and not a domain.

---

### Post by Iowan on 2006-12-18
I've seen an article/post/HowTo *somewhere* that describes how to make a Samba server join a domain (even it's own  - as a PDC).

---

### Post by pppetter on 2006-12-18
I have for some time though about making a script for automatically backing up my own webserver via FTP. And you just gave me a good reason to actually get me started. Do you have a FTP-server on your windows machine or could you easily fix one? If the answer is yes, you'll have a fix for your problem really soon ;)

---

### Post by MystaMax on 2006-12-18
Thanks for chiming in pppetter.

I discussed this with my windows admins and unix admins, and they insisted that a follow suit on how our *nix boxes are backed up. Most of them talk to our main file server which is attached to a network appliance. I only wish it was that easy.

---

### Post by pppetter on 2006-12-19
Okey. But if there are other 'nix systems getting backed up the same way you want your system to be backed up. Why don't you check out their configurations then? :)

---

### Post by MystaMax on 2006-12-19
I honestly think, I've read so much samba references that I may of just completely confused myself.

I spoke with my unix admin, and he said he doesn't mount the linux share in windows, but vice versa. He mounts the windows share in linux. So the linux box is just a client. I completely confused the two.

So now I think all I need to do is setup the folder I want to share out on my windows server (with the correct permissions), setup a folder on the dapper server which will contain the windows mounted share(**where's the best/most logical place for this**), and figure out **how to automount this windows share without including my password within the fstab file.** Right now I know to type:

```
smbmount //WINDOWS2k3SERVER/WindowsShare /UnixMountPoint -o username=DOMAINusername,workgroup=DOMAIN
```

I should then be prompted for the password for the DOMAINusername. I couldn't run this as the current user, or sudo it. The wikipedia article states you need to be [root]("https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c") to do so.


UPDATE:

the [smbmount wikipedia article]("http://en.wikipedia.org/wiki/Smbmount") was actually quite helpful

this [ubuntu wiki article]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#head-9a9417197b46f020de9ba46f4842e4c18b11f3d0") helped me automount windows shares without including a password.

making progress!

---

