---
title: "Package Management for Windows"
date: 2009-07-04
forum: The Cafe
---

### Post by earthpigg on 2009-07-04
[http://win-get.sourceforge.net/index.php](http://win-get.sourceforge.net/index.php)

"
Win-get package manager for Windows

Win-get is a automatic software installer and package manager for Windows, inspired by Debian's apt-get tool. With win-get, downloading and installing an application to your computer is as simple as:

    win-get install firefox
"

how come projects like this haven't taken off in popularity and maturity?

---

### Post by dragos240 on 2009-07-04
DO they have a repository?

---

### Post by wojox on 2009-07-04
Never last. Windows people love point and double clicking.
You shouldn't add anything in C:\WINDOWS
That what environment variables are for.

---

### Post by tjwoosta on 2009-07-04
Id probably use this if theres a maintained and trusted repository, I cant find any informaiton about it though. 

Also the forums have been overrun with spam.

---

### Post by SunnyRabbiera on 2009-07-04
A package manager would be handy in windows though, I find linux package managers easier then .exe installers.

---

### Post by earthpigg on 2009-07-04
i noticed that their forum has been overrun with spam, too. i wasn't referring to that specific project - it is obviously dead. its predecessor, windows-get, is also dead.

making a package manager that is only friendly with open source doesn't seem so practical on a closed source operating system.

food for thought:

make the package manager's server only hold a list of where to download from, but not hold the actual software.

for example, typing 

```
winget install opera
```

would:

1) sync the source list with the winget servers
2) find where opera is located from that source list ([http://www.opera.com/blazibla/whatever/opera10.exe](http://www.opera.com/blazibla/whatever/opera10.exe))
3) ask the user which version s/he wants to download (community volunteers would be needed here to maintain this master list)
3) invoke wget for windows to download it
4) execute the opera setup.exe file
5) keep a log of where setup puts files and folders
5) once that is done, it would remove the setup.exe file

```
winget uninstall opera
```

1) launch the uninstaller for opera
2) once the uninstaller is done, reference the install log and tell the end-user what files where not removed
3) (maybe) give the user the option to remove those files



as i said, community volunteers would be needed to maintain the master software list containing software packages, and different versions.

---

### Post by 23meg on 2009-07-04
[QUOTE=earthpigg]how come projects like this haven't taken off in popularity and maturity?[/QUOTE]

Because the core strengths of centralized software distribution and management besides ease of installation (which is relative, and can be obtained through other means as well) are the notions of *trust* and *freedom*, which cannot exist in a proprietary and closed source platform the way we know them in the free software ecosystem. It's not possible to compile and package undisclosed code, and build a network of trust around it. It's not practically possible to gather thousands of binaries from different vendors with different restrictive licenses (a lot of which completely forbid redistribution through third parties, or subject it to various agreements) in a centralized repository of any significant size and popularity either.

It would be interesting to see a "straw man" effort, maybe a mockup, that would attempt to ship the most popular Windows software on the same scale of coverage as the Ubuntu repositories applied to the Windows ecosystem, or even precisely the same amount of coverage, in such a way. An interesting social experiment (to put it mildly) would be to apply the tired "too much choice" / "too many licenses" / "Linux is fragmented and that's why it will never blah blah" arguments against free software to the results that would ensue.

---

### Post by UbuWu on 2009-07-05
> **earthpigg said:**
> food for thought:

make the package manager's server only hold a list of where to download from, but not hold the actual software.


The [Filehippo updater]("http://filehippo.com/updatechecker/") does this more or less. It checks for updates for all free software you have installed and then presents you a list of links to the installers.

---

### Post by koleoptero on 2009-07-05
> **UbuWu said:**
> The [Filehippo updater]("http://filehippo.com/updatechecker/") does this more or less. It checks for updates for all free software you have installed and then presents you a list of links to the installers.

Yeah but the filehippo site doesn't have half as many apps as it should unfortunately.

---

