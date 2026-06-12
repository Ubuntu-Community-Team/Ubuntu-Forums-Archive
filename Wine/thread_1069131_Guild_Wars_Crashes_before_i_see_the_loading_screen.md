---
title: "Guild Wars Crashes before i see the loading screen"
date: 2009-02-13
forum: Wine
---

### Post by rasmus91 on 2009-02-13
Hello Again (yeah, i know I'm one of these annoying guys who needs a lot of help) 

But anyway:

I've now tried to install GW twice, once with wine... Just the normal wine. and now with playonlinux

With PlayOnLinux it seems to work better than on ordinary Wine, how ever:
When the game launches, the screen will blank for less than a sec, then I'll see the GW cursor, and then GW crashes (before I've seen the login screen). Then when the screen turns normal, the resolution will be 1024x768 instead of 1440x900...

I can't figure out on my own why this happens

the computer is: Dell Latitude E6400

(i found a [link]("http://k-disk.com/Linux/page.php?page=Linux:GuildWars") which told something about what to do, but the result remains the same)

Any questions? 

Any Suggestions?

Thanks in advance

---

### Post by binbash on 2009-02-13
can you post the terminal output after the crash?Also did you read the comments at appdb.winehq.org's guild wars entry?

---

### Post by rasmus91 on 2009-02-13
Yeah, read them. How to get terminal output?

---

### Post by betrunkenaffe on 2009-02-13
Make sure Compiz is off OR make sure that GW is opening in windowed mode. I ran into similar issues when I was opening fullscreen because there was a fight over the resolution that should be used. I resolved by disabling Compiz, opening, setting to windowed mode and then closing. Turned Compiz back on and opened again (in window).

Also, definately make sure you have all the settings set in regedit as winedb says.

---

### Post by rasmus91 on 2009-02-14
okay... I've tried turning the desktop effects off, and running in windowed mode, it doesn't help...

---

### Post by ironstorm on 2009-02-14
Try running it in a Wine Desktop window -> [http://ubuntuforums.org/showthread.php?t=498069&page=2#post6732983](http://ubuntuforums.org/showthread.php?t=498069&page=2#post6732983)

See if that works

---

### Post by rasmus91 on 2009-02-20
> Try running it in a Wine Desktop window -> [http://ubuntuforums.org/showthread.p...=2#post6732983](http://ubuntuforums.org/showthread.p...=2#post6732983)

See if that works

Did, its still just the same :(

---

### Post by NightMKoder on 2009-02-20
Console output would be nice. Open a terminal window and browse to the folder where you installed guild wars (ie /home/rasmus/.wine/drive_c/Program Files/Guild Wars). In other words, type "cd ~/.wine/drive_c/Program Files/" and then type "ls" and try finding where guild wars is. Then type "cd Guild Wars" or whatever you find and you should be in the game's folder. Then type "wine gw.exe" or whatever file guild wars uses to launch itself (use "ls *.exe" to find all programs in the folder).

Of course the above commands, without quotes. Also, in case you need to go one level higher, "cd .." works.

For more, I suggest [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands) .

---

### Post by rasmus91 on 2009-03-11
> Of course the above commands, without quotes. Also, in case you need to go one level higher, "cd .." works.

Hehe... Im not such a newb to BASH anymore... Infact i use it a lot because its a easy way to manage files. I'll give you an output as soon as possible... ;) 

I formatted since i had this problem, i haven't tried to install since. however, I will try again when i get the time.

you just want to see output of the "ls -F" command right?

---

### Post by rasmus91 on 2009-03-11
Sorry man can't open Gw.exe ... Yes the terminal gets some outputs, but the computer messes up and logs out before i can do anything at all is there a way to run the file without actually opening a window with the game in?

---

### Post by rasmus91 on 2009-03-14
This is my outputs by now : 
```
wine Gw.exe
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  481
  Current serial number in output stream:  481
```

---

### Post by rasmus91 on 2009-03-15
> Console output would be nice. Open a terminal window and browse to the folder where you installed guild wars (ie /home/rasmus/.wine/drive_c/Program Files/Guild Wars). In other words, type "cd ~/.wine/drive_c/Program Files/" and then type "ls" and try finding where guild wars is. Then type "cd Guild Wars" or whatever you find and you should be in the game's folder. Then type "wine gw.exe" or whatever file guild wars uses to launch itself (use "ls *.exe" to find all programs in the folder).

Of course the above commands, without quotes. Also, in case you need to go one level higher, "cd .." works.

For more, I suggest [https://help.ubuntu.com/community/Us...=BasicCommands](https://help.ubuntu.com/community/Us...=BasicCommands) .

okay, here is output: 
```

X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  481
  Current serial number in output stream:  481

```

I have no problems with the alsa Lib by now, i fixed it with: 
```
sudo modprobe snd-seq 
```

---

