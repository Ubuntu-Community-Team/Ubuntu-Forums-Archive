---
title: "Samba with Roaming profiles"
date: 2010-05-27
forum: Server Platforms
---

### Post by yesrno on 2010-05-27
Hello,
I want to create an extra Ubuntu Server for storing roaming profiles, and I need some help doing so because I really can't get this to work in my test environment.

I got:
One Win2k8 server as Domain controller.
One Ubuntu 9.10 server who is a member of the domain using Samba. Winbind is working correctly.. I can at least connect to shares with user names of the AD.

Anyway my client (WinXP) currently logs on to the AD and works from there. I want to configure it so that all accounts are going to use roaming profiles, but here it comes... I want to store the roaming profiles on the extra Ubuntu server.
I really have no clue how to get this done, I tried a couple of different configurations but I hope someone here could give me some guidance.

Thanks in advance!

---

### Post by mstjohn1974 on 2010-05-27
What are the symptoms you are seeing...how is your SAMBA Share configured..can you post your smb.conf and if you see error events in 2k8 Server related to that issue could you post them too?

---

### Post by yesrno on 2010-05-27
Well I tried different configurations I thought they "might theoretically work".
One was to just share a folder with Samba, and make a mapdrive with the Win2k8 server to that folder, then in the User profile path of the user, I filled in driveletter:\\%username%. But this soon led to permission problems (Even with a public writable share).
I also tried a configuration similar to this one in Samba, which is from the following article:
[http://wiki.samba.org/index.php/Samba_%26_Windows_Profiles](http://wiki.samba.org/index.php/Samba_%26_Windows_Profiles)

```
 
 logon path = \\%L\profiles\%U 
 logon home = \\%L\%U\.9xprofile 
 logon drive = P:

```

But without success.

---

### Post by mstjohn1974 on 2010-05-27
I think the issue is that you use %L which would be the Servername and I do know if Windows 2k8 can make use of %L....try using the servername of the SAMBA Server or the ip address

---

### Post by yesrno on 2010-05-28
Then I would still have to fill in the userprofile path on the win2k8 server and such ?
Seeing Samba ain't the PDC.

---

### Post by mstjohn1974 on 2010-05-28
If your Win2k8 is your DC and Samba is just a file server, then you should only use the Win2k8 to specify where the profile is located and not the samba box because the users authenticate through Win2k8.

If your samba box is the one who handles user accounts then you need to manage this on samba.

---

### Post by yesrno on 2010-05-28
Yea but that is kinda the problem, If I create a share for saving the profiles let's say /Profiles, and share that folder, then make the DC use that share for saving the profiles, then every user would save there profiles in /Profiles/Username automatically right ? But I don't think the permissions would be correctly this way. Because when a user logs on, he should have access to the folder which he doesn't have, because the folder 
/Profiles/Username doesn't even exist for users that haven't logged in ever, yet.
Or I have to create 500 folders for every user and set permissions to that but I don't really plan on doing that as you might understand :p

See my problem now :) ?

---

### Post by yesrno on 2010-05-29
bump, anyone ?

---

### Post by badger_fruit on 2010-05-29
Typically, setting up a user profile one would specify profile path to be:

\\server\share\%username%

When the user logs on, their folder is created automatically.
The share permission should be set to at least modify for network users.

I don't know about S2008 but in S2003 you can select multiple users at once to configure this parameter.  Perhaps there may be a group policy setting you can mess with to achieve this too but as I said earlier, 2008 isn't that familiar to me sorry.

Good luck.

---

