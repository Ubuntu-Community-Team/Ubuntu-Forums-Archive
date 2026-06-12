---
title: "iFolder Ubuntu 10.04 (Lucid Lynx)   Active Directory"
date: 2010-06-21
forum: Server Platforms
---

### Post by Keamas on 2010-06-21
Hi I installed a iFolder Server to Sync folders between my clients. I followed this howto: [https://help.ubuntu.com/community/iFolderInstall](https://help.ubuntu.com/community/iFolderInstall)

Now I wana connect the iFolder Server with my Active Directory for the userinformation. But I don't get the iFolder server connected with the Active Directory.

Is there anyone who already did it ? And tell me how to do it  ?
The only documentation I found is this:

[http://www.novell.com/documentation/ifolder3/ifolder38_admin](http://www.novell.com/documentation/ifolder3/ifolder38_admin)

> 5.4 Active Directory

If you are using Active Directory as the LDAP source for iFolder, consider the following:

    *

      During iFolder server configuration, ensure that you select the Require a secure connection between the LDAP server and the iFolder Server option.
    *

      An iFolder proxy user will be assigned browse rights on the user containers that are configured. On the other hand a proxy user will be assigned read and compare rights for all the attributes of users,groups, and container objects configured under the container.
    *

      Ensure that for all users, the User must change password at next login option is not set. This is because iFolder does not support password change. Setting this option will lead to a login failure and an appropriate message will be displayed in the Simias.log file.

NOTE:Read rights refer to the entry rights and all the attributes rights.

For information on how to configure Active Directory as an alternate LDAP server, see Novell iFolder LDAP Configuration


It would be great if anyone can tell me how to do this !!
thx

---

