---
title: "file share Problems"
date: 2005-12-26
forum: Server Platforms
---

### Post by ewtesterman@cox.net on 2005-12-26
Okay I have setup Ubunutu server w/ no desktop at all. I have apache2 up with a few mods. I have openssh up and working. The only part of the equation that is missing is the ability to put files onto my server so that they can be served. I have tried Samba, and Proftp. Unfortunately it seems that the howto's are a little dated because all of the example .conf's I see do not look like mine. Both Samba and FTP are up and running. When I try and access my server through samba from and XP box I get a message saying that I do not haver permission to acess this network. I would think that if it were a password thing it would ask for one first right. Any very frustrated here. If anyone could help it would be great. I do not want to have to put windows back onto this machine.

---

### Post by steve_250 on 2005-12-30
I just had the same problem this morning.
This is what I did to solve it, your situation may be different....

smb.conf:
Make sure you have the same workgroup name there as your delivery machine is on.
Also, in smb.conf, make sure you can write to the area you want to put stuff in.
There may be a security issue with the way I have this set up, if so someone PLEASE shout out so I can fix it!

[/var]
path = /var
available = yes
browseable = yes
public = yes
writable = yes

[www]
path = /var/www
available = yes
browseable = yes
public = yes
writable = yes

[apache]
path = /var/www
available = yes
browseable = yes
public = yes
writable = yes

[Files]
path = /var/www/files
available = yes
browseable = yes
public = yes
writable = yes

With the OS's file browser, I went into each area and changed permissions and changed the owner to www-data and allowed r/w/e to all.
I know I have some fixing to do with this setup.

My setup is NOT on the net (yet) and has a pw protect on it.  My eventual intention is to  be able to grab files from it while I am at work.  I would greatly appreciate someone pointing out the (obvious to some) problems with this setup.
But, as I stated, this is how I was able to transfer files from another machine on my home net.

---

### Post by Bender10 on 2006-01-02
Hi, I am in the same boat. I have done a complete install of Ubuntu 5.10 and Samba.  Which I would like to use as a server for my 5 w2k/Xp machines. I can SEE from Ubuntu to all my Win machines, and visa versa. I can also use Ubuntu to copy from the Win machines. 

But, when I try to connect to Ubuntu from a Win machine I get the '\\Ubuntu is not accessible' (w2k), or '\\Ubuntu is not accessible You might not have permission to use the network resource Contact your administrator.....' (on XP).

I have been editing the various config files to no avail. I can still connect to the internet with Ubuntu (at this very moment). I have not installed any extra packages yet. But I like Ubuntu so far execpt for the minor sharing problem...

---

### Post by Bender10 on 2006-01-03
Ok,
I fixed a few things with some help from [www.samba.org](www.samba.org). There are so many sources of help, I've going in circles. Anyway, I am past the error stage when I select the server from Windows. Now I get a login screen with the user grayed-out (unbuntu/Guest) and it is waiting for a password, ????

Here is my smb file....

[global]

   workgroup = Workgroup
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   security = share

   socket options = TCP_NODELAY

 [/home/Share]
    path = /home/share
    available = yes
    browseable = yes
    public = yes
    writable = yes

[allusers]
    comment = All Users
    path = /home/shares/allusers
    valid users = @users
    force group = users 
    create mask = 0660
    directory mask = 0771
    writable = yes

I feel like i should dump the install, and start from scratch...applying what i have learned so far. 

Bruce

---

### Post by duffydack on 2006-01-12
i get same error message as you bender.
Im logged into it as "admin" and ive setup file sharing with samba and added admin to the users list in control centre (but it doesnt save it).
When i goto network places in windows i get prompted for login (as i wanted) and then get that msg after puttin in the username/password of the user ive setup and using on the linux machine.  I have to add another unix user (administrator as thats the windows account im using) and then smbpasswd -a to add it to samba for it to work properly....
anyone know why i cant use "admin" thats setup and logged into linux already? too many logins at same time?

---

### Post by i_am_socket on 2006-01-12
Easy fix for most Samba problems: use the latest debian version from Samba.org (I just posted this yesterday for someone else I think) instead of the Ubuntu version on synaptic.  This made life easier sharing for windows and macs.

Any dev guys reading this: you may want to update the package there especially since the debian binary is known to work already...

---

### Post by frodon on 2006-01-12
You can ask this package to be backported if you wish, here is the place to do it : [http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)
Informations on what is backport : [http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

---

### Post by i_am_socket on 2006-01-12
Request made.

---

### Post by LordHunter317 on 2006-01-12
[QUOTE=steve_250]There may be a security issue with the way I have this set up, if so someone PLEASE shout out so I can fix it![/quote]You shouldn't be exporting /var.  You definetely shouldn't be exporting it with guest access.

You shouldn't export multiple shares with the same path, it's rather silly.

But no one can do a real audit without your [global] seciton.

> With the OS's file browser, I went into each area and changed permissions and changed the owner to www-data and allowed r/w/e to all.
I know I have some fixing to do with this setup.If you did that on /var, then you hosed your system.  Unless you've really put a ton of work into it, a reinstall would be prudent.

Don't play with permissions unless you're 100% what you're playing with.  If you're not, ask.

[quote=Bender10]But, when I try to connect to Ubuntu from a Win machine I get the '\\Ubuntu is not accessible' (w2k), or '\\Ubuntu is not accessible You might not have permission to use the network resource Contact your administrator.....' (on XP).[/quote]First off, use an IP address to verify the connection, not the name.  Second, please post the whole message.  Windows gives the same paragraph of text for most Windows Networking (SMB/CIFS) errors, with only the last line of the dialog being different.  Finally, did you create a SMB password for your account with: 'sudo smbpasswd -a user'?

[quote=duffydack]anyone know why i cant use "admin" thats setup and logged into linux already? too many logins at same tim[/quote]There is no admin user by default, only a group.  And you can't login as a group.

[quote=i_am_socket]Easy fix for most Samba problems: use the latest debian version from Samba.org (I just posted this yesterday for someone else I think) instead of the Ubuntu version on synaptic. This made life easier sharing for windows and macs.[/quote]Besides for a recent serious Windows 2003 SP1 breakage, this won't help issues at all.  Samba's relatively stable, as in Windows.  This is bad advice.  Version upgrades should only be recommended as a fix when it will actually fix the issue.  Everything I've seen posted here is configuration.

---

