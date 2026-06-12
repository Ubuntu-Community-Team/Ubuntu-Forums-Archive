---
title: "Unlocking 'Private Folders' in XP - Argh!"
date: 2008-05-08
forum: Windows
---

### Post by logos34 on 2008-05-08
I'm helping a friend undo 'Make Folders Private' option in XP Home after a reinstall, and can't seem to find a way to make the particular unlock method I'm using also apply to child folders contained in parent. 

In linux all I'd need to do would be run chmod with **-R** option to apply it recursively. How elegantly simple! But with Microsoft I'm having to jump through hoops to do the same thing, booting into 'Safe Made', checking this and that box and all manner of absurdities to alter the security/permissions profile. (It's apparent;y easier in XP Pro, but only slightly).

Jeez, what a pile of crap windoze really is!

---

### Post by smoker on 2008-05-08
have a look at this video and see if it will help:
[http://www.metacafe.com/watch/327864/how_to_unlock_files_of_another_administrative_user_account_xp/](http://www.metacafe.com/watch/327864/how_to_unlock_files_of_another_administrative_user_account_xp/)

---

### Post by CREEPING DEATH on 2008-05-08
With XP running, drop the XP Home CD in the drive.  Explore in until you find "NTBACKUP" then install that program.  Run it, I think it's under 'accessories'.  Select the folders you want to remove the permissions from and back them up to a .bkf.  Then 'restore' the .bkf after removing the permissions, it's under 'advanced'.

CD

---

### Post by Archmage on 2008-05-08
> **logos34 said:**
> I'm helping a friend undo 'Make Folders Private' option in XP Home after a reinstall, and can't seem to find a way to make the particular unlock method I'm using also apply to child folders contained in parent. 

For this you would need Windows XP **Profesional**. MS needs something to sell there more expensive one, aren't they?

I think there are 3rd-part-utilites out there to do the job, but you wont find something directly to do the job.

---

### Post by logos34 on 2008-05-08
> **smoker said:**
> have a look at this video and see if it will help:
[http://www.metacafe.com/watch/327864/how_to_unlock_files_of_another_administrative_user_account_xp/](http://www.metacafe.com/watch/327864/how_to_unlock_files_of_another_administrative_user_account_xp/)

The video (in German by the way) must be using XP Pro, because it shoes how to go to >Documents & Settings>Tools>Folder Options>View tab>uncheck 'Use simple File Sharing' -- that last option is not avail in XP Home, which is hard-coded to use simple file sharing at user level.  Hence the need start in Safe mode

---

### Post by logos34 on 2008-05-08
> **CREEPING DEATH said:**
> With XP running, drop the XP Home CD in the drive.  Explore in until you find "NTBACKUP" then install that program.  Run it, I think it's under 'accessories'.  Select the folders you want to remove the permissions from and back them up to a .bkf.  Then 'restore' the .bkf after removing the permissions, it's under 'advanced'.

CD

Sounds interesting--she's already got ntbackup installed.  We'll try it first thing in the morning.  Just hope it unlocks the child folders.

---

### Post by smoker on 2008-05-08
> **logos34 said:**
> The video (in German by the way) must be using XP Pro, because it shoes how to go to >Documents & Settings>Tools>Folder Options>View tab>uncheck 'Use simple File Sharing' -- that last option is not avail in XP Home, which is hard-coded to use simple file sharing at user level.  Hence the need start in Safe mode

sorry it didn't help (it viewed with english text, no volume, with me). the only other thing i can think you could try at the moment is maybe make a 'bartsPE' bootable version of windows, and see if there are available plugins that may give you the options you require.
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
[http://www.nu2.nu/pebuilder/plugins/](http://www.nu2.nu/pebuilder/plugins/)

best of luck

---

### Post by logos34 on 2008-05-08
> **smoker said:**
> sorry it didn't help (it viewed with english text, no volume, with me). the only other thing i can think you could try at the moment is maybe make a 'bartsPE' bootable version of windows, and see if there are available plugins that may give you the options you require.
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
[http://www.nu2.nu/pebuilder/plugins/](http://www.nu2.nu/pebuilder/plugins/)

best of luck

Thanks anyway.  What I meant was the video is in english but the version of XP in it is in German...the quality is poor too. At any rate I can't disable simple file sharing because the option isn't there on xphome.

I check out bartspe.

---

### Post by logos34 on 2008-05-08
ok, I managed to fix it (I *think*).  Not quite the way the howtos explained, though.

Basically I did this:

Restart>F8>Safe Mode>click 'Administrator' login icon>Start>My Computer>My Documents>right-click on locked folder>Properties>Security tab>Advanced button>Owner tab>select 'Administrators {XXXX-XXXXX\Administrators}'>check box 'Replace owner on subcontainers and objects'>Apply>OK

Thanks everyone for the suggestions.

---

