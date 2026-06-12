---
title: "Safe to completely ditch explorer.exe&amp;co ?"
date: 2009-01-22
forum: Windows
---

### Post by BogdanV on 2009-01-22
First of all, I'm running Windows2000 along with Xubuntu. One of the things that still keep me on a M$ OS is an obsession of mine to try to make Windows as light and stable as much as my knowledge and skills allow.
    What I've done now was to rip-off IE and all of the MSHTML crap from Windows Setup thanks to HFSLIP and some special files and force Windows to run WinFile as main shell.
    With all this done, Explorer and all its extensions though, are still here.
    TBH, I don't need Windows's GUI and its functionality so I'd be more than happy to ditch it with all of its reg keys, inf, dll, etc. files.

   My question though is if Explorer and its components is needed by typical applications or is it "safe to remove" ?
   And if its safe to, could anyone tell me exactly what are all the files used/dependent on Explorer so that I may remove them completely from the Setup CD I'm compiling ?

 Thanks in advance!

PS. If anyone knows if progman.exe (win3.1 version) can run on win2k/similar, do tell.

---

### Post by donkyhotay on 2009-01-22
First of all, there is a BIG difference between explorer.exe and iexplorer.exe! If you go to the task manager and shut down explorer.exe you will essentially kill the entire GUI. On the other hand if you shut down iexplorer.exe then internet explorer will close. Unfortunately M$ likes to integrate internet explorer into EVERYTHING and while it's possible to remove, doing so does odd things to windows. The more recent the version of windows, the harder to remove internet explorer. You shouldn't remove explorer.exe as that *will* do bad things, in regards to removing iexplorer.exe you are on your own as I don't know enough but I would just leave it alone. If you want a lean mean machine that you can customize to your hearts content then install linux which is designed for doing stuff like that. With linux you can safely pull out any and all web browsers you don't want or even the GUI itself if you need that last bit of efficiency.

---

### Post by Giant Speck on 2009-01-22
It is possible to replace explorer.exe with a different GUI shell.  That's how shells like Talisman work.  They shut down explorer.exe and replace it with another process.

Try finding a lightweight shell and using that instead of removing explorer.exe altogether.

---

### Post by BogdanV on 2009-01-22
To donkyhotay:

I know the difference between iexplore.exe and explorer.exe, that's why I mentioned that I wanted to know if its safe to ditch the entire GUI (since explorer is not a file browser but the UI itself.The file browser is just a "Windows Explorer Command"). As for removing MSHTML from Windows, I've done it and tested it on a VM. Apart from replacing Add/Remove with the 9x HTML-free version and some other processes that I never really needed, it seems that there are no functionality/stability problems.


 To Giant Speck : 
 
 I have already replaced it with NT4.0's File Manager "WinFile.exe" as I've mentioned in my first post. The thing I wanted to do was to go a step further and completely remove Explorer since I won't be using it at all (ControlPanel can be accessed without Explorer, that being the only limitation I encountered -and solved).

---

### Post by donkyhotay on 2009-01-22
Sorry, I have seen many people ditch explorer.exe thinking "I don't need internet explorer" and be stuck without a GUI. I noticed you talking about removing IE and MSHTML and assumed you were making that mistake. If you don't need the GUI then I think it's ok but I'll admit I've never done that to a windows box before so I don't know if there are any other side effects if you replace with a different GUI.

---

### Post by TenPlus1 on 2009-01-22
When I had WinXP installed on my system I used bbLean as my front-end instead of explorer.exe, and in my opinion it was faster and a lot lighter plus the fact it could be highly customized...

Check out [www.boxshots.org](www.boxshots.org)

---

### Post by BogdanV on 2009-01-22
No problem. Thanks anyway for expressing your concerns.

---

