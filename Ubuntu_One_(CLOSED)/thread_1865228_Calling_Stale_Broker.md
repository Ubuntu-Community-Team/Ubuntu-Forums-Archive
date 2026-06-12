---
title: "Calling Stale Broker"
date: 2011-10-19
forum: Ubuntu One (CLOSED)
---

### Post by exsysprog on 2011-10-19
Things seemed to be going well with U1 2.0.1 on Windows7.  I'm also running it on Natty and on my Android phone which both seem to be working fine. The Windows client has stopped syncing and will eventually produce an error dialog containing the details:

DeadReferenceError
'Calling Stale Broker'

I seem to be dead in the water on this.  Is anyone else seeing these symptoms / has found a work around or fix??

---

### Post by exsysprog on 2011-10-24
Uninstalled and re-installed the windows client.  Same results as above. I anybody using a windows7 64-bit client successfully at this point or am I just lucky??

---

### Post by exsysprog on 2011-10-25
There seem to be a few threads running in regards to Windows 7 client screeching to a halt.

Does anyone presently have a working Windows 7 U1 client?  If so please acknowledge.

My Android client continues to work like a charm.

---

### Post by exsysprog on 2011-10-25
Added comment on launchpad Bug #878750. I have very little experience with launchpad so maybe I haven't followed protocol but .. the bug is currently in "unasssigned" status with "undecided" priority.  As far as I can tell Windows is dead in the water.  Seems kinda important.

---

### Post by exsysprog on 2011-11-12
Am I to interpret the complete lack of response as an indication that NOBODY has a working U1 client on Windows 7?

---

### Post by alex_sv on 2011-11-16
I've win7 on one of my laptops.
Reboot works for me to get rid of this message (I noticed that it occurs after laptop wakes up).

---

### Post by dokoma on 2011-11-28
I meet the same error in Windows

finally I got it
1.shutdown the 3 process contain ubuntu
such as windows-ubuntu-sso-login.exe
ubuntuone-syncdaemon.exe
ubuntuone-control-panel-qt.exe

2.AND then GOTO the Folder such as
C:\Documents and Settings\Administrator\Local Settings\Application Data\xdg\ubuntuone\syncdaemon\tritcask

3.Delete them all  and restart the Ubuntu One icon.

and now it works for me.

I think it must be some error breaked during the sync and can't resume .
hanging dead. what I do maybe make it a restart.

---

### Post by exsysprog on 2012-01-03
thanks dokoma .. I've been very tied up so  I haven't had a chance to confirm your approach but I will do so within a day or two and post results here.. I have high hopes.

---

### Post by exsysprog on 2012-01-05
Well I'm not sure if Dokoma's recommendations or the client upgrade taht just took place made the difference but .. it looks like I'm back in business. I did shut down the recommended processes and delete the recommended files.  Once I restarted the U1 client it showed only the UbuntuOne folder as being configured to sync, but shortly thereafter the rest of my folders showed back up in the "always sync" list and the did in fact sync. I'm back in business.

Thanks to all.

---

### Post by oliver369 on 2012-02-06
I have had the same issue on Windows 7 x64. dokoma's suggestion seems to work however it seems to "forget" which folders were synchronised.
This issue is a little frustrating to say the least :(

---

### Post by sysop on 2012-05-17
> **dokoma said:**
> I meet the same error in Windows

finally I got it
1.shutdown the 3 process contain ubuntu
such as windows-ubuntu-sso-login.exe
ubuntuone-syncdaemon.exe
ubuntuone-control-panel-qt.exe

2.AND then GOTO the Folder such as
C:\Documents and Settings\Administrator\Local Settings\Application Data\xdg\ubuntuone\syncdaemon\tritcask

3.Delete them all  and restart the Ubuntu One icon.

and now it works for me.

I think it must be some error breaked during the sync and can't resume .
hanging dead. what I do maybe make it a restart.

Just used this resolution for Windows 7 Pro x86 with version 3.0.0 of Ubuntu One client for Windows and worked great! Thanks!

---

### Post by affinityvision on 2012-08-19
My solution was to quit U1 via the system area app icon and restart it via the desktop icon.  It then carried out the sync operation, but it didn't update the space used!  So I quit again the same way and restarted it, then the usage updated.

How can I recommend this product choice to family, friends, colleagues or customers when it needs this much baby sitting?  Sure I could have carried out the other suggestions above (shutting down and restarting services), but the average Joe isn't going to be able to do that easily without clear instruction -- heck some people can't even understand how to create a new folder to store files...

---

### Post by mb59 on 2013-01-19
Thanks for the tip dokoma. It worked for me!!!
The folder in WIn7 for me was

C:\Users\michael\AppData\Local\xdg\ubuntuone\syncdaemon\tritcask

After deleting the files in this folder and restarting U1 everything worked fine. You'll lose your sync directories. Delete it via the U1 Homepage and reset it again.

Thx and BR
Michael

---

### Post by volos-86 on 2013-07-30
thanx

---

