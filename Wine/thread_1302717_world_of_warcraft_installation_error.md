---
title: "world of warcraft installation error"
date: 2009-10-27
forum: Wine
---

### Post by Kaffekop on 2009-10-27
Ok so I actually managed to get the installation going with wine *yay*, but now I keep getting the same error!

the installation stop and tells me that it could'nt read a specefic file (always a random one, and it has happened on 3 cd's so far!).

any ideas?

edit: btw I use Ubuntu 9.04 :-)

---

### Post by hikaricore on 2009-10-28
Copy the contents of the cds to one directory (for example your Desktop) and install from there.
Problem solved.

You probably have a cd drive that's not working 100%

---

### Post by Kaffekop on 2009-10-28
> **hikaricore said:**
> Copy the contents of the cds to one directory (for example your Desktop) and install from there.
Problem solved.

You probably have a cd drive that's not working 100%

its only with ubuntu that this problem happens.. but I've already tried the other method, and I get a whole different bug while doing that! (tries to find the install file in a system32 folder!??)

geez I've spend hours and hours on this so far :P

whenever I try to install from the downloadmanager or from having copied the contents of cd1 to my hd, I get the following error:

wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found

and yes I write the code properly, and yes I've tried to do it in other ways. I think theres a wrong configuration somewhere, or I'm missing something on my system. Someone was talking about graphics card? I have nVidea Gforce, so should that be a problem? Any special things to do in this case, that might solve my problem??

Kind regards

---

### Post by Kaffekop on 2009-10-28
cmon ive been staringh out in empty space for 3 days now. Everyone else can install wow so it must be some kind of ugly little thing that doesent work!!!!!!!!

when i "cd" it tells me "bash: <path> is a directory
or something like that..

please help im beginning to loose faith in this.. nothing works :(

---

### Post by Soulcage on 2009-10-28
No Installer.exe?
This may primarily be a Fuse problem, but may appear on other systems not using Fuse as well. Run the following command from a terminal: 
sudo mount -o remount,unhide /dev/cdrom

(copied from [http://www.wowwiki.com/Wine]("http://www.wowwiki.com/Wine"))

---

### Post by pedro_orange on 2009-10-29
> **Kaffekop said:**
> cmon ive been staringh out in empty space for 3 days now. Everyone else can install wow so it must be some kind of ugly little thing that doesent work!!!!!!!!

when i "cd" it tells me "bash: <path> is a directory
or something like that..

please help im beginning to loose faith in this.. nothing works :(

Install the game on Windows.
Copy C:\Program Files\World of Warcraft folder to an external USB disk
Boot into Linux
Copy that folder into home/<your_usrname>/.wine/Program Files/
Open a terminal and run WoW.exe under wine

---

