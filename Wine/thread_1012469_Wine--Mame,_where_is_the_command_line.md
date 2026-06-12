---
title: "Wine--Mame, where is the command line?"
date: 2008-12-15
forum: Wine
---

### Post by jukingeo on 2008-12-15
Hello all,

First off, I will open by saying that I DO have SDLMame running with WahCade (frond end) in Linux already.  So with that said, I know the first question would be, "Why run the Windows version in Wine if a Linux version exists"?

Good question.  The answer is this:

I found out that most versions of Mame (running under WinXP) following version .106 are power hogs and do slow the system down considerably.  I noticed that with versions .111 and .123 (which is also the same version as my SDLMame), audio stutters more with certain games (vector and Sega games) and vector games look horrible in comparison to using an older version (than .106) of Mame. Given that the older versions do not have this problem in Windows and they do run faster than the newer versions prompted me to try out Mame running under Wine


The version I have selected is version 0.100 because I am running this version in Windows XP and I like the way it runs.

Now, with MAME you need a command line "C" prompt to launch a rom with the program.

Naturally since the Terminal is pretty much Linux' command line, I tried running Mame through there first.

This is what I get in my Terminal:

geo@home:~$ wine mame pacman
wine: could not load L"C:\\windows\\system32\\mame.exe": Module not found
geo@home:~$ 

If I try to click on "Mame.exe" within my Wine C: drive folder the program comes up for a split second and then closes.  However, I know that regular Mame will do this if you do not specify a rom to load with Mame.exe.  So I am not sure if I am doing this right within the terminal.

According to Wine's website,  Mame has a platinum rating so even though my version is older I would assume that it should run.

Any advice would be appreciated.

Thank You,

Geo

---

### Post by asdfoo on 2008-12-16
> **jukingeo said:**
> Hello all,

First off, I will open by saying that I DO have SDLMame running with WahCade (frond end) in Linux already.  So with that said, I know the first question would be, "Why run the Windows version in Wine if a Linux version exists"?

Good question.  The answer is this:

I found out that most versions of Mame (running under WinXP) following version .106 are power hogs and do slow the system down considerably.  I noticed that with versions .111 and .123 (which is also the same version as my SDLMame), audio stutters more with certain games (vector and Sega games) and vector games look horrible in comparison to using an older version (than .106) of Mame. Given that the older versions do not have this problem in Windows and they do run faster than the newer versions prompted me to try out Mame running under Wine


The version I have selected is version 0.100 because I am running this version in Windows XP and I like the way it runs.

Now, with MAME you need a command line "C" prompt to launch a rom with the program.

Naturally since the Terminal is pretty much Linux' command line, I tried running Mame through there first.

This is what I get in my Terminal:

geo@home:~$ wine mame pacman
wine: could not load L"C:\\windows\\system32\\mame.exe": Module not found
geo@home:~$ 

If I try to click on "Mame.exe" within my Wine C: drive folder the program comes up for a split second and then closes.  However, I know that regular Mame will do this if you do not specify a rom to load with Mame.exe.  So I am not sure if I am doing this right within the terminal.

According to Wine's website,  Mame has a platinum rating so even though my version is older I would assume that it should run.

Any advice would be appreciated.

Thank You,

Geo

[http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

---

### Post by jukingeo on 2008-12-16
> **asdfoo said:**
> [http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

Thanx for the info.  I managed to get Mame to do "something", but apparently it isn't launching.

This is the output of my Terminal:

geo@home:~$ cd .wine/drive_c/Mame
[email]geo@home:~/.wine[/email]/drive_c/Mame$ wine mame starwars
Unable to open the keyboard device. (error 2)
136021.105   NOT FOUND                  
136021.214   NOT FOUND
136021.102   NOT FOUND
136021.203   NOT FOUND
136021.104   NOT FOUND
136021.206   NOT FOUND
136021.107   NOT FOUND
136021.208   NOT FOUND
136021.110   NOT FOUND
136021.111   NOT FOUND
136021.112   NOT FOUND
136021.113   NOT FOUND
ERROR: required files are missing, the game cannot be run.
Unable to close the keyboard device. (error 2)
[email]geo@home:~/.wine[/email]/drive_c/Mame$ wine mame.exe starwars
Unable to open the keyboard device. (error 2)
136021.105   NOT FOUND                  
136021.214   NOT FOUND
136021.102   NOT FOUND
136021.203   NOT FOUND
136021.104   NOT FOUND
136021.206   NOT FOUND
136021.107   NOT FOUND
136021.208   NOT FOUND
136021.110   NOT FOUND
136021.111   NOT FOUND
136021.112   NOT FOUND
136021.113   NOT FOUND
ERROR: required files are missing, the game cannot be run.
Unable to close the keyboard device. (error 2)
[email]geo@home:~/.wine[/email]/drive_c/Mame$ 

Now I know that this can't be rom information because that particular rom runs in Windows fine.

Edit:  I tried to execute it via the "path" method and that didn't work either however, the message was different:

geo@home:~$ wine start 'C:\Mame\mame.exe starwars'
fixme:exec:SHELL_execute flags ignored: 0x00000500
geo@home:~$ 

In this way a typical "Dos" window opened up to tell me it couldn't open the keyboard device.

Any ideas what is going on?

Thanx,

Geo

---

