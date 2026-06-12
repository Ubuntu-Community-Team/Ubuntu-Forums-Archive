---
title: "Samba: Windows YAY, Samba:Kubuntu NAY!"
date: 2008-09-25
forum: Server Platforms
---

### Post by DarkPhoenixTSi on 2008-09-25
Okay, after getting SAMBA configured, I can access the two folders I made from all of my windows computers on my network (small workgroup). When I try to access from my Kubuntu machine, it sees the workgroup under SAMBA Shares, and then prompts for a password. I used the id and pw that I created, and it fails. It's not a big deal, but I will be using the Kubuntu machine to remote in for administration.

I thought I won when I got Windows to communicate, only to get kicked in berries by Kubuntu.

Any help would be greatly appreciated.

---

### Post by Megabird on 2008-09-25
For the Ubuntu computer to be able to get on the shares of Windows XP, you need to activate the guest account, and change a policy (only of you are not in an Active Directory Domain, because it is already set in the default domain policy) in your XP computers.

To activate your guest account:
[LIST]
[*]Click on "Start" / "Execute"
[*]Type "compmgmt.msc" and click "OK"
[*]Open "Local Users and Groups" / "Users"
[*]Double-Click on "Guest"
[*]Untick the box "Account is disabled" and click "OK"
[*]Close the window "Manage your computer"
[/LIST]
To change the local policy (You'll need to do this only if you are not in an ActiveDirectory Domain or if you have a pre SP2 windows XP) : 
[LIST]
[*]Click on "Start" / "Execute"
[*]Type "GPEDIT.MSC" and click "OK"
[*]Open "Computer Configuration" / "Windows Settings" / "Local Policies" / "User Rights Assignment" 
[*]Double-click on "Deny access to this computer from the network"
[*]remove "Guest" from the list and click "OK"
[*]Close the "Group Strategy" window
[/LIST]
You should now be able to connect to your Windows computer with ubuntu and it sould not ask you to put in a username/password.

---

### Post by DarkPhoenixTSi on 2008-09-26
Well, accessing the Windows machines is done. The issue I am running into is accessing the Linux Shares with my Kubuntu 8.04 box.

---

