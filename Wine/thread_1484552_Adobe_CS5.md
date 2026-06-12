---
title: "Adobe CS5"
date: 2010-05-15
forum: Wine
---

### Post by Coruba67 on 2010-05-15
Anyone know how to get or where to go to look at getting Dreamweaver CS5 working on Ubuntu 10.04

Any idea why they are still just not creating a linux version of the CS5 suite, it would seem to me this is a growing platform full of the people that would utilise these tools...

---

### Post by alex.rayu on 2010-05-16
Its a growing platform full of people used to free software man! And they know it. If it grows like it is, it will be some time before they make a decision to port. I mean, Linux grows and Ubuntu is its messiah (for not and hopefully for long), but it is still a way to go in terms of percentage of users that would make it justified for Adobe to port to.

I have seen oh Wine HQ that CS4 is supposed to be working fine under Wine and even install now. I really hoped that this time they would make an app that would take to account Wine users with CS5 and it would actually be loading better in Wine. But they have evidently not only ignored that, but even added more things that break it under Wine. I wonder if there's a Big Brother behind this misfortune.

---

### Post by Szise on 2010-05-16
Will not run by default in Wine, i'm receiving an error, something about Adobe Manager.

---

### Post by ophthop on 2010-05-18
You can get that error message overwritten by typing

```
$wine Set-up.exe --mode=silent
```However the progress bar of the installer disapears, and of course, CS5 won't install, even if installer states it did. 

This is the result of the above operation, I hope it helps for a more skilled dude.
```
fixme:console:AttachConsole stub ffffffff
Starting installer...
UI mode : Silent.
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\Archivos de programa\\Archivos comunes\\Adobe\\AAMUpdaterInventory\\1.0\\AdobeApplicationManager-1.0\\ChannelDescription.xml" 1 4 (nil) (nil) (nil) (nil)
fixme:console:AttachConsole stub ffffffff
Installation successful.
Exiting Installer with Code: 0

```This is my distro, wine and Winetricks version.
```
Ubuntu: 10.04 64 bits Wine: 1.1.44 Winetricks: 0.0+20100424-0ubuntu1
```

---

### Post by alex.rayu on 2010-05-19
[http://docs.activestate.com/activepython/2.4/pywin32/win32file_MOVEFILE_WRITE_THROUGH.html](http://docs.activestate.com/activepython/2.4/pywin32/win32file_MOVEFILE_WRITE_THROUGH.html)

---

### Post by asdfoo on 2010-05-19
> **alex.rayu said:**
> [http://docs.activestate.com/activepython/2.4/pywin32/win32file_MOVEFILE_WRITE_THROUGH.html](http://docs.activestate.com/activepython/2.4/pywin32/win32file_MOVEFILE_WRITE_THROUGH.html)

what is the point of linking this?

---

### Post by firefly2005 on 2010-05-27
Hi Guys,

The installer on Dreamweaver CS5 doesn't work as of yet with Ubuntu however it can be run by copying files from a windows partition or virtual box..

Here is how i done it...(using Kubuntu 10.04 and Wine 1.2)

```
sudo apt-get autoremove wine
```

This will get rid of the Wine version that you already have.

```
rm -r -v .wine
```

Removes the Wine directory

```
sudo apt-get install wine
```

Installs a fresh version of wine :guitar: WEYHEY!
This may take a while

```
winecfg
```

This will now configure your wine installation. If you get an error message here its possible that you haven't deleted your old .wine folder

The next step is to install the Dreamweaver dependencies. For this i cheated and used winetricks

```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
```

This will download the winetricks script and change its privileges to be executable

```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

Above should install the requirements. Fingers Crossed

When this is all done, next is the tricky bit. I dual booted into windows xp sp3 and installed my Dreamweaver CS5 on there. I then pressed windows + R and ran regedit and exported the keys from localmachine software adobe saving them in my C:.

Just a quick note, my xp partition is 32bit and the dreamweaver installation is also 32 bit. In Ubuntu i am using 64bit  but i have the 32bit library installed . not sure if this will effect anything.

Back into lovely ubuntu =P~ i mounted my xp volume and copied (from the top of my head so dont follow links exactly):

c:/Program Files/Adobe/ into .wine/drive_c/program files/adobe

c:/Program Files/common files/adobe into .wine/drive_c/program files/common files/adobe

c:/documents and settings/mynamebutyourswillbedifferent/application data/adobe to wine/drive_c/users/mynamebutyourswillbedifferent/applications data/adobe

c:/windows/system32/odbc32.dll to .wine/drive_c/windows/system32/odbc32.dll

c:/windows/system32/odbcint.dll to .wine/drive_c/windows/system32/odbcint.dll

I then copied the adobe registry keys which i exported from regedit into my user area folder.

```
wine regedit adobe.reg
```

This should import your registry keys into wine. To be honest i think i encountered an error message here (i installed it last night at about 2am so i cant remember too much). i just googled it and found an override in wine to combat it.



next we need to override the odbc32 and odbcint in the wine cfg so run wine config again

```
winecfg
``` 

Click the libraries tab and from the drop down box select odbc32. then select built in then native. Do the same for odbcint (you may have to just type it into the drop down box and press enter)


Edit: Thanks to Vehuel for this step!

Another override is rpcrt4. Edit it to be Built in then native also!

Cheers again Vehuel


and finally we should be good to go!

cd to the dreamweaver exe, for me it was:
```
cd .wine/drive_c/Program\ Files/Adobe/Adobe\ Dreamweaver\ CS5/

```
and finally run

```
wine Dreamweaver.exe
```

Any problems just comment or PM :KS

Tom

---

### Post by Vehuel on 2010-05-28
firefly2005 tutorial worked nice for me.

About regedit error, run **winecfg**, goto **Library**, **select rpcrt4** then **Edit** and **select Builtin then Native**.

Try to run dreamweaver.

If you get a error like it

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library mfc90u.dll (which is needed by L"C:\\Arquivos de programas\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Arquivos de programas\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
err:module:import_dll Library mfc90u.dll (which is needed by L"C:\\Arquivos de programas\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Arquivos de programas\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe" failed, status c0000135
```

run **sh winetricks vcrun2005sp1** again.

Good luck and thank you very much firefly2005!

Sorry my poor english.

---

### Post by firefly2005 on 2010-05-29
No problem Vehuel and thanks for the tip! =D

Will hopefully amend the guide to include your step

Cheers again.

---

### Post by Zerocool Djx on 2010-05-29
This is good to know,.. I am working on installing Ableton right now,..  but this is next on my roster...

[Vehuel]("http://ubuntuforums.org/member.php?u=902009") can you help me out with Ableton?

---

### Post by nordstern on 2010-05-30
I've done everything you say but i get an error message like this:

> err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe" failed, status c0000005

I've tried a lot of odbc32.dll file but could not solve the problem.

system info:
Ubuntu 10.04 x64
Wine 1.2 rc2

---

### Post by Zerocool Djx on 2010-05-30
See another issue is,.. a new security feature for CS5 is that they have built into the program that even if you insert a serial, it has to connect to there server and verify it. And I highly doubt wine will be capable of such a thing because of the port issue. So even if you got it installed, serial entered, it's only a matter of time before it will shut itself off. I think it works on how many times you load it or something..

Anyway,... If need be,.. PM me and we will talk about it... ;)

---

### Post by firefly2005 on 2010-05-30
Well it hasn't happened so far. Maybe as the reg keys are imported from windows and it was activated on windows? I'm using the same technique that i used to install adobe cs4 and i never came across that problem. Without digging myself a massive hole, the naughty people who use illegal copies of adobe programs change the hosts file so that when adobe tries to phone home, it is looped back to the program and cannot connect. So if anything, unix is doing them a favour?

nordstern: did you copy the odbc32.dll from a windows xp partition? And have you set the overrides in winecfg? Is it a clean install of wine? :KS

---

### Post by thushy on 2010-06-01
> **firefly2005 said:**
> Hi Guys,

The installer on Dreamweaver CS5 doesn't work as of yet with Ubuntu however it can be run by copying files from a windows partition or virtual box..

Here is how i done it...(using Kubuntu 10.04 and Wine 1.2)

```
sudo apt-get autoremove wine
```

This will get rid of the Wine version that you already have.

```
rm -r -v .wine
```

Removes the Wine directory

```
sudo apt-get install wine
```

Installs a fresh version of wine :guitar: WEYHEY!
This may take a while

```
winecfg
```

This will now configure your wine installation. If you get an error message here its possible that you haven't deleted your old .wine folder

The next step is to install the Dreamweaver dependencies. For this i cheated and used winetricks

```
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks
```

This will download the winetricks script and change its privileges to be executable

```
sh winetricks gdiplus gecko dcom98 vcrun2008 ie6 msxml3 vcrun2005sp1
```

Above should install the requirements. Fingers Crossed

When this is all done, next is the tricky bit. I dual booted into windows xp sp3 and installed my Dreamweaver CS5 on there. I then pressed windows + R and ran regedit and exported the keys from localmachine software adobe saving them in my C:.

Just a quick note, my xp partition is 32bit and the dreamweaver installation is also 32 bit. In Ubuntu i am using 64bit  but i have the 32bit library installed . not sure if this will effect anything.

Back into lovely ubuntu =P~ i mounted my xp volume and copied (from the top of my head so dont follow links exactly):

c:/Program Files/Adobe/ into .wine/drive_c/program files/adobe

c:/Program Files/common files/adobe into .wine/drive_c/program files/common files/adobe

c:/documents and settings/mynamebutyourswillbedifferent/application data/adobe to wine/drive_c/users/mynamebutyourswillbedifferent/applications data/adobe

c:/windows/system32/odbc32.dll to .wine/drive_c/windows/system32/odbc32.dll

c:/windows/system32/odbcint.dll to .wine/drive_c/windows/system32/odbcint.dll

I then copied the adobe registry keys which i exported from regedit into my user area folder.

```
wine regedit adobe.reg
```

This should import your registry keys into wine. To be honest i think i encountered an error message here (i installed it last night at about 2am so i cant remember too much). i just googled it and found an override in wine to combat it.



next we need to override the odbc32 and odbcint in the wine cfg so run wine config again

```
winecfg
``` 

Click the libraries tab and from the drop down box select odbc32. then select built in then native. Do the same for odbcint (you may have to just type it into the drop down box and press enter)


Edit: Thanks to Vehuel for this step!

Another override is rpcrt4. Edit it to be Built in then native also!

Cheers again Vehuel


and finally we should be good to go!

cd to the dreamweaver exe, for me it was:
```
cd .wine/drive_c/Program\ Files/Adobe/Adobe\ Dreamweaver\ CS5/

```
and finally run

```
wine Dreamweaver.exe
```

Any problems just comment or PM :KS

Tom
hi firefly, 
i am new to linux or ubuntu.
i have install ubuntu  10.04 64 bit ver
i have master collection of adobe cs5
i tried to  install many times in few weeks and failed.
now i try your method  too, unfortunately i don't have windows installed.
i am getting error like below,
===============================================
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Trying to load PE image for unsupported architecture (AMD-64)
err:process:create_process starting 64-bit process L"Z:\\home\\thushyanthan\\Desktop\\adobe_cs5\\setup.exe" not supported on this environment
wine: Bad EXE format for Z:\home\thushyanthan\Desktop\adobe_cs5\setup.exe


===============================================

is there any way  to install , please help me put
thanks in advance

---

### Post by HomeSlixe on 2010-06-01
Hi there! 

I have installed all the posted winetricks dependencies including vcrun2005sp1 with all mentioned libraries loaded and set builtin,native and I am still getting these errors: 


fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

...  

err:module:import_dll Library mfc90u.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found


I am using Ubuntu 10.04
copied files from a fresh (and reluctant), install of Vista
wine 1.1.44

Any help would be GREATLY appreciated.
Thanks in advance!

---

### Post by AloneWolfCRO on 2010-06-09
I have this problem :((

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\NetIO.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\LogSession.dll") not found
err:module:import_dll Library LogSession.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\AlcidDLL.dll") not found
err:module:import_dll Library AlcidDLL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library dvaui.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\AdobeLinguistic.dll") not found
err:module:import_dll Library AdobeLinguistic.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\adbeape.dll") not found
err:module:import_dll Library adbeape.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_system.dll") not found
err:module:import_dll Library boost_system.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_filesystem.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_filesystem.dll") not found
err:module:import_dll Library boost_filesystem.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_system.dll") not found
err:module:import_dll Library boost_system.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library dvaui.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
err:module:import_dll Library mfc90u.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_signals.dll") not found
err:module:import_dll Library boost_signals.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_system.dll") not found
err:module:import_dll Library boost_system.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_threads.dll") not found
err:module:import_dll Library boost_threads.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvacore.dll") not found
err:module:import_dll Library dvacore.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaui.dll") not found
err:module:import_dll Library dvaui.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_system.dll") not found
err:module:import_dll Library boost_system.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_filesystem.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_filesystem.dll") not found
err:module:import_dll Library boost_filesystem.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_regex.dll") not found
err:module:import_dll Library boost_regex.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_date_time.dll") not found
err:module:import_dll Library boost_date_time.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\dvaadameve.dll") not found
err:module:import_dll Library dvaadameve.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
err:module:import_dll Library mfc90u.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\boost_signals.dll") not found
err:module:import_dll Library boost_signals.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS5\\Dreamweaver.exe" failed, status c0000135

```

How to fix that :(( I need this for school

---

### Post by mikemastercorp on 2010-11-21
Guys, thank you all for the help on installing DreamWeaver CS5. I must say that I am still in doubt whether to run it on virtual windows + DW or under native Ubuntu support as for a few things that can stop you working with DW directly. However everything has its own price and I will just mention some inconveniences I have for now.

Everything worked like a charm according to the instructions. However I did few steps further to improve my DW. For the tests I used a vbox virtual Windows XP in which I have installed DreamWeaver CS5 according to the instructions. After the end of the installation I did run an update, and got about 25MB of DreamWeaver program update as well as few libs/extensions. Only after that I did transferred all the files listed in the beginning of this posting.

!!!PLEASE READ!!! If you are intending to use a torrent version of DW CS5, I suggest you to create a folder `etc` in ./wine/drive_c/windows/system32/driver  and in which to place your hosts file. I am not sure whether this is ever used under linux, however under windows without it you will have problems. I do suggest though to used the officialy bought version as by doing such you support the developers and give hope to the world that one day we will all have a native Linux support.

What I have tried is to run a live preview on the DreamWeaver side with my local installation of LAMP (I will not go over it as there are billions of simple and clean instructions how to do that). So I must say that I did not expected it to work, but it did. The local preview is working, the file follower (I am not sure whether it is called like that) also works, so everything works fine. When I tried to do some style modifications and tried to save it, it shown up an error window stating I have no rights to write in that files. Well I cannot expect anything else since I am trying to write with my regular user under /var/www/... . So I thought what will be the simpliest sollution and i have so far two however I am not pretty sure which one exposes your server (if it is a directly connected to Internet). The first that worked like a charm for me was to simply ` sudo chmod -R 777 /var/www/ ` and not to care about the security as far as my server is configured to work in localhost ONLY! The other trick I think should work but I did not tried and consider riskier is to run the DreamWeaver under the Root rights, however you might mess up your whole system with just few clicks.

Now the fun starts here! I have started thinking how can I avoid installing DreamWeaver every single time when I want it to run on another Ubuntu machine, so I guess I have found a solution. If I simply backup my .wine folder I will have all the imported from windows registries, as well as all the updated Adobe/DreamWeaver files. So all I will have to do is to write down a simple bash script to remove any previous wine installations, install the latest, install the winetricks with all the libraries and create a shortcut. I am still testing it as I do have only one Ubuntu desktop at home, but I will have results in few days and will keep you informed.

So if we manage to keep it that way, one can even make a visual installer and call himself UBADOBE (Ubuntu Adobe) or something else.

Oh, I forgot to mention that I cannot say that I am a linux guru, so everybody that have some patience and ability to follow exact instructions, can have the same results as me. My pc is not one of the powerful machines (Asus P4P800-SE, CPU: Pentium IV-1.6Ghz,3GB DDR2 (if I am not wrong), 120GB HDD, Nvidia GeForce 5200-128 )

Will stay in touch and once again - thanks for the great howto. I am starting to digg on the UBADOBE :)

---

### Post by Another Quixote on 2010-12-11
Thank you firefly2005 and Vehuel, his post is brilliant!

After following your instructions I have managed to get almost all of the the CS5 Creative Suite running beautifully on Ubuntu 10.10.  However when trying to execute Illustrator.exe I get the following lines:

```

fixme:heap:HeapSetInformation 0x110000 0 0x32fd90 4
fixme:win:EnumDisplayDevicesW ((null),0,0x32f704,0x00000000), stub!
fixme:ntdll:NtSetInformationToken unimplemented class 24
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x142b94 0x142ba0 0x142c80 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x142c34 0x142c40 0x142d20 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x142c5c 0x142c68 0x142d48 (nil)

```

Any ideas?

Thanks. 

-Quixote

---

### Post by dino99 on 2010-12-11
Is there a bug report posted on winehq/bugzilla yet ?

Its nice to find such a thread but it should be better to improve next wine release.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

[http://bugs.winehq.org/buglist.cgi?bug_status=REOPENED&bug_status=NEW&bug_status=ASSIGNED&bug_status=UNCONFIRMED&field0-0-0=product&field0-0-1=component&field0-0-2=short_desc&field0-0-3=status_whiteboard&field0-0-4=longdesc&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&value0-0-0=photoshop&value0-0-1=photoshop&value0-0-2=photoshop&value0-0-3=photoshop&value0-0-4=photoshop&order=bug_id%20DESC&query_based_on=](http://bugs.winehq.org/buglist.cgi?bug_status=REOPENED&bug_status=NEW&bug_status=ASSIGNED&bug_status=UNCONFIRMED&field0-0-0=product&field0-0-1=component&field0-0-2=short_desc&field0-0-3=status_whiteboard&field0-0-4=longdesc&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&value0-0-0=photoshop&value0-0-1=photoshop&value0-0-2=photoshop&value0-0-3=photoshop&value0-0-4=photoshop&order=bug_id%20DESC&query_based_on=)

---

### Post by Gerontion on 2011-02-24
I've just done this and experienced the same problem with odbc32.dll but running winecfg and setting odbc32.dll to native (*not* built in, native) seems to have cured the problem.

---

### Post by gesti on 2011-04-18
Hello,

I had that problem that when I wanted to start PH (after I have finished firefly's tutorial) a little window poped up: Photoshop complaining about that I should reinstall **Adobe Application Manager** 'cos it's damaged... :confused:

So, I have downloaded this little program for it (from [www.adobe.com]("http://www.adobe.com")). Tried to install of course it install to some degree but then it died. The solution for this was to **copy the c:\Program Files\Common Files\Adobe for wine to /home/$USER/.wine/drive_c/Program Files/Common Files/ **

After this I have joined the happy bunnies on the farm :D

Hope this will help someone one day :P

s

---

### Post by gesti on 2011-04-18
lol, I'm not a happy bunny... :(

when I want to open my psd file, PS dies... grr

also it starts with a Program Error from wine, but after that I can still open a jpeg file and use the program, it just dies if I want to edit a psd file...

---

### Post by AlmightyMokona on 2012-03-03
Hey I don't know if anyone here is still looking for a Dreamweaver that works in Wine, but mine works with no problems atm...Give me feedback if I am allowed to post mediafire links here, alternately you can add me on Pidgin Messenger.

---

### Post by macgyvre on 2012-06-06
Thank you firefly2005 and Vehuel..
I succeed in installing the 30 day try-version of dreamweaver CS6 on ubuntu 12.04 in following this tutorial.
Just have to execute a command more :
```
winetricks gdiplus msxml3 msxml6 vcrun2005 vcrun2008 vcrun2010 
atmlib
```
and it works...
Somebody to try with the real version ?

sorry for my poor english...

---

