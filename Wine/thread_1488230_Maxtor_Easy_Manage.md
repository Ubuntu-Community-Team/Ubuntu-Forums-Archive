---
title: "Maxtor Easy Manage"
date: 2010-05-19
forum: Wine
---

### Post by pizza-is-good on 2010-05-19
Hi there.

I have a Maxtor One touch 3 mini backup HDD that I'd like to use in Ubuntu. I have installed the utility using wine, but every time I try to run it, I get the following error:

```
Application Initialization Failed: maxrestore.dll
```I click OK on it and the utility does open up, but it does not detect my HDD. (It still shows up on my desktop however)

Anyway, all help will be appreciated.

I'll provide all information that is needed, if you tell me how to find it.
Please don't try to get me to replace the Maxtor utility for anything else.:lolflag: This does exactly what I need it to do exactly the way I want it to do. If you do know however of a FOSS version that is nearly the same, let me know.

Thanks in advance.

~pizza

---

### Post by asdfoo on 2010-05-20
what does it do?

---

### Post by pizza-is-good on 2010-05-21
> **asdfoo said:**
> what does it do?

It only works on Maxtor drives. Anyways, what it does is it makes a copy of whatever directories you specify to the backup drive. The files in the backup drive are still navigable and are not compressed like all other backup utilities I have used. This allows me to just use my backup drive for transferring files from my computer to another one without having to copy the file onto another drive, since it is already there. Because you can 'see' all the files, restoring files that I accidentally delete on my computer is much easier, as all I have to do is just copy the file onto my computer again, not do a full data restore. Another nice feature is that it keeps a history of file versions. If the file changed since it was last used, the new version is copied over, and the old one is put in a 'history' folder in the backup drive. It does this for any number of versions that you want. And of course it has a backup schedule.

I have not been able to find a FOSS version of a similar program. All of the backup utilities I find for linux compress all the files and are only useful for if you have to do a full system/data restore.

If you do know of one that works as Maxtor EasyManage, please let me know.

~pizza

---

### Post by hikaricore on 2010-05-21
I think you can accomplish this with rsync, but I'm not really familiar enough with it to say for sure.
You basically want to schedule backups to your external drive?  Not an overly complex request at all.

---

### Post by pizza-is-good on 2010-05-22
> **hikaricore said:**
> I think you can accomplish this with rsync, but I'm not really familiar enough with it to say for sure.
You basically want to schedule backups to your external drive?  Not an overly complex request at all.

It's not the scheduling that is hard to find, that is the least of my concerns, its the fact that I can still go through my backup as if it was my HDD. Nothing is compressed and packaged into hundreds of little .tar(s) that are only good for restoring.

I'll look into rsync. Thanks for the pointer.

~pizza

---

### Post by hikaricore on 2010-05-22
I'm pretty sure that archiving is optional in any backup method worth mentioning, I'm not sure where you get the idea that it isn't.

---

### Post by pizza-is-good on 2010-05-25
alright. bump. Anyone actually know how to get that .dll working in wine? That was what I was asking...

---

### Post by pizza-is-good on 2010-05-26
any ideas?

---

### Post by cascade9 on 2010-05-26
I have an idea.  :D 

If you acess to a windows machine with the maxtor software installed, find the .dll, copy it to whatever you want to move the file your linux machine. Then try following this- 

> The .dll goes in your C:\windows\system directory (the one wine made for you). Once it's in place, you'll need to run winecfg, hit the "Add Application..." button for the game you're running, and go through the [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]file[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") dialog to find the game's executable. Once it's added, highlight its name in the list, go to the "Libraries" tab, and add an override for the .dll you need.

[http://www.linuxforums.org/forum/wine/57825-install-dlls-wine.html](http://www.linuxforums.org/forum/wine/57825-install-dlls-wine.html)

Copied because I'm to stupid and painkillered up to do much apart from copy n paste LOL

---

### Post by pizza-is-good on 2010-05-27
OK. Did that.

Still not working, but here is the problem now:

According to the tutorial you linked me to, I need to reinstall the software. That is fine. The problem is that I cannot unintstall the old Maxtor EasyManage that I already had installed. When I go to Wine>>Uninstall Wine Software and attempt to remove the already installed software, it tells me that I need setup.exe to uninstall. How can I easily remove those programs without having to find setup.exe? which I am sure I don't have because the installer for Maxtor EasyManage is Launch.exe. :lolflag:

Thanks,

~pizza

---

### Post by cascade9 on 2010-05-28
I'm no WINE expert, I've never even tried to uninstall a program from WINE. But did you try pointing it at lauch.exe where it asked for setup.exe?

---

