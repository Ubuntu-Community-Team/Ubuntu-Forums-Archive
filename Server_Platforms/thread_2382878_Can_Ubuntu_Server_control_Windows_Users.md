---
title: "Can Ubuntu Server control Windows Users?"
date: 2018-01-18
forum: Server Platforms
---

### Post by whiteworx on 2018-01-18
The company I work for would like to change the business so everyone is on a hotdesk.

We currently all have our "own" machines and connect to a QNAP box which is acting as the server, but the management want to change this.


Ideal Scenario...

[LIST]
[*]Ubuntu Server holding all the user login information and their computer customisations. - All files will be held in their own 'home' directories on the NAS which will be sent to their desktop when logged in.
[*]The users desktop PCs will all be running Windows 10 and have the MS Office Suite installed on them.
[*]Have remote access for certain users from their home locations.
[*]QNAP NAS connected as the storage device for these files/folders - this is on a constant sync with OneDrive.
[/LIST]

Is something like this doable? I'm not asking how to do it, but is Ubuntu capable of it or will I have to opt for a Windows Server?

Ta
Ian

---

### Post by QIII on 2018-01-18
Moved to Server Platforms

---

### Post by SeijiSensei on 2018-01-18
Modern versions of Samba can function as an Active Directory Domain Controller:  [https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller)

You can use a simpler method if you're only interested in authenticating users so they can access shares on the server:  [https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Standalone_Server#Creating_a_Local_User_Account](https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Standalone_Server#Creating_a_Local_User_Account)

---

### Post by LHammonds on 2018-01-19
Yes, Ubuntu (any Linux) can do this.  One of my [active research projects](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=235) is to setup Ubuntu as a Samba Active Directory server in order to host a network shared file repository and join Windows PCs to the domain so the same account/password can be used on any of the machines.

The current highest functional level supported is 2008 R2 but should be sufficient for your needs.

LHammonds

---

