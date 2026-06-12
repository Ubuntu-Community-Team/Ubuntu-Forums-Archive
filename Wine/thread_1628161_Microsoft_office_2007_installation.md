---
title: "Microsoft office 2007 installation"
date: 2010-11-22
forum: Wine
---

### Post by lithupa on 2010-11-22
Can anyone provide me with DETAILED steps on how to install Microsoft office 2007 on Ubuntu 10.10. I have already installed wine and configure it but still the installation process  starts but cannot complete.ANYONE,pls help

---

### Post by dino99 on 2010-11-22
might be a little bit oldish using latest wine, but;

[http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html](http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html)

the other solution is to install openoffice from synaptic

---

### Post by sites on 2010-11-22
It's important to rule out the common mistakes first & sort out some details while we're at it.  Are you installing from a DVD or from the hard drive?  If it's a DVD, is it scratched or damaged?  Have you ever performed a complete install with this particular DVD/image/folder before in wine or in Windows?  Another important detail for us to find out is if you are animal, vegetable, or mineral?

---

### Post by doctorzeus on 2010-11-22
> **sites said:**
> It's important to rule out the common mistakes first & sort out some details while we're at it.  Are you installing from a DVD or from the hard drive?  If it's a DVD, is it scratched or damaged?  Have you ever performed a complete install with this particular DVD/image/folder before in wine or in Windows?  Another important detail for us to find out is if you are animal, vegetable, or mineral?

I've got MS Office 2007 and it installed no prob....

---

### Post by KevinPreuss on 2010-11-30
I am having the same installation problems as well.  Here is my problem.  

So I went back to the absolute beginning with my Dell Precision M6500

I just reinstalled Ubuntu 10.10 OS with formatting
I just added Wine 1.2 stable, no other programs except the update manager.
I then configured Wine to the .exe on the CD  which by the way is autorun.exe for Office 2007 not setup.exe
The configuration within Wine is as follows:
1) Change to run as Vista
2) Library:  msxml3 edited to native
3) Library:  rpcrt4 edited to native

I right mouse click to open with wine windows program loader
From CD and on the desktop.

I see it start the autoloader in the panel at the bottom then it just disappears.

I have installed/uninstalled through the Ubuntu software center
I have installed/uninstalled through the synaptic package manager
I even learned how to compile-kind of.

I know what the problem will be- something extremely simple staring me in the face.  Like spelling my name wrong over and over and over.  i just need help finding that little thing I did wrong and I have a strange feeling that it will be the same as this person.

Kevin

---

### Post by jre6 on 2010-11-30
[LIST]
[*]Do this in a terminal window to install Wine 1.2 or later:
[/LIST]
```

sudo apt-get install wine1.2
winecfg

```
[LIST]
[*]In the window, set riched20 and usp10 as Native (Built-in) overrides.
[*]Close the wine Configuration window bu clicking on OK.
[*]Type in these commands in the terminal:
[/LIST]
```

http://www.kegel.com/wine/winetricks
sh winetricks

```
[LIST]
[*]Select wsh56js and optionally msxml3 (I am not very sure - skip this if you are not going to install Office Service Packs) and install them.
[*]Insert the MS Office disc and start the installer by double clicking, or by the command:
[/LIST]
```

wine start /media/*discname*/setup.exe

```
[LIST]
[*]The installer may or may not accept the key code (you can't just type in). Try a few times, and if it does not work try this and start afresh:
[/LIST]
```

rm -rf ~/.wine

```
[LIST]
[*]The installer will sometimes appear to hang (especially at 2/3 of the installation) but it is normal. Wait for the installation to finish.
[/LIST]
Hope this works.

[B]If you have an existing installation of Wine (prior to 1.2), do the following before installing:
[/B]```

sudo dpkg -r wine
sudo dpkg --purge wine
rm -rf ~/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*

```

---

### Post by KevinPreuss on 2010-11-30
It still doesn't work.  I followed you instructions to the "T"

Does anyone want to try and remote desktop on my machine.  I have never done this either though.  I teach tonight until about 10 pm eastern.

Any body want to stay up late or if in the Detroit/Royal Oak  Mi. area who would want to show me?

Kevin

---

### Post by jre6 on 2010-11-30
This should have worked without problems.

Anyway, if this fails, you may try virtualising Windows with [VirtualBox]("http://www.virtualbox.org") to run MS Office 2007.

To install VirtualBox, do the following:

[LIST]
[*] Add one of the following lines according to your distribution to your /etc/apt/sources.list:  
 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
[*]Then, in a terminal window, do the following:
[/LIST]
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get install virtualbox-3.2

```VirtualBox will be installed. Now:

[LIST]
[*]Open VirtualBox from Applications > System Tools.
[*]Create a new VM (virtual machine) from the New button.
[*]Select the OS, the amount of RAM you want to spend (no more than 50% of your original RAM) and the disks. Create a new hard disk, select a dynamically expanding storage, and assign the amount of space the virtual disk should grow upto.
[*]After doing so, select settings, go to shared folder, and add a shared folder (which will be a common storage space for the OS in the VM as well as Ubuntu)
[*]Put the Windows disk and run the VM from the Start button.
[*]The VM will boot from the Windows disc. Install Windows from the on-screen instructions.
[*]After installing Windows, install the guest additions from the devices menu. Continue with the installation, even if "unsigned driver" alerts come up and reboot when you are told to do so.
[*]In a command prompt window (or the Run window) in Windows type:
[/LIST]
```

net use X: \\vboxsvr\*Sharedname*

```
where X: refers to the drive letter assigned to the shared folder in Windows and Sharedname refers to the name of the Shared folder (whatever you wrote in folder name).

[LIST]
[*]Now install MS Office 2007.
[/LIST]
Keep all your documents in the shared folder so that Windows in the VM can access it. You may even consider making your home folder as the shared folder.

---

### Post by KevinPreuss on 2010-12-01
OK.

I installed all msxml3, msxml4, msxml6 native, then builtin

And whoopee little progress with mostly fail sauce.

2007 will not install no matter what.

But I was at least able to enter the key on my 2010 before it crashes.

I am still lost

Kevin

---

### Post by jre6 on 2010-12-01
> **KevinPreuss said:**
> I installed all msxml3, msxml4, msxml6 native, then builtin. And whoopee little progress with mostly fail sauce.2007 will not install no matter what.But I was at least able to enter the key on my 2010 before it crashes.

Are you running the MS Office with the configuration of Vista? Make it XP.

Use the previous post how to use VirtualBox if Wine fails.

---

### Post by marl30 on 2010-12-01
I recommend Playonlinux for installing Office 2007. It makes running Office 2007 much easier than messing around with Wine. It does all the Winetricks stuff and Library overrides behind the scene. Try it, it works. It's in the Software Center.

---

### Post by lithupa on 2010-12-01
Thanks everyone for the insights you provided on the installation of Office 2007 in ubuntu. I'm now happily using Office on my lovely ubuntu. Anyone who has problems with installing windows applications on ubuntu,please do not hesitate to conduct me or anyone.

Thanks again everyone.

UBUNTU FOREVER

---

### Post by tora201 on 2010-12-02
Followed instructions in post #6, and also did playonlinux - same result: Excel, Word and PowerPoint are all fine but the rest of the programs, crash. Especially unstable are: Publisher and Onenote.   

Any ideas?

---

### Post by DodgeV83 on 2010-12-02
> **tora201 said:**
> Followed instructions in post #6, and also did playonlinux - same result: Excel, Word and PowerPoint are all fine but the rest of the programs, crash. Especially unstable are: Publisher and Onenote.   

Any ideas?

Publisher is not currently compatible in Wine, Onenote also has problems.  You likely won't get them to work.

---

### Post by Ampi on 2011-02-04
I have MS Office 2007 installed with no problems, including Publisher and Onenote. 

I have downloaded the blue edition of MS Office, it has the license code already in it, so you do not need to enter enything. 
I used the following steps: [http://ubuntu-reference-guide.blogspot.com/search/label/microsoft%20office](http://ubuntu-reference-guide.blogspot.com/search/label/microsoft%20office)
I dont know if you already have it installed correctly now, but in case it might help you I post this anyway.

---

