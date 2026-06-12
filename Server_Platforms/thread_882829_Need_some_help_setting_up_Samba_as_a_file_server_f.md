---
title: "Need some help setting up Samba as a file server for Windows clients"
date: 2008-08-07
forum: Server Platforms
---

### Post by KolosoK on 2008-08-07
EDIT: PLEASE SEE THE SECOND POST ON THE SECOND PAGE AFTER READING THIS :)

Hello,

I've finally decided to take the plunge and use Linux for a file server instead of Windows. It seems to be running way more stable and is taking up fewer resources, which is awesome! I am using version 8.04 of Ubuntu Server. I have had some previous experience with unix-based systems my last quarter of freshman year at UCLA (I'm a CS major), so I know some basics.

I've gone for a LAMP configuration (even though I will not be using all of its features just yet, but a database and a simple internal website for being organized may be in the works soon). Everything is up and running. I am able to remotely SSH into the server (it has a static IP address), as well as access WebMin with no problems whatsoever. So the routing aspect was done correctly (as far as I know) - all the necessary ports are open and the configuration files (hosts, etc) for the network seem to work the way they are supposed to.

Now the problem I am having involves Samba. I would like to use this server to host some files that are accessible to certain users and to provide some users with around 2gb of their own space. However, all of these users employ Windows Vista as their primary operating experience. Using linux is not an option for them.

Unfortunately, when I create shared folders and configure them, they end up having either too much or too little access. Sometimes I am able to access the folder from a Windows machine, but them I am unable to copy files to it (I do have the writeable flag set to yes/true). Sometimes the folder requires no password even though I've set it to ask for one.

Here's the basic structure that I would like the file server to have:

```
MAIN FOLDER (accessible by anyone without a password, not writeable)
- READ ONLY FILE FOLDER (accessible by certain users with a password, not writeable)
- WRITE FOLDER (accessible by the same certain users with a password, writeable)
- SEPARATE FOLDERS FOR EACH USER (accessible by the owner user, writeable)
```

Could anyone please assist me in writing a configuration file for samba in order to achieve such a structure?

Thank you all for your generous help!

---

### Post by hyper_ch on 2008-08-07
[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by KolosoK on 2008-08-07
> **hyper_ch said:**
> [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

Thank you for the link! Unfortunately, it describes how to share folders on Windows machines for the Linux machine to be able to access them. I am working on something that does the opposite. I think I simply need help editing the samba configuration file. WebMin's interface for Samba makes it a bit confusing.

---

### Post by hyper_ch on 2008-08-07
did you search the forum or tried google yet on that issue?

---

### Post by jerome1232 on 2008-08-07
you might want to install samba-doc

fire up you favorite web browser and point it to /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html

you may check out samaba's config man page: man smb.conf

---

### Post by KolosoK on 2008-08-07
> **hyper_ch said:**
> did you search the forum or tried google yet on that issue?

Yes, I looked at sample configuration files for folder sharing. For some reason, some of them do not work as advertised (my main issue was gaining write access). Are there key parameters that must be set in [global] within the configuration file?

> **jerome1232 said:**
> you might want to install samba-doc

fire up you favorite web browser and point it to /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html

you may check out samaba's config man page: man smb.conf

Which browsers are available on Ubuntu Server?

I read the man pages yesterday, I'll try to play around more with it.

---

### Post by jerome1232 on 2008-08-07
lynx, links2 are both good, you would run them like lynx <address to go to> I believe they are both installed by default. I admin my server via ssh so in my case I'd just install samba-doc on the machine I'm at and use firefox :)

---

### Post by KolosoK on 2008-08-07
> **jerome1232 said:**
> lynx, links2 are both good, you would run them like lynx <address to go to> I believe they are both installed by default. I admin my server via ssh so in my case I'd just install samba-doc on the machine I'm at and use firefox :)

Thanks,

Unfortunately, I'm using Putty to SSH from a Vista machine :s

I'll try lynx/links2.

EDIT: Yep, worked fine, thanks again :) Going to do a read through of that.

---

### Post by jerome1232 on 2008-08-07
This is totally off subject but you might be interested in the program screen

it can create split windows etc and if you lost your ssh session, next time you log in you can type screen -r to resume your previous screen session.

You could have your documentation in one window and be doing you work in the region below it

like this:
```
screen lynx <url>
then hit ctrl+a shift+s      # that creates a new region
then ctrl+a tab              # switches to new region
ctrl+a ctrl+c                # creates a new window in current region

```

now you should have your documentaion up at the top and a prompt to work in at the bottom, screen was a godsend for me so I thought i'd mention it

edit: make sure putty is set for utf8 otherwise a few programs can give you garbled text, ctral+a shift+x deletes a region

---

### Post by KolosoK on 2008-08-07
I've been fighting it for a few hours now and got nowhere. I created a folder, set it to permissions 755, and set myself as the owner.

My computer sees the folder fine, but when I try to log in with my username and password, Windows says that logon was unsuccessful.

Here's my configuration for the shared folder:

```
[FOLDERNAME]
force create mode = 755
writeable = yes
write list = myusername
path = /pathtofolder
force directory mode = 755
available = yes
browseable = yes
```

Edit: Windows Vista changes my login information to ComputerName/MyUserName. Is this why it does not work?


Edit 2: I've decided to work completely from scratch...

Here's my smb.conf so far:

```
[global]
	netbios name = ServerName
	load printers = no
	netbios aliases = ServerName
	server string = ServerName
	socket options = TCP_NODELAY
	workgroup = WorkGroupName
	os level = 32
	encrypt passwords = yes
	security = user
	wins support = true
```

---

### Post by KolosoK on 2008-08-08
Alright, finally got it working using the following guides:

[http://www.giannistsakiris.com/index.php/2007/09/22/writeable-shared-folder-with-samba-on-ubuntu/](http://www.giannistsakiris.com/index.php/2007/09/22/writeable-shared-folder-with-samba-on-ubuntu/)
[http://ubuntuforums.org/archive/index.php/t-126838.html](http://ubuntuforums.org/archive/index.php/t-126838.html) (LordHunter317's post)

Anyone know how I would make it so two groups own a folder and can access it? :s

---

### Post by KolosoK on 2008-08-11
Ok, some new issues came up:

- I would like to test various groups' access rights from a Windows machine. How can I change my login? It keeps logging me in as guest user. What do I have to put into the address bar? (Something like user@hostname?)

- I need Samba to allow certain groups access to certain files and disallow such access to other certain groups. For example, I want the smb group to be able to access everything (rwx), but specific users to be able to access only their own folders (rwx, r_x for everything else).

Can anyone help me out with these two? :)

EDIT: Also would like some guidance for using quotatool (for setting up quotas for individual users)

EDIT 2: I figured out the access control and the quotatool. For the folder log in I used network drive mapping. And I found a nice quotatool guide here: [http://www.debian-administration.org/articles/47](http://www.debian-administration.org/articles/47)

---

### Post by guilly on 2008-08-11
> **KolosoK said:**
> Ok, some new issues came up:

- I would like to test various groups' access rights from a Windows machine. How can I change my login? It keeps logging me in as guest user. What do I have to put into the address bar? (Something like user@hostname?)

- I need Samba to allow certain groups access to certain files and disallow such access to other certain groups. For example, I want the smb group to be able to access everything (rwx), but specific users to be able to access only their own folders (rwx, r_x for everything else).

Can anyone help me out with these two? :)

EDIT: Also would like some guidance for using quotatool (for setting up quotas for individual users)

EDIT 2: I figured out the access control and the quotatool. For the folder log in I used network drive mapping. And I found a nice quotatool guide here: [http://www.debian-administration.org/articles/47](http://www.debian-administration.org/articles/47)

I know from a linux box you can put in the address bar I believe it's something like smb://host@XXX.XXX.XXX.XXX

but from windows I would say the best way would be to try and connect from network places but make sure you are logged in under a user that does not have a corresponding username on your linux box. This way it should prompt you for user name and password each time. Just make sure not to click the box to remember password and you should be good.

---

### Post by KolosoK on 2008-08-11
> **guilly said:**
> I know from a linux box you can put in the address bar I believe it's something like smb://host@XXX.XXX.XXX.XXX

but from windows I would say the best way would be to try and connect from network places but make sure you are logged in under a user that does not have a corresponding username on your linux box. This way it should prompt you for user name and password each time. Just make sure not to click the box to remember password and you should be good.

Unfortunately the samba user accounts will be different from what the Vista machines are using. I solved this by using network drive mapping.

Still need to figure out how to allow only a certain user and members of a different group to have write permissions in a certain folder.

---

### Post by cariboo on 2008-08-11
I always found this document:

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

To be very helpful in setting up samba.

Jim

---

