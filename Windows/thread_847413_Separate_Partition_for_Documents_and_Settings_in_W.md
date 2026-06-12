---
title: "Separate Partition for Documents and Settings in Windows 2000"
date: 2008-07-02
forum: Windows
---

### Post by Jeffery Mewtamer on 2008-07-02
Doing a search provided no help, so I apologize if this has been asked before.

I manage a pair of computers that are used by individuals that either cannot or refuse to use Linux. One is running Windows 2000 and the other is running XP(think of doing a clean install of 2000 though).

I have the hard drives on both systems partitioned 5GBs for C Drive with the rest distributed to D. I have made my best attempts to store all user files on D and make it easily accessible to the users involved. In a nutshell, I am trying to emulate the Linux concept of a Home Partition.

There are several problems with this system:
1. most programs default to saving in My Documents, so I either have to manually move files to D on a regular basis or configure every application individually.
2. It confuses the users I serve when they fail to find files under shortcut to D.
3. Since the users are on limited accounts, I have to modify D's advanced file permissions, which I feel is a potential security issue since I do not fully understand these permissions.

Ideally, I want to tell Windows 2000 to store user profiles at D:\Documents and Settings instead of C:\Documents and Settings. If this is possible, it would alleviate one of the most annoying steps in fixing these systems when they break completely, and possibly even help to prevent such catastrophic failures by simplifying their operation for the users, and their maintenance for me.

---

### Post by ilrudie on 2008-07-02
There is a way to do this I'm pretty sure but I can't recall if its a registry hack or just a setting somewhere.  You can even store profiles on a SMB share I think.  Its probably more common in Citrix and Terminal Server setups (thats the only place I have ever done it) so you may want to research it from that angle.  I will post back if I recall anything more about it.  I no longer have a windows box to toy with so I can't really look around on it track it down for you.

---

### Post by rickyjones on 2008-07-02
> **Jeffery Mewtamer said:**
> Doing a search provided no help, so I apologize if this has been asked before.

I manage a pair of computers that are used by individuals that either cannot or refuse to use Linux. One is running Windows 2000 and the other is running XP(think of doing a clean install of 2000 though).

I have the hard drives on both systems partitioned 5GBs for C Drive with the rest distributed to D. I have made my best attempts to store all user files on D and make it easily accessible to the users involved. In a nutshell, I am trying to emulate the Linux concept of a Home Partition.

There are several problems with this system:
1. most programs default to saving in My Documents, so I either have to manually move files to D on a regular basis or configure every application individually.
2. It confuses the users I serve when they fail to find files under shortcut to D.
3. Since the users are on limited accounts, I have to modify D's advanced file permissions, which I feel is a potential security issue since I do not fully understand these permissions.

Ideally, I want to tell Windows 2000 to store user profiles at D:\Documents and Settings instead of C:\Documents and Settings. If this is possible, it would alleviate one of the most annoying steps in fixing these systems when they break completely, and possibly even help to prevent such catastrophic failures by simplifying their operation for the users, and their maintenance for me.

It is very simple to move the My Documents folder on Windows 2000 and Windows XP.

1. Right Click "My Documents" folder and click Properties
2. Type the new path (D:\MyDocs\) into the Target text box
3. Click OK and then click Yes to move all the files.

Now the My Documents is located on the D: drive and you do not need to change any applications.

However moving the other folders is a little trickier than this. You can use TweakUI to do it or you can manually modify the registry.

[http://www.google.com/search?hl=en&q=redirect+profile+folders+windows+xp+windows+2000&btnG=Google+Search](http://www.google.com/search?hl=en&q=redirect+profile+folders+windows+xp+windows+2000&btnG=Google+Search)
[http://www.microsoft.com/technet/community/en-us/management/manage_faq.mspx](http://www.microsoft.com/technet/community/en-us/management/manage_faq.mspx)
[http://technet2.microsoft.com/windowsserver/en/library/60b2157c-aa5b-44f2-b045-b74d2fd1bf701033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/60b2157c-aa5b-44f2-b045-b74d2fd1bf701033.mspx?mfr=true)
[http://en.wikipedia.org/wiki/Folder_redirection](http://en.wikipedia.org/wiki/Folder_redirection)
[http://techbold.com/2007/02/redirecting-specail-folders-in-widows/](http://techbold.com/2007/02/redirecting-specail-folders-in-widows/)

The simplest way to bulk-redirect all the "Special Folders" would be to use a local Group Policy Object (GPO). 

I hope this helps!

Sincerely,
Richard

---

### Post by MaxIBoy on 2008-07-03
Nice. I have multiple installations of Windows on one partition, only one actually works. I still prefer to save everything to my old installation because that's where everything is. Now I can!

---

