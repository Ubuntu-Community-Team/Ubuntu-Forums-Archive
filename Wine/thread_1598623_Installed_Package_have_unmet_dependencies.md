---
title: "Installed Package have unmet dependencies"
date: 2010-10-16
forum: Wine
---

### Post by devpas on 2010-10-16
Hello,

I recently installed Ubuntu on my laptop

the version of Ubuntu is 10.04 Release (lucid).

I wanted to install Microsoft Office 2007 on Ubuntu, so after googling, i eventually found this particular website linked as below

[http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html](http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html)

the step one asked me to insert the following commands on the termimal

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/...t.d/hardy.list](http://wine.budgetdedicated.com/apt/...t.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo aptitude install wine

how ever since then i have been getting an error which says on the panel

"An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error:opening the cache(e:type'<html></html>' is not known on line 1 in source list/etc/apt/source.list.d/winehq.list, E:The list of source could not be read.)'This usually means that your installed packages have unmet dependencies"

when i right click and try to open the package manager or update manager, it doesnt work. 

Also i cant use the software source or Ubuntu Software Center.

Please Help

---

### Post by Quadunit404 on 2010-10-16
[http://wine.budgetdedicated.com/apt/...t.d/hardy.list](http://wine.budgetdedicated.com/apt/...t.d/hardy.list)
Your problem -----------------------------^

It's an incomplete ("crunched") URL. I don't know why whoever wrote that didn't notice that.

---

### Post by Soulcage on 2010-10-17
You need to install from the instructions on here [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb") installing either wine1.2 or wine1.3.
What you posted is for a much older version of ubuntu.

---

### Post by devpas on 2010-10-17
Well the problem that has happened is, i cant get use the Pacakge manager or update manager or software sources

Every time i try to do it, it blocks me.

i also tried physically deleting the file

etc/apt/source.list.d/winehq.list

but i cant delete the file

when i open the file with gpedit

d only content in the file was 

<html></html>

i presume there might be a link in between. 

Please Help

---

### Post by YokoZar on 2010-10-17
> **devpas said:**
> Well the problem that has happened is, i cant get use the Pacakge manager or update manager or software sources

Every time i try to do it, it blocks me.

i also tried physically deleting the file

etc/apt/source.list.d/winehq.list

but i cant delete the file

when i open the file with gpedit

d only content in the file was 

<html></html>

i presume there might be a link in between. 

Please Help

try:

sudo rm /etc/apt/sources.list.d/winehq.list
(enter password)
sudo apt-get remove wine

---

