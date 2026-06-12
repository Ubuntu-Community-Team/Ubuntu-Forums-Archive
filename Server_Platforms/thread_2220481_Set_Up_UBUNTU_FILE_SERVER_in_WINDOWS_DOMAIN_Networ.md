---
title: "Set Up UBUNTU FILE SERVER in WINDOWS DOMAIN Network"
date: 2014-04-28
forum: Server Platforms
---

### Post by noriel on 2014-04-28
I have a Windows Domain Server 2008R2... I must use and stick with it for Windows Activation...

I manage to join my ubuntu desktop 12.04 in my windowsDomain using LIKEWISE...

I manage to create a folder in my ubuntu and share it to any WindowsPC in my DomainNetwork with samba...



in my current set up... I have Windows2008r2 as PDC and a windowsPC as file server....

[COLOR=#0000ff]1. I create a folder in windowsPC that is connected to the domain then share the folder
    foldername : **ccsfs**

2. In my PDC. I create a user in AD. under PROFILE, I configure a homefolder and direct it to ccsfs folder that I created in step1

      \\ccsfs\%username%

=== as a result.. each user has its own homefolder that stored in **ccsfs** folder.. and can't touch others' homefolder... [/COLOR]


[COLOR=#ff0000]**BUT.... when I do this in ubuntu...**[/COLOR]

1. 1. I create a folder in UBUNTU that is connected to the domain then share the folder with samba's help
    foldername : **ccsfs**

2.  In my PDC. I create a user in AD. under PROFILE, I configure a  homefolder and direct it to ccsfs folder that I created in step1

      \\ccsfs\%username%

=== as a result.. each user has its own homefolder that stored in **ccsfs** folder.. [COLOR=#ff0000]BUT IT CANT WRITE FILES ON ITS OWN HOMEFOLDER (permission problem) and everyone on the network can see other shared folders[/COLOR]


I hope I'm able to express the problem and the help I need... 

Im new to samba and linux... please help.. Thanks

---

### Post by Gyokuro on 2014-04-28
Hi

I do not know what you have already done but you should read at first:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

and the SAMBA documentation is a must read:

[http://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](http://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server) 

[http://wiki.samba.org/index.php/Setting_up_a_home_share](http://wiki.samba.org/index.php/Setting_up_a_home_share)

- HTH

---

### Post by noriel on 2014-04-30
> **Gyokuro said:**
> Hi

I do not know what you have already done but you should read at first:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

and the SAMBA documentation is a must read:

[http://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](http://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server) 

[http://wiki.samba.org/index.php/Setting_up_a_home_share](http://wiki.samba.org/index.php/Setting_up_a_home_share)

- HTH

thanks for the links... 

This might help me.. [https://wiki.samba.org/index.php/Setup_and_configure_file_shares#SeDiskOperatorPrivilege](https://wiki.samba.org/index.php/Setup_and_configure_file_shares#SeDiskOperatorPrivilege) 


[LIST]
[*][SIZE=2] [COLOR=#ff0000]**Log on to a Windows machine using an account, to which the  „SeDiskOperatorPrivilege“ was granted to or an account in a group with  granted privilege. **[/COLOR][/SIZE]
[/LIST]


but when I run 
**net rpc rights grant 'CCS\Domain Admins' SeDiskOperatorPrivilege -Uadministrator**

i got 

[I]noriel@ccslynxfs:~$ net rpc rights grant 'CCS\Domain Admins' SeDiskOperatorPrivilege -Uadministrator
Enter administrator's password:
Failed to grant privileges for CCS\Domain Admins (NT_STATUS_ACCESS_DENIED)[/I]

WHY? anyone please help?

---

### Post by Gyokuro on 2014-05-02
Could you please post: net rpc rights list accounts -Uadministrator # Existing privileges

---

