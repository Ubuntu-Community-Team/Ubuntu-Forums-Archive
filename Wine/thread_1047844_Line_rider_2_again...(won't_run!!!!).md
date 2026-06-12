---
title: "Line rider 2 again...(won't run!!!!)"
date: 2009-01-22
forum: Wine
---

### Post by Hyper Tails on 2009-01-22
Hi I have intreid ibex and I want to run line lider 2 in it and every time i do it it shows a little retangle and doeses nothing at all

same thing on laptop
help please

---

### Post by hikaricore on 2009-01-22
Have you changed anything since your issue was solved back then?

[http://ubuntuforums.org/showthread.php?t=952049](http://ubuntuforums.org/showthread.php?t=952049)

---

### Post by Hyper Tails on 2009-01-22
yes i clicked on the linerider2.exe and it did the same thing
i'll do this torrow because i'm off to bed and I got school also

---

### Post by Hyper Tails on 2009-01-23
time for a bump

---

### Post by Hyper Tails on 2009-01-23
.............................................

---

### Post by cogadh on 2009-01-23
More than 1 bump in a 24 hour period is too much. Be patient, I sure someone will respond soon enough.

In fact...

Before anyone can actually help you, you need to provide more (useful) information:
- What version of Wine are you using
- Does your PC actually meet the requirements for the game (other than the OS, obviously)
- Have you tried running the game from the terminal and if so, please post the terminal output
- You never actually answered hikaricore's question

---

### Post by Hyper Tails on 2009-01-23
> **cogadh said:**
> More than 1 bump in a 24 hour period is too much. Be patient, I sure someone will respond soon enough.

In fact...

Before anyone can actually help you, you need to provide more (useful) information:
- What version of Wine are you using
- Does your PC actually meet the requirements for the game (other than the OS, obviously)
- Have you tried running the game from the terminal and if so, please post the terminal output
- You never actually answered hikaricore's question

I got 1.1.13
I have the required hardware
and I don't know how to run it through terminal

---

### Post by AlexMono94 on 2009-01-23
To run from the terminal:

Open a terminal
Navigate to the directory where linerider2.exe is located (cd <directory> to go to a directory and "cd .." to go back)
then type "wine linerider2.exe"

---

### Post by Hyper Tails on 2009-01-23
```
root@liam-desktop:/home/liam# wine LineRider2.exe
wine: created the configuration directory '/root/.wine'
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/root/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\LineRider2.exe": Module not found
root@liam-desktop:/home/liam# err:seh:setup_exception_record stack overflow 864 bytes in thread 000b eip 7bc3c474 esp 00240fd0 stack 0x240000-0x241000-0x340000


```
is this correct?

---

### Post by cogadh on 2009-01-23
That's the output we were looking for, but something is wrong with it. For some reason it has created the .wine directory in root's home directory instead of yours. Also, the game should not be installed in "/home/liam" it should be somewhere like "/home/liam/.wine/drive_c/Program\ Files/LineRider2".

How did you install the software?

---

### Post by Hyper Tails on 2009-01-23
I did it from the disk

---

### Post by hikaricore on 2009-01-23
You're being too vague.  Please provide more detail.

Also just curious why in the smeg are you running wine as root?

After trying the instructions you were given about how to properly run the title from it's own folder what results did you get?
Terminal output, ect.

---

### Post by Hyper Tails on 2009-01-23
how do i set wine to run not as root?

---

### Post by hikaricore on 2009-01-23
You're logged into X or possibly just the terminal as root.
I have no idea why you would do either to run WINE but it's not recommended.

Try the method of running the game from it's own directory in a terminal please, you're avoiding the info provided simply because you don't care to do what's suggested.
Situations like this usually end with people no longer assisting you.

---

### Post by Hyper Tails on 2009-01-23
to be honest i'm trying my hardest to do the cd thing because i put the place of the file and it keeps showing up as so such dicotary of file

---

### Post by Hyper Tails on 2009-01-23
okay I had to create a short cut of the linerider 2 files in my home folder and here's the results
```
liam@liam-desktop:~$ cd LineRider2
liam@liam-desktop:~/LineRider2$ wine LineRider2.exe
fixme:shdocvw:PersistStreamInit_InitNew (0x133298)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32fb10:3; TargetFrameName 0x32fb00:8)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 8007007e

```

---

### Post by cogadh on 2009-01-24
You're missing the point. It appears that you have not installed LineRider correctly at all because it seems to be installed in a .wine directory that belongs to root and not your user. Until you configure Wine properly for your user and then install the game properly, anything you try to do is not likely to work at all.

To configure Wine correctly, log in to your normal user account, open a terminal and run "winecfg". Don't use the "sudo" command with it at all, otherwise you will create a similar problem to the one you already have. After you have configured Wine, install the game just like you would if you were installing it on Windows (find the setup.exe file on the install disk and double-click it) or use the terminal to install it:
```
wine /media/cdrom/setup.exe
```
Obviously if the installation setup executable has a different name or if your CD/DVD drive mounts in a different location, you will need to adjust that path to match it. Make sure you follow any of the additional instructions from your original thread on this subject, otherwise the game will not work:
[http://ubuntuforums.org/showthread.php?t=952049](http://ubuntuforums.org/showthread.php?t=952049)

After you have done that, try running the game again and see what happens

---

### Post by Hyper Tails on 2009-02-09
i tried that thing and still won't work
is it just me or is it my graphics card

graphics card: ati redaon hd 3650

---

### Post by Hyper Tails on 2009-02-10
.....................................

---

