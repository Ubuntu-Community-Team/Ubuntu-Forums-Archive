---
title: "Setting up file sharing to/from XP PRO SP3"
date: 2011-02-07
forum: System76 Support
---

### Post by eightbits89 on 2011-02-07
I am a new merrkat 10.10 64 bit Net Box version user. I have been trying for about a week now to get file sharing to work with a XP PRO laptop.
Samba is installed and printer sharing is working, printers on XP PRO PC.

From windows I can 'see' the UBUNTU machine. However , I can not access and I get
messages that indicate I don't have the correct permissions.

I can not seem to get past that issue. I am hoping that there is a step by step instruction that can assist me in getting this set up. 

It just this should be relative straight forward to set up.

thanks in advance for any input.

Cheers

---

### Post by isantop on 2011-02-08
Right click on the folder you're sharing from the Meerkat, then click "Sharing Options." is the "Guest Access" box checked?

---

### Post by eightbits89 on 2011-02-09
Yes, I have those  check box's selected. BTW, the printer sharing does work. :p

On the Windows PC: 
Windows Explorer->My Network Places->Entire Network->Microsoft Networks (nothing else displayed) Clicking 
Displays Mshome and Workgroup.

Clicking on Workgroup brings up the Ubuntu Machine. When clicking on this , I get an error msg indicating that I XXXX-MEERKAT-Nxxxxx-NetTop erver(Samba,Ubuntu) is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access privileges. 

The Parameter is incorrect. :confused:

Clicking on MSHOME brings up the Icon for Mshome. When clicking on this Icon it displays the Windows machine.
Selecting this  then displays a drop down displaying: A folder Shared Docs, a folder Scheduled Task, 4 printer icons, and a folder Printers and faxes. Clicking here shows 5 printer Icons, the additional printer "FinePrint" can not be networked.
When clicking on Mshome->SharedDocs it displays the Windows folder set up as shared. For testing I have 2 files there.
I can access that folder and files via windows as I expected to be able to do.

From the UBUNTU Places->network I see the Icons for: 
 name-MEERKAT-N and an icon for Workgroup. As I understand , the workgroup is supposed to relate to the Windows folder(s).
Clicking on this (workgroup) Icon displays (again) both the Mshome Icon as well as the Workgroup icon.
This is a confusing part to me, displaying these Icons again(?).
At this level, clicking on MSHOME displays the Windows PC Icon and selecting that one displays folders ADMIN$, C$, PRINT$ and SharedDocs which contains two test files and can be accessed on the Ubuntu PC.

At this point I can access either of the two files in that folder , add and edit the files. I can also edit the files in the same manner from the windows machine as well.

I am thinking that the Ubuntu sharing must not be set up correctly(?).
When , on the Windows machine, and clicking on the workgroup->Ubuntu machine and I get the previously mentioned error, I never get a prompt to enter user and password. I think that indicates the error but not sure.

I am hoping someone can correct me on the errors.

Thanks in advance.

---

### Post by Morbius1 on 2011-02-09
>  Clicking on Workgroup brings up the Ubuntu Machine. When clicking on  this , I get an error msg indicating that I [COLOR=Blue]XXXX-MEERKAT-Nxxxxx-NetTop[/COLOR]  erver(Samba,Ubuntu) is not accessible. You might not have permission to  use this network resource. Contact the administrator of this server to  find out if you have access privileges. If that's your actual host name it's 11 characters too long.

Go back into Ubuntu, edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And add the following line to the [global] section:
```
netbios name = something
```[COLOR=Blue]NOTE: "something" must be 15 characters or less in length[/COLOR]

Save smb.conf and then restart samba:
```
sudo service smbd restart
```

---

### Post by eightbits89 on 2011-02-09
Thanks for the reply isantop and Morbius1:  I looked at the file (smb.config) and there is no existing netbios entry in it. Do you mean I have to just add that line with a different name any where after the [GLOBALS] area?
 Also, will this require I change the name of the Windows computer?  If I do that, will it be required to reset the remote printer parameters?  Once again thanks to the replies.
I think that this can be resolved.....

---

### Post by Morbius1 on 2011-02-09
Anywhere in the [global] section. Right after the WORKGROUP line makes the most sense to me but it really doesn't matter.
> Also, will this require I change the name of the Windows computer?I think Windows prevents you from choosing a name longer that 15 characters so I don't think that's an issue.

---

### Post by eightbits89 on 2011-02-09
Well I changed and added the netbios , but had the identical results. So, I will continue on and try to get this working. Thanks for your efforts. Cheers

---

### Post by Morbius1 on 2011-02-10
What would be helpful for those wishing to help is for you to post the output of the following command:
```
smbtree
```It's hard to follow from your description who's doing what to who. The output of that command will list every workgroup and within them every host on your LAN or else provide error messages if something isn't right.

---

### Post by eightbits89 on 2011-02-10
The results of: smbtree


WORKGROUP
    \\JERRY                  jerryl-Meerkat-NetTop server (Samba, Ubuntu)
        \\JERRY\icons              
        \\JERRY\sharefolder        
        \\JERRY\IPC$               IPC Service (jerryl-Meerkat-NetTop server (Samba, Ubuntu))
        \\JERRY\Documents          
        \\JERRY\print$             Printer Drivers
jerryl@jerryl-Meerkat-NetTop:~$ 

Previous send was not formatted well.

Hope this offers some insight.
Thanks much for the assistance. :D
Cheers

---

### Post by Morbius1 on 2011-02-11
> Clicking on Workgroup brings up the Ubuntu Machine. When clicking on  this , I get an error msg indicating that I XXXX-MEERKAT-Nxxxxx-NetTop  erver(Samba,Ubuntu) is not accessible. You might not have permission to  use this network resource. Contact the administrator of this server to  find out if you have access privileges. It would appear from the output of smbtree that this error has now been fixed. So as long as linux file permissions are in sync with how you set up your share everything should work.
> At this level, clicking on MSHOME displays the Windows PC Icon and  selecting that one displays folders ADMIN$, C$, PRINT$ and SharedDocs  which contains two test files and can be accessed on the Ubuntu PC.Although access to the Windows PC seemed not to have been an issue, smbtree has no output for that machine. Perhaps it was not on the LAN at the time you ran the command.

If you still can't access the Ubuntu machine I suspect this is not a Samba problem but a Linux file permissions problem. The entire path to the target shared folder has to have the right permissions or else the remote user will never gain access. Please post the output of the following commands:
```
testparm -s
``````
net usrshare info --long
```

---

### Post by eightbits89 on 2011-02-12
Results of: testparm -s
 
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = JERRY
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

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Documents]
    path = /home/jerryl/Documents
    guest ok = Yes

Please note that: net usrshare info --long did not work(?).

Also, after working on another seemingly unrelated problem and making changes to
files associated with Evolution and then restarting both Windows and Ubuntu, it seemed to be working. 

The Evolution problem was the loss of contacts and email which was later restored after support from System76 (thanks guys). The Evolution issues showed up after attempting to install programs to fix a DVD movie player issue. Seems unrelated to me.

I still think something isn't set up correctly in the file sharing and that is due to my lack of experience in using/configuring Linux :confused:

I noticed on one occasion, when it first seemed to work correctly, I actually got the user/password window on the Windows machine. After that I no longer get that prompt. 

Not sure if I should flag this thread as 'fixed' or not. I will use the file sharing some more and then post as to results.

Thanks for the support,

Cheers

---

### Post by Morbius1 on 2011-02-12
You've only got one share:
> [Documents]
    path = /home/jerryl/Documents
    guest ok = YesAnd it's set to allow guest access - read only. So I'm not sure why Windows is / was even asking you for a password to gain access. The only thing I can think of is that the Linux file permissions are / were not allowing "others" access. If you do a:
```
ls -dl /home/jerryl/Documents
```It should come back with at least this for all this to work:
> drwxr-xr-x 2 jerryl jerryl

---

