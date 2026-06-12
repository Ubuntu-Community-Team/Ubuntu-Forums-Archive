---
title: "An idea on file-to-application matchup."
date: 2006-06-19
forum: The Cafe
---

### Post by prizrak on 2006-06-19
I recently ran into a wall in Dapper when I tried opening a .rar archive. The default install does not handle .rar files at all. I did find the rar and unrar packages in the repositories and installed them, file-roller even auto configured itself to use them as needed but it did give me an idea. 

You know how in Windows when you come across an unknown file type it gives you a choice of associating some program with it manually or searching the web for a program known to handle such a file. I thought about something similar for Ubuntu, I think it would be a pretty neat improvement if Ubuntu would give an option to search the repositories for the needed program and present the user with a list of suitable applications along with their description and an option to install on the spot. 

What do you guys think of the idea, I will attempt to create a poll (first time for me so may not work) and if the feedback is positive enough I'll submit it as a feature request into Launchpad.

---

### Post by benplaut on 2006-06-19
i'm not sure how the legality would work out with nonfree stuff (like rar)...

---

### Post by ssam on 2006-06-19
see [https://wiki.ubuntu.com/DesktopTeam/CommonInstallHook](https://wiki.ubuntu.com/DesktopTeam/CommonInstallHook)

---

### Post by prizrak on 2006-06-19
[QUOTE=benplaut]i'm not sure how the legality would work out with nonfree stuff (like rar)...[/QUOTE]
Well both free and non-free rar are in the repositories so they are legal I would assume. Also legality of things is up to the user, most of us install W32codecs as well as decss, which are illegal. 
> see [https://wiki.ubuntu.com/DesktopTeam/CommonInstallHook](https://wiki.ubuntu.com/DesktopTeam/CommonInstallHook)
Great minds think alike huh :)

---

### Post by Kimm on 2006-06-19
I personaly think that Nautilus has superb support in this area... perhaps not counting the downloading of new software part.

It seems like Nautilus allways knows what type of file it is dealing with... it never peeks at the file extention, and seems to allways just know what app should handle what file.

---

### Post by prizrak on 2006-06-19
[QUOTE=Kimm]I personaly think that Nautilus has superb support in this area... perhaps not counting the downloading of new software part.

It seems like Nautilus allways knows what type of file it is dealing with... it never peeks at the file extention, and seems to allways just know what app should handle what file.[/QUOTE]
File extensions mean alot less in Linux than they do in Windows. In fact they mean damn near nothing, you can change your .avi to anything you want and it will still be opened as a header is unchanged. Nautilus does handle file associations well, the only thing that's missing is the ability to install an application if nothing can handle the file.

---

### Post by bruce89 on 2006-06-19
That's how viruses on windows are opened by people, they just add a nice extension on top of the original one thus - Virus.exe.jpg, plus Windows hides the file extension by default.  I once thought that my sister's files all had no extentions, so added one, to find they then had 2.

---

### Post by nalmeth on 2006-06-20
I think this is pretty cool.

Maybe to get around restriction issue there would be a legal warning, and an option to view the licenses (in a browser) used by the codec.

All in all it would be a lot of work of course.

---

