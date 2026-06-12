---
title: "Can't Extract .exe file from .rar"
date: 2010-07-09
forum: Wine
---

### Post by phoriuh on 2010-07-09
I am using Ubuntu 10.04 LTS, and I have a .rar file that i can open and see everything that's in it, but I click extract and it loads just like i extracted it but the .exe file doesn't show up where I extracted it. 

I have the program unrar installed and i went into terminal to extract the files and it says this when I use this command line

**unrar -x X360_PROFILE_EDITOR_V2.rar**

> unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/joey/Desktop/X360_PROFILE_EDITOR_V2.rar

Extracting  X360 PROFILE EDITOR V2/DevComponents.DotNetBar2.dll       Failed    
Extracting  X360 PROFILE EDITOR V2/LeonSaunders.dll                           Failed    
Extracting  X360 PROFILE EDITOR V2/ProfileEditor.exe                            Failed    
3 FailedNow I also have the program p7zip and i tried to use that but it doesn't do anything. It says this when I type the command line [B]

7z x X360_PROFILE_EDITOR_V2.rar[/B]

> 7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.utf8,Utf16=on,HugeFiles=on,1 CPU)

Processing archive: X360_PROFILE_EDITOR_V2.rar

Extracting  X360 PROFILE EDITOR V2/DevComponents.DotNetBar2.dll
Extracting  X360 PROFILE EDITOR V2/LeonSaunders.dll
Extracting  X360 PROFILE EDITOR V2/ProfileEditor.exe
Extracting  X360 PROFILE EDITOR V2

Everything is Ok

Folders: 1
Files: 3
Size:       4204032
Compressed: 1248384And it doesn't extract the files anywhere. Is there any other way I can get these files out of the .rar file?

---

### Post by hikaricore on 2010-07-09
This nothing to do with wine..
I suspect you have a corrupt archive, download it again.

---

