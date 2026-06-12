---
title: "Likewise Integration with AD?"
date: 2008-04-24
forum: Server Platforms
---

### Post by johnwillis on 2008-04-24
Hi everyone,

Not sure if this is something I'm doing wrong but when I want to join my hardy machine onto a windows 2003 network I can "join" the domain but then I cannot use my login credentials from windows on my hardy install?

What am I doing wrong? Are there any further steps needed? 

Also how would I get a Ubuntu workstation to log on directly from the login screen to a terminal server? (For example edubuntu)

Many thanks guys,

J

---

### Post by inselaffe on 2008-04-24
I just gave it a bash, and was able to logon immediately without doing anything else as a domain user by entering the username in this format:
domain\user

Not sure about passthrough logon to a terminal server. The newer RDP protocol version 6 features network level authentication, but I don't think there is a Linux client implementation.

---

### Post by johnwillis on 2008-04-24
That is what i did wrong.

I forgot to put in the DOMAIN\ before my user name

Is it possible to have this filled in automatically do you know. So if i use 'john' it will use KINGSNORTONGIRL\john?

Other than that it seems to work well.

I'm trying to get our school to invest in some new workstations running Ubuntu and Openoffice.org!

So far I've got them running Joomla - [www.kngs.co.uk](www.kngs.co.uk) , Moodle [www.kngs.co.uk/moodle](www.kngs.co.uk/moodle) and we're also using other open source software for our helpdesk, live support as well as other tasks.

My backup server is also running Linux.

So with a bit of luck we'll convert them to Linux yet! :)

Ubuntu 8.04 seems a vast improvement in my opinion. A little buggy with my NVIDIA drivers, but other than that. Good solid distro.

Thanks for your help.

-J

---

### Post by gtdaqua on 2008-04-25
> **johnwillis said:**
> That is what i did wrong.

I forgot to put in the DOMAIN\ before my user name

Is it possible to have this filled in automatically do you know. So if i use 'john' it will use KINGSNORTONGIRL\john?

Other than that it seems to work well.



No, domain\username is the standard format. Just username means you are logging on locally and not through the directory! Active Directory is a fantastic concept for centralized control and audit. You can also try username@domain but admins prefer the good ole domain\username format

> **johnwillis said:**
> 
I'm trying to get our school to invest in some new workstations running Ubuntu and Openoffice.org!

Ubuntu 8.04 seems a vast improvement in my opinion. A little buggy with my NVIDIA drivers, but other than that. Good solid distro.

Thanks for your help.

-J

NVIDIA ones are the simplest to compile and install in Ubuntu Flavours - although you have to reinstall the drivers everytime the kernel is updated (which is once in a while)

---

### Post by rcasha on 2008-04-29
> **johnwillis said:**
> That is what i did wrong.

I forgot to put in the DOMAIN\ before my user name

Is it possible to have this filled in automatically do you know. So if i use 'john' it will use KINGSNORTONGIRL\john?


Yes. From what I can see, Likewise is nothing more than Samba+Kerberos under the hood - what they seem to provide is a nice, simple interface for it - which is way better than the loads of files and config options required before.

So... If you go to the file /etc/samba/lwiauthd.conf and add the line:
```
winbind use default domain = yes
```
...it should work as you describe. Just make sure that you don't have the same username as both a local and an ADS user to avoid conflicts. 

This file is a regular smb.conf file - but do be careful - the idea of likewise is that the user should be kept away from config files.

---

### Post by commonplace on 2008-05-07
> **rcasha said:**
> So... If you go to the file /etc/samba/lwiauthd.conf and add the line:
```
winbind use default domain = yes
```
...it should work as you describe. Just make sure that you don't have the same username as both a local and an ADS user to avoid conflicts.


If you make this change, how can you specify that you WANT to login as a local user instead of an ADS user, should the need/desire arise? Would "username@localhost" as the user name work, assuming 'username' is a valid local user name?

/Kevin

---

### Post by rcasha on 2008-05-07
Ideally, you should have different usernames on the AD server and local machine. If I'm not mistaken (the ADS machine is at another place), your PAM files are configured to look up first one then the other.

I believe it is possible, using the useradd command, to add a user with the same uid/gid and home directory as another user, though I haven't tried it. So you could create a user "local_joe" to complement ADS\joe

---

### Post by Mr_Whippy on 2008-05-08
If it works the same as a windows logon which from what you are saying it looks like it does, as long as your domain username is different to your local username you will have no issues, as someone said earlier, the pc will check the domain first then the local machine for credentials.

---

### Post by johnwillis on 2009-04-22
Sorry to drag up and old topic but one thing I haven't been able to figure out is how to map a folder on the desktop (like a mounted SMB share) of the users home folder that is specified in Active Directory?

Has anyone achieved this and how?

Many thanks in advance...

---

### Post by bjk03 on 2009-06-03
> **johnwillis said:**
> Sorry to drag up and old topic but one thing I haven't been able to figure out is how to map a folder on the desktop (like a mounted SMB share) of the users home folder that is specified in Active Directory?

Has anyone achieved this and how?

Many thanks in advance...

I too would like to do this. Any help is greatly appreciated.

---

