---
title: "Help with simple samba configuration"
date: 2017-09-23
forum: Server Platforms
---

### Post by warofdevil90 on 2017-09-23
Hi guys, I am new to the Ubuntu family and I have been struggling to configure samba.  OS: Ubuntu Server 16.04 - Kernel 4.13, Samba version: 4.3.11

GOAL: What I want to achieve is the following: My server has to expose two directory, those will be reachable by my family using Windows 10 machines and OSX. 

1) Share: I want it to be public, everybody can connect to it without password and can rwx files. The files on the server are saved with user group warofdevil:sambashare in mode 770. The reason because warofdevil is my main user on the server, and I want to be able to manipulate those files if needed.

2) Legacy: I want it to be private, and to be accessible only by me using password. Also here files should be saved on the server with u:g warofdevil:sambashare in mode 770.

3) RecycleBin: Not visible and not browsable. When user delete a file, the file will go in the trashbin under a folder created for every single username.

That is the smb.conf that I have created so far:

```

# WarOfDevil SAMBA configuration
#
# NOTE: "testparm" to check syntax errors

#===========GLOBAL SETTINGS==============
[global]
workgroup = WORKGROUP
log file = /var/log/samba/log.%m
panic action = /usr/share/samba/panic-action %d
server string = Samba DevilServer
netbios name = devilserver
security = user
encrypt passwords = true
#username map = /etc/samba/smbusers
map to guest = bad user
guest account = nobody
dns proxy = no

force user = warofdevil
force group = sambashare

#========RECYCLE BIN====================
vfs object = recycle
recycle:repository = /mnt/raid5/Share/recyclebin/%U
recycle:touch = Yes
recycle:keeptree = Yes
recycle:versions = Yes
recycle:noversions = *.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
recycle:exclude = *.tmp,*.temp,*.o,*.obj,~$*,*.~??,~*.*,*.TMP,*.TEMP,lock.*,.~lock.*,LOCK.*,*.lock,*.~lock,*.LNK,*.lnk,*.ldb
recycle:excludedir = /recyclebin,/tmp,/temp,/TMP,/TEMP

[RecycleBin]
path = /home/user1/Shares/recyclebin
browsable = no
public = no
writable = yes

#==========SHARES DEFINITION=============
[Share]
comment = Guest Users Network Share
path = /mnt/raid5/Share/guest_share
browsable = yes
guest ok = yes
writeable = yes
force create mode = 0770
force directory mode = 0770
create mask = 0660
directory mask = 0770

[Legacy]
comment = Private Network Share
path = /mnt/raid5/Share/legacy
browsable = yes
guest ok = no
read list = warofdevil
write list = warofdevil

```

The problem of the current configuration is: On Windows if I click on my server, it will ask a password for both Share and Legacy. And anyway the password that I have set for my user doesn't work anyway. For my warofdevil user on my server I did set a password with smbpassword to be 12345, and if I type that on windows doesn't work.
Can someone please help me?

---

### Post by Morbius1 on 2017-09-23
I think I'm going to have to try and reproduce your setup when I get time to give your question justice but I'd like to point out some logical errors:
> [Share]
comment = Guest Users Network Share
path = /mnt/raid5/Share/guest_share
browsable = yes
guest ok = yes
writeable = yes
[B][COLOR=#0000cd]force create mode = 0770
force directory mode = 0770
create mask = 0660
directory mask = 0770[/COLOR][/B]
[COLOR=#000000]You really don't need the highlighted areas and you really don't need the "force group = sambashare" because everyone is being converted to [/COLOR]warofdevil ( force user = 
warofdevil).
> [Legacy]
comment = Private Network Share
path = /mnt/raid5/Share/legacy
browsable = yes
guest ok = no
[COLOR=#0000cd][B]read list = warofdevil
write list = warofdevil[/B][/COLOR]
You can't have read / write list and force user in the same configuration because everyone who passes the credentials phase of accessing that share is the forced user. If you want to make the share accessible only to warodevil then use "valid users":
> [Legacy]
comment = Private Network Share
path = /mnt/raid5/Share/legacy
browsable = yes
guest ok = no
[COLOR=#0000cd]**valid users = warofdevil**[/COLOR]
"valid users" and "force user" can be used together because they happen at different times. "valid users" when you try to access the share and "force user" after his credentials are accepted.
> RecycleBin: Not visible and not browsable. When user delete a file, the  file will go in the trashbin under a folder created for every single  username.
I'll admit I only used the recycle bin capability once a while ago but I don't think it will do what you want because everyone is forced to be warodevil.

At the moment Samba not accepting the smbpasswd for the Win10 user has me confused. Does Win10 just comeback to prompting you for credentials or is there a more involved error message?

---

### Post by warofdevil90 on 2017-09-23
> **Morbius1 said:**
> 
I'll admit I only used the recycle bin capability once a while ago but I don't think it will do what you want because everyone is forced to be warodevil.

At the moment Samba not accepting the smbpasswd for the Win10 user has me confused. Does Win10 just comeback to prompting you for credentials or is there a more involved error message?

For the recycle bin it works with that configuration (before I started implementing the Legacy folder). So if my brother on windows access Share and delete a file, on my server I will find a folder with his windows-username and the deleted file. 

The problem is after I have implemented the Legacy folder I can't access anything. Basically now If click on Computer -> Network, and I double click on the server hostname, windows will ask for a password for both Share and Legacy. (Before that it didn't ask any passoword for Share). And anyway if I type user: warofdevil, password: 12345, windows doesn't let me log-in. It complain that the password is not correct and the user is already logged in.

---

### Post by Morbius1 on 2017-09-23
> And anyway if I type user: warofdevil, password: 12345, windows doesn't  let me log-in. It complain that the password is not correct and the user  is already logged in.         
Is warofdevil the login user name of the Win10 user? On the Win10 system itself? Or is it something else?

[COLOR=#0000cd]**Edit**[/COLOR]: Another way to ask the question. Run this command on Ubuntu:
```
 sudo smbstatus
```
When Win10 complains that you are already logged in, the above command should tell you as who?

---

### Post by warofdevil90 on 2017-09-23
> **Morbius1 said:**
> Is warofdevil the login user name of the Win10 user? On the Win10 system itself? Or is it something else?

[COLOR=#0000cd]**Edit**[/COLOR]: Another way to ask the question. Run this command on Ubuntu:
```
 sudo smbstatus
```
When Win10 complains that you are already logged in, the above command should tell you as who?

No the login username of win10 is vinko. Btw now windows accept the password, but it ask for it right when I double click on the hostname of the server, and then it shows Legacy and Share folders, and that's not what I want. 

Samba version 4.3.11-Ubuntu
PID     Username      Group         Machine            Protocol Version
------------------------------------------------------------------------------
16031     warofdevil    warofdevil    10.0.0.53    (ipv4:10.0.0.53:50840) Unknown (0x0311)

Service      pid     machine       Connected at
-------------------------------------------------------
Share        16031   10.0.0.53     Sat Sep 23 18:13:01 2017
Legacy       16031   10.0.0.53     Sat Sep 23 18:12:32 2017
IPC$         16031   10.0.0.53     Sat Sep 23 18:12:29 2017

Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
16031        1000       DENY_NONE  0x100081    RDONLY     NONE             /mnt/raid5/Share/legacy   .   Sat Sep 23 18:13:17 2017
16031        1000       DENY_NONE  0x100081    RDONLY     NONE             /mnt/raid5/Share/legacy   .   Sat Sep 23 18:13:17 2017

---

### Post by Morbius1 on 2017-09-23
I reproduced your smb.conf on a test box - the way you had originally set up your shares but without the Recycle Bin and I cannot reproduce your symptoms.

I set this up in stages just like you did with a public share first and I can access that share from Win10 without passing credentials:
> tester@vub-16041:~$ sudo smbstatus

Samba version 4.3.11-Ubuntu
PID     Username      Group         Machine             
---------------------------------------------------
2544      nobody        nogroup       192.168.1.208

Service      pid     machine     
---------------------------------
IPC$         2544   192.168.1.208
Share        2544   192.168.1.208 

When I then set up the private share I am prompted for credentials - at the share level not the host level:
> tester@vub-16041:~$ sudo smbstatus

Samba version 4.3.11-Ubuntu
PID     Username      Group         Machine          
----------------------------------------------------
2558      tester        tester        192.168.1.208 

Service      pid     machine       
---------------------------------
Legacy       2558   192.168.1.208 

At the moment I do not know how to explain your symptoms..

---

### Post by warofdevil90 on 2017-09-24
Then I have no idea where is the problem :(

Would it be better to install webmin to configure samba? Or are there any other alternatives to configure samba over a webpage for example?

---

### Post by Morbius1 on 2017-09-24
Webmin has no intelligence in it that would prevent you from doing something goofy. It just makes it easier to accomplish it. 

I think I found a scenario that matches at least one of your symptoms.

** I created a local user on Win10 named tester1 with a local win10 password of tester01.

** I then created the same user on my Ubuntu box.

** Then I added that user to the samba database ( smbpasswd ) giving it the same password as the Windows user - tester01

When I access the Public share I am not prompted for a password - either at the host level or the share level. 

** Then I changed the samba password to tester11.

When I access the host I'm confronted with an error:
[ATTACH=CONFIG]276834[/ATTACH]
Windows automatically sends the current users local user name and password when it makes contact with a server. If the samba server has the same user name and a samba password that matches the Windows users login password then credentials are accepted even though you may be accessing a public share. Change the samba password so that it doesn't match the windows users login password and that user will get prompted for just accessing the host.

If I go back to ubuntu and change the samba password back to the Windows users login password everything works again.

---

### Post by warofdevil90 on 2017-09-24
> **Morbius1 said:**
> Webmin has no intelligence in it that would prevent you from doing something goofy. It just makes it easier to accomplish it. 

I think I found a scenario that matches at least one of your symptoms.

** I created a local user on Win10 named tester1 with a local win10 password of tester01.

** I then created the same user on my Ubuntu box.

** Then I added that user to the samba database ( smbpasswd ) giving it the same password as the Windows user - tester01

When I access the Public share I am not prompted for a password - either at the host level or the share level. 

** Then I changed the samba password to tester11.

When I access the host I'm confronted with an error:
[ATTACH=CONFIG]276834[/ATTACH]
Windows automatically sends the current users local user name and password when it makes contact with a server. If the samba server has the same user name and a samba password that matches the Windows users login password then credentials are accepted even though you may be accessing a public share. Change the samba password so that it doesn't match the windows users login password and that user will get prompted for just accessing the host.

If I go back to ubuntu and change the samba password back to the Windows users login password everything works again.

Thanks a lot!!! I did exactly what you did and now it works perfectly :)

---

