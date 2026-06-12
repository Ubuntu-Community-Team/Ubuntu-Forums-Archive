---
title: "Ubuntu 64 and Steam symlinking"
date: 2009-10-03
forum: Wine
---

### Post by Weidbrewer on 2009-10-03
Okay, this goes around the bend a few times.  I'm looking to set up a Left 4 Dead dedicated server, for which I need Steam.  Also, I don't really have space on the drive that houses my home directory.  Now, when I was running Ubuntu 8.10 32-bit, I had no problem doing this by simply moving the drive_c folder where I wanted and symlinking it.  However, on the 64-bit version, I can't get Steam to startup this way.  (works fine when housed in the home directory.)  I accomplished the linking with the following:

Moving just the drive_c:

```
ln -s /media/raid/drive_c /home/myusername/.wine/ 

```

When that didn't work, I tried migrating the entire wine folder:

```
ln -s /media/raid/.wine /home/myusername/

```

Neither of these worked.  A box would appear on my task bar to say it was loading, it would sit there a bit, then go away.  Running from the command line gets me:

```
*****@******:~$ wine "C:\\Program Files\\Steam\\steam.exe" 
wine: Unhandled page fault on execute access to 0x0048720d at address 0x48720d (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x0048720d in 32-bit code (0x0048720d).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0048720d ESP:0032ff0c EBP:0032ffe8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8b6ff4 ECX:96f58c25 EDX:00000000
 ESI:0048720d EDI:7ffdf000
Stack dump:
0x0032ff0c:  7b879028 7ffdf000 00000000 00000000
0x0032ff1c:  00000000 00000000 00000000 00000000
0x0032ff2c:  ffffffff 7b8790b0 7b845ef0 7b8b6ff4
0x0032ff3c:  ffc60602 00000018 0032ffe8 7bc4a2d2
0x0032ff4c:  11252825 00000000 00000000 00000000
0x0032ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x0048720d EntryPoint() in steam (0x0032ffe8)
  2 0xf7e0fd77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0048720d EntryPoint in steam: call	0x004952bf
Modules:
Module	Address			Debug info	Name (80 modules)
PE	  400000-  530000	Export          steam

```


So, it looks like there might be something there with the 32 vs 64, but I don't know what.  Any help would be awesome.

---

### Post by hal10000 on 2009-10-03
> When that didn't work, I tried migrating the entire wine folder:

Code:

ln -s /media/raid/.wine /home/myusername/



Where is your .wine directoy located? I suppose it is in our home directory ([COLOR="Red"]/home/yourname/.wine[/COLOR])

You can move your whole .wine folder to your raiddrive:
```
sudo mv /home/yourname/.wine /media/raid
```
and then make a symlink that points to this new location:
```
ln -s /media/raid/.wine /home/yourname
```
Take in mind that the correct syntax for the ln -s command is ```
 ln -s SOURCE_DIR DESTINATION_DIR
```

---

### Post by beastrace91 on 2009-10-03
Might I suggest moving just the Steam folder from your ~/.wine/drive_c/Program\ Files/? This is how I run my Steam games (including L4D) because my main partition is only 80 gigs and my Data partition is 190.

Also just as an FYI you do not need Steam installed to [run a dedicated server](http://www.left4deadforums.com/1187-left-4-dead-linux-server-guide.html). That link talks about settings a srcds via SSH but it is easily adjusted for use locally.

EDIT: Also you are using the wrong syntax for symlinking, it should be like this to move your whole Wine folder: ```
ln -s /media/raid/.wine ~/.wine
``` And your raid partition, what file format is it?

~Jeff

---

### Post by Weidbrewer on 2009-10-04
> **beastrace91 said:**
> Might I suggest moving just the Steam folder from your ~/.wine/drive_c/Program\ Files/? This is how I run my Steam games (including L4D) because my main partition is only 80 gigs and my Data partition is 190.

Same result.

> 
Also just as an FYI you do not need Steam installed to [run a dedicated server](http://www.left4deadforums.com/1187-left-4-dead-linux-server-guide.html). That link talks about settings a srcds via SSH but it is easily adjusted for use locally.

Yeah, I had seen that tutorial...thing is, I have other Steam products I want to be able to use on this computer, necessitating a working Steam client.

> 
EDIT: Also you are using the wrong syntax for symlinking, it should be like this to move your whole Wine folder: ```
ln -s /media/raid/.wine ~/.wine
``` 

Same result.  Steam tries to start and then just...doesn't.

> 
And your raid partition, what file format is it?


JFS.


Again, to point out:  I'm using 64-bit now.  Everything worked on 32 using my original steps.  I'm really suspecting that has something to do with this, but I'm not sure what.

---

### Post by beastrace91 on 2009-10-04
Alrighty well I am a bit lost then. I have a very similar setup on my Sager laptop (also on Jaunty 64bit). Also are you sure this is an issue with symlinking and not your Wine?... Does loading Steam work when you do it from your ~/ directory?

~Jeff

---

### Post by renkinjutsu on 2009-10-04
your syntax for `ln -s` was perfectly correct.. the problem isn't your symlinks.. it's something else.. Do you have 32-bit wine installed (do they even have a 64 bit version?) .. is your RAID NTFS? i remember wine had problems with NTFS

---

### Post by Weidbrewer on 2009-10-04
First off, this is my first post while tailgating.

Yes, Steam works fine when not symlinking...now, maybe it has something to do with 8.10 vs Jaunty, but I don't think so.

---

### Post by Weidbrewer on 2009-10-04
> **renkinjutsu said:**
> your syntax for `ln -s` was perfectly correct.. the problem isn't your symlinks.. it's something else.. Do you have 32-bit wine installed (do they even have a 64 bit version?) .. is your RAID NTFS? i remember wine had problems with NTFS

Drive is JFS.  I don't think there is a 64 bit version, and my error above seems to point to 32 being part of the problem.

---

### Post by renkinjutsu on 2009-10-04
you have steam running on 8.10?

Try going on your 8.10 install and repeat exactly what you did with your 64bit (Jaunty?) system

symlink your steam folder...

see if wine runs it..

---

### Post by Weidbrewer on 2009-10-05
> **renkinjutsu said:**
> you have steam running on 8.10?

Try going on your 8.10 install and repeat exactly what you did with your 64bit (Jaunty?) system

symlink your steam folder...

see if wine runs it..

I'm *only* running 8.10 on this machine.  No Jaunty installed.

---

### Post by Weidbrewer on 2009-10-07
I just tried uninstalling Wine and Steam, then reinstalling them.  This time, I installed Steam in drive_c rather than drive_c/program files.

Tried symlinking again, and once again, it will not start.  Works fine when not symlinked.

---

### Post by NightMKoder on 2009-10-07
Just install steam like:

WINEPREFIX=/media/raid/.wine_steam wine Setup.exe

No need to try hacking it together yourself.

---

### Post by Weidbrewer on 2009-10-07
Is...that a command line command?  I'm sorry, I don't know what your post means.  (Thanks for chiming in.)

---

