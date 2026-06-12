---
title: "Samba interaction with windows user"
date: 2009-06-03
forum: Security
---

### Post by markdavidoff on 2009-06-03
I am trying to set up a new fileserver. I understand that samba has some method of checking the windows username (and password?) with the accounts that are on the fileserver.

**What I need:**

My last fileserver had the same username and password as my windows computer that accessed it. It was set up in a way so that anyone on the share had "full access"

```
[global]
security=share

[public]
comment = Public Share
path = /home/public
browseable = yes
guest ok = yes
read only = no
```

except, my user on the fileserver (with the same name and password as my windows computer) was the only one with unix read/write/execute access.
Therefore, only my windows computer with the same username and password was able to write to the directory. All the other windows computers had read access only.

**Now for the problem:**

My new fileserver setup is different. I installed ubuntu desktop edition on it instead of server edition. I wanted full access to anyone physically using the fileserver machine to modify the shared drive. This is fine, i just gave full permissions to the drive. However, I don't want my network users having write access, so I decided that would be handled by my smb.conf.

However, I am having problems getting samba to recognize my windows computer. The new fileserver hasn't got the same username and password on it, so I created a user on that machine with the same username and password. I want it set up like my last server - samba will detect that my username and password on my windows computer is valid for write permissions automatically.

my new smb.conf:

```
[Global]
security=share

[Share]
comment = Shared Media
path  = /media/Media
browseable = yes
guest ok = yes
read only = yes
write list = mark
```

So what I have here is the opposite to my last set up:
[LIST]
[*]I am using desktop edition instead of server edition
[*]Samba is setting the drive as read-only (except for the write list) instead of read-write
[*]The drive itself has unix permission based full access, instead of unix permission based user only access
[/LIST]

**What I did:**

[LIST]
[*]I apparently needed to install libpam-smbpass, so I did that.
[*]I mounted the drive with full-access permissions on the server
[*]I created a smb.conf which would allow only read access to this drive, except for the users on the write list
[*]I added a new user on the fileserver using the "Users and groups" admin tool.
[/LIST]

I can log in to the drive on my windows computer (with the same username and password as the user on the write list), but I cannot modify files.

It is a problem with my samba set up. I can modify files if I turn read only off in the smb.conf file.

I also browsed to /var/log/samba/log.(computername)

and it says:```
smbd/service.c:make_connection_snum(1111)
  (computername) (computerIP) connect to service NEWSERVER initially as user nobody
```

It is not detecting my username!

On my old fileserver, the same log file read:
```
smbd/service.c:make_connection_snum(1111)
 (computername) (computerIP) connect to service OLDSERVER initially as user mark
```

So what can I do so that it will detect my username?

---

### Post by markdavidoff on 2009-06-04
Help, any one?

---

### Post by munky99999 on 2009-06-04
[Global]
security=share

[Share]
comment = Shared Media
path  = /media/Media
browseable = yes
guest ok = yes
read only = no
force user = WHATEVER
force group = WHATEVER
create mask = 0775

That'll do the job.

Now [https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html) shows you how to secure the server.

---

### Post by markdavidoff on 2009-06-05
> **munky99999 said:**
> [Global]
security=share

[Share]
comment = Shared Media
path  = /media/Media
browseable = yes
guest ok = yes
read only = no
force user = WHATEVER
force group = WHATEVER
create mask = 0775

That'll do the job.

Now [https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html) shows you how to secure the server.

No...that will just force every user to connect as the defined user.
I need a write list so that only certain users have write access.

However, I did manage to solve the problem by installing SSH, and logging in from my system using my username

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

I suppose it authenticated my computer access to that username. Is that correct? Can someone explain this?

Thanks

---

### Post by daaussie on 2009-06-05
Ok, I got it working the first time and mine looks like this. What's your thoughts on this?

Also do you use UFW? I posted a thread on this today: [http://ubuntuforums.org/showthread.php?t=1179473](http://ubuntuforums.org/showthread.php?t=1179473)

[test]
path = /home/<<USER>>/<<CHOOSE YOUR NAME>>
available = yes
valid users = tms
read only = no
browsable = yes
public = yes
writable = yes

Then: 
save file
sudo /etc/init.d/samba restart

On the Desktops you just insert a mount command in "sudo gedit /etc/fstab":

//<<server IP>>/<<CHOOSE YOUR NAME>> /home/<<WORKSTATION NAME (eg Katie)>>/<<CHOOSE YOUR NAME>>_ON_SERVER smbfs username=<<server logon name>>,password=<<_____>>, 0 0

Make sure you create the folder as well on the WORKSTATION by going into terminal:
sudo mkdir /home/<<WORKSTATION NAME>>/<<CHOOSE YOUR NAME>>_ON_SERVER

---

### Post by markdavidoff on 2009-06-06
> **daaussie said:**
> Ok, I got it working the first time and mine looks like this. What's your thoughts on this?

Also do you use UFW? I posted a thread on this today: [http://ubuntuforums.org/showthread.php?t=1179473](http://ubuntuforums.org/showthread.php?t=1179473)

[test]
path = /home/<<USER>>/<<CHOOSE YOUR NAME>>
available = yes
valid users = tms
read only = no
browsable = yes
public = yes
writable = yes

Then: 
save file
sudo /etc/init.d/samba restart

On the Desktops you just insert a mount command in "sudo gedit /etc/fstab":

//<<server IP>>/<<CHOOSE YOUR NAME>> /home/<<WORKSTATION NAME (eg Katie)>>/<<CHOOSE YOUR NAME>>_ON_SERVER smbfs username=<<server logon name>>,password=<<_____>>, 0 0

Make sure you create the folder as well on the WORKSTATION by going into terminal:
sudo mkdir /home/<<WORKSTATION NAME>>/<<CHOOSE YOUR NAME>>_ON_SERVER


My desktops are windows desktops, which was probably part of the problem.
When I connected to my share, it logged my windows computers in as "nobody" instead of their user account names (checked in the samba log files).

So if I used your config, it still wouldn't have worked, as you have defined a valid user, but the computers usernames were not being recognised.

Only after I installed an SSH server, and logged in to that, my windows computers were being recognised, probably due to some authorisation issue.

I was hoping someone could explain the relationship to the SSH authorisation and samba user authorisation

Also, no, I'm not using UFW, I don't even know what that is :)

---

### Post by cariboo on 2009-06-06
I don't see any mention of setting samba passwords for your windows users, that may be part of the problem.

```
sudo smbpasswd -L -a <user>
```

and to enable the user

```
sudo smbpasswd -L -e <user>
```

---

