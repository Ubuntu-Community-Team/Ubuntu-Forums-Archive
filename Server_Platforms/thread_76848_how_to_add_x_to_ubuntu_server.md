---
title: "how to add x to ubuntu server"
date: 2005-10-15
forum: Server Platforms
---

### Post by unarmedninja on 2005-10-15
I installed Ubuntu as a server to test it out and now I want to switch to the regular desktop mode.  How can I do this without reinstalling?

thanks.

---

### Post by DJ_Max on 2005-10-15
It would go something like [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

---

### Post by unarmedninja on 2005-10-15
thanks for the quick reply.  i tried those commands but it says im missing packages.  I've read those tutorials and they all seem to need the universe repository available in the sources.list.  I dont have internet working on my laptop where im trying to install (i need ndiswrapper).  Is there anyway around this?

---

### Post by TomB on 2005-10-15
You could probably try and upgrade like if you were tryingto upgrade from hoary to breezy, or if you haven't installed much, you could install breezy from scratch

---

### Post by az on 2005-10-16
[QUOTE=unarmedninja]thanks for the quick reply.  i tried those commands but it says im missing packages.  I've read those tutorials and they all seem to need the universe repository available in the sources.list.  I dont have internet working on my laptop where im trying to install (i need ndiswrapper).  Is there anyway around this?[/QUOTE]


You installed the server system from the cd and now you want to install the desktop.  Just log in and type

sudo apt-get install ubuntu-desktop

And you are done.  It will ask you to putin the cd and get the packages from there)

By the way, ndiswrapper is on the cd.  Just install the ndiswrapper-utils package and you are good to go

set up your wireless the usuall ndiswrapper way (ndiswrapper -i file.inf...blablabla)

---

### Post by unarmedninja on 2005-10-16
Hey, thanks for all the replies. The problem was that apt-get wasnt finding any packages on the cd so I used a combination of dselect and aptitude to install the gui separately.  Its running now but I have another problem with the cpu fan not working.  Ive tried disabling acpi in grub but that doesnt work.  This isnt related to server so i'll post this problem in another area.

---

