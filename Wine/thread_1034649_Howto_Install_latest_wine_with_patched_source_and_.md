---
title: "Howto: Install latest wine with patched source and manage wine prefixes"
date: 2009-01-08
forum: Wine
---

### Post by orlox on 2009-01-08
Just wrote this entire howto, and the forums sent me a 502 error and all sort of stuff and long story short, I am rewriting it now...

[SIZE="4"]*Important note!*[/SIZE]
If you dont need a patched wine, I strongly reccomend you to use the package manager to installed compiled sources. To obtain the latest wine in this way, you first need to add the gpg key of winehq's repository:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
Then add the repository:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/$(lsb_release -sc).list \
 -O /etc/apt/sources.list.d/winehq.list

```
And then wine can be installed with:
```

sudo apt-get update
sudo apt-get install wine

```
[SIZE="5"]**Introduction**[/SIZE]

Well, although there are repositories with the latest development verison of wine 1.1.12 at the date of writing, many of the latest games require some patches to the source. So, this is what this tutorial is about!

Unlike other howtos ive seen elsewhere, I download and keep the sources up to date using git, and install wine with checkinstall. Almost all this with some slight modifications was written by the user Massimo from appDB

[SIZE="5"]**1. Installing Wine**[/SIZE]

So lets begin by removing wine (only if you have installed it already through the package manager):
```
sudo apt-get remove wine
```

If you had previously added the winehq repository, delete it:
```

sudo rm /etc/apt/sources.list.d/winehq.list

```

Then, we install git:
```

sudo apt-get install git-core 

```
And download wine sources from the git repository (this should take a while):
```

git clone git://source.winehq.org/git/wine.git ~/wine-git 

```
This will download the sources at a folder called wine-git inside your home folder. **You should keep this folder after the installation so it is easier (and less time consuming) to update and apply your patches later.**

Next, we install the necessary packages to build wine:
```

sudo apt-get build-dep wine
sudo apt-get install fakeroot 

```
You will also need checkinstall to install it later:
```

sudo apt-get install checkinstall

```
Build wine. This will quite some time (over 40 minutes to me with an AthlonX2 with 2gb ram):
```

cd ~/wine-git
./configure --prefix=/usr
make

```
Then, install wine (DONT CLOSE YOUR TERMINAL! or if you did, open it again and run cd ~/wine-git). I use checkinstall because it creates a deb package and installs it, and this makes it easier at the end to manage all of your compiled programs (NOTE, if you have installed the latest wine with the package manager, then you should delete the entry of the wine repository from /etc/apt/sources.list and then run sudo apt-get update before continuing). To install wine, I need to specify the version on checkinstall so it works. For example, with the 1.1.12 version, I did this:
```

sudo checkinstall --fstrans=no --pkgversion=1.1.12

```
Answer yes to everything, add a minor comment to the package if you like, and you'll have wine installed.

[SIZE="5"]**2. Patching Wine**[/SIZE]

This instructions can be followed any number of times you want, for all the patches you want, after going through the installation as explained above. Take care though, that it might be possible that patching one application will affect another one.

Almost all patches can be downloaded from internet. So, Ill suppose you have the URL of the patch (referred as <URL>). First, we will create a folder to store your patches on your home folder:
```

mkdir ~/wine-patches

```
Then we download the patch:
```

wget <URL> -O ~/wine-patches/<PATCH>

```
Where <PATCH> is the name you want for the patch. If you have more than one patch, you need to download each one separetaly. Then, patch and compile wine (Compilation will take MUCH less time than before):
```

cd ~/wine-git
patch -p1 < ~/wine-patches/<PATCH>
make

```
If you have more than one patch, run the patch command for each patch before compiling. Finally, you must install it againg with checkinstall:
```

sudo checkinstall --fstrans=no --pkgversion=1.1.12

```
and TADA! you have a patched wine installed.

[SIZE="5"]**3. Updating Wine**[/SIZE]

To update wine, first you need to update your sources:
```

cd ~/wine-git
git reset --hard origin
git fetch
git rebase origin

```
Then you should apply your patches as explained in the previous section, compile, and install (I suppose here the version changed form 1.1.12 to 1.1.13 so I change that on checkinstall):
```

cd ~/wine-git
patch -p1 < ~/wine-patches/<PATCH>
make
sudo checkinstall --fstrans=no --pkgversion=1.1.13

```
(REMEMBER TO RUN THE PATCH COMMAND FOR EACH OF YOUR PATCHES)

[SIZE="5"]**4. Undoing patches**[/SIZE]
To undo patches, you can try two different methods, number 1 is a sure way to go, but is time consuming cause you need to recompile everything, and number 2 should compile swiftly, but I havent personally tried it. I recommend trying number 2 first, and if it fails, trying number 1.

[SIZE="4"]*Method 1: Slow but sure...*[/SIZE]
If a particular patch ruined your installation, then you have to recover the original sources, apply the patches you want to use (obviously, omitting the one that left a mess), recompile and install:
```

cd ~/wine-git
git reset --hard origin
patch -p1 < ~/wine-patches/<PATCH>
make
sudo checkinstall --fstrans=no --pkgversion=1.1.13

```
**Remember to run the patch command for all your patches but the one that caused conflicts!**

[SIZE="4"]*Method 2: swift, but untested*[/SIZE]
However, the precious procedure will have to recompile everything and so, it will take quite long. The unsure way to do this while avoiding (I mean unsure cause I havent test it) is to unpatch your sources:
```

cd ~/wine-git
patch -p1 -R < ~/wine-patches/<PATCH>
make
sudo checkinstall --fstrans=no --pkgversion=1.1.13

```
Where the patch command should be run for all patches you wish to undo. This should take much less time than compiling with the first method. If it works for you, please let me know...

[SIZE="5"]**5. Wine prefixes, or as I like to call them, BOTTLES!**[/SIZE]

Next, Ill explain an additional topic, BOTTLES!. Bottles (actually called wine prefixes, but I got accustomed to this term) let you encapsulate different applications, and apply particular tweaks only to the envorionment of a particular application. Here Ill explain how to install an application in a bottle, run the wine configuration utility winecfg, downloading windows dlls and setting as native, and uing winetricks, all these for an specific bottle so we dont mess with other applications configuration.

[SIZE="5"]**5.1 Keeping all your application on separate "bottles"**[/SIZE]

It is highly recommended to keep all your applications on separete "bottles" with they're own tweaks. This is because the tweaks for one application usually render other ones useless. To do this, lets create first a directory to keep all your bottles (You only need to do this once!):
```

mkdir ~/wine-bottles

```
Then, to install an application, do the following:
```

export WINEPREFIX=/home/<YOUR-USERNAME>/wine-bottles/<BOTTLE-NAME>
wine <PATH-TO-INSTALLER>

```
So, for example, if I want to install spore, Ill call the bottle spore, my username is pablo, and the installer is in /media/cdrom0/SPORESetup.exe and the previous commands would read:
```

export WINEPREFIX=/home/pablo/wine-bottles/spore
wine /media/cdrom0/SPORESetup.exe

```
And thats it!

[SIZE="5"]**5.2 Running winecfg to configure different bottles**[/SIZE]

There are some windows applications that I prefer to keep windowed, while others full-screened. Another advantage of bottles is that you can configure this and many other stuff with winecfg for each bottle independently. To run winecfg for a bottle, you must open a terminal, specify the bottle, and run winecfg:
```

export WINEPREFIX=/home/<YOUR-USERNAME>/wine-bottles/<BOTTLE-NAME>
winecfg

```
And go ahead and configure all you want!

[SIZE="5"]**5.3 Set a dll as native on a bottle**[/SIZE]

To use a downloaded dll as native for an specific bottle, you must download your dll and put it at the appropriate place in the appropriate bottle. The folder where you must put the dlls is:
```
~/wine-bottles/<BOTTLE-NAME>/drive_c/windows/system32
```
(In case you dont know, ~/ is equal to /home/<YOUR-USERNAME>/)

Then, open the winecfg application for the bottle as mentioned in the previous section, select libraries, look for your dll, and set it as native.

[SIZE="5"]**5.4 Use winetricks with a bottle**[/SIZE]

winetricks is an usefull app to install common packages needed for some applications. Usually, the versions required for different applications vary, for instance, some applications work with dotnet 1.1, and others with dotnet 2.0, so By keeping things on separate bottles, you can solve this.

First, lets download the winetricks script and make it executable (You only need to do this once). Ill keep winetricks on the wine-patches folder:
```

cd ~/wine-patches/
wget http://www.kegel.com/wine/winetricks
chmod +x winetricks

```
Then, you can run winetricks with the console, specifying first the bottle, and the running winetricks:
```

export WINEPREFIX=/home/<YOUR-USERNAME>/wine-bottles/<BOTTLE-NAME>
~/wine-patches/winetricks

```
[SIZE="5"]**5.5 File association**[/SIZE]
To associate a specific file type in gnome with a wine application, first, create an executable for your application in /usr/bin (**WARNING: BE SURE NOT TO OVERWRITE ANYTHING ON /usr/bin**).First, create an open the file to edit it:
```

sudo gedit /usr/bin/<LAUNCHER-NAME>

```
Here <LAUNCHER-NAME> is the name of the file that will launch your application. **REMEMBER NOT TO OVERWRITE ANYTHING UNDER /usr/bin**. On the editor, add this content to the file and save it:
```

export WINEPREFIX=/home/<YOUR-USERNAME>/wine-bottles/<BOTTLE-NAME>

wine "<PATH-TO-EXE>" "`winepath -w "$*"`" 

```
Remember to change <YOUR-USERNAME> and <BOTTLE-NAME> accordingly, and where it says <PATH-TO-EXE> put the path of your program .exe file. If you are not using bottles, drop the line that starts with export. Then, make this executable:
```

sudo chmod +x /usr/bin/<LAUNCHER-NAME>

```
Then, on a file you want to associate to this application, select "open with another application", then choose "use custom command", and put this:
```

/usr/bin/<LAUNCHER-NAME> %f 

```
After that, your files should be correctly associated.
[SIZE="5"]**6. Conclusions**[/SIZE]

Well, I hope this helps someone. If something can be run with wine, then by following this instructions together with specific instructions for the installation of the application (such as patches, extra things needed, etc) you should get it done, as long as there are no hardware specific problems that affect you. Almost all the application-specific info you need can be found at appdb ([http://appdb.winehq.org/](http://appdb.winehq.org/)).

Bye!

---

### Post by cristian.palmas on 2009-03-29
Hi,

I'm a newbie on kubuntu and wine and I need a further explanation since I DID NOT find any article that explains directly how to install different versions of wine on the same PC on Linux and how to use them for the applications.

Let's see a practical example.
I need to use IEs4Linux for work and the best wine version on which that software was tested is 0.9.58 (anyway I think the 1.0.1 can work as well and it is the latest stable version).

But I want to install games too, and from the AppDB I found that the games I want run best on certain wine version, such as 1.1.17, 1.1.11, 1.1.14 and so on.

So, If I don't want problems, I need to install, at least, those wine versions:
wine-1.0.1
wine-1.1.11
wine-1.1.14
wine-1.1.17

The tutorial you wrote is really useful but it seems to me that is focused on make different applications work on the same wine version (in your example, the 1.1.12 version).

So my question is, how your instructions may be changed in order to install different wine versions and use them for the right applications?

Thanks in advance

---

### Post by orlox on 2009-03-29
Dont know precisely how to use es4linux on newer wine versions, but for the games on appDB, you should consider that even though the last test result shows wiine version 1.1.15 (for example) it will most probably work just as good or better with the latest version, 1.1.18 in this case.

Cases where older versions of wine are more suitable are scarce...

If you want to get IE running, you can probably pass through the winehq forums and ask them (if you find oout how to it, please tell me here!)

---

### Post by cristian.palmas on 2009-03-30
> **orlox said:**
> Dont know precisely how to use es4linux on newer wine versions, but for the games on appDB, you should consider that even though the last test result shows wiine version 1.1.15 (for example) it will most probably work just as good or better with the latest version, 1.1.18 in this case.

Cases where older versions of wine are more suitable are scarce...

If you want to get IE running, you can probably pass through the winehq forums and ask them (if you find oout how to it, please tell me here!)

Thanks for the fast answer, Orlox,

It makes me more untroubled about thinking of how to install different versions.
Anyway I noticed that, for example, when I installed GTA San Andreas (original) on the 1.0.1 version everything went well except the graphics rendering which was broken (large rectangles appeared instead of writings). Instead, on the 1.1.17 version (one of the latest) the game did not even start.

The two behaviours are different and so I was feeling more secure to install different versions in order to reduce the probabilities to get wrong behaviours with the software.

Maybe there is something wrong in my hardware configuration (I know ATI video cards give a lot of problems) and probably that's the case, since in AppDB the latest tests about GTA San Andreas are good on 1.1.17 version.
But I'd like to know the same about installing different versions.
Can you help on that?

Thanks again

Cristian Palmas

---

### Post by orlox on 2009-03-30
[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

That thread explains a method to install multiple wines in parallel. Its not precisely simple, but I think thats your way to go.

Beware that it will be a lengthy procedure cause you will have to compile every wine you want to install, and I cant assure you it will work cause I havent tried it...

---

### Post by yeehi on 2009-03-30
I received the following error message 

> configure: error: FreeType 32-bit development files not found. Fonts will not be built.
Use the --without-freetype option if you really want this.


If I now type make at the same terminal I get the following output:

>  *** No targets specified and no makefile found. Stop.

What should I do?

---

### Post by orlox on 2009-03-30
Perhaps you're missing the freetype developement files (wich would be strange since the howto includes the installation of the build dependencies for wine).

On a terminal run:

```

sudo apt-get install libfreetype6-dev

```

And try configure again.

I heard there were some issues with the dependencies when you use a 64 bit OS, is that by any chance your case???

---

### Post by orlox on 2009-03-30
According to the winehq wiki. To compile on ubuntu 64 bits, you have to create several links to system libraries:

```

mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
ln -s /usr/lib32/libgnutls.so.13 `pwd`/lib32/libgnutls.so

```
This will create a lib32 folder on your home.

Afterwards, instead of the configure command mentioned, you use this:

```
CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v

```
And then you can proceed with the make command

---

### Post by yeehi on 2009-03-30
Yes, it is 64 bit!

I will try and use your suggestions. Do I just copy/paste/enter that entire block of code in one go?

Thank you for writing this very good tutorial, by the way. And thank you again for retyping it after it had all been lost when you first tried to save it! You must have needed some camomile tea after that!

---

### Post by warosenoff on 2009-04-24
Thank you for this guide, I am new to Linux and not really comfortable with the terminal.
Is there a way to check which version of wine I currently have installed?

Also if I need a newer version, will I be able to keep applications I already have in the .wine directory?

I am trying to run Command and Conquer Generals, and the WineHQ web site says that it should work fine if I have at least V1.1.11. The game seems to be working fine except that the mouse cursor does not display on screen.

Thanks again for the help.

---

### Post by orlox on 2009-04-24
press alt+F2, type winecfg and run. This will open the wine configuration utility, if you choose the tab about, you can see your wine version.

How did you installed wine anyway???

---

### Post by ssdt on 2009-04-24
I think it would be better if the sypnetec gave the latest version of Wine because then the installation would be much easier and you didn't have to follow these steps. But thanks for them though.

---

### Post by orlox on 2009-04-24
The reason why synaptic doesnt have the latest version is because its a development version. After updates it usually has important regressions which are not acceptable in a stable OS. When wine gets out a new stable release, that will become part of ubuntu.

In any case, you can enable the winehq repository (I explain that at the top of the howto) to get the latest wine from synaptic, with automatic updates. The instructions for that are really simple and you dont need to compile a thing...

---

### Post by warosenoff on 2009-04-24
> **orlox said:**
> press alt+F2, type winecfg and run. This will open the wine configuration utility, if you choose the tab about, you can see your wine version.

How did you installed wine anyway???

I'm not actually sure how wine got installed, I think I clicked on "add/remove" under the Applications tab before I installed Starcraft.

Version said 1.0, I just backed up the stuff from my wine c drive to an external hard drive, and followed the instructions you had to remove wine.  Now I am following your instructions on how to install the latest version without patches, it looks like v1.1.19 is currently installing.

I will let you know how it works out.  Thanks again for the help.  Very simple to follow guide too so far.

---

### Post by orlox on 2009-04-24
In any case, if you dont need to patch anything, just follow the steps described at the beggining (under where it says "important note!"). Those few commands will install wine and will allow for automatic updates.

If you do need patching, then you should follow everythin g mentioned after the introduction.

---

### Post by warosenoff on 2009-04-24
Now that I have v1.1.19 of Wine installed, game play seems to work perfectly.  Videos and load times seem to be a little slow, I think this may be because of the no-cd crack. Load times were pretty slow even with the cd in windows though I guess.  I have not tried a network game yet, the wine web site says it will not work in V1.1.16, fingers crossed.

Thanks for the help.  

Great job on this guide too.  I have only been using Linux for a few weeks now and I had no trouble with these instructions.

---

### Post by mamamia88 on 2012-11-17
Oops wrong thread

---

