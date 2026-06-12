---
title: "HowTo: Ubuntu 10.04 Samba Primary Domain Controller with LDAP"
date: 2010-06-02
forum: Tutorials
---

### Post by bulletxt on 2010-06-02
Sorry, I have decided to rewrite this manual as it was incomplete in some areas, including roaming profiles and so on. It also had some errors.

I will update it soon.

---

### Post by ricpelo on 2010-06-17
Hi, bulletxt! Excellent post. All works flawless, like a charm :).

Only one question: Is there a way to have roaming profiles enabled with this config? I have a classroom of 30 client PCs and I would like to have that option available, so the students can sit on any PC and get all their docs and configuration available.

Thanks very much in advance.

---

### Post by bulletxt on 2010-06-17
> **ricpelo said:**
> Hi, bulletxt! Excellent post. All works flawless, like a charm :).

Only one question: Is there a way to have roaming profiles enabled with this config? I have a classroom of 30 client PCs and I would like to have that option available, so the students can sit on any PC and get all their docs and configuration available.

Thanks very much in advance.

Hi, I'm sorry but I'm not sure how to enable roaming profiles, and I really don't have the time now to test it. Taking a wild guess, I'm quite sure you'll have to modify smb.conf at "logon home" and "logon path". Something similar must be done in /etc/smbldap/smbldap.conf

If you find how to do it, please share it and I'll put it in main thread!

---

### Post by ricpelo on 2010-06-17
> **bulletxt said:**
> Hi, I'm sorry but I'm not sure how to enable roaming profiles, and I really don't have the time now to test it. Taking a wild guess, I'm quite sure you'll have to modify smb.conf at "logon home" and "logon path". Something similar must be done in /etc/smbldap/smbldap.conf

If you find how to do it, please share it and I'll put it in main thread!

Hi. Thank you very much for the answer. I'm trying to enable the roaming profiles, but without luck. The WinXP client refuses to load the profile during the logon and displays an error message like "Windows cannot locate the server copy of your roaming profile...". I've tried with:

logon drive = H:
logon home = \\%N\%U
logon path = \\%N\%U\profile
logon script = logon.cmd

as well as:

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /var/lib/samba/profiles
        read only = No
        profile acls = Yes
        browsable = No

I can't see where's the point. Any clues?

Cheers,

Ricardo.

---

### Post by bulletxt on 2010-06-17
Try this, put it inside [netlogon] :

logon path = \\$netbios\profiles\%U

Replace $netbios with your netbios= set in smb.conf

---

### Post by SonicSteve on 2010-06-17
Is there a way that you know of to integrate a samba domain controller into a network running Active Directory? I've been wanting to do this for some time. I understand that Samba 4 might help with this but in the mean time I've been looking.

I have a network with 4 AD servers running Win2k3 server, and 140 workstations. Instead of adding yet another AD server I've been wanting to add a linux box with a share that the windows boxes will be able to access.

---

### Post by bulletxt on 2010-06-17
Give a look at this: [https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html)

---

### Post by SonicSteve on 2010-06-17
I'll give that a try. I don't see where the ubuntu box is getting it's AD information from but hopefully I can try soon.

Thanks.

---

### Post by ricpelo on 2010-06-18
> **bulletxt said:**
> Try this, put it inside [netlogon] :

logon path = \\$netbios\profiles\%U

Replace $netbios with your netbios= set in smb.conf

Thanks, but it doesn't work, sorry :(. I've got the same error message in my WinXP client.

This is an excerpt of what I have inside my smb.conf:

```

[netlogon]
    comment = Network Logon Service
    path= /var/lib/samba/netlogon
    admin users = root
    guest ok = Yes
    browseable = No
    logon drive = H:
    logon script = logon.cmd
    logon home = \\%N\%U
    logon path = \\%N\profiles\%U

[profiles]
    comment = Roaming Profile Share
    path = /var/lib/samba/profiles
    read only = No
    profile acls = Yes
    browsable = No

```

Both /var/lib/samba/netlogon and /var/lib/samba/profiles exist and have a chmod 777. May I miss something?

---

### Post by pcmb8866 on 2010-06-19
Try this
In Global section
logon script = logon.cmd
logon path = \\%L\profiles\%U\%m
logon drive = H:
logon home = [\\%L\%U\.win_profile\%m]("file://\\%L\%U\.win_profile\%m")      (for old windows version, 98)
 
[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
write list = @"Domain Admins"
guest ok = Yes
 
[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
profile acls = Yes
browseable = No
 
This works for me!

---

### Post by bulletxt on 2010-06-19
Thanks pcmb8866.  If someone confirms his method works I'll add it to main thread!

---

### Post by ricpelo on 2010-06-19
> **pcmb8866 said:**
> Try this
In Global section
logon script = logon.cmd
logon path = \\%L\profiles\%U\%m
logon drive = H:
logon home = [\\%L\%U\.win_profile\%m]("file://\\%L\%U\.win_profile\%m")      (for old windows version, 98)
 
[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
write list = @"Domain Admins"
guest ok = Yes
 
[profiles]
comment = Profile Share
path = /var/lib/samba/profiles
read only = No
profile acls = Yes
browseable = No
 
This works for me!

Sorry, I'm unable to reproduce your success :(. I still get an error message like "Windows cannot locate the server copy of your roaming profile..." from my WinXP client, because it's unable to get the profile from the server.

Could you please tell me the exactly steps you followed in order to get your server working? (an step-by-step howto similar to the bulletxt's one would be very very helpful).

Until now, what I did was to follow the bulletxt's howto from start to end, and then I changed the smb.conf according to your information. May I need to do something more?

Thank you very much in advance.

---

### Post by pcmb8866 on 2010-06-20
You have to make a little change to your smbldap.conf file.
Change according to the following:
For adding new users:
userSmbHome=""
userProfile=""
userHomeDrive=""
userScript=""
 
For existing users enter your ldap-server, e.g. with LDAP Admin.
Edit users and empty:
sambahomedrive
sambahomepath
sambalogonscript
sambaprofilepath
 
This should do the job.

---

### Post by ricpelo on 2010-06-20
> **pcmb8866 said:**
> You have to make a little change to your smbldap.conf file.
Change according to the following:
For adding new users:
userSmbHome=""
userProfile=""
userHomeDrive=""
userScript=""
 
For existing users enter your ldap-server, e.g. with LDAP Admin.
Edit users and empty:
sambahomedrive
sambahomepath
sambalogonscript
sambaprofilepath
 
This should do the job.

Great! Now it works! :guitar:

After editing the smbldap.conf, I then created a new user using smbldap-useradd, and now it works perfectly!

For the record, I change your **logon path** and **logon home** in *smb.conf* a little bit:

```

logon home = \\%N\%U
logon path = \\%N\%U\profile

```

so now the roaming profile is stored under the user's home directory. Works great :).

Thank you very much!

---

### Post by pcmb8866 on 2010-06-20
> **ricpelo said:**
> Great! Now it works! :guitar:
 
After editing the smbldap.conf, I then created a new user using smbldap-useradd, and now it works perfectly!
 
For the record, I change your **logon path** and **logon home** in *smb.conf* a little bit:
 
```

logon home = \\%N\%U
logon path = \\%N\%U\profile

```
 
so now the roaming profile is stored under the user's home directory. Works great :).
 
Thank you very much!
 
I have to use the %m (machine) variable because i have different laptops, some with winXP and some with Win7. They have different profiles.
So the profile of a user is stored under profiles\username\machinename.
 
BTW, using your logon path a user can change or delete his/her entire profile. Is a bit dangerous, isn't it!
Anyway. At logout his/her profile is stored again, accept when the machine is powered off.
 
Good luck!

---

### Post by nixnotwin on 2010-06-21
I wanted to have home directories auto-mounted at login so I did the following in smb.conf

```
logon drive = q:
logon home = \\%N\%U 
```
It's working fine. Do I have to do anything else?

As for roaming profile, it worked for me without any changes. I just did what bulletxt had written in the first post, and tried to login from different xp machines with a single user name and it just worked. 

  In my network just for a single group  I want to map and mount a commonly shared directory and home directory, while for other groups I just want home directory to be mapped. Any suggestions?

---

### Post by pcmb8866 on 2010-06-21
> **nixnotwin said:**
> I wanted to have home directories auto-mounted at login so I did the following in smb.conf
 
```
logon drive = q:
logon home = \\%N\%U 
```
It's working fine. Do I have to do anything else?
 
As for roaming profile, it worked for me without any changes. I just did what bulletxt had written in the first post, and tried to login from different xp machines with a single user name and it just worked. 
 
In my network just for a single group I want to map and mount a commonly shared directory and home directory, while for other groups I just want home directory to be mapped. Any suggestions?
 
You can make as many groups as you like in ldap. Add these groups to your different shares. E.g. group games to share games. Then add users to the desired group.
In netlogon you can then make some scripts checking groupmembership and then mount the share with that group.
A very easy script programm, and free, is kixtart.

---

### Post by nixnotwin on 2010-06-22
Thanks, pcmb8866.

I was trying to setup quota for home directories, and I followed this guide [http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny](http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny)

I don't have fdd and cd drive so i just modified entry for / in fstab file. And when I run 
```
sudo quotacheck -avugm
```I get this error

```
quotacheck: WARNING -  Quotafile //aquota.user was probably truncated. Cannot save quota settings...
quotacheck: WARNING -  Quotafile //aquota.group was probably truncated. Cannot save quota settings...
quotacheck: Scanning /dev/sda9 [/] quotacheck: lstat Cannot stat `//home/user11/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...
```The command
```
sudo quotaon -avug
``` gives this error
```

quotaon: Cannot find quota file on / [/dev/sda9] to turn quotas on/off.
quotaon: Cannot find quota file on / [/dev/sda9] to turn quotas on/off.
```Any suggestions are welcome :confused:

---

### Post by dslink on 2010-06-22
it's really great to see a document like this already done for the latest release.

---

### Post by pcmb8866 on 2010-06-22
> **nixnotwin said:**
> Thanks, pcmb8866.
 
I was trying to setup quota for home directories, and I followed this guide [http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny](http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny)
 
I don't have fdd and cd drive so i just modified entry for / in fstab file. And when I run 
```
sudo quotacheck -avugm
```I get this error
 
```
quotacheck: WARNING -  Quotafile //aquota.user was probably truncated. Cannot save quota settings...
quotacheck: WARNING -  Quotafile //aquota.group was probably truncated. Cannot save quota settings...
quotacheck: Scanning /dev/sda9 [/] quotacheck: lstat Cannot stat `//home/user11/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...
```The command
```
sudo quotaon -avug
``` gives this error
```

quotaon: Cannot find quota file on / [/dev/sda9] to turn quotas on/off.
quotaon: Cannot find quota file on / [/dev/sda9] to turn quotas on/off.
```Any suggestions are welcome :confused:
 
I'm not using quota, but installed it anyway with guide:
[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p4)
 
aptitude install quota quotatool
 
Changed my fstab to:
```

# /home was on /dev/md6 during installation
UUID=a3a1d213-afca-4aab-ab34-98d9a730a09c /home ext4 defaults,,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0 2

```
Then to enable quota:
```
touch /home/aquota.user /home/aquota.group
chmod 600 /home/aquota.*
mount -o remount /home
```
```
quotacheck -avugm
quotaon -avug
```
 
Then I use quotatool to set a per user quota.
 
That's it. All went well.

---

### Post by nixnotwin on 2010-06-23
Thanks I was able to track down the issue. It is a bug. I use ubuntu desktop. The file /home/user11/.gvfs is a gnome file. It stops disk check command. I rebooted, went into recovery mode (root-shell) and issued quotacheck -avugm command and it worked. When I issued '[FONT=monospace]quotaon -avug' command I got this output
[/FONT]```
 
quotaon: using //aquota.group on /dev/sda9 [/]: Device or resource busy
quotaon: using //aquota.user on /dev/sda9 [/]: Device or resource busy
```
Then I created a group and added a user to the group with these commands

```
sudo smbldap-useradd -a -m -P user20
sudo smbldap-groupadd group2
sudo smbldap-groupmod -m 'user20' 'group2'
sudo auth-client-config -t nss -p lac_ldap
```After that I went into webmin diskquota configuration page, and  set disk space soft-limit and hard-limit to 300 and files soft-limit and hard-limit to 300 as well for the user group2. And I copied a 50 mb file onto user20's home folder and it got copied. Then I tried a 1 GB file and it also got copied. Something must have gone wrong. Any idea how can I troubleshoot the issue. I don't have a separate parttion for /home, my /home is in root partition.

---

### Post by pogztimz on 2010-06-23
this is freakin awesome.. i will try this in our computer laboratory in the next few weeks. i've been using rickyjones' guide [http://ubuntuforums.org/showthread.php?t=640760&highlight=OpenLDAP+Samba+Domain+Controller]("http://ubuntuforums.org/showthread.php?t=640760&highlight=OpenLDAP+Samba+Domain+Controller") for almost 3 years now and it worked flawless for winXP and ubuntu clients.. but now i have to try it on Win 7.. thnks...:guitar:

---

### Post by joseph.attard on 2010-06-23
> **pcmb8866 said:**
> You can make as many groups as you like in ldap. Add these groups to your different shares. E.g. group games to share games. Then add users to the desired group.
In netlogon you can then make some scripts checking groupmembership and then mount the share with that group.
A very easy script programm, and free, is kixtart.

[COLOR=Red]
** I got the roaming profile to work but how do I get the users share to mount? I also want to mount the shared folder, I had that one working before by the following way:**[/COLOR]

**To make your PDC automatically map net drives:**
-> apt-get install flip
->  > /var/lib/samba/netlogon/allusers.bat
In this example you'll have a shared folder for all users, of course you  can edit /etc/samba/smb.conf to create specific user shares.
-> mkdir -p /var/lib/samba/shared/
-> chmod -R 777 /var/lib/samba/shared/
-> nano /var/lib/samba/netlogon/allusers.bat
NOTE: change "PSAMBA" with the Netbios name set in step 9. Change drive  "m:" to any letter you prefer.
     Quote:
                                                 @echo off
net use m: /delete
net use m: "\\PSAMBA\shared"                                 
-> flip -m /var/lib/samba/netlogon/allusers.bat


[B][COLOR=Red]Also I can only only connect to LDAPAdmin anonymously, why is that?  (BASE: dc=pdc)
Do i have to go down to the users hierachy?[/COLOR][/B]

---

### Post by pcmb8866 on 2010-06-23
> **joseph.attard said:**
> **[COLOR=red]Also I can only only connect to LDAPAdmin anonymously, why is that? (BASE: dc=pdc)[/COLOR]**
**[COLOR=red]Do i have to go down to the users hierachy?[/COLOR]**
 
You have to setup your LDAP server as in BULLETXT tutorial to the letter. This is till now the best I have ever seen. 
**[COLOR=magenta]BULLETXT GREAT JOB[/COLOR]**\\:D/
 
A special notice about the password. This has to be everywhere the same.
This weekend I will post my setup about mounting shares to users checking their membership in LDAP.
 
Right now I have some trouble installing CUPS / CUPS-PDF. (Almost working)
 
BTW: I'm using UBUNTU **SERVER** 10.04 (two hdd RAID0, two 1Gb eth interfaces)
 
Till then.

---

### Post by nixnotwin on 2010-06-24
I am facing a serious issue. When I boot up ubuntu 10.04, on which I have PDC, into GNOME, after I enter desktop login password it takes more than 3 minutes to authenticate. The login screen freezes for a long time. Even after login, if I want to run any commands as a super user in the terminal I have to wait for few minutes before the password gets accepted. This only happens in the beginning, second time the sudo password gets accepted quickly. Any help is appreciated.

---

### Post by wizard_karan on 2010-06-24
Hi bulletxt

1) i have followed all of the above steps and i got no errors. now i am confused how to add my laptop which runs on Windows 7 Home Premium 64 Bit to the PDC network.(please elaborate in detail)
i have never used domains and am a complete networking noob!:confused:

2) i have read in some posts online that Windows7 home premium cant do domain join, is that true or is there some workaround ?:KS

3)also please elaborate how to share files on my linux server so that i can access them from my Windows 7 laptop.

4) i have connected both with a Lan cable(cross-type), do i need something else ?:p

Any help will be greatly appreciated!!!):P

from
Karan Pratap Singh

---

### Post by nixnotwin on 2010-06-25
I wanted to have certain shares accessible only to certain groups, here are the steps I followed. This requires flip to be installed (you can find instructions at the end of the first post)
 
First you need to create a gruop and add a user to that group

 ```
smbldap-groupadd group1
```create a user

 ```
smbldap-useradd -a -m -P user1
```add the user to group1

```
smbldap-groupmod -m 'user1' 'group1'
auth-client-config -t nss -p lac_ldap
```Create a directory which'll be accessible to group1 users

```
mkdir /var/lib/samba/restricted
```Change ownership of the directory you created

```
chgrp group1 /var/lib/samba/restricted

```Change directory permissions

```
chmod u=rwx,g=rwx /var/lib/samba/restricted
```Open samba conf file 

```
nano /etc/samba/smb.conf
```and add this at the end

```
[restricted]
        Comment = Shared space only for restricted groups
        path = /var/lib/samba/restricted
        read only = no
        browseable = no
        force create mode = 0660
        force directory mode = 2770
```Save and close

Open allusers.bat 
```

nano /var/lib/samba/netlogon/allusers.bat
```add this and change YOURNETBIOS to your netbios name.
```
net use r: /delete 
net use r: "\\YOURNETBIOS\restricted"
```save and close

Run this command
```

flip -m /var/lib/samba/netlogon/allusers.bat
```Restart samba 

```
service smbd restart
```Now If you login with user you modified above you can see the drive R: mounted. The drive can be seen by other users who are not in the group, but it will not be accessible for them. Can it be made invisible for users who belong to other groups?

---

### Post by pcmb8866 on 2010-06-26
**Making shares accessible to certain groups checking groupmembership and then mount this share to a drive.**
(Works for WinXP and Win7)
 
Follow the instructions of NIXTOWIN to the end of samba config.
Edit smb.conf
change logon script
 
> 
logon script = logon.bat

 
Download KIXTART from [http://www.kixtart.org](http://www.kixtart.org)
Extract the zip file.
Copy KIX32.exe to your netlogon.
In your netlogon add file logon.bat
> 
nano logon.bat

add this
> 
@ECHO OFF
%0\..\Kix32.exe %0\..\logon.kix /f

save close
 
run this:
> flip -m /var/lib/samba/netlogon/logon.bat
 
Add file logon.kix
> nano logon.kix
add this:
> 
break on
; delete all mappings
USE * /delete
 
; Map the home directory
USE H: @HOMESHR
 
; And here is one group-oriented script to show what can be
; done that way:
IF INGROUP("YOURDOMAINNAME\group1")
USE R: [\\YOURNETBIOSNAME\restricted]("file://\\YOURNETBIOSNAME\restricted")
ENDIF
IF INGROUP("YOURDOMAINNAME\nextgroup")
USE N: [\\_[COLOR=#0066cc]YOURNETBIOSNAME\nextshare[/COLOR]_]("file://\\YOURNETBIOSNAME\nextshare")
ENDIF

save close
 
run this:
> flip -m /var/lib/samba/netlogon/logon.kix
 
restart samba
> service smbd restart
 
Now If you login with user you modified above you can see the drive R: mounted. The drive can **NOT** be seen by other users who are not in the group.
 
You can make more groups and share which are accessible and seen by users who belong to certain groups.
 
(Read the manual of KIXTART for more options!
 
Good luck!

---

### Post by pcmb8866 on 2010-06-26
> **wizard_karan said:**
> Hi bulletxt
 
1) i have followed all of the above steps and i got no errors. now i am confused how to add my laptop which runs on Windows 7 Home Premium 64 Bit to the PDC network.(please elaborate in detail)
i have never used domains and am a complete networking noob!:confused:
 
2) i have read in some posts online that Windows7 home premium cant do domain join, is that true or is there some workaround ?:KS
 
3)also please elaborate how to share files on my linux server so that i can access them from my Windows 7 laptop.
 
4) i have connected both with a Lan cable(cross-type), do i need something else ?:p
 
Any help will be greatly appreciated!!!):P
 
from
Karan Pratap Singh
 
Hi wizard_karan,
 
You can't join a DOMAIN with Windows 7 Home Premium. You have to upgrade to Win7 Pro or Win7 Ultimate

---

### Post by ekenb on 2010-06-26
Hi!

I am trying to get this to work on a brand new ubuntu 10.04 installation, but something goes wrong at (or rather before) step 12.

I am unable to connect, the error message is:
root@pdc:/etc/samba# smbclient -L localhost
Enter root's password:
session setup failed: NT_STATUS_LOGON_FAILURE

These are the two lines i have altered in smb.conf, attaching theses since it's the only thing I can think of that can have gone wrong if the guide is correct...

[global]
        # Domain name ..
        workgroup = MYDOMAIN
        # Server name - as seen by Windows PCs ..
        netbios name = MYDOMAIN1

Anyone got a solution?

Edit:
there is no secrets.tdb created in /etc/samba after
smbpasswd -W
is executed...

---

### Post by wizard_karan on 2010-06-27
> **pcmb8866 said:**
> Hi wizard_karan,
 
You can't join a DOMAIN with Windows 7 Home Premium. You have to upgrade to Win7 Pro or Win7 Ultimate

Hi pcmb8866
many thanks for helping me out!!:p

I am sure that you are correct as other people on the net were saying so too. Now that i am convinced i will buy a copy of Windows 7 Professional!! 

Thanks again):P
from
Karan Pratap Singh
Chandigarh,India:-o

---

### Post by pcmb8866 on 2010-06-27
**Trouble logging in to your domain?**
 
:idea: TIP:
 
When you try to login and get a message: Can't find logonserver then:
 
> 
Edit smb.conf
Comment out "obey pam restrictions"
or change it to: obey pam restrictions = no
 
Save
 
Restart samba:
service smbd restart

 
You should now be able to login=D>

---

### Post by bandcoach on 2010-06-28
OK, I'm going to go out onto a very strong limb here (at least I think it is strong).

[COLOR="Red"][SIZE="5"]In step 6[/SIZE][/COLOR]
the file [COLOR="DarkOrchid"]backend.example.com.ldif[/COLOR] can named [COLOR="DarkOrchid"]backend.your.domain.ldif[/COLOR]?, otherwise it locks us into calling our domain example.com.

the [COLOR="DarkOrchid"]dc=pdc[/COLOR] likewise can be changed to what we wish to call our primary domain controller?, say [COLOR="DarkOrchid"]dc = dcontrol[/COLOR] in my case!

Forgive me if i am being obtuse, but these finer points are not in the article and can make or break a setup in my opinion, even if we all do this behind NAT firewall.

I need an answer as I will stay at this point until I can be certain of what effect following this instructions will have or what variation is permissible to ensure local compatibility.

Shane

---

### Post by bulletxt on 2010-06-28
Of course you can change dc=pdc to dc=$anything, however if you change that you must be sure to change that line in all other places where you see it.

And you can rename backend.example.com.ldif  to anything you want!

---

### Post by nixnotwin on 2010-06-28
[pcmb8866]("http://ubuntuforums.org/member.php?u=1098446"), the setup you posted about using kixstart did not work me. I spent about 2 hours trying to figure out what went wrong. Still, even after carefully following your steps once again, it just didn't work.

---

### Post by pcmb8866 on 2010-06-28
> **nixnotwin said:**
> [pcmb8866]("http://ubuntuforums.org/member.php?u=1098446"), the setup you posted about using kixstart did not work me. I spent about 2 hours trying to figure out what went wrong. Still, even after carefully following your steps once again, it just didn't work.
 
When you created your group "group1" did you use the -a option?
E.g. smbldap-groupadd -a group1
 
This automaticaly adds a windows - samba - groupmapping.

---

### Post by pcmb8866 on 2010-06-28
Restarting SMBD
 
Everytime I reboot I have to manualy restart smbd. In syslog is a message smbd cannot connect to ldap. (Because ldap isn't running yet)
How can I automate the startup of smbd at the end of the bootsequence. (Ubuntu 10.04 server)
 
Any help I'll appreciate.
 
TIA
Peter

---

### Post by bandcoach on 2010-06-29
[SIZE="4"][COLOR="Red"]STEP 30[/COLOR][/SIZE]

my results varied in the following way

[COLOR="Red"]Administrators:*:544:[/COLOR]

not root at the end of this line all others were as indicated.

I did not deviate from the main instructions only substituting my domain name and workgroup and password throughout.

Why would this result be different ~ I'm currently too tired to think too hard about this and would just appreciate a pointer to where I should go to correct and rerun the command

Cheers

Shane

---

### Post by bandcoach on 2010-06-29
General question for those who have implemented this:

Has anyone gone the next step and configured webmin to administer the groups and users once the pdc is running??

Would be helpful if someone has, otherwise I guess I am in for a long day inputting all of the configuration info that webmin requires for user/group administration for ldap.

I'll write it up if I end up doing this

Cheers

Shane

---

### Post by bulletxt on 2010-06-29
> **bandcoach said:**
> [SIZE="4"][COLOR="Red"]STEP 30[/COLOR][/SIZE]

my results varied in the following way

[COLOR="Red"]Administrators:*:544:[/COLOR]

not root at the end of this line all others were as indicated.

I did not deviate from the main instructions only substituting my domain name and workgroup and password throughout.

Why would this result be different ~ I'm currently too tired to think too hard about this and would just appreciate a pointer to where I should go to correct and rerun the command

Cheers

Shane

Did you do Step 26? Any errors?

---

### Post by bandcoach on 2010-06-29
> **bulletxt said:**
> Did you do Step 26? Any errors?

No - I did not. Nice thing about being able to recall commands on the command line - can check what you have done (or not). Have done now and error free.

It is what comes of not being awake when you do things like this - you skip steps even though you are certain you haven't.:lolflag:

Thank you

Shane

---

### Post by aimi on 2010-07-03
Hi. Thank for your guide. It Work !!
I can join my xp to the domain but after restart xp 
i can not log in  it said "system can not log you in Domain test.com is not available "
 
how can i fix this ?
 
Thank you all

---

### Post by vtulin on 2010-07-05
Point 30:

The result have a lot of stuff, but I don't have similar records, no one. :(

---

### Post by bjorgein on 2010-07-05
Whenever I try to join a Windows XP machine to the domain I get the following error: 

"The following error occurred attempting to join the domain "ldaptest2"

The network path was not found.

I get the little prompt thingy to enter in credentials but then craps out when I put in the administrator credentials to join the machine to the domain. I see that it successfully adds the machine to the ou=computers group in my ldap directory but I can't join the domain!
any ideas??

---

### Post by bjorgein on 2010-07-05
I did a little poking around and now the error I get when trying to join the domain after entering in my credentials is "The user name could not be found."

What is the issue with this? One thing I can think of but I do not know how to fix is the algorithm used to map windows usernames to UIDS in LDAP. I know that LDAP starts at 1000 but I started at 10000, this might be the issue but I am not sure!

any help??:D

---

### Post by bulletxt on 2010-07-05
> **bjorgein said:**
> I did a little poking around and now the error I get when trying to join the domain after entering in my credentials is "The user name could not be found."

What is the issue with this? One thing I can think of but I do not know how to fix is the algorithm used to map windows usernames to UIDS in LDAP. I know that LDAP starts at 1000 but I started at 10000, this might be the issue but I am not sure!

any help??:D

If you didn't follow my guide doing exactly what I said, I'm sorry but I can't help you. :)

---

### Post by nixnotwin on 2010-07-06
I was not able to get kixstart working on my network.

This is the content of my logon.bat file

```
@ECHO OFF 
::  Network logon script 
::  Use KiXtart to manage network logons 
%0\..\Kix32.exe %0\..\kixtart.kix /f 			 		
```This is the content of my kixtart.kix file
```

break on 
; delete all mappings 
 
USE * /delete 
 
; And here is one group-oriented script to show what can be 
; done that way: 
IF INGROUP("DOMAIN1\group1") 
USE R: \\SMBSERVER\teefiles 
IF INGROUP("DOMAIN1\group2") 
USE N: \\SMBSERVER\myfiles 

```In smb.conf files I have the entry "logon script = logon.bat"

And also entries for the shared directories with group access permissions in the smb.conf file

---

### Post by AlexPE on 2010-07-06
Hi,
I followed the instructions to the letter, got to step 12, and got the dreaded NT_LOGON_FAILURE error. back-checked every line, could not find a descrepancy. Continued and completed all steps, same error. cannot join xp pro sp3 machine to domain "domain PRIMARYSAMBA doesn't exist or couldn't be contacted". The PC isn't a part of any domains, I used your example smb.conf verbatim: cannot join, primarysamba doesn't show up in MS Windows Network. I do have a 2003 PDC on this network; would that have any bearing? I'm lost; any help will be appreciated.

[DSL GW/RTR 192.168.0.1]--[PDC 192.168.0.201]--[ROUTER 2 192.168.1.1] --[PSAMBA 192.168.1.10]--[TESTPC 192.168.1.108]

ROUTER 2 IS A DLINK DIR-655 set to factory default.

Thanks for your help in advance

---

### Post by bulletxt on 2010-07-06
> **AlexPE said:**
> Hi,
I followed the instructions to the letter, got to step 12, and got the dreaded NT_LOGON_FAILURE error. back-checked every line, could not find a descrepancy. Continued and completed all steps, same error. cannot join xp pro sp3 machine to domain "domain PRIMARYSAMBA doesn't exist or couldn't be contacted". The PC isn't a part of any domains, I used your example smb.conf verbatim: cannot join, primarysamba doesn't show up in MS Windows Network. I do have a 2003 PDC on this network; would that have any bearing? I'm lost; any help will be appreciated.

[DSL GW/RTR 192.168.0.1]--[PDC 192.168.0.201]--[ROUTER 2 192.168.1.1] --[PSAMBA 192.168.1.10]--[TESTPC 192.168.1.108]

ROUTER 2 IS A DLINK DIR-655 set to factory default.

Thanks for your help in advance

Reboot your Linux machine. Do again step 10 and be sure to put the correct password. Reboot again your machine. Then do step 12 and see if it works. I'm quite sure you did step 10 putting wrong password because that's the error you're getting.

---

### Post by AlexPE on 2010-07-06
> **bulletxt said:**
> Reboot your Linux machine. Do again step 10 and be sure to put the correct password. Reboot again your machine. Then do step 12 and see if it works. I'm quite sure you did step 10 putting wrong password because that's the error you're getting.

Thanks for your response. I get the correct info (no errors) from step 12, but in trying to join the domain, "the specified domain (primarysamba) doesn't exist or cannot be contacted" error remains. I can login using valid unix users, but cannot join my xp pc to this domain. I've also tried disconnecting from the main network,but the problem persists. The XP error is: "DNS name does not exist. RCODE_NAME_ERROR. The query was for the SRV record for _ldap._tcp.dc._msdcs.PRIMARYSAMBA." Do I need to install DNS on PSAMBA? Is there something I can add upstream to make it work? I'm a bit of a Noob, so your help is appreciated.

---

### Post by robertomason on 2010-07-07
Don't know if any answered this one, I haven't seen it. I've had the same problem. The reason why it does this is that you have winbind running on your pdc. You shouldn't. Winbind is used by domain member machines, to look up Domain groups and users. I removed my winbind on my pdc. 


> **nixnotwin said:**
> I am facing a serious issue. When I boot up ubuntu 10.04, on which I have PDC, into GNOME, after I enter desktop login password it takes more than 3 minutes to authenticate. The login screen freezes for a long time. Even after login, if I want to run any commands as a super user in the terminal I have to wait for few minutes before the password gets accepted. This only happens in the beginning, second time the sudo password gets accepted quickly. Any help is appreciated.

---

### Post by pcmb8866 on 2010-07-07
> **nixnotwin said:**
> I was not able to get kixstart working on my network.
 
This is the content of my logon.bat file
 
```
@ECHO OFF 
::  Network logon script 
::  Use KiXtart to manage network logons 
%0\..\Kix32.exe %0\..\kixtart.kix /f                      
```This is the content of my kixtart.kix file
```

break on 
; delete all mappings 
 
USE * /delete 
 
; And here is one group-oriented script to show what can be 
; done that way: 
IF INGROUP("DOMAIN1\group1") 
USE R: \\SMBSERVER\teefiles 
IF INGROUP("DOMAIN1\group2") 
USE N: \\SMBSERVER\myfiles 

```In smb.conf files I have the entry "logon script = logon.bat"
 
And also entries for the shared directories with group access permissions in the smb.conf file
 
Did you add group1 and group2 in ldap with smbldap-groupadd -a group1; smbldap-groupadd -a group2.
 
Then add users to these groups:
smbldap-groupmod -m user1 group1
smbldap-groupmod -m user2 group2
 
When you don't use the -a option in smbldap-groupadd it won't work!

---

### Post by bjorgein on 2010-07-07
I just thought I would be courteous to other people trying to troubleshoot issues with Samba and Windows Domain Issues. If anyone is having the issue of "User not found" When trying to join a domain in Windows with a administrator account. 

[http://lists.samba.org/archive/samba/2007-August/134847.html](http://lists.samba.org/archive/samba/2007-August/134847.html)

There is a bug which causes machine accounts to get written ou=computers(or whatever you set in smb.conf and smbldap.conf) but then read from ou=people(or ou=users or where ever you set user accounts to be stored).

To fix it i just changed /etc/samba/smb.conf "ldap machine suffix = ou=computers" to "ldap machine suffix = ou=people" and then /etc/smbldap-tools/smbldap.conf "computersdn="ou=computers,${suffix}" to "computersdn="ou=people,${suffix}"

I then could join my domain and login in with credentials stored on my LDAP server through Samba because it would write and then read computer accounts from the ou=people section.

if anyone has any more questions just ask i check back here fairly frequently.

---

### Post by enigmait on 2010-07-07
I've followed the tutorial exactly and no errors throughout the tutorial and when I try to join Windows XP Pro machine to domain as root I get the error:

The following error has occurred attempting to join the domain "domainname"

the specified domain either does not exist or could not be contacted.

---

### Post by nixnotwin on 2010-07-08
pcmb8866. I used -a while creating groups, and also used "smbldap-groupmod -m user1 group1" string. I tried with new user and group. Still it doesn't work. If i logged in as user1 I can access  \\DOMAIN1\restricted manually with both read write permissions.

---

### Post by AlexPE on 2010-07-08
> **bjorgein said:**
> I just thought I would be courteous to other people trying to troubleshoot issues with Samba and Windows Domain Issues. If anyone is having the issue of "User not found" When trying to join a domain in Windows with a administrator account. 

[http://lists.samba.org/archive/samba/2007-August/134847.html](http://lists.samba.org/archive/samba/2007-August/134847.html)

There is a bug which causes machine accounts to get written ou=computers(or whatever you set in smb.conf and smbldap.conf) but then read from ou=people(or ou=users or where ever you set user accounts to be stored).

To fix it i just changed /etc/samba/smb.conf "ldap machine suffix = ou=computers" to "ldap machine suffix = ou=people" and then /etc/smbldap-tools/smbldap.conf "computersdn="ou=computers,${suffix}" to "computersdn="ou=people,${suffix}"

I then could join my domain and login in with credentials stored on my LDAP server through Samba because it would write and then read computer accounts from the ou=people section.

if anyone has any more questions just ask i check back here fairly frequently.

I'm having that problem too.. been working with Bulletxt's howto, but got stumped when this occurred. I don't have winbindd, dns or dhcpd running, but so far no one seems to need these(?) to get theirs working. Am clueless!

---

### Post by bjorgein on 2010-07-08
> **AlexPE said:**
> I'm having that problem too.. been working with Bulletxt's howto, but got stumped when this occurred. I don't have winbindd, dns or dhcpd running, but so far no one seems to need these(?) to get theirs working. Am clueless!

I followed his guide exactly from the point after LDAP setup as I already had a working LDAP server installed. I just had to switch the place where the workstation accounts would get added when a new Windows workstation tries to connect. Make sure that all the groups that you made have the correct domain SID and that you have correct permissions on everything. Samba is very picky.

---

### Post by enigmait on 2010-07-08
The reason mine was failing was due to DHCP. 

I set static on the workstation and all is ok now.

I can only assume that the Samba PDC needs to be a DHCP controller.

---

### Post by AlexPE on 2010-07-08
> **ricpelo said:**
> Hi, bulletxt! Excellent post. All works flawless, like a charm :).

Only one question: Is there a way to have roaming profiles enabled with this config? I have a classroom of 30 client PCs and I would like to have that option available, so the students can sit on any PC and get all their docs and configuration available.

Thanks very much in advance.

Hi Riccpelo,
I'm having heck trying to get this to work.. I get user not found or bad password errors joining xp pcs to the domain.. any suggestions?

---

### Post by AlexPE on 2010-07-08
> **bjorgein said:**
> I followed his guide exactly from the point after LDAP setup as I already had a working LDAP server installed. I just had to switch the place where the workstation accounts would get added when a new Windows workstation tries to connect. Make sure that all the groups that you made have the correct domain SID and that you have correct permissions on everything. Samba is very picky.

did you use samba 3.4.7 or 4.0 ? It was suggested to use 4.0 but it's still in alpha.. not sure if that would mess-up everything already done, and it take hours to reinstall everything from scratch.

---

### Post by Leppie on 2010-07-09
> **AlexPE said:**
> did you use samba 3.4.7 or 4.0 ? It was suggested to use 4.0 but it's still in alpha.. not sure if that would mess-up everything already done, and it take hours to reinstall everything from scratch.
it's working well on my samba 3.4.7.
even joining xp virtual machines to the domain without a hitch (accounts created in ou=Computers). i just cannot seem to join the 7 virtual machine to the domain...

---

### Post by pcmb8866 on 2010-07-10
[FONT=Times New Roman][SIZE=3]**Setting up ldap, samba, roaming profiles and netlogon to mount shares according to groupmembership...**[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]! Read entire post before trying ![/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I use:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]LDAP:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dc=landgr,dc=lb (change to yours) instead of dc=pdc[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]SAMBA:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Workgroup: LANDGR (change to yours)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Netbios name: UBUNTU (change to yours) must not be the same as workgroup[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have my netlogon and profiles all under /home because this is the disk with most space available. (change to yours)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]All shares are also under /home.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]NETLOGON:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]KIXTART (Scripting language to check groupmembership)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]First install and configure ldap as descripted in post #1 changing all entries dc=pdc to yours. For me it was dc=landgr,dc=lb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Also change password &#8220;pwd123&#8221; to your own. ([COLOR=red]**CHANGE IT EVERYWHERE**[/COLOR])[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]At point 9 I didn't download smb.conf. I use my own. See below:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]# Global parameters[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][global][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Change all values to your own &#8211; workgroup, netbios name, realm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]workgroup = LANDGR[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]netbios name = UBUNTU[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]realm = LANDGR.LB[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]server string = Home Server[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]interfaces = eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]bind interfaces only = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]passdb backend = ldapsam:ldap://127.0.0.1/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]panic action = /usr/share/samba/panic-action %d[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]pam password change = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]username map = /etc/samba/smbusers[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]time server = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# obey pam restrictions = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dns proxy = no[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]printing = cups[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]load printers = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]printcap name = cups[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]show add printer wizard = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]cups options = Raw[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]domain logons = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]os level = 65[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]preferred master = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]domain master = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]wins support = yes[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]# LDAP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap admin dn = cn=admin,dc=landgr,dc=lb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap delete dn = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap suffix = dc=landgr,dc=lb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap user suffix = ou=people[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap group suffix = ou=groups[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap machine suffix = ou=computers[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap passwd sync = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ldap ssl = no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]add user script = /usr/sbin/smbldap-useradd -m "%u"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]delete user script = /usr/sbin/smbldap-userdel "%u"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]add group script = /usr/sbin/smbldap-groupadd -p "%g"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]delete group script = /usr/sbin/smbldap-groupdel "%g"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]add machine script = /usr/sbin/smbldap-useradd -w "%u"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]logon script = logon.bat[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]logon path = \\%L\profiles\%U\%m[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]logon drive = H:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]logon home = \\%L\%U\.win_profile\%m[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]# Change hosts allow to your network IP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hosts allow = 127.0.0.1, 192.168.1.0/24[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]case sensitive = no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hide files = /desktop.ini/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]admin users = root, @"Domain Admins"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]server signing = auto [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]server schannel = auto[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]enable privileges = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]log level = 3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]unix extensions = no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]wide links = yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smb ports = 139[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][IPC$][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /tmp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Change hosts allow to your network IP[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hosts allow = 192.168.1.0/24, 127.0.0.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hosts deny = 0.0.0.0/0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][netlogon][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Network Logon Service[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/netlogon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Domain Admins"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]guest ok = Yes[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][profiles][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Profile Share[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/samba-ntprof[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]read only = No[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]profile acls = Yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]browseable = No[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][printers][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = All Printers[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /var/spool/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]guest ok = no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]printable = Yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]use client driver = Yes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]browseable = no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]writeable = no[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][homes][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Home Directories[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]valid users = %S[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]read only = No[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]create mask = 0770[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hide files = /desktop.ini/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]browseable = No[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]volume = HOME[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][Common][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Common files[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force user = pcmb8866[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force group = Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Common"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][Application][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Application Files[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force user = pcmb8866[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force group = Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Apps"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][Department][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Department[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Dept"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][Movies][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Movieshare[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Movies"[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][Music][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]comment = Musicshare[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]path = /home/Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force user = pcmb8866[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]force group = Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]write list = @"Music"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]At point 13 I changed (only for me)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> mkdir -v /home/samba-ntprof (profiles)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]-> chmod 777 /home/samba-ntprof[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]-> mkdir -v -p /home/netlogon (netlogon)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]-> chmod 777 /home/netlogon [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]When you have installed smbldap-tools make sure that the entries in the file smbldap.conf are as shown:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]userSmbHome=""[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]userProfile=""[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]userHomeDrive=""[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]userScript="" [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Add groups to ldap:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]smbldap-groupadd -a Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupadd -a Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupadd -a Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupadd -a Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupadd -a Music[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Don't forget to use the -a option!![/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Create your shares:[/SIZE][/FONT]
> 
Because I have all shares under /home:
cd /home
[FONT=Times New Roman][SIZE=3]mkdir netlogon (your netlogon)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chown root:root netlogon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 777 netlogon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mkdir samba-ntprof (your profiles share)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chown root:root samba-ntprof[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 777 samba-ntprof[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]mkdir Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chgrp Common Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 770 Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mkdir Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chown pcmb8866:Apps Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 750 Apps (only owner can add files)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mkdir Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chgrp Dept Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 770 Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mkdir Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chgrp Movies Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 770 Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mkdir Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chgrp Music Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 770 Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add users to ldap:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]smbldap-useradd -a -m -P pcmb8866 (me)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-useradd -a -m -P user1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-useradd -a -m -P user2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add user to groups:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]smbldap-groupmod -m pcmb8866,user1,user2 Common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupmod -m pcmb8866,user1,user2 Apps[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupmod -m pcmb8866,user1 Dept[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupmod -m pcmb8866,user2 Movies[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]smbldap-groupmod -m pcmb8866,user1 Music[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Download KIXTART from [http://www.kixtart.org]("http://www.kixtart.org/")[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Extract the zip file.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Copy KIX32.exe to your netlogon.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]In your netlogon add file logon.bat [/FONT][/SIZE]
> 
[FONT=Times New Roman][SIZE=3]touch /home/netlogon/logon.bat[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]nano /home/netlogon/logon.bat[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]@ECHO OFF[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]%0\..\Kix32.exe %0\..\logon.kix /f [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Save &#8211; close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In netlogon add file logon.kix[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]touch /home/netlogon/logon.kix[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]nano /home/netlogon/logon.kix[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]break on[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]; delete all mappings[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]USE * /delete[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]; Map the home directory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]USE H: @HOMESHR[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]; And here is one group-oriented script to show what can be[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]; done that way:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]IF INGROUP("Common")[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]USE I: \\UBUNTU\Common[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ENDIF[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]IF INGROUP("Apps")[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]USE P: [\\UBUNTU\Application]("file://\\UBUNTU\Application")[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ENDIF[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]IF INGROUP("Dept")[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]USE N: \\UBUNTU\Department[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ENDIF[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]IF INGROUP("Movies")[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]USE M: \\UBUNTU\Movies[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ENDIF[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]IF INGROUP("Music")[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]USE L: \\UBUNTU\Music[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ENDIF[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]EXIT[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Save &#8211; close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]One more step to go:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]Change to your netlogon.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Cd /home/netlogon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]flip -m logon.bat[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]flip -m logon.kix[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]chmod 755 *[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]REBOOT[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Now you should be able to log in with user1 en user2 and the drive letters should be mounted to the shares.[/SIZE][/FONT]
Pictures of result:
[http://www.codior.nl/sambashares/](http://www.codior.nl/sambashares/)
 
**One last TIP:**
 
**[COLOR=red]CHECK, CHECK, DOUBLE CHECK[/COLOR]**
**[COLOR=#ff0000]Also pay attention to BULLETXT post regarding NETBIOS name, workgroup name and password.[/COLOR]**
**[COLOR=#ff0000]Don' be hasty[/COLOR]** 
 
I've got mine working flawless, like a charme with Windows XP and Windows 7
 
 
**[FONT=Times New Roman][SIZE=3]When samba won't start automatic after reboot.[/SIZE][/FONT]**..
[FONT=Times New Roman][SIZE=3]When you have the same trouble as I did that samba won't start after reboot there is a workaround.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The problem is the new &#8220;UPSTART JOB&#8221;[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Workaround:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Rename /etc/init/smbd.conf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv /etc/init/smbd.conf /etc/init/smbd.conf.org[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Rename /etc/init/nmbd.conf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv /etc/init/nmbd.conf /etc/init/nmbd.conf.org[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Add samba to /etc/init.d[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]touch /etc/init.d/samba[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nano /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
> 
[FONT=Times New Roman][SIZE=3]#!/bin/sh[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]### BEGIN INIT INFO[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Provides: samba[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Required-Start: $network $local_fs $remote_fs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Required-Stop: $network $local_fs $remote_fs[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Default-Start: 2 3 4 5[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Default-Stop: 0 1 6[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Short-Description: start Samba daemons (nmbd and smbd)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]### END INIT INFO[/FONT][/SIZE]
 
 
[SIZE=3][FONT=Times New Roman]# Defaults[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]RUN_MODE="daemons"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# Reads config file (will override defaults above)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][ -r /etc/default/samba ] && . /etc/default/samba[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]NMBDPID=/var/run/samba/nmbd.pid[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]SMBDPID=/var/run/samba/smbd.pid[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# clear conflicting settings from the environment[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]unset TMPDIR[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]# See if the daemons are there[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]test -x /usr/sbin/nmbd -a -x /usr/sbin/smbd || exit 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]. /lib/lsb/init-functions[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]case "$1" in[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]start)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_daemon_msg "Starting Samba daemons" "nmbd"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/nmbd -- -D; then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_end_msg 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]exit 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]if [ "$RUN_MODE" != "inetd" ]; then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_progress_msg "smbd"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D; then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_end_msg 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]exit 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]log_end_msg 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman];;[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]stop)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_daemon_msg "Stopping Samba daemons" "nmbd"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]start-stop-daemon --stop --quiet --pidfile $NMBDPID[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Wait a little and remove stale PID file[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]sleep 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]if [ -f $NMBDPID ] && ! ps h `cat $NMBDPID` > /dev/null[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Stale PID file (nmbd was succesfully stopped),[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# remove it (should be removed by nmbd itself IMHO.)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]rm -f $NMBDPID[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]if [ "$RUN_MODE" != "inetd" ]; then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_progress_msg "smbd"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]start-stop-daemon --stop --quiet --pidfile $SMBDPID[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Wait a little and remove stale PID file[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]sleep 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]if [ -f $SMBDPID ] && ! ps h `cat $SMBDPID` > /dev/null[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]then[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# Stale PID file (nmbd was succesfully stopped),[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]# remove it (should be removed by smbd itself IMHO.)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]rm -f $SMBDPID[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]fi[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]log_end_msg 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman];;[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]reload)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]log_daemon_msg "Reloading /etc/samba/smb.conf" "smbd only"[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]start-stop-daemon --stop --signal HUP --pidfile $SMBDPID[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]log_end_msg 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman];;[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]restart|force-reload)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]$0 stop[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]sleep 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]$0 start[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman];;[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]echo "Usage: /etc/init.d/samba {start|stop|reload|restart|force-reload}"[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]exit 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman];;[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]esac[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]exit 0[/FONT][/SIZE]
 
 [FONT=Times New Roman][SIZE=3]Save &#8211; close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]chown root:root /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 755 /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]update-rc.d samba start 52 2 3 4 5 . stop 52 0 1 6 .[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]REBOOT[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]All should work now because samba starts when ldap is already running.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]With this workaround when you have to restart samba in the future you must use:[/FONT][/SIZE]
```

[SIZE=3][FONT=Times New Roman]/etc/init.d/samba start / restart / stop[/FONT][/SIZE]

```

---

### Post by bulletxt on 2010-07-10
Thanks so much pcmb8866, I will put a link to your post in main thread!

---

### Post by Leppie on 2010-07-10
i get an error on the USE statement in logon.kix

any ideas?

---

### Post by pcmb8866 on 2010-07-10
> **Leppie said:**
> i get an error on the USE statement in logon.kix
 
any ideas?
 
What's the error like?
 
Both logon.bat and logon.kix are DOS formatted files.
You could use another editor instead of nano or vi. I use aee.

---

### Post by wizard_karan on 2010-07-10
Hi all

I got the PDC working perfectly!! All thanks to simple and easy steps given by bulletxt!:D

Now after my PDC setup was done, i was wondering from where bulletxt might have got so much information regarding Samba and openLDAP?;)

For a more comprehensive guide for setting up a Samba + openLDAP PDC ,I found that the Section 5-"Making Happy Users" of the book called "Samba 3 by Example" is a great resource.

Samba 3 by Example is provided FREE OF COST with Samba and is located in the DOCS folder of the un-tarred Samba directory.:o

Though before setting up a Samba+openLDAP PDC , if you do not know much about Windows Networking and how domain controllers work in a network, i would recommend Samba-HOWTO's domain control chapters.
Again Samba-HOWTO is also provided FREE OF COST along with Samba and can also be found in the DOCS subdirectory.

Hope this information helps all newcomers like me in the world of PDCs(and Samba and openLDAP for that matter).:)

Also if any of the people posting here know of anymore great(read well-explained) Samba+openLDAP PDC resources then please post the links here, it would be a great help to newbies like me.

from
Karan Pratap Singh
Chandigarh,India

---

### Post by Leppie on 2010-07-10
> **pcmb8866 said:**
> What's the error like?
 
Both logon.bat and logon.kix are DOS formatted files.
You could use another editor instead of nano or vi. I use aee.
the error is like this:
> ERROR: error in USE statement!
Script: \\SERVER\NETLOGON\logon.kix
Line: 4

i'm using the script you posted.
```
break on
USE * /DELETE            
USE H: @HOMESHR           

IF INGROUP("mygroup")
USE N: \\SERVER\mygroup     
ENDIF

```
any ideas?

---

### Post by pcmb8866 on 2010-07-11
```
break on
USE * /DELETE            
USE H: @HOMESHR           

IF INGROUP("mygroup")
USE N: \\SERVER\mygroup     
ENDIF

```any ideas?

You forgot something. 
IF INGROUP("mygroup") must be IF INGROUP("WORKGROUPname\mygroup")
and USE N: \\SERVER\mygroup where SERVER is your NETBIOSname in Samba.
WORKGROUP is the name of Workgroup in Samba.

---

### Post by typxx on 2010-07-11
Thanks for the great HowTo, that's just what i was looking for.
But because I'm really new to Linux/Ubuntu, i don't know how to make an Ubuntu 10.4 Client join the domain.

---

### Post by Leppie on 2010-07-13
> **pcmb8866 said:**
> You forgot something. 
IF INGROUP("mygroup") must be IF INGROUP("WORKGROUPname\mygroup")
and USE N: \\SERVER\mygroup where SERVER is your NETBIOSname in Samba.
WORKGROUP is the name of Workgroup in Samba.
actually, if i add a line for the general share after the @HOMESHR mount, it still gives me error in line 4. so it actually never gets to the INGROUP part.
did you copy kixtart to the windows clients?

---

### Post by pcmb8866 on 2010-07-13
> **Leppie said:**
> actually, if i add a line for the general share after the @HOMESHR mount, it still gives me error in line 4. so it actually never gets to the INGROUP part.
did you copy kixtart to the windows clients?
I have tried to reproduce your error in every possible way. Can't get that error.
All files, KIX32.EXE and logon.kix are on my server in folder /home/netlogon.
Have you set all permissions of files right in netlogon. minimal 744, but best to set to 755 and folder /home/netlogon 777.
See picture
 [IMG]http://sambashares.codior.nl/netlogon.jpg[/IMG]
 
Check all your settings in samba and groups in ldap.
Or just start all over again with bulletxt installing and configuring ldap. Then adjust your smb.conf.
Read everything carefully. Its probably a type error.

---

### Post by nixnotwin on 2010-07-14
pcmb8866, I followed your new post for using kixtart to setup PDC on a complete new installation. I have closely examined your smb.conf and modified my smb.conf accordingly. Whatever I did I wan not able to mount a commonly shared drive. The home drive gets mounted because there is an entry for it in the smb.conf. In order to troubleshoot, I logged in as a user on windows xp, opened the netlogon directory and double clicked on logon.bat, and the shared drive and the home drive both got mounted with read+write permissions. I have the entry "logon script = logon.bat" in my smb.conf, but it doesn't happen automatically.

---

### Post by pcmb8866 on 2010-07-15
> **nixnotwin said:**
> pcmb8866, I followed your new post for using kixtart to setup PDC on a complete new installation. I have closely examined your smb.conf and modified my smb.conf accordingly. Whatever I did I wan not able to mount a commonly shared drive. The home drive gets mounted because there is an entry for it in the smb.conf. In order to troubleshoot, I logged in as a user on windows xp, opened the netlogon directory and double clicked on logon.bat, and the shared drive and the home drive both got mounted with read+write permissions. I have the entry "logon script = logon.bat" in my smb.conf, but it doesn't happen automatically.
 
Login domain with user. 
Open LDAPAdmin. Goto Groups and click on group library. At the right side you will see the SAMBASID.
Check your groupmemberchip cache in XP.
> 
regedt32
 
goto:
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Group Policy\GroupMembership

Also at the right side you will see all the groups user is a member off in the form of a SAMBASID.
Is the SAMBASID in LDAPAdmin and regedt32 present? If not something is wrong in your ldap or samba setup.
Edit logon.kix and change
> 
IF INGROUP("BBM.SDM\library")
USE I: \\BBMSERVER\libfiles
ENDIF

to
> 
IF INGROUP("library")
USE I: \\BBMSERVER\libfiles
ENDIF

Because of some strange behavior in kixtart it will not accept a dot in the domainname.
 
Logout user and login again.
 
Hope this will help.

---

### Post by jeezpc on 2010-07-15
Hi Bulletxt,

I followed your tutorial. It almost work completelly ;)

- Samba / LDAP connect ok
- I can add a WinXP machine to the domain
- I can browse somes shares.

But here's my problem : 
1) I create my users with :
smbldap-useradd -a -m -P test2
2) It works
3) When I try to browse my "Home" share, i get a "Denied" error ...
4) When I "ls -la /home", i get the listing by the folders created by smbldap-useradd have the oid/gid instead of the user/group name :
ex:
1006 513 /home/test2

instead of :
test2 Domain Users /home/test2 ...

Any clue to why that is?

Thanks for your help!!!! And thanks again for this tutorial!


__

---

### Post by jeezpc on 2010-07-15
Hi again,

One more piece of info :

when i do "sudo ls -la", now the user/group is ok.

Any clue?

---

### Post by gnuINA on 2010-07-15
Thank you very much for kindly tutorial...

---

### Post by david.garceau on 2010-07-16
Tutorial has been absolutely wonderful!!! Great job with it, ran through some problems but were all at my own fault :P. 

My only question now is if you could provide any information on setting up a pdc with a bdc both using the same ldap server which is located on the pdc. Any help would greatly be appreciated.

Just incase i am going the wrong route ill also ask opinions on how i should do what i am looking for...

I have 3 servers, one is the domain controller, and then i have two file servers. I want it so that when the client logs into the domain controller in the morning, it automatically authenticates him with his own username and password to the two other samba file servers. Any help would really be appreciated, i really like the detail in your tutorials compared to others that ive read so far.



My major hurdle for this guide, was that for some reason my clients wouldnt see the domain controller, but once i manually went into the client and went into tcp/ip options and then advanced and set the wins server ip as my domain controller, everything worked. I hope that can help some of you

---

### Post by nixnotwin on 2010-07-16
I wanted to use disk quota for home directories. I used [this guide]("http://www.howtoforge.com/how-to-set-up-journaled-quota-on-debian-lenny"). I have 500 users, and I wanted to give 200 MB space for each users home directory. I had thought that by putting all the 500 users under a group and specifying 200 MB for that group would give each home directory 200 MB space. But I was wrong, group quota is used to assign quota for a shared directory which can be used by any user of that group. Imagine if group quota is specified as 50 MB for a shared directory, if a user puts 25 MB file in it, other users will have only 25 MB space left. So, if there are many users on whose home directories quota should be set, the only solution is to use user quota. But there is a feature which allows us to copy one users quota settings to other users.

```
edquota -p user1 user2,user3,user4

```The code above copies the quota settings of user1 to user2,user3 and so on. If there are really many users for whom quota should be assigned, then the solution provided in [this link]("http://wiki.archlinux.org/index.php/Disk_Quota") under the subheading 'copying quota settings for multiple users' will be of help. 

Is there a better of doing it? Anyone?

---

### Post by nixnotwin on 2010-07-16
Another issue for those have hundreds of clients, is creating users on the PDC. Here is a script I found which accepts user names and passwords from a csv file. 
```

#!/bin/bash
CSVFILE=/home/acep/smbUsers.csv
SLAU=`which smbldap-useradd`
for i in `cat $CSVFILE|sed 's/, /,/g'`; do
        UN=`echo $i | cut -f1 -d','`
        #PW=`echo $i | cut -f2 -d','`
        $SLAU -a -m $UN
done
```

I found[ it here]("http://www.linuxquestions.org/questions/linux-newbie-8/a-simple-bash-file-for-importing-samba-users-from-a-file-692992/")

When I used it it created the users, but it looked as though passwords were not set. Is there anything that should be modified?

---

### Post by waygooder on 2010-07-16
So I have followed the guide and I believe that I did everything right. I got no errors all the way through the end, but when I try to join the domain on an XP computer I get: Login failure: unknown username or bad password.

I have triple checked the password and reset it numerous times but I cannot get the computer to log on.

any ideas?

---

### Post by david.garceau on 2010-07-16
are you using the admin account that you setup?

---

### Post by waygooder on 2010-07-16
Yes, as well as a test account that I set that is not part of the Administrators group.

---

### Post by david.garceau on 2010-07-16
The only problem i had was with that... i mistakenly didnt use the adminpdc account that was created. also make sure that on the windows machine, when you login, make sure you are connecting to the domain and not local computer. The first time you join a computer to the domain you need to use the adminpdc account

---

### Post by waygooder on 2010-07-16
Just added the adminpdc user and that did not work either. I had added a user the same way before, I just called it something different.

---

### Post by AKnightintheDesert on 2010-07-17
Thanks for the great tutorial.  It seems the server is running great, I am getting a DNS Error every time I try to add my win 7 machine to the domain.  My network has the following:

**pfsence router**
running as the DHCP server
basic firewall 
no DNS cahe

**Ubuntu Server**
configured as per this tutorial with the addition of an openssh server

**Ubuntu 10.04 Workstation**
used to configure the server

**Windows 7 Ultimate Box**
used to test shares and logins on the PDC.  

When I log in to the server using a folders window in win7 and log in I am able to log in using a user and my domain that I set up.  However when I try to join the domain with the win 7 server I get an error that says the domain can't be found.  Does the PDC Server need to be the dhcp server?? Do I need to set up some sort of cache for DNS??  Any help would be appreciated.

---

### Post by ricpelo on 2010-07-17
If your smbd doesn't start during computer bootup due to the Upstart, you can use another rather simple solution:

[LIST=1]
[*] Edit /etc/init/smbd.conf:

```
# vi /etc/init/smbd.conf

```

[*] Add the following line just before the "end script" line:

```

while [ ! -f /var/run/slapd/slapd.pid ]; do sleep 1; done       # WAIT FOR slapd

```

[*] Save & exit, and now reboot the computer.

[/LIST]

If you wish, you can add another line in order to wait for the cupsd, too:

```

while [ ! -f /var/run/cups/cupsd.pid ]; do sleep 1; done        # WAIT FOR cupsd

```

as well as change the "start on" line in order to wait for the networking:

```

start on (local-filesystems and net-device-up IFACE!=lo)

```

Hope this helps,

Ricardo.

---

### Post by mr E on 2010-07-17
**bulletxt **Great info!!
I want to use it, but before I have some questions:

I want to replace our old windows 2000 SBS (**w2ksbs)**, installed in 1 poweredge, that runs as Domain Controller, AD, with SQL Server 2000 for 1 ERP, IIS, file server, printer server, Firebird for payroll system, for less than 50 users.

I wish to use another PDC: a new shiny Ubuntu 10.04 Samba PDC (**U1004SPDC**)  that provides services as: print, file, apache and maybe other services need it.

I wish to replace the old **w2ksbs **with a newer windows 2008 R2 with SQL Server 2008 (**w2k8r2**), this new server will be a member server on the **U1004SPDC**, so the users/computers that use sql/erp log into the **U1004SPDC** domain and work without notice.

Other apps like the payroll system/Firebird can be installed into another PC running Windows 7 (by example), just six or seven users need to work concurrent.

[LIST]
[*][COLOR=Blue]But I wish to know if w2k8r2 servers can be members of this **U1004SPDC** without issues? any information, steps, guide, advices, samples to add member servers to a **U1004SPDC** [/COLOR][COLOR=Blue]are very well appreciated.[/COLOR]
[*][COLOR=Blue]How many member servers can be handled with **U1004SPDC**?[/COLOR]
[*][COLOR=Blue]**U1004SPDC** can be used (or is not recommended) to run a local mail server?[/COLOR]
[*][COLOR=Blue]For a production server what kind of hardware is recommended, a simple computer: by example an optiplex or server hardware?[/COLOR]
[*][COLOR=Blue]For backup of a production [/COLOR][COLOR=Blue]**U1004SPDC **[/COLOR][COLOR=Blue]server, can someone provide information? the disc can or need to be cloned? with what tools?[/COLOR]
[*][COLOR=Blue]In case of hardware fail, is safe to take the hard disk and put in another computer to run the [/COLOR][COLOR=Blue]**U1004SPDC **[/COLOR][COLOR=Blue]server?[/COLOR]
[/LIST]
Thanks for the time reading my questions, hope there is useful to someone else too.

Regards
Mr E

---

### Post by ricpelo on 2010-07-18
I have one issue:

After max mount count of my root filesystem, fsck check is forced, but just after fsck has been finished checking, the boot process freezes for exactly one minute (I measured it with a timer), and then resumes normally, as far I can see...

This isn't seems to be a big issue (forced fsck checks aren't very frequent, and one minute waiting is not too much, IMHO) but I would like to know where is the problem.

Any clues?

Ricardo.

---

### Post by david.garceau on 2010-07-19
> **waygooder said:**
> Just added the adminpdc user and that did not work either. I had added a user the same way before, I just called it something different.


i tried to replicate this for you. Once i had the problem, i only made two changes... im not sure if your problem was the same, but i just did dpkg-reconfigure ldap-auth-config. Under there i had messed up where you need to enter ldapi:/// (there was only two //) and also where i had to type in the ldap account for root, i had cn=admin, dc=pdc,dc=local. where it should have been cn=admin, dc=pdc, dc=local (note the space between pdc, dc=local. 

Once you make the changes type pam-auth-update ldap
Hope this helps you somehow

---

### Post by phaed on 2010-07-19
I just want to say THANK YOU!  I added a symbolic link to a 2 TB external hard drive that I have set up on my Ubuntu server and now I can access all the files from Win 7, finally. :-)

---

### Post by felixdecat on 2010-07-20
> **ekenb said:**
> Hi!

I am trying to get this to work on a brand new ubuntu 10.04 installation, but something goes wrong at (or rather before) step 12.

I am unable to connect, the error message is:
root@pdc:/etc/samba# smbclient -L localhost
Enter root's password:
session setup failed: NT_STATUS_LOGON_FAILURE

These are the two lines i have altered in smb.conf, attaching theses since it's the only thing I can think of that can have gone wrong if the guide is correct...

[global]
        # Domain name ..
        workgroup = MYDOMAIN
        # Server name - as seen by Windows PCs ..
        netbios name = MYDOMAIN1

Anyone got a solution?

Edit:
there is no secrets.tdb created in /etc/samba after
smbpasswd -W
is executed...

Ive got the same problem with a fresh install. I followed the Tutorial too the letter.

Any idea guys??

---

### Post by nixnotwin on 2010-07-21
When you see ```
Enter root's password:
``` don't enter the password, just press the enter key.

---

### Post by waygooder on 2010-07-21
Ok, got it working. I ended up reinstalling Ubuntu and starting fresh. I think what what I got wrong was not replacing dc=pdc everywhere correctly.

I wanted just a local domain so I went through set up again and everywhere you see "dc=pdc" you must replace it with "dc=yourdomain,dc=local".

I think in a couple of them I must have only changed "dc=mydomain" and left off the "dc=local"

so thanks for all the help, before I found this guide I had tried to get a PDC set up on 10.04 using the ubuntu guide but was unsuccessful.

---

### Post by pcmb8866 on 2010-07-22
> **nixnotwin said:**
> pcmb8866, I followed your new post for using kixtart to setup PDC on a complete new installation. I have closely examined your smb.conf and modified my smb.conf accordingly. Whatever I did I wan not able to mount a commonly shared drive. The home drive gets mounted because there is an entry for it in the smb.conf. In order to troubleshoot, I logged in as a user on windows xp, opened the netlogon directory and double clicked on logon.bat, and the shared drive and the home drive both got mounted with read+write permissions. I have the entry "logon script = logon.bat" in my smb.conf, but it doesn't happen automatically.
nixnotwin:
I found another way to map drives to shares. Using VB-script
 
Change your logon.bat file in folder netlogon to:
```

cscript [\\ubuntu\netlogon\logon.vbs]("file://\\ubuntu\netlogon\logon.vbs")

```
Changing ubuntu to your servername.
 
Then execute flip -m logon.bat
 
Add a file logon.vbs in your netlogon folder
```

touch logon.vbs

```
 
Edit logon.vbs and add the following code changing "[COLOR=red]**ubuntu**[/COLOR]" to your **NETBIOSname** and "[COLOR=red]**LANDGR.LB**[/COLOR]" to your **WORKGROUPname** in smb.conf:
```

'First make sure all variables are dimensioned.
'This isn't necessary for functionality; it's for coding discipline only.
Option Explicit
 
'dimension all our variables
dim objNetwork
dim strDriveLetter, strRemotePath, strUser, strGrp
dim strGroupADSPath, strUserADSPath, grp
dim oDrives, i
 
'This script will use the MapNetworkDrive method
'for each network drive mapped.
 
'Delete already mapped network drives
On error resume next 
 
'We'll be using the Wscript.Network Object to enumerate the user as well as to map drives.
'We only need to instantiate it once at the beginning.
 
Set objNetwork = WScript.CreateObject("WScript.Network") 
Set oDrives = objNetwork.EnumNetworkDrives 
 
For i = 0 to oDrives.Count - 1 Step 2 
objNetwork.RemoveNetworkDrive oDrives.Item(i),true,true 
Next 
 
'First let's get the user name since we'll use it for mapping the home directory
'as well as checking group memberships.
strUser = objNetwork.UserName
 
'User Drive to H:
strDriveLetter = "H:"
strRemotePath = "\\[COLOR=red]**ubuntu**[/COLOR]"
objNetwork.MapNetworkDrive strDriveLetter, strRemotePath & "\" & strUser
 
'next we'll enumerate groups and map drives for specific departmental memberships
'The code to check for memberships and map the drives is in a subroutine called IsMember.
'All we have to do is copy the same block over again for each group membership we want to check.
'The block only needs to set the string values for the group name, the desired drive letter, and the share path.
'Then it calls the IsMember subroutine down below.
 
'N: for members of _[COLOR=#0066cc]Department[/COLOR]_
strGrp="Dept"
strDriveLetter = "N:"
strRemotePath = [\\**[COLOR=red]ubuntu[/COLOR]**\Department]("file://\\ubuntu\Department")
IsMember
 
'P: for members of Apps
strGrp="Apps"
strDriveLetter = "P:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Application]("file://\\ubuntu\Application")
IsMember
 
'I: for members of Common
strGrp="Common"
strDriveLetter = "I:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Common]("file://\\ubuntu\Common")
IsMember
 
'L: for members of Movies
strGrp="Movies"
strDriveLetter = "L:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Movies]("file://\\ubuntu\Movies")
IsMember
 
'M: for members of Music
strGrp="Music"
strDriveLetter = "M:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Music]("file://\\ubuntu\Music")
IsMember
 
'Repeat for as many private groups and their respective enumerated shares as you wish.
'We're done with the login script.
 
'Let's tidy up variables first to make sure we're not leaving anything behind.
objNetwork = ""
strDriveLetter = ""
strRemotePath = ""
strUser = ""
strGrp = ""
strGroupADSPath = ""
strUserADSPath = ""
grp = ""
 
'That's all. Close the script processor.
wscript.quit
 
sub IsMember
'set the directory service path to enumerate the group
strGroupADSPath = "WinNT://[COLOR=red]**LANDGR.LB**[/COLOR]/" & strGrp & ",group"
'poll the PDC for the group
set grp = GetObject(strGroupADSPath)
'set the user directory service path to enumerate the user
strUserADSPath = "WinNT://**[COLOR=red]LANDGR.LB[/COLOR]**/" & strUser
'Check membership in the group.
If (grp.IsMember(strUserADSPath)) Then
'map the drive
objNetwork.MapNetworkDrive strDriveLetter, strRemotePath
End If
'clean up variables for next group check.
strGrp = ""
strDriveLetter = ""
strRemotePath = ""
'Rinse, lather and repeat this code as many times as needed.
End sub

```
 
Then execute flip -m logon.vbs
 
Make files logon.bat and logon.vbs executables
```

chown root:root logon.*
chmod 755 logon.*

```
 
Check when you login with roaming user if logon.bat executes. If not there is something wrong with your netlogon share in samba or some permissions are not set correctly.
 
Hope this works!

---

### Post by bluecartz on 2010-07-22
hi BULLET and others, i tried this tutorial and i made it up to the last part. I'm just a beginner in linux,We have Ubuntu 10 server,ubuntu 10 workstations and windows XP workstations. i just want to ask how can i make my ubuntu workstations connect to ubuntu server with this domain controller? since im just a beginner im not sure whats the 1st thing to do.hope you can help me with this one.

---

### Post by eck42 on 2010-07-25
After the reboot at STEP31 the server is showing a flashing cursor
fsck was performed. It shows as clean but flashing cursor. No login prompt.
I logged in via ssh and performed STEP 32 with the following error

root@rafs:/home/eric# smbldap-useradd -a -m -P user1
erreur LDAP: Can't contact master ldap server for writing (IO::Socket::INET: connect: Connection refused) at /usr/share/perl5/smbldap_tools.pm line 322.

I feel that I followed the directions correctly. However I had thaterror when trying to add a user at STEP 32.

Thought this was interesting when I ran "Top"

Cpu(s):  0.0%us,  0.2%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

1 root      20   0 57568 2752 1888 S    0  0.1   0:00.76 init


Any thoughts would be appreciated.
thanks
Eric

---

### Post by cancer07 on 2010-07-28
Hi, everyone!

I configured lucid the way described above. The process of configuring LDAP and SAMBA was OK all over the way, but when I tried to join a XP running machine, I got error message "Can't locate the network path". Can anyone help with this?

---

### Post by jessmagz on 2010-08-03
Sir:

I am a newbie with Linux. I just followed your step-by-step instructions but I'am stuck in Step #13. I am referring to the last 2 commands.

When I did:
cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap-> /schema/

I got an error:
bash: /schema/: Is a directory

I did not notice it so I proceeded to the last command:
gzip -d /etc/ldap/schema/samba.schema.gz

I got an error:
No such file or directory

Please advice on what might have caused this and how to proceed. This is my 4th attempt. The previous attampts ended with the re-installation of my server.

Thanks.

Jess

---

### Post by CyberPingU on 2010-08-03
Hi,
when I log in into the Linux Server using the root account, everything goes well.
Anyhow, when I log in with a username that I had previously created with 
> 
**Create/Delete/Manage Users:**
To Add: smbldap-useradd -a -m -P user
To Delete: smbldap-userdel user
To ChangePassword: smbldap-passwd user
 
**To add a Domain Administrator:**
-> smbldap-groupmod -m 'user' 'Administrators'
-> smbldap-groupmod -m 'user' 'Domain Admins'
-> auth-client-config -t nss -p lac_ldap

 
if I try to add a user to the domain, I get
 
$ smbldap-useradd -a -m -P username
Error: modifications require authentication at /usr/share/perl5/smbldap_tools.pm line 1187, <DATA> line 466.
 
Why cannot I create a new user, if I logged with a user flagged as Domain Administrator? Can only root do this?
And then... how do I set an expiration date with a must change day for passwords?
And how do I set permissions to let Domain Administrators change domain users' passwords and add/remove domain users without giving them the unix root account privileges?
Thanks for the answers, 
regards

---

### Post by CyberPingU on 2010-08-03
**@jessmagz**
 
You have to:
 
>  
# cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/
# gzip -d /etc/ldap/schema/samba.schema.gz


---

### Post by pcmb8866 on 2010-08-03
> Why cannot I create a new user, if I logged with a user flagged as Domain Administrator? Can only root do this?
And then... how do I set an expiration date with a must change day for passwords?
And how do I set permissions to let Domain Administrators change domain users' passwords and add/remove domain users without giving them the unix root account privileges?
Thanks for the answers, 
regardsEvery smbldap-... command can be used with "sudo smbldap-...". So you don't have to log in as root.
Setting the expiration date take a look at this site:
[http://search.cpan.org/~ghenry/Samba-LDAP-0.05/scripts/smbldap-usermod]("http://search.cpan.org/%7Eghenry/Samba-LDAP-0.05/scripts/smbldap-usermod").

Hope this will help

Peter.

---

### Post by upengan78 on 2010-08-03
Hello ,

Thanks! for creating such a nice HowTo.

All commands were successful for me but when I try to join the domain, it shows me error that Domain not found. If I try to join workgroup by the same name then it welcomes me.

Can anyone help me fix this issue?(Error screen shot attached from windows XP)

Thanks

EDIT,

Just remembered that this machine was not DHCP network. Once DHCP IP was assigned then I tried again to join domain and this time it did Welcome me. Sorry for the noise. :(

Good day

---

### Post by upengan78 on 2010-08-04
Hello guys,

I was able to configure winxp clients in the domain. Now I have added an apple os X in LDAP . Authentication and autofs works fine. (Using local files on OS X for autofs and not any automount map in LDAP)

I see a lot of messages in the log file on LDAP server,

```
root@upenubuntuser:/export# tail -f /var/log/debug 
Aug  4 09:04:38 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (cn) not indexed
Aug  4 09:04:38 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (uid) not indexed
Aug  4 09:04:38 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (cn) not indexed
Aug  4 09:04:38 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (uid) not indexed
Aug  4 09:04:38 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (cn) not indexed
Aug  4 09:04:39 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (memberUid) not indexed
Aug  4 09:04:40 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (uid) not indexed
Aug  4 09:04:40 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (cn) not indexed
Aug  4 09:04:40 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (uid) not indexed
Aug  4 09:04:40 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (cn) not indexed
Aug  4 09:05:30 upenubuntuser slapd[3137]: <= bdb_equality_candidates: (memberUid) not indexed

```There was one more issue that I forgot to mention while I configured samba+ldap using the nice tutorial.

```
# slapindex 

WARNING!
Runnig as root!
There's a fair chance slapd will fail to start.
Check file permissions!

root@upenubuntuser:/export# ls -ald /var/lib/ldap/
drwxr-x--- 2 openldap openldap 4096 2010-08-04 09:40 /var/lib/ldap/
```Is this normal or I missed on something that's why the messages?

If someone can throw some light, it will be great. I am trying to implement samba+ldap only because I have many Apple OS X client as well as winxp clients and I want security provided by LDAP. I already have samba + NIS working here.

Any help is appreciated.  (Also, if someone can find me docs or notes to add automount configuration into this LDAP configuration it will be great!)

Thanks.

---

### Post by Nakano on 2010-08-07
I've tried this twice now with no luck.. the second time I used a completely clean install and followed everything to the letter, but when I get to step 21 I get:


root@dwd:~# net getlocalsid
[2010/08/07 21:19:07,  0] utils/net.c:166(net_getlocalsid)
  Can't fetch domain SID for name: DWDFS

DWDFS is my netbios name, DWD is my workgroup, why is it trying to find my netbios name? 

when I do "net getlocalsid DWD" I get the right thing:

root@dwd:~# net getlocalsid DWD
SID for domain DWD is: S-1-5-21-3438458003-302388127-1581158526

so the first time I tried this tutorial, I continued on, and did a "new setlocalsid " with the SID returned for DWD and that let me get all the way through it, but I was then unable to add my windows 7 machine to the domain.

any help? "smbclient -L localhost" returns:

root@dwd:~# smbclient -L localhost                      Domain=[DWD] OS=[Unix] Server=[Samba 3.4.7]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers Share
        shared          Disk
        IPC$            IPC       IPC Service (Samba 3.4.7)
Domain=[DWD] OS=[Unix] Server=[Samba 3.4.7]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            NAKANO-PC

---

### Post by Nakano on 2010-08-08
Was able to get things working by setting my netbios name == my workgroup name, something the tutorial spells out that I specifically shouldn't do... yet it works, I was able to add my windows 7 box to the domain, things are good.. only problem I'm having is that when I add a user using the smbldap-useradd command, I then cannot authenticate against the domain, I get a message about "no login servers available"

Thanks for the great tutorial though, it really is a crazy complicated setup...

---

### Post by jthom263 on 2010-08-08
Hey Thanks For the Tutorial Mate, But So Far I Have Had One Problem, When I get Up **[COLOR=Red]STEP 26[/COLOR]**[COLOR=Black] I Type In The CMD And It Returns:[/COLOR] ```
No such object at /usr/share/perl5/smbldap_tools.pm line 961, <DATA> line 466.
``` I Also Had A Problem Before This In [COLOR=Red]**Step 25**[/COLOR] When I Typed In: ```
 chown openldap:openldap /var/lib/ldap/*
``` I Got the Error: ```
chown: cannot access `/var/lib/ldap/*': No such file or directory
``` After I Got this Error I Tried ```
chown openldap:openldap /var/lib/ldap
``` And I Think That Worked Because It Just Returned A Prompt For A new CMD.

Can Anyone Please Tell Me Where I Went Wrong?
Any help Will Will Be Dearly Appreciated,
Thanks In Advance, Jack. :)

---

### Post by v2ueha6 on 2010-08-11
I need to know if I will cause any problems if I follow the ubuntu ldap domain controller tutorial for Ubuntu 7.10 to setup webman  bind [http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p3](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p3) Because I know a lot of things changed in ubuntu v9 and v10.  The nice thing about setting up bind is that I can set certain machine using mac address so it gets the same ip address when it is on the home network and still leave it on dhcp for when traveling. Switching from dhcp to static address is hard for some people  This way my database server and mail server machines can just be plugged back into the network and they work.  Sometimes I demonstrate the at other locations.

---

### Post by sysardex on 2010-08-13
**2 [bulletxt]("http://ubuntuforums.org/member.php?u=110982"), **

Thank you for the very good manual. I'm all set and I have works well. But I would like to further understand how to configure Slave domain server and configure replication ldap. Can somebody tell me how to do this?

---

### Post by Davide911 on 2010-08-13
Also for me this tutorial is very very wonderful. All ok at the first try.


> **david.garceau said:**
> My only question now is if you could provide any information on setting up a pdc with a bdc both using the same ldap server which is located on the pdc. Any help would greatly be appreciated.

Like david.garceau, now I would like to install a BDC, Any help would greatly be appreciated.

Ciao, Davide

---

### Post by TheRiX on 2010-08-14
> **bulletxt said:**
> 
**To make your PDC automatically map net drives:**
-> apt-get install flip
->  > /var/lib/samba/netlogon/allusers.bat
In this example you'll have a shared folder for all users, of course you can edit /etc/samba/smb.conf to create specific user shares.
-> mkdir -p /var/lib/samba/shared/
-> chmod -R 777 /var/lib/samba/shared/
-> nano /var/lib/samba/netlogon/allusers.bat
NOTE: change "PSAMBA" with the Netbios name set in step 9. Change drive "m:" to any letter you prefer.
-> flip -m /var/lib/samba/netlogon/allusers.bat

Just a FYI 
->nano -D /var/lib/samba/netlogon/allusers.bat
would work instead of installing flip and using it to convert it over to DOS readable format.

Other than that, great guide. Still get errors with smbclient -L localhost, but pressing enter on the password field allowed it to go ahead and give me the info from that. With the password it gives NT_STATUS_UNKNOWN_USER_OR_BAD_PASSWORD or something to that effect.

---

### Post by nixnotwin on 2010-08-18
> **pcmb8866 said:**
> nixnotwin:
I found another way to map drives to shares. Using VB-script
 
Change your logon.bat file in folder netlogon to:
```

cscript [\\ubuntu\netlogon\logon.vbs]("file://\\ubuntu\netlogon\logon.vbs")

```
Changing ubuntu to your servername.
 
Then execute flip -m logon.bat
 
Add a file logon.vbs in your netlogon folder
```

touch logon.vbs

```
 
Edit logon.vbs and add the following code changing "[COLOR=red]**ubuntu**[/COLOR]" to your **NETBIOSname** and "[COLOR=red]**LANDGR.LB**[/COLOR]" to your **WORKGROUPname** in smb.conf:
```

'First make sure all variables are dimensioned.
'This isn't necessary for functionality; it's for coding discipline only.
Option Explicit
 
'dimension all our variables
dim objNetwork
dim strDriveLetter, strRemotePath, strUser, strGrp
dim strGroupADSPath, strUserADSPath, grp
dim oDrives, i
 
'This script will use the MapNetworkDrive method
'for each network drive mapped.
 
'Delete already mapped network drives
On error resume next 
 
'We'll be using the Wscript.Network Object to enumerate the user as well as to map drives.
'We only need to instantiate it once at the beginning.
 
Set objNetwork = WScript.CreateObject("WScript.Network") 
Set oDrives = objNetwork.EnumNetworkDrives 
 
For i = 0 to oDrives.Count - 1 Step 2 
objNetwork.RemoveNetworkDrive oDrives.Item(i),true,true 
Next 
 
'First let's get the user name since we'll use it for mapping the home directory
'as well as checking group memberships.
strUser = objNetwork.UserName
 
'User Drive to H:
strDriveLetter = "H:"
strRemotePath = "\\[COLOR=red]**ubuntu**[/COLOR]"
objNetwork.MapNetworkDrive strDriveLetter, strRemotePath & "\" & strUser
 
'next we'll enumerate groups and map drives for specific departmental memberships
'The code to check for memberships and map the drives is in a subroutine called IsMember.
'All we have to do is copy the same block over again for each group membership we want to check.
'The block only needs to set the string values for the group name, the desired drive letter, and the share path.
'Then it calls the IsMember subroutine down below.
 
'N: for members of _[COLOR=#0066cc]Department[/COLOR]_
strGrp="Dept"
strDriveLetter = "N:"
strRemotePath = [\\**[COLOR=red]ubuntu[/COLOR]**\Department]("file://\\ubuntu\Department")
IsMember
 
'P: for members of Apps
strGrp="Apps"
strDriveLetter = "P:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Application]("file://\\ubuntu\Application")
IsMember
 
'I: for members of Common
strGrp="Common"
strDriveLetter = "I:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Common]("file://\\ubuntu\Common")
IsMember
 
'L: for members of Movies
strGrp="Movies"
strDriveLetter = "L:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Movies]("file://\\ubuntu\Movies")
IsMember
 
'M: for members of Music
strGrp="Music"
strDriveLetter = "M:"
strRemotePath = [\\[COLOR=red]**ubuntu**[/COLOR]\Music]("file://\\ubuntu\Music")
IsMember
 
'Repeat for as many private groups and their respective enumerated shares as you wish.
'We're done with the login script.
 
'Let's tidy up variables first to make sure we're not leaving anything behind.
objNetwork = ""
strDriveLetter = ""
strRemotePath = ""
strUser = ""
strGrp = ""
strGroupADSPath = ""
strUserADSPath = ""
grp = ""
 
'That's all. Close the script processor.
wscript.quit
 
sub IsMember
'set the directory service path to enumerate the group
strGroupADSPath = "WinNT://[COLOR=red]**LANDGR.LB**[/COLOR]/" & strGrp & ",group"
'poll the PDC for the group
set grp = GetObject(strGroupADSPath)
'set the user directory service path to enumerate the user
strUserADSPath = "WinNT://**[COLOR=red]LANDGR.LB[/COLOR]**/" & strUser
'Check membership in the group.
If (grp.IsMember(strUserADSPath)) Then
'map the drive
objNetwork.MapNetworkDrive strDriveLetter, strRemotePath
End If
'clean up variables for next group check.
strGrp = ""
strDriveLetter = ""
strRemotePath = ""
'Rinse, lather and repeat this code as many times as needed.
End sub

```
 
Then execute flip -m logon.vbs
 
Make files logon.bat and logon.vbs executables
```

chown root:root logon.*
chmod 755 logon.*

```
 
Check when you login with roaming user if logon.bat executes. If not there is something wrong with your netlogon share in samba or some permissions are not set correctly.
 
Hope this works!

Thanks pcmb8866. Soon I will be experimenting with your alternative solution. I will let you know the results.

---

### Post by Understandmoe on 2010-08-19
Does anyone know if it is possible to have Mac snow leopard join this domain. Every time I try to join the domain I get an error message.

---

### Post by LoveJoyDK on 2010-08-21
> **bulletxt said:**
> Sorry, I have decided to rewrite this manual as it was incomplete in some areas, including roaming profiles and so on. It also had some errors.
 
I will update it soon.
 
But was it needed to take away the old one from us?
 
Just spend days on getting a server to run after your very helpfull HowTo. And now after tweaking it, I find my reference to my first steps are gone.
 
 
It was still a good help even if a bit outdated.
LoveJoy sad.
 
N.B: for others in same need. I found the google cache.
[http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk](http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk)
 
[IMG]http://farm3.static.flickr.com/2287/2492671049_4afaef7fbc_o.gif[/IMG]

---

### Post by shadowwup on 2010-08-26
**EDIT** RESOLVED this by changing the password program to use smbldap-passwd


About a month ago 45days I implemented this guide and everything worked like a dream.
However I have now run into a password expiry problem and am unsure on how to proceed.
Basically when logging into the domain thru a pc running windows 7 I am told that my password has expired and needs to be changed. I change the password and I receive a password change successful message. When I try to relogin I keep getting the same password expired message.

If I attempt to login to the linux box with the same user account I get:

```
Last login: Thu Aug 26 11:19:54 2010 from 10.1.0.100
WARNING: Your password has expired.
You must change your password now and login again!
Changing password for USER_X
(current) NT password:
```Typing in the old password or the newly changed one I get:

```
passwd: Authentication information cannot be recovered
passwd: password unchanged
```If logged in on the linux box as an admin and I su to USER_X I get:

```
You are required to change your password immediately (password aged)
su: Authentication token is no longer valid; new one required
(Ignored)
```I have tried changing the password using slappasswd and smbpasswd to no avail.

Anyone come across this issue? Can anyone help me out?

I can see the following in syslog

```
Aug 26 12:35:36 madelx01 slapd[23654]: SASL [conn=1117] Failure: realm changed: authentication aborted
Aug 26 12:37:10 madelx01 sudo: pam_ldap: error trying to bind as user "uid=USER_X,ou=Users,dc=mscpdc" (Invalid credentials)
Aug 26 12:37:14 madelx01 sudo: pam_ldap: error trying to bind as user "uid=USER_X,ou=Users,dc=mscpdc" (Invalid credentials)
```in the samba log for the machine I can see:
```
[2010/08/25 18:07:36,  1] smbd/service.c:1063(make_connection_snum)
  made-richardj (10.1.0.100) signed connect to service Profiles initially as user USER_X (uid=1001, gid=513) (pid 8954)
[2010/08/25 18:07:50,  1] smbd/service.c:1240(close_cnum)
  made-richardj (10.1.0.100) closed connection to service USER_X
[2010/08/25 18:08:02,  1] smbd/service.c:1240(close_cnum)
  made-richardj (10.1.0.100) closed connection to service Profiles
[2010/08/25 18:08:02,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/25 18:08:02,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/08/26 11:08:59,  0] rpc_server/srv_netlog_nt.c:603(_netr_ServerAuthenticate3)
  _netr_ServerAuthenticate3: netlogon_creds_server_check failed. Rejecting auth request from client MADE-1 machine account MADE-1$
[2010/08/26 11:08:59,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:08:59,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:09:50,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/26 11:09:50,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/08/26 11:09:52,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:09:52,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:09:55,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:09:55,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:10:16,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:10:16,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:10:38,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/26 11:10:38,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer
```.

---

### Post by rayne127 on 2010-08-27
Hi-

I am having an issue setting up Samba to authenticate with LDAP.

I currently have openLDAP installed and set up, I'm able to connect to it and view my tree through phpLDAPadmin. I also have Samba set up as a PDC, which is also working fine (I've been able to connect my Win2k computer to it for testing purposes).

I'm following the tutorial on the Ubuntu website ([https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html")), and I'm stuck at step 5. Whenever I try to add the new schema to my directory, I get an error saying 'Insufficient Access'. I don't understand why I'm not able to add this even though I'm connecting as cn=admin?

Anybody able to help or provide a better tutorial for setting up Samba PDC w/ LDAP?

Thank you so much!
Adam

---

### Post by pcmb8866 on 2010-08-29
> **rayne127 said:**
> Hi-
 
I am having an issue setting up Samba to authenticate with LDAP.
 
I currently have openLDAP installed and set up, I'm able to connect to it and view my tree through phpLDAPadmin. I also have Samba set up as a PDC, which is also working fine (I've been able to connect my Win2k computer to it for testing purposes).
 
I'm following the tutorial on the Ubuntu website ([https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)), and I'm stuck at step 5. Whenever I try to add the new schema to my directory, I get an error saying 'Insufficient Access'. I don't understand why I'm not able to add this even though I'm connecting as cn=admin?
 
Anybody able to help or provide a better tutorial for setting up Samba PDC w/ LDAP?
 
Thank you so much!
Adam
 
Use this awesome tutorial from bulletxt (a bit outdated, but works excellent). He is rewriting it.
 
_[COLOR=#0066cc][http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk]("http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk")[/COLOR]_[[COLOR=#444444][/COLOR]]("http://webcache.googleusercontent.co...&ct=clnk&gl=dk")

---

### Post by rayne127 on 2010-08-29
> **pcmb8866 said:**
> Use this awesome tutorial from bulletxt (a bit outdated, but works excellent). He is rewriting it.
 
_[COLOR=#0066cc][http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk]("http://webcache.googleusercontent.com/search?q=cache:hA59pMAkJRsJ:ubuntuforums.org/showthread.php%3Ft%3D1499753+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=3&hl=en&ct=clnk&gl=dk")[/COLOR]_[[COLOR=#444444][/COLOR]]("http://webcache.googleusercontent.co...&ct=clnk&gl=dk")

Thanks, I would love to... from all the comments I've read on the thread it seems to work great. However, it's not longer up. 

=( I guess I'll keep checking back to see when it's posted again.

---

### Post by ottabaub on 2010-09-01
> **pcmb8866 said:**
> [FONT=Times New Roman][SIZE=3]**Setting up ldap, samba, roaming profiles and netlogon to mount shares according to groupmembership...**[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]! Read entire post before trying ![/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I use:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]LDAP:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dc=landgr,dc=lb (change to yours) instead of dc=pdc[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]SAMBA:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Workgroup: LANDGR (change to yours)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Netbios name: UBUNTU (change to yours) must not be the same as workgroup[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have my netlogon and profiles all under /home because this is the disk with most space available. (change to yours)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]All shares are also under /home.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]NETLOGON:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]KIXTART (Scripting language to check groupmembership)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]First install and configure ldap as descripted in post #1 changing all entries dc=pdc to yours. For me it was dc=landgr,dc=lb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Also change password “pwd123” to your own. ([COLOR=red]**CHANGE IT EVERYWHERE**[/COLOR])[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]At point 9 I didn't download smb.conf. I use my own. See below:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]At point 13 I changed (only for me)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-> mkdir -v /home/samba-ntprof (profiles)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]-> chmod 777 /home/samba-ntprof[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]-> mkdir -v -p /home/netlogon (netlogon)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]-> chmod 777 /home/netlogon [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]When you have installed smbldap-tools make sure that the entries in the file smbldap.conf are as shown:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add groups to ldap:[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Don't forget to use the -a option!![/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Create your shares:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add users to ldap:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add user to groups:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Download KIXTART from [http://www.kixtart.org]("http://www.kixtart.org/")[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Extract the zip file.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Copy KIX32.exe to your netlogon.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]In your netlogon add file logon.bat [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Save – close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In netlogon add file logon.kix[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Save – close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]One more step to go:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]REBOOT[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Now you should be able to log in with user1 en user2 and the drive letters should be mounted to the shares.[/SIZE][/FONT]
Pictures of result:
[http://www.codior.nl/sambashares/](http://www.codior.nl/sambashares/)
 
**One last TIP:**
 
**[COLOR=red]CHECK, CHECK, DOUBLE CHECK[/COLOR]**
**[COLOR=#ff0000]Also pay attention to BULLETXT post regarding NETBIOS name, workgroup name and password.[/COLOR]**
**[COLOR=#ff0000]Don' be hasty[/COLOR]** 
 
I've got mine working flawless, like a charme with Windows XP and Windows 7
 
 
**[FONT=Times New Roman][SIZE=3]When samba won't start automatic after reboot.[/SIZE][/FONT]**..
[FONT=Times New Roman][SIZE=3]When you have the same trouble as I did that samba won't start after reboot there is a workaround.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The problem is the new “UPSTART JOB”[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Workaround:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Rename /etc/init/smbd.conf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv /etc/init/smbd.conf /etc/init/smbd.conf.org[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Rename /etc/init/nmbd.conf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mv /etc/init/nmbd.conf /etc/init/nmbd.conf.org[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Add samba to /etc/init.d[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]touch /etc/init.d/samba[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nano /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Add:[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Save – close[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]chown root:root /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]chmod 755 /etc/init.d/samba[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]update-rc.d samba start 52 2 3 4 5 . stop 52 0 1 6 .[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]REBOOT[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]All should work now because samba starts when ldap is already running.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]With this workaround when you have to restart samba in the future you must use:[/FONT][/SIZE]
```

[SIZE=3][FONT=Times New Roman]/etc/init.d/samba start / restart / stop[/FONT][/SIZE]

```


Actually, from what I can gather, in 10.04 we're supposed to use:
   *sudo service smbd start / restart / stop*

---

### Post by nixnotwin on 2010-09-01
The link for the guide from google cache posted above doesn't show the original post.

Here is another link

[http://webcache.googleusercontent.com/search?q=cache:A6J-35iY0YsJ:www.uluga.ubuntuforums.org/showthread.php%3Ft%3D1499753+cache:+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=5&hl=en&ct=clnk&gl=in](http://webcache.googleusercontent.com/search?q=cache:A6J-35iY0YsJ:www.uluga.ubuntuforums.org/showthread.php%3Ft%3D1499753+cache:+Ubuntu+10.04+Samba+Primary+Domain+Controller+with+LDAP&cd=5&hl=en&ct=clnk&gl=in)

---

### Post by uoL on 2010-09-02
Could you post the old how to again ?.. 
it doesn't matter if it's not updated but I need it and google has not cached it :(

Thanks !

---

### Post by madeulook967 on 2010-09-13
Thank goodness for bulletxt's instructions, I managed to get this set up.  :) I managed to get Windows XP machines to join the domain but i am now having trouble getting my Macs on 10.6.4 binding to the PDC.  To do this on the MBP, I go to System Preferences -> Accounts -> Login Options -> Join

I've tried the following: 
1.  From there I've tried entering the domain name, the IP - [http://192.XXX](http://192.XXX)..., but I get "Unable to add server. Could not resolve the address.  (2200)"

2.  From Join, going to Open Directory Utility, I enable Active Directory, and enter the domain details respectively. For me Active Directory Domain=servername, Username and Password as admin details as set up in Samba PDC.

3.  Ran it from Terminal too - but got a similar error - "An invalid Domain was specified.  You should enter a fully qualified DNS name for the domain (e.g., ads.company.com)."

Has anyone managed to connect their Mac's to this?  Is there's something I'm doing wrong?  I've googled, read and watched a killion tutorials and forums but to no avail.  

Greatly appreciate anyone who can help me out on this. 

Thanks a bunch!

S.

---

### Post by Korsakof on 2010-09-16
> **bulletxt said:**
> Sorry, I have decided to rewrite this manual as it was incomplete in some areas, including roaming profiles and so on. It also had some errors.

I will update it soon.

Please... Leave the original post in place until the new revision is ready. I really need this kind of stuff.

thanks

---

### Post by spliner on 2010-09-17
Are we any closer to a re-write?  How about the original tutorial, if anyone has a copy would you pm me?  Thanks!

Spliner

---

### Post by rmax75 on 2010-09-19
I'm looking forward to read your howto.

Great work,
Massimo

---

### Post by wizard210 on 2010-09-20
This is exactly what I'm looking for. Please does anyone have the orginal. If so please PM with me with it. 

When do you think we can expect the rewrite?

---

### Post by AndrewDarnell on 2010-09-20
[http://www.server-world.info/en/note?os=Ubuntu_10.04&p=install](http://www.server-world.info/en/note?os=Ubuntu_10.04&p=install)

this site has many how-to's for the current ubuntu build.

---

### Post by wizard210 on 2010-09-20
does anyone know if the guide from Ricky works on 10.04

---

### Post by CyberPingU on 2010-09-25
Hi all,
since the very first post (the guide, in other words) is not available anymore, nor the google's cache (that has been updated)... is there anyone that did save the page and/or the guide and would mail it to me, or let me read it in some how?
Thanks for your replies...

PS. Any luck, Spliner?

---

### Post by spliner on 2010-09-27
No luck.. I saved the 'Tips and Tricks' on a whim, but did not save the whole tutorial.  I had intended to compare it to Rikcy's original guide and create a hybrid tutorial for myself but it dissapeared in this thread too quickly.

Spliner

Scratch that.. below is a copy of the original guide that I managed to dig up using different web caches.  Keep in mind, the author seems to think it is broken and has removed it, however a rewrite does not seem to be forthcoming at the moment.  Use at your own risk (as I and the author likely can't help with issues), and had it not been originally submitted here as a guide I would not be re-posting it.  It did work for me, but has some glitches here and there, and does not cover everything.  IF I have time later I may use it and the original 7.04/8.04 guide by Ricky and see if a hybrid can be made, but I generally have no time for this stuff these days so no promises.

Here you go:

Please note this guide is outdated and is being re-written by the author.  Use at your own risk:


```
Hi all,

Hi everyone, after digging over the net and after spending a lot of time trying to understand how things work, I'm proud to present a very quick and super easy tutorial to create a Samba Primary Domain Controller with LDAP integration inside Ubuntu 10.04, both 32bit and 64bit.

In less than 30 minutes you'll have:
- A fully working PDC for Windows Clients
- Roaming profiles NOT enabled (this is what most of you want)
- Be able to have shared folders automatically mounted when a user logs into the domain
- Tested and fully working with(all flavours): Windows XP, Windows Vista and even Windows 7!

If you do everything exactly like I wrote I guarantee it will work. One single error can compromise everything and you'll have to restart from the beginning! You have been warned!

General Information before reading:
- In this guide each step will have a number, so if you ever have to ask me a question be sure you point the exact number, I will ignore any posts without the number being explicited.
- Commands you must type start with a "->".
- The guide presumes you know how to use Nano text editor (or any other text editor from shell like Vim).
- In this guide my default password is always "pwd123".

Let's Start.

1)
Install Ubuntu Server 10.04 32Bit or 64Bit
Once Ubuntu 10.04 is up, log with root user:
-> sudo su
From now on I assume you are always root user.

2)
Set a static IP,
in this example the NIC card is eth0 and the network is part of 192.168.1.x class.
-> nano /etc/network/interfaces

Quote:
auto lo eth0
iface lo inet loopback
iface eth0 inet static
address 192.168.1.10
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.1 

3)
-> /etc/init.d/networking restart
-> ifconfig
The output should show you the static IP, try pinging a local IP or an internet IP to be sure you are on the net, ex:
-> ping [www.google.it](www.google.it)
or try pinging your gateway set before:
-> ping 192.168.1.1
If you are unsure, reboot your machine to see if "ifconfig" command still shows you the same IP and to be sure you're still part of the network by pinging as said before.
ONCE YOU FINISHED WITH THIS GUIDE, IF YOU EVER CHANGE YOUR IP BE SURE TO READ SECTION: "TIPS AND TRICKS", FOUND AT THE END OF THIS GUIDE OR YOUR PDC WILL STOP WORKING.

4)
-> apt-get update
-> apt-get dist-upgrade
-> reboot
-> sudo su

5)
-> apt-get install slapd ldap-utils
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

6)
-> > backend.example.com.ldif
Your next step will be to modify this file, the only thing you should care of changing is the password, which is set at line "olcRootPW:". By default password is "pwd123".
-> nano backend.example.com.ldif

Quote:
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb 
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=pdc
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=pdc
olcRootPW: pwd123
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=pdc" write by * read
 


7)
From now on, if ldap commands similar to this ask for a password, put password set above in step 6, by default in this guide as said "pwd123".
-> ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif

8)
-> apt-get install samba samba-doc libpam-smbpass smbclient smbldap-tools

9)
Now I'll make you download my samba configuration file.
-> wget [http://digilander.libero.it/bulletxt...10.04/smb.conf](http://digilander.libero.it/bulletxt...10.04/smb.conf)
After downloading it, you'll have to change ONLY two values: "workgroup = " and "netbios = ".
Workgroup is the name of the Domain. This is the name that you'll have to enter in a Windows client to make it join the domain. Netbios is instead the name used to browse shared folders, for example in Windows you'll put "\\$netbiosname\$shared_folder".
DO NOT PUT WORKGROUP NAME IDENTICAL TO NETBIOS NAME.
IMPORTANT: carefully decide the NETBIOS name, once you change it YOU CAN'T CHANGE IT AGAIN OTHERWISE IT WILL BREAK EVERYTHING! YOU'VE BEEN WARNED.
Type the following and change the two values.
-> nano smb.conf
Once you changed the two values type:
-> cp -rf smb.conf /etc/samba/smb.conf

10)
In the next command it will prompt you to put a password, this must be the same as set before in step 6, by default in this guide "pwd123"
-> smbpasswd -W

11)
-> service smbd restart

12)
Now you must check that samba is running, it will ask you for a password, just hit Enter.
-> smbclient -L localhost
It should not give you any errors, instead it must show some stuff and you should see your Workgroup Name set in step 9

13)
-> mkdir -v /var/lib/samba/profiles
-> chmod 777 /var/lib/samba/profiles
-> mkdir -v -p /var/lib/samba/netlogon
-> chmod 777 /var/lib/samba/netlogon
-> cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap-> /schema/
-> gzip -d /etc/ldap/schema/samba.schema.gz

14)
-> > schema_convert.conf
-> nano schema_convert.conf

Quote:
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema 

15)
-> mkdir /tmp/ldif_output
-> slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/cn=samba.ldif

16)
Now you'll have to edit a file, open the file with the following command and read below to understand what must be edited.
-> nano /tmp/cn\=samba.ldif
At the very top you'll see:

Quote:
dn: cn{12}=samba,cn=schema,cn=config 

Change it to:

Quote:
dn: cn=samba,cn=schema,cn=config 

Always at the top you'll see:

Quote:
cn: {12}samba 

Change it to:

Quote:
cn: samba 

At the end of the file you'll see:

Quote:
structuralObjectClass: olcSchemaConfig
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95
creatorsName: cn=config
createTimestamp: 20080827045234Z
entryCSN: 20080827045234.341425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080827045234Z 

Delete all those lines, save and close.

17)
Be sure the following command does not give errors:
-> ldapadd -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif

18)
-> > samba_indexes.ldif
-> nano samba_indexes.ldif

Quote:
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub 

19)
Be sure the following does not give any errors.
-> ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif

20)
Now thanks to the following command, you'll finally understand if everything till now went fine. If everything goes fine, it will output a lot of stuff, including at the end strings similar to the ones found in step 18
-> ldapsearch -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -b cn=config -W olcDatabase={1}hdb

21)
Now that ldap is working perfectly, we must also be sure Samba is working too.
The following command MUST not give errors, and it must output something similar to this:

Quote:
SID for domain DOMAIN is: S-1-5-21-908678672-1104131578-2020688504 

So this is the command to type:
-> net getlocalsid

22)
-> gzip -d /usr/share/doc/smbldap-tools/configure.pl.gz

23)
Next command is crucial to make Samba and Ldap work together. When prompted,
press always Enter without inserting anything. There are only two cases where you must type something.
When it asks for "Logon Home" and "Logon Path", put a "." character.
At a certain point, it will ask you for a password two times, once for ldap bind master and then for ldap bind slave. In both cases, you must put the exact same password you put in step 6, by default in this guide "pwd123".
So now you know what to do, this is the command:
-> perl /usr/share/doc/smbldap-tools/configure.pl

24)
Following command should create some groups, at the end it will ask for a password. As always put password provided in step 6, default of this guide is "pwd123".
-> smbldap-populate

25)
-> /etc/init.d/slapd stop
-> slapindex 
-> chown openldap:openldap /var/lib/ldap/*
-> /etc/init.d/slapd start

26)
If everything till now is really working, the next command will make user "root" be a Domain Administrator.
In section "Tips and Tricks" you'll see how to make other users be a Domain admin.
THIS COMMAND MUST NOT GIVE ERRORS, otherwise it means LDAP is not working with Samba.
-> smbldap-groupmod -m 'root' 'Administrators'

27)
In the next command, it will ask you for some stuff. Do not make errors here!
When it asks for questions that want a Yes/No reply, just press Enter leaving default.
When it asks for LDAP server Uniform Resource Identifier, leave it as it is "ldapi:///"
When it asks for Distinguished name of the search base, put "dc=pdc"
When it asks for LDAP account for root, put "cn=admin, dc=pdc"
When it asks for LDAP password, put the same set in step 6, default of this guide was "pwd123"

The command is:
-> apt-get --yes install ldap-auth-client

IMPORTANT: if you do a mistake, you can reconfigure the previous command typing:
-> dpkg-reconfigure ldap-auth-config

28)
-> auth-client-config -t nss -p lac_ldap

29)
The following command is used to enable Unix, Ldap and Samba authentication.
Be sure all of them are selected with "*" character and press Enter.
The command is:
-> pam-auth-update ldap

30)
The following command should output something similar to this:

Quote:
Domain Admins:*:512:root
Domain Users:*:513:
Domain Guests:*:514:
Domain Computers:*:515:
Administrators:*:544:root
Account Operators:*:548:
Print Operators:*:550:
Backup Operators:*:551:
Replicators:*:552: 

The command is:
-> getent group

31)
-> reboot

32)
Good, we're done. After reboot, let's check that everything is working by creating a user.
-> sudo su
If the following command does not give errors, it means Samba and Ldap are both working together, and you should be happy! It will ask for a password, the password is the password you want for the user, in this case for user "user1":
-> smbldap-useradd -a -m -P user1

33) 
If you reached this step without errors, it means you are ready to make your Windows Clients join the domain.
However for security reasons it's not a good idea to make your customer know the password of "root" account. At the moment, to make a Windows Client join the domain you'll have to put user "root" and its password, let's instead make another user which will be part of the Domain Administrators. We'll call the user "adminpdc".
-> smbldap-useradd -a -m -P adminpdc
-> smbldap-groupmod -m ' adminpdc' 'Administrators'
-> smbldap-groupmod -m ' adminpdc' 'Domain Admins'
-> sudo auth-client-config -t nss -p lac_ldap

Good, now we have user "adminpdc" that is a Domain Administrator but is in no way a possible security danger for your Linux machine, since it's not part of sudoers. In this way you'll never have to use account "root" to make a Windows client join the domain or to make changes to the Windows client OS.

Finally, make your Windows Client (xp,vista,7) join the domain! :
- In Windows XP, right click on Computer->Properties and click on Change as seen here: [http://www.iaji.net/wp-content/uploa...uter_name3.png](http://www.iaji.net/wp-content/uploa...uter_name3.png)
- For Windows Vista and 7 instead, right click on Computer, on the left click on Advanced Settings and then click on "Change" under "Computer Name" Tab.

IMPORTANT ABOUT WINDOWS 7:
To make Windows 7 be part of the domain, read below section Tips and Tricks.

- As domain, put the workgroup name you set in step 9
- When it asks for username and password, put "adminpdc" and the password of this user, you set this on step 33. If everything goes well it will say you joined the domain and you must reboot.

That's all!

TIPS AND TRICKS:

Create/Delete/Manage Users:
To Add: smbldap-useradd -a -m -P user
To Delete: smbldap-userdel user
To ChangePassword: smbldap-passwd user

To add a Domain Administrator:
-> smbldap-groupmod -m 'user' 'Administrators'
-> smbldap-groupmod -m 'user' 'Domain Admins'
-> auth-client-config -t nss -p lac_ldap

If you ever change the static IP of the PDC:
-> service smbd stop
-> rm /var/cache/samba/browse.dat 
-> rm /var/cache/samba/login_cache.tdb
-> rm /var/lib/samba/wins.dat
-> reboot

To make Windows 7 join the domain:
- Download this file and click on it: [https://bugzilla.samba.org/attachmen...88&action=view](https://bugzilla.samba.org/attachmen...88&action=view)
- Reboot Windows 7
- Make Windows 7 join the domain. It will say it joined the domain but then it will give you a DNS error. Ignore it and reboot again Windows 7
- You should now be part of the domain

To make your PDC automatically map net drives:
-> apt-get install flip
-> > /var/lib/samba/netlogon/allusers.bat
In this example you'll have a shared folder for all users, of course you can edit /etc/samba/smb.conf to create specific user shares.
-> mkdir -p /var/lib/samba/shared/
-> chmod -R 777 /var/lib/samba/shared/
-> nano /var/lib/samba/netlogon/allusers.bat
NOTE: change "PSAMBA" with the Netbios name set in step 9. Change drive "m:" to any letter you prefer.

Quote:
@echo off
net use m: /delete
net use m: "\\PSAMBA\shared" 

-> flip -m /var/lib/samba/netlogon/allusers.bat

```

---

### Post by CyberPingU on 2010-09-27
Thanks Spliner for your post. I'm sure that the author will understand that you posted just to let us continue out tests. 
Luckily Windows 7 is not that used where I work, and the guide is good enough for our production environment.
Meanwhile we'll wait for Bull's news.
Thanks again =)

---

### Post by vanceibz on 2010-09-29
Thanks Spliner for the post, I am stuck on step 9, where I need to download the smb.conf from [http://digilander.libero.it/bulletxt...10.04/smb.conf](http://digilander.libero.it/bulletxt...10.04/smb.conf) Its not available on their server. Anyone can post it here would be great, I have searched the net but with no luck.

Best regards

---

### Post by 13thMonkey on 2010-09-29
```
http://digilander.libero.it/bulletxt/Samba_PDC_Ubuntu-10.04/smb.conf
```

---

### Post by vanceibz on 2010-10-01
Thanks 13thMonkey, Its my second install because I couldnt get the xp to join the domain.. must have missed something. I get an error on step 6, when running command: ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif

```


root@vserver:/home/adminpdc# ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
ldapadd: attributeDescription "dn": (possible missing newline after line 7, entry "cn=module,cn=config"?)
adding new entry "cn=module,cn=config"
ldap_add: Invalid syntax (21)
        additional info: objectClass: value #2 invalid per syntax


```

This is the ldif config:

```

dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=pdc
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=pdc
olcRootPW: pwd123
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=pdc" write by * read

```

---

### Post by vanceibz on 2010-10-01
ok, well dont know if it was that but now I have executed the command successfully. I added a space between exactly like to file pasted. see below. And worked.

```

olcModuleload: back_hdb

dn: olcDatabase=hdb,cn=config

```

---

### Post by vanceibz on 2010-10-01
following the steps very carefully I was getting a "NT_STATUS_CONNECTION_REFUSED" when running the command "smbclient -L localhost" 

I have been searching the net for a long while and making changes, got it working. Went back to the original smb.conf / changed everything back to the original to find the problem and, rebooted and still working. ??? strange.

Now I'm getting an error with "net getlocalsid", must be something with the smb.conf

```

root@vserver:/home/adminpdc# net getlocalsid
[2010/10/01 17:19:13,  0] utils/net.c:166(net_getlocalsid)
  Can't fetch domain SID for name: NETVILA


```

Any help would be appreciated..

---

### Post by vanceibz on 2010-10-02
ok finally got it working. Can login in the domain with XP. GREAT!!

So what i did.

I followed this guide until step 5. Then followed this one [http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

And worked the first time. 

Thanks for the great howto's and help from all.

---

### Post by Fruguy101 on 2010-10-04
when will the updated guide be posted? i would very much like to use it, but can't since there's no guide to use.

---

### Post by gyimesia on 2010-10-04
Hello!

I cant see the tutorial. Where is it?

thanks

---

### Post by spliner on 2010-10-04
> **gyimesia said:**
> Hello!

I cant see the tutorial. Where is it?

thanks

I re-posted the original guide on post #129 of this thread.  Some of the files linked in the original post are no longer there as the author pulled them down, so be sure to read on the next few posts after that since others have posted solutions.  I have no time to write a new guide, still hoping the author will post one soon.  I was able to get his original guide to work for me with a few changes, however I did not write those changes down when I made them.  So if you run into issues post in this thread and we can try and help if we spot something wrong.

Spliner

---

### Post by upengan78 on 2010-10-25
> **shadowwup said:**
> **EDIT** RESOLVED this by changing the password program to use smbldap-passwd


About a month ago 45days I implemented this guide and everything worked like a dream.
However I have now run into a password expiry problem and am unsure on how to proceed.
Basically when logging into the domain thru a pc running windows 7 I am told that my password has expired and needs to be changed. I change the password and I receive a password change successful message. When I try to relogin I keep getting the same password expired message.

If I attempt to login to the linux box with the same user account I get:

```
Last login: Thu Aug 26 11:19:54 2010 from 10.1.0.100
WARNING: Your password has expired.
You must change your password now and login again!
Changing password for USER_X
(current) NT password:
```Typing in the old password or the newly changed one I get:

```
passwd: Authentication information cannot be recovered
passwd: password unchanged
```If logged in on the linux box as an admin and I su to USER_X I get:

```
You are required to change your password immediately (password aged)
su: Authentication token is no longer valid; new one required
(Ignored)
```I have tried changing the password using slappasswd and smbpasswd to no avail.

Anyone come across this issue? Can anyone help me out?

I can see the following in syslog

```
Aug 26 12:35:36 madelx01 slapd[23654]: SASL [conn=1117] Failure: realm changed: authentication aborted
Aug 26 12:37:10 madelx01 sudo: pam_ldap: error trying to bind as user "uid=USER_X,ou=Users,dc=mscpdc" (Invalid credentials)
Aug 26 12:37:14 madelx01 sudo: pam_ldap: error trying to bind as user "uid=USER_X,ou=Users,dc=mscpdc" (Invalid credentials)
```in the samba log for the machine I can see:
```
[2010/08/25 18:07:36,  1] smbd/service.c:1063(make_connection_snum)
  made-richardj (10.1.0.100) signed connect to service Profiles initially as user USER_X (uid=1001, gid=513) (pid 8954)
[2010/08/25 18:07:50,  1] smbd/service.c:1240(close_cnum)
  made-richardj (10.1.0.100) closed connection to service USER_X
[2010/08/25 18:08:02,  1] smbd/service.c:1240(close_cnum)
  made-richardj (10.1.0.100) closed connection to service Profiles
[2010/08/25 18:08:02,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/25 18:08:02,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/08/26 11:08:59,  0] rpc_server/srv_netlog_nt.c:603(_netr_ServerAuthenticate3)
  _netr_ServerAuthenticate3: netlogon_creds_server_check failed. Rejecting auth request from client MADE-1 machine account MADE-1$
[2010/08/26 11:08:59,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:08:59,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:09:50,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/26 11:09:50,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/08/26 11:09:52,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:09:52,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:09:55,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:09:55,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:10:16,  0] auth/pampass.c:586(smb_pam_account)
  smb_pam_account: PAM: UNKNOWN PAM ERROR (12) during Account Management for User: USER_X
[2010/08/26 11:10:16,  0] auth/pampass.c:794(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User USER_X!
[2010/08/26 11:10:38,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/26 11:10:38,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer
```.

Hi , were you able to take care of this issue. I am currently facing same issue. smb/ldap user tries to ssh into this box and they see the password changing messages as you mentioned in your post. Please let me know.

Thank you.

EDIT :

Okay, as you said in your post about using smbldap-passwd, I don't know what exactly that you did. 

However, I had to login as root on smb-ldap server and run smbldap-passwd 'username' to set a  password for that user and had that user login again. Now it is fine. However, I am thinking there must be something in configuration that is forcing the smb/ldap user to change password after some period of time.

---

### Post by akha666 on 2010-10-28
[SIZE=4]Hello [spliner]("http://ubuntuforums.org/member.php?u=398361")
I have followed ur tutorial and I got it working with Ubuntu Server 10.04.1 LTS with Roaming Profile enabled without any problem
know I asked for help to make Samba BDC
should I have to make all steps I did with PDC (OpenLDAP Server + Client  , and Samba PDC) ? and only change in smb.conf 
domain master = no
passdb backend = ldapsam:ldap://IP_of_the_PDC 
can you help for to build Samba BDC
thx for advance [/SIZE]

> **spliner said:**
> No luck.. I saved the 'Tips and Tricks' on a whim, but did not save the whole tutorial.  I had intended to compare it to Rikcy's original guide and create a hybrid tutorial for myself but it dissapeared in this thread too quickly.

Spliner

Scratch that.. below is a copy of the original guide that I managed to dig up using different web caches.  Keep in mind, the author seems to think it is broken and has removed it, however a rewrite does not seem to be forthcoming at the moment.  Use at your own risk (as I and the author likely can't help with issues), and had it not been originally submitted here as a guide I would not be re-posting it.  It did work for me, but has some glitches here and there, and does not cover everything.  IF I have time later I may use it and the original 7.04/8.04 guide by Ricky and see if a hybrid can be made, but I generally have no time for this stuff these days so no promises.

Here you go:

Please note this guide is outdated and is being re-written by the author.  Use at your own risk:


```
Hi all,

Hi everyone, after digging over the net and after spending a lot of time trying to understand how things work, I'm proud to present a very quick and super easy tutorial to create a Samba Primary Domain Controller with LDAP integration inside Ubuntu 10.04, both 32bit and 64bit.

In less than 30 minutes you'll have:
- A fully working PDC for Windows Clients
- Roaming profiles NOT enabled (this is what most of you want)
- Be able to have shared folders automatically mounted when a user logs into the domain
- Tested and fully working with(all flavours): Windows XP, Windows Vista and even Windows 7!

If you do everything exactly like I wrote I guarantee it will work. One single error can compromise everything and you'll have to restart from the beginning! You have been warned!

General Information before reading:
- In this guide each step will have a number, so if you ever have to ask me a question be sure you point the exact number, I will ignore any posts without the number being explicited.
- Commands you must type start with a "->".
- The guide presumes you know how to use Nano text editor (or any other text editor from shell like Vim).
- In this guide my default password is always "pwd123".

Let's Start.

1)
Install Ubuntu Server 10.04 32Bit or 64Bit
Once Ubuntu 10.04 is up, log with root user:
-> sudo su
From now on I assume you are always root user.

2)
Set a static IP,
in this example the NIC card is eth0 and the network is part of 192.168.1.x class.
-> nano /etc/network/interfaces

Quote:
auto lo eth0
iface lo inet loopback
iface eth0 inet static
address 192.168.1.10
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.1 

3)
-> /etc/init.d/networking restart
-> ifconfig
The output should show you the static IP, try pinging a local IP or an internet IP to be sure you are on the net, ex:
-> ping [www.google.it]("http://www.google.it")
or try pinging your gateway set before:
-> ping 192.168.1.1
If you are unsure, reboot your machine to see if "ifconfig" command still shows you the same IP and to be sure you're still part of the network by pinging as said before.
ONCE YOU FINISHED WITH THIS GUIDE, IF YOU EVER CHANGE YOUR IP BE SURE TO READ SECTION: "TIPS AND TRICKS", FOUND AT THE END OF THIS GUIDE OR YOUR PDC WILL STOP WORKING.

4)
-> apt-get update
-> apt-get dist-upgrade
-> reboot
-> sudo su

5)
-> apt-get install slapd ldap-utils
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
-> ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

6)
-> > backend.example.com.ldif
Your next step will be to modify this file, the only thing you should care of changing is the password, which is set at line "olcRootPW:". By default password is "pwd123".
-> nano backend.example.com.ldif

Quote:
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb 
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=pdc
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=pdc
olcRootPW: pwd123
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=pdc" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=pdc" write by * read
 


7)
From now on, if ldap commands similar to this ask for a password, put password set above in step 6, by default in this guide as said "pwd123".
-> ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif

8)
-> apt-get install samba samba-doc libpam-smbpass smbclient smbldap-tools

9)
Now I'll make you download my samba configuration file.
-> wget [http://digilander.libero.it/bulletxt...10.04/smb.conf](http://digilander.libero.it/bulletxt...10.04/smb.conf)
After downloading it, you'll have to change ONLY two values: "workgroup = " and "netbios = ".
Workgroup is the name of the Domain. This is the name that you'll have to enter in a Windows client to make it join the domain. Netbios is instead the name used to browse shared folders, for example in Windows you'll put "\\$netbiosname\$shared_folder".
DO NOT PUT WORKGROUP NAME IDENTICAL TO NETBIOS NAME.
IMPORTANT: carefully decide the NETBIOS name, once you change it YOU CAN'T CHANGE IT AGAIN OTHERWISE IT WILL BREAK EVERYTHING! YOU'VE BEEN WARNED.
Type the following and change the two values.
-> nano smb.conf
Once you changed the two values type:
-> cp -rf smb.conf /etc/samba/smb.conf

10)
In the next command it will prompt you to put a password, this must be the same as set before in step 6, by default in this guide "pwd123"
-> smbpasswd -W

11)
-> service smbd restart

12)
Now you must check that samba is running, it will ask you for a password, just hit Enter.
-> smbclient -L localhost
It should not give you any errors, instead it must show some stuff and you should see your Workgroup Name set in step 9

13)
-> mkdir -v /var/lib/samba/profiles
-> chmod 777 /var/lib/samba/profiles
-> mkdir -v -p /var/lib/samba/netlogon
-> chmod 777 /var/lib/samba/netlogon
-> cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap-> /schema/
-> gzip -d /etc/ldap/schema/samba.schema.gz

14)
-> > schema_convert.conf
-> nano schema_convert.conf

Quote:
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema 

15)
-> mkdir /tmp/ldif_output
-> slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/cn=samba.ldif

16)
Now you'll have to edit a file, open the file with the following command and read below to understand what must be edited.
-> nano /tmp/cn\=samba.ldif
At the very top you'll see:

Quote:
dn: cn{12}=samba,cn=schema,cn=config 

Change it to:

Quote:
dn: cn=samba,cn=schema,cn=config 

Always at the top you'll see:

Quote:
cn: {12}samba 

Change it to:

Quote:
cn: samba 

At the end of the file you'll see:

Quote:
structuralObjectClass: olcSchemaConfig
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95
creatorsName: cn=config
createTimestamp: 20080827045234Z
entryCSN: 20080827045234.341425Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20080827045234Z 

Delete all those lines, save and close.

17)
Be sure the following command does not give errors:
-> ldapadd -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif

18)
-> > samba_indexes.ldif
-> nano samba_indexes.ldif

Quote:
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub 

19)
Be sure the following does not give any errors.
-> ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif

20)
Now thanks to the following command, you'll finally understand if everything till now went fine. If everything goes fine, it will output a lot of stuff, including at the end strings similar to the ones found in step 18
-> ldapsearch -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -b cn=config -W olcDatabase={1}hdb

21)
Now that ldap is working perfectly, we must also be sure Samba is working too.
The following command MUST not give errors, and it must output something similar to this:

Quote:
SID for domain DOMAIN is: S-1-5-21-908678672-1104131578-2020688504 

So this is the command to type:
-> net getlocalsid

22)
-> gzip -d /usr/share/doc/smbldap-tools/configure.pl.gz

23)
Next command is crucial to make Samba and Ldap work together. When prompted,
press always Enter without inserting anything. There are only two cases where you must type something.
When it asks for "Logon Home" and "Logon Path", put a "." character.
At a certain point, it will ask you for a password two times, once for ldap bind master and then for ldap bind slave. In both cases, you must put the exact same password you put in step 6, by default in this guide "pwd123".
So now you know what to do, this is the command:
-> perl /usr/share/doc/smbldap-tools/configure.pl

24)
Following command should create some groups, at the end it will ask for a password. As always put password provided in step 6, default of this guide is "pwd123".
-> smbldap-populate

25)
-> /etc/init.d/slapd stop
-> slapindex 
-> chown openldap:openldap /var/lib/ldap/*
-> /etc/init.d/slapd start

26)
If everything till now is really working, the next command will make user "root" be a Domain Administrator.
In section "Tips and Tricks" you'll see how to make other users be a Domain admin.
THIS COMMAND MUST NOT GIVE ERRORS, otherwise it means LDAP is not working with Samba.
-> smbldap-groupmod -m 'root' 'Administrators'

27)
In the next command, it will ask you for some stuff. Do not make errors here!
When it asks for questions that want a Yes/No reply, just press Enter leaving default.
When it asks for LDAP server Uniform Resource Identifier, leave it as it is "ldapi:///"
When it asks for Distinguished name of the search base, put "dc=pdc"
When it asks for LDAP account for root, put "cn=admin, dc=pdc"
When it asks for LDAP password, put the same set in step 6, default of this guide was "pwd123"

The command is:
-> apt-get --yes install ldap-auth-client

IMPORTANT: if you do a mistake, you can reconfigure the previous command typing:
-> dpkg-reconfigure ldap-auth-config

28)
-> auth-client-config -t nss -p lac_ldap

29)
The following command is used to enable Unix, Ldap and Samba authentication.
Be sure all of them are selected with "*" character and press Enter.
The command is:
-> pam-auth-update ldap

30)
The following command should output something similar to this:

Quote:
Domain Admins:*:512:root
Domain Users:*:513:
Domain Guests:*:514:
Domain Computers:*:515:
Administrators:*:544:root
Account Operators:*:548:
Print Operators:*:550:
Backup Operators:*:551:
Replicators:*:552: 

The command is:
-> getent group

31)
-> reboot

32)
Good, we're done. After reboot, let's check that everything is working by creating a user.
-> sudo su
If the following command does not give errors, it means Samba and Ldap are both working together, and you should be happy! It will ask for a password, the password is the password you want for the user, in this case for user "user1":
-> smbldap-useradd -a -m -P user1

33) 
If you reached this step without errors, it means you are ready to make your Windows Clients join the domain.
However for security reasons it's not a good idea to make your customer know the password of "root" account. At the moment, to make a Windows Client join the domain you'll have to put user "root" and its password, let's instead make another user which will be part of the Domain Administrators. We'll call the user "adminpdc".
-> smbldap-useradd -a -m -P adminpdc
-> smbldap-groupmod -m ' adminpdc' 'Administrators'
-> smbldap-groupmod -m ' adminpdc' 'Domain Admins'
-> sudo auth-client-config -t nss -p lac_ldap

Good, now we have user "adminpdc" that is a Domain Administrator but is in no way a possible security danger for your Linux machine, since it's not part of sudoers. In this way you'll never have to use account "root" to make a Windows client join the domain or to make changes to the Windows client OS.

Finally, make your Windows Client (xp,vista,7) join the domain! :
- In Windows XP, right click on Computer->Properties and click on Change as seen here: [http://www.iaji.net/wp-content/uploa...uter_name3.png](http://www.iaji.net/wp-content/uploa...uter_name3.png)
- For Windows Vista and 7 instead, right click on Computer, on the left click on Advanced Settings and then click on "Change" under "Computer Name" Tab.

IMPORTANT ABOUT WINDOWS 7:
To make Windows 7 be part of the domain, read below section Tips and Tricks.

- As domain, put the workgroup name you set in step 9
- When it asks for username and password, put "adminpdc" and the password of this user, you set this on step 33. If everything goes well it will say you joined the domain and you must reboot.

That's all!

TIPS AND TRICKS:

Create/Delete/Manage Users:
To Add: smbldap-useradd -a -m -P user
To Delete: smbldap-userdel user
To ChangePassword: smbldap-passwd user

To add a Domain Administrator:
-> smbldap-groupmod -m 'user' 'Administrators'
-> smbldap-groupmod -m 'user' 'Domain Admins'
-> auth-client-config -t nss -p lac_ldap

If you ever change the static IP of the PDC:
-> service smbd stop
-> rm /var/cache/samba/browse.dat 
-> rm /var/cache/samba/login_cache.tdb
-> rm /var/lib/samba/wins.dat
-> reboot

To make Windows 7 join the domain:
- Download this file and click on it: [https://bugzilla.samba.org/attachmen...88&action=view](https://bugzilla.samba.org/attachmen...88&action=view)
- Reboot Windows 7
- Make Windows 7 join the domain. It will say it joined the domain but then it will give you a DNS error. Ignore it and reboot again Windows 7
- You should now be part of the domain

To make your PDC automatically map net drives:
-> apt-get install flip
-> > /var/lib/samba/netlogon/allusers.bat
In this example you'll have a shared folder for all users, of course you can edit /etc/samba/smb.conf to create specific user shares.
-> mkdir -p /var/lib/samba/shared/
-> chmod -R 777 /var/lib/samba/shared/
-> nano /var/lib/samba/netlogon/allusers.bat
NOTE: change "PSAMBA" with the Netbios name set in step 9. Change drive "m:" to any letter you prefer.

Quote:
@echo off
net use m: /delete
net use m: "\\PSAMBA\shared" 

-> flip -m /var/lib/samba/netlogon/allusers.bat

```

---

### Post by spliner on 2010-11-02
Sorry, I have never set up a BDC.  Its been on my list 'to do' but never have gotten around to it.  Instead I back the system up nightly with a bash script.  

Also.. don't forget.. this isn't my tutorial, I just found a copy of it and re-posted it.  Props go to the original author bulletxt although I fear he may have abandoned the re-write of this guide.  I am just about at the point where I am going to switch to a Microsoft PDC because these guides are too scarce and get out dated quickly.  The original authors mean well but nobody can be expected to take the time to do a complete re-write every time something minor changes; which is what happens frequenly with Linux.

---

### Post by akha666 on 2010-11-04
> **spliner said:**
> Sorry, I have never set up a BDC.  Its been on my list 'to do' but never have gotten around to it.  Instead I back the system up nightly with a bash script.  

Also.. don't forget.. this isn't my tutorial, I just found a copy of it and re-posted it.  Props go to the original author bulletxt although I fear he may have abandoned the re-write of this guide.  I am just about at the point where I am going to switch to a Microsoft PDC because these guides are too scarce and get out dated quickly.  The original authors mean well but nobody can be expected to take the time to do a complete re-write every time something minor changes; which is what happens frequenly with Linux.

[FONT=Comic Sans MS][SIZE=4][COLOR=Blue]Thanks for the clarification
Did you try to do apply this tutorial on U-server 10.10 ???
I did it with no error and I can join XP Maxhine but after restart and chose my domina from list to logon , it give me error <the domain is not available> 
I can ping to server but I can't login it[/COLOR][/SIZE][/FONT]

---

### Post by AKnightintheDesert on 2010-11-11
I used this tutorial to create a couple of PDC's that I am using for various things including controlling my small business network.  They work great the only trouble I have is every 45 days they prompt for a password change that doesn't work.  Te only workaround that I have found is changing the shadow min / max setting to extremely high / low number so the user never has to reset their password.  Has anyone found a more useful fix to this problem??

Update> If it helps at all if you change the password from windows and then run smbldap-userlist the samba password change date gets set to current but the shadow password change date doesn't change. This seems to mean that when windows initiates a password change it doesn't use smbldap-tools it just changes samba. The original post said to put the Unix password sync to no in the smb.conf file, it would seem that turning this to yes would solve the problem but does anyone know why I should not so this or why it was turned off in the first place??

---

### Post by upengan78 on 2010-11-16
> **AKnightintheDesert said:**
> I used this tutorial to create a couple of PDC's that I am using for various things including controlling my small business network.  They work great the only trouble I have is every 45 days they prompt for a password change that doesn't work.  Te only workaround that I have found is changing the shadow min / max setting to extremely high / low number so the user never has to reset their password.  Has anyone found a more useful fix to this problem??

Update> If it helps at all if you change the password from windows and then run smbldap-userlist the samba password change date gets set to current but the shadow password change date doesn't change. This seems to mean that when windows initiates a password change it doesn't use smbldap-tools it just changes samba. The original post said to put the Unix password sync to no in the smb.conf file, it would seem that turning this to yes would solve the problem but does anyone know why I should not so this or why it was turned off in the first place??

Hi, sorry for late reply,

In /etc/smbldap-tools/smbldap.conf note below config,

```
# Default password validation time (time in days) Comment the next line if
# you don't want password to be enable for defaultMaxPasswordAge days (be
# careful to the sambaPwdMustChange attribute's value)
defaultMaxPasswordAge="45"
```

May be you can comment that line and push that config to ldap using "smbldap-populate"

Also, may be you want add in smb.conf and smb-ldap.conf(with its syntax)
```
passwd program = /usr/sbin/smbldap-passwd -s %u
```

One more thing if you can do for me, could you paste o/p of below command ?
```
net sam policy show "maximum password age"
```

Cheers

---

### Post by MyTer on 2010-11-22
> **akha666 said:**
> [SIZE=4]Hello [spliner]("http://ubuntuforums.org/member.php?u=398361")
I have followed ur tutorial and I got it working with Ubuntu Server 10.04.1 LTS with Roaming Profile enabled without any problem
know I asked for help to make Samba BDC
should I have to make all steps I did with PDC (OpenLDAP Server + Client  , and Samba PDC) ? and only change in smb.conf 
domain master = no
passdb backend = ldapsam:ldap://IP_of_the_PDC 
can you help for to build Samba BDC
thx for advance [/SIZE]

Hi
I found this:
[http://www.server-world.info/en/note?os=Ubuntu_10.04&p=samba&f=6]("http://www.server-world.info/en/note?os=Ubuntu_10.04&p=samba&f=6")

Seems pretty straight forward for the BDC

[SIZE="5"]Thanks a lot Spliner for this guide, finally one that works for me (Ubuntu server 10.10)[/SIZE]

I've been working on LDAP for about 5 weeks now. 
I've worked a lot on Netware NDS before, seems easy now in comparison to openLDAP!
I can access from Windows 7, Just have to check out from Ubuntu client 10.10 as well. Will continue tomorrow

---

### Post by spliner on 2010-11-29
Just keep in mind that 10.04 is a LTS release which means it is supported for much longer than the 10.10 release.  I made that mistake with my first production PDC using 8.10 instead of 8.04 LTS and the support dropped on it (no more updates) before I was ready to do a new version/upgrade.  I was then forced to do an upgrade to the latest release which was a nightmare on a production machine.

For instance (feel free to correct me if I'm wrong) 8.04 LTS support (updates) are good until April of 2011.  Ubuntu 8.10 support ended April of 2010.  Its always best to use an LTS release for a server such as this for that reason, unless you're willing to re-create the thing with the newer version in a year's time if the upgrade fails or trashes your PDC.

I now have a Win2k8 PDC in the works, so I'll be switching from Linux for my PDC/BDC.  Free is always better, but I've run into far too many issues that I personally could not easily solve with a Linux PDC.  Relying on some kind soul to write a guide for us newbs (Been using Linux as a PDC for 4 years now and I still consider myself a newb) is not so fun some days.  I still use Ubuntu 10.04 LTS on my home network as my PDC, which was set up using bulletxt's guide.

Spliner

---

### Post by jackfusion on 2010-11-29
on step 9 there the link for the smb.conf does not work please reupload.

---

### Post by AKnightintheDesert on 2010-12-02
> **upengan78 said:**
> Hi, sorry for late reply,

In /etc/smbldap-tools/smbldap.conf note below config,

```
# Default password validation time (time in days) Comment the next line if
# you don't want password to be enable for defaultMaxPasswordAge days (be
# careful to the sambaPwdMustChange attribute's value)
defaultMaxPasswordAge="45"
```

May be you can comment that line and push that config to ldap using "smbldap-populate"

Also, may be you want add in smb.conf and smb-ldap.conf(with its syntax)
```
passwd program = /usr/sbin/smbldap-passwd -s %u
```

One more thing if you can do for me, could you paste o/p of below command ?
```
net sam policy show "maximum password age"
```

Cheers

Thanks for the prompt reply, After some extensive research and testing I still am no closer to a solution. I added the following to the smb.conf file:

```
passwd program = /usr/sbin/smbldap-passwd %u
passwd chat = *password:*%n\n*password:*%n\n*changed*
```

I have tried this with the "unix password sync" variable set to both yes and no.  When it is set to "yes" it gives me an "access denied" error when I try to change the password from windows.  When I set it to "no" it changes the Samba password but doesn't change the unix password.  I really want this to change both the samba and unix/linux password.  Otherwise auto-expiring passwords do not work.  Anyone have some suggestions??

Also as requested the output of ```
 net sam policy show "maximum password age"
```
```
Account policy 'maximum password age' description: Maximum password age, in seconds (default: -1 => never expire passwords)
Account Policy "maximum password age" value is: -1
```

---

### Post by AKnightintheDesert on 2010-12-08
I think I made some progress.  It appears that this is actually  problem with PAM.  Here is the code puke from the samba log when I try to change a password:
```

[2010/12/07 23:35:51,  4] auth/pampass.c:670(smb_pam_chauthtok)
  smb_pam_chauthtok: PAM: Password Change for User: XXXXX
[2010/12/07 23:35:51,  2] auth/pampass.c:682(smb_pam_chauthtok)
  PAM: unable to obtain the old authentication token - was the old password wrong?.
[2010/12/07 23:35:51,  2] auth/pampass.c:77(smb_pam_error_handler)
  smb_pam_error_handler: PAM: Password Change Failed : Authentication information cannot be recovered
[2010/12/07 23:35:51,  0] auth/pampass.c:861(smb_pam_passchange)
  smb_pam_passchange: PAM: Password Change Failed for userXXXXX!

```

anyone have any ideas??

---

### Post by AKnightintheDesert on 2010-12-08
OK I finally got it working. After about 16+ hours of testing and researching online I finally got a smb.conf that worked, and have come to the conclusion that PAM Fails at this task. Here is the modified SMB.conf:

```

[global]
        #log level = 10
        # Domain name ..
        workgroup = **YOURDOMAIN.LOCAL**
        # Server name - as seen by Windows PCs ..
        netbios name = **YOUR SEVER NAME WITHOUT THE DOMAIN**
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        # obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        # pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = yes
        ldap passwd sync = yes
        passwd program = /usr/sbin/smbldap-passwd -u %u
        passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"
        passwd chat timeout = 4

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = **dc=YOURDOMAIN,dc=LOCAL**
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,**dc=YOURDOMAIN,dc=LOCAL**

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
        logon drive =
        logon home =
        logon path =
        logon script = allusers.bat


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No
        logon script = allusers.bat

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /Storage/Profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = No
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root

[shared]
        writeable = yes
        path = /Storage/SharedDrive
        public = yes
        browseable = yes

```

What I modified:
I commented out this so it would stop trying to use PAM, because it fails :D
```
        # obey pam restrictions = Yes
        # pam password change = Yes
```
and I added this to force it to use smbldap as the password change engine for the Linux users:
```
passwd program = /usr/sbin/smbldap-passwd -u %u
        passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"
        passwd chat timeout = 4
```
The chat timeout is because I am running my PDC on a 6+ year old HP AMD laptop, just for testing. 
you also need to change
```
        unix password sync = yes
```
otherwise it will ignore the other code.  

When a password change is initiated from the two Winblows 7 64bit systems that I have it succeeds on the windows box and changes both the samba and shadow values when viewed from: ```
smbldap-userlist -a
```
I hope this helps and thanks for the help from the other members.

---

### Post by bulletxt on 2010-12-08
> **AKnightintheDesert said:**
> OK I finally got it working. After about 16+ hours of testing and researching online I finally got a smb.conf that worked, and have come to the conclusion that PAM Fails at this task. Here is the modified SMB.conf:

```

[global]
        #log level = 10
        # Domain name ..
        workgroup = **YOURDOMAIN.LOCAL**
        # Server name - as seen by Windows PCs ..
        netbios name = **YOUR SEVER NAME WITHOUT THE DOMAIN**
        # Be a PDC ..
        domain logons = Yes
        domain master = Yes
        # Be a WINS server ..
        wins support = true

        # obey pam restrictions = Yes
        dns proxy = No
        os level = 35
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        # pam password change = Yes

        # Allows users on WinXP PCs to change their password when they press Ctrl-Alt-Del
        unix password sync = yes
        ldap passwd sync = yes
        passwd program = /usr/sbin/smbldap-passwd -u %u
        passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"
        passwd chat timeout = 4

        # Printing from PCs will go via CUPS ..
        load printers = yes
        printing = cups
        printcap name = cups

        # Use LDAP for Samba user accounts and groups ..
        passdb backend = ldapsam:ldap://localhost

        # This must match init.ldif ..
        ldap suffix = **dc=YOURDOMAIN,dc=LOCAL**
        # The password for cn=admin MUST be stored in /etc/samba/secrets.tdb
        # This is done by running 'sudo smbpasswd -w'.
        ldap admin dn = cn=admin,**dc=YOURDOMAIN,dc=LOCAL**

        # 4 OUs that Samba uses when creating user accounts, computer accounts, etc.
        # (Because we are using smbldap-tools, call them 'Users', 'Computers', etc.)
        ldap machine suffix = ou=Computers
        ldap user suffix = ou=Users
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        # Samba and LDAP server are on the same server in this example.
        ldap ssl = no

        # Scripts for Samba to use if it creates users, groups, etc.
        add user script = /usr/sbin/smbldap-useradd -m '%u'
        delete user script = /usr/sbin/smbldap-userdel %u
        add group script = /usr/sbin/smbldap-groupadd -p '%g'
        delete group script = /usr/sbin/smbldap-groupdel '%g'
        add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
        delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
        set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'

        # Script that Samba users when a PC joins the domain ..
        # (when changing 'Computer Properties' on the PC)
        add machine script = /usr/sbin/smbldap-useradd -w '%u'

        # Values used when a new user is created ..
        # (Note: '%L' does not work properly with smbldap-tools 0.9.4-1)
        logon drive =
        logon home =
        logon path =
        logon script = allusers.bat


        # This is required for Windows XP client ..
        server signing = auto
        server schannel = Auto

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        admin users = root
        guest ok = Yes
        browseable = No
        logon script = allusers.bat

[Profiles]
        comment = Roaming Profile Share
        # would probably change this to elsewhere in a production system ..
        path = /Storage/Profiles
        read only = No
        profile acls = Yes
        browsable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        use client driver = Yes
        create mask = 0600
        guest ok = No
        printable = Yes
        browseable = No
        public = yes
        writable = yes
        admin users = root
        write list = root

[print$]
        comment = Printer Drivers Share
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        admin users = root

[shared]
        writeable = yes
        path = /Storage/SharedDrive
        public = yes
        browseable = yes

```

What I modified:
I commented out this so it would stop trying to use PAM, because it fails :D
```
        # obey pam restrictions = Yes
        # pam password change = Yes
```
and I added this to force it to use smbldap as the password change engine for the Linux users:
```
passwd program = /usr/sbin/smbldap-passwd -u %u
        passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"
        passwd chat timeout = 4
```
The chat timeout is because I am running my PDC on a 6+ year old HP AMD laptop, just for testing. 
you also need to change
```
        unix password sync = yes
```
otherwise it will ignore the other code.  

When a password change is initiated from the two Winblows 7 64bit systems that I have it succeeds on the windows box and changes both the samba and shadow values when viewed from: ```
smbldap-userlist -a
```
I hope this helps and thanks for the help from the other members.

Is that the solution to make pwd change while running a windows client with a user logged in and also change pwd when it expires?

---

### Post by AKnightintheDesert on 2010-12-08
> **bulletxt said:**
> Is that the solution to make pwd change while running a windows client with a user logged in and also change pwd when it expires?

Ill have to wait until my password expires to know for sure.  However the issue with the password expiring and not being able to change it was because Samba was not changing the unix/linux password when it changed the Samba LDAP password.  As I said this now reflects a password change on all of the variables listed with the smbldap-userlist -a tool. I assume that this will also fix the password timeout issue.  I am setting up a user with a 24 hour password expire to check to make sure.

---

### Post by onlyu on 2010-12-11
Hi All,

Thanks for author of thread. I follow and work like a charm. But I resetup many many times and always see this issues. Is is the bug???
I can joint domain, change user pass,... but in /var/log/samba/log.smbd show bellow

```

[2010/02/18 12:29:19,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2010/02/18 12:29:19,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2010/02/18 12:29:44,  0] lib/smbldap.c:1052(smbldap_connect_system)
  failed to bind to server [ldap://192.168.100.1]("ldap://192.168.1.8:389") 
with dn="cn=admin,dc=mydomain,dc=com" Error: Can't contact LDAP server
        (unknown)

```

Anyone success setup PDC on Ubuntu 10.04 could double check?

Regards,
OnlyU

---

### Post by bulletxt on 2010-12-17
> **AKnightintheDesert said:**
> Ill have to wait until my password expires to know for sure.  However the issue with the password expiring and not being able to change it was because Samba was not changing the unix/linux password when it changed the Samba LDAP password.  As I said this now reflects a password change on all of the variables listed with the smbldap-userlist -a tool. I assume that this will also fix the password timeout issue.  I am setting up a user with a 24 hour password expire to check to make sure.


Any news about this? Please share :)

---

### Post by kerfurdt on 2010-12-20
I found a few things about passwords.  I really don't want my passwords to expire at all and after some searching I found that the object 'sambaDomain' has a property 'sambaMaxPwdAge' that if set to -1 stops passwords from exipring.  Also on a per-user basis if you add '-A 0 -B 0' to the smbldap-adduser command it creates a user with an 'X' flag for whom the password does not expire regardless of the sambaDomain configuration.

---

### Post by demanlov on 2011-01-26
I'm confused.  I see messages about the tutorial being re-written and comments about people using this tutorial, but I don't see any tutorial.  Maybe I am dense, but I don't see any tutorial to download.  Where can I download this tutorial.

Thanks!!!

---

### Post by BinaryMn on 2011-02-08
Can someone post the original guide?

It's rather irritating, bordering on rude, creating a thread detailing a howto only to find on the first page that the guide has been taken down when a note could have been put in the guide.

---

### Post by jarek.k on 2011-02-10
Hi,

I would also like to see original tutorial.
Thanks

---

### Post by pcmb8866 on 2011-02-20
> **bulletxt said:**
> Any news about this? Please share :)
 
@**AKnightintheDesert, @bulletxt**
 
Works great, finally!
The only thing I had to change was in ldap.
sambaDomainName=YOURDOMAIN.LOCAL  --> sambaMaxPwdAge to 3888000  (45 days in sec (60*60*24*nDays))
 
The only option that isn't updated in ldap users is: sambaPwdMustChange, but you can workaround this by modifying smbldap-passwd. Copy this file to smbldap-pwd and change the code below
```

# Update 'userPassword' field
if ( $update_unix_passwd ) {
my $shadowLastChange=int(time()/86400);
my $modify;
if (($< != 0) || (!defined $config{defaultMaxPasswordAge})) {
$modify = $ldap_master->modify ( "$dn",
changes => [
replace => [userPassword => "$hash_password"],
replace => [shadowLastChange => "$shadowLastChange"]
]
);
} else {
$modify = $ldap_master->modify ( "$dn",
changes => [
replace => [userPassword => "$hash_password"],
replace => [shadowLastChange => "$shadowLastChange"],
replace => [shadowMax => "$config{defaultMaxPasswordAge}"]
]
);
}
$modify->code && warn "Failed to modify UNIX password: ", $modify->error ;
}
```
to
```

# Update 'userPassword' field
if ( $update_unix_passwd ) {
my $shadowLastChange=int(time()/86400);
my $modify;
if (($< != 0) || (!defined $config{defaultMaxPasswordAge})) {
$modify = $ldap_master->modify ( "$dn",
changes => [
replace => [userPassword => "$hash_password"],
replace => [shadowLastChange => "$shadowLastChange"]
]
);
} else {
***[COLOR=red]my $date=time;[/COLOR]***
***[COLOR=red]my $sambaPwdMustChange=$date+$config{defaultMaxPasswordAge}*24*60*60;[/COLOR]***
$modify = $ldap_master->modify ( "$dn",
changes => [
replace => [userPassword => "$hash_password"],
replace => [shadowLastChange => "$shadowLastChange"],
***[COLOR=red]replace => [sambaPwdMustChange => "$sambaPwdMustChange"],[/COLOR]***
replace => [shadowMax => "$config{defaultMaxPasswordAge}"]
]
);
}
$modify->code && warn "Failed to modify UNIX password: ", $modify->error ;
}
```
In smb.conf change password program to smbldap-pwd -u %u
 
That's it and all works great.
Thank you AKnightintheDesert for the direction to search.

---

### Post by pcmb8866 on 2011-02-20
> **jarek.k said:**
> Hi,
 
I would also like to see original tutorial.
Thanks
 
You can see the original post on page 13 post #129

---

### Post by jarek.k on 2011-02-22
> **pcmb8866 said:**
> You can see the original post on page 13 post #129

thanks for that

---

### Post by rmax75 on 2011-03-20
> **pcmb8866 said:**
> The only thing I had to change was in ldap.
sambaDomainName=YOURDOMAIN.LOCAL  --> sambaMaxPwdAge to 3888000  (45 days in sec (60*60*24*nDays))


Great job! :D

You can set the "maximum password age" policy easily with the command:
**pdbedit -P "maximum password age" -C 2592000**

Where **2592000 **(30 days) represents the period of validity of the password expressed in seconds (60*60*24*nDays).


Thanks a lot to all the authors,
Massimo (rmax75)

---

### Post by sja2998 on 2011-04-15
I have done this tutorial twice without any problems.  Barring a few typos, it worked perfectly.

I had a hard drive fail this week and did a fresh 10.04 install without any issues.  I get through step 11 without any problems, but now when I type 

smbclient -L localhost

*I get *
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

I rebooted and when I log in as administrator, root, or any other username, I create, I get 

Failed to add entry for user administrator  (or any username)

I have since retired the tutorial 4 more times with fresh installs being very careful, and I get identical results. 

I don't know where to start to troubleshoot this.  Could any packages have changed to cause these errors?

Since I did this tutorial about a month ago without problem I can't really figure out what has changed.

Any help would be greatly appreciated.

---

### Post by onurbiccud on 2011-04-28
> **ricpelo said:**
> Hi, bulletxt! Excellent post. All works flawless, like a charm :).

Only one question: Is there a way to have roaming profiles enabled with this config? I have a classroom of 30 client PCs and I would like to have that option available, so the students can sit on any PC and get all their docs and configuration available.

Thanks very much in advance.
4 thinks thah work for me

1) domain mame not longer than 15 char
2) S09slapd on /etc/rc2.d
3)chmod 1777 /var/lib/samba/profiles
4)
        logon drive = H:
        logon home = \\%L\%U\.profiles
        logon path = \\%L\Profiles\%U

---

### Post by gade.chaitanya@gmail.com on 2011-05-03
Hi [spliner]("http://ubuntuforums.org/member.php?u=398361") and to other members who are contributing here..

I am following this step by step how to and up to step no 6 it worked perfectly, but after executing the command in step no 7 I got some errors..
I am quoting them 
"SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: <olcModuleLoad> handler exited with 1"

I dig a lot in the google but I am unable to find a solution, can anyone help me with proper solution for it?

---

### Post by eliseojason on 2011-05-06
Hi to all!

Great job.

I followed this guide until step 12 but I was getting a "NT_STATUS_LOGON_FAILURE" when running the command "smbclient -L localhost".

Thanks so much for your help.

---

### Post by sisyphe21 on 2011-06-17
> **eliseojason said:**
> Hi to all!

Great job.

I followed this guide until step 12 but I was getting a "NT_STATUS_LOGON_FAILURE" when running the command "smbclient -L localhost".

Thanks so much for your help.


well, even if most people are clever than i am, i encountered this problem and solved it, just by.... reading the tuto wich says : "it wil ask you for a password, just hit Enter" ... without typing any password, of course!
If it may help some lightheaded like me...
and thanks for this tuto!!!

---

### Post by theller on 2011-06-22
I want to set up a domain controller for a High School and I see you have not updated the tutorial. Could I use the old version? Could you post the old one until the new version is ready.

---

### Post by engragy on 2011-07-03
this is very cool , very good info .
thanks

---

### Post by razor7 on 2011-07-05
Hi, do you plan to post the tut again?

Thanks a lot!

---

### Post by hanslammerts on 2011-07-14
Hi,
 
Followed the tutorial to the letter, and all went fine until step 17.
When doing thye smbldap-populate command, I get the following error :
 
Populating LDAP directory for domain schacht.beuningen (S-1-5-21-292848559-2307444814-738947609)
(using builtin directory structure)
erreur LDAP: Can't contact master ldap server for writing (IO::Socket::INET: Bad hostname '') at /usr/share/perl5/smbldap_tools.pm line 322.
 
I do not understand why it gives me a bad hostname.
 
Anyone knows where to look for possible errors ?
Did not find any (good) hits for this problem on Google.
 
Thanks,
 
Hans

---

### Post by ByteJuggler on 2011-11-11
Hmm, given that the original post has been removed and the replacement is not forthcoming, please note that the original post can be retrieved from the internet archive, [here]("http://web.archive.org/web/20100719194925/http://ubuntuforums.org/showthread.php?t=1499753").

---

### Post by buntmebaby on 2012-02-08
Um, forgive me for being thick but...WHERE is the tutorial exactly?
Is there a subtle link somewhere here.....

---

### Post by xtdv on 2012-05-30
> **akha666 said:**
> [FONT=Comic Sans MS][SIZE=4][COLOR=Blue]Thanks for the clarification
Did you try to do apply this tutorial on U-server 10.10 ???
I did it with no error and I can join XP Maxhine but after restart and chose my domina from list to logon , it give me error <the domain is not available> 
I can ping to server but I can't login it[/COLOR][/SIZE][/FONT]

I have the same problem...
Does anyone find the solutions?

---

