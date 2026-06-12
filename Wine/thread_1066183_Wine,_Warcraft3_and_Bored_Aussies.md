---
title: "Wine, Warcraft3 and Bored Aussies"
date: 2009-02-10
forum: Wine
---

### Post by WaLshy11 on 2009-02-10
Hey.

I am having some trouble getting Bored Aussies to work through wine. War3 by itself works fine, but BA doesnt.

The program I am getting is using a launcher to load BA. When I go to launch it, it say 'Could not start war3. Make sure the loader is located in the right directory' (something like that).
BUT
When I go to the folder, through browse wine > games > war3 etc and load BA from there, it works fine.

The loader command I am using is:
```
wine "/home/user/.wine/blah blah war3 directory/BA launcher" -opengl
```

If I use the same command but with the ordinary war3 launcher, it works fine.

BTW I have copied the BA files over again and installed the reg file.


AHhh wats going on?

---

### Post by moforilla on 2009-02-10
You should check out the thread on the BA forums for running warcraft 3 under wine. From what I can remember you don't use the BA loader. You need to add registry entries into wine for the BA server.

All you need is in the thread, search "wine" on BA forums.

---

### Post by WaLshy11 on 2009-02-10
Had a check and couldnt find anything of use there...

Everything works fine, its just when I create a shortcut (launcher) to the BA exe I get an error. When I run the BA exe direct (actually go into the war3 folder and click on the w3l.exe) it runs fine, but it will be a pain to do this all the time

---

### Post by WaLshy11 on 2009-02-11
bump~

---

### Post by WaLshy11 on 2009-02-11
So I tried the command

```
cd "/home/user/blah blah war3 directory" && wine w3l.exe -opengl
```

This looked promising but I get an error message saying:

There was error launching the application
Details: Failed to execute child process "cd" (No such file or directory)


Anyone got any other ideas?

---

### Post by tomd123 on 2009-02-11
> **WaLshy11 said:**
> So I tried the command

```
cd "/home/user/blah blah war3 directory" && wine w3l.exe -opengl
```

This looked promising but I get an error message saying:

There was error launching the application
Details: Failed to execute child process "cd" (No such file or directory)


Anyone got any other ideas?

umm why don't you do "cd pathtowar3" and then do "wine w31.exe"
and the path should not be within quotes... if you want spaces, put "\ " where ever there are supposed to be spaces in the pathname.

---

### Post by WaLshy11 on 2009-02-11
> **tomd123 said:**
> umm why don't you do "cd pathtowar3" and then do "wine w31.exe"
and the path should not be within quotes... if you want spaces, put "\ " where ever there are supposed to be spaces in the pathname.


Im trying to create a launcher im not running this in terminal..

---

### Post by hikaricore on 2009-02-11
> **WaLshy11 said:**
> Im trying to create a launcher im not running this in terminal..

Tell us the exact full path to WC3 and I'll tell you how to make a launcher.

---

### Post by WaLshy11 on 2009-02-11
> **hikaricore said:**
> Tell us the exact full path to WC3 and I'll tell you how to make a launcher.


/home/<username>/.wine/drive_c/Program Files/Games/Warcraft III/w3l.exe

---

### Post by hikaricore on 2009-02-11
> **WaLshy11 said:**
> /home/<username>/.wine/drive_c/Program Files/Games/Warcraft III/w3l.exe

Make a file called wc3.sh in your home directory and paste the following into it.

```
#! /bin/bash

cd /home/yourusername/.wine/drive_c/Program\ Files/Games/Warcraft\ III/
wine w3l.exe -opengl
```

You will need to set this file as executable either through the file dialog or from a terminal with: *chmod +x wc3.sh*

Then link to this file from a shortcut on your desktop.
Should work like a charm.

I know this isn't the only way to do this but it's a way to do it.  :p

---

### Post by WaLshy11 on 2009-02-11
Thanks heaps ill give it a shot :D

---

