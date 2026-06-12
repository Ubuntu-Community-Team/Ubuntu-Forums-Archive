---
title: "Unable to get Wine working."
date: 2009-03-18
forum: Wine
---

### Post by schievelbein on 2009-03-18
I have been using Ubuntu for the last two years and never needed a windows product until lately.  I needed to install PAF Persoanl Ancestory File, but I never even got that far. After I downloaded the install program and double clicked on it, nothing happen.  

So I went to Applications->Programs->Accessories->Notepad, and clicked, NOTHING.  

So I tried WineCfg, NOTHING. 

Went to terminal and typed WineCFG, 
I got : "wine: invalid directory ~/.wine in WINEPREFIX: not an absolute path"  

I typed "Wine --Ver" and got wine 1.0.something, so I removed it COMPLETELY

I went to WineHQ and followed the directions to add the repository and install 1.1.17.

Tried the above and got same results. 

I googled and it told me to go to /home/myname/.wine and do some stuff.
Trouble is, I do not have a .wine directory.  Did my install not work correctly?  Did my configure not work correctly?  I have tried removing and reinstalling three times with same results.  As far as I know, my system and all drivers are up to date.

Any and all suggestions are appreciated.

---

### Post by illmatic on 2009-03-18
Have you tried to go to synaptic and delete the wine package completely and also do delete the windows directory by your own and just reinstall it ?

---

### Post by alex.rayu on 2009-03-18
no .wine directory? Type "wine" in console. If that does not create a .wine directory, then you'll have to reinstall wine. Wine is supposed to create a new .wine directory whenever it is missing. Are you using some custom wineprefix in your menus?

---

### Post by cogadh on 2009-03-18
The .wine directory is a hidden directory, so you will need to show hidden files (CTRL+H) to view it. When you do that, delete and re-run winecfg to create a new one.

---

### Post by schievelbein on 2009-03-18
Thanks for the suggestions... but no go...
I have already tried removed/completeremoved wine from synaptic and it removes it and 2 dependancies.  I reboot and do an "ls -la" in my home directory and no .wine, also tried it from file browser and it shows all of the other .* directories, but no .wine.  I reinstall Wine 1.1.17, same errors.  My permissions on my home directory are 744.  I have the latest Vnidia drivers and everything is up to date and current.  I even tried what one of the webpages suggested and did an "sudo apt-get -remove wine" and "sudo apt-get install wine", I still get the same results...

"winecfg" OR "wine notepad"  or any other exe
wine: invalid directory ~/.wine in WINEPREFIX: not an absolute path

Do I need to do these from a certain directory?
Do I need to do them as root?

I tried "sudo winecfg" and I get:
wine: '/home/michael' is not owned by you, refusing to create a configuration directory there

I read somewhere that you should never use sudo in conjunction with Wine?

Where is the WINEPREFIX stored?  Could that have been changed over the last year somehow?  Can I reset WINEPREFIX?  Like I said, I never even tried to use Wine before this week.  

Please help, I want to help my mom with her genealogy....

---

### Post by cogadh on 2009-03-18
Just for troubleshooting, try forcing the creation of a proper .wine directory:
```
wineprefixcreate --prefix ~/.wine
```
After doing that, try running winecfg or something else to see what happens.

EDIT - I don't know if this means anything, but I just noticed on my fresh Ubuntu install, the home directory permissions are 755, not 744.

---

### Post by schievelbein on 2009-03-20
I tried the "wineprefixcreate --prefix ~/.wine" and it still gives me the same error.  I checked my home directory and it is 755, my bad.  This is really weird, this is the first major problem I have had in two years of using Ubuntu.  I would hate to have to reinstall, but if all else fails, I guess I will. 

I would appreciate any other troubleshooting thoughts.  This might be something really simple that I am overlooking.

---

### Post by Nexusx6 on 2009-06-12
I realize this thread is a little bit old, but just in case it is still broken or someone else runs into this thread, I think I know how to fix your problem.

The issue is rising because wine doesn't know where to look when you give it commands like regedit or winecfg, and this is because of the way you are pointing to it. Wine does not understand ~/ as home like bash does, instead you have use the variable $HOME to point to home when dealing with wine. So here is a possible fix:

```
export WINEPREFIX="$HOME/.wine/"
```

You can also manually type in the absolute path, such as: */home/YOUR_USER_NAME/.wine*

This should fix wine's absolute path problem and from there you should be able to type in regedit or winecfg. Let me know what happens.

---

