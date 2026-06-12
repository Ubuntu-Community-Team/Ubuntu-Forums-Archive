---
title: "Drive Mapping : I want .wine to be on other partition"
date: 2010-10-02
forum: Wine
---

### Post by ze3rax on 2010-10-02
Hello,

I'm new to Linux (got my working properly at last today). After installing the latest 1.3.4 version of Wine I wanted to configure it from

-
wine winecfg
-

The main idea was to move the default place of storying Wine things from this 

/home/ze3rax      to     /media/Software/Wine

--------------------------

[[IMG]http://img824.imageshack.us/img824/2582/screenshotwineconfigura.th.png[/IMG]]("http://img824.imageshack.us/i/screenshotwineconfigura.png/")

In this window, in Advanced menu I can't change the "C:" location, but can edit "H:"

---------------------------

This is the location I want Wine to be installed by default (like custom install location in Windows) [100 GB ext4 partition - like in Windows would be used for programs/photos/music]

[[IMG]http://img541.imageshack.us/img541/192/screenshot320gbharddisk.th.png[/IMG]]("http://img541.imageshack.us/i/screenshot320gbharddisk.png/")

[[IMG]http://img706.imageshack.us/img706/5755/screenshotsoftwarefileb.th.png[/IMG]]("http://img706.imageshack.us/i/screenshotsoftwarefileb.png/")

------

I really would like to know how to change the location of the .wine folder and  disable the automatic creation of new .wine folder after entering config mode. (in /home/ze3rax). Also would like to know if that can't change cant be made if there's any custom location ways for installing Wine, because I've read most issue-close threads and tried a few things but nothing helps...

Any deeper configuration are appreciated beside those how to install programs, add things or so. The first thing I was doing in every Windows soft was to configure the program and understand it.

Regards,
Z

---

### Post by dino99 on 2010-10-03
all you need to know:

[http://wiki.jswindle.com/index.php/Main_Page](http://wiki.jswindle.com/index.php/Main_Page)

---

### Post by ze3rax on 2010-10-03
Hello,

IF I had understood the main idea of all FAQ I read hours ago I would NOT post in here and the link you gave me... I've read it on first install of Wine.

I already wrote it that I don't need such information:
*" Any deeper configuration are appreciated beside those how to install  programs, add things or so. The first thing I was doing in every Windows  soft was to configure the program and understand it. " *

From the link you gave me the onliest thing I understood was that obviously I should have .wine folder for each windows application I want to use under Linux.

---

### Post by ajackson on 2010-10-03
The quickest way is to create /media/Software/Wine, check the permissions to make sure it is owned by your user id and that you have read, write and executable permission on it.

Then launch a console and do the following

```
cp -vR /home/ze3rax/.wine/* /media/Software/Wine/
```
That will copy everything from your current wine directory to the place you want wine to live

```
rm -rf /home/ze3rax/.wine
```
That removes the old wine directory

```
ln -s /media/Software/Wine /home/ze3rax/.wine
```
That creates a special file that, in this case, redirects anything wanting to access /home/ze3rax/.wine to the correct place in /media/Software/Wine.

---

### Post by ze3rax on 2010-10-03
Hey ajackson,

I followed your guidance and the results are:

* From ```
cp -vR /home/ze3rax/.wine/* /media/Software/Wine/
```I managed to copy what I wanted not like I copy/pasted it before.


* From ```
rm -rf /home/ze3rax/.wine
```It did not remove .wine folder from /home/ze3rax

* After executing this
```
ln -s /media/Software/Wine /home/ze3rax/.wine
```and when I enter config from Wine's menu ( Applications -> Wine -> Configure ) a new .wine folder was created in /home/ze3rax.

I've decided to uninstall Wine and there's the problem: in /media/Software/ze3rax/

[[IMG]http://img237.imageshack.us/img237/3738/screenshotwinefilebrows.png[/IMG]]("http://img237.imageshack.us/i/screenshotwinefilebrows.png/")

Those locked files are only accessible for removing only by root and no other.
Edit: I'm definitely making a progress - deleted that folder with "sudo rm -ri" and now there's no Wine installed.


Is it possible in that Linux "user friendly environment" *cough* irony *cough* programs like Wine to have their install locations to be defined in the process of installing with out the need of more "terminal" attempts to make it like you want it. Command like [WINEPREFIX]("http://wiki.jswindle.com/index.php/WINEPREFIX") are useless in my case. If that .wine folder is like the registry entries in Windows I'm cool with that but they are not - that drive_c drives me crazy because in that 16 GB partition (from previous post) I don't want to have such programs installed.

---

### Post by ajackson on 2010-10-03
> **ze3rax said:**
> Is it possible in that Linux "user friendly environment" *cough* irony *cough* programs like Wine to have their install locations to be defined in the process of installing with out the need of more "terminal" attempts to make it like you want it.
Who said that Wine was a "user friendly environment" application?

You can do exactly the same as what I said without needing to use the terminal, it just takes more steps to explain it. You asked how to do it and I told you, next time I think I won't bother when someone asks for help. Don't ask for help and then complain because you are asked to use the command line and don't PM people asking for support either.

---

### Post by ze3rax on 2010-10-03
Quite aggressive don't you think. I'll continue my research and was glad you helped beside the fact you obviously got offended by my last post. When I was helping in Windows support forums I was not pointing link to people that probably might help them. You helped me the best way help could be given so don't be that harsh with me. Obviously those forums are quite differently constructed and different type of people are using them. I also can provide support , sure - there are tons of links out there, just try to remember your first steps in this environment !

Personal answer to your quoted text: try to understand the exact meaning of words even being in quotation marks. If that's the way of Linux I'll get used to it - to install 1st and then configure, not like Win - configuring before installing.

/ not solved but better that way /

---

