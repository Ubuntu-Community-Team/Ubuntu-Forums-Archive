---
title: "Netatalk 64-bit"
date: 2007-09-28
forum: Server Platforms
---

### Post by spectre_25gt on 2007-09-28
Has anyone had any experience with Netatalk on 64-bit installs? I'm having trouble with my Mac hanging as soon as I choose a volume to mount. It's a clean install.

---

### Post by kidders on 2007-09-29
Hi there,

I've never had any problems with 32-bit or 64-bit netatalk builds. Do your system logs give away any hints?

---

### Post by lintoon on 2007-09-29
I think you need to confirm whether its a problem with the linux box or the mac.
Some mac troubleshooting questions to pursue to narrow it down:

Has your Mac (with its current os) ever connected to the Netatalk box, and if so what's changed?
Have you tried rebuilding the desktop?
Have you tried deleting Finder preferences (System Folder - Preferences)
What OS is on the Mac? 
Does your mac work with any other networked devices?
Can you upgrade opentransport on the mac?  (Google for issues with your verion first)
Are there any 3rd party extensions/fonts conflicting?  (Especially Suitcase MenuFonts extension - this has caused so much trouble over the years.  And also any Norton extensions)
Have you tried going to Control Panel - Extensions manager and setting it back to the OS defaults?
Remove Appleshare preferences from the System Folder - Preferences folder.

You could try reinstalling the Mac OS.  Don't worry you wont lose anything.

-Boot of your OS cd
-Go to System Folder and delete the files "System" and "Finder"
-Go to System Folder - Preferences and delete Finder preferences
-Install the OS

Nothing will have changed. Your data will be safe.  You will end up with a clean(ish) system folder.
To have an extra clean install, perfrom the above but instead of installing the OS after deleting the System and Finder files just rename the System Folder to Old System Folder.  After the reinstall of a nice clean system you can copy your extensions/fonts etc from your old System Folder into your new System Folder.

Good luck

---

### Post by kidders on 2007-09-29
> **lintoon said:**
> Has your Mac (with its current os) ever connected to the Netatalk box, and if so what's changed?
Have you tried rebuilding the desktop?
Have you tried deleting Finder preferences (System Folder - Preferences)
What OS is on the Mac? 
Does your mac work with any other networked devices?
Can you upgrade opentransport on the mac?  (Google for issues with your verion first)
Are there any 3rd party extensions/fonts conflicting?  (Especially Suitcase MenuFonts extension - this has caused so much trouble over the years.  And also any Norton extensions)
Have you tried going to Control Panel - Extensions manager and setting it back to the OS defaults?
Remove Appleshare preferences from the System Folder - Preferences folder.

You could try reinstalling the Mac OS. Yikes... most of these suggestions are a little extreme. Before blaming your mac, I would suggest tarballing and temporarily deleting resource forks & other mac-specific dotfiles. If restarting netatalk at that point fails to correct the problem, it might be worth considering client-side problems.

---

### Post by lintoon on 2007-09-30
Sorry I didn't mean to appear extreme.  I was just giving some pointers on the Mac end because I have worked on Macs for years and was giving some general troubleshooting pointers because I'm not an expert on the linux side.  None of the steps are extreme except the reinstall option.  Even then it's not too much of an issue.

The reinstall of the OS is not as extreme as it sounds.  I can't tell you how many times I have had to do it because of a corrupt System Folder (Extensions, fonts etc).  I assume you are using OS 8/9 so you will not get any permission problems with your files/apps on the Mac.

Just a note:
If you are using OSX I would only reinstall as a last resort and if you do have to reinstall make sure you select an "Archive and install" (Click "Options" at the point where you are asked which drive to install onto).  This will preserve your files and applications.  Before the reinstall though I would create a new user on the Mac then log in as that user and try to mount your share.  This will tell you whether its problem with the users profile or a system wide issue.

Please note I only suggest a reinstall as a LAST RESORT.  I am not recommending you just go ahead and do it.  Back up your data first though (Just in case).

Let us know which OS you are running.  And as kidders says, rule out netatalk side first.
Sorry for any confusion.

---

### Post by spectre_25gt on 2007-09-30
Firstly, as I should have mentioned before, this is a newish Macbook Pro running 10.4.10. A lot of what you mentioned seems like it's for OS 9 and below.

It has worked fine previously with my last server which was running on 6.06 (32-bit) with Netatalk custom compiled with SSL. The new server is 7.04 running under Xen on 6.06. I've got 2 other virtual servers running on the same box.

Nothing has changed on the Mac as far as I know. I've tried deleting preferences, but to no avail. I've got a couple more Macs in the house (all running Tiger), so I can try connecting with one of those.

---

### Post by lintoon on 2007-09-30
OK.  First things first I must apologise for diving in feet first and assuming you were running OS9 and then waffling on for ages.  

It does sound like it's a problem on the Netatalk side though (Eg It was working before the update) so I'll take a back seat for a while.  I'll keep an eye on the post and if there are any Tiger issues that pop up maybe I can help then.

Sorry for the confusion.

Good luck.

---

### Post by spectre_25gt on 2007-09-30
No worries. I really appreciate the input.

---

