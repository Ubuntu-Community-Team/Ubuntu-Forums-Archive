---
title: "Wine, bottles VS Windows 10 in dual boot with Ubuntu (for ntfs recovery etc)?"
date: 2023-01-07
forum: Windows
---

### Post by smith73 on 2023-01-07
I am considering installing Ubuntu in dual boot with Windows 10. But maybe bottles, wine and other "Windows-for-Linux" visualizations (if any) for Ubuntu seem to provide some
Windows functionality to run Windows apps in Ubuntu. Are they essentially unsafe for Ubuntu, as Windows malware can propagate?
As there is *apparmor* function in Ubuntu, which containerizes apps, can  "Windows-for-Linux" visualizations be made more secure by installing Windows apps
(somehow) in a virtual environment (+apparmor)?

Can  "Windows-for-Linux" visualizations be sufficient to run Windows 3D CAD etc software on Ubuntu?

 I have 2 SSD USB drives, for which I need to regularly run *chkdsk -f* in Windows to repair the NTFS system, which for some reasons slightly malfunctions upon usage.
After copying the files from/to the USB drives in Ubuntu, + after 5-15 minutes after that upon clicking to safely remove/unmount the drive I do not get the notification that ~"Device is ready to safely remove". And I can estimate the state of the SSDs only by the solid/blinking/powered off LED indicator on these drives. Most of the time in this situation
the LED continues to blink (="device is busy"), though the Desktop icon for the device is removed after unmounting.
There are some guides on how to repair the NTFS system by installing some NTFS virtualization app in Ubuntu, but they caution that this can be unsafe and the best way to repair
it is via native Windows NTFS system = via a directly installed Windows.

Can any "Windows-for-Linux" visualizations like wine or bottles be used to repair NTFS system on an USB drive in Ubuntu?

---

### Post by TheFu on 2023-01-07
Lots of good questions, but your questions are extremely specific, so no single person can possibly answer with authority.  Also, just because something works no, that's no guarantee it will work in the next release.  Similarly, just because something doesn't work today, that doesn't mean that the next release won't allow it to work.  Generally, if something starts working, it will continue to work for 10 yrs, but not always.

> **smith73 said:**
> I am considering installing Ubuntu in dual boot with Windows 10. But maybe bottles, wine and other "Windows-for-Linux" visualizations (if any) for Ubuntu seem to provide some Windows functionality to run Windows apps in Ubuntu. Are they essentially unsafe for Ubuntu, as Windows malware can propagate?
I don't understand your use of the term "visualizations".  To a native speaker, it doesn't fit.  Do you mean "running a program?"

Some Windows malware runs under WINE, but not all of it does.  WINE isn't a full implementation of the Windows APIs.  That's good and bad.

You shouldn't switch to Linux expecting all the previously used MS-Windows programs to work.  Any that need direct access to hardware will likely NOT work.  In my experience, perhaps 20% of small, Windows programs can be made to work under Linux.  The WINE team has an appdb, which is where they try to specify which programs and versions of those programs are known to work under which WINE release. Some will have a 20-step setup/configuration guide.  Expect different MS-Windows programs to require different setups.

In short, seek native Lijnux applications, which are actively being developed and maintained as your primary choice for all new programs going forward.  WINE should be your last resort.  For example, I used to have a personal/small business MS-Windows program running under WINE, but only about 80% of the core functionality worked.  That was fine for most things.  Skip forward 2 yrs and a new WINE release.  It never worked again.  After trying to get it working for about 3 weeks, I installed Win7 into a virtual machine, then installed the same program and I'm still using that exact VM and program today.  I'd like a native Linux program that handles the same functions, but none exists. Sigh.  This 1 program, that gets run 5 minutes every other week, is the only remaining reason for MS-Windows here ... until tax time.

> **smith73 said:**
> As there is *apparmor* function in Ubuntu, which containerizes apps, can  "Windows-for-Linux" visualizations be made more secure by installing Windows apps (somehow) in a virtual environment (+apparmor)?
"Linux Containers" are a very specific term. They don't have anything to do with running MS-Windows programs.  Only native Linux programs can possibly run in a Linux Container.  Period.  Very few people touch apparmor for anything.  There are easier solutions to sandbox program access.  Getting in to those options isn't something for a beginner.

> **smith73 said:**
> 
Can  "Windows-for-Linux" visualizations be sufficient to run Windows 3D CAD etc software on Ubuntu?
Usually no.  I can't say "no" definitively, but it is highly unlikely.

> **smith73 said:**
>  I have 2 SSD USB drives, for which I need to regularly run *chkdsk -f* in Windows to repair the NTFS system, which for some reasons slightly malfunctions upon usage.
After copying the files from/to the USB drives in Ubuntu, + after 5-15 minutes after that upon clicking to safely remove/unmount the drive I do not get the notification that ~"Device is ready to safely remove". And I can estimate the state of the SSDs only by the solid/blinking/powered off LED indicator on these drives. Most of the time in this situation the LED continues to blink (="device is busy"), though the Desktop icon for the device is removed after unmounting.
There are some guides on how to repair the NTFS system by installing some NTFS virtualization app in Ubuntu, but they caution that this can be unsafe and the best way to repair it is via native Windows NTFS system = via a directly installed Windows.

Can any "Windows-for-Linux" visualizations like wine or bottles be used to repair NTFS system on an USB drive in Ubuntu?
Always use Native programs for the OS that the file system you want to repair.  That means using MS-Windows tools in MS-Windows for NTFS and FAT-whatever file systems.

> "Windows-for-Linux" visualizations like wine or bottles 
When I read that, it seems like you mean emulator or API-translator, since WINE actually stands for 
**W**ine
**I**s
**N**ot an 
**E**mulator
This is their attempt to point out that WINE is an API translation/interpretation tool.  It sees the Windows OS and API calls, translates them into native Linux APIs and runs the program.  The difference is something a programming background is probably needed to understand. They are definitely very different from each other.

---

### Post by yancek on 2023-01-07
Apps created to work in Linux for windows are not going to be as good as the original windows apps.  In what situations do you have to run chkdsk in windows?  There is no equivalent in Linux and if you have filesystem problems with windows, use windows software..  Seems odd that you would need chkdsk that frequently.

>  Can any "Windows-for-Linux" visualizations like wine or bottles be used to repair NTFS system on an USB drive in Ubuntu?         

I don't know what you are referring to when you say 'bottles' but windows programs will be better at repairing ntfs filesystems.

---

### Post by QIII on 2023-01-07
Some things work well under Wine, some do not.  There is a database of various rankings based on the observations of individuals who have tested them.  Unless you find someone who has studied the Wine database and has an eidetic memory, is a savant or a mnemonist, you won't find someone who has all the answers.  (By the way, although exceptional, even persons in those categories do not actually have perfect memory.)

It is important to know what Wine is:

As stated above Wine Is Not an Emulator.  Neither it is a hypervisor.

Wine attempts to intercept Windows API calls and translate them into POSIX calls that Linux can respond to.  That means someone has to do the work to make that hook function.  For some Windows applications, nobody has bothered.  For others, it does not work well.  For some few, things work pretty well.  But none work as well as they do in Windows.

Asking people here to be put on the spot is not likely to get you many detailed answers.

Unless you use a Linux alternative, you have three options, really:

1.  Research the Wine application database at [https://appdb.winehq.org/](https://appdb.winehq.org/) and find how well an application that interests you works ... if it is even listed.  Bear in mind, however, that Wine has some serious, possibly disastrous, security implications for Linux because the very Windows APIs for which Wine attempts to provide POSIX alternatives for can be used by malware designed to attack in that manner.  I would simply never, ever, install Wine.

2.  Run Windows in a virtual machine.  This is not likely a perfect answer, since much of the "hardware" is actually provided by a software "hardware abstraction layer", which means it's not a perfect one-for-one and you won't likely get, for instance, really good graphics performance without using a pass-through GPU.

3.  Run Windows on bare metal, as in a multi-boot or a separate machine.

I usually virtualize, but then I don't do graphics-heavy computation in a Windows VM.

---

### Post by VMC on 2023-01-08
Number **3.** above has always been my choice. I tried the alternatives in years past. Some issue always came up;hence Windows on its own playground.

---

### Post by TheFu on 2023-01-08
> **yancek said:**
>  I don't know what you are referring to when you say 'bottles' but windows programs will be better at repairing ntfs filesystems.

If WINE is the API layer, then "bottles" are custom configurations of WINE for specific programs.  That's their intent.  Basically, "bottles" are a fancy marketing name for managing the WINE_PREFIX environment variable.  Perhaps they have pre-configured settings for each bottle to add value?  IDK.  Since it would be illegal to include all the DLLs in a bottle, that must just make it easy to get them installed into a specific WINE_PREFIX.  I'm guessing.  I've always used WINE directly, though I've had commercial licenses for a popular run-on-linux commercial version of WINE. Never found that license useful, as they split it between MS-Office and everything else - where everything else was typically for games.  Only 14 yr old boys have the stamina to figure out all the WINE configs, required DLLS details, to make a game work and little interest in making 98% of the commercial programs to work.  

It is sorta a game.  Try the defaults, look at the errors, fix the first error by installing a DLL or tweaking some setting. Repeat.  Do that 50 times, and perhaps your Windows program will work.  OTOH, last time I tried to get it working, the program was using COM libraries, which weren't supported by WINE, so they'd never, ever, ever, work.

The older and simpler the program, the more likely it is that WINE can run it. That's been my experience, though some games from the late 1990s don't work still.  Much easier to have Win95/NT/XP inside a VM for my effort.

---

### Post by smith73 on 2023-01-08
> **TheFu said:**
> 
I don't understand your use of the term "visualizations".  To a native speaker, it doesn't fit.  Do you mean "running a program?"

Yes. Sorry. The term "visualizations" here should point to a "compatibility layer program".

---

