---
title: "Trying to setup .NET Framework 3.5 SP1 error... Halp!"
date: 2009-12-27
forum: Wine
---

### Post by Toastytoes on 2009-12-27
Using wine in combination with X11 to run a .exe installer (on an intel mac, still in OSX :( ) for a program called "Warrior's Battle Cannon". Basically, the installer says that it is installing something called ".NET Framework 3.5 SP1". It runs, and at the end it says "An error occurred while installing system components for warriors battle cannon. Setup cannot continue until all system components have been successfully installed." When I click "Details" it says:

Component .NET Framework 3.5 SP1 has failed to install with the following error message:
'A failure occurred attempting to install .NET Framework 3.5 SP1.'

The following components failed to install:
- .NET Framework 3.5 SP1

See the setup log file located at 'C:\Windows\temp\VSD3439.tmp\install.log' for more information"

Does anyone know what to do here? I'm absolutely clueless. I'm a huge newbie when it comes to wine, and I would really like to run this program. Pleez help!

---

### Post by gsmanners on 2009-12-28
You could try doing the winetricks thing, but I doubt it will get you further:

```
wget http://kegel.com/wine/winetricks
sh winetricks dotnet20
sh winetricks dotnet30
```

That should get you up to .NET 3.0, but I don't know if 3.5 will work at this point.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10166](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10166)

---

### Post by Toastytoes on 2009-12-29
I'll give that a shot. Thanks!

---

### Post by Bwathke on 2010-01-18
Im having this problem also.... How far did you get? I cant even install 3.0 with winetricks.

---

### Post by Toastytoes on 2010-01-18
Well, I tried a bunch of stuff with winetricks, read up on a bunch of crap, etc... I gave up for a little while. I'm gonna give it another shot soon though. I'll let you know... :confused:

---

### Post by rocky5051 on 2010-01-19
It's not worth the effort at the moment. .NET 2.0 is still very buggy...I can't imagine how awful 3.0 and higher would work, if at all.

Your best bet would be to use Mono. That is installable via winetricks as well.

---

