---
title: "file server problem.urgent unexpectable"
date: 2008-07-15
forum: Server Platforms
---

### Post by soundofhammer on 2008-07-15
Hi everybody . &#304;n my main server Dapperdrake 7.06 installed and Wmware workstation on it.1.0.3, And i have 8 virtual servers over this interface.One of them is my file server. LAst night i change the operation panel &#304;t's the trigger, whatever; i restart the servers. Everything looks like cool. But this morning i check the mail server and couldnt connect to database.I say how could it be .And than face with disaster. There're 250 gb data on my File server also mail database on it. But now nothing on it. I look for the reason and found it. When i restart it &#304;t reverts itself to a old time from vmware workstation snapshots. So i couldn't do anything over wmvare because there is only one snapshot ,i couldn't do anything over fileserver because Files lives in 2007,And only windows time service seem up to date.
So i couldnt do anything over 2003 but i hope i could do something over ubuntu . But what can i do ??  Thanks very much.

---

### Post by windependence on 2008-07-16
Sorry, you are out of luck. You had snapshots turned on, you had taken a snapshot, and then you had the option checked to revert to snapshot after reboot. when you rebooted, it reverted back to the earlier snapshot and all your data is gone. You have to be really really careful with snpashots in VMware.

-Tim

---

### Post by soundofhammer on 2008-07-17
Yes thank you i get the file operation over vmware.But it's too late for me. I want to ask that "does ubuntu has a restoration point". Does it have an disk image in somewhere . If i can make a litle time travel everything will be fine. I found some data recovery firms.I'll go there by tomorrow but may be i have an another chance to take data over ubuntu.

---

### Post by songshu on 2008-07-17
well.....

if you wait another 50 years you might meet some time travelers who can bring you back to yesterday.....or maybe not.

there is no back in time option...for the future you might consider using the ext2 file system to restore deleted files, but it would not do you any good in a situation as this. The only thing that could have helped you in this case would be backup backup backup.

nevertheless...i seriously doubt that it will work on an image like this......but.....if the data is worth recovering you might want to try ***_testdisk_*** no guarantees but i would give it a look since it saved my life before after recovering files from a formatted disk.

---

