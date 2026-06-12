---
title: "Samba Host Users Authentication"
date: 2011-05-07
forum: Server Platforms
---

### Post by grants on 2011-05-07
How can I configure smbd to use the current users of my server rather then creating a new samba account for each user with different passwords?

I'd like to set my samba server up so that when authenticating to it would just direct users logging in to their home directory (~) if they are permitted to login. Kinda like what SSH does when you jail someone to their home folder. But I also don't want to have to manage passwords for samba and passwords for the server itself. I'd like to use the same accounts. Is this possible?

I've tried searching and it looks possible but I'm pretty new to samba and I seem to be getting confused with the config file. I even installed the GUI for administering samba but this doesn't seem to do what I want either.

---

### Post by Morbius1 on 2011-05-07
If I understand your requirements this is an old school Server configuration and is accomplished using the [homes] share in smb.conf:

[1] Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```[2] Add the following section to smb.conf:
```
[homes]
comment = Home Directories
browseable = no
valid users = %S
writable = yes

```[COLOR=Blue]*You will notice that the share definition has no path. That is not a mistake that's the way the [homes] share works.*[/COLOR]
[3] Save smb.conf and then restart samba:
```
 sudo service smbd restart
```In practice it works differently for a Windows client than a Linux client.

In Windows if the Server user name and samba password are an exact match to the Windows login username and password ( and I'm talking about the actual login name to the Windows box itself ) then the connection is automatic.

In Linux the remote user will have to access the server this way since you cannot browse to the [homes] share:
```
nautilus smb://server/user-name
```Once nautilus opens up you can bookmark it so the user will not have to use the terminal anymore.

For the second part about not requiring the creation of a samba password for each user there is a package that can take care of that for you:
```
sudo apt-get install libpam-smbpass
```What this package will do is force at boot time the smbpassword = server user's login password.

[COLOR=Blue]**EDIT**[/COLOR]: Each remote user will only have access to their corresponding home directory on the server. In fact since the shares are not browseable they won't even know that other users exist.

---

### Post by grants on 2011-05-07
> **Morbius1 said:**
> In fact since the shares are not browseable they won't even know that other users exist.

PERFECT.

This will effectively set all user accounts on my server to have corresponding samba accounts jailed to their home not being able to see other shares correct?

Q1,
How can I restrict access to only some of my user accounts on the server? Can I reject specific people or only allow specific people with libpam-smbpass, either option would work for my case.

Q2
Will I still be able to create one master account that will be able to see all shares?

Sorry I'm a noob with this stuff. Thanks for the helpful directions though.

---

### Post by Morbius1 on 2011-05-07
>  This will effectively set all user accounts on my server to have  corresponding samba accounts jailed to their home not being able to see  other shares correct?They will not be able to see anyone else's home share but you can always create other shares that are browseable and accessible by anyone.
>  How can I restrict access to only some of my user accounts on the  server? Can I reject specific people or only allow specific people with  libpam-smbpass, either option would work for my case.Not through libpam-smbpass. It's been a while but I'm almost certain you can add an "invalid users" line to the [homes] section in addition to the "valid users = %S" line, for example:
```
invalid users = bob, jane, agness
```"invalid users" always has priority over the "valid users" line.
> Will I still be able to create one master account that will be able to see all shares?That's a good question. I'm not used to using it this way. I always login into the server itself and then as sudo do whatever I have to do. That one I need to think about a bit.

---

### Post by grants on 2011-05-07
I have openssh working great with key authentication so I can always login and sudo to root to be able to move things around as needed. But I'd still like the ease of a GUI on my mac.

My goal to do the following:

1) Set everyone up with their own account. With the ability to restrict access when needed. 

2) Have one shared folder among a specific few users (a music folder)

3) Have one master account for me to use if I need to move files around for people. 
 - SSH and scp would work but i don't like running each command by itself if I need to move many files around. And OS X makes it complicated on FTP since I only get read access regardless of the settings (why they did this, I will never know)
- I've tried transmit and a few other FTP programs on my Mac but haven't found a reliable one that will send a 1 gig file with out disconnecting. But Samba seems to work great even with large files.

---

### Post by Morbius1 on 2011-05-07
Well I can get this to work using [homes] with the additional requirement of a master user but it's actually somewhat complicated because of Linux permissions and in the long run I think we should dump the [homes] idea and use a different approach.

For each user share his own home directory and limit access to that specific user and the master user and no one else. So in smb.conf it would look like this:
> [user1share]
path = /home/user1share
valid users = user1, master
read only = no
force user = user1The valid users will restrict access to just that user and user = master.
The force user line resolves the problem with master's access. When master is allowed in by samba his identity will be converted to user1. This will allow master to add to, delete, and edit any file in the share.

You would have to do that for every user whose home folder you want to share. For those users that you do not want to have access to a home folder don't create a share for them. Libpam-smbpass will still create the samba password automatically.

As for the Music folder something like this should work:
Create a shared Music directory , say....
```
sudo mkdir /home/Music
```Change permissions on the directory to allow everyone access:
```
sudo chmod 1777 /home/Music
```The "1" is a sticky bit meaning that everyone will be able to add to the folder but only the original owner, the owner of the parent directory, and root can delete it. You can either keep the owner as root or change it to master if that's what you want to do:
```
sudo chown master /home/Music
```Then limit access to the share in the samba definition:
```
[music]
path = /home/Music
valid users = jim, pat, alice, tim, master
read only = no

```So when "jim" adds a music file it will save as 644 permissions meaning "pat" for example will be able to copy it and use it but won't be able to edit the file and because of the 1777 permissions on the parent folder "pat" will not be able to delete the file.

---

### Post by grants on 2011-05-08
> **Morbius1 said:**
> Well I can get this to work using [homes] with the additional requirement of a master user but it's actually somewhat complicated because of Linux permissions and in the long run I think we should dump the [homes] idea and use a different approach.
That's my hope to, start from square one the right way.


> **Morbius1 said:**
> 
For those users that you do not want to have access to a home folder don't create a share for them. Libpam-smbpass will still create the samba password automatically.

So this is making a share for the restricted users that have accounts on my system but since nothing is shared they wont see anything? Ideally I'd like to just block the logon. Maybe thats what this is doing too.

> **Morbius1 said:**
> 
So when "jim" adds a music file it will save as 644 permissions meaning "pat" for example will be able to copy it and use it but won't be able to edit the file and because of the 1777 permissions on the parent folder "pat" will not be able to delete the file.


This is a iTunes library database. All users need to be able to modify and delete content. This is essentially a shared library among a few MacBook Air's since I can't hold everything on my drive. Other people will be using this too that I have given access and also activated their computer under my account. If each user doesn't have the ability to change the metadata / db files, iTunes will lock up. Any way uploads to that folder can be 777 instead of 644, and what is the 1 on the chmod 1777 statement? I don't know if I've ever seen that before. 


I never said this one was going to be easy! :mrgreen: But I appreciate your help so far, I think I have enough to get this started. Server is in the middle of some processing and I don't know how to suspend it so I have to wait a few days to do a reboot. but hopefully when all this is done I'll be able to do a nice write up for others to use and get this working securely.

---

### Post by Morbius1 on 2011-05-08
> So this is making a share for the restricted users that have accounts on  my system but since nothing is shared they wont see anything? Ideally  I'd like to just block the logon. Maybe thats what this is doing too.It's making a share of the home directory only for those users that you want to access their corresponding home directories and for the master user that has access to all the these home directories. The other users will see that another users home directory exists but they will not be able to access it.
> All users need to be able to modify  and delete content. This is essentially a shared library among a few  MacBook Air's since I can't hold everything on my drive. Other people  will be using this too that I have given access and also activated their  computer under my account. If each user doesn't have the ability to  change the metadata / db files, iTunes will lock up. Any way uploads to  that folder can be 777 instead of 644, and what is the 1 on the chmod  1777 statement? I don't know if I've ever seen that before. The "1" is called a sticky bit. It doesn't limit who can add to the directory but it does limit who can delete from the directory. It was created so that "mary" can't delete "jeff's" files because they had a fight last night :wink:. If you don't want or need that feature then don't use the "1":
```
sudo chmod 777 /home/Music
```

---

### Post by grants on 2011-05-08
Great,
Thank you.

It may be a few days before I check back on this thread due to the restart thing. So it would be great if you can check your previous posts in a few days if I have a few final problems :D

---

### Post by grants on 2011-05-21
Can I send you my smb config file for you to take a look at?

I made the changes as you had said, still can't seem to get this working. 

I'm stuck on part 1. User authentication. I have a fresh install of samba and a few test users made and none of them work.

---

### Post by grants on 2011-05-21
CORRECTION.

Root account works, newer users however do not. Still trying some things with the other accounts to find out why.

---

### Post by Morbius1 on 2011-05-22
Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by grants on 2011-06-01
root@ubuntu-server:/etc/samba# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[storage]"
Processing section "[ubuntu-server]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	invalid users = steph, adam, kevin, george
	valid users = %S
	read only = No
	create mask = 0755
	browseable = No
	browsable = No

[storage]
	comment = /storage
	path = /storage
	invalid users = steph, adam, kevin, george
	valid users = %S
	read only = No
	create mask = 0755
	browseable = No
	browsable = No

[ubuntu-server]
	comment = /root
	path = /
	invalid users = steph, adam, kevin, george
	valid users = grant
	force user = grant
	read only = No
	create mask = 0755
	browseable = No
	browsable = No






net usershare info -long 
- No output.


My problem is that once i'm logged in as one user it keeps me as that user. 

Ex 1. I log in as myself to see my home directory it forces me as that users. This is ok but when I load my root share I have permission issues for some reason.

Ex 2. User loads the group share first. Now they will not be able to load there personal share. 

Other problem, 
Any user can access any other users share even though they don't see it. I think I need to separate the shares out with specific requirements for each


ex.
[grant]

[steph]

[guest1]

[guest2]

This would also take care of the issues with permissions since I could force user for each home directory. 

Is there anyway to specify the users home directory with that path option and also have a second path. 

ex.

[grant]
	comment = My Master Share
	path = /home/grant
        path = /
	invalid users = steph, adam, kevin, george
	valid users = %S
	read only = No
	create mask = 0755
	browseable = No
	browsable = No
        force user = grant

I know this sounds dumb to have two paths but for OS x and how it reads samba shares its useful to separate the root directory from my personal directory with how I'm setting this up with iTunes.

---

### Post by jhardydj on 2011-06-02
> **grants said:**
> I have openssh working great with key authentication so I can always login and sudo to root to be able to move things around as needed. But I'd still like the ease of a GUI on my mac.

My goal to do the following:

1) Set everyone up with their own account. With the ability to restrict access when needed. 

2) Have one shared folder among a specific few users (a music folder)

3) Have one master account for me to use if I need to move files around for people. 
 - SSH and scp would work but i don't like running each command by itself if I need to move many files around. And OS X makes it complicated on FTP since I only get read access regardless of the settings (why they did this, I will never know)
- I've tried transmit and a few other FTP programs on my Mac but haven't found a reliable one that will send a 1 gig file with out disconnecting. But Samba seems to work great even with large files.

Check out Samba4.

---

### Post by grants on 2011-06-02
> **jhardydj said:**
> Check out Samba4.

I didn't know there was even a new version in development. 

From what I've read so far this looks too new to rely on and there doesn't seem to be much documentation on how to set it up and what the differences are. 

Thanks for the help though.

---

