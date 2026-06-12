---
title: "Fileserver Questions"
date: 2007-06-27
forum: Server Platforms
---

### Post by borahshadow on 2007-06-27
ok I posted a while back with questions on how to set up a file server that I was building.  I actually never got it working exactly how I would like but I limped by because I had other things to do.  That thread seems to have died and I am rebuilding this fileserver so I decided that I would post again and try to get it working right.
here is my smb.conf that I was using
> [global]
	netbios name = SERVER-HOME
	load printers = yes
	name resolve order = hosts wins bcast
	server string = 
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	workgroup = WORKGROUP
	syslog only = yes
	username map = /etc/samba/smbusers
	null passwords = true
	printcap name = CUPS
	syslog = 1
	security = share
	passdb backend = tdbsam
	wins support = no
        unix extensions = no
    ; General server settings






[shared]
	guest account = samba
	writeable = yes
	path = /shared
	force group = samba
	force user = samba
	create mask = 0777
	public = yes
	directory mask = 0777
[picturemate]
	printer = picturemate
	printable = yes



What I need is one share(folder) that anybody can have full access too read/write.  Tthis server should be able to be run headless and will not be used as a workstation like I was trying to do before
the above confg seems to work fine from windows (have not done extensive testing but no one complained about it not working right) but when mounted from linux with this command> sudo mount -t cifs //192.168.0.50/shared /media/shared -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 I get strange errors
This is what I posted at the end of my other thread but noone anwsered and it quickly got drowned by other posts so I will just copy part of it here
**Scenario 1: **Try to copy a folder over through konqueror say ~/pictures to /media/shared/pictures
konqueror will bring up a box that says can't change permissions on file XYZ and if I click ok it will bring it up for the next file too, but if I leave it up it will suppress all the other files saying that. The files copy and if I go look on the server they seem to have the correct permissions so why the seemingly pointless error?

**Scenario 2:** A program trying to create folders and files on the mounted share (ie. kaudiocreator)
ok I was ripping a bunch of cd's to the server and had this problem.  kaudiocreator was configured to make a folder for the artist and then a folder for the album and then put the ripped tracks in there.
well the first track would rip and then the encoder would throw up an error that it could not create the folder but the artist folder would be created. Then the second track would throw up an error about the album folder then all tracks after that would work fine because even though it thought it couldn't create the folder it did.
I would either manually create the folders or just do the first 2 tracks over again to work around this one
I think it could be related to some kind of delay from the time the program tries to make the folder to the time it is created
[B]
Scenario 3:[/B]  rsync
ok I was actually using grsync which is just a gui for rsync so that should not effect this
when copying things over to the server I get output similar to this
Quote:
rsync: failed to set times on "/media/shared/pictures/.": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/Home and Family/Family/Cody": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/.": Operation not permitted (1)
rsync: failed to set times on "/media/shared/pictures/Home and Family/Family/Cody": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
I think the times is similar to the permissions thing from konqueror

**Scenario 4:** Firefox
I have Firefox set to ask me where to save things if I select someplace on the server it will give me an error about permission denied and it creates a file.extension.part and then if I try again it works but the .part file is still there.  Now here is the really weird thing the file shows up with a padlock on it and I can't access the file I just downloaded but if I go over to the server it has all the correct permissions and I can do things like extract archives
and then after a reboot of the remote machine I can see things correctly (probably just after an unmount and remount but I have not tried that) just a refresh does not work.

Please help because these are getting really annoying and some (like the Firefox one) are really inconvenient.
Thanks for your help

---

### Post by DugieHowsa on 2007-06-28
try using the noperm flag if you want to give everyone full access to the share.

Code:
sudo mount -t cifs //192.168.0.50/shared /media/shared -o noperm,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77

---

### Post by borahshadow on 2007-06-28
so just use the config file that I have?
it works on windows (i think)
and the noperm will fix it on linux right?
thnaks i'll try when I get my server installed raid is giving me trouble :(

---

### Post by borahshadow on 2007-06-29
I think that did the trick thanks I'll post if I run into any more trouble

---

