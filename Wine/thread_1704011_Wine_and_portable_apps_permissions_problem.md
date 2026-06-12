---
title: "Wine and portable apps permissions problem"
date: 2011-03-10
forum: Wine
---

### Post by gc2712 on 2011-03-10
I am trying to run Portable Apps (The Windows variety not linux) on Ubuntu 10.10 desktop, using wine-1.3.15. I can run the apps as root, but not as user - even though in properties I am listed as the owner! 

I have also tried to set executable bits as both user and as root but the exe file reverts immediately to the non-executable bit. (This has not been a problem starting PortableApps as root.)

Is there anything I can do to correct this problem? And why am I unable to change the executable bit even as root? 

Many thanks for assistance.

---

### Post by cogadh on 2011-03-10
It's a "security feature" of Ubuntu. All executables on removable media are automatically set to no execute now. Been that way for the last two version of Ubuntu. The only way to get around it with Wine is to run the app via the terminal; trying to run it via the GUI won't work.

BTW - Running Wine using sudo or a root account is inherently bad, you really shouldn't do that.

---

### Post by gc2712 on 2011-03-10
Thanks for the quick response. I do realise its not good to run wine as root, hence my wish to solve the problem running it as ordinary user.

I tried the cli approach to running the app with wine as you suggest. No go, same error. (Although it has worked for me before with other exe files) It was using wine from the wine ppa that got me running without cli.

Is there another answer to running Portable Apps as an ordinary user from usb HDD? and also changing the executible bit so it sticks?

---

### Post by yesrno on 2011-03-10
What if you type the following command in the terminal:
chmod +x appname.exe
 
Than execute the file with
wine appname.exe

---

### Post by bob-linux-user on 2011-03-10
Have you tried running the portable apps from a FAT32 or NTFS formatted drive? That might work better.

---

### Post by Morbius1 on 2011-03-10
Wine doesn't care if it's executable.
Wine is not capable of determining if a given *.exe has a Linux executable bit set. 
The problem is with something called cautious-launcher that Ubuntu places before the actual wine command. So the solution is to bypass it:

Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] you added [/COLOR]as  the default ( and not the "Wine" that's already there).

Now double click the "non-executable" *.exe file and see if it runs.

---

### Post by gc2712 on 2011-03-10
Many thanks for the responses. I appreciate the assistance.

I tried yesrno's solution already, thats what I meant by using cli to chmod. It reverts immediately to non executable.

bob-linux-user: The external HDD IS already ntfs formatted (This may even be the problem!).

Hadn't tried Morbius1's solution before, but that didn't work either. 

As it all works as root user its almost certainly a 'permissions thing'. Is there any way to change permissions on an external usb drive that is ntfs formatted?

---

### Post by Morbius1 on 2011-03-11
> Is there any way to change permissions on an external usb drive that is ntfs formatted?     Sure, write your own udev rule for these devices.

But like I said wine doesn't care if the exe is executable. Perhaps if you went to the source of the problem instead of using the easier method it will work better for you:
> **Curisu said:**
> 
> Originally Posted by Morbius1 View Post
The irony of all this is that wine doesn't care if it's executable. Wine is incapable of determining if a file has a Linux executable bit set. Wine isn't stopping you from running an exe file Ubuntu is through something called "cautious-launcher".

[COLOR=Blue]Open up "Properties" on /usr/share/applications/wine. The first thing you see in the Command Box is "cautious-launcher".
[/COLOR] 
Now go to /usr/bin/cautious-launcher - it's a script that checks to see if it has a Linux executable bit set.

If you right click an *.exe file and select Properties -> Open With -> Add -> Use a custom command > type in: wine
In the "Open With" tab mark the "wine" you added as the default ( from the Wine that's already selected) and theoretically every time you run an exe it should select the wine without the cautious launcher script.
Thanks Morbius; [COLOR=Blue]Opened a root privileged file browser with "gksudo nautilus" command in Terminal. From that window that popped up from the "gksudo nautilus" command, opened /usr/share/applications/wine and changed the "Command" box in "Wine Windows Program Loader" from "cautious-launcher %f wine start /unix" to "wine start /unix".[/COLOR] Now everything in I try to launch that is a .exe file starts up without a hitch as long as it works in Lunix.



Edit 2 regarding my original post:
I guess since I found out that changing the command area in the "Wine Windows Program Loader" under "Properties"(when run as a root user) from "cautious-launcher %f wine start /unix" to "wine start /unix" will start up program with Wine without the "executable bit" warning coming up, I suppose this thread is solved but I'd still like to know if anyone knows any answer regarding my first edit. Thank you.

---

### Post by gc2712 on 2011-03-12
Many thanks Morbius1 for your follow up. I tried your last solution - still no go. But I then discovered the cause of the problem. I tried running other *.exe programs from the same external drive and they worked! It turns out that I had installed a beta version of Portable Apps which works in Windows, but not in wine. (I had forgotten I installed a beta). So I reinstalled the stable version and lo! It all works as expected.

I am grateful for the solution to the nagging about "executable bit" that has arisen in recent versions of Ubuntu. Making that change to the wine loader properties was really worth it. Sorry about the 'red herring' chase though from my incorrect diagnosis. Help of everyone greatly appreciated.

---

