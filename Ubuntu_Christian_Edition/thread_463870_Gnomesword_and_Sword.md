---
title: "Gnomesword and Sword"
date: 2007-06-04
forum: Ubuntu Christian Edition
---

### Post by stureharry on 2007-06-04
I am have newly installed Ub Chr Ed. I have worked with Ubuntu 6.06 earlier. Two questions: Gnomesword as installed from the beginning is not possible to use, either in 6.06 or inChrEdition. There is a wrongmessage, My second question ist: e-sword, in the iso-file as the rest of Ubuntu Christian Edition, tries to be installed in C:\program files , for me that is Windows, not Linux. I am a little bit confused. What to do? Coming from Sweden, English is not my mothertongue,

---

### Post by tak1150 on 2007-06-04
> **stureharry said:**
> I am have newly installed Ub Chr Ed. I have worked with Ubuntu 6.06 earlier. Two questions: Gnomesword as installed from the beginning is not possible to use, either in 6.06 or inChrEdition. There is a wrongmessage,

I am not sure what you mean by "wrongmessage" ...

> My second question ist: e-sword, in the iso-file as the rest of Ubuntu Christian Edition, tries to be installed in C:\program files , for me that is Windows, not Linux. I am a little bit confused. What to do? 


It tries to install in a folder that sounds like windows because e-Sword that comes with Ubuntu CE is a windows program and it is installed with a windows emulator (i guess technically it's not an emulator) that lets you install and run windows programs. The e-Sword installer that comes with Ubuntu CE should work perfectly. 

I've tried Linux native Bible softwares, but nothing really beats e-Sword (even better than commercial Windows softwares that are expensive).

---

### Post by shane2peru on 2007-06-04
> **stureharry said:**
> I am have newly installed Ub Chr Ed. I have worked with Ubuntu 6.06 earlier. Two questions: Gnomesword as installed from the beginning is not possible to use, either in 6.06 or inChrEdition. There is a wrongmessage, My second question ist: e-sword, in the iso-file as the rest of Ubuntu Christian Edition, tries to be installed in C:\program files , for me that is Windows, not Linux. I am a little bit confused. What to do? Coming from Sweden, English is not my mothertongue,
The wrong message you are getting is from a missing library in Ubuntu 6.06.  There is a way around this see this post to find the missing library:
[http://ubuntuforums.org/showthread.php?t=285641&highlight=libsword](http://ubuntuforums.org/showthread.php?t=285641&highlight=libsword)

E-Sword is much better than Gnomesword.  I would recommend that.

Shane

---

### Post by stureharry on 2007-06-04
But, after downloading Esword, where on earth do I start the program? Silly question but I have tried Accessories:E-sword, and E-sword module, but nothing happens.

---

### Post by shane2peru on 2007-06-04
> **stureharry said:**
> But, after downloading Esword, where on earth do I start the program? Silly question but I have tried Accessories:E-sword, and E-sword module, but nothing happens.

Did you install it with the file that comes with Ubuntu CE?  Or did you install it on your own?  If you installed it with the Ubuntu CE installer it should be located at:  **Accessories -> E-Sword**  If not you may need to open a terminal and type:```
wine ~/.wine/drive_c/Program\ Files/e-Sword/e-sword.exe 
```  If you just recently installed it you may need to downgrade your wine installation see this post here:  [http://ubuntuforums.org/showthread.php?t=462097](http://ubuntuforums.org/showthread.php?t=462097)
Specifically post #6 Jeremy outlined a very nice way of fixing this issue.

Shane

---

### Post by mhancoc7 on 2007-06-04
> **stureharry said:**
> But, after downloading Esword, where on earth do I start the program? Silly question but I have tried Accessories:E-sword, and E-sword module, but nothing happens.

The reason that the apps are not starting is probably because you did not install using English. If that is the case you will simply have to change the menu path for the apps. Below is the default (English) paths. Once you figure out the correct path you need to edit the following two files with the correct path.

/usr/local/apps/esword4linux/runesword
/usr/local/apps/esword4linux/runeswordmm

eSword default path:
"/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword/e-Sword.exe"

eSword Module Manage default pathr:
"/usr/local/apps/esword4linux/esword4linux_module_manager/esword4linux_module_manager"

I am working to give the installer better language support, but for now this is the workaround.


Jereme

---

### Post by stureharry on 2007-06-05
I used Ubuntu CE. I will make another installation from the beginning. At the same time I have problems with the printerinstall. Would it be easier to update my old Ubuntu 6.06?

---

### Post by stureharry on 2007-06-05
Infact, I just succeeded with the printer, and I have put away the update of wine, and had put the older version back, so where do I find the esword for Ubuntu?

---

### Post by stureharry on 2007-06-05
Actually I have got a swedish Ubuntu Chr Ed. Where do I try to write another path? I am too new on Linux, working only 2 years with it. Interesting, but a little bit more thinking than using Windows XP. So, I will look in my filsystem to see where the program has been placed, and then doing what...?

From summertime in the nordic countries

---

### Post by stureharry on 2007-06-05
Well, some repetitio: I downloaded setup785.exe. In terminal I run wine setup785.exe. The result of that I cannot see. The last in the answer about reference to an exe-file I have some problem to catch.

---

### Post by stureharry on 2007-06-05
I made the installation once more and got this message:
hilding@hilding-desktop:~/Desktop$ sudo wine setup785.exe
Password:
fixme:advapi:LookupAccountNameW (null) L"root" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"root" 0x16c788 0x34f808 0x16b348 0x34f804 0x34f810 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub UnpublishFeatures -> 48 ignored L"FeatureComponents" table values
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 11 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 5 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 48 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 9 ignored L"CreateFolder" table values
fixme:ole:DllRegisterServer stub

---

### Post by santy_kushwaha on 2007-06-05
i have worked on the chridtian edition but i not sure what is ur question so i will ask to write the question clearly

---

### Post by shane2peru on 2007-06-05
> **stureharry said:**
> Actually I have got a swedish Ubuntu Chr Ed. Where do I try to write another path? I am too new on Linux, working only 2 years with it. Interesting, but a little bit more thinking than using Windows XP. So, I will look in my filsystem to see where the program has been placed, and then doing what...?

From summertime in the nordic countries

If you system is in sweedish, I'm not sure that the commands would be the same.  If they are you can try this:
```

slocate runesword

```
in the terminal, and that should tell you the location of your e-Sword directory.

Shane

---

