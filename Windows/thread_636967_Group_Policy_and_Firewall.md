---
title: "Group Policy and Firewall"
date: 2007-12-10
forum: Windows
---

### Post by Black Mage on 2007-12-10
I'm trying to get Group Policy to disable everyones FireWall in the domain. I tried this method but it doesn't work.

```

1. From Start -> Run -> gpedit.msc (to open Group policy editor) 
2. Computer Configuration folder. 
3. Open the Administrative Templates folder. 
4. Open the Network folder. 
5. Open the Network Connections folder. 
6. Open the Windows Firewall folder. 
7. If the computer is in the domain, then open the Domain Profile folder; otherwise, open the Standard Profile folder. 
8. Click Windows Firewall: Allow remote administration exception. On the Action menu, select Properties. 
9. Click Enable, and then click OK. 

```

Does anyone know how to use Group Policy to disable the FireWalll?

Thnx in advance.

---

### Post by rickyjones on 2007-12-11
Are you running gpedit.msc on the domain controller from the run menu? Because that will only affect the local group policy.

You need to edit the domain group policy object that affects your computers. Do you know what kind of active directory layout you have?

Let me give you an example of what to do: On the domain controller open up the Active Directory Users and Computer MMC object. Expand your domain and find the organizational unit that your computers are in. Right click the organization unit and click Properties. One of the tabs will be Group Policy. Click it. Now you should see the group policy object that affects this organizational unit. Right click > Edit and make your changes in this group policy window.

The procedure is vastly different if you installed the Group Policy Management Console. I highly recommend reading articles on technet.microsoft.com for more information.

PM me if you'd like some more assistance in group policy and active directory.

Hope it helps!

-Richard

---

