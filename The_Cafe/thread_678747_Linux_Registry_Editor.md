---
title: "Linux Registry Editor"
date: 2008-01-26
forum: The Cafe
---

### Post by Bungo Pony on 2008-01-26
I don't know if this exists, but it would be REALLY useful if it did.

Last night, my wife booted into Windows on my PC. She usually does it to play one game that won't run on her PC. Anyway, I don't know what she did, but I got infected with a really nasty piece of malware. So, I'm currently in Linux cleaning it out :D

Anyway, I'll probably end up back in Windows to manually fix the registry. It would make things REALLY easy if there was a Windows Registry Editor for Linux. Does such a thing exist?

---

### Post by forrestcupp on 2008-01-26
I wonder if you could run regedit with wine.  I know wine has its own regedit, so maybe you could run the Windows one with it.

---

### Post by LaRoza on 2008-01-26
Did you make any restore points? They are just backups of the registry.

---

### Post by Bungo Pony on 2008-01-26
Well, finally got the bloody thing removed. What a pain. In case you're wondering, it was storageprotector.com. I couldn't even run HiJackThis.

After seeing the infections, it looks like my wife was using IE, even though I have Opera installed. Perhaps I should install Firefox for her to use (which she likes). Might save me a headache or two in the future.

Just another reason for my slow migration to Linux. Unfortunately, I was getting that damn Gnome error again that I've been having problems with, so that's why I booted into Windows. Even though both OSes have their faults, it's Windows that costs me more time, not Linux.

And I may just try running regedit in Wine :D

---

### Post by Bungo Pony on 2008-01-26
Just tried running RegEdit with Wine. By default it loads up the Wine Registry. I'm guessing it's possible to import the real Windows registry, but I don't know where Windows stores it.

---

### Post by gn2 on 2008-01-26
> **Bungo Pony said:**
> Perhaps I should install Firefox for her to use (which she likes).

Good idea, if you install the Firefox IETab add-on you can run Windows Update through it, so you can totally remove Internet Explorer altogether.

---

### Post by jrusso2 on 2008-01-26
> **gn2 said:**
> Good idea, if you install the Firefox IETab add-on you can run Windows Update through it, so you can totally remove Internet Explorer altogether.

Not so sure you can remove IE entirely as it is used in many other applications including Firefox IE Tab

---

### Post by phrostbyte on 2008-01-26
Yes, it's called gconf-editor  :)

But remember Linux is not Windows! The same concepts aren't always there. In the case of gconf, only Gnome applications use it. KDE and most of Linux use simple text files for configuration.

---

### Post by LaRoza on 2008-01-26
> **phrostbyte said:**
> Yes, it's called gconf-editor  :)

But remember Linux is not Windows! The same concepts aren't always there. In the case of gconf, only Gnome applications use it. KDE and most of Linux use simple text files for configuration.

The title was misleading. The OP wants to edit the Windows registry from Linux.

---

### Post by popch on 2008-01-26
You can backup and restore the Windows registry with Linux if you have a dual boot setup or if you run Windows in a virtual machine, I think. That's something which can be somewhat difficult to do in Windows, especially the restoring.

I don't know about an editor, though.

---

### Post by forrestcupp on 2008-01-26
> **Bungo Pony said:**
> Just tried running RegEdit with Wine. By default it loads up the Wine Registry. I'm guessing it's possible to import the real Windows registry, but I don't know where Windows stores it.

Did you use the wine version of regedit, or did you actually navigate to  regedit.exe on your Windows partition and run it with wine?

---

### Post by Bungo Pony on 2008-01-26
> **forrestcupp said:**
> Did you use the wine version of regedit, or did you actually navigate to  regedit.exe on your Windows partition and run it with wine?

First, I navigated to my Windows directory using the terminal. When I saw that the Wine registry loaded instead of the Windows one, I tried doing a right-click in Nautilus and "run with" which also brought up the Wine registry.

BTW, I am running a dual boot system.

---

### Post by hhhhhx on 2008-01-26
i would probably just reinstall wondoze

---

### Post by Christmas on 2008-01-27
As far as I remember the Windows registry is kept in several files inside c:\windows or c:\windows\system (don't know the exact names). So you can probably edit them manually from Linux or if they are in some binary form use Wine's registry editor.

---

### Post by LaRoza on 2008-01-27
> **Christmas said:**
> As far as I remember the Windows registry is kept in several files inside c:\windows or c:\windows\system (don't know the exact names). So you can probably edit them manually from Linux or if they are in some binary form use Wine's registry editor.

They are in binary form.

---

### Post by Antman on 2008-03-25
Hmm... just found this thread. I am looking for a way to edit the Windows registry from linux too. 
Hmmm... I guess I could try and find a windows program to do it and just run it with Wine?!? hmmm

---

### Post by regomodo on 2008-03-25
there must be a form of doing so as there is a linux live cd that can wipe administrator passwords and other such user account settings. I'll try and find the live-cd distro and they may have info on how they edit the registry

[edit] [Found it]("http://home.eunet.no/~pnordahl/ntpasswd/"). It apparently is an alomost fully-fledged registry editor as well. I've only used it to reset passwords

---

### Post by BDNiner on 2008-03-25
If you have a second windows computer with a different IP address you can connect to a network registry. it is in the file menu of regedit. I have done this across a VPN from South Florida to a computer in Tennessee. I don't know if regedit in wine can do this because i don't have it installed.

---

### Post by Bungo Pony on 2008-03-25
> **regomodo said:**
> there must be a form of doing so as there is a linux live cd that can wipe administrator passwords and other such user account settings. I'll try and find the live-cd distro and they may have info on how they edit the registry

[edit] [Found it]("http://home.eunet.no/~pnordahl/ntpasswd/"). It apparently is an alomost fully-fledged registry editor as well. I've only used it to reset passwords

Wow, thanks for posting that! I just may give it a try.

I've pretty much left Windows to rot until Hardy comes out, and I'll re-do my whole PC. But that utility may be useful when I have to fix other people's PCs.

---

### Post by ice60 on 2008-03-25
this is a very good registry editor, it might run with wine?? it's about 100 times faster then regedit.
[http://www.resplendence.com/reglite](http://www.resplendence.com/reglite)

---

### Post by Bungo Pony on 2008-03-25
> **ice60 said:**
> this is a very good registry editor, it might run with wine?? it's about 100 times faster then regedit.
[http://www.resplendence.com/reglite](http://www.resplendence.com/reglite)

The problem is which registry will it read? The one in Windows, or the one Wine uses? When I ran Regedit in Wine from the windows directory, it loaded up Wine's registry.

---

### Post by thisllub on 2008-03-25
> **Bungo Pony said:**
> 
Just another reason for my slow migration to Linux. Unfortunately, I was getting that damn Gnome error again that I've been having problems with, so that's why I booted into Windows. Even though both OSes have their faults, it's Windows that costs me more time, not Linux.

And I may just try running regedit in Wine :D

I have been running Linux since SUSE 6 and have never had a trouble free X system. 
Until I started running Openbox.



The Windows registry is in windows/system32/config
Windows opens it exclusively so you can't copy it while windows is running.


I believe it may be possible to edit it in Wine by copying it over Wine's registry but if the registry is corrupt it won't work anyway.

You are better to copy a non corrupt hive file e.g. software.sav 
like this

I run XP in VirtualBox so I set my XP VM to boot from a Ubuntu ISO. This gives me a Ubuntu VM with an XP hard disk.
I boot the XP machine with a Ubuntu CD and copy the hive files from the Ubuntu / XP VM via the network.

It does work but some, many or all of your Windows settings will be screwed.

---

### Post by ice60 on 2008-03-26
> **Bungo Pony said:**
> The problem is which registry will it read? The one in Windows, or the one Wine uses? When I ran Regedit in Wine from the windows directory, it loaded up Wine's registry.

that's what i was thinking too, i was going to say you can just run regedit from the CLI and it will open wine's own regedit, but it does the same thing. but, i'm sure you can tell it which registry to open because registry editors aren't connected to the registry, they just read the registry binary blob. there should be a switch you can use to point the reg editor to the registry you need to read.

here's the first pages i opened for 'edit the windows registry remotely', there are lots more. it should allow you to associate the editor to a non local registry. you should be able to just run wine's native regedit by typing **regedit** from a terminal.
[http://docs.rinet.ru/Registratura/htm/ch11.htm](http://docs.rinet.ru/Registratura/htm/ch11.htm)
[http://support.microsoft.com/kb/314837](http://support.microsoft.com/kb/314837)

---

### Post by jonathan morales on 2009-10-02
I got this working, so here's a simple how-to:

1) copy regedit32.exe from c:\windows on a real windows machine to the /home/user/.wine/drive_c/windows directory

2) copy these libraries from c:\windows\system32 on a real windows machine: authz.dll, alcui.dll, ulib.dll, clb.dll. They go to the ./wine/drive_c/windows directory also

3) run it in a terminal by wine regedit32.exe. When you get in, you can edit other registries by loading a hive. Just go to a key where the option under file>load hive option is allowed (for example it gives you the option to load a hive under the <user> key)- then navigate your way onto the windows file system in question, make your way over to c:\windows\system32\config\ and load the hive you need to mess with (e.g. sam for user account information, software for software, etc.)

This is the real windows registry editor, rather than a dumbed down version like the one that wine has by default. Now if somebody would put this on a live linux cd, along with gparted it would blow away even the ultimate boot cd in a computer technicians toolkit.

---

### Post by allenwjones on 2009-10-14
[SIZE="4"]Hello![/SIZE]

I have scoured the interweb for some means to export specific registry keys (such as drive mappings and network printer locations) for backup from linux.

Your solution (as listed above) seems to be a good way to edit the registry from linux (using the GUI) but have you attempted to export keys using the regedit command modifiers? My goal would be to automate this using a BASH script. However, if I cannot specify *which* registry to modify, this solution may not work.

I will be testing your solution and will post any successes I have with the command line, but it would be nice to have confirmation from someone with more experience..

[SIZE="4"]Thanks![/SIZE]

---

### Post by gsiliceo on 2009-12-03
@jonathan morales

It doesnt work anymore in 9.10 =( i did all the steps, copying files from my windows xp partition to the wine directories and the load hive option doesnt appear in any of the registry keys.

By the way you made a little mistake is not alcui.dll but aclui.dll and is not regedit32.exe but regedt32.exe.

I even removed the regedit.exe from wine directory and still nothing.

Thanks anyway i'll keep looking for a simple registry editor that works in wine.

---

### Post by gsiliceo on 2009-12-03
OMG i deleted all regedit.exe and regedt32.exe from all wine directories and when i issue wine regedit still opens the dumbed down version! wtf what is it loading?

---

### Post by Psumi on 2009-12-03
> **Bungo Pony said:**
> Last night, my wife booted into Windows on my PC. She usually does it to play one game that won't run on her PC. Anyway, I don't know what she did, but I got infected with a really nasty piece of malware. So, I'm currently in Linux cleaning it out :D

Says the man with malware in his avatar.

---

### Post by RiceMonster on 2009-12-03
> **Psumi said:**
> Says the man with malware in his avatar.

Chance the avatar is used for humorous reasons: 0%


Also, old thread is old

---

### Post by Psumi on 2009-12-03
> **RiceMonster said:**
> Also, old thread is old

Tell that to gsiliceo

---

### Post by forrestcupp on 2009-12-03
Interesting necroposting.

I was the first poster! \\:D/

---

### Post by Psumi on 2009-12-03
> **forrestcupp said:**
> Interesting necroposting.

I was the first replier! \\:D/

fixed.

---

### Post by pirulo on 2010-01-14
The utility "Offline NT Password & Registry Editor" has such feature. It can be found at :

[http://pogostick.net/~pnh/ntpasswd/]("http://pogostick.net/~pnh/ntpasswd/")

The address has changed since last post !

---

### Post by tarator on 2010-01-20
I used PCRegedit ([http://www.pcregedit.com/](http://www.pcregedit.com/)) to edit my Windows Registry.
(I couldn't use the Windows built-in regedit because of a login/logoff-loop.)

This program is freeware.

It worked great for me!!!

It's a small Linux Distribution which can't do anything except editing the windows Registry.

Just download the .iso file, burn it on CD and start from CD.

:popcorn:

---

### Post by MasterNetra on 2010-01-20
Just a thought. Prehaps adjusting wine and its C: drive to that of the windows partition might of done the trick just a thought...

---

### Post by CJ Master on 2010-01-20
The thread that **just won't *die***.

---

### Post by zx5000 on 2010-01-27
Ah yes as long as the windows registry exists so will the desire for a solution.

**Reged**
I have tried reged but it is very clumsy, crashes often and some documented features just don't work. For example the help states you can get all the keys in the hive with the . designator but then it complains that it cannot find key ".".

```

reged version 0.1 080526, (c) Petter N Hagen
-x <registryhivefile> <prefixstring> <key> <output.reg>
   Xport. Where <prefixstring> for example is HKEY_LOCAL_MACHINE
   <key> is key to dump (recursively), . means all keys in hive

-e <registryhive> ...
   Interactive edit one or more of registry files
-v : More verbose messages

```

Reged does come with the source so I plan to look at extending it's capabilities to add a batch mode to it.

**PCRegedit**
I downloaded PCRegedit and it's good if you want a bootable CD with a GUI. It did write to my XP's dirty even though I didn't save any changes bit thus forcing a CHKDSK cycle on next boot. I wonder what else it did?

Neither offer a search function and PCRegedit does not export or import.

That's my two bits.

---

### Post by Elfy on 2010-08-01
Thread closed - necro.

---

