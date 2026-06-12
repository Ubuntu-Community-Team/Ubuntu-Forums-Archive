---
title: "wine problem &quot;Microsoft.VC80.CRT.manifest&quot;"
date: 2009-12-01
forum: Wine
---

### Post by saadlulu on 2009-12-01
hey guys 
i have a game installed through wine thats called "MISE" 
i checked in wine and they say that they got it working under ubunutu/wine with no problems.
so when i tried playing it i get the following :

boza@ubuntu:~$ wine '/host/MISE/MISE.exe' 
err: process:__wine_kernel_init boot event wait timed out
fixme:actctx: parse _assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50608.0
fixme:actctx: parse_manifest_buffer failed to parse manifest L"Z:\\host\\MISE\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library X3DAudio1_6.dll (which is needed by L"Z:\\host\\MISE\\MISE.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\host\\MISE\\MISE.exe" failed, status c0000135

i used winetrick and am using wine 1.1.33
thanks to u all !

---

### Post by saadlulu on 2009-12-01
what the hell is a Microsoft VC80.CRT.manifest thing ?

any help ?

---

### Post by beastrace91 on 2009-12-01
Have you tried installing the "vcrun2005" package from Winetricks? It contains the file that the error message is referring to and might help resolve your issue.

Regards,
~Jeff

---

### Post by saadlulu on 2009-12-01
actually i did 
i typed 
sh winetricks vcrun2005

after its done " with some errors " and i tried to start the game again 
it still gives me the very same error 

what could cause this ?

---

### Post by saadlulu on 2009-12-01
and here is what i get when installing vcrun2005

boza@ubuntu:~$ sh winetricks vcrun2005
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
err:process:__wine_kernel_init boot event wait timed out
Executing wine /home/boza/.winetrickscache/vcrun2005-ms09-035/vcredist_x86.exe
err:process:__wine_kernel_init boot event wait timed out
Install of vcrun2005 done
winetricks done.

and a pop up comes out saying 
windows 95 or NT is required to install

---

### Post by beastrace91 on 2009-12-01
Can you provide a link to the game you are trying to run? Might give me a better idea of helping get it to work - how ever it might just be a limitation in Wine that prevents it from running.

~Jeff

---

### Post by saadlulu on 2009-12-02
thanks for helping so far Mr.Jeff :)

heres the link 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17211&iTestingId=46787](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17211&iTestingId=46787)

---

### Post by beastrace91 on 2009-12-02
Did you grab all the winetricks packages they suggest on that appdb page?

```
sh winetricks vcrun6 allfonts allcodecs dotnet11 dotnet20 directx9 comctl32 comctl32.ocx fontfix mfc40 mfc42 msls31 ole2 pdh urlmon wininet native_mdac
```

Regards,
~Jeff

---

### Post by saadlulu on 2009-12-02
yes i did. but ignore the fact that some of them had an 1 or more errors during the installation .

---

### Post by saadlulu on 2009-12-02
just tried the samething i did on my friends computer and it worked fine ..
so i think theres something wrong with just my laptop

---

### Post by beastrace91 on 2009-12-02
> **saadlulu said:**
> yes i did. but ignore the fact that some of them had an 1 or more errors during the installation .

What errors did it throw? Some of the winetricks components failing to install properly could very well be the source of the issues you are having on your own computer.

Also what video card/driver version are you using?

Regards,
~Jeff

---

### Post by starstalker on 2009-12-16
hi 
when I used 

sh winetricks vcrun6 allfonts allcodecs dotnet11 dotnet20 directx9 comctl32 comctl32.ocx fontfix mfc40 mfc42 msls31 ole2 pdh urlmon wininet native_mdac

I got this:

sha1sum mismatch!  Rename /home/sary/.winetrickscache/./codinstl.exe and try again.

is there a way to fix this

---

### Post by Denieru on 2009-12-16
I've got the same problem with Runes of Magic ( [http://ubuntuforums.org/showthread.php?t=1354806](http://ubuntuforums.org/showthread.php?t=1354806) ), I get this message:


```
 fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\client.exe" failed, status c0000142

```

Running karmic 64bit Wine 1.1.33

---

### Post by saadlulu on 2009-12-16
Mr.Denieru 
just download the vcrun2005 and it should fix ur problem 

to do so go to the terminal and write 
sh winetricks vcrun2005

give feed back please :)

---

### Post by Denieru on 2009-12-16
> **saadlulu said:**
> Mr.Denieru 
just download the vcrun2005 and it should fix ur problem 

to do so go to the terminal and write 
sh winetricks vcrun2005

give feed back please :)
Done that a long time ago, still won't work.:(

---

### Post by saadlulu on 2009-12-17
i fixed my problem with uninstalling ubunut " i installed it using wubi" and installed a fresh one the standard way.
it fixed the problem

---

### Post by saadlulu on 2009-12-17
> **starstalker said:**
> hi 
when I used 

sh winetricks vcrun6 allfonts allcodecs dotnet11 dotnet20 directx9 comctl32 comctl32.ocx fontfix mfc40 mfc42 msls31 ole2 pdh urlmon wininet native_mdac

I got this:

sha1sum mismatch!  Rename /home/sary/.winetrickscache/./codinstl.exe and try again.

is there a way to fix this

yes there is a way to fix this, all u have to do is go to your home and show hidden files " ctrl + H " and then delete the folder thats called .winetrickscache .

---

### Post by L1ttl3J1m on 2010-08-01
The root of the problem is in a "FixMe" message from just before the runtime error. Look for

[INDENT]fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762) <-**this is the version we need** 
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50608.0[/INDENT]


To fix it, find the VC80.CRT (8.0.50727.762) files in a /Windows/WinSxS folder

[INDENT][LIST]
[*]- copy the folder x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6b128700 from /Windows/WinSxS/
[*]- copy the matching .cat and .manifest files to the /windows/winsxs/manifests directory
[/LIST][/INDENT]

---

