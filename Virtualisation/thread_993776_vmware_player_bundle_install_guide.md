---
title: "vmware player bundle install guide"
date: 2008-11-26
forum: Virtualisation
---

### Post by markg48 on 2008-11-26
download .bundle from vmware site open terminal then

cd /home/yourusername/Desktop

then 

if your vmware version is deferent name change it to that then do this

sudo sh VMware-Workstation-6.5.0-118166.i386.bundle

or

sudo sh VMware-Player-2.5.1-126130.i386.bundle

 enjoy

---

### Post by talsemgeest on 2008-11-28
Please mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by coloel22 on 2009-03-31
Thanks!

Jonatan.

---

### Post by Dennismb90 on 2011-01-13
> **markg48 said:**
> download .bundle from vmware site open terminal then

cd /home/yourusername/Desktop

then 

if your vmware version is deferent name change it to that then do this

sudo sh VMware-Workstation-6.5.0-118166.i386.bundle

or

sudo sh VMware-Player-2.5.1-126130.i386.bundle

 enjoy

Thanks:D

---

### Post by Looking4MyAnswers on 2011-04-11
Thanks a lot Markg48
:D

---

### Post by AmanJivan on 2011-07-31
markg48

I did what was suggested and it seemed pretty straight forward using Ubuntu 10.10 and trying to install VMplayer. 3.1.4.

Did the first command you recommended changing user name etc. and got no such file or directory

---

### Post by AmanJivan on 2011-07-31
1

---

### Post by ianp5a on 2012-03-13
Is there any way to install it directly from Nautilus?

---

### Post by dcstar on 2012-03-13
> **ianp5a said:**
> Is there any way to install it directly from Nautilus?
Create a Launcher with this:
```
gksudo "dbus-launch nautilus --no-desktop --browser"
```
Set the Executable attribute on the VMware file, then double-click it.

---

### Post by ianp5a on 2012-03-17
Thanks dcstar

I wasnt sure what to do with the code you wrote, but the tip about setting it as executable solved the problem:

[LIST=1]
[*]Right Click on the .bundle file
[*]Choose Properties
[*]Choose the Permissions Tab
[*]Tick the "Allow Executing file as program"
[*]Navigate up one folder level in Nautilus
[*]Right Click on it's containing folder and choose Open as Administrator. (to get admin permission)
[*]Double click the File
[*]Choose Run on the pop up dialog: The Program runs as expected
[/LIST]

None of that should be necessary though. It seems they did it in a way to put non techies off.

---

### Post by dcstar on 2012-03-17
> **ianp5a said:**
> 
.........
[LIST=1]
[*]Right Click on it's containing folder and choose Open as Administrator. (to get admin permission)
[/LIST]


Be aware that "Open as Administrator" is no longer available in Ubuntu 12.04, which is why people will need to create a Launcher for Root Nautilus with the code I placed above.

---

