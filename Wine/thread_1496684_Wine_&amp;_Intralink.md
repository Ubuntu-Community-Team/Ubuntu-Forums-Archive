---
title: "Wine &amp; Intralink"
date: 2010-05-29
forum: Wine
---

### Post by icelolli on 2010-05-29
Hi

My name i Lorenzo, I'm new on linux's world. I wold like to know is someone has tried to use Wine with Pro/Intralink (a PTC product). During installation...no problem. Lunching the program after installation... no results.
Need help.

Thanx

---

### Post by cogadh on 2010-05-29
You have not provided enough information. Please see the [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111") sticky for details on what we need from you so you can help us help you.

---

### Post by icelolli on 2010-05-31
[FONT=Verdana]Following, more informations:

[/FONT][FONT=Verdana]WINE Version: Wine 1.2-rc1

TERMINAL OUTPUT DURING INSTALLATION[/FONT]
```
icelolli@ascari:/media/PRO$ wine setup.exe
icelolli@ascari:/media/PRO$ fixme:win:LockWindowUpdate (0x30030), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:imm:ImmReleaseContext (0x100cc, 0x175050): stub
```[FONT=Verdana]TERMINAL OUTPUT AFTER LUNCHING PROGRAM[/FONT]
```
icelolli@ascari:~/.wine/drive_c/ptc/proiclient3.4/bin$ wine cmd
Versione di CMD 1.2-rc1


C:\ptc\proiclient3.4\bin>dir
Il volume nell'unit&#65533; C &#65533; 
Il numero seriale del volume &#65533; 0000-0000

Directory of C:\ptc\proiclient3.4\bin

31/05/2010      9.16  <DIR>         .
31/05/2010      8.51  <DIR>         ..
31/05/2010      8.51         1,546  distribute_object.bat
31/05/2010      8.50        40,960  i486_nt_ptc_setvars.exe
31/05/2010      8.51         1,094  ldbcompact.bat
31/05/2010      8.51         1,766  mark_replica.bat
31/05/2010      8.51         4,905  proilink3.4.bat
31/05/2010      8.51         1,852  ptcflush.bat
31/05/2010      8.51         1,283  ptchostid.bat
31/05/2010      8.51         2,374  ptcsetup.bat
31/05/2010      8.51         1,763  ptcstatus.bat
31/05/2010      8.51         1,541  replicate_folder.bat
31/05/2010      8.51         1,546  subscribe_package.bat
31/05/2010      8.51         1,518  sync_names.bat
31/05/2010      8.51         1,279  tnsping.bat
      13 files                   63,427 bytes
       2 directories     66,792,452,096 bytes free


C:\ptc\proiclient3.4\bin>proilink3.4.bat
fixme:exec:SHELL_execute flags ignored: 0x00000100
Non &#65533; stato possibile eseguire l'applicazione, o nessuna applicazione &#65533; associata con il file specificato.
ShellExecuteEx fallito: Invalid parameter

Path not found
```

Any idea? Attached you will find the bat file renamed in txt.

---

