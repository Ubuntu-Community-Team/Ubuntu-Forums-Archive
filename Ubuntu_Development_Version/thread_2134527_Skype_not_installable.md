---
title: "Skype not installable"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by andreaolivato on 2013-04-11
Hi, I'm no longer able to install Skype on 13.04 x86_64 because of broken dependencies for i386 packages

This is apt-get install skype output. Tried both with the package downlodable at skype.con and the "partners" canonical repository, both ways no luck.

Any idea?

```
skype-bin:i386 : Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
                  Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
                  Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed

```

---

### Post by philinux on 2013-04-11
I've been meaning to get skype installed on my 64 bit acer 1410. This thread reminded me.

It installed without error and runs fine.

Standard install here and skype has never been installed on this machine before.

Is your system fully up to date.

I just did a normal install sudo apt-get install skype

---

### Post by kuvanito on 2013-04-11
skype does installs and works on 13.04 UNITY but the GUI has no borders,in other words no window buttons
but if you run 13.04 Gnome Shell it has window buttoms as it is suppose.It is not a Skype problem as someone suggested,it is a UNITY problem.

---

### Post by philinux on 2013-04-11
> **kuvanito said:**
> skype does installs and works on 13.04 UNITY but the GUI has no borders,in other words no window buttons
but if you run 13.04 Gnome Shell it has window buttoms as it is suppose.It is not a Skype problem as someone suggested,it is a UNITY problem.

Works as intended here window buttons normal on ubuntu with unity.

---

### Post by kuvanito on 2013-04-11
> **philinux said:**
> Works as intended here window buttons normal on ubuntu with unity.

and your version of skype is?

---

### Post by mcellius on 2013-04-11
I just installed it and ran it on my Dell laptop (running Unity) and all appears to be well here, too.

---

### Post by kuvanito on 2013-04-11
I am running 13.04 both Unity and Gnome,no matter what I do I can not get Skype to show window buttons on Unity
I have installed Skype 4.0,Skype 4.1 and both show the same result but only in Unity not in Gnome
I am also running the 32 bit version of 13.04 and my rig is 100% intel,CPU,GPU,etc so it is not an nvidia issue here either
It does not happens in Gnome Shell thou.

---

### Post by mcellius on 2013-04-11
I installed Skype just by entering > sudo apt-get install skype since it is already in the Ubuntu Software Center.  Is that how you did it, or did you go out to Skype's site and grab a version for Linux?

---

### Post by jimafternoon on 2013-04-11
This worked for me:

```

[INDENT] 
[LIST]
[*][COLOR=red]sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install skype && sudo apt-get -f install[/COLOR]            
```
[/LIST]

But I also have the issues with no buttons to close the chat window after I open it. 
[/INDENT]

---

### Post by ppjdee on 2013-04-11
> **jimafternoon said:**
> This worked for me:

```
[INDENT] 
[LIST]
[*][COLOR=red]sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"[/COLOR] 
[*][COLOR=red]sudo apt-get update[/COLOR] 
[*][COLOR=red]sudo apt-get install skype && sudo apt-get -f install[/COLOR] 
[/LIST]
[/INDENT]

```[INDENT]
[COLOR=#ff8c00]But I also have the issues with no buttons to close the chat window after I open it. [/COLOR]
[/INDENT]


same for me. 
all i did was sudo apt-get install skype

---

### Post by philinux on 2013-04-12
> **kuvanito said:**
> and your version of skype is?

The one in the repo.

sudo apt-get install skype

Default repos and I have no added sources or ppas.

---

### Post by kuvanito on 2013-04-12
> **mcellius said:**
> I installed Skype just by entering  since it is already in the Ubuntu Software Center.  Is that how you did it, or did you go out to Skype's site and grab a version for Linux?

this is what I get:

leo@leo:~$ sudo apt-get install skype 
[sudo] password for ari: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
leo@leo:~$ 

now this is because skype is already installed
if I purge skype and type the same command i get skype not available or package not available

still no window buttons

I normally go to skype.com and download the latest for 32 bit

---

### Post by philinux on 2013-04-13
Just seen this workaround for nvidia machines. Although with nvidia-current installed here skype runs fine. 

[http://m.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html?m=1](http://m.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html?m=1)

---

### Post by shantiq on 2013-04-13
kuvanito   try link linked by Phil  and if this still does not play  4.0 [works fine ]("http://ubuntuforums.org/showthread.php?t=2133148&p=12592353#post12592353")on 13.04 if you do not mind an earlier version
i have not tried the W8 fix as i installed 4.0 a week ago and am happy with that for time being 

Nonetheless would love to know how one fares with [W8]("http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html?m=1") workaround if anyone has tried it yet

---

