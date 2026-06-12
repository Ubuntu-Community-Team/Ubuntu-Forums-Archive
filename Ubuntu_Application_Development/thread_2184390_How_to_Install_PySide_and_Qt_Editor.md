---
title: "How to Install PySide and Qt Editor"
date: 2013-10-28
forum: Ubuntu Application Development
---

### Post by adi06 on 2013-10-28
Hi everyone!

I'm too much fed up, maybe boz i'm noob and too new to development, but i can't follow the procedurees of installing PySide and QT aeditor on Ubuntu 13.10.
As there is no setup/libariaes for Ubuntu 13.10, i had to rcompile the source of PySide using cmake myself, which drove me Nuts for last 2 days non stop.

Please help me on this and help me through if posible step by step installation of the Python3 PySide QT application Environment Plzzzzzzzzzzzzzzzzz....

I don't know how is this wiki even correct. At least i'm not able to compile PySide by their method.
[http://qt-project.org/wiki/Building_PySide_on_Linux](http://qt-project.org/wiki/Building_PySide_on_Linux)

I tried their suggested automated script, [this]([https://github.com/PySide/BuildScripts](https://github.com/PySide/BuildScripts)) but when i try it gives error:
./dependencies.arch.sh: 4: ./dependencies.arch.sh: pacman: not found

and tried [this]([https://github.com/PySide/pyside-setup](https://github.com/PySide/pyside-setup)) also, but one this it confuses is, it ask t issue this command
sudo apt-get install qt-sdk
which install qt5 which is not supported by pySide but he have commented on it: Install qt4.8

i left that command. and with this command using pyton3 i got error
File "pyside_postinstall.py", line 190, in install_posix
    import PySide
ImportError: No module named 'PySide'
The PySide package not found: None

its a known bug for python3 but the did not responded to the bug report yet. since 10 days.
[https://github.com/PySide/pyside-setup/commit/de53ee6a3a3d345fd4b1e7f92428ca8e521d4de7](https://github.com/PySide/pyside-setup/commit/de53ee6a3a3d345fd4b1e7f92428ca8e521d4de7)

Besides when i to install c make, it was a mess.
untill i read a post where it said sudo-apt install cmake, 
why cmake do not mention this and force to recompile cmake.

Well after that i tried cmake and it gave c++ compiler not found when it was already installed. so i reinstalled it solced that error oddly.
But then it gave some stargenge error, an di  searched on net and a post said ineed cmake-dev or something .Dev also. i installed it and it worked.
but that post mention to install all dependecies with sudo debian-pkg cmake for all dependencies.

Why not no one mention all that before >.<

I tried that all and at last FAILED!

Have pitty on me and help me get this working.
i want it to work with Python 3 on ubuntu 13.10 with QT Creater maybe or some other GUI editor whichever is better for Python which give syntax highlighting.
Thanks In anticipation.
Fewwwwwwww....

---

### Post by spjackson on 2013-10-29
> **adi06 said:**
> 
As there is no setup/libariaes for Ubuntu 13.10, i had to rcompile the source of PySide using cmake myself, which drove me Nuts for last 2 days non stop.

Please help me on this and help me through if posible step by step installation of the Python3 PySide QT application Environment Plzzzzzzzzzzzzzzzzz....

Why do you say that? There are plenty of python3-pyside packages in the repositories. Full the full lot do:
```

sudo apt-get install python3-pyside

```
or select it in Synaptic, or whatever else is your favourite package manager.

Compiling something like this from source isn't something for beginners. I suggest you avoid this until you have a genuine need and some more expertise.

I'm not sure what Qt Editor is. Do you have a link for that?

---

### Post by adi06 on 2013-10-29
> **spjackson said:**
> Why do you say that? There are plenty of python3-pyside packages in the repositories. Full the full lot do:
```

**sudo apt-get install python3-pyside**

```
or select it in Synaptic, or whatever else is your favourite package manager.

Compiling something like this from source isn't something for beginners. I suggest you avoid this until you have a genuine need and some more expertise.

I'm not sure what Qt Editor is. Do you have a link for that?

[http://qt-project.org/wiki/PySide_Binaries_Linux](http://qt-project.org/wiki/PySide_Binaries_Linux)
**says:**
Didier, together with the PySide core dev team, maintains a PPA  repository for Ubuntu. Currently, up-to-date packages are available for  versions from 10.04 (Lucid) up to 11.10 (Oneiric).** Python 3  experimental support is available for 11.04 (Natty) and 11.10 (Oneiric)**.  Follow the instructions below to install PySide in your system in order  to use it with Python 2.x .

^Not available for ubuntu 13.10
ppa: pyside is not available for ubuntu saucy salamander

Oh and i meant QT Creator, not editor.  will edit that.

---

### Post by spjackson on 2013-10-29
The PySide core dev team may no longer provide binaries for the lastest Ubuntu, but the packages do exist in the standard repositories. I wasn't making up that apt-get command, I ran it successfully on Ubuntu 13.10. Here's a list of related packages [http://packages.ubuntu.com/source/saucy/pyside](http://packages.ubuntu.com/source/saucy/pyside)

Qt Creator is also available as a standard install from the Ubuntu repositories.

---

### Post by adi06 on 2013-10-29
> **spjackson said:**
>  I wasn't making up that apt-get command, I ran it successfully on Ubuntu 13.10.

Hi Thanks for replying, i never said u made up anything, i just gave that details bcoz that's only what it says in their webpage and thats only all i get from them. Nothing useful information as simple as you had and gave.

Why woudn't they mention that its available through apt install? how did u knew?
And how could i have known, i'm just a read and follow user, i followed their instructions step by step as it is and ran in dozens of problems, which They didn't mention which were some prerequisites for cmake and Qt etc, and some other strange one as well.

I'm few days old in Ubuntu world, just recently installed ubujntu a week ago, and you can find many of my posts, for beginners help.
I was almost fed up to delete Ubuntu bcoz of the mess and uncertain instructions. But thanks to u for saving my love for ubuntu.

Ok, i'm uncertain of of one thing. I installed PySide with, apt-get install python3-pyside, And installed latest QT editor which i downloaded, the one in software center was older version. I though that for QT based GUI app development i need, Python, QT & PySide. But i only installed python and Pyside and the Pyside GUI code did worked and ran.

I did >where PySide, but no result nor for QT. but when i do in python shell >> (sudo-code) print (PySide__version) && print(QT_version)
i get Pyside 1.2.1 && QT 4.8.4
It means QT is installed, does it get installed by installing PySide?

And can you suggest some great IDE for python, which will have syntax highlighting and auto completion etc. QTs Creater is not much friendly. i din't found it much better.
FOR GUI i'm using QTs GUI Designer. Is that best? or u could suggest something else.
For editor i have heared PyCharm is very Good, and on other hand netbeans/eclipe one of them's PyDev.
one of a user said Geany.
What about PyQuickly...?

---

### Post by spjackson on 2013-10-31
> **adi06 said:**
> Hi Thanks for replying, i never said u made up anything, i just gave that details bcoz that's only what it says in their webpage and thats only all i get from them. Nothing useful information as simple as you had and gave.

Why woudn't they mention that its available through apt install? how did u knew?

Initially, when a project such as PySide starts, it isn't included in the Ubuntu repositories (or the packaging systems for other distros). So it is up to the project developers to provide either binaries for certain platforms or instructions for building from source, if they want their software to be used by many people.

As time goes by, once the project becomes established and popular, it will get picked up by the distro packagers. So I assumed that there would be an Ubuntu package for PySide. I started up Synaptic and searched for it. Another method is to Google for "ubuntu saucy package pyside". (This method can be useful if you are running an older version that doesn't have the package you want, so you can easily see if it is in a newer version and decide whether to upgrade.)

A good rule of thumb is to assume that there's a package and search for it first, because that's always the best way to install stuff. Only if something is really new or you have specific need for the latest version do you need to resort to other methods.
> 
And how could i have known, i'm just a read and follow user, i followed their instructions step by step as it is and ran in dozens of problems, which They didn't mention which were some prerequisites for cmake and Qt etc, and some other strange one as well.

I'm few days old in Ubuntu world, just recently installed ubujntu a week ago, and you can find many of my posts, for beginners help.
I was almost fed up to delete Ubuntu bcoz of the mess and uncertain instructions. But thanks to u for saving my love for ubuntu.

You are welcome.
> 
Ok, i'm uncertain of of one thing. I installed PySide with, apt-get install python3-pyside, And installed latest QT editor which i downloaded, the one in software center was older version. I though that for QT based GUI app development i need, Python, QT & PySide. But i only installed python and Pyside and the Pyside GUI code did worked and ran.

I did >where PySide, but no result nor for QT. but when i do in python shell >> (sudo-code) print (PySide__version) && print(QT_version)
i get Pyside 1.2.1 && QT 4.8.4
It means QT is installed, does it get installed by installing PySide?

If the Qt libraries weren't installed already, then yes, they would get installed by installing PySide. That is one of the beauties of the packaging system: pre-requisites get installed automatically.
> 
And can you suggest some great IDE for python, which will have syntax highlighting and auto completion etc. QTs Creater is not much friendly. i din't found it much better.
FOR GUI i'm using QTs GUI Designer. Is that best? or u could suggest something else.
For editor i have heared PyCharm is very Good, and on other hand netbeans/eclipe one of them's PyDev.
one of a user said Geany.
What about PyQuickly...?
I'm not a big fan of IDEs and I don't really use them for Python. I haven't used PySide (just PyQt). I write Python (and PyQt) code mainly in gVim, but it's not to everyone's taste. Qt's designer is the thing to use for GUI design.

Perhaps someone else can help you here. This sort of topic occurs often on the forums, especially on Programming Talk.

---

### Post by adi06 on 2013-10-31
Thanks for reply,
PYSide is same as PyQT
And thanks for the information, i'm new linux user and such tips will help me grow.
Thanks

---

