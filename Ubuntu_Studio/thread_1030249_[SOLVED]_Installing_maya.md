---
title: "[SOLVED] Installing maya"
date: 2009-01-04
forum: Ubuntu Studio
---

### Post by vegetali on 2009-01-04
I want to install autodesk maya 2009 software on Ubuntu 8.10, 64bit. The maya installer is suited for Red Hat/Fedora distros, but it should be possible to install it on Ubuntu. There are a lot of posts, even on ubuntuforums, about how to do it. The problem is that every post suggests a completely different procedure, and most of the people in the discussions say they had problem to follow that procedure. Is there anybody who successfully installed maya 2009 on Ubuntu 8.10, and may want to describe the procedure or give a link?

I wonder whether a simple install using rpm will work.
thx

---

### Post by vegetali on 2009-01-06
Ok, it's easy. The software is distributed for installation with rpm, the red hat package manager. Of course, there is a debian port of rpm. I will describe the procedure, trying to make it as easy as possible. There are a few command lines to be typed in the terminal, but even newbies can install this easily.

1- Install the debian packages "rpm" and "chs". You can do this via synaptic or opening a terminal and typing
```
sudo apt-get install rpm csh
```
Here and hereafter, insert your root password when required.

2- In the terminal, go to the directory in which the rpm files are. For instance
```
cd maya/linux-amd64/
```
or in general
```
cd [rpm package directory]
```

3- In the terminal, type
```
ls
```
to have a list of the files in the directory.

4- In the terminal, install the rpm files using the utility rpm
```
sudo rpm -ivh --nodeps AWCommon-XXX.XXX.x86_64.rpm Maya2009_0_64-2009X-XXX.x86_64.rpm
```
where you should replace XXX.XXX with the actual build number of your files. You can see this numbers in the list in 3-, or simply press "Tab" while typing the name of the files in the terminal.

5- Create a temporary directory for maya (this step may be unneeded most times, but it won't hurt in any case)
```
sudo mkdir /usr/tmp sudo chmod 777 /usr/tmp
```

6- Start Maya by writing in the terminal
```
csh usr/autodesk/maya/bin/maya
```

7- Insert your license data to have the softwae up and running.

8- Next time, it is enough to type
```
csh usr/autodesk/maya/bin/maya
```
in the terminal to launch maya. As this is quite annoying, you can instead press "Alt+F2" and write this command in the command line then appearing. By the way, the best option to launch maya, is to create a panel launcher with this command. Right click on the panel, press "Add to panel", click on "Custom launcher", chose a name for the laucher (for instance "maya"), and use "csh usr/autodesk/maya/bin/maya" as command. You can also add the laucher to the menu.

9- Enjoy a perfomance boost by using maya on linux :-)



----Credits to http//stackoverflow.com/questions/294891/how-do-i-install-autodesk-maya-2008-on-ubuntu-810-64-bit

---

### Post by skullmunky on 2009-01-11
It ought to install links to maya and fcheck in /usr/local/bin, so you ought to be able to launch maya just by typing 'maya' in the shell too.  

Maya ought to show up in the Applications menu too, in Graphics.

I always do this using alien to convert from RPM to DEB first; I wonder if that makes any difference?

---

### Post by bangee on 2009-01-12
Hi all! does anybody has been in same trouble than me?
This is the [[COLOR="Blue"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1032388") to my problem
thanks to everybody ^^

---

### Post by bebin on 2009-01-14
hi everyone i installed maya 2009 on ubuntu it showes 
 
sh: apcw: not found

what  could be the problem please help me on this

---

### Post by skullmunky on 2009-01-15
> **bebin said:**
> hi everyone i installed maya 2009 on ubuntu it showes 
 
sh: apcw: not found

what  could be the problem please help me on this

Never seen that before, but have a look at the monster "Installing Maya on Ubuntu" thread, maybe there's something in there:

[http://ubuntuforums.org/showthread.php?t=66859&page=35]("http://ubuntuforums.org/showthread.php?t=66859&page=35")

Ihe thread title is "Installing Maya 7" but over the years it's grown to be a treasure trove of info and troubleshooting tips for each new version as well.

---

### Post by vegetali on 2009-01-20
did you install the package csh  ?

---

### Post by barx on 2009-01-31
All done guys. I got Same problem:

```
[COLOR="Red"]apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64[/COLOR]
```

but you need to do two steps more for Amd 64 like I am.



```

[COLOR="Sienna"]sudo apt-get install getlibs

getlibs maya[/COLOR]

```

and then, Finally, enjoy Maya. This worked in 2009 version, Ubuntu 8.10 AMD Thurion 64x2

---

### Post by barx on 2009-04-09
Guys, no matter how I want to thank you all.

Recently the HD of my laptop cursed a failure, and ubuntu was unable to reinstall it. I hope to buy another disk. 

Also in **[COLOR="Blue"][SIZE="3"]Fedora 8[/SIZE][/COLOR]**   worked! But the rpm packages seems to be cursed or something.
The double-click packages returned me many errors.

What  did I do? Unistall them, use your instructions and one more steps:

```
[COLOR="Blue"]yum whatprovides libXp.so.6[/COLOR]
```

and the it returned me something like this 

```
libXp-1.0.0-8.fc8.i386 : Biblioteca de tiempo de ejecución de X.Org X11 libXp
Repo        : fedora
Matched from:
Other       : libXp.so.6



libXp-1.0.0-8.fc8.i386 : Biblioteca de tiempo de ejecución de X.Org X11 libXp
Repo        : installed
Matched from:
Other       : Provides-match: libXp.so.6

```

The final step is:

```
[COLOR="YellowGreen"]yum install libXp[/COLOR]
```

of course you have to be root.

The tutorial is universal for every linux distributions also for red hat distro's that have problems.

Yes, it installs, but never load main screen

[SIZE="4"][COLOR="Sienna"]Congrats Ubuntu Team[/COLOR][/SIZE];)

---

### Post by mickie.kext on 2009-05-14
> **bebin said:**
> hi everyone i installed maya 2009 on ubuntu it showes 
 
**sh: apcw: not found**

what  could be the problem please help me on this

I have same preoblem, but solution is nowhere to be found. How did you solwe that? Please...

---

### Post by fraserad on 2009-05-17
I get the exact same problem I follow all the instructions without any errors and then when i try and run Maya I get an error that says

```
sh: apcw: not found
```Does anyone know how to fix it??

---

### Post by arianos10 on 2009-05-29
Me too. I also figured out that the AWCommon packages are not suitable for amd64 architectures (Well thats what the alien convertion-to-deb log says), so i can't convert them to deb in order to install them. Does anyone know if this issue is responsible for the apcw error ???? :(:(

---

### Post by skullmunky on 2009-05-30
see also this thread:[http://ubuntuforums.org/showthread.php?t=1153363]("http://ubuntuforums.org/showthread.php?t=1153363")

apcw is the product activation wizard.  it should be in /usr/autodesk/maya{yourversion}/bin.  where maya{yourversion} is, for example, maya2008, maya2009, maya2008-x64, maya2009-x64, etc.  

try running it from the shell directly.

if you are running 64 bit, and it complains about ELF CLASS, install ia32-libs.  

You don't need anything in the AWCommmon packages unless you are running a license server.  If you have a standalone license, just put it in /var/flexlm as usual.

---

### Post by barx on 2009-06-22
That's new, if **[COLOR="DarkOrange"]getlibs[/COLOR]** or the **[COLOR="DarkRed"]ia32-libs[/COLOR]** didn't help you out paste your process in terminal here.

Also check if you miss one step like **[COLOR="SeaGreen"]csh[/COLOR]** or **[COLOR="YellowGreen"]rpm[/COLOR]**. Somethimes we forget one step xD.

Also install **[COLOR="Blue"]chkconfig[/COLOR]**, sometimes Maya asks you to show the License instalation log

---

### Post by babygenius55 on 2009-07-29
I was having the exact same problem. In short, if your file name are all caps... your file names are probably truncated.

This is an excerpt from a post I made to... [http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)

 The problem was that I was mounting an ".iso" file and when I used the terminal to copy, the names were changed. I'm pretty suer they were truncated while they were mounted, but not certain. anyway I just double-clicked on the iso, and navigated my way to the LINUX64 folder, and I noticed it right away.(That the file names were being truncated) I guess using the archiver would be the way to go. I find it strange that noone ever mentioned this.  I really am sorry for all the caps.

---

### Post by barx on 2009-10-31
In the realease of Ubuntu Karmic, the sudo rmp -ivh --nodeps "rpm pacages" here's what it tells me:

[COLOR="DarkRed"]
**rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.**[/COLOR]

Curiosly I installed Karmic in the free space of my Hard Disk and mounted the another disk

I copied the [COLOR="DarkOrange"]/usr/autodesk[/COLOR] and /[COLOR="DarkOrange"]usr/aw[/COLOR] folders to the /usr folder of the karmic partition, then I runned the command /usr/autodesk/maya/bin/maya to run it. Then appeared the installation log and installed again my licence.

There is one point good and one bad

[COLOR="Lime"]Good[/COLOR]: If you have installed succesfully Maya in a ubuntu's old version -not karmic- pasting all configurations that made maya to work, it would be no problem in look for library errors and things like that.

[COLOR="Blue"]Bad[/COLOR]: If you install ubuntu 9.10 from zero and buy maya cd, open the destination and run the commands, also try to convert rpm-packages into alien, for some reason it doesn't let you do it.

Guy's, What do you think about this? Is there a politic's behind rpm and Debian? Has the turkey less fats than chicken?

---

### Post by misterbk on 2009-12-06
Hey guys, I just finished installing Maya 2009 x64 on Ubuntu 9.10.

If you're getting this error:
**sh: apcw: not found**

I had this for a while and solved it by licensing to a different MAC address.  My Windows install was using the MAC address of the currently connected ethernet port, which in Linux turns out to be **eth1**.  Seems on Windows, you can use the MAC address of any adapter, but Linux is picky.

Used the MAC address from **eth0** and it worked immediately.

BTW I've seen people having problems with Maya licensing on laptops.  If you use the MAC address of a wifi adapter, you will lose your Maya license whenever you turn off the WiFi switch.  (e.g. to save battery life or use it on an airplane.)  Just one more way to have licensing issues!

---

### Post by misterbk on 2009-12-06
> **barx said:**
> 
[COLOR="Blue"]Bad[/COLOR]: If you install ubuntu 9.10 from zero and buy maya cd, open the destination and run the commands, also try to convert rpm-packages into alien, for some reason it doesn't let you do it.

Guy's, What do you think about this? Is there a politic's behind rpm and Debian? Has the turkey less fats than chicken?

I installed Maya 2009 X64 from bare RPMs onto Ubuntu 9.10 and got it working.  There are a few graphical glitches, like font sizes in menus, and the hotbox and context menu vanishing.  (Happens when you switch desktops.  Minimize and restore Maya to bring them back.)

I followed this guide:
[http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/]("http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/")

Interesting note: Not all RPMs converted.  Only the main Maya RPM and the Maya Docs RPM made it into .DEB form.  So, I'm missing all "Maya Common" files, but that doesn't seem to matter.  (yet?)

I'm also getting images back from Mental Ray renders.  (Seen issues reported with that too.)

---

