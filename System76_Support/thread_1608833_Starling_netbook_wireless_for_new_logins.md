---
title: "Starling netbook wireless for new logins"
date: 2010-10-29
forum: System76 Support
---

### Post by DuchessLynne on 2010-10-29
Okay, I'll admit to be new to Linux, so I apologize if this is more an Ubuntu question than a System76 question.  I have a new Starling Netbook purchased last month.  I have two logins which have wireless working fine on them--there is a wireless icon at the top of the screen, you can click on it and see available networks.  However, I made a new login and no wireless icon appears at the top.  I've disabled and reenabled the wireless several times and that doesn't seem to help.  I can't find any other way to get the icon to show.  help!!! 

Thanks!

Lynne
  :confused:

---

### Post by Flyers2391 on 2010-11-02
> **DuchessLynne said:**
> Okay, I'll admit to be new to Linux, so I apologize if this is more an Ubuntu question than a System76 question.  I have a new Starling Netbook purchased last month.  I have two logins which have wireless working fine on them--there is a wireless icon at the top of the screen, you can click on it and see available networks.  However, I made a new login and no wireless icon appears at the top.  I've disabled and reenabled the wireless several times and that doesn't seem to help.  I can't find any other way to get the icon to show.  help!!! 

Thanks!

Lynne
  :confused:

Do you have a battery or volume icon?  If not, right click on the top panel and select "Add to Panel..." find "Notification Area" and add it.

EDIT: sorry, that is assuming you are using the desktop version not netbook remix, not sure how it works with that interface

---

### Post by Dave_L on 2010-11-02
I'm fairly new to Ubuntu, so this is only a guess.

Check the file /etc/group and see if the new user (without the wireless icon) belongs to the same groups as the old users (with the wireless icons).

Each line of that file represents one group.  The first field is the name of the group. The users in that group are listed at the end of the line, separated by commas.

---

### Post by Plecebo on 2010-11-17
A bit late to this discussion but, maybe this will be useful for others. 

By default Ubuntu does not add new user accounts with the ability to connect to wireless networks. 

In order to fix this you need to give the user the "connect to wireless and ethernet networks" permission. 

Open System -> Administration -> Users and Groups. 

Chose the user who you would like to have access and click the "Advanced Settings" button. On the User Priviliges tab put a tick into the box for "connect to wireless and ethernet networks"

If the person is logged onto the machine they will have to log off and back on for the permissions to take effect. 

Hope that clears up your issue.

---

