---
title: "Win10 - &quot;File or directory is corrupted and unreadable&quot; Error"
date: 2023-09-03
forum: Windows
---

### Post by gipsyshadow on 2023-09-03
Hi all, I know is not so "elegant" to ask question about windows' issues but I'd like to get your opinion anyway.
I run a dual boot windows 10 & ubuntu on my PC. Rarely I work with windows but this error occurs only from last month and only in windows environment, not ubuntu's. I've got a certain folder in my "storage" NTFS partition (which is named E: in windows and /dev/sda6 in ubuntu) and, every time I try to access it from windows I get "File or directory is corrupted and unreadable" error.
I've tried to copy this folder from E: to C: (where windows is installed) and all works fine there therefore I think it's an only E: partition related issue.

Both the 2 test ran on my western digital HDD went good so I'm almost sure it's not a hardware issue, just a logical issue. I also run a test on E: drive to check its file system while windows was running on and this is the result (sorry if it's not in english!)
```

Chkdsk eseguito in modalità analisi su uno snapshot di volume.  

Controllo in corso del file system su E:
L'etichetta del volume è STORAGE.

Fase 1: analisi della struttura del file system di base in corso...
                                                                                       
  115600 record file elaborati.
Verifica file completata.
                                                                                       
  465 record di file di grandi dimensioni elaborati.                                                                                                              
  0 record file non validi elaborati.                                      
Fase 2: analisi del collegamento dei nomi file in corso...
    Rilevata struttura file di base danneggiata per "<0x5,0x3536>"
        ... in coda per la riparazione offline.
[...]

```
As you can see in step 2 ("fase 2") there's the first one of many sectors with errors but this test establishes only logical errors, doesn't it?

Afaik this errors must be fixed performing "chkdsk E: /f /x /r" in windows command line but data lost is possible. I'd like to avoid to backup all my data stored in E: so this is my idea based on this gparted scheme
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292685&stc=1[/IMG]
- I split "storage" (sda6) in 2 other partitions, let's name them E: and Z:, where my data relay on E: and Z: is empty;
- I perform chkdsk Z: and fix errors;
- I copy my data from E: to Z: in ubuntu environment;
- I perform chkdsk E: and fix errors;
- I format E: and copy my data back here;
- I format Z:;
- I merge E: and Z: ang get only E: as at the beginning.

All that said:
- Do you know why this error occurs only in windows and not in ubuntu?
- Is it possible to establish the cause of this error? I mean I'd want to know if I did something wrong so I'll avoid that in future.
- Will my "idea" work?

---

