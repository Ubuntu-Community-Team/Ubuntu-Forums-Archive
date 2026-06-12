---
title: "Setting up vsftpd on Ubuntu Server"
date: 2013-03-03
forum: Server Platforms
---

### Post by ranger12 on 2013-03-03
Okay I am going to post how I setup vsftpd on my server. I don't know if this could be of any use to anyone but hopefully it will.
What I wanted was to setup a ftp server on my home lan so that users could log into the ftp service but only download files but when I log in I could both upload and download. Your needs may vary so this may not be exactly what you are looking for.

_**Server:**_
Ubuntu Server 12.04.2 LTS running on a Dell 8100 PC. It is running straight on the box - NO VIRTUAL STUFF!!!
vsftpd 2.3.5-1ubuntu2
Linux Kernel 3.5.0.25.39-precise

_**Desktop:**_
Ubuntu Desktop 12.04.2 LTS running on a Dell 4800 PC. It is running straight on the the box - NO VIRTUAL STUFF!!
Linux kernel 3.5.0.25-39-precise
xserver-xorg-lts-quantal


I am going to skip the install step - see the server guide for that. It's pretty simple to install vsftpd anyways. I had no problem installing it last summer and it has ran fine ever since.

_**Directories I setup:**_
FTP directory is /srv/ftp
I created 2 directories in /srv/ftp: files and roms. Your needs will be different of course.
I made both directories world-writeable.
sudo chmod a+rwx /srv/ftp/files
sudo chmod a+rwx /srv/ftp/roms.

I created a **directory** in /etc called vsftpd_user_conf. Do you have to name it this? No. I just simply took it from the man page for vsftpd.conf. Just make sure it matches the name given for user_config_dir in your vsftpd.conf.

[U][B]VSFTPD.CONF settings:
[/B][/U]I have stripped out all the comments for brevity's sake:

listen=YES
anonymous=NO
local_enable=YES
local_root=/srv/ftp
user_config_dir=/etc/vsftpd_user_conf
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
hide_ids=YES
ftpd_banner=Welcome to the El Rancho Ritchie FTP service. ' Don't ask, it's a long story. :)
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd

These are the only settings I have in my /etc/vsftpd.conf. This is not a public ftp service - it is private - so I do not have ftp over ssl enabled, if you are you doing this than I would highly recommend you enable ftp over ssl. 

_**Custom Configuration file:**_
**In my /etc/vsftpd_user_conf directory** I created a custom vsftpd configuration file with a filename that **matches exactly** my login username. For example, if your user name is chris - you would simply name this custom file* - *chris. My custom config file only contains 1 directive:
write_enable=YES

So when I login in it to the ftp service, it loads my custom config file, since it matches my username and overrides the write_enable setting - which I did not set to yes in vsftpd.conf since I do not one anyone else to have write access. This custom config allows me to have write operations but no one else. So now I can create, delete folders and upload stuff into those folders I created. You cannot upload files directory into the local root under chroot because of the security changes made but that is okay. I have no problem with creating folders and uploading into those folders.

I have tested this by logging in as myself and had no problem uploading files into the folders I created under /srv/ftp. I then logged in under another user and attempted to upload and the operation failed as I expected it to. I used Nautilus for this. I also briefly installed FileZilla on my desktop and tried it. I did no configuration changes to FileZilla and it worked fine.

One more thing when I mentioned earlier about being able to create and delete folders; that is just inside existing folders. You cannot do this at the local root under chroot after logging in either. If you need more folders at the ftp root than you will have to do this at the server or ssh over to the server - not a big deal for me.

I hope this helps someone.

---

### Post by aerokid240 on 2013-03-06
Nice guide. Thanks for sharing.

---

