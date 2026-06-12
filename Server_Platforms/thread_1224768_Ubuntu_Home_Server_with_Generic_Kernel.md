---
title: "Ubuntu Home Server with Generic Kernel"
date: 2009-07-27
forum: Server Platforms
---

### Post by Serangan on 2009-07-27
Hey,
 I have some questions that i would like answered

1) If in installed ubuntu home server and apt-get'ed the generic kernel, would i then get the power management features? 'Cause i have my server set to go to sleep when no other pc's are on, and it wakes via wol. I can't do this with the server kernel, but i also dont want any of the 'extras' that come with the generic kernel;
ie. OpenOffice.org etc.

2) I also have LVM set up. If i reinstall will I lose this setup? Is there some way (in needed) of keeping a copy of the lvm setup?

3a) Im getting an Intel Atom for my new server (this one [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3082](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3082) ), it's 64 bit capable, so would i need to install the 'netbook' install of ubuntu? Or will it be fine with 'desktop' or 'server'.

3b) Do I need 64bit? Im only going to have 2gig of memory, but if i have the capability of a 64bit system, should i take it?

Ah, i think that's all that i can think of for now.

Thanks in advanced.

---

### Post by paped on 2009-07-27
Re Q3a the Atom question I have a genuine Intel Atom board with the latest Ubuntu Server LTS loaded, but had to install the generic kernel and remove the server one with APT, as the network card would not work with the server kernel....

Not sure about the other questions so can't really comment on them....

---

### Post by doogy2004 on 2009-07-27
> **Serangan said:**
> If in installed ubuntu home server and apt-get'ed the generic kernel, would i then get the power management features? 'Cause i have my server set to go to sleep when no other pc's are on, and it wakes via wol. I can't do this with the server kernel, but i also dont want any of the 'extras' that come with the generic kernel;
ie. OpenOffice.org etc.

Installing the linux-generic package only installs the generic kernel, nothing else.  The other software is pulled in if you install the ubuntu-desktop package.

---

### Post by Serangan on 2009-07-28
> 
Re Q3a the Atom question I have a genuine Intel Atom board with the latest Ubuntu Server LTS loaded, but had to install the generic kernel and remove the server one with APT, as the network card would not work with the server kernel....

Ok, so ill try the server kernel and if it doesnt work, ill install the generic kernel.

> Installing the linux-generic package only installs the generic kernel, nothing else. The other software is pulled in if you install the ubuntu-desktop package.
ok... so that means that if i want the power management ill need the ubuntu-desktop? Or is it part of the kernel?

---

### Post by doogy2004 on 2009-07-28
> **Serangan said:**
> ok... so that means that if i want the power management ill need the ubuntu-desktop? Or is it part of the kernel?

Not necessarily, you should be able to use the generic kernel.  If that doesn't enable power management, you may need to install another package.  ubuntu-desktop is a meta package that installs all of the software included in a default installation of Ubuntu Desktop.

---

### Post by Serangan on 2009-07-28
Yah, i tried this. I install server-edition, then apt-get'd the generic kernel. rebooted into that and still no power management. Didn't try the ubuntu-desktop, but i did install apci and acpid - didn't work.

Also, I've worked out how to keep the lvm partitions. I tried on a new hdd, and installed lvm2, it saw them, but couldnt mount 'cause ```
/dev/Storage/xxxx
``` didn't exist, so i copied that across and it works.

---

### Post by Serangan on 2009-07-29
Yeah, didn't go well.

Turns the ```
/dev/Storage/xxxx
``` files are a symbolic link to ```
/dev/mapper/Storage-xxxx
```

Now i need away to get some files off the botched lvm. Unless i can create the required files.

Any suggestions?
Edit
I worked it out!
this site --> [http://www.novell.com/coolsolutions/appnote/19386.html](http://www.novell.com/coolsolutions/appnote/19386.html)

pvscan -> vgs -> lvs

Or it was testdisk... one of the two. either way, im happy that i've got everything back.

---

