---
title: "SAMBA4 as domain controller problems"
date: 2014-01-21
forum: Server Platforms
---

### Post by CappyT on 2014-01-21
Hi everyone, this is my very first post so I hope I'm not in the wrong section...

I have a problem with samba4 as dc.
I'm really new to samba and either to domains.
I searched the web long time and I finally managed to install samba4 as dc, right on this forum.

[http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)

I have now a problem.. How to add new users to samba (both for activesync and share)? The only working account is administrator, which is obviusly the domain admin.

My configuration is 1:1 like the guide says. I didn't touch a line.

Thanks to everybody who will reply.
CappyT

---

### Post by JnPson on 2014-01-22
You can use AD Users and computers from any windows client that is a member of the domain. If you don't have it on any client you either install adminpak for Windows xp or RSAT for Windows 7.

---

### Post by CappyT on 2014-01-22
> **JnPson said:**
> You can use AD Users and computers from any windows client that is a member of the domain. If you don't have it on any client you either install adminpak for Windows xp or RSAT for Windows 7.

What is AD and how it works?
Also... How to install?

---

### Post by CappyT on 2014-01-22
> **JnPson said:**
> You can use AD Users and computers from any windows client that is a member of the domain. If you don't have it on any client you either install adminpak for Windows xp or RSAT for Windows 7.

OK, figured out that AD means Active Directory, the problem is that when I try to add a User to dc with samba-tool this user can't login on the domain...

---

### Post by access1denied on 2014-01-23
I am new to this as well; however, be that you haven't received an answer... I hope what I have done will help.  I presumed you have tested your domain from Linux and it is working... also, I presume you have connected a windows xp computer to the dc.  if you are using windows 7, do the following: go to Control Panel
Click on programs
Click on "Turn Windows features on or off"
look for "Remote Server Administration Tools" and install it.

If you are using Windows Xp, search the web for "adminpak windows xp" you will get a Microsoft link to download adminpak for server 2003 and XP... download and install it.  

Once you have completed the installation of either admin tool on the PC that is connected to the DC... open up Active Directory Users and Computers... click on the plus sign next to your domain, then right click on the Users folder >>New >>User.

Hope that is what you need...

---

### Post by JnPson on 2014-01-24
You are talking about creating users on your new DC and there are two ways of doing that, (if there are more plz forgive my ignorance).
 One way is to use Active Directory Users and Computers, the other way is using samba-tool.   


 I was under the impression that you was new to Samba, but you created a user with samba-tool, which is good. AD UaC is the easier way of doing that.  


 How are the user trying to log on to the computer? Is he/she logging on through interactive remote desktop or directly on to the computer?
 If he/she is loggin on with remote desktop I think you have to add the new user to a group with interactive logon rights.  
 You created the user with  
 ```
samba-tool user add <username> <password>


``` now you have to add the user to a group with
 ```
samba-tool group addmembers <groupname> <user>

```
I'm not sure what default groups have that interactive right though. 

I hope this will help a little.

---

### Post by CappyT on 2014-01-27
> **JnPson said:**
> You are talking about creating users on your new DC and there are two ways of doing that, (if there are more plz forgive my ignorance).
 One way is to use Active Directory Users and Computers, the other way is using samba-tool.   


 I was under the impression that you was new to Samba, but you created a user with samba-tool, which is good. AD UaC is the easier way of doing that.  


 How are the user trying to log on to the computer? Is he/she logging on through interactive remote desktop or directly on to the computer?
 If he/she is loggin on with remote desktop I think you have to add the new user to a group with interactive logon rights.  
 You created the user with  
 ```
samba-tool user add <username> <password>


``` now you have to add the user to a group with
 ```
samba-tool group addmembers <groupname> <user>

```
I'm not sure what default groups have that interactive right though. 

I hope this will help a little.

Ok, users can now login correctly, domain is OK and everything (except permission and samba shares) is working as intended.
I was forced to use "force user = samba" in the config, otherwise I got only read for all users (except for the creator. Tried chmod 777 and also use create mode 0777, still only read)

Now I need to setup this groups: domain admins, domain superusers, domain users, domain guest
I also need to be able to add this groups to some shares in samba and assign permission to write folders or not.

So, how I must proceed?

---

### Post by JnPson on 2014-01-28
If you are using the samba-tool you can list all different commands with 
```
samba-tool group -h
```

To see all available domain groups:
```
samba-tool group list
```
From there you can add members with 
```
samba-tool group addmembers <groupname> <username>
```

There may be other ways of doing that in the terminal but this is how I would do it.

---

