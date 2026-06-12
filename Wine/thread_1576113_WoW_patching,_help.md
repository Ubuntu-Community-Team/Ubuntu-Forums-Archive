---
title: "WoW patching, help"
date: 2010-09-16
forum: Wine
---

### Post by Kareta on 2010-09-16
Having trouble patching :\.

Pictures of problem:

[IMG]http://i53.tinypic.com/24mgrpt.jpg[/IMG]

[IMG]http://i51.tinypic.com/t9ik4n.jpg[/IMG]



And when I decided to download the patch, when it finished I got this:
[IMG]http://i55.tinypic.com/abqvib.jpg[/IMG]


Someone please help.

---

### Post by cwwilson721 on 2010-09-16
They did the tools screwup again..

Do a search for "wow wine permissions patch" to find a solution

Basically, the patch changes your folder permissions, and now nobody has access to the folder and all subfolders/files.

You might need to change your launcher to 'wow.exe' instead of 'launcher.exe' too.

---

### Post by r+9 on 2010-09-16
find your wow folder (usually in your $HOME/.wine path)

go one level up and "chmod -R 777 World\ of\ Warcraft"

that will open the permissions wide.

---

### Post by r+9 on 2010-09-16
another trick that I haven't seen posted, 

for your "wow shortcut" 

wine explorer /desktop=wow,1400x900 wow.exe

this will allow you to alt+ctrl+(left/right) to another desktop 
allow you to alt-tab out of wow without it going to hell.

sub in your screen resolution and your wow-path of course.

---

### Post by Kareta on 2010-09-16
Works now, thanks for the help.

---

### Post by r+9 on 2010-09-16
Happy Harvest Festival!

---

### Post by cwwilson721 on 2010-09-16
The OP must be European, 'cuz the patch ain't going to us, yet..Just says "No data yet" or some other rigamarole.

Looking at WoW Patch Mirrors, only EU servers have an actual file to d/l

---

### Post by wahsape on 2010-09-29
Can someone be a little more clear on how to get to the World\ of \Warcraft folder?

How do you type it in a terminal?

$Home/.wine ???(have no idea how to navigate)

---

