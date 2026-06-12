---
title: "Can't change system language"
date: 2015-12-21
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-12-21
Hello,
first problem with 16.04. I really can't change the language settings. I've installed Italian from "Settings" -> "Language Support" -> "Install/Remove Language" but in the list above Italian is grey instead of black. The tip says "Drag languages to arrange them in order of preference" but nothing happens when I drag the language on the top of the list. 
Sometimes when I drag the language on the top another language goes on the top. In this moment I've dragged Italian on the top of the list and "English (Australia)" is now on the top....

I can't understand if it is a bug or if I am so stupid... :confused:

---

### Post by dino99 on 2015-12-21
From the Settings , select 'language support' and after selecting "italian", hit "apply system wide" ; then the "Region & Language" icon let you tweak your prefs

---

### Post by enricobe on 2015-12-21
> **dino99 said:**
> From the Settings , select 'language support' and after selecting "italian", hit "apply system wide" ; then the "Region & Language" icon let you tweak your prefs

Thank you for the reply. I clic on Italian (it's grey and not black) then Apply System Wide, but nothing happens. All the system is still in english. Regional Formats is correctly set on Italiano (Italia).
It seems that I can't click on any language in the list...

---

### Post by MikeMecanic on 2015-12-21
You must remove or delete English to get Italiano.  Then you re-enable English if you want,  Italian must be the first one the list, otherwise it won't work.  Welcome to the Xenial cycle Enricobe. **Changes take effect next time you log in.**  Mark the thread solved after if you succeed.

EDIT: 
Language Support / Supporto Lingue
Install/Remove Languages
Enable Italian Log out / Log in
Disable English: Log out / Log in
Enable Italiano System Wide : Log out / Log in / 
Computer will be in Italian with System Wide enable.

---

### Post by enricobe on 2015-12-22
> **MikeMecanic said:**
> You must remove or delete English to get Italiano.  Then you re-enable English if you want,  Italian must be the first one the list, otherwise it won't work.  Welcome to the Xenial cycle Enricobe. **Changes take effect next time you log in.**  Mark the thread solved after if you succeed.

EDIT: 
Language Support / Supporto Lingue
Install/Remove Languages
Enable Italian Log out / Log in
Disable English: Log out / Log in
Enable Italiano System Wide : Log out / Log in / 
Computer will be in Italian with System Wide enable.

Thank you very much for your help.
Unfortunately it doesn't work :( I've removed English and now I only see Italian in the language list, but when I click on the language it doesn't stay selected and the "apply system wide" doesn't work.

---

### Post by MikeMecanic on 2015-12-22
**There is something you do wrong**.  If Italiano is the first on the list and in black, it should work because all the others are in grey.  
Did you upgrade to Ubuntu 16.04 or you made a fresh install?  If you upgrade, was it in Italian before?  

You can go in Ubuntu Software Center to see if *Supporto Lingue* was correctly installed (screenshot).  
Just type language in All Software and see the result.  


You may want try this link if you don't succeed:
[https://help.ubuntu.com/stable/ubuntu-help/prefs-language-install.html](https://help.ubuntu.com/stable/ubuntu-help/prefs-language-install.html)

EDIT:  You must close the application before you log out.

---

### Post by enricobe on 2015-12-23
> **MikeMecanic said:**
> **There is something you do wrong**.  If Italiano is the first on the list and in black, it should work because all the others are in grey.  
Did you upgrade to Ubuntu 16.04 or you made a fresh install?  If you upgrade, was it in Italian before?  

You can go in Ubuntu Software Center to see if *Supporto Lingue* was correctly installed (screenshot).  
Just type language in All Software and see the result.  


You may want try this link if you don't succeed:
[https://help.ubuntu.com/stable/ubuntu-help/prefs-language-install.html](https://help.ubuntu.com/stable/ubuntu-help/prefs-language-install.html)

EDIT:  You must close the application before you log out.

Hello, look at this 
[https://youtu.be/XFf8soN02cY](https://youtu.be/XFf8soN02cY)
It doesn't seem to work at all...

I did a fresh install of 16.04

---

### Post by flocculant on 2015-12-23
I just added Italian - not selectable.

I just added French - not selectable.

I just added German - not selectable.

Logged out/re-booted - no changes.

I'd call bug and expect you to report it :)

---

### Post by enricobe on 2015-12-23
> **flocculant said:**
> I just added Italian - not selectable.

I just added French - not selectable.

I just added German - not selectable.

Logged out/re-booted - no changes.

I'd call bug and expect you to report it :)

Should I report it using the command "ubuntu-bug gnome-language-selector" ?

How should I title the bug? I ask for your help because I want to create a good bug report and you can help me with english ;)

---

### Post by MikeMecanic on 2015-12-24
The bug seems to be in Supporte Lingue.  Go in Ubuntu Software Center and remove Supporte Lingue to see if you can recover English and all languages in grey.  If you succeed, then redo post #4.

---

### Post by enricobe on 2015-12-25
> **MikeMecanic said:**
> The bug seems to be in Supporte Lingue.  Go in Ubuntu Software Center and remove Supporte Lingue to see if you can recover English and all languages in grey.  If you succeed, then redo post #4.

I marked them (language selector & language selector common) for reinstallation from Synaptic, then I have applied changes. It still doesn't work... :(

---

### Post by flocculant on 2015-12-25
[lpbug]1529225[/lpbug]

Reported it. 

Please add your details to that.

---

### Post by xc3RnbFO8P on 2015-12-25
Blah.....

---

### Post by enricobe on 2015-12-25
> **flocculant said:**
> [lpbug]1529225[/lpbug]

Reported it. 

Please add your details to that.

Thank you very much for reporting this bug. I've added the "affects me" vote and attached the short video about this bug. I hope this can help a bit more to understand the problem. 

> **Ringi said:**
> Maybe you can add it manual?
I will wait some days to do this. I just want to help the developers to understand the bug if I can provide useful informations. Thank you very much for your help! I'll try to do this in some days :)

---

### Post by dino99 on 2015-12-25
Does not get problem with a gnome-shell session; Are you guys only getting it with xfce ?

---

### Post by enricobe on 2015-12-25
> **dino99 said:**
> Does not get problem with a gnome-shell session; Are you guys only getting it with xfce ?

I'm using Ubuntu, so I have Unity as DE.

---

### Post by xc3RnbFO8P on 2015-12-25
You have to change it in USERS

---

### Post by MikeMecanic on 2015-12-25
I removed *Supporte Lingue* in Ubuntu Software Center and lost Language Support in Desktop Manager. Try it on the 21st just to see if it works and to help Enricobe. 

Even if I don't use a second language (English US default/Installer).* Supporte Lingue* (Italiano) controls my machine now even if it was removed from language support.  

I reinstall *Supporte Lingue* and recover Language Support back to It's previous state: English us (reboot each time).  If this can help?

---

### Post by enricobe on 2015-12-25
> **MikeMecanic said:**
> I removed *Supporte Lingue* in Ubuntu Software Center and lost Language Support in Desktop Manager. Try it on the 21st just to see if it works and to help Enricobe. 

Even if I don't use a second language (English US default/Installer).* Supporte Lingue* (Italiano) controls my machine now even if it was removed from language support.  

I reinstall *Supporte Lingue* and recover Language Support back to It's previous state: English us (reboot each time).  If this can help?
Thanks for spend some time to try to help me :)

I can't fully understand suggestions in your message, what do you suggest me do to?

---

### Post by MikeMecanic on 2015-12-25
You must go back to English, the one you choose in the installer,  Your video shows no other language and that's a real bug: Support language is altered and you must try to recover default setting.  The bug is in Supporte Lingue see comments in Ubuntu Software Center for Italiano, Portuguese and french.  Try to remove it.  You may have to re-install it if Language Support don't show up.  It's language support you need to get first to fix this issue

---

### Post by enricobe on 2015-12-25
I've solved the problem thank to this comment on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/1529225/comments/5](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/1529225/comments/5)

English MUST BE INSTALLED.
The first time I was really unable to change language so I've tried to remove English, but this should never be done! Without english the language selector doesn't seem to work at all.

---

### Post by QDR06VV9 on 2015-12-25
You might want to mark this as solved to help others with similar problem.
If you are satisfied with the result of course.:D
Regards

---

### Post by enricobe on 2015-12-25
> **runrickus said:**
> You might want to mark this as solved to help others with similar problem.
If you are satisfied with the result of course.:D
Regards

I'll mark SOLVED as soon as I finish to write this post :)

I'm satisfied, I just don't understand why language-selector allows to remove english if this behaviour breaks the program itself. :confused:

---

### Post by MikeMecanic on 2015-12-25
With grateful thanks to Gunnar Hjalmarsson.

---

### Post by enricobe on 2015-12-25
> **mikemecanic said:**
> with grateful thanks to gunnar hjalmarsson.

sure!

---

### Post by flocculant on 2015-12-25
seems a bit of a half-baked idea tbh - but never actually going to affect me ;)

(half-baked being code for ridiculous ... )

---

