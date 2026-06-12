---
title: "Samba guide for 16.04?"
date: 2016-06-12
forum: Server Platforms
---

### Post by timg11 on 2016-06-12
I've been trying to get Samba to share files to Windows machines for a couple of days, and read a lot of threads. The best I've done is to be able to see the share exists from a Windows machine, but read and write access is always denied.  I was trying for anonymous access, but even logging in with the Ubuntu machines credentials doesn't work. 

There are a few guides and wikis, but they are for Ubuntu versions between 8 and 12.  Is there any definitive guide for configuring Samba for 16.04?  Or are the changes in that range of Ubuntu versions inconsequential? 

[This guide ]("https://help.ubuntu.com/community/Samba/SambaServerGuide") talks about "Samba Server Configuration by GUI" for KDE and Gnome. No mention of Unity. Is there a config GUI for Unity?

---

### Post by X-RED_Tech on 2016-06-12
When you right-click -> Share... in any folder you're presented with a config GUI where you can enable r/w for the share and/or guest access.
Also there are a few graphical tools for the job but I never used them. Enabling it via file manager as mentioned above always worked as it should.

---

### Post by timg11 on 2016-06-12
Wow - I had no idea that interface was there. I've been commandline and editing in /etc/samba/smb.conf for hours. 
So I tried "Folder Sharing", Share this folder, Allow others to create and delete, and Guest Access.

When I try to access the Ubuntu machine from Windows, I get the Enter Password dialog. Not exactly Guest Access. But to see what happens, I enter the credentials for a valid user on the Ubuntu machine.  Doesn't work  - "unknown user name or bad password". 

Maybe I need to go back to the original version of /etc/samba/smb.conf?

Here's what is added currently:

```

[global]
  follow symlinks = yes
  wide links = yes
  unix extensions = no



[sharing]
   comment = XD-2T-08
   path = /media/tim/XD-2T-08
   browseable = yes
   public = yes
   writable = yes
   readonly = No
   guest ok = yes
   guest only = Yes
   createmask = 0664
   force directory mode = 2775
```

---

### Post by bab1 on 2016-06-13
> **timg11 said:**
> Wow - I had no idea that interface was there. I've been commandline and editing in /etc/samba/smb.conf for hours. 
So I tried "Folder Sharing", Share this folder, Allow others to create and delete, and Guest Access.

When I try to access the Ubuntu machine from Windows, I get the Enter Password dialog. Not exactly Guest Access. But to see what happens, I enter the credentials for a valid user on the Ubuntu machine.  Doesn't work  - "unknown user name or bad password". 

Maybe I need to go back to the original version of /etc/samba/smb.conf?

Here's what is added currently:

```

[global]
  follow symlinks = yes
  wide links = yes
  unix extensions = no



[sharing]
   comment = XD-2T-08
   path = /media/tim/XD-2T-08
   browseable = yes
   public = yes
   writable = yes
   readonly = No
   guest ok = yes
   guest only = Yes
   createmask = 0664
   force directory mode = **[COLOR="#FF0000"]2[/COLOR]**775
```
Samba shares can be created both manually (as above) or using The GUI file manager (gvfs (Nautilus usershares).  But you should use one or the other for the share definition.  The usershares definitions are located at /var/lib/samba/usershares.

The share definition is only part of the equation.  You need to insure that the ownership and permissions allow the user to access the directories in the path from / to  /media/tim/XD-2T-08.  Mortal users (humans) can create usershares and should do so only in their own /home directory.  

There is no reason to modify the smb.conf file other than adding the share definitions at the bottom of the file.  Run this terminal command and post the contents back here```
smbtree -d3
```

Please post the text output inside [noparse]```
  
```[/noparse] blocks.  The easiest way to do that is to click on the  **[SIZE=8]#[/SIZE]** ***icon*** at the top of the advanced editor that you use to respond to the forum.

---

### Post by timg11 on 2016-06-13
> **bab1 said:**
> Samba shares can be created both manually (as above) or using The GUI file manager (gvfs (Nautilus usershares).  But you should use one or the other for the share definition.  The usershares definitions are located at /var/lib/samba/usershares.

The share definition is only part of the equation.  You need to insure that the ownership and permissions allow the user to access the directories in the path from / to  /media/tim/XD-2T-08.  Mortal users (humans) can create usershares and should do so only in their own /home directory.  

There is no reason to modify the smb.conf file other than adding the share definitions at the bottom of the file.  Run this terminal command and post the contents back here```
smbtree -d3
```

Please post the text output inside [noparse]```
  
```[/noparse] blocks.  The easiest way to do that is to click on the  **[SIZE=8]#[/SIZE]** ***icon*** at the top of the advanced editor that you use to respond to the forum.

 
Thanks for the help. I had to install smb client first:  "sudo apt install smbclient"

Then smbtree -d3  resulted in several hundred lines of text, including details of many, but not all, machines on my network. I'm not comfortable posting all of it. 
Here's a few lines that caught my attention as being relevant. Let me know if there are other parts needed:

```

tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name GALAXY<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name GALAXY<0x1d>
Got a positive name query response from 192.168.xxx.xxx ( 192.168.xxx.xxx )
Connecting to 192.168.xxx.xxx at port 445

```

Here's the section that scans the Ubuntu system in question (Uranus)

```

Connecting to 192.168.xxx.xxx at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
	\\URANUS         		Uranus server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name URANUS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name URANUS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name URANUS<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
		\\URANUS\images         	
		\\URANUS\IPC$           	IPC Service (Uranus server (Samba, Ubuntu))
		\\URANUS\sharing        	XD-2T-08
		\\URANUS\print$         	Printer Drivers

```

---

### Post by Doug S on 2016-06-13
There are significant changes in samba with 16.04. We have been trying to get the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/samba.html") updated, and have only been partially successful so far.

---

### Post by bab1 on 2016-06-15
> **timg11 said:**
> Thanks for the help. I had to install smb client first:  "sudo apt install smbclient"

What an unfortunate package name.  The package installs the command line tools.  I don't know how you installed the "package" samba, but I never have had to install the command line tools separately. 
> 
Then smbtree -d3  resulted in several hundred lines of text, including details of many, but not all, machines on my network. I'm not comfortable posting all of it. 
There is nothing secret in the output.  The only parts that are variable are the IP addresses.  This are the same on millions of computers all over the globe.  Private addrs are used over and over by everyone.  The other variables are the NetBIOS names.  Nobody really cares what you name these hosts.> 
Here's a few lines that caught my attention as being relevant. 
If your asking for help, how would you know what is relevant?  ;-)> 
Let me know if there are other parts needed:

Here's the section that scans the Ubuntu system in question (Uranus)

```

Connecting to 192.168.xxx.xxx at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
	\\URANUS         		Uranus server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name URANUS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name URANUS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
[SIZE=3][COLOR="#FF0000"][B]resolve_hosts: Attempting host lookup for name URANUS<0x20>
Connecting to 127.0.1.1 at port 445[/B][/COLOR][/SIZE]
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
SPNEGO login failed: Logon failure
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62008a15
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62008a15
		\\URANUS\images         	
		\\URANUS\IPC$           	IPC Service (Uranus server (Samba, Ubuntu))
		\\URANUS\sharing        	XD-2T-08
		\\URANUS\print$         	Printer Drivers

```
The part in red is the problem.  You can either correct the hostname setting by editing the ***/etc/hosts*** file mapping or you can add these lines to the [global] section of the ***smb.conf*** file```
# Declare NetBIOS name
        netbios name = URANUS
# Set name resolve order
        name resolve order = bcas
```

Don't forget to restart the smbd daemon with this command```
sudo systemctl restart smbd.service 
```

---

### Post by bab1 on 2016-06-15
> **Doug S said:**
> There are significant changes in samba with 16.04. We have been trying to get the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/samba.html") updated, and have only been partially successful so far.
What do you see as "significant changes in samba with 16.04".  As far as the smbd (file sharing) and nmbd (name services) are concerned, there doesn't seem to be any difference other that using systemd to start|stop|restart those daemons.

I seem to spend most of my time helping others get Samba file sharing to work so I am interested in others information on this.  I'm no guru when it comes to AD/DC.  My guess is that AD is where the differences are, yes?

---

### Post by timg11 on 2016-06-15
Thanks for the information. 

I will add those hostname settings, but I found the real issue elsewhere.

It is now required to set the smb password separately with "sudo smbpasswd -a user" 
Apparently, in earlier versions Earlier libpam-smbpass would synchronize your existing password with samba password, but that has been taken out.

Once I set the smb password, I was able to log in from the client and access the share.

---

### Post by bab1 on 2016-06-15
> **timg11 said:**
> 
It is now required to set the smb password separately with "sudo smbpasswd -a user" 
Apparently, in earlier versions Earlier libpam-smbpass would synchronize your existing password with samba password, but that has been taken out.

Once I set the smb password, I was able to log in from the client and access the share.
The security setting ```
security = share
```Has been deprecated for years now.  You should have always used (and it is now the default) ```
security = user
```

This is nothing new for Samba.  I have been preaching this for years.  You can still set guest access however.

If you have solved your problem it helps to mark this thread as "Solved".  Do you know how to do that?

---

### Post by Doug S on 2016-06-16
> **bab1 said:**
> What do you see as "significant changes in samba with 16.04".  As far as the smbd (file sharing) and nmbd (name services) are concerned, there doesn't seem to be any difference other that using systemd to start|stop|restart those daemons.I meant that one can not longer setup samba the same way that they always have before (and as this thread found.  libpam-smbpass was removed (rather late in the 16.04 cycle, by the way). It took me a couple of months to get samba working again. While a few updates have been made to the Ubuntu Serverguide, more updates are needed. I cann't recall the name of the package that is supposed to restore some of the functionality (it might have been libpam-winbind).

> **bab1 said:**
> I seem to spend most of my time helping others get Samba file sharing to work so I am interested in others information on this.  I'm no guru when it comes to AD/DC.  My guess is that AD is where the differences are, yes?I don't know what you mean by AC/DC. My troubles were partly related to trying to use "classic primary domain controller", and I gave up and moved to "standalone server".

---

### Post by Morbius1 on 2016-06-16
The irony here is that credentials have to be passed to access a guest share. It has nothing to do with changes made to samba since 14.04. It has nothing to do with libpam-smbpass. It has to do with the path to the shared folder:
> [sharing] 
   comment = XD-2T-08
   [COLOR=#0000cd]**path = /media/tim/XD-2T-08**[/COLOR]
   browseable = yes
   public = yes
   writable = yes
   readonly = No
   guest ok = yes
   guest only = Yes
   createmask = 0664
   force directory mode = 2775
I suspect "tim" is a user name and if the OP would run this command he would see the dilemma posed by that path:
```
getfacl /media/tim
```
It should look something like this:
> getfacl /media/tim
getfacl: Removing leading '/' from absolute path names
# file: media/tim
# owner: root
# group: root
user::rwx
user:tim:r-x
group::---
mask::r-x
other::---
There is only one user that will be allowed to pass /media/tim to get to XD-2T-08 and that's "tim". 

Many ways around this issue:

*** Change the mount point to be one level higher on the tree: /media/XD-2T-08
*** Change the share definition so that the guest appears to be "tim" for this share:
> [sharing] 
   comment = XD-2T-08
   [COLOR=#000000]path = /media/tim/XD-2T-08[/COLOR]
   browseable = yes
   public = yes
   writable = yes
   readonly = No
   guest ok = yes
[COLOR=#0000cd]**force user = tim**[/COLOR]
   

There's an additional issue in this thread. He now has two share definitions for the same folder. One in smb.conf and another in /var/lib/samba/usershares. It's fine to use both methods at the same time ... but not on the same folder. So choose one or the other.

---

### Post by bab1 on 2016-06-16
> ** Morbius1]... It has nothing to do with changes made to samba since 14.04. It has nothing to do with libpam-smbpass. 
[/QUOTE]
I have to agree with all of Morbius1's points.  The OP was not interested in "getting it right" and I'm distracted and tired due to medical issues.  So I'm not chasing after the completeness issue.  If it works for him, it works for me.

I assume, as far as @Doug S's points, we are talking about a Ubuntu Sever environment and therefore talking about a non-GUI environment where everything is configured manually.

[QUOTE=Doug S said:**
> I meant that one can not longer setup samba the same way that they always have before (and as this thread found.  libpam-smbpass was removed (rather late in the 16.04 cycle, by the way). It took me a couple of months to get samba working again. While a few updates have been made to the Ubuntu Serverguide, more updates are needed. I can't recall the name of the package that is supposed to restore some of the functionality (it might have been libpam-winbind).

The  setting*** security=share*** which meant that no user needed to be added to the Samba users database (smbpasswd -a) was deprecated years ago.  Recently the ***security=share*** has been eliminated, but we shouldn't have been using it anyway.  I have never used that parameter.  In fact I believe the current default setting is ***security=AUTO*** which means that Samba searches for the line  ***server role = <your server type>*** and automagically sets the security parameter.  All of this is described in the smb.conf man pages.

I have been told that libpam-smbpass has been changed upstream to pam-smbpass.  Since the upstream packager really controls what happens we don't really have any choice but to follow, even if it is late in the Ubuntu LTS schedule.

The libpam-smbpass has nothing to do with the OP's problem.  Libpam-smbpass doesn't force the user to smbpasswd at all.  The tool smbpasswd adds users to the Samba database.  Libpam-smbpass syncs the Samba password with the Linux password.  You always need to add the user to the Samba users database regardless of whether it is synchronized with the Linux user (passwd) database or not.

The package libpam-winbind just installs the PAM plugins to integrate with winbindd.  If winbindd is not is not installed it will install it for you.  You don't need winbind at all on a stanalone server.  Winbind maps Windows users (SIDS) to Linux (Samba) users (UID/GID).  It is not the source of this problem. 
> 
I don't know what you mean by AC/DC. My troubles were partly related to trying to use "classic primary domain controller", and I gave up and moved to "standalone server".
AD (not AC) means Active Directory and DC stands for Domain Controller.  With Samba v4 there is no "classic primary domain controller" (NT-domains).  It's Active Directory/Domain Controller (AD/DC) or member server (standalone).  Samba.org recommends that the Samba AD/DC not serve files at all.  The preferred setup is a dedicated AD/DC server and a standalone server to serve files.  The problem is the interaction of winbind and the file server causes problems!!!  Samba.org knows about this and is working on the solution.

In the end it appears that there are several small details that have changed (e.g went from deprecated to dropped) that can affect the casual user.  The serious user most likely won't be affected at all.  The only thing that has had any effect on my setup was the recent packaging regression and that was corrected quickly.  If anything it revealed a lot of users misconfiguration.

I'm interested enough to offer my impressions for your Server Guide.  If the guide is correct, hopefully it will help diminish the amount Samba questions to this forum.  Feel free to PM me if interested

---

### Post by Doug S on 2016-06-17
> **bab1 said:**
> I assume, as far as @Doug S's points, we are talking about a Ubuntu Sever environment and therefore talking about a non-GUI environment where everything is configured manually.Yes.

> **bab1 said:**
> You always need to add the user to the Samba users database regardless of whether it is synchronized with the Linux user (passwd) database or not.This is what I never had to do before.

> **bab1 said:**
> I'm interested enough to offer my impressions for your Server Guide.  If the guide is correct, hopefully it will help diminish the amount Samba questions to this forum.  Feel free to PM me if interestedThe [Ubuntu serverguide ]("https://help.ubuntu.com/lts/serverguide/samba.html")would be most grateful for any subject matter expert input to help make it better. The doc team has been pestering the server team for subject matter expert help, and did get some, but more is needed (and not for just Samba).

---

### Post by bab1 on 2016-06-17
> **Doug S said:**
> 

[QUOTE=bab1]You always need to add the user to the Samba users database regardless of whether it is synchronized with the Linux user (passwd) database or not.
This is what I never had to do before.
[/QUOTE]
This has just uncovered your long term misconfiguration.  See here for a [**2010 description**]("http://www.jonathanmoeller.com/screed/?p=1590") of the proper configuration.
> 

The [Ubuntu serverguide ]("https://help.ubuntu.com/lts/serverguide/samba.html")would be most grateful for any subject matter expert input to help make it better. The doc team has been pestering the server team for subject matter expert help, and did get some, but more is needed (and not for just Samba).
Thanks for this

---

### Post by alsoeric on 2016-10-24
> **bab1 said:**
> This has just uncovered your long term misconfiguration.  See here for a [**2010 description**]("http://www.jonathanmoeller.com/screed/?p=1590") of the proper configuration.


This URL doesn't exist anymore. Is the information available somewhere else because I'm having the same problem with 16.04 that there is no synchronization between the unit's accounts and the SMB accounts

---

### Post by bab1 on 2016-10-25
> **alsoeric said:**
> This URL doesn't exist anymore. Is the information available somewhere else because I'm having the same problem with 16.04 that there is no synchronization between the unit's accounts and the SMB accounts

Not all symptoms point to the same resolution.  Start your own thread telling us how you installed samba and what configuration settings you have made.

---

