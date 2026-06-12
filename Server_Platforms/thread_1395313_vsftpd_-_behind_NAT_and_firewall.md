---
title: "vsftpd - behind NAT and firewall"
date: 2010-01-31
forum: Server Platforms
---

### Post by Zidaps on 2010-01-31
Hi, 

I've been trying to get this going for the past month or so. I've searched the forums, and tried irc chat rooms, still can't figure out what i'm doing wrong. 

I'm using firestarter, and connect through a linksys WRT310N router.
standard ftp ports 20-21 have been forwarded on the router. Ports 20-21 are also opened by ftp policy on firestarter.

**
-I would like to be able to share my data with peers over the internet securely.
-I would like each user to have his/her own user name and password.
-I would like to share files that are located on an internal disk, but not the disk ubuntu is installed on. ex. /media/my_other_disk/Public_Folder/user
**

Here is what my vsftpd.conf file looks like:

listen=YES

local_enable=YES
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

write_enable=YES

local_umask=022

anonymous_enable=NO
anon_root=/home/ftp/
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO

use_localtime=YES

xferlog_enable=YES
dual_log_enable=YES

connect_from_port_20=YES

ascii_upload_enable=YES
ascii_download_enable=YES

ftpd_banner=Welcome to The Vault FTP service.

chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

_________________________________END_______________________________________

When I try to log in with my ip [ftp://###.###.###.###](ftp://###.###.###.###)

I keep getting the following Alert:   530 Permission denied.
Any ideas what I might be doing wrong? How can I get the desired setup as outlined above?? (the section between the 2 asterisks **)

---

### Post by Lars Noodén on 2010-02-01
> **Zidaps said:**
> -I would like to be able to share my data with peers over the internet securely.


Remove vsftp and any other ftp servers.  With a lot of work, you *might* get ftps working, but then it's still complicated to maintain and still stuck with FTP tunneled over SSL.  Or you might spend a month with no positive results.  

Instead, install openssh-server, if it is not there already.  It has SFTP (not FTPS) support working out of the box.  You can then connect using any SFTP client, including Filezilla, Nautilus, Konqueror, Dolphin, Fugu or Cyberduck.  The URL would start with **sftp://** instead of ftp://

If you want access from the outside, you'll need to configure your router to forward port 22 from the outside to your machine with openssh-server.  The router/modem instructions will have info about how to do that.  

> **Zidaps said:**
> 
-I would like each user to have his/her own user name and password.


Create user accounts for these people.  You might make a special group and add them to that, too, such as 'datapeers' or something to identify them.  They can then connect with sftp.  

If you want to get fancy, add something like this to the tail end of the sshd configuration file, /etc/sshd_config:
```

Subsystem sftp internal-sftp


Match Group **datapeers**
     ForceCommand internal-sftp
     AllowTcpForwarding no

```

That will help prevent shell access for any user in the group **datapeers** while allowing sftp access.

> **Zidaps said:**
> 
-I would like to share files that are located on an internal disk, but not the disk ubuntu is installed on. ex. /media/my_other_disk/Public_Folder/user
...


It does not mater which disk the file are on, just the part of the directory hierarchy.  chroot can limit access to a particular part of the system.   

If you want to get fancy, add something like this to the tail end of the sshd configuration file, /etc/sshd_config:
```

Subsystem sftp internal-sftp


Match Group **datapeers**
     ChrootDirectory */media/my_other_disk*
     ForceCommand internal-sftp
     AllowTcpForwarding no

```

In addition to sftp-only, that will limit sftp access to only what is in */media/my_other_disk* and its subfolders.

---

### Post by Zidaps on 2010-02-04
Thanks for the help. I am able to successfully log into the sftp server using ssh. However, the user logs into their local username  home directory. i.e. /home/user

**
Upon signing in, I would like to get them automatically to /media/other_disk/Files
**

I know this is the purpose of the "ChrootDirectory" portion of the code you gave me earlier. However, when I attempt to use ChrootDirectory, that's when I receive an error. If I don't use it, I am able to log in as the user fine, but it logs me into the wrong place... it logs me into the home directory instead of: /media/other_disk/Files

Here's the error I receive from Filezilla when I use the "ChrootDirectory" code in the ssdh_config file:

Status:    Connecting to ##.###.###.###...
Response:    fzSftp started
Command:    open "user@##.###.###.###" 22
Command:    Trust new Hostkey: Once
Command:    Pass: *******
Error:    Could not connect to server 

I've configured the sshd_config file as you specified in your response. Thanks again.

---

### Post by Lars Noodén on 2010-02-04
> **Zidaps said:**
> Thanks for the help. I am able to successfully log into the sftp server using ssh. However, the user logs into their local username  home directory. i.e. /home/user


Yes, ssh gives you a shell.  If you follow the instructions above, it should not be possible for members of the group to login except through sftp (not ssh)

> **Zidaps said:**
> 
I've configured the sshd_config file as you specified in your response. 

It should go at the end of the configuration file /etc/ssh/sshd_config.  

After that there are three things to check: The machine running sshd should have a group **datapeers**, or whatever you decided to call it.  The users who are to be restricted must be members of that group.  That group must be the one named in the Match directive in sshd_config.

You may want to create a test account and add it to the group when testing this.

---

### Post by Zidaps on 2010-02-04
Hi, 

Thanks again for all the help, but i'm still not able to get the ChrootDirectory to work. Maybe you can pin point what i'm doing wrong, here is what I have in the config file.

****** Toward the very end...******

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

UsePAM yes

Subsystem sftp internal-sftp

Match Group datapeers
     ForceCommand internal-sftp
     ChrootDirectory /media/Media/Public
     AllowTcpForwarding no

******       -     END       -      *******

Any ideas? Keep in mind that If I remove "ChrootDirectory /media/Media/Public"
then users in the group "datapeers" can log in with their user name and password no problem. But it takes them directly to /home/user  in sftp, and it allows them to browse my entire machine. I don't want that.

Thanks again.

---

### Post by Lars Noodén on 2010-02-05
Sorry, I may have missed the obvious.  What version of OpenSSH are you running?  ChrootDirectory was added to Ubuntu as of only Intrepid Ibex (OpenSSH 5.1)

---

### Post by Zidaps on 2010-02-05
Hi,

I'm running Ubuntu 9.10 and the ssh server is version 1:5.1p1-6ubuntu2. I'm still not able to get ChrootDirectory to work. Could it have something to do with disk permissions?? As since I updated to 9.10 about a month ago my samba shares got messed up and I can't share folders, getting the error below when I try to share my folders:

**
```
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
```
**

But smbd is running and that can be proven when i do: "sudo /etc/init.d/samba status"
It returns:
         * nmbd is running
         * smbd is running

But thats beside the main point in the thread. Still having errors logging in once "ChrootDirectory /media/Media/Public" is enabled in the "/etc/ssh/ssdh_config" file. The error i'm getting from Filezilla is:

**
```
Status:    Connecting to ##.###.###.###...
Response:    fzSftp started
Command:    open "user@##.###.###.###" 22
Command:    Trust new Hostkey: Once
Command:    Pass: *******
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Connecting to ##.###.###.###...
Response:    fzSftp started
Command:    open "user@##.###.###.###" 22
Command:    Trust new Hostkey: Once
Command:    Pass: *******
Error:    Could not connect to server
```
**

Thanks again.

---

