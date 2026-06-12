---
title: "Error while installing WoW with Wine 1.1.17"
date: 2009-03-15
forum: Wine
---

### Post by mzpunk on 2009-03-15
Hi

I've been trying to install WoW for the past few days and been searching for threads with people that have the same problem as me, but cant seem to find anyone. I've downloaded all of the files smoothly but when i try to install it at about 60% i get an error screen saying

" The installer was unable to read the file "C:\Program Files\Common Files\Blizzard Entertainment\World of Warcraft Installer\Installer Tome 4.mpq". This error may be caused by problems with the media or drive at C:\--for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the installer. (The data being read was "MPQs-2\BurningCrusade common\unconditional\Data#expansion.MPQ\World\Maps\Expansion01\Expansion01_24_39.adt", and the error code was 8.) If this problem persists, please contact Blizzard Technical Support. (Converter::Load) "

At some point i got a diffrent error message with basically the same message but earlier in the installation, dunno if that helps.

Been trying to change the directory to install it and see if that would help, have no clue what the problem is, if anyone been thru the same please help me
cheers

---

### Post by Kaffekop on 2009-10-27
I'll have to bump this one - i got the exact same problem!

---

### Post by unidentified on 2009-10-27
> **mzpunk said:**
> Hi

I've been trying to install WoW for the past few days and been searching for threads with people that have the same problem as me, but cant seem to find anyone. I've downloaded all of the files smoothly but when i try to install it at about 60% i get an error screen saying

" The installer was unable to read the file "C:\Program Files\Common Files\Blizzard Entertainment\World of Warcraft Installer\Installer Tome 4.mpq". This error may be caused by problems with the media or drive at C:\--for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the installer. (The data being read was "MPQs-2\BurningCrusade common\unconditional\Data#expansion.MPQ\World\Maps\Expansion01\Expansion01_24_39.adt", and the error code was 8.) If this problem persists, please contact Blizzard Technical Support. (Converter::Load) "

At some point i got a diffrent error message with basically the same message but earlier in the installation, dunno if that helps.

Been trying to change the directory to install it and see if that would help, have no clue what the problem is, if anyone been thru the same please help me
cheers
Perhaps, the installer tries to open that file to check if that is working or corrupted, I might be wrong but try to install media codecs on Wine before installing WOW.
Reply me with updates.

---

### Post by gjoellee on 2009-10-27
I found a post on the same issue for you. It says that this sometimes happens with CD's. Try downloading WoW instead.

---

### Post by Kaffekop on 2009-10-27
> **gjoellee said:**
> I found a post on the same issue for you. It says that this sometimes happens with CD's. Try downloading WoW instead.

I've downloaded the wow installer, but it won't work with wine.
It tries to open a destination in windows folders (somewhere in system32).

---

