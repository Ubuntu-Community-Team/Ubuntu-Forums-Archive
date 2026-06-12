---
title: "SFTP chroot assistance needed"
date: 2012-08-08
forum: Server Platforms
---

### Post by darkapec on 2012-08-08
I will try to keep this short but I tend to be over specific...

I have a series of peripherals (Raspberry Pi, apple tv, etc) that all access my server to stream music and movies. Some via internet others intranet (internet uses SFTP, intranet uses SAMBA), I also have a few friends that login via the web. 

I would like to be able to create a user with the name "guest" that will allow simultaneous logins (up to 5 at a time). This user does not need SSH access, however it would be nice. The user will need to be locked to a directory "/Backup" and not be allowed to edit or delete ANYTHING. 

I have achieved the above by adding the code below to the /etc/ssh/sshd_config file 
```
Subsystem sftp internal-sftp

Match User guest
    ChrootDirectory /Backup/Movies
    AllowTCPForwarding no
    X11Forwarding no
    ForceCommand internal-sftp
```

The biggest issues with the above is the user "guest" is secured the way I want however I had to change permissions to every folder in the "/Backup/Movies" directory to "root:ftp" so the chroot would work. Doing so made it impossible for my other admin users to edit / add / or delete any files. I was also unable to SSH into the server with the "guest" account.

So quick summary, I would like the guest account locked to the directory, but need the ability to still edit files with other users. I will also need all other forms of access to still work eg. apache, samba, ssh, sftp with permissions of 755

I have looked and looked on the internet for a solution and the only instances I can find are for accounts that people want jailed to there home directory. So I am not quite sure where to go from here. I have always had great luck with the ubuntu community so hopefully I can get a quick easy answer. 

On a side note I do not want to go to FTP if at all possible. My infrastructure is already all setup for SFTP and I don't like the idea of personal media files being unencrypted as it passes through the internet. 

Thanks
Jake

---

### Post by darkapec on 2012-08-08
Well this is the best thing I could come up with... and it was a pain in the a$$

I had to go to the root directory "/" and set ACL's for each folder. For most of the folders I had to add the group "ftp-users" (the group my guest login is in) and deny it read / write / execute access. On a few folders (bin, etc, lib, lib64, usr) I had to add group "ftp-users" and allow execution but deny write and read. This allowed my guest user to still SSH and SFTP into the server but not able to read any files other then the contents of "/Backup/Movies"

If anyone knows of a different way to allow a user to have SFTP / SSH access to a directory that is shared and edited by others please let me know.

---

### Post by dbrooke on 2012-08-08
As far as I understand it, the

ChrootDirectory path directive doesn't allow write access by any other user:group but root (and needs to be owned by root). 

I guess the idea is to create a directory inside whatever chrootdirectory path you set which will allow write access from there.

Donovan

---

### Post by kevinthecomputerguy on 2012-08-08
dbrooke is correct 
This might help
[http://woodel.com/domore/sftp/woodel_sftp.pdf](http://woodel.com/domore/sftp/woodel_sftp.pdf)

---

