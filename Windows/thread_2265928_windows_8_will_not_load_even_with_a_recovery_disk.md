---
title: "windows 8 will not load even with a recovery disk"
date: 2015-02-18
forum: Windows
---

### Post by david350 on 2015-02-18
Hello all,Please note than I am not that IT savvy.
Have a Dell Inspiron 17 core i3 with window,s 8 which was upgraded over the internet to 8.1. The operating system will not 'fire up'. I have a windows 8.  32 & 64 BIT recovery/reinstall disc. This does not see. To get me anywhere after f12 and changing to legacy and cd/DVD/cd-rw drive. Nothing else gets me anywhere so I run through the command prompt as recommended on some sites. From x:\sources.  Bootrec/fixmbr and fixboot both worked successfully. The scanos results in one windows installation in c:/windows with the operation completed successfully.


With x:/sources> boot rev/rebuildbcd I get one windows installation. However when I hit 'A' return I get "the requested system device cannot be found"


I then try


Diskport    X:\sources>diskpart
Sel disk 0 DISKPART>sel disk 0
List vol. DISKPART>list vol.   I get


Volume ltr label.                           Fs.      Type.     Size
0.           D win8aio.                   Udr.     Dvdrom.   3978mb
1.           C os.                            Ntfs.    Partition.   916mb
2.                                                Fat32.  Ditto.         500mb
3.                Winretools               Ntfs.      Ditto.        500mb
4.                                                 Ntfs.      Ditto.        450mb
5.                 Pbr image.             Ntfs.        Ditto.         13gb
6.                  Dials.                    Fat32.      Ditto.          40mb


So I select.          DISKPART> sel vol 2


Return says. Volume 2 is the selected volume.......then


DISKPART>assign letter=z:
Diskpart successfully assigned.................
Then hit exit and it returns to


X:/sources>. Cd /d z:\efi\microsoft\boot


However I get the message.     The system cannot find the path specified.




Can someone please advise ?


Many thanks,

David

---

### Post by oldfred on 2015-02-18
Moved to Windows sub-forum. Not an Ubuntu question.
But only use 64 bit versions for repairs or you may corrupt system.
Only a few small systems used 32 bit UEFI.

You may do better in a Windows forum.
       Windows 8 has both a Refresh and a Reset option. To find out the details of both, and to decide which best to use, you should check in with the Windows 8 forum:
 [http://www.eightforums.com](http://www.eightforums.com). 
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

