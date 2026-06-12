---
title: "Windows Registry and DLL's??? What's going on!"
date: 2006-06-29
forum: The Cafe
---

### Post by user1397 on 2006-06-29
Even though i'm a full-time ubuntu user now, I wasn't 3 months ago. I'm just wondering, what is the windows registry and what are those files that end with .dll in windows? I've heard so much crap about the windows registry being horrible, but why does everyone hate it? i'm looking for reasons and explanations. thanks for your time.

---

### Post by x64Jimbo on 2006-06-29
Windows registry is like /proc in Linux, and .dll's are like .so's in Linux. The reason they're nightmarish in Windows is that there is a very large population of trained primates releasing crappy software for Windows that breaks stuff. Windows wouldn't be nearly as bad if it weren't for the morons writing the programs for it.

---

### Post by mcduck on 2006-06-29
Think about the registry like this:

Take all those text-based configuration files (both system and user confgs) in linux, put them all in a massive binary file, sorted by complex series of alphanumeric keys instead of any sane names. Now think that every app has somewhat free acces to modify this registry, and that it's not actually controlled by anything so installing/removing things can break other settings and removing apps usually leaves most of it's registry settings there..

DLL's are like shared libraries in linux, but once again there is no version controll or anything so apps can overwrite or remove DLL files freely, even if other apps depend on them.. So installing a new program can actually replace a DLL file with older version thus breaking all programs that needed the new version..

---

### Post by amohanty on 2006-06-29
[QUOTE=x64Jimbo]Windows registry is like /proc in Linux, and .dll's are like .so's in Linux. The reason they're nightmarish in Windows is that there is a very large population of trained primates releasing crappy software for Windows that breaks stuff. Windows wouldn't be nearly as bad if it weren't for the morons writing the programs for it.[/QUOTE]


Although I do agree with it mostly :) - too may idiot point and click devs (not meant as flame bait - so if it offends you please ignore), I would have to say that that's not quite right. 

The registry is a single database of pretty much all the settings, startup, shutdown info, user session info, system state info, etc that the operating system and most applications use. The nearest equivalent in Linux would be some combination of:
/etc
/boot (some parts) 
/proc (some parts) 
/dev 
/sys 
/var (some parts)
+ a whole bunch of dot dirs in all users home directories.

note: I might have missed some here.

Now as to windows dll begin nightmarish take a look at:
[http://en.wikipedia.org/wiki/DLL_hell](http://en.wikipedia.org/wiki/DLL_hell)
you can google for dll hell too. Primarily there are severe issues with versioning , naming, installation and management of dlls in windows. As stated above they are quite similar to the .so files in linux however COM server are a completely different beast. Managed code under the .NET framework is supposed to eliminate these issues, but since I dont use it I can't say for sure.

HTH
AM

---

### Post by user1397 on 2006-06-29
wow, hearing all this, i'm never switching back to windows, ever!

---

### Post by rai4shu2 on 2006-06-29
To make matters worse, the registry is all stuffed in one giant file. It's not difficult to edit, but it's practically impossible to clean it up.

---

### Post by Virogenesis on 2006-06-29
registry is used not only for applications  but windows aswell.
Reg hacking to improve performance is a common thing to do BUT when do change things you'll find breakages that are hard to fix.
The registry gets huge and slow downs are common because of this.
AOL software is nery naughty for hiding crap in the registry.

---

### Post by Kvark on 2006-06-29
Type regedit on a Windows system and look around. Then type gconf-editor on an Ubuntu system and look around. The Gnome registry looks pretty similar to the Windows registry doesn't it? And if you have Wine installed then type regedit on Ubuntu to have a look at the Wine registry.

---

### Post by nocturn on 2006-06-29
[QUOTE=Kvark]Type regedit on a Windows system and look around. Then type gconf-editor on an Ubuntu system and look around. The Gnome registry looks pretty similar to the Windows registry doesn't it? And if you have Wine installed then type regedit on Ubuntu to have a look at the Wine registry.[/QUOTE]

Gconf does look similar, but the backend is in .gconf in your homedirectory.
Gconf is made up of one xml file per application (or multiple), but not one giant binary file.

If banshee breaks its gconf schema, it does not affect the panels or evolution.  It does not affect other users on the system or system startup and shutdown.

this is not the case on windows.

Let alone the fragility of such a single point of failure, it also gives a horrible performance.

---

### Post by aysiu on 2006-06-29
I wish Windows had something like *gtkorphan*. Whenever I've gotten messages about whether I should remove a .dll which may or may not be in use (yes, really helpful message), I've always kept it, just to be safe.

---

### Post by Jucato on 2006-06-29
IIRC, one of the problems of the Windows registry is that having all configurations for everything, both system-wide and application/user-specific, in one single database, in one single location, makes it an easy target from the security point of view. At least, that's how I understood it from previous discussions in here. 

Regarding DLL's, the problem is not so much as the DLL concept itself, which is a concept also used in Linux and other OS'es AFAIK. The problem lies in the way the Windows OS handles the installation/removal of DLL's. Unlike in Linux, Windows does not check dependencies and stuff like that. So it's very easy to overwrite validly/correctly working DLL's with corrupt/non-working ones. Of course, installers usually asks you when you are about overwrite a DLL, but Windows users, so used to clicking yes anywhere and everywhere, will most likely just ignore it and overwrite the DLL.

---

### Post by aysiu on 2006-06-29
[QUOTE=Fenyx]Of course, installers usually asks you when you are about overwrite a DLL, but Windows users, so used to clicking yes anywhere and everywhere, will most likely just ignore it and overwrite the DLL.[/QUOTE] Or maybe they don't just click yes for everything but have no idea which version to use because the wizard isn't very informative about what the issue is.

---

### Post by nocturn on 2006-06-29
[QUOTE=aysiu]Or maybe they don't just click yes for everything but have no idea which version to use because the wizard isn't very informative about what the issue is.[/QUOTE]

Indeed Aysiu.  I don't think an end user should be left to decide if he needs msvcrt40.dll version 4.0.1251.1 or 4.0.1254.2.  
Given that DLL's are not always backward compatible, it becomes impossible for even an advanced user to manage them.  And you have no way of determining what program put a particular DLL there or which overwrote it.

In addition, DLL names can clash (my video driver in Win98 used a DLL that was named identical to one in Laplink, the two programs couldn't be installed on the same system at the same time).

---

### Post by rcarring on 2006-06-29
Some application developers get around dll incompatibility by renaming a dll and putting the renamed file in the application directory rather than windows/system32.

A good example of this is Norton who renamed the Microsoft Foundation Classes version 4.0 file to sfc400.dll (or something like that, I won't have Norton software on any of my machines as it is crap)

Another infuriating aspect is when a dll version is the same as a dll to be installed, but newer, so the dll to be installed isn't and as a result the application to be installed crashes its installer.

---

### Post by user1397 on 2006-07-03
so where exactly is the system registry located?

---

### Post by blastus on 2006-07-03
The first time I heard about the Windows registry was two weeks after I had bought my new machine. I just turned it on one day and it wouldn't boot into Windows 95 anymore because the registry had been corrupted. I didn't know what the registry was or what it was used for or anything, but I knew that it must be a fragile piece of junk that was critical to Windows.

After calling Future Shop, they said that the only option was to reinstall Windows. As the store I bought the computer from offered absolutely no software support and I wasn't going to shell out a couple hundred to Future Shop to fix a brand new $3000+ machine, I bought a couple of books and figured out what the registry was all about and everything about how Windows 95 was different than Windows 3.1.

Ever since then no-one has given me any reason to believe that the Windows registry has any redeeming qualities. The registry fails, Windows fails, it's just that simple.

---

### Post by bruce89 on 2006-07-03
[QUOTE=erik1397]so where exactlyis the system registry located?[/QUOTE]
C:\WINDOWS\system32\config\system (the slashes are this way round in windows, don't ask me why)

It is a 5MiB (on my system) binary file.

---

### Post by Dr. Nick on 2006-07-03
Yeah registry fies are different depending on which version
look [here]("http://www.easydesksoftware.com/regfiles.htm")

The deal with win 3.1 was that most programs then acted sort of like linux applocations do today. Each program would make a .ini file for its configuration settings, I actually prefer that better than the registry, but someone got the bright idea that it would be better to make 1 big "ini file" and call it the registry instead of having a bunch of seperate files.

Think of this, In windows you download a "free trial" of some application and run it for 30days. After the 30 days it tells you its expired and wants you to purchase it. You decide you dont want too so you uninstall it and go on with your life. You then stumble upon the program again and install it but upon launching you get the message to purchase it again. Now how did they know you had already tried it? Chances are it left some nasty remnants in your registry upon previous removal to prevent you from just reinstalling the trail every 30days. Now think of all the "free trials" you have tried and removed, Think about how much combined crud they all have left behind and the registry doesnt seem so nice.

---

### Post by user1397 on 2006-07-03
so does wine bring a system registry folder?

---

### Post by prizrak on 2006-07-03
Registry has been discussed enough that I don't have to mention anything. One of the biggest problems with it is lack of transparency, not many people would know what each key does and even if they did who would bother looking through a huge database of random values. Spyware tends to put keys into the registry at will. While in Linux it is also possible it's not too difficult to look through your home directory with "View Hidden Files" turned on and see what doesn't belong there. 

DLL's have a huge number of problems. At first DLL's were meant as shared libraries much like we have in Linux. Unfortunately when ISV's wrote programs they would package their own DLL's. That of course led to many DLL's being overwritten by 3rd party applications, which could break compatibility with other applications. In Linux shared libraries are actually shared, so they don't get overwritten by 3rd party programs. The DLL issue has been largely solved in Windows though, however it was solved in a stupid way, applications now install their DLL's into their own directories instead of the same directory as system DLL's. That pretty much defies the whole point of sharing libraries.

---

