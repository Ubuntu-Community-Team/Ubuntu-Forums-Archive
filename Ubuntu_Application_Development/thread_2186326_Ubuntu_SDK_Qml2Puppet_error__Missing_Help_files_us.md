---
title: "Ubuntu SDK Qml2Puppet error / Missing Help files using F1"
date: 2013-11-06
forum: Ubuntu Application Development
---

### Post by Das Goat on 2013-11-06
Hello everyone,

My buddy and I are trying to learn QML using the Ubuntu SDK installed from the Software Center. We are both on Saucy, we have different laptops (me: toshiba 64 bit, him: dell 32 bit). I am using the ATI drivers from ATI (I have to or my screen will never come back from sleep mode), he is using the open source drivers, but I am not sure what his card is.

Here is our problem: the SDK works generally well, but when ever we click on the Design button, we get three blank windows called qml2puppet that open up and we can't really do anything until we get them to close by "x"ing out of them. The program doesn't crash and everything seems to work otherwise, but it is very bothersome to jump between Design and Edit views as we attempt to teach ourselves QML.

I have seen a bug report entered for this problem, but it says it only affects one user. I don't know how to add to that count. I have also seen in Google searches that this is affecting others as well, but I can't find any references to the bug here on the forums.

Any help would be appreciated.

---

### Post by Das Goat on 2013-11-16
Well after a few weeks, 138 views and no replys, It seems clear that no one has any idea what causes this error. Since I am not the kind to just give up, I have been trying to find solutions to the Qml2Puppet error and the fact that the documentation is missing when you try to use F1 to get help. Here is what I have found:

This error seems to not be Cononical's implementation (which I first thought) but a more general problem with the Linux version of Qt-Creator. I am trying to solve both the Qml2Puppet error and the lack of the help files loading like they are supposed to. I have a few systems I work with so I can try different things, but all systems run 13.10.

I have tried uninstalling the Ubuntu SDK and loading Qt Creator from the software center (ver 2.7.1). I have also installed QtCreator from this link [http://www.ubuntuupdates.org/package/ubuntu_sdk_release/raring/main/base/qtcreator](http://www.ubuntuupdates.org/package/ubuntu_sdk_release/raring/main/base/qtcreator) which is version 2.8.1 and running Qt creator NOT the Ubuntu SDK. The Qml2Puppet error still occurs on both, but I can see what is trying to load in the box.It is duplicate copies of the designer page. I have to close them before I can do anything, but like in the Ubuntu SDK, it is mostly just annoying as the designer does work. As I learn more QML coding, I don't really need the Designer right now so I am shelving that part of the problem until the next version (due in December 2013 I believe).

The missing Help files is more annoying. Like the QML2Puppet error, no version of QtCreator I load will load the help files for an Element if you press F1. Elleo from the IRC site suggested I grab a working .qch file from another version (I grabed the Windows as it was handly) and replaced the Ubuntu installed one, but that didn't fix anything either. Yes, I know you can go to [http://developer.ubuntu.com/api/qml/sdk-1.0/QtQuick/](http://developer.ubuntu.com/api/qml/sdk-1.0/QtQuick/) and get help with an Element, but this is a Krudge, and you do not get the visual examples. I will keep pounding away at this, but if someone has a clue that would be helpful.

---

### Post by usr drc on 2013-11-17
I have the same issue. I was led here on G+; [https://launchpad.net/qtcreator-plugin-ubuntu](https://launchpad.net/qtcreator-plugin-ubuntu), if it is any help.

---

### Post by Das Goat on 2013-11-23
I have a Partial Fix!

I have gotten at least the help files fixed on two Ubuntu installations. Here is what you need to do. If you have installed a lot of Qt versions like I did trying to fix this, I recommend Uninstalling Ubuntu SDK using the software center and then running

sudo apt-get purge qtcrea* 

to get rid of any config files laying around. For good measure, I looked around and deleted any Qt folders I found in my home directory and the Qt stuff I found in the the ~/.config directory. Then I re-installed the Ubuntu SDK. I then went out to the Qt Project homepage and downloaded the Qt 5.1.1 w/ QtCreator 2.8.1 package (it is your first choice). As a side note, I tried installing QtCreator 2.8.1 by itself, but that did not fix anything, so the help files must be contained in the Qt 5.1.1 package. Since this is not offered by itself, you need to get the combo package.

This might be obvious to more experiances users, but when you download the package, you have to set it to installable by right clicking the file -> properties -> permissions -> Allow executing the file as a program. If you don't, it just unpacks the file and nothing happens. That was annoying until I found the answer. Then in the GUI, just doulbe click the icon and the installer will run. There is at least one guide out there that suggests running it from the command line with sudo but DO NOT DO THAT! It is not necessary and only causes errors that make you have to redo the whole process because now you have set the config files to root only. Just double click the icon and let the installer do it's work.

When you are done you will have two Qt Creators installed, the Ubuntu SDK and the official QtCreator 2.8.1. If you are an Ubuntu purist, don't worry, just unlock the Qt Creator from Unity and don't use it. But what you will find is that the F1 help files now load in the Ubuntu SDK and you can get instant help with all of the functions / elements (or what ever they are called).

Now here is the screwy thing. On one of my installations where I didn't purge anything but I had also not installed multiple Qt versions, the design function works perfectly without qml2puppet errors if I use Qt Creator, but they still exist if I use Ubuntu SDK. However, my projects have a very hard time running if I created them under Ubuntu SDK. On the other instance, Qt Creator reports an error about Puppet not being installed correctly. However, I have no errors running projects created in any version of Creator, but it did give me some valuable information about how to fix the Puppet error. Here is the output:

[INDENT]The executable of the QML Puppet process (/opt/qtcreator-2.8.1/bin/qml2puppet) cannot be found. Check your installation. QML Puppet is a process which runs in the background to render the items.
You can build qml2puppet yourself with Qt 5.0.1 or higher. The source can be found in /opt/qtcreator-2.8.1/share/qtcreator/qml/qmlpuppet/qml2puppet/.
qml2puppet will be installed to the bin directory of your Qt version. Qt Quick Designer will check the bin directory of the currently active Qt version of your project.[/INDENT]

Some bright person on this forum who has more experiance than I do should be able to interpret this and maybe fix this for us. *hint, hint. nudge, nudge*

I would like to get this information to the Ubuntu development team so they can fix the SDK, but I am inexperianced with the bug reporting system. Maybe someone could help me with that process?

One last thought. I plan on wiping out one of my Ubuntu installations and starting fresh, but it might be a few weeks before I can get around to that. If someone is willing to give that a try and then following my directions, I would appreciate any feedback you can give.

---

### Post by Das Goat on 2013-11-25
Just an update. I did fresh installs of Ubuntu 13.10 on two of my devices. After doing all of the normal updates, I installed Ubuntu SDK and then QT 5.1.1 package from the Qt project. Help files can now be accessed normally. Also, the error where the Creator 2.8.1 version would not run files created with Ubuntu SDK seems to be fixed as well. The qml2puppet error is still in the Ubuntu SDK, but if you just close the windows the Designer does work. If that bothers you, you can open the project in 2.8.1 and the designer works without error. 

I am going to attempt to put in a ticket with Launchpad. If anything changes I will let you know.

---

### Post by adamduren on 2014-02-20
What is the number of the ticket you logged and has any progress been made? I am running into the same issue with the three popup windows in design mode.

Laptop: Dell E6530
Graphic Card 1: Intel Ivybridge Mobile HD 4000
Graphic Card 2: Nvidia NVS 5200M/PCIe/SSE2
Qt Creator 2.8.1
Ubuntu 14.04 alpha

The issue occurs when running either graphics cards.

---

