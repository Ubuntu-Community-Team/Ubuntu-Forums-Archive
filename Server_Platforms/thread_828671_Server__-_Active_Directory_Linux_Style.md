---
title: "Server  - Active Directory Linux Style?"
date: 2008-06-14
forum: Server Platforms
---

### Post by Cyberpawz on 2008-06-14
Here is my dilemma: 

I have three PCs, 12 users, and a computer without an OS.

This is what I want to do

Install Ubuntu into the computer without an OS, make it so that it the authentication server for the other computers, make it so that no matter what person logs into either of the three computers they can access their data from wherever they sit. 

I've seen documentation satiating that you need an Active Directory Server to make it happen, but I can't imagine Ubuntu not being able to do the same thing. So what am I missing? Can someone help here, because I don't think I am wording my searches here well enough to find the answer. 

Thanks in advance.

---

### Post by Ryan483 on 2008-06-14
A super easy way would be [SME Server]("http://contribs.org"), but you could accomplish the same thing with Ubuntu. Check out [HowToForge]("http://howtoforge.com/howtos/linux/ubuntu") if you want to install everything manually, which is not bad thing to do.

---

### Post by windependence on 2008-06-14
You could make the Ubuntu machine a domain controller/SAMBA server and acheive close to the same thing.

-Tim

---

### Post by bluefrog on 2008-06-14
LDAP server for authentication and NFS to export the /home of users (so /home by NFS is included in the /etc/fstab of the machines).

Depending on what is the need of the 12 persons, you could also have a central server with LTSP and have only 12 thin clients.

James Dupin

---

### Post by Cyberpawz on 2008-06-15
> **bluefrog said:**
> LDAP server for authentication and NFS to export the /home of users (so /home by NFS is included in the /etc/fstab of the machines).

Depending on what is the need of the 12 persons, you could also have a central server with LTSP and have only 12 thin clients.

James Dupin

I'd love thin clients but we can't use/afford them right now, it is an annoyance, the problem is everyone is use to windows, I want to use Ubnutu for the server so everything is stored in one place. I will be getting a data storage system for backup too if I can find it in the budget as well.

Since I want to do that, and people are not willing to change to Linux, what is the best way to take care of this situation? They still need their "Windows" although I'd rather see them use a Mac, or Linux at least.

So: 

LDAP in the Ubuntu for authentication, what is NFS?

---

### Post by Cyberpawz on 2008-06-15
> **windependence said:**
> You could make the Ubuntu machine a domain controller/SAMBA server and acheive close to the same thing.

-Tim

What would I be missing?

---

### Post by promodus on 2008-06-15
> **Cyberpawz said:**
> Here is my dilemma: 

I have three PCs, 12 users, and a computer without an OS.

This is what I want to do

Install Ubuntu into the computer without an OS, make it so that it the authentication server for the other computers, make it so that no matter what person logs into either of the three computers they can access their data from wherever they sit. 

I've seen documentation satiating that you need an Active Directory Server to make it happen, but I can't imagine Ubuntu not being able to do the same thing. So what am I missing? Can someone help here, because I don't think I am wording my searches here well enough to find the answer. 

Thanks in advance.

Can you define data? 
This could be a simple SMB share where all users save their data on a shared drive, or this could be as involved as their desktop & settings are identical at each workstation.

---

### Post by windependence on 2008-06-16
> **Cyberpawz said:**
> What would I be missing?


I can't tell you for sure because I am not an AD expert, but I know it won't be exactly the same. If you just want to share a directory on the network however, it works very well with AD.

-Tim

---

### Post by Cyberpawz on 2008-06-16
> **promodus said:**
> Can you define data? 
This could be a simple SMB share where all users save their data on a shared drive, or this could be as involved as their desktop & settings are identical at each workstation.

Desktops should be 100% identical, their desktop images can be their own, but specific users will have access to only specific folders on the server, etc...

It comes down to it like this:

Administrator (myself): Full Access
Sales Staff Lead:  Full access to Sales staff, but not system stuff.
Sales Staff: Their stuff only, and intranet access.
Lead Instructors: Access to only their group's stuff, and Intranet.
Instructors: Access to only their class material and Intranet.
Guests: No access, except to internet, all other data will remain hidden to them.

Hope this helps more.

---

### Post by vav on 2008-06-18
I think I want do the same thing as Cyberpawz... so here is what my requirements are:

0> Server is ubuntu, clients are windows 2000 and windows xp
1> Login authentication should be done at the server. i.e. if I add/delete a user, or change password, this should be reflected in all the nodes. further, if possible, admin/non-admin rights of the user should also be controllable from the server (which active directory can do)
2> Desktop of the user should look the same. So
 a> Background image should be same, selectable by the user!
 b> Desktop saved items _could_ be same
 c> home directory contents or data drive contents should be same wherever he logs in. this could be a smb mounted drive, but then if I create a new user the smb mount should be done from the server, i.e. I won't go to each client and map a network drive.

Is this possible? Open source? Free?

---

### Post by theonegod on 2008-06-19
The shared file and loin part probably is. The remote profiles though I doubt.

---

### Post by snakdoc on 2008-06-19
i am looking for this also i am wanting to have a centeral auth system

---

### Post by doogy2004 on 2008-06-19
the samba shares for each users isn't difficult, the problem is getting the windows clients verify the credentials of the users from the backend server.

Looks like Samba 4 should do the trick problem is, that it is in alpha [http://news.samba.org/releases/4.0.0alpha4/](http://news.samba.org/releases/4.0.0alpha4/)

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by Pro_D on 2008-06-20
Firstly, I am no expert on this stuff.  I largely followed the linked guide step by step (except for the DNS stuff which I had configured in advance for Dynamic updates and some other fun stuff).

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

That is a GREAT guide.  This helped me add PDC like behavior to my linux server (as all the client computers are currently windows XP).  BE CAREFUL a misstep when you don't notice it can be disastrous since you won't know something is wrong till you are largely done with the guide.  Also I recommend the command line tools (smbldap-tools) for changing things (like adding/removing users/groups) and phpldapadmin for verifying things and making small changes.  Also you will have to have the windows users using linux style user names.  There is a way to have windows style user names (capital first letter and spaces allowed) with this config though.  Involved editing one of the samba files but I misplaced the link and got to go.

The guide included some tidbits on things like the home drive (a share that follows the user) though I had the impression you could skip NFS if there were no linux clients to the server.  I think the guide puts you in a good position to get into roaming profiles which I think would cover about everything requested.

---

