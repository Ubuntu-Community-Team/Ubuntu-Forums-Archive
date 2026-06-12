---
title: "Some problems with Unreal Gold"
date: 2009-11-21
forum: Wine
---

### Post by blueshiftoverwatch on 2009-11-21
I'm trying to play Unreal Gold (not Unreal Tournament) in WINE 1.1.31 and am having problems installing these two patches that the WineHQ [page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3733&iTestingId=2826") recommends: [UnrealPatch226final]("http://www.oldunreal.com/patch/official/UnrealPatch226Final.exe") and [OMP-226]("http://oldunreal.com/patch/OMP-226-V0.2.zip").

I have the game installed to a separate partition, a virtual D:\ drive which is located in on a separate mounted partition. Instead of the default virtual C:\ drive that wine puts in the /.wine folder on in your /home directory.

I tried to install the UnrealPatch226Final patch. But I only get to the part where it asks me where my game CD is located. I changed the location where the game is installed from "C:\Unreal" to "D:\UnrealGold", so far so good. Then it tells me that it must get some files from the game CD. Which is in my virtual E:\ drive. But when I click "next" it says "*The expected version of Unreal file System\Engine.u was not found on the CD-ROM drive. Please verify that the proper CD is in the drive*".

I have no idea at all how to install the OMP-226 patch.

The UnrealPatch226final patch is something I'd like to have. But the OMP-226 patch is something that's necessary for me to play the game due to the following major gameplay bug.
> This older game may run too fast on your computer, and therefore, the action is sped up. If you are using the enhanced OpenGL renderer, you can have it limit t*he frame rate. Set "FrameRateLimit" to "60", and if neccessary set "SwapInterval" to "1" in 'System/Unreal.ini', under the "[OpenGLDrv.OpenGLRenderDevice]" section.

---

### Post by Butthead on 2009-11-22
Hmm, can't you just copy the patch you're trying to install into the "Public" folder (and just run it from there?) with the Unreal Gold CD in your physical CD drive? :confused: 

I don't really understand you drive re-naming conventions.

---

### Post by blueshiftoverwatch on 2009-11-22
> **Butthead said:**
> Hmm, can't you just copy the patch you're trying to install into the "Public" folder (and just run it from there?) with the Unreal Gold CD in your physical CD drive? :confused:

I don't really understand you drive re-naming conventions.
Why would it make any difference where my patch files were located?

It found where I have Unreal Gold installed (D:\WINE\UnrealGold). It just won't recognize a necessary file on the CD I have in my drive. I tried both the E:\ drive (cdrom) and H:\ (cdrom0) when it asked me for a path to my cdrom drive. But neither of them worked. I don't know why Linux recognizes my 1 cdrom drive as two drives. But that's another topic.

From reading the instructions on the OMP-226-VO.2 patch I think I need to have the UnrealPatch226Final installed. The version I have installed is 226b.

---

### Post by Butthead on 2009-11-23
Heh, now that I think of it, it doesn't.  Somehow I read you were trying to run the installer and actual game files from the same CD drive. :oops:

I think your problem is the "\WINE" directory.  My Wine install (if I remember correctly?) didn't show an extra \WINE directory.  These installers can be funny in that way, and I'm generally an idiot when it comes to tweaking Linux to get things to run.  Best to keep things as close to stock as possible for success.  Not to say that the way you have things set up that you won't eventually get it to work. :-k

---

### Post by blueshiftoverwatch on 2009-11-23
> **Butthead said:**
> These installers can be funny in that way, and I'm generally an idiot when it comes to tweaking Linux to get things to run.  Best to keep things as close to stock as possible for success.  Not to say that the way you have things set up that you won't eventually get it to work. :-k
I've tried and it doesn't matter where the game is installed to. Besides telling me that I don't have the right version of a file wasn't found on the CD. The patch installation also tried to by default install to a folder called "Unreal" when the default name of the folder the game installs to is "Unreal Gold". I just change Unreal to Unreal Gold, but I wonder if that has something to do with it. Maybe the patch assumes I'm trying to update a previous version of the game or something.

---

### Post by Butthead on 2009-11-24
How hard would it be to change your "Unreal Gold" directory to one just called "Unreal" (like the patch file is looking for?). :confused: 

I imagine if that doesn't work, it would be no big deal to change it back to "Unreal Gold" if you prefer it to be that way. :-k

---

### Post by xnerdx on 2009-11-24
It seems you might be confusing where the CD is mounted with a direct path to the patch files. I suggest you extract the patches somewhere on your physical drive (For example /home/linus/Desktop/Patch_Files) this would likely work if it comes to not being able to find some patch files and make sure that the directory is exact, it is CASE-SENSITIVE.

---

### Post by blueshiftoverwatch on 2009-11-24
> **Butthead said:**
> How hard would it be to change your "Unreal Gold" directory to one just called "Unreal" (like the patch file is looking for?). :confused: 

I imagine if that doesn't work, it would be no big deal to change it back to "Unreal Gold" if you prefer it to be that way. :-k
The problem doesn't have anything to do with the game installation on my HD, I could call the folder "cucumbers" if I wanted. It's that the game can't find the right version of a file on my installation CD.
> **xnerdx said:**
> It seems you might be confusing where the CD is mounted with a direct path to the patch files. I suggest you extract the patches somewhere on your physical drive (For example /home/linus/Desktop/Patch_Files) this would likely work if it comes to not being able to find some patch files and make sure that the directory is exact, it is CASE-SENSITIVE.
The UnrealPatch226Final patch isn't looking for a path to where the patch is (the patch file is an .exe and isn't meant to be extracted anyway), it's looking for my game CD, which it found, but is telling me that I have the wrong version of a file that is needed on the CD.

---

