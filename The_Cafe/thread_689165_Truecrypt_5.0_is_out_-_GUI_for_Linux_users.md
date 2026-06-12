---
title: "Truecrypt 5.0 is out - GUI for Linux users"
date: 2008-02-06
forum: The Cafe
---

### Post by wieman01 on 2008-02-06
Read this:

[http://www.truecrypt.org/docs/?s=version-history]("http://www.truecrypt.org/docs/?s=version-history")

Good news for Linux users!

_**EDIT 1:**_
Server is temporarily down it seems... Too many Linux users downloading?

_**EDIT 2:**_
Also read this on Digg: [http://digg.com/software/TrueCrypt_5_0_Released_including_Linux_GUI_and_OSX_version]("http://digg.com/software/TrueCrypt_5_0_Released_including_Linux_GUI_and_OSX_version")

---

### Post by PmDematagoda on 2008-02-06
Brilliant, I have been waiting for this moment for months:).

Now to see if Truecrypt works on Hardy.

I just hope that their site comes back up as soon as possible.

---

### Post by wieman01 on 2008-02-06
It's going up & down at random. No idea what's going on.

I'll check it out as well, buddy. Let's attach some nice screenshots once we have it up & running, ok? :-) Just to make people jealous and feel bad because they have not got it yet! :-)

---

### Post by PmDematagoda on 2008-02-06
> **wieman01 said:**
> It's going up & down at random. No idea what's going on.

I'll check it out as well, buddy. Let's attach some nice screenshots once we have it up & running, ok? :-) Just to make people jealous and feel bad because they have not got it yet! :-)

I will try to do the same, but in order for use to have a "competition" the site has to come up in the first place:D.

---

### Post by PmDematagoda on 2008-02-06
Uhh wieman01, why did you start this thread in the Community Cafe Games if this thread is not a game thread? I would have thought such a thing like the release of Truecrypt 5.0 would have merited the Community Cafe;).

---

### Post by wieman01 on 2008-02-06
> **PmDematagoda said:**
> Uhh wieman01, why did you start this thread in the Community Cafe Games if this thread is not a game thread? I would have thought such a thing like the release of Truecrypt 5.0 would have merited the Community Cafe;).
Oh, aeh, yeah. I'll move it. Just noticed.

---

### Post by regomodo on 2008-02-06
blimey! i was  just about to give up with tcgui and truecrypt on linux in general. Refuses to mount a truecrypt volume i created using the windows client.

Once their server is resurrected i must give it a try.

---

### Post by rheywood on 2008-02-06
Managed to get this earlier this morning. Looks just like the Windows version, works great for me!

---

### Post by hyper_ch on 2008-02-06
Can you now fully encrypt your system (linux and/or windoze) with it?

---

### Post by wieman01 on 2008-02-06
> **rheywood said:**
> Managed to get this earlier this morning. Looks just like the Windows version, works great for me!
Screenshot perhaps? Guess the audience would appreciate it! :-)

---

### Post by wieman01 on 2008-02-06
> **hyper_ch said:**
> Can you now fully encrypt your system (linux and/or windoze) with it?
Windows users can, Linux users can't so far.

---

### Post by hyper_ch on 2008-02-06
> **wieman01 said:**
> Windows users can

Damn ;)

---

### Post by rheywood on 2008-02-06
Sure thing! Take a look at it [http://img265.imageshack.us/my.php?image=tcnq0.png]("http://img265.imageshack.us/my.php?image=tcnq0.png"). Hope thats ok :)

---

### Post by wieman01 on 2008-02-06
> **rheywood said:**
> Sure thing! Take a look at it [http://img265.imageshack.us/my.php?image=tcnq0.png]("http://img265.imageshack.us/my.php?image=tcnq0.png"). Hope thats ok :)
Absolutely gorgeous! Thanks!

_**EDIT:**_
Do you have full write/read access as non-privileged (non-root) user?

---

### Post by rheywood on 2008-02-06
As far as I can tell, yeah. I just mounted the volume without needing the root password, and copied a file across with no problems...

---

### Post by jbkerns on 2008-02-06
At this point in time, the windows and x86 deb is downloading at a blazing 2K rate.  In the meantime, can you tell me if the 64bit deb is available?  Thanks in advance.

---

### Post by stephantom on 2008-02-06
Wow, I am blown away.
If everything works as perfectly as the release notes suggest, woah.
You can download the files from [this mirror](http://neroon.com/Truecrypt/), signatures included so you can verify them.

Can't wait to get home so I can try this on Hardy. And until we get full drive encryption on Linux.
But still, wow. I'm excited.

---

### Post by wieman01 on 2008-02-06
> **rheywood said:**
> As far as I can tell, yeah. I just mounted the volume without needing the root password, and copied a file across with no problems...
Excellent! I can't tell you how excited I am, really.

---

### Post by Polygon on 2008-02-06
yay yay yay !

ive been forced to use forcefiled which is incredibly buggy!

but now we get an offical, gtk2 gui! im so excited =P

---

### Post by PmDematagoda on 2008-02-06
I am using the new Truecrypt right now(was slow in the uptake as I did not check this thread often), and it is really good, not bad at all for a first attempt in making a GUI for Linux:).

---

### Post by matthew on 2008-02-06
Great news! I'm really busy right now, but I will definitely give this a download soon. Thanks for the heads up!

---

### Post by wieman01 on 2008-02-06
Full HD encyrption does not work with Linux because Truecrypt only supports FAT32 and NTFS. Imagine a Linux system on a FAT32 file system. A contradiction in terms.

---

### Post by bone2006 on 2008-02-06
really happy it got a gui.  I had to create alias, because my memory isn't that good.........
I prefer using a gui and really really happy this was released.  It's a good day for me so far

Would have been nice if they did ext3 partitions, so hopefully that will come soon.

---

### Post by oudalrich on 2008-02-06
> Full HD encyrption does not work with Linux because Truecrypt only supports FAT32 and NTFS.

Not true. Truecrypt does not care which file system you use on a mapped volume. Look [here]("http://www.micressor.ch/index.php/Truecrypt") for a tutorial on how to set up a Truecrypt-encrypted ext3 disk. I can confirm this works, I'm using it on an external disk. And while it's true that Truecrypt can't encrypt your boot disk under Linux right now, there are [alternatives]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html").

Edit: And by the way, if have [Ext2 IFS]("http://www.fs-driver.org/") or something similar installed on a Windows machine, you have full read and write access to the Truecrypt-encrypted ext3 volume from Windows.

---

### Post by wieman01 on 2008-02-06
> **oudalrich said:**
> Not true. Truecrypt does not care which file system you use on a mapped volume. Look [here]("http://www.micressor.ch/index.php/Truecrypt") for a tutorial on how to set up a Truecrypt-encrypted ext3 disk. I can confirm this works, I'm using it on an external disk. And while it's true that Truecrypt can't encrypt your boot disk under Linux right now, there are [alternatives]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html").

Edit: And by the way, if have [Ext2 IFS]("http://www.fs-driver.org/") or something similar installed on a Windows machine, you have full read and write access to the Truecrypt-encrypted ext3 volume from Windows.
Oops, you're obviously right. I don't know where I had this piece of information from.

I got this from their FAQ:
> Yes, when mounted, TrueCrypt volumes can be formatted as FAT12, FAT16, FAT32, NTFS, or any other file system. TrueCrypt volumes behave as standard disk devices so you can right-click the device icon (for example in the 'Computer' or 'My Computer' list) and select 'Format'. The actual volume contents will be lost. However, the whole volume will remain encrypted. If you format a TrueCrypt-encrypted partition when the TrueCrypt volume that the partition hosts is not mounted, then the volume will be destroyed, and the partition will not be encrypted anymore (it will be empty).

---

### Post by 50words on 2008-02-06
The new Linux GUI is beautiful. I'm so happy I could cry. Seriously. I could never get Forcefield to mount my NTFS volumes properly.

I still hope to get some of the great Windows features like auto-dismount on shutdown. But for now, I will be plenty happy.

My review:
[http://solosmalltech.com/index.php/2008/02/06/truecrypt-50-released-with-major-new-features-linux-gui/](http://solosmalltech.com/index.php/2008/02/06/truecrypt-50-released-with-major-new-features-linux-gui/)

I can't remember if I donated to the TrueCrypt project last year, but I just sent $50 their way.

---

### Post by 50words on 2008-02-06
.

---

### Post by meho_r on 2008-02-06
Did they resolve /var/auth.log problem? No more cleartext passwords and keyfiles paths recorded?

---

### Post by gorgor_bay on 2008-02-06
I'm using an x86_64 system here, so I had to go with manual compilation.
The step are rather new for compiling, since there is now a GUI included.

First thing that surprised me is the need for wxwidgets source code. So I donwloaded it and extracted it into /usr/src as suggested by the TrueCrypt Readme.txt.
I then went on building wxwidgets for TrueCrypt:

```

$ make WX_ROOT=/usr/src/wxWidgets-2.8.7 wxbuild
Configuring wxWidgets library...
Building wxWidgets library...

```

This build terminated without problems and indeed created a './wxrelease/' directory. as promised by the Readme.txt

So I naturally went on to the next step: the main build. Unfortunately this is what happens:

```

$ make
Compiling Buffer.cpp
StringConverter.h:23: erreur: «static std::wstring TrueCrypt::StringConverter::FromNumber(long int)" cannot be overloaded
StringConverter.h:22: erreur: with «static std::wstring TrueCrypt::StringConverter::FromNumber(TrueCrypt::int64)"
StringConverter.h:26: erreur: «static std::wstring TrueCrypt::StringConverter::FromNumber(TrueCrypt::uint64)" cannot be overloaded
StringConverter.h:25: erreur: with «static std::wstring TrueCrypt::StringConverter::FromNumber(long unsigned int)"
make[1]: *** [Buffer.o] Erreur 1
make: *** [all] Erreur 2

```

Any idea what could be wrong ?

---

### Post by hyper_ch on 2008-02-06
as long as there is no kernel module available for TC it cannot be used for full-sytem encryption where only /boot remains unencrypted. Right?

---

### Post by snoopy1 on 2008-02-06
I jumped when I should have stepped lightly.  Very excited about the promise of a GUI, I removed truecrypt 4.3a-0 and installed version 5.0.  I'm running Kubuntu 6.06 LTS (I must continue using 6.06 to be in sync with work), and I have fuse-utils, libfuse2, and libfuse-dev installed, but when I run truecrypt 5.0, I get the following messages:

truecrypt: /usr/lib/libfuse.so.2: version `FUSE_2.6' not found (required by truecrypt)
truecrypt: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by truecrypt)

To me, it seems like a version problem.  Unfortunately, I did not keep a copy of the .deb file for 4.3a-0.  (I could hit myself! #-o )

Has anyone encountered this problem and found a solution?  Or does anyone know where I can get a copy of the .deb file for truecrypt 4.3a-0?  I can't reach my data... ](*,)

---

### Post by capink on 2008-02-06
> **hyper_ch said:**
> as long as there is no kernel module available for TC it cannot be used for full-sytem encryption where only /boot remains unencrypted. Right?

I only use containers with truecrypt. So I am not sure. Have you tried including the truecrypt kernel module into initramfs?

---

### Post by kuja on 2008-02-06
> **hyper_ch said:**
> as long as there is no kernel module available for TC it cannot be used for full-sytem encryption where only /boot remains unencrypted. Right?

THere is a kernel module. It ...oddly enough ........ is called ..... truecrypt.

---

### Post by p0llux on 2008-02-06
```

diff -Npr -x Language.xml.h truecrypt-5.0-source/Main/Forms/MainFrame.cpp truecrypt-5.0-patched/Main/Forms/MainFrame.cpp
*** truecrypt-5.0-source/Main/Forms/MainFrame.cpp	2008-02-05 10:21:10.000000000 +0100
--- truecrypt-5.0-patched/Main/Forms/MainFrame.cpp	2008-02-06 17:25:16.000000000 +0100
***************
*** 20,26 ****
  #include "FavoriteVolumesDialog.h"
  #include "LegalNoticesDialog.h"
  #include "PreferencesDialog.h"
! #include "TravelerDiskWizard.h"
  #include "VolumeCreationWizard.h"
  #include "VolumePropertiesDialog.h"
  
--- 20,26 ----
  #include "FavoriteVolumesDialog.h"
  #include "LegalNoticesDialog.h"
  #include "PreferencesDialog.h"
! //#include "TravelerDiskWizard.h"
  #include "VolumeCreationWizard.h"
  #include "VolumePropertiesDialog.h"
  
diff -Npr -x Language.xml.h truecrypt-5.0-source/Main/Forms/VolumeCreationWizard.h truecrypt-5.0-patched/Main/Forms/VolumeCreationWizard.h
*** truecrypt-5.0-source/Main/Forms/VolumeCreationWizard.h	2008-02-05 10:21:10.000000000 +0100
--- truecrypt-5.0-patched/Main/Forms/VolumeCreationWizard.h	2008-02-06 17:28:05.000000000 +0100
***************
*** 10,16 ****
  #define TC_HEADER_Main_Forms_VolumeCreationWizard
  
  #include "WizardFrame.h"
! #include "TravelerMountOptionsWizardPage.h"
  #include "Core/VolumeCreator.h"
  
  namespace TrueCrypt
--- 10,16 ----
  #define TC_HEADER_Main_Forms_VolumeCreationWizard
  
  #include "WizardFrame.h"
! //#include "TravelerMountOptionsWizardPage.h"
  #include "Core/VolumeCreator.h"
  
  namespace TrueCrypt
diff -Npr -x Language.xml.h truecrypt-5.0-source/Main/Main.make truecrypt-5.0-patched/Main/Main.make
*** truecrypt-5.0-source/Main/Main.make	2008-02-05 10:21:10.000000000 +0100
--- truecrypt-5.0-patched/Main/Main.make	2008-02-06 17:20:54.000000000 +0100
*************** CXXFLAGS += -I$(BASE_DIR)/Main
*** 67,74 ****
  
  ifeq "$(TC_BUILD_CONFIG)" "Release"
  
! CXXFLAGS += $(shell $(WX_BUILD_DIR)/wx-config --unicode --static --cxxflags)
! WX_LIBS = $(shell $(WX_BUILD_DIR)/wx-config --unicode --static --libs adv,core,base)
  
  else
  
--- 67,74 ----
  
  ifeq "$(TC_BUILD_CONFIG)" "Release"
  
! CXXFLAGS += $(shell $(WX_BUILD_DIR)/wx-config --unicode --cxxflags)
! WX_LIBS = $(shell $(WX_BUILD_DIR)/wx-config --unicode --libs adv,core,base)
  
  else
  

```
this is a quick and dirty hack for making tc5 compile on hardy.

---

### Post by imT on 2008-02-06
ok, installed, so now how can i place a truecrypt icon in my menu or it works only from terminal ???

---

### Post by rheywood on 2008-02-06
imT - go to System > Preferences > Main Menu. Then when that box appears, click on a sub menu, i.e 'Other' or whatever fits for you. Then click 'New Item'. Enter the name as 'Truecrypt' and in the command area enter 'truecrypt', then you're done!

---

### Post by regomodo on 2008-02-06
> **imT said:**
> ok, installed, so now how can i place a truecrypt icon in my menu or it works only from terminal ???

alt + f2. enter "truecrypt"

---

### Post by imT on 2008-02-06
@rheywood
i kind of knew that, i was wondering if the app has his own icon somewhere, thanks anyway :)

---

### Post by rheywood on 2008-02-06
Ah okay, sorry about that. Not that I know of anyway!

---

### Post by 50words on 2008-02-06
> **imT said:**
> @rheywood
i kind of knew that, i was wondering if the app has his own icon somewhere, thanks anyway :)

I couldn't find a TrueCrypt icon, although there must be one somewhere, since they use it for the system tray. I just used a padlock I found in the gnome emblems.

---

### Post by Polygon on 2008-02-06
To make an encrypyed filesystem thats other then fat32 , you just gotta select 'blank' file system, and then format it to the fs of your choice.

---

### Post by Jahl on 2008-02-06
I came across a few issues with the new GUI.

1. You can't select ext3 from the GUI
2. If you select NONE from the GUI for the filesystem the option to mount it raw has also been removed from the command line (-N option).

The work around to get an ext3 file system.

1. Use the GUI and create a FAT filesystem.
2. Mount the new Truecrypt volume using the GUI
3. Open a terminal and type mount
4. Unmount the truecrypt volume. For me it was umount /media/truecrypt1
5. Create the new file system. For ext3 use the following:
sudo mkfs -t ext3 /dev/loop0
6. Remount the drive using the GUI if you want.

---

### Post by bobbocanfly on 2008-02-06
> **50words said:**
> I couldn't find a TrueCrypt icon, although there must be one somewhere, since they use it for the system tray. I just used a padlock I found in the gnome emblems.

There are no icon files included in the deb so im guessing the icon is compiled into the binary.

---

### Post by breaking on 2008-02-06
Ok, just to put it out there...  if you want to use truecrypt that is your decision however Luks on linux does everything the current truecrypt 5.0 linux does...   It makes much more sense to me (at least) to use GPLed software if it is feature compatible.

My worry:  Could any part of truecrypt ever become closed or Payware or does the license somehow prohibit this?
Will there _ever_ cease to be a feature disparity between the linux and windows versions?  hidden vols/autodismount timeouts would be nice under linux too...

The data as it stands:
Luks pros:
GPL - no worries on freedoms
already integrated into ubuntu (and other distros)
integrated with hal and gnome-mount
(tc cant/wont clean up /dev/mapper if you use umount in the nautilus menu unlike luks)
ubuntu alt cd can make an encrypted root install!

Truecrypt pros:
hidden vols (only with fat) (5.0 linux CAN'T even make them)

Are there pros / cons to either side that i missed?  Personally i have no problem with using nonGPL tools if the advantage is there... but in this case, i just dont see why people would choose the current version of linux tc...  (except for the fact that they are just used to it)

General:
[http://blog.fubar.dk/?p=64](http://blog.fubar.dk/?p=64)
[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1196256,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1196256,00.html)

Luks linux automounter 
  cryptsetup (look in your package manager)

Windows luks tools:
[http://www.freeotfe.org/screenshots_pc.html](http://www.freeotfe.org/screenshots_pc.html)

ext2 for win:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Potential license issues:
[http://lists.debian.org/debian-legal/2006/06/msg00295.html](http://lists.debian.org/debian-legal/2006/06/msg00295.html)

---

### Post by ftk on 2008-02-06
> **snoopy1 said:**
> I jumped when I should have stepped lightly.  Very excited about the promise of a GUI, I removed truecrypt 4.3a-0 and installed version 5.0.  I'm running Kubuntu 6.06 LTS (I must continue using 6.06 to be in sync with work), and I have fuse-utils, libfuse2, and libfuse-dev installed, but when I run truecrypt 5.0, I get the following messages:

truecrypt: /usr/lib/libfuse.so.2: version `FUSE_2.6' not found (required by truecrypt)
truecrypt: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by truecrypt)

To me, it seems like a version problem.  Unfortunately, I did not keep a copy of the .deb file for 4.3a-0.  (I could hit myself! #-o )

Has anyone encountered this problem and found a solution?  Or does anyone know where I can get a copy of the .deb file for truecrypt 4.3a-0?  I can't reach my data... ](*,)

I am running into the same problem here. (6.06 LTS, truecrypt 5.0). Does anybody have any suggestions?

---

### Post by wieman01 on 2008-02-06
Just tested it. It's just great. I love the new interface. Although I can confirm there are still a few shortcomings (e.g. no ext3). But no big deal, really.

---

### Post by wieman01 on 2008-02-06
> **ftk said:**
> I am running into the same problem here. (6.06 LTS, truecrypt 5.0). Does anybody have any suggestions?
Upgrade to Feisty?

---

### Post by ftk on 2008-02-06
> **wieman01 said:**
> Upgrade to Feisty?

I am running Feisty at home, yes, but at work we are standardized on Dapper, for the reason that it is a Long Term Support release.

---

### Post by articpenguin on 2008-02-06
to use ext3. you have to do 

mkfs.ext3 /dev/loop0

with the truecrypt mounted.

---

### Post by AusIV4 on 2008-02-06
The Linux version seems to have regressed.

The GUI is nice, but I have a bunch of scripts that I wrote for version 4.3a, and the command line syntax has changed considerably. But, I do suppose backwards compatibility can prevent progress, so I won't complain about that too much.

The things that really bug me: It's too gui-centric. You can no longer create a volume from the command line, which means it's useless on headless systems (unless you create the volumes elsewhere and copy them to the headless system, which is more work than it should be).

It also bothers me that you can no longer create a hidden volume. You can open hidden volumes created on older versions or Windows systems, but you can't create them yourself.

The lack of easy ext3 support is nothing new, as it always gave the options of FAT or unformatted.

I doubt they'll re-introduce command-line creation anytime soon, but I hope they add support for creating hidden volumes before too long.
[EDIT]
It turns out you can't even use the command line options without X running. That means no mounting volumes remotely or before X has started.

---

### Post by bruce89 on 2008-02-06
> **wieman01 said:**
> Upgrade to Feisty?

Why Feisty and not Gutsy?

---

### Post by PmDematagoda on 2008-02-06
Since some people have been wanting to use Truecrypt version 4.3a, I decided to upload one that was lying around my PC, there may be some problems since the version is made for Gutsy, but it may work on Dapper as well, I cannot be sure though so you will have to use it at your own risk.

---

### Post by Polygon on 2008-02-06
truecrypt 5.0 and the gui work flawlessly, im impressed.

---

### Post by serzz on 2008-02-06
I'm having very big problem with new version. Everytime I try to copy some new files on encrypted volume first nautilus and then whole system hangs. Tried to run from terminal no error output whatsoever. Anyone having these kind of problems?

---

### Post by anitract on 2008-02-06
Why on earth would the developers remove command line features?   I really do not understand the logic behind this.  I would assume that a large number of the TC Linux users are power users that rely on good command line options...it just seems strange to me.

Can we confirm that there are missing command line switches?  And if so, which ones?

---

### Post by Polygon on 2008-02-06
> **anitract said:**
> Why on earth would the developers remove command line features?   I really do not understand the logic behind this.  I would assume that a large number of the TC Linux users are power users that rely on good command line options...it just seems strange to me.

Can we confirm that there are missing command line switches?  And if so, which ones?

it seems normal

> 
mark@Cactus-Fantastico:~/svn/deluge/trunk$ truecrypt --help
Usage: truecrypt [--auto-mount <str>] [--background-task] [-d] [--cache] [-C] [--explore] [-f] [-h] [-k <str>] [--filesystem <str>] [--fs-options <str>] [-l] [-m <str>] [--new-keyfiles <str>] [--new-password <str>] [--non-interactive] [-p <str>] [--load-preferences] [--protect-hidden] [--protection-keyfiles <str>] [--protection-password <str>] [-v] [--slot <str>] [--test] [-t] [--version] [Volume path] [Mount point]
  --auto-mount=<str>            Auto mount device-hosted/favorite volumes
  --background-task             Start Background Task
  -d, --dismount                Dismount volume
  --cache                       Cache passwords and keyfiles
  -C, --change                  Change password or keyfiles
  --explore                     Open explorer window for mounted volume
  -f, --force                   Force mount/dismount/overwrite
  -h, --help                    Display help
  -k, --keyfiles=<str>          Keyfiles
  --filesystem=<str>            Filesystem type
  --fs-options=<str>            Filesystem options
  -l, --list                    List mounted volumes
  -m, --mount-options=<str>     Mount options
  --new-keyfiles=<str>          New keyfiles
  --new-password=<str>          New password
  --non-interactive             Do not interact with user
  -p, --password=<str>          Password
  --load-preferences            Load user preferences
  --protect-hidden              Protect hidden volume
  --protection-keyfiles=<str>   Keyfiles for protected hidden volume
  --protection-password=<str>   Password for protected hidden volume
  -v, --verbose                 Enable verbose output
  --slot=<str>                  Volume slot number
  --test                        Test internal algorithms
  -t, --text                    Use text user interface
  --version                     Display version information


the only thing i dont see is creating a volume with the cli, but everything else seems to be there. Creating a volume with the cli was annoying anyway.

---

### Post by anitract on 2008-02-07
Annoying but necessary if you have a headless system.  I'm still not seeing the benefit of removing one switch (if that is indeed the case)?

---

### Post by wieman01 on 2008-02-07
> **AusIV4 said:**
> The Linux version seems to have regressed.

The GUI is nice, but I have a bunch of scripts that I wrote for version 4.3a, and the command line syntax has changed considerably. But, I do suppose backwards compatibility can prevent progress, so I won't complain about that too much.

The things that really bug me: It's too gui-centric. You can no longer create a volume from the command line, which means it's useless on headless systems (unless you create the volumes elsewhere and copy them to the headless system, which is more work than it should be).

It also bothers me that you can no longer create a hidden volume. You can open hidden volumes created on older versions or Windows systems, but you can't create them yourself.

The lack of easy ext3 support is nothing new, as it always gave the options of FAT or unformatted.

I doubt they'll re-introduce command-line creation anytime soon, but I hope they add support for creating hidden volumes before too long.
[EDIT]
It turns out you can't even use the command line options without X running. That means no mounting volumes remotely or before X has started.
But you can format the volume yourself and make it a 'ext3'. There is a post further above with a link to a website which explains how to do that.

---

### Post by wieman01 on 2008-02-07
> **bruce89 said:**
> Why Feisty and not Gutsy?
Or even Gutsy.

---

### Post by FuturePilot on 2008-02-07
Just curious, why can I only select FAT for the file system?

---

### Post by wieman01 on 2008-02-07
> **FuturePilot said:**
> Just curious, why can I only select FAT for the file system?
I don't know but you can format the volume afterwards. That's what I am going to do (ext3 in my case).

---

### Post by uzd4ce on 2008-02-07
I tried it out, but ended up going back to Forcefield.  I looked around in TC 5, but I couldn't find a setting to dismount on screensaver activation.  

Does anyone know if that feature is in there and I just missed it?  That's a big one for me and Forcefield seems to work fine.

Thanks

---

### Post by FuturePilot on 2008-02-07
> **wieman01 said:**
> I don't know but you can format the volume afterwards. That's what I am going to do (ext3 in my case).

Ah, didn't think of that. :)

---

### Post by sajochin on 2008-02-07
> **serzz said:**
> I'm having very big problem with new version. Everytime I try to copy some new files on encrypted volume first nautilus and then whole system hangs. Tried to run from terminal no error output whatsoever. Anyone having these kind of problems?

I've got the same problem here. It also happens when I try to format /dev/loop0 (unmounted truecrypt volume) with an ext filesystem.

---

### Post by Heinzelotto on 2008-02-07
> **AusIV4 said:**
> 
[EDIT]
It turns out you can't even use the command line options without X running. That means no mounting volumes remotely or before X has started.

does it work if you use the text-mode (-t switch)?

---

### Post by meho_r on 2008-02-07
It is nice to have GUI, but removing CLI options -- man that's bad. I think I'll stick with 4.3a for some time.

BTW, although TC GUI is welcome, I think EasyCrypt GUI is much intuitive and useful. It has better integration in Gnome DE, it is much simpler to use, has two modes: Normal for total beginner and expert, it has "crypt creation presets" so you can create crypt with CD, DVD or manual sizes, it has support for FAT, ext2, ext3 and NTFS FS so no need for manually formatting, it mounts crypt under it's name, not "truecrypt 1, truecrypt 2...", it's in the Hardy's repos;).... etc.

---

### Post by WorldTripping on 2008-02-07
er,

I'm having a few problems mounting volumes with the new version.

The script;

```
#!/bin/bash
truecrypt -M 'rw,user,umask=0002,gid=plugdev,iocharset=utf8' /media/External-250Gb/Backups/Crypt/Crypt.tc /media/Crypt
```

Used to mount a volume, and depending on which password was used, a container or a hidden volume would be mounted.

Now, with TrueCrypt 5.0 I can get the container to mount, but in no way can I get hidden volumes to mount.

Not with the GUI, nor with the command line.

Anyone any ideas ?

---

### Post by wieman01 on 2008-02-07
> **WorldTripping said:**
> er,

I'm having a few problems mounting volumes with the new version.

The script;

```
#!/bin/bash
truecrypt -M 'rw,user,umask=0002,gid=plugdev,iocharset=utf8' /media/External-250Gb/Backups/Crypt/Crypt.tc /media/Crypt
```

Used to mount a volume, and depending on which password was used, a container or a hidden volume would be mounted.

Now, with TrueCrypt 5.0 I can get the container to mount, but in no way can I get hidden volumes to mount.

Not with the GUI, nor with the command line.

Anyone any ideas ?
One user in this thread mentioned that 'hidden' volumes are no more supported. Could that be the issue?

---

### Post by WorldTripping on 2008-02-07
> **AusIV4 said:**
> 
It also bothers me that you can no longer create a hidden volume. You can open hidden volumes created on older versions or Windows systems, but you can't create them yourself.


hmmm,

It may just be me, but I couldn't find a mention in this thread about a lack of mounting existing hidden volumes.

I'd be very suprised if I could create and mount a hidden volume in 4.3, and not access this volume in 5.0

I dont care if this is done via CLI or GUI, but I would expect forward compatability.

Like I say, it might just be me missing the correct CLI command, but there should be some way of mounting and accessing volumes created in prior versions.

---

### Post by Mandorr on 2008-02-07
No more text mode in turecrypt? well that can't be ture?

When i tray to use truecrypt it just say.

Error: unable to initialize GTK, is display set properly?

there has to be a way around this! :confused:

---

### Post by DigitalDuality on 2008-02-07
d

---

### Post by Mandorr on 2008-02-07
I just can’t believe this ****!

I just install gnome on my lab server and it just runs!
No more text mode, no more truecrypt!

It’s a sad day! :cry:

---

### Post by meho_r on 2008-02-07
Well, you don't have to use v.5. Use 4.3. I cannot see any (positive) difference anyway...

---

### Post by ftk on 2008-02-07
> **ftk said:**
> I am running into the same problem here. (6.06 LTS, truecrypt 5.0). Does anybody have any suggestions?

After spending over an hour of paid time trying to get this resolved and reading about the lost CLI functionality I have decided to go back to 4.3a. If anybody needs the source to compile let me know and I will post it, as I didn't see it on the truecrypt site.

A GUI is nice and all but at the same time cumbersome. I also believe that backwards compatibility is important, especially when in previous versions CLI was the only way to get things done. This is a bummer as truecrypt is a great product due to the cross-platform compatibility.

---

### Post by WorldTripping on 2008-02-07
> **meho_r said:**
> Well, you don't have to use v.5. Use 4.3. I cannot see any (positive) difference anyway...

I agree, and that is exactly what I have just had to do.

Still a bit perplexed though as to why it's not possible to mount a volume within a volume, as this was exactly one of TrueCrypt's selling points.

If I used to be able to do this using the CLI in 4.3, then why can I not do it in 5.0 using either the GUI or the CLI.

Ah well, nothing lost, but nothing gained either.

---

### Post by 50words on 2008-02-07
Are people sending these concerns to the project? If not, please do.

---

### Post by meho_r on 2008-02-07
Bug has been raised in this regard. I know that at least two guys done it;) It might be more. And it should be

---

### Post by mveltre on 2008-02-07
my system freezes when I try to move about 80mb to a "fresh" formatted truecrypt volume (whirlpool, aes). I used the same disk with truecrypt 4.3a before on ubuntu 7.10 i386. Installed truecrypt 5.0 via the .deb-file.

---

### Post by dustigroove on 2008-02-07
I've been getting along quite nicely with the EasyCrypt/TrueCrypt combo but having a native GUI is great, works well so far.

Anyone found a good icon to use for the launcher? (It appears the icon the app uses is embedded.)

Cheers,

---

### Post by yottabit on 2008-02-07
Hi All,

I'm using TrueCrypt 5.0 in up-to-date Ubuntu 7.10.

1. I use TrueCrypt to create a container file of 384 MB, called pagefile.sys, on my Desktop (or on a USB drive; doesn't matter). I enter a 26-character password for encryption, and select to use IMG_5190.JPG, a 3.9 MB photo, for the keyfile. Encryption chugs right along, then I'm told it's finished.

Problem is, when I try to mount the new volume, the decryption fails. I am positive I'm entering the correct password and selecting the correct keyfile.

2. So I start over, and this time I don't select a keyfile during the creation wizard. This time I can mount it fine. Oookay, sure. Dismount, add keyfile, remount, works fine!

3. Next I create the volume again, using only a password. After completion I immediately add a keyfile before ever mounting the volume. After that success, I try a mount, and no-go. Same problem as in #1 above.

So I have a work-around, to create volume with password, mount, unmount, add keyfile, remount, and it works. But obviously this is a bug? Can anyone else confirm?

J

---

### Post by Washer on 2008-02-07
> **regomodo said:**
> blimey! i was  just about to give up with tcgui and truecrypt on linux in general. Refuses to mount a truecrypt volume i created using the windows client.

Once their server is resurrected i must give it a try. I had that problem a while ago. You need root permissions to mount it. Feel free to bother me if you can't get it.

---

### Post by leftorvo on 2008-02-07
it also apparently works after upgrading the kernel (I think it uses fuse or something, before you had to remake the kernel module each time you upgraded the kernel), which is great!

---

### Post by OmegaBLK on 2008-02-07
^Yea, that was one of the improvements that the project alluded to for 5.0:

> 
The Linux version of TrueCrypt has been redesigned so that it will no longer be affected by changes to the Linux kernel (kernel upgrades/updates).

[source](http://www.truecrypt.org/docs/?s=version-history)


Anyways, I pretty happy about the new 5.0 version.  Had to wait awhile since Truecrypt broke after a kernel update and I didn't feel like compiling from source.  Been waiting for the GUI also; won't have to use third-party frontends no more.  Works fine so far.

---

### Post by kingleer on 2008-02-07
> 
I came across a few issues with the new GUI.

1. You can't select ext3 from the GUI
2. If you select NONE from the GUI for the filesystem the option to mount it raw has also been removed from the command line (-N option).

The work around to get an ext3 file system.

1. Use the GUI and create a FAT filesystem.
2. Mount the new Truecrypt volume using the GUI
3. Open a terminal and type mount
4. Unmount the truecrypt volume. For me it was umount /media/truecrypt1
5. Create the new file system. For ext3 use the following:
sudo mkfs -t ext3 /dev/loop0
6. Remount the drive using the GUI if you want.
__________________

 

Anyone who wants to make an ntfs volume should use  mkntfs  instead pf mkfs 

see 

[http://linux.die.net/man/8/mkfs.ntfs](http://linux.die.net/man/8/mkfs.ntfs)

My question is: 

How long should mkfs take to format a 250 gb hardrive connected to a computer via a usb cable? 

It takes forever for me, and freezes.  Is there a quick format option with mkfs?

---

### Post by StevenHarper on 2008-02-07
My major problem is that you cannot create a Crypt from the command Line, I am the author and packager of Easy Crypt, an alternative GUI for Hardy, but as 5.0 cannot make crypt on the CLI, I am stuck.

[http://ubuntuforums.org/showthread.php?t=585578&page=27](http://ubuntuforums.org/showthread.php?t=585578&page=27)

Steve

---

### Post by craZy_omfg on 2008-02-07
> **yottabit said:**
> Hi All,

I'm using TrueCrypt 5.0 in up-to-date Ubuntu 7.10.

1. I use TrueCrypt to create a container file of 384 MB, called pagefile.sys, on my Desktop (or on a USB drive; doesn't matter). I enter a 26-character password for encryption, and select to use IMG_5190.JPG, a 3.9 MB photo, for the keyfile. Encryption chugs right along, then I'm told it's finished.

Problem is, when I try to mount the new volume, the decryption fails. I am positive I'm entering the correct password and selecting the correct keyfile.

2. So I start over, and this time I don't select a keyfile during the creation wizard. This time I can mount it fine. Oookay, sure. Dismount, add keyfile, remount, works fine!

3. Next I create the volume again, using only a password. After completion I immediately add a keyfile before ever mounting the volume. After that success, I try a mount, and no-go. Same problem as in #1 above.

So I have a work-around, to create volume with password, mount, unmount, add keyfile, remount, and it works. But obviously this is a bug? Can anyone else confirm?

J

Same here
no container but a partition
when adding the keyfile afterwards it works fine.


greetz

---

### Post by Polygon on 2008-02-08
they might of removed cli creation of volumes just for this version cause it wasnt working with the gui or something, hopefully they will add it back in

---

### Post by wieman01 on 2008-02-08
> **Jahl said:**
> I came across a few issues with the new GUI.

1. You can't select ext3 from the GUI
2. If you select NONE from the GUI for the filesystem the option to mount it raw has also been removed from the command line (-N option).

The work around to get an ext3 file system.

1. Use the GUI and create a FAT filesystem.
2. Mount the new Truecrypt volume using the GUI
3. Open a terminal and type mount
4. Unmount the truecrypt volume. For me it was umount /media/truecrypt1
5. Create the new file system. For ext3 use the following:
sudo mkfs -t ext3 /dev/loop0
6. Remount the drive using the GUI if you want.
Does this work? Can anybody else confirm it?

---

### Post by craZy_omfg on 2008-02-08
> **wieman01 said:**
> Does this work? Can anybody else confirm it?

Yes this is working.
/dev/loop0 might be slight different, depends on what 'mount' says.


btw is there an possibility to benchmark the algorithm ?

on win they can select 'benchmark' in the truecrypt gui..
but nothing on the linux gui..


greetz

---

### Post by wieman01 on 2008-02-08
Excellent, craZy_omfg. That's great news!

---

### Post by anitract on 2008-02-08
Forums are now up.  

Let's keep our discussions civil over there. ;)

Hopefully the next release will be fairly quick addressing some of our concerns!

---

### Post by i M@N on 2008-02-09
Hello.

GUi is really nice in this 5.0 BUT :
- compiling it is a pain, i'm still trying ...
- command line has regressed : no more creation of volume (well i didn't find it)

For those who need an icon i join one to my post.
i join also the source code for 4.3a : [http://imanweb.free.fr/uploaded/truecrypt-4.3a-source-code.tar.gz](http://imanweb.free.fr/uploaded/truecrypt-4.3a-source-code.tar.gz)

@+...

---

### Post by jal on 2008-02-09
> **PmDematagoda said:**
> Since some people have been wanting to use Truecrypt version 4.3a, I decided to upload one that was lying around my PC, there may be some problems since the version is made for Gutsy, but it may work on Dapper as well, I cannot be sure though so you will have to use it at your own risk.

Thanks for the upload. I installed this deb onto 6.06 (2.6.15-51-386) and got:

truecrypt: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by truecrypt)

I found this though:

jal@acknak:/lib/tls/i686/cmov$ ls -l libc.so.6
lrwxrwxrwx 1 root root 13 2007-07-25 17:22 libc.so.6 -> libc-2.3.6.so

---

### Post by kevdog on 2008-02-09
think Im going to hold off on truecrypt 5.0 until some of these issues are rectified. I definitely need to create volumes on the CLI and need ext3 filesystem.  I was so looking forward to the new version -- sounds like the window's developers got a hold of it and took functionality away.

---

### Post by dustigroove on 2008-02-09
> **i M@N said:**
> For those who need an icon i join one to my post.

Excellent, many thanks.

---

### Post by wieman01 on 2008-02-11
> **kevdog said:**
> think Im going to hold off on truecrypt 5.0 until some of these issues are rectified. I definitely need to create volumes on the CLI and need ext3 filesystem.  I was so looking forward to the new version -- sounds like the window's developers got a hold of it and took functionality away.
Kevdog, 

**'ext3'** is no issue at all. I just did it over the weekend and it works fine, both for file containers and entire partitions. I have never been in need of CLI, so I can't say much here, but **'ext3'** is definitely no problem. There are instructions posted in this thread, but I could repeat them here if you like me to.

---

### Post by leftorvo on 2008-02-11
> Since some people have been wanting to use Truecrypt version 4.3a, I decided to upload one that was lying around my PC, there may be some problems since the version is made for Gutsy, but it may work on Dapper as well, I cannot be sure though so you will have to use it at your own risk.

Thank you, this might come in useful if I have to uninstall 5.0 - i might, it is freezing my computer whever the TC partition gets heavy usage :(

---

### Post by gweaver on 2008-02-12
> **kevdog said:**
> think Im going to hold off on truecrypt 5.0 until some of these issues are rectified. I definitely need to create volumes on the CLI and need ext3 filesystem.  I was so looking forward to the new version -- sounds like the window's developers got a hold of it and took functionality away.

The CLI feature reduction is a problem for me too, and it breaks easycrypt:(

---

### Post by wieman01 on 2008-02-12
> **gweaver said:**
> The CLI feature reduction is a problem for me too, and it breaks easycrypt:(
What does CLI actually do? First time I hear of it.

---

### Post by leftorvo on 2008-02-12
> What does CLI actually do? First time I hear of it.

before you had to use the cli, now that there is an added gui the cli is greatly reduced in its features

anyway, tc5 has many extremely significant improvements (most significant of all being using fuse so it doesnt have to get recompiled each kernel upgrade), but an equally (or more) problem, that it freezes allmost all my applications whenever it takes hard usage :( i dont know what to do, but i really hope there is a way to fix it, it is an extreme inconveinence

---

### Post by ftk on 2008-02-12
> **wieman01 said:**
> What does CLI actually do? First time I hear of it.

CLI stands for Command Line Interface. A lot of people prefer typing in a short command to having to click through ten windows to do the same thing.

[http://en.wikipedia.org/wiki/Command_line_interface]("http://en.wikipedia.org/wiki/Command_line_interface")

---

### Post by wieman01 on 2008-02-13
> **ftk said:**
> CLI stands for Command Line Interface. A lot of people prefer typing in a short command to having to click through ten windows to do the same thing.

[http://en.wikipedia.org/wiki/Command_line_interface]("http://en.wikipedia.org/wiki/Command_line_interface")
Ah, that makes sense. Thanks.

---

### Post by toagu on 2008-02-13
For those looking for 4.3a for various Linux distros & kernel versions - it is available from the truecrypt website too :

[http://www.truecrypt.org/pastversions.php](http://www.truecrypt.org/pastversions.php)

HTH

---

### Post by toagu on 2008-02-13
I had a different problem with CLI in 5.0a .... My TC volume is NTFS and I used to load it with ntfs-3g using the options:
  --filesystem ntfs-3g --mount-options defaults,locale=en_US.utf8

The new CLI expects a = after --filesystem and --mount-options (as per the help) - but even after doing that, I still get a "unknown option: defaults"  error message. 

Anyone know of any workarounds for this ? 

TIA

---

### Post by adpads on 2008-02-14
> **oudalrich said:**
> And by the way, if have [Ext2 IFS]("http://www.fs-driver.org/") or something similar installed on a Windows machine, you have full read and write access to the Truecrypt-encrypted ext3 volume from Windows.

Alas! If only this were the case! I have been trying to put a truecrypt volume on a shared ext3 partition on my dual booting machine, but I am having a conflict ont eh windows side between truecrypt and ext2ifs. Whenever Truecrypt tries to mount or finish creating a volume under windows with ext2ifs installed, regardless of the location of the volume (on or off the ext3 partition), windows gives me the blue screen of death or hangs. Is anyone else having this problem?

---

### Post by MacGeneral on 2008-02-16
[COLOR="Red"]**I posted a small How-To about using TrueCrypt along with ext3 and in terminal mode only => [here]("http://ubuntuforums.org/showpost.php?p=4344099&postcount=3") <=**[/COLOR]

---

### Post by IamAcoconut on 2008-02-19
How can you create a volume on a CD/DVD, other then burning an existing volume from HDD? I heard Truecrypt can do this on Windows. Would be very useful way to backup sensitive data.

---

### Post by IamAcoconut on 2008-02-20
BTW, here's an icon Truecrypt puts in the notification tray. I made a screenshot of it.
You may save it to desktop and...
```
cd ~/Desktop 
sudo mv truecrypt.png /usr/share/pixmaps/truecrypt.png
```
Once you add a truecrypt launcher to your menu or panel it will automatically be associated with the icon. Did this under Gnome.

---

### Post by Polygon on 2008-02-20
there is a new version out not (5.0a) although it does not list what bugs are fixed...besides that some are fixed.

---

### Post by savantelite on 2008-02-20
Wooo hooo, 

Now no one will ever find out I have porn on my computer!

---

### Post by IamAcoconut on 2008-02-20
> **savantelite said:**
> Wooo hooo, 

Now no one will ever find out I have porn on my computer!
Aha. Btw, [http://www.eff.org/press/archives/2008/02/07](http://www.eff.org/press/archives/2008/02/07)

---

### Post by OmegaBLK on 2008-02-20
> **Polygon said:**
> there is a new version out not (5.0a) **although it does not list what bugs are fixed...besides that some are fixed**.

**Emphasis mine**

I don't get this mentality.  The devs (in the Readme file) say check their website to view changes for 5.0a.  I go to the website and then the only reference to fixed bugs for Linux states:

> 
Many other minor bug fixes.  (Windows, Mac OS X, and Linux)


WTF?  I guess I spoke to soon praising this particular release and the GUI.  It is still better then a broken TrueCrypt and the added features/fixes are welcomed, but I still would have liked a functioning CLI version and the man page--what happened to that?  None of this stuff is deal-breaker, but there are a few minor touches that I wish the devs had addressed before releasing the Linux version.  I guess I'll login and rant over at the TC-Linux forum to give them a piece of my mind also.  :)

---

### Post by wieman01 on 2008-02-22
If anybody could help me with this one, I would surely appreciate it:

[http://ubuntuforums.org/showthread.php?p=4380748#post4380748]("http://ubuntuforums.org/showthread.php?p=4380748#post4380748")

Might be an interesting question that others have asked themselves as well.

---

### Post by netlogic on 2008-02-23
> **imT said:**
> @rheywood
i kind of knew that, i was wondering if the app has his own icon somewhere, thanks anyway :)

here you go. i extracted from the original windows exe.
[truecrypt png icons]("ftp://www1.myftp.org/pub/truecrypt.icons.tar.gz")
just drop them in your /usr/share/pixmaps

---

### Post by wieman01 on 2008-03-11
Good news... With version 5.1 CLI is back to normal!

[http://www.truecrypt.org/docs/?s=version-history]("http://www.truecrypt.org/docs/?s=version-history")

---

### Post by matthew on 2008-03-11
> **wieman01 said:**
> Good news... With version 5.1 CLI is back to normal!

[http://www.truecrypt.org/docs/?s=version-history](http://www.truecrypt.org/docs/?s=version-history)Thanks for the heads up! I'm downloading it now.

---

### Post by wieman01 on 2008-03-11
> **matthew said:**
> Thanks for the heads up! I'm downloading it now.
So will I, Matthew, as soon as I get back home. I cannot believe the pace at which they are making progress and implementing improvements. The Truecrypt team is doing a great job.

---

### Post by matthew on 2008-03-11
> **wieman01 said:**
> The Truecrypt team is doing a great job.Agreed. They have impressed me from the beginning. I used E4M years ago, and when the developer(s) of it decided to go closed-source and commercial I was thrilled to see the TrueCrypt project start as a fork of that code.

---

### Post by Polygon on 2008-03-12
is creating an encrypted drive with ext3 fixed now? aka creating a blank volume and then mounting it with like /dev/mapper and then formatting that? I tried it with 5.0 and it didnt work, anyone have a positive test report?

---

### Post by anoopengineer on 2008-03-28
You can find an icon for truecrypt [here: http://www.dailygyan.com/2008/03/truecrypt-icon-for-ubuntu.html]("http://www.dailygyan.com/2008/03/truecrypt-icon-for-ubuntu.html")

[http://www.dailygyan.com/search/label/TrueCrypt](http://www.dailygyan.com/search/label/TrueCrypt) for more Truecrypt articles

Happy encrypting

---

### Post by war59312 on 2008-05-26
Easy enough to add icon for TrueCrypt...

First open a terminal and run:

sudo gedit /usr/share/applications/TrueCrypt.desktop

Add to file and save:

> [Desktop Entry]
Name=TrueCrypt
Comment=TrueCrypt
Exec=/usr/bin/truecrypt
Icon=/home/**will**/.icons/truecrypt.png
Terminal=false
Type=Application
Categories=Application;System

Dont forget to edit home directory of course. ;)

Then you can run TrueCrypt via Applications > System Tools .

Just edit last line if you dont want it under system tools.

And of course download the truecrypt icon to the icon directory.

---

