---
title: "Ubuntu as a server for Windows clients network"
date: 2007-01-07
forum: Server Platforms
---

### Post by sliwowitz on 2007-01-07
I want to ask, how can I use an Ubuntu 6.06 server to serve a network of Windows XP clients. We have a small network of 12 Windows clients and about 60 users and want to replace the Windows 2003 server with Ubuntu. I know, how to configure a linux firewall, nfs and some other linux services, I have working smb file and printer sharing at home, but this seems not like a trivial task (no howto ;-))
Basically, all we need is to manage user accounts - passwords and home directories (documents, settings etc.) So that anyone can login to any workstation and have his start menu and desktop background (I think it's called "roaming profile").
During the past week, I've been searching the web for some useful information - I know there are LDAP, SMB and Kerberos. They all seem to be overly complicated with many obscure features and configuration options (I already tried a lot of ideas, but failed) I know, where to find help on configuration, but I didn't find any information on how exactly do these relate to Windows networking, or how to connect them together, so they'll satisfy our needs. I would be very grateful, if someone could tell me "for a Windows server replacement, you need to instal W, X, Y and Z. Y will store the passwords, Z will handle profiles" or point me to an page (not neccessarily a step-by-step howto) about "what do you need to replace a windows server with a linux one"

---

### Post by Koybe on 2007-01-07
You don't need ldap and many complicated things to manage 12 PC. All you need is samba et make it act as a PDC (Primary Domaine Controller).

Just put this in you smb.conf file to act as a PDC :

```
domain logons = yes
```

To manage your profiles/Home dir :
```

logon path = \%L\profiles\%U  
logon drive = O:
logon home = \%L\%U

[profiles]      
comment = Profles 
path = /home/samba/profiles 
browseable = No 
read only = No
```

Don't forget to create /home/samba/profiles and make home share writable.

If you don't have dns you can also enable wins support if you have some trouble with binding names.

```
wins support = yes
```

Be sure not having root as 'invalid users', add root to samba users using 'smbpasswd -a root'. After this restart samba and you'll be able to join the domain with your windows XP computers.

Maybe you'll need netlogon too. The share is already set in smb.conf, just uncomment it.

There is many other paramters, but anyway this is enough to make it works. If you google for 'samba pdc' you'll find a lot of help.

---

### Post by Akita on 2007-01-07
Comlete how-to for a small workgroup server: [http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")

---

### Post by mikemaggio on 2007-01-07
How to you get samba? I've been following the directions in thes SAMBA Server for Small Workgroups document and when I exectute this command

apt-get install samba samba-common samba-doc libcupsys2-gnutls10 libkrb53 winbind smbclient

I get these results:

Reading package lists... Done
Building dependency tree... Done
Package winbind is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package winbind has no installation candidate

---

### Post by Akita on 2007-01-07
It's there on my Edgy box - perhaps you need the Universe repositories for it or something it depends on.

---

### Post by Koybe on 2007-01-08
You do not need winbind unless you want to connect to a Windows Domain Controler.

---

### Post by mikemaggio on 2007-01-08
OK. How do I know that it is working properly? How do I know that it is acting as a DNS server and a DC? My other PCs are all using XP Home. How do I get them to log on to the domain?

Also, when I gave each a static IP and plugged in the IP of the ubuntu box as the dns server, I could not longer connect to the internet.

---

### Post by echo $USER on 2007-01-10
> **mikemaggio said:**
> OK. How do I know that it is working properly? How do I know that it is acting as a DNS server and a DC? My other PCs are all using XP Home. How do I get them to log on to the domain?

Also, when I gave each a static IP and plugged in the IP of the ubuntu box as the dns server, I could not longer connect to the internet.

XP Home can't belong to a domain, only woekgroups.  You will need all the MS clients running Pro.

---

### Post by sliwowitz on 2007-01-12
Hello everyone. Forst of all, I want to thank all of you you for quick help. I now have domain logons almost perfectly working.
The only trouble is, I am unable to properly set up roaming profiles. One of the users called "host" (which means "guest" in Czech) is able to login without any warnings. Other users (so far "administrator" and "badcat") get error on login saying (in Czech) that Windows can't find server copy of the roaming profile and tries to login using local profile (and fails doing this, for there are no local profiles set). The "host" user logs in without warning, but apparently stores profile locally - when I login from other workstation, no changes made to the desktop etc. are visible. There seem to be no files or directories created on the server no matter what I do on the workstations.
What have I done so far: ([see my smb.conf]("http://public.toh.cz/smb.conf"))
- configured [profiles] section as advised
- made empty word-writable /home/samba/profiles folder
- copied "Default User" profile to /home/samba/netlogon
- set that group policies thing in gpedit.msc on workstations
- ](*,) banged my head against the wall at least ten times

---

### Post by herzzreh on 2007-01-24
> **sliwowitz said:**
> Hello everyone. Forst of all, I want to thank all of you you for quick help. I now have domain logons almost perfectly working.
The only trouble is, I am unable to properly set up roaming profiles. One of the users called "host" (which means "guest" in Czech) is able to login without any warnings. Other users (so far "administrator" and "badcat") get error on login saying (in Czech) that Windows can't find server copy of the roaming profile and tries to login using local profile (and fails doing this, for there are no local profiles set). The "host" user logs in without warning, but apparently stores profile locally - when I login from other workstation, no changes made to the desktop etc. are visible. There seem to be no files or directories created on the server no matter what I do on the workstations.
What have I done so far: ([see my smb.conf]("http://public.toh.cz/smb.conf"))
- configured [profiles] section as advised
- made empty word-writable /home/samba/profiles folder
- copied "Default User" profile to /home/samba/netlogon
- set that group policies thing in gpedit.msc on workstations
- ](*,) banged my head against the wall at least ten times

Hi,

I have the same issue. I get an error that windows cannot locate network profile, "network name not found" and then it just loads the local temp profile.

Have you found a resolution?

---

### Post by Koybe on 2007-01-27
Not sure, but think you should double backslases in your smb.conf.
>     logon path = \\%L\profiles\%U
    logon drive = H:
    logon home = \\%L\%U

And... Are you stil using winbind for something? Otherwise you don't need these : 
> 	idmap uid = 15000-20000
	idmap gid = 15000-20000

---

### Post by sliwowitz on 2007-02-02
Yes, it was the double backslashes. I can't believe I missed them :oops: 
Now everything seems to work. The only trouble is, that all workstations contain a lot of mess from local profiles I have to clean. This is gonna be a long weekend...
Again thanks everyone for help :-)

---

### Post by meomike2000 on 2007-02-02
> **echo $USER said:**
> XP Home can't belong to a domain, only woekgroups.  You will need all the MS clients running Pro.

under
[global]
You can add the line 
workgroup="enter the windows workgroup name here"

this will basicly tell samba it is part of the workgroup, this should work,,,,,,,,,I think maybe
has worked for me so far

---

### Post by bigun on 2007-02-13
> **echo $USER said:**
> XP Home can't belong to a domain, only woekgroups.  You will need all the MS clients running Pro.

Actually... XP Home can join a domain...
[http://vowe.net/archives/001639.html]("http://vowe.net/archives/001639.html")

Follow the link and use x-setup.

---

