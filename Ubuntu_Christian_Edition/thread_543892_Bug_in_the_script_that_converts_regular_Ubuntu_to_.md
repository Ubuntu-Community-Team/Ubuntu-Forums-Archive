---
title: "Bug in the script that converts regular Ubuntu to CE"
date: 2007-09-05
forum: Ubuntu Christian Edition
---

### Post by mssever on 2007-09-05
My brother recently switched his install to Ubuntu CE via the script. He later noticed that his Firefox bookmarks were missing. While I was talking to him on the phone, we discovered that the conversion script had **deleted** his Firefox profile.

Here's the evidence:
[LIST=1]
[*]When Firefox creates a profile (in ~/.mozilla/firefox), it uses a name that is partially random. For example, mine is alwec2x5.default. My brother's is ubuntuce.default (or something like that). It would be quite a coincidence for Firefox to generate that string at random.
[*]There is no other profile in his ~/.mozilla/firefox.
[*]His bookmarks are gone and he had to re-download his Firefox theme[/LIST]This is clearly an extremely serious bug, as bookmarks, extensions, themes, and settings are all valuable and shouldn't be deleted. One of the following should be done:
[LIST]
[*]Properly parse the various files in the current profile and make the proper changes--making absolutely sure to delete nothing (preferred)
[*]Don't touch the Firefox profile at all (second best)
[*]Back up the current profile before creating the new one (last resort)[/LIST]=======
By the way, there's no bug tracker on the Ubuntu CE website. What's up with that?

---

### Post by mhancoc7 on 2007-09-06
> **mssever said:**
> My brother recently switched his install to Ubuntu CE via the script. He later noticed that his Firefox bookmarks were missing. While I was talking to him on the phone, we discovered that the conversion script had **deleted** his Firefox profile.

Here's the evidence:[LIST=1]
[*]When Firefox creates a profile (in ~/.mozilla/firefox), it uses a name that is partially random. For example, mine is alwec2x5.default. My brother's is ubuntuce.default (or something like that). It would be quite a coincidence for Firefox to generate that string at random.
[*]There is no other profile in his ~/.mozilla/firefox.
[*]His bookmarks are gone and he had to re-download his Firefox theme[/LIST]This is clearly an extremely serious bug, as bookmarks, extensions, themes, and settings are all valuable and shouldn't be deleted. One of the following should be done:[LIST]
[*]Properly parse the various files in the current profile and make the proper changes--making absolutely sure to delete nothing (preferred)
[*]Don't touch the Firefox profile at all (second best)
[*]Back up the current profile before creating the new one (last resort)[/LIST]=======
By the way, there's no bug tracker on the Ubuntu CE website. What's up with that?

Thanks for your comments.

The current convert_me script has a warning before the script runs giving information on the fact that the script will be making changes and should be used at "your own risk". It also gives info on the backups that are made. 

The Firefox profile is backed up with the current script so users can easily get their bookmarks and such back.

Sorry, that there is not currently any official bug tracking system for Ubuntu CE. Keep in mind that Ubuntu CE is basically a one man operation. I do get lots of help with various areas of development from our Team members. I do not mean to minimize their contributions. However, the "core" development is all done by me.

If you have any questions just let me know.

Thanks, Jereme

---

### Post by mssever on 2007-09-06
> **mhancoc7 said:**
> The current convert_me script has a warning before the script runs giving information on the fact that the script will be making changes and should be used at "your own risk". It also gives info on the backups that are made. 

The Firefox profile is backed up with the current script so users can easily get their bookmarks and such back.

OK, I downloaded the script so that I could see for myself what it was doing. After reading the script, I have a few comments.

First, the warning. All it says is that it will be making changes to the system. It does NOT say that it will delete a bunch of data. The use at your own risk and back up warning looks similar to the standard disclaimer that every open source program carries. That means that it's insufficient warning for such destructive action as deleting much data for Firefox, most Gnome programs' settings, GDesklets' settings, and /etc/apt/sources.list. I realize that there is a backup, but how is a non-expert user to merge those backups with the Ubuntu CE settings that they want to keep? In short, there needs to be a very prominent warning that the script will delete data.

Next, the disclaimer states that the script has only been tested on a fresh install of Ubuntu. But if someone was in the install process, why wouldn't they simply install CE via the live CD? Isn't the whole purpose of the conversion script to enable people who have valuable data and settings to use CE without losing them in a reinstall? (And, by the way, even if you keep a separate /home partition, you can still lose stuff in a reinstall.) So it's important that the script play nice with data. Otherwise, there really isn't any reason for it to exist.

Here are my suggestions:[LIST=1]
[*]There's no reason to replace the .gconf folder. It contains a lot of settings for a lot of different programs--many completely unrelated to CE. You can use gconftool to make the settings you need without affecting anything unrelated. And using gconftool is dead simple.
[*]Settings such as sources.list and GDM are again fairly easy to merge, though the job might be a little difficult to do in bash. (Ruby would be excellent for the task, and Python or even <shudder> Perl would do.) Actually, I just remembered that in Feisty sources.list has an include mechanism so that you can drop a file in and have it included without touching sources.list. This is what Medibuntu does.
[*]I don't remember much about GDesklets, as it's been a while since I've used it, but it shouldn't be too difficult to merge your settings with whatever might already be there.
[*]For Firefox, merging your bookmarks is absolutely trivial. It's just a simple HTML file. And installing your theme and extensions without touching whatever already exists shouldn't be too difficult, either. The package firefox-webdeveloper (in the Universe) should make an excellent model to study.[/LIST]

---

### Post by mhancoc7 on 2007-09-06
> **mssever said:**
> OK, I downloaded the script so that I could see for myself what it was doing. After reading the script, I have a few comments.

First, the warning. All it says is that it will be making changes to the system. It does NOT say that it will delete a bunch of data. The use at your own risk and back up warning looks similar to the standard disclaimer that every open source program carries. That means that it's insufficient warning for such destructive action as deleting much data for Firefox, most Gnome programs' settings, GDesklets' settings, and /etc/apt/sources.list. I realize that there is a backup, but how is a non-expert user to merge those backups with the Ubuntu CE settings that they want to keep? In short, there needs to be a very prominent warning that the script will delete data.

Next, the disclaimer states that the script has only been tested on a fresh install of Ubuntu. But if someone was in the install process, why wouldn't they simply install CE via the live CD? Isn't the whole purpose of the conversion script to enable people who have valuable data and settings to use CE without losing them in a reinstall? (And, by the way, even if you keep a separate /home partition, you can still lose stuff in a reinstall.) So it's important that the script play nice with data. Otherwise, there really isn't any reason for it to exist.

Here are my suggestions:[LIST=1]
[*]There's no reason to replace the .gconf folder. It contains a lot of settings for a lot of different programs--many completely unrelated to CE. You can use gconftool to make the settings you need without affecting anything unrelated. And using gconftool is dead simple.
[*]Settings such as sources.list and GDM are again fairly easy to merge, though the job might be a little difficult to do in bash. (Ruby would be excellent for the task, and Python or even <shudder> Perl would do.) Actually, I just remembered that in Feisty sources.list has an include mechanism so that you can drop a file in and have it included without touching sources.list. This is what Medibuntu does.
[*]I don't remember much about GDesklets, as it's been a while since I've used it, but it shouldn't be too difficult to merge your settings with whatever might already be there.
[*]For Firefox, merging your bookmarks is absolutely trivial. It's just a simple HTML file. And installing your theme and extensions without touching whatever already exists shouldn't be too difficult, either. The package firefox-webdeveloper (in the Universe) should make an excellent model to study.[/LIST]

Thank you for your comments and suggestions. Obviously the script has a long way to go. 

The reason for the statement regarding the fact that the script has only been tested on a fresh install of Ubuntu is because it is impossible for me to test it on the infinite number of various Ubuntu configurations. So I test on a fresh install.

As far as the "standard" disclaimer, I think it is important for users to take all disclaimers seriously. 

I would love for the script to be better. If you would like to help in its development please let me know. I would love to have you on the Team.

Thanks again, Jereme

---

