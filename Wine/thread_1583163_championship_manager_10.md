---
title: "championship manager 10"
date: 2010-09-27
forum: Wine
---

### Post by percyhahn on 2010-09-27
Hi everyone,
   im relastively new to ubuntu, and im not very good with it yet. however im not bad with windows, so am quite competant...ish at computing itelf.
    when i got rid of windows, i put all files i wanted to keep onto usb sticks.
     championship manager was one of them. it has a no cd crack, as i the disk no longer works.
    on ubuntu, i extracted the file off the usb into a folder, and then extracted it. theres an icon called cm2010.exe which is the install/play icon. however when i click it it comes with a message saying wine has blocked it, as it isnt marked as executable?
    i dont really know anything about using terminal, or even wine tbh so not sure how to get around it, but was wondering if anyone would know what i could do/try?
     cheers
          Pete

   ps if you need anymore info or anythning just ask :)

---

### Post by Silmeth on 2010-09-27
You need to set executable flag to the .exe file. You can do that by typing in terminal:
```
cd /path/to/directory/with/the/exe/file/
chmod a+x ./cm2010.exe
```

Or by right-clicking on the file icon, choosing preferences and setting executability there ;-).

---

### Post by percyhahn on 2010-09-27
thats great, cheers :),
   just another quick problem, which i suspect maybe the game itself, and not ubuntu, but it may be ubuntu.
   when i double click, a window opens, but then a 'fatal programm error' box come up saying an unknown error has occurred, no languages found?

---

### Post by Silmeth on 2010-09-27
Try running it from Terminal, with command:
```
cd /path/to/the/directory/of/the/game
wine ./cm2010.exe
```

And copy all the output you see in the terminal window. Maybe then somebody would know the problem and how to fix it. But, seeing it's quite new game, it is possible that the game won't run under wine or it would require much hacking around wine configuration and register.

Unfortunately wine isn't (yet) full implementation of Windows API and DirectX, so not everything works under it. But don't lose your hope, there is still a chance ;-).

---

### Post by percyhahn on 2010-09-27
peter@peter-laptop:~$ cd /path/to/the/direcotry/of/the/game
bash: cd: /path/to/the/direcotry/of/the/game: No such file or directory
peter@peter-laptop:~$ wine ./cm2010.exe
wine: cannot find './cm2010.exe'
peter@peter-laptop:~$ cd /path/to/the/directory/of/the/game
bash: cd: /path/to/the/directory/of/the/game: No such file or directory
peter@peter-laptop:~$ wine ./cm2010.exe
wine: cannot find './cm2010.exe'
peter@peter-laptop:~$ 

    im not sure if its an error on my part, but terminal couldnt find it?
   yeah iv read about wine not being perfect yet, but hopefully in time :)
   if i knew anything about programming, id try and help, but i dont know programming at all, wouldnt mind starting though

---

### Post by Silmeth on 2010-09-27
Yeah... you should replace these "/path/to/blablabla/" with actual path to the game :P. Like, I don't know, /media/pendrive/championship_manager, or /home/your_username/championship... whatever is correct on your computer.

/home/your_username/ is your home directory path, /media/ is the directory where all mounted pendrives, etc. directories are being put.

Learn about paths and filesystems on Linux (and Unix in general) systems ;-).

---

### Post by Joeb454 on 2010-09-27
Thread moved to **Wine** sub-forum

---

### Post by percyhahn on 2010-09-27
ok, when i try to start cm from terminal, it comes up with this error code
  peter@peter-laptop:~/Desktop$ cd /home/peter/Desktop
peter@peter-laptop:~/Desktop$ wine CM2010.exe
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
peter@peter-laptop:~/Desktop$ 

    also wine pops up as a blue screen, with an error  popup saying 'an unknown error has occurred, no languages found'
    it would be great if anyone knows what to do if anything, or has any suggestions.
   if not, hope this is helpful for a wine developer :)

---

