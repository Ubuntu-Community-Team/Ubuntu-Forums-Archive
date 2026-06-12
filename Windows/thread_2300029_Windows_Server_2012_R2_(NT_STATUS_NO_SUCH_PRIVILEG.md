---
title: "Windows Server 2012 R2 (NT_STATUS_NO_SUCH_PRIVILEGE)"
date: 2015-10-23
forum: Windows
---

### Post by David_Silva_Ribeau on 2015-10-23
Hello Guys,

I try to setup Samba as a AD Member on Winodws Server 2012 R2.
I used the Documentation from the official Samba Wiki (wiki.samba.org Setup_a_Samba_AD_Member_Server). 

I want to use the ACL's from windows for the samba Login. Therefore in the Documentation 
in Section SeDiskOperatorPrivilege [https://wiki.samba.org/index.php/Shares_with_Windows_ACLs](https://wiki.samba.org/index.php/Shares_with_Windows_ACLs) I have to use the command 
[COLOR=#000000][FONT=monospace]
net rpc rights grant 'SAMDOM\Domain Admins' SeDiskOperatorPrivilege -U'SAMDOM\administrator' -I dc1.samdom.example.com
[/FONT][/COLOR]
but it returns only NT_STATUS_NO_SUCH_PRIVILEGE.

After a while searching on google I find out the SeDiskOperatorPrivilege isn't avaiable on Windows Server 2012 R2.
(net -S 192.168.XX.X -U% rpc rights list)

Can anybody of you Guys help me, plz?


Regards,
David

---

