---
title: "Ubuntu CE 5.0 and e-sword-installer"
date: 2009-07-17
forum: Ubuntu Christian Edition
---

### Post by beta.tester on 2009-07-17
Hi Guys

Something amiss I am afraid. I run xiphos ok and everything else appears fine, but when I go to install e-sword-installerI get the following error and it aborts:

Esword_installer error: Note: command "env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.EXE" returned status 193. aborting

Any help appreciated to get this sorted :)

Runing 32 bit Ubuntu CE 5.0 on a Core 2 Duo home made system :)

---

### Post by mhancoc7 on 2009-07-17
> **beta.tester said:**
> Hi Guys

Something amiss I am afraid. I run xiphos ok and everything else appears fine, but when I go to install e-sword-installerI get the following error and it aborts:

Esword_installer error: Note: command "env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.EXE" returned status 193. aborting

Any help appreciated to get this sorted :)

Runing 32 bit Ubuntu CE 5.0 on a Core 2 Duo home made system :)


Did you install from disc or from repos? I had this issue when I installed from disc but not from repos.

Thanks, Jereme

---

### Post by david_kt on 2009-07-17
> **beta.tester said:**
> Hi Guys

Something amiss I am afraid. I run xiphos ok and everything else appears fine, but when I go to install e-sword-installerI get the following error and it aborts:

Esword_installer error: Note: command "env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.EXE" returned status 193. aborting

Any help appreciated to get this sorted :)

Runing 32 bit Ubuntu CE 5.0 on a Core 2 Duo home made system :)

That is due to internet connection problem, either your computer or e-Sword server. What you could do is:

1. Launch e-sword-installer and choose clear cache
2. Make sure your Internet connection is ok and then Re-launch e-sword installer and install e-sword.

DK

---

### Post by beta.tester on 2009-07-18
> **david_kt said:**
> That is due to internet connection problem, either your computer or e-Sword server. What you could do is:

1. Launch e-sword-installer and choose clear cache
2. Make sure your Internet connection is ok and then Re-launch e-sword installer and install e-sword.

DK

Hi Guys

Many thanks for the replies, I did as you suggested - cleared cache first (made sure it cam back to the esword menu and chose install esword, here is what happened:

Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/jb/.wine_Esword wine regedit /home/jb/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/jb/.wine_Esword' has been updated.
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/jb/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.exe
wine: could not load L"Z:\\home\\jb\\.wineeswordcache\\setup903.exe": Bad EXE format for 
Note: command 'env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.exe' returned status 193.  Aborting.



I am using xiphos but would like to fix this problem on my system.

---

### Post by david_kt on 2009-07-18
> **beta.tester said:**
> 
wine: could not load L"Z:\\home\\jb\\.wineeswordcache\\setup903.exe": Bad EXE format for 
Note: command 'env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.exe' returned status 193.  Aborting.

This is very sure a fail download again. What you could do is to download the exe file manually:

[http://www.e-sword.net/files/setup903.exe](http://www.e-sword.net/files/setup903.exe)

If it is successfully downloaded, copy it to /home/jb/.wineeswordcache/

```
cp setup903.exe /home/jb/.wineeswordcache/
```

After that launch e-sword-installer and choose esword, DO NOT clear cache this time.

DK

---

### Post by beta.tester on 2009-07-18
> **beta.tester said:**
> Hi Guys

Many thanks for the replies, I did as you suggested - cleared cache first (made sure it cam back to the esword menu and chose install esword, here is what happened:

Using builtin override for following DLLs: riched20 oleaut32
Executing env WINEPREFIX=/home/jb/.wine_Esword wine regedit /home/jb/.wine_Esword/drive_c/wineeswordtmp/override-dll.reg
Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/jb/.wine_Esword' has been updated.
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/jb/.wine_Esword' has been updated.
Executing env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.exe
wine: could not load L"Z:\\home\\jb\\.wineeswordcache\\setup903.exe": Bad EXE format for 
Note: command 'env WINEPREFIX=/home/jb/.wine_Esword wine /home/jb/.wineeswordcache/setup903.exe' returned status 193.  Aborting.



I am using xiphos but would like to fix this problem on my system.

HI again! fixed!! I noticed the above error message consistently pointed to an error of the setup903.exe in the /home/jb/.wineswordcache hidden directory. Clearing cache did *not* remove the setup903.exe file. 
I manually downloaded the setup903.exe file from Rick's site direct and put it manually into the /home/jb/wineswordcache directory, ran you esword installer and it worked!! Before downloading the file direct from Rick I could reproduce this problem at will. Could it be a bad copy of setup903.exe that has somehow got into the system?
Also how come clearing the cache left the file setup903.exe in the directory (all other files were gone after clearing cache).

Hope this helps.

---

### Post by beta.tester on 2009-07-18
> **david_kt said:**
> This is very sure a fail download again. What you could do is to download the exe file manually:

[http://www.e-sword.net/files/setup903.exe](http://www.e-sword.net/files/setup903.exe)

If it is successfully downloaded, copy it to /home/jb/.wineeswordcache/

```
cp setup903.exe /home/jb/.wineeswordcache/
```

After that launch e-sword-installer and choose esword, DO NOT clear cache this time.

DK

Hi David

Just seen your reply, thank you. Yes I actually worked that out for myself eventually :)

Many thanks again.

---

### Post by david_kt on 2009-07-18
> **beta.tester said:**
> Could it be a bad copy of setup903.exe that has somehow got into the system?
Also how come clearing the cache left the file setup903.exe in the directory (all other files were gone after clearing cache).

Hope this helps.

Yes, it is a fail download, and it would blocking subsequent download unless the cache is cleared.

When you choose:

```
clear_cache   To clear cache, compulsary for people upgrading..........
```

It delete the whole directory of /home/jb/.wineeswordcache/. But may be there are cases it could not remove the directory. I will add -f ("force") to make sure it would remove fail.

Thank you for your feedback, I will release the update tonight.

DK

---

### Post by beta.tester on 2009-07-18
> **david_kt said:**
> Yes, it is a fail download, and it would blocking subsequent download unless the cache is cleared.

When you choose:

```
clear_cache   To clear cache, compulsary for people upgrading..........
```

It delete the whole directory of /home/jb/.wineeswordcache/. But may be if there was cases it could not remove the directory. I will add -f ("force") to make sure it would remove fail.

Thank you for your feedback, I will release the update tonight.

DK

Many thanks for your help, appreciated.

---

