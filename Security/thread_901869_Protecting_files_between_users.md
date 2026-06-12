---
title: "Protecting files between users"
date: 2008-08-26
forum: Security
---

### Post by brad1138 on 2008-08-26
Maybe I should ask this in "beginners" but, I have 3 different logins in Ubuntu 8.04. I have found that files saved in the home/"user" directory are accessible to anyone. I can look into the files contained in anyones directory regardless of what name I log in under, it doesn't even ask for a password. Shouldn't those files be inaccessible to anyone but there owner? I have looked in "users and groups" but there is no "make my files private" option.

Help please,
Brad

---

### Post by wgrant on 2008-08-26
Open up the properties of your home directory, (Places->Home Folder, right click on the background, Properties), head over to the Permissions tab, and set the Other permissions to None.

---

### Post by koenn on 2008-08-27
> **fujitsu said:**
> Open up the properties of your home directory, (Places->Home Folder, right click on the background, Properties), head over to the Permissions tab, and set the Other permissions to None.

Is there a reason Ubuntu sets others:read on home directories ?

---

### Post by rogeriopvl on 2008-08-27
> **koenn said:**
> Is there a reason Ubuntu sets others:read on home directories ?

To be honest, I don't understand either. I think it's a bad choice to leave them open by default.

---

### Post by Oldsoldier2003 on 2008-08-27
> **koenn said:**
> Is there a reason Ubuntu sets others:read on home directories ?

> **rogeriopvl said:**
> To be honest, I don't understand either. I think it's a bad choice to leave them open by default.

agreed. 
I chmod home directories to 700

---

### Post by brian_p on 2008-08-27
> **koenn said:**
> Is there a reason Ubuntu sets others:read on home directories ?

Not all files in $HOME are readable by default. For example, mail files and some of the files in ~/.mozilla.

I expect most files are world readable in a spirit of openness and with the assumption users will want to share. Files you do not want to share can have their permissions set to 600.

Those who advocate complete privacy by default for their own files would presumably be happy with all system files being readable only by the root user.

---

### Post by rogeriopvl on 2008-08-28
> **brian_p said:**
> 
I expect most files are world readable in a spirit of openness and with the assumption users will want to share.

Wasn't that the biggest problem with Windows security?

"Assumption is the mother of all (...)" :rolleyes:

---

### Post by vanadium on 2008-08-28
> Wasn't that the biggest problem with Windows security?
No. The biggest problem with Windows security was that the files were readable *and writable* by the world.

Keeping the files readable by anyone is just a sensible default. If ever there are people peeking at your files that shouldn't, they can't do your files any harm anyway. If you have more sensitive information, then you are free to impose more strict restrictions.

---

### Post by rogeriopvl on 2008-08-28
I more or less agree, but I wasn't completely serious when I made that statement :)

But I think that they shouldn't be readable, if the user wishes to share, then he must set it that way, otherwise the best secure way is to have all locked to others by default.

---

