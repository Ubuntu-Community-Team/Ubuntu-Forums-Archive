---
title: "Wine help"
date: 2009-02-16
forum: Wine
---

### Post by Shobuz99 on 2009-02-16
hello.
I did a wrong thing. 
I had two versions of Dreamweaver MX, ver 6.0 and ver 7.0 on my hardy heron 8.10 box. 
Version 7 was installed, from CD using Wine.
Version 6.0 was just copied from CD, to a folder, not installed.
Version 7.0 was working fine, with Wine. I was planning on deleting the folder and files of Version 6.0., sooooo...
I accidentally, deleted the Version 7 files by mistake.. by the time I realized I had deleted the wrong version, it was too late. 
I tried to reinstall version 7.0 using Wine, but it won't load after it's been installed. 
The install works fine, but no Dreamweaver when I try running it from Wine or from the Terminal box. Nothing happens..
I've also gained an 'untitled' window on my desktop, that won't delete or even move to Trash. I can't get rid of it.

At this point, I'm wondering if I can uninstall Dreamweaver 7.0, using Wine; then uninstall Wine, and somehow get rid of the 'untitled' window on my desktop...Except, I'm not sure how to know that Wine is completely uninstalled or how to remove the 'untitled' window. 
Of course I want to get the newest version of Wine and reinstall that and then try reinstalling Dreamweaver 7.0. 
Anyone have any suggestions?

Thank you for any advice you have.
Shobuz99

---

### Post by Dizzle7677 on 2009-02-16
How did you uninstall it? Did you just delete the directory or do a Uninstall Dreamweaver type thingy? Did you have 6 installed before 7 then upgraded it 7? 
  In any case .... you don't have to uninstall wine , just delete the /home/(username)/.wine directory , it'll be recreated when you install Dreamweaver again. Backup any important files you might have there beforehand. Dunno what the untitled window is about.:)

---

### Post by Shobuz99 on 2009-02-16
> **Dizzle7677 said:**
> How did you uninstall it? Did you just delete the directory or do a Uninstall Dreamweaver type thingy? Did you have 6 installed before 7 then upgraded it 7? 
  In any case .... you don't have to uninstall wine , just delete the /home/(username)/.wine directory , it'll be recreated when you install Dreamweaver again. Backup any important files you might have there beforehand. Dunno what the untitled window is about.:)

Dizzle7677
Ok. I'll explain it better.
I didn't uninstall Dreamweaver 7.0. I just moved it and all its folders to Trash. Then I emptied Trash. I thought it was Dreamweaver 6.0. I never installed Dreamweaver 6.0, just had copied the files from the CD,
with the intention of installing it from there...I later got a copy of DW 7.0 and installed that, successfully. I forgot about DW 6.0, because I got involved with trying to get Wine to run Dreamweaver 7.0.. I successfully did that....then I left Ubuntu for a few weeks and forgot what I had done...when I came back to Ubuntu, I decided to delete Dreamweaver 6.0...except I didn't pay attention to the version and the folders and I deleted 7.0 instead...see? It was wrong wrong wrong.

Alright, so I can 'delete' the /home/shobuz99/.wine folder and then,
put the CD in and install Dreamweaver 7.0 using Wine, and everything should work?

Ok. I'll do that and let you know.
Thanks very much for your help.
Shobuz99

---

### Post by Shobuz99 on 2009-02-17
> **Dizzle7677 said:**
> How did you uninstall it? Did you just delete the directory or do a Uninstall Dreamweaver type thingy? Did you have 6 installed before 7 then upgraded it 7? 
  In any case .... you don't have to uninstall wine , just delete the /home/(username)/.wine directory , it'll be recreated when you install Dreamweaver again. Backup any important files you might have there beforehand. Dunno what the untitled window is about.:)

Ok. Update. I got an error that prevents me from installing Dreamweaver MX using Wine... the error is:
**"An installation support file '%systemDrive%\Program files\Common files\InstallShield\engine\6\Intel 32\corecomp.ini' could not be installed (0x8000ffff)"**

This happened to me back in September of 2008..because I checked some old forums...BUT I can't remember how I was able to get around this error, and I can't find a post with the answer...
Any ideas?
Shobuz99

---

