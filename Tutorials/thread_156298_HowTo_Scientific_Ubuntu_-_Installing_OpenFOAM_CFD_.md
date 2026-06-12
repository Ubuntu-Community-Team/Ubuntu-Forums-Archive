---
title: "HowTo: Scientific Ubuntu - Installing OpenFOAM CFD software"
date: 2006-04-06
forum: Tutorials
---

### Post by derjames on 2006-04-06
I wrote this when using Ubuntu Breeze Badger. Now I am using Hardy (32Bit)... note that version 1.5 has been recently released. 

update 13-Septempber-2008: OpenFOAM release 1.5 is slightly different but easier to install in a stand alone configuration, I will describe the steps here but the old guide (v1.4.1 and older) will still be found in this document just for reference. One of the main changes is the discontinuation of FoamX, from now on the configuration files are to be modified by using your favorite text editor. The other main change is the use of paraview 3.0

The instruccions for installation are:

(1)Create the OpenFOAM folder in you home
(2)navigate to the OpenFOAM webpage and download from there the five installation files:  OpenFOAM-1.5.General.gtgz,  OpenFOAM-1.5.linuxGccDPOpt.gtgz, OpenFOAM-1.5.linuxGccSPOpt.gtgz, ThirdParty.General.gtgz, ThirdParty.linuxGcc.gtgz
(3)Extract the files in this location in starting with those marked as *general*
(4)You will see that two new folders are created: OpenFOAM-1.5 and ThirParty
(5)Update your environment variables by adding the following line to our .bashrc script

```
. $HOME/OpenFOAM/OpenFOAM-1.5/etc/bashrc
```

now 'source' the variables with

```
source ~/.bashrc
```

(5)Navigate to OpenFOAM-1.5/bin and execute the foamIntallationTest script

```
./foamInstallationTest
```

Since this is a standalone installation you will see that the script fails to connect to a remote server, however as I said before 'who cares' just ignore this message.

This is all you need to do, OpenFOAM is ready to run. Please see the documentation since some syntax has been changed. 

I found one problem: After finishing a case a file called file.OpenFOAM containing your computation is created which is supposed to open fine when paraview is called, however an error when reading these type of files arises when one is trying to load them. The quick fix is to export the file to VTK by using the 'foamToVTK' utility and then opening the exported file normally with paraview.

Cheers
j

update 25-february-2008: WIndows users willing to install OpenFoam under XP/Vista read this guide and the advice by "Florante" from the andLinux forum here: 
[http://www.andlinux.org/forum/viewtopic.php?t=44](http://www.andlinux.org/forum/viewtopic.php?t=44)
this will solve the the paraView visualisation problem...

date:23-february-2008: Note to **Windows** users: You may try to install OpenFOAM on Windows XP/VISTA via andLinux ([http://www.andlinux.org](http://www.andlinux.org))  (colinux+Ubuntu) and following the guide below. I've made an attempt and the solvers are working just fine. However paraView for any reason is not working properly. The GUI works OK but the visualisation window is not displaying anything at all (at least on my computer). I will try to check this in the future and/or install any alternative such as OpenDX and post the results here...

Thanks everybody for your comments... enjoy

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 

This Thread/Howto is aimed to all Engineers, Scientist, Students interested in learning/applying/experimenting Computational Fluids Dynamics (CFD), CFD uses numerical approximation to the partial differential equations that govern flow of fluids in nature (i.e. Navier-Stokes equation, etc) the solution of the Navier-Stokes equation once it comply with the requirements of the Continuity equation gives the behavior of the fluids subject to the given boundary and initial conditions. This has a tremendous importance since practically any fluid can be simulated/modeled in a computer before doing any 'real life' experiment. For example you can test the design of a new aircraft using computational techniques before even build a small scale protitype for wind tunnel testing. Thus a wide range of experimental conditions can be fully tested and corrected on the fly...
Since the basic equations (full) that govern fluid flow are in form of PDEs, the numerical methods to approximate the solution are complex, a very simple problem can be solved in a couple of minutes however if the problem is much more complicated the solver can take days in find a solution... in general CFD is not intended for common PCs but for high end computers designed to tackle this kind of problems. Of course this cannot stop you, you can install this software in your computer and 'play' with simple geometries and doing a lot of assumptions to solve a given problem more easily.
There are several CFD brands out there like Fluent, COMSOL, CFD-RC, CFD-ADAPCO, (which are quite expensive though) ... however there are also free alternatives like ELMER Multiphysics (I have already dowloaded but not playing around with it!), OpenFOAM and many others.
Inherently CFD software is a bit complicated to use, it requires a deep understanding of the physical phenomena involved in given problem, and a good mathematical background (this is a plus)

Well, after that boring introduction, this is the ultimate guide to install OpenFOAM in an Ubuntu System, I decided to this because (1) I do really need a CFD software to experiment with. (2) Commercial software is expensive (you know as a student you've got a very limited budget, I would have to spend all my year savings only for a one year license!!!!) (3) Help the scientific/student community with freely available tools. (4) Understand more about the world/nature around us...

* * * Step One * * * *
First of all System requirements (well based on my PC!!!!)

-An x86 processor or equivalent. I am using a Core 2 Duo T5600 and running great!)
-640 MB (The web page states nothing, but everybody knows the more, the better)
-1 GB hard drive available, this is a must, uncompressed files takes 750 MB, plus the cases, tutorials, grids, etc
-broadband conection (the compressed files are from 50 to 100 MB average) of course you can use dial up and wait 48 hours to download it, it's up to you...
-Ubuntu LINUX 6.10 Edgy Eft (it works also in Dapper and Breeze) , if you download the AMD64 version then use the 64bit LINUX kernel 


2 * * * * * * * * * * * * *
Enter to OpenFOAM web page

[http://www.openfoam.org](http://www.openfoam.org)
or
[http://www.opencfd.co.uk](http://www.opencfd.co.uk)

3 * Click on download
4 * Select your version
5 * Dowload all the packges to your Desktop  (very advance LINUX users can avoid obvious steps)

```
~/Desktop
```

where ~/ is the home folder for example /home/<username>

N.B from this point it is necesary to remenber that LINUX is CASE SENSITIVE, a mistake can delay you some hours... 

second I did install everything in my home folder which is ~/ it is the recommended option from the web site


6 * create a folder caller OpenFOAM in ~/  using mkdir
copy
OpenFOAM-1.4.General.gtgz
OpenFOAM-1.4.linuxGcc4DPOpt.gtgz
OpenFOAM-1.4.linuxGcc4SPOpt.gtgz
which are on ~/Desktop to the folder you've just created ~/OpenFOAM

7 * create the following folder  (remember LINUX is case sensitive)

```
~/OpenFOAM/linux
```

8 * copy 
gcc-4.1.1.linux.tgz
paraview-2.4.4.linux.tgz
j2sdk1.4.2.os.linux.tgz
which are in ~/Desktop to ~/OpenFOAM/linux

9 * untar avery single file in the following order

OpenFOAM-1.4.General.gtgz
OpenFOAM-1.4.linuxGcc4DPOpt.gtgz
OpenFOAM-1.4.linuxGcc4SPOpt.gtgz
gcc-4.1.1.linux.tgz
paraview-2.4.4.linux.tgz
j2sdk1.4.2.os.linux.tgz

using ```
tar -xzvf <filename>
```
This takes a bit of time

10 * after finishing you will see new directories created in ~/OpenFOAM

11 * now look for foamSystemCheck
which is located at

```
~/OpenFOAM/OpenFOAM-1.4/bin
```

 this is a shell script that we have to execute, however we need to change it to an executable format

type 

```
chmod -v 555 foamSystemCheck 
```

press enter, then type

```
export PATH=$PATH:~/OpenFOAM/OpenFOAM-1.4/bin/
```

press enter, then type

```
foamSystemCheck
```

press enter

At this time, the shell script will call some functions to check if your system comply with the minimum requirements for the installation, Host, username, Linux version, and Network conectivity, however at the end of the process some error occur, just ignore any warning or fatal error about ssh or rsh, this is not needed for the stand alone installation (It doesn't matter what it tells you, just ignore it!!!)

type 

```
chmod -v 755 foamSystemCheck
```

press enter

12 * * * * * *
Now you have to set the environment variables for a correct file access 

The environment variable settings are stored in
 
```
~/OpenFOAM/OpenFOAM-1.4/.OpenFOAM-1.4
```

since I am using the default options in UBUNTU, my shell is BASH and my text editor is gedit, you can use VIM as well

type

```
echo $SHELL
```

(if you are not sure which shell you are using)

now type

```
gedit ~/.bashrc &
```

once in gedit type

```
. ~/OpenFOAM/OpenFOAM-1.4/.OpenFOAM-1.4/bashrc
```

N.B. it is dot, space~/.......
select 
```
file>save
and then file>quit

```
now update the environment typing

```
. ~/.bashrc
```
N.B. it is dot space ~/.......


the environment variables are updated, you can see this if you type

```
echo $PATH
```

We are almost done!!, 
13 **** Now test the installation

look for foamInstallationTest

it is located at

```
~/OpenFOAM/OpenFOAM-1.4/bin
```

in the same way this file is a shell script

type

```
chmod -v 555 foamInstallationTest
```

press enter

in this case you don't need to export the path, since you have already done it...

now type

```
foamInstallationTest
```

press enter

here the shell scrip verifies every directory and assigns to each of them an environment variable (PATH), also this takes a bit of time. However you will see an error at the end of the process, something like this:

test_rsh  unsuccessful_conection_refused*
test_ssh  unsuccessful_conection_refused*

FATAL: No remote shell available (blah, blah, blah, blah, etc....)

It is very simple: who cares, just ignore it.....

well for this new version of openFoam is likely that FoamX does not run in your system if you don't have the** libssl.so.o.9.7** installed. A simple look at synaptic solve this problem... (thanks for orodoni_le  for this). O course you can use OpenFoam without FoamX if you feel comfortable editing text files...

And it's done!!!!!!!

Now open 

```
~/OpenFOAM/OpenFOAM-1.4/doc/Guides-a4
```

you will find there some PDFs with tutorials and very useful examples....


**This section applies only to WIndows users**

Alternative method for installing OpenFOAM in a windows system (2000/XP/VISTA) using andLinux(colinux+Ubuntu).

This method requires to install andLinux which is basically colinux(a linux kernel implementation for windows) xming(an X-server for windows) and Ubuntu. Once andLinux is installed it uses the Windows desktop instead of GNOME/KDE/etc...

Files you need to get:

The andLinux installer. For simplicity I decided to install the minimal version
[HTML]http://www.andlinux.org/downloads.php[/HTML]

The xming mesa-OpenGL version. For any reason the xming-version provided with andLinux interferes with paraView so you need to replace the shipped version with this one 6.9.031
[HTML]http://www.straightrunning.com/XmingNotes/[/HTML]

The OpenFOAM installation files from the places indicated in the guide above.

-The first step is to install andLinux (which is straight forward). After the installation you will notice that the default installation size of andLinux is 2GB so we need to increase the size of the virtual drive for the OpenFOAM installation and also for any other applications you may need. To do this go to the installation directory of andLinux

```
c:\Program Files\andLinux
```

stop andLinux by double clicking at srvstop.bat

Then look for 

```
ImageResizeTool.zip
```

unzip that file in the current directory. Enter to the directory and look for the file

```
toporesize.bat
```

Execute this file. From the window that appears select *find file. Then navigate to

```
c:\Program Files\andLinux\Drives
```

Select base.drv and change the size to at least 3GB with the slider. Click OK

Now navigate to the xming directory at:

```
c:\Program Files\andLinux\xming
```

look for xming.exe and rename it as xming_1.exe (just in case, this is our old version)

Now install the mesa version of xming. Once the installation finishes go to installation directory

```
c:\Program Files\xming
```

and copy xming.exe from this location to 

```
c:\Program Files\andLinux\xming
```

Reboot the computer

Now install OpenFOAM as described in the guide... 
__ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

Well that's all,  have fun 
* * * * * derjames * * * * *

---

### Post by derjames on 2006-04-07
And some screenshots... the first three are running on Linux, the last one running on Windows/andLinux/ubuntu

---

### Post by adamkane on 2006-04-07
Thanks for the great post!

---

### Post by parktownprawn on 2006-04-08
great howto - why don't you post it on the wiki (wiki.ubuntu.com)?

---

### Post by derjames on 2006-04-09
Hello there, I did update the wiki page, just some aesthetic changes ... well back to work...

[https://wiki.ubuntu.com/HowTo_install_OpenFOAM?highlight=%28OpenFOAM%29](https://wiki.ubuntu.com/HowTo_install_OpenFOAM?highlight=%28OpenFOAM%29)

Cheers

---

### Post by xtacocorex on 2006-05-22
I'm going to try this when I get home even though I should wait until Dapper is released since I'm going to upgrade when it's stable. But since /opt on my laptop is a separate partition, I might do it anyway since it shouldn't change too much.

derjames, have you tried any of the converting Fluent/Gambit meshes to openFoam yet? I'm assuming that it doesn't do mesh generation as that's what I got from the site. Please correct me if I'm wrong.

---

### Post by derjames on 2006-05-23
Hi xtacocorex

You can convert Gambit grids to OpenFOAM format by using the utilities included in the distribution... also you can create grids using other CAD/solvers packages such as: CFX, EnSight, FieldView, I-deas, Star-CD andconvert them with the plugins (all are included in the distribution)...

OpenFOAM includes a pretty basic mesh generator, which does not  have GUI, i.e. you have to create and modify the mesh information file by hand (in a text file), and then use the mesh tool included which works well for my applications (Flow in microchannels), I know it is a bit tedious but it's OK once you get use to it...

hope this helps

---

### Post by larry on 2006-06-27
[QUOTE=derjames]Hello there, I did update the wiki page, just some aesthetic changes ... well back to work...

[https://wiki.ubuntu.com/HowTo_install_OpenFOAM?highlight=%28OpenFOAM%29](https://wiki.ubuntu.com/HowTo_install_OpenFOAM?highlight=%28OpenFOAM%29)

Cheers[/QUOTE]


Hello,
I simply want to thank you for the excellent job!
My institute has just bought a licence for a commercial code (not exactly a CFD code, but something a PDE solver).
However, OpenFOAM looks like a good tool and I can use free on my laptop.
I am not sure, though, that it will be so easy to jump into modelling (well, I am someone who comes from a different background; it could be different for someone already experienced).
Cheers

Larry

---

### Post by mkw87 on 2006-07-23
I have successfully installed this on a 64 bit Dapper build.  

Key things to note:  
I had to edit ~/OpenFOAM/OpenFOAM-1.3/.bashrc to have in it at the top
```
WM_64="on"
```

I also had trouble with it not finding the correct directory of:
~/OpenFOAM/OpenFOAM-1.3/....
it always went ~/OpenFOAM/...
so to fix this I manually added the extra directory where it was necessary (for me, that was in the export of JAVA_HOME, where gcc is exported, and in the bashrc file in ~/OpenFOAM/OpenFOAM-1.3/.OpenFOAM-1.3/apps/paraview/bashrc

Feel free to add that to your wiki.

---

### Post by derjames on 2006-08-01
Hey, cheers for this...

---

### Post by derjames on 2006-08-04
Hello there!
Perhaps it is too late for this warning: The instructions given only apply for the 32 bit version of OpenFOAM 1.3, if you try to follow them exactly for the 64 bit compilation you will run into troubles, I do not have a 64 bit machine to test this, so I don't know what could happen. Please see advice by MKW87 above (thanks for this!) and read the release notes included in the OpenFOAM distribution regarding the installation on 64 bit environments...

Cheers

---

### Post by mkw87 on 2006-08-04
> **derjames said:**
> Hello there!
Perhaps it is too late for this warning: The instructions given only apply for the 32 bit version of OpenFOAM 1.3, if you try to follow them exactly for the 64 bit compilation you will run into troubles, I do not have a 64 bit machine to test this, so I don't know what could happen. Please see advice by MKW87 above (thanks for this!) and read the release notes included in the OpenFOAM distribution regarding the installation on 64 bit environments...

Cheers
Actually the installation is the same except for setting 64-bit mode to on, which I noted how to do and added to the Wiki as well.  I'm not sure why I had problems with the directories, that may be related to 64-bit as well, but since I wasn't sure I put it in a general troubleshooting section at the end of the wiki.

---

### Post by derjames on 2006-08-11
Hey,  I've just upgraded my system to Dapper (fresh install) and I had no problems whatsoever during the OpenFOAM installation... I have a feeling it is somewhat slower (It is just a feel)... but any way if you've got one of those fancy dual core processors perhaps you won't see any difference...

Cheers

---

### Post by mkw87 on 2006-08-27
Are you still able to use this program?  One of the recent updates (not sure which) appears to have broken mine, and I cannot get it fixed.  Even though I have it set up for 64-bit version, it does not look in the appropriate folders.  If I echo $WM_64, it says its on, which it should, but when I try to execute FoamX, it looks for java in ~/x/x/x/linux/j2sdk1.4.2_05 instead of ~/x/x/x/linuxAMD64/j2sdk1.4.2_05

Any ideas?

Nevermind, I figured it out.  Not sure what I did though...:roll:

---

### Post by derjames on 2006-08-27
HEllo, mkw87, No problems whatsoever... FoamX still running OK... however in my case I decided not to use FoamX, I change the dictionary files using the text editor (VIM, gedit, etc) and run the solvers from the command line... I think that's faster...

cheers

---

### Post by derjames on 2006-09-06
Hello people,
There is another way to use OpenFOAM, There is a liveCD out there called-CAE Linux based on PCLinuxOS which contains a lot of preprossesing utilities Salomé, Gmesh, etc.,  solvers: including OpenFOAM, Elmer, COde_Aster, etc, and Postprocessing utilities. It can be run as a live CD, it can be installed in hard drive and running in LINUX/Windows using VMware...

[http://www.caelinux.com](http://www.caelinux.com)

running as a live CD, all FEA, FVM solvers are preconfigured so no more installation hassles...

---

### Post by derjames on 2006-11-22
Now running on Ubuntu Edgy - No problems so far...

---

### Post by akkas on 2006-12-07
I have installed OpenFoam successfully in my PC. everything is working fine. But problem is now with paraview. Previously it was working okay. yesterday I have updated some ubuntu applications. After that when I try to open paraview I am getting follwing error message.
--------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Aborted
--------------------------------------------------

Anyone can help me?

Thanks in advance.

---

### Post by adamkane on 2006-12-07
Don't know if I have an answer, but it looks like you have an nvidia video card.

Can you describe what you did previously to get your video card working.

Other threads say you may need to install/update linux-restricted-formats or edit your /etc/X11/xorg.conf file.

---

### Post by bodhi.zazen on 2006-12-16
Nice How-to

This thread has been added to the UDSF wiki.

[OpenFOAM](http://doc.gwos.org/index.php/OpenFOAM)

---

### Post by derjames on 2007-01-20
I was having a look at Openfoam.org and they say that OpenFoam 1.4 is the testing stage (alpha) so it seems it will be available soon to download... As soon is available I will post any news... cheers

---

### Post by arkangel on 2007-01-24
Any idea how to compile it on 64bit ?

---

### Post by in_flu_ence on 2007-01-30
I have tried to install OpenFoam but apparently that what I have gotten when I did my FoamInstallationTest and FoamX

```
influence@inlapence:~/OpenFOAM/OpenFOAM-1.3/bin$ foamInstallationTest
Executing /home/influence/OpenFOAM/OpenFOAM-1.3/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               inlapence
OS:                 Linux version 2.6.17-10-generic
User:               influence
User_config:        /home/influence/.bashrc
Foam_config:        /home/influence/.OpenFOAM-1.3/bashrc sourced correctly.
-------------------------------------------------------------------------------


Checking main FOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR /home/influence/OpenFOAM                 yes       yes
$WM_PROJECT_USER_DIR /home/influence/OpenFOAM/influence-1.3   yes       no
$FOAM_JOB_DIR        /home/influence/OpenFOAM/jobControl      no        yes
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      /home/influence/OpenFOAM/OpenFOAM-1.3    yes  yes  yes

$FOAM_USER_APPBIN    ...-1.3/applications/bin/linuxGcc4DPOpt  yes  yes  no
$FOAM_APPBIN         ...-1.3/applications/bin/linuxGcc4DPOpt  yes  yes  yes
$WM_DIR              ...nfluence/OpenFOAM/OpenFOAM-1.3/wmake  yes  yes  yes
$FOAMX_PATH          ...ations/utilities/preProcessing/FoamX  yes   no  yes
$CEI_HOME            /usr/local/ensight/CEI                   no        no

$JAVA_PATH           ...fluence/OpenFOAM/linux/j2sdk1.4.2_05  yes  yes  no
$MICO_ARCH_PATH      ...mico-2.3.11/platforms/linuxGcc4DPOpt  yes  yes  yes
$LAM_ARCH_PATH       ...c/lam-7.1.1/platforms/linuxGcc4DPOpt  yes  yes  yes
$MPICH_ARCH_PATH     --------- env variable not set ---------            no
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         ...FOAM/OpenFOAM-1.3/lib/linuxGcc4DPOpt  yes  yes  yes
$FOAM_USER_LIBBIN    ...OAM/influence-1.3/lib/linuxGcc4DPOpt  yes  yes  no
$LAM_ARCH_PATH       ...c/lam-7.1.1/platforms/linuxGcc4DPOpt  yes  yes  yes
-------------------------------------------------------------------------------


Software versions
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
gcc      4.1.0     /home/influence/OpenFOAM/linux/gcc-4.1.0/bin/gcc         
java     1.4.2_05  /home/influence/OpenFOAM/linux/j2sdk1.4.2_05/bin/java    
gzip     1.3.5     /bin/gzip                                                
tar      1.3.5     /bin/tar                                                 
icoFoam            ...M/OpenFOAM-1.3/applications/bin/linuxGcc4DPOpt/icoFoam
-------------------------------------------------------------------------------


Checking file/directory permissions...
-------------------------------------------------------------------------------
File/directory                                    Set  Reqd Crit
-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_inlapence        No_entry_for_"inlapence"_in_/etc/hosts       yes 
WARNING: CRITICAL ERROR

Pinging_localHost        Successful                                   yes 
Test_rsh:                Not_active*                                  yes
Test_ssh:                Not_active*                                  yes
FATAL ERROR: No remote shell available.
             Foam1.3 enviroment requires either ssh and/or rsh.
             Contact your system administrator.


-------------------------------------------------------------------------------

The system test has evoked 1 fatal error(s).

The foam installation contains 1 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

influence@inlapence:~/OpenFOAM/OpenFOAM-1.3/bin$ FoamX
Starting NameServer with inet:inlapence:1234 ...
uncaught MICO exception: IDL:omg.org/CORBA/INITIALIZE:1.0 (0, not-completed)

```

Any help? (I have followed the steps as the wiki but somethings seems to be wrong)

---

### Post by in_flu_ence on 2007-01-31
I did somehow solved the CORBR problem by changing the hostname in /etc/hosts

This was from the OpenFOAM forum.

These problems are always one of the following:
- the hostname is not set ('localhost' is not acceptable to Corba)
- the hostname is not (or twice) in /etc/hosts
- only the truncated name is present in /etc/hosts
- some port opening problem due to security

---

### Post by arkangel on 2007-02-13
do you have a ssh service running ?

try with 
# ssh "user"@localhost  

you should login in your own computer

---

### Post by in_flu_ence on 2007-02-15
Install perfectly into 64bit Kubuntu. Straight forward how-to.

Just wonder if I can use the /usr/bin/gcc & the java1.5 rather than having another copy of java in the disk

Also wonder on how to get paraview 2.6 rather than the given 2.4.2.

Solutions will be great.

---

### Post by in_flu_ence on 2007-03-07
For those who would like to use the system installed gcc and java, I have done the following by editing the ~/OpenFOAM/OpenFOAM-1.3/.bashrc (where ~ refers to your home path, e.g. /home/username)

Edit the following lines (the bold part)
```

if [ "$WM_COMPILER" = "Gcc4" ]; then
    export WM_COMPILER_DIR=**/usr**$WM_COMPILER_ARCH
    WM_COMPILER_BIN="$WM_COMPILER_DIR/bin:$WM_COMPILER_DIR/../gdb-6.4/bin"
    WM_COMPILER_LIB=$WM_COMPILER_DIR/lib${WM_COMPILER_LIB_ARCH}:$WM_COMPILER_DIR/lib:
```

&

```

# Java
# ~~~~

# Linux workstation
# ~~~~~~~~~~~~~~~~~
if [ "$machineTest" = "Linux" ]; then

    export JAVA_HOME=**/usr**

    processor=`uname -m`

    if [ "$processor" = "ia64" ]; then
        export JAVA_HOME=/usr/java/j2sdk1.4.2
    fi

```

With this, I can delete the gcc and java folders that were unzippd to the /linux folder or for those going to install, you don't have to download that two package.

Hope it helps.

If someone else has tested this, I guess we can edit the wiki to reflect the changes.

---

### Post by derjames on 2007-04-14
Hello Folks...

OpenFOAM 1.4 has been released... THe good news is that the installation procedure is exactly the same as the version 1.3...

I am doing just some minors corrections to the HOWTO

cheers

J

---

### Post by in_flu_ence on 2007-04-15
Any idea how to upgrade from 1.3 to 1.4 or a clean removal of 1.3 before 1.4 is installed.

To me, i think it is just removing all the files. but i might be wrong.

---

### Post by derjames on 2007-04-17
> **in_flu_ence said:**
> Any idea how to upgrade from 1.3 to 1.4 or a clean removal of 1.3 before 1.4 is installed.

To me, i think it is just removing all the files. but i might be wrong.

What i did was to backup the USERNAME-1.3 folder, then i did a fresh install. at the end a just renamed the folder to USERNAME-1.4

I think this is right...

---

### Post by orodoni_le on 2007-04-30
I use several CFD packages in my work. So far, I've tried Fluent (different versions), CFX (different versions), AirPak and FIDAP. I decided to to test OpenFOAM (1.4 version, 32bits), specially for the software licensing.

Thanks derjames for the great post. I'm a newbie in Linux (Ubuntu 7.04), and your post helps a lot during the installation process. Only one thing. Whe I try to run FoamX from console, i get this error message:

nsd: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory

I went to Synaptic and install the libssl.so.0.9.7 package. Now the FoamX opens without any problem.

Thanks again

---

### Post by derjames on 2007-05-04
> **orodoni_le said:**
> I use several CFD packages in my work. So far, I've tried Fluent (different versions), CFX (different versions), AirPak and FIDAP. I decided to to test OpenFOAM (1.4 version, 32bits), specially for the software licensing.

Thanks derjames for the great post. I'm a newbie in Linux (Ubuntu 7.04), and your post helps a lot during the installation process. Only one thing. Whe I try to run FoamX from console, i get this error message:

nsd: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory

I went to Synaptic and install the libssl.so.0.9.7 package. Now the FoamX opens without any problem.

Thanks again

Yes... thanks for that.. I did not realise about that since I am not using FOamX... (I am editing the text files directly) ...  so I tested FoamX and I had the same problem... the installation of the library solves the problem...
I am editing the howto with your finding

thanks again for that...

---

### Post by Pablitox on 2007-06-24
Thanks man!! I have just installed OpenFOAM 1.4!!!

Only one thing: the package I had to get and install from Synaptic is **libssl0.9.7**

---

### Post by derjames on 2007-08-18
hello folks... version 1.4.1 has been set free... 

[www.openfoam.org](www.openfoam.org)

happy modelling!

---

### Post by happy-hippo on 2007-11-01
thanks derjames for the howto and the others for the hints.
tutorials are running without problems so far (OpenFoam1.4, Feisty, 32 bits) :-)

---

### Post by DanielLloyd on 2007-11-06
Hi guys,

I'm a super ultra Ubuntu newbie, so this is all over my head a little, I've tried installing OpenFoam by following the particularly awesome guide but I cant get it working.

This is what I get:

> Executing /home/daniel/OpenFOAM/OpenFOAM-1.4.1/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               daniel-laptop
OS:                 Linux version 2.6.22-14-generic
User:               daniel
User_config:        /home/daniel/.bashrc
Foam_config:        /home/daniel/.OpenFOAM-1.4.1/bashrc sourced correctly.

FATAL ERROR Foam install directory not set.

Set correct path to installation 'WM_PROJECT_INST_DIR' in /home/daniel/.foam2.3/bashrc
-------------------------------------------------------------------------------


Checking main FOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR --------- env variable not set ---------            yes
$WM_PROJECT_USER_DIR --------- env variable not set ---------            no
$FOAM_JOB_DIR        --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      --------- env variable not set ---------            yes

$FOAM_USER_APPBIN    --------- env variable not set ---------            no
$FOAM_APPBIN         --------- env variable not set ---------            yes
$WM_DIR              --------- env variable not set ---------            yes
$FOAMX_PATH          --------- env variable not set ---------            yes
$CEI_HOME            --------- env variable not set ---------            no

$JAVA_PATH           --------- env variable not set ---------            no
$MICO_ARCH_PATH      --------- env variable not set ---------            yes
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
$MPICH_ARCH_PATH     --------- env variable not set ---------            no
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         --------- env variable not set ---------            yes
$FOAM_USER_LIBBIN    --------- env variable not set ---------            no
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Software versions
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
gcc      4.1.3    
WARNING:  Conflicting installations:
          foam settings: /bin/gcc
          current path : /usr/bin/gcc
          CRITICAL ERROR

java     1.5.0
libgcj)    
WARNING:  Conflicting installations:
          foam settings: /bin/java
          current path : /usr/bin/java

gzip     1.3.12    /bin/gzip                                                
tar      1.3.12    /bin/tar                                                 
icoFoam  *** not installed ***
          CRITICAL ERROR

-------------------------------------------------------------------------------


Checking file/directory permissions...
-------------------------------------------------------------------------------
File/directory                                    Set  Reqd Crit
-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_daniel-laptop    Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Unsuccessful_connection_refused*             yes
FATAL ERROR: No remote shell available.
             Foam1.4.1 enviroment requires either ssh and/or rsh.
             Contact your system administrator.


-------------------------------------------------------------------------------

The system test has evoked 1 fatal error(s).

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.


Sorry if its obvious or been asked and sorted before but I just don't really get it :confused:

---

### Post by DanielLloyd on 2007-11-07
Hi again,

I reinstalled it and this time it seemed to work... I closed Open Foam and the went off and did some work stuff, came back run FoamX again and it all went pair shaped

I know get this:
> daniel@daniel-laptop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ FoamX
Starting NameServer with inet:daniel-laptop:1234 ...
Starting FoamX Host Browser with inet:daniel-laptop:1234 ...
/*---------------------------------------------------------------------------*\
| =========                 |                                                 |
| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |
|  \\    /   O peration     | Version:  1.4.1                                 |
|   \\  /    A nd           | Web:      [http://www.openfoam.org](http://www.openfoam.org)               |
|    \\/     M anipulation  |                                                 |
\*---------------------------------------------------------------------------*/

Exec   : FoamXHostBrowser 
Date   : Nov 07 2007
Time   : 11:31:22
Host   : daniel-laptop
PID    : 18959
Root   : 
Case   : 
Nprocs : 1
HostBrowser running.....
Setting LANG to en_EN
Using jar /home/daniel/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/FoamX.jar
Using jar /home/daniel/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/jlfgr-1_0.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at FoamX.App.<init>(App.java:196)
   at FoamX.App.main(App.java:184)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more
Killed
runFoamXHB : cleanup
runFoamXHB: Killing name server nsd(pid 18957).
daniel@daniel-laptop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ 



I dont get why it worked ones and now it wont. Can someone please help?

---

### Post by zhoubinwx on 2007-11-08
Dear DanielLloyd
I am very glad you have the same problem as me.
According to compare our results with the post in the website: [http://ubuntuforums.org/showthread.php?t=156298&page=3](http://ubuntuforums.org/showthread.php?t=156298&page=3)
I find ours have 2 differences:
1. FATAL ERROR Foam install directory not set.
   Set correct path to installation 'WM_PROJECT_INST_DIR' in /home/zhou/.foam2.3/bashrc
2. we do not set update the environment properly, because you can see &#8220;env variable not set&#8221;

I am a student in Politecnico di Torino, and I am very glad to make progress with you.

Best regards,

Zhou Bin
(zhoubinwx@hotmail.com)

---

### Post by david_flo on 2007-11-30
> **DanielLloyd said:**
> Hi again,

I reinstalled it and this time it seemed to work... I closed Open Foam and the went off and did some work stuff, came back run FoamX again and it all went pair shaped

I know get this:


I dont get why it worked ones and now it wont. Can someone please help?


I installed on an HP laptop, AMD Turion64 X2, Edubuntu 7,1 and OpenFOAM 1.4

First of all it was a real pain to get Edubuntu to boot after successfull installation. Apparently there is something not very nice between HP laps and Ubuntu.

Anyway, I managed to get all the tests ok on the 64 version of OpenFOAM, the examples run etc. FoamX crashes with the same error as Daniel.

I thought it was java not being up to date or missing something as I am using the one on the system instead of the one provided with OpenFOAM, same for gcc.

Even after trying to follow the instructions in posts like
[http://ubuntuforums.org/archive/index.php/t-76735.html](http://ubuntuforums.org/archive/index.php/t-76735.html)
my update manager can't get the updates lists, it says some error 404, could not find the repository.

Regarding the subject in this thread, I would like to know if anyone has experienced the same java related crash with the same versions of the software as myself.

Additionally, in a hopeful tone, if anyone has this same problem updating java, on a different laptop/PC and same software versions, I would really appreciate any inputs.  This is getting very frustrating.

Regards

---

### Post by derjames on 2007-12-13
@david_flo and Daniel.

Open Foam is perfectly OK without FoamX. You just need to use your text editor to modify the config files...

---

### Post by charlesreid1 on 2008-01-12
This worked fine for me with one modification.  The line below:

    export WM_COMPILER_DIR=**/usr**$WM_COMPILER_ARCH

was changed to:

    export WM_COMPILER_DIR=**/usr**

and then running foamInstallationTest worked just fine. I'm running on an AMD 64-bit system.


> **in_flu_ence said:**
> For those who would like to use the system installed gcc and java, I have done the following by editing the ~/OpenFOAM/OpenFOAM-1.3/.bashrc (where ~ refers to your home path, e.g. /home/username)

Edit the following lines (the bold part)
```

if [ "$WM_COMPILER" = "Gcc4" ]; then
    export WM_COMPILER_DIR=**/usr**$WM_COMPILER_ARCH
    WM_COMPILER_BIN="$WM_COMPILER_DIR/bin:$WM_COMPILER_DIR/../gdb-6.4/bin"
    WM_COMPILER_LIB=$WM_COMPILER_DIR/lib${WM_COMPILER_LIB_ARCH}:$WM_COMPILER_DIR/lib:
```

&

```

# Java
# ~~~~

# Linux workstation
# ~~~~~~~~~~~~~~~~~
if [ "$machineTest" = "Linux" ]; then

    export JAVA_HOME=**/usr**

    processor=`uname -m`

    if [ "$processor" = "ia64" ]; then
        export JAVA_HOME=/usr/java/j2sdk1.4.2
    fi

```

With this, I can delete the gcc and java folders that were unzippd to the /linux folder or for those going to install, you don't have to download that two package.

Hope it helps.

If someone else has tested this, I guess we can edit the wiki to reflect the changes.

---

### Post by derjames on 2008-02-23
Hello Folks!, I hope all is well with you...

This is a quick note to Windows users: There is an alternative way to install OpenFOAM in a windows system (XP/VISTA) apart from the CYGWIN build. You need to install adlinux ([http://www.andLinux.org](http://www.andLinux.org)) (colinux+ubuntu) and follow the guide as usual. The solvers work perfectly but in my particular case I have  a problem with paraView (you may o may not have this problem) in which the visualisation window is not working at all. Rather strange because the GUI works fine... anyway I will post any progress here if any...

cheers

---

### Post by derjames on 2008-02-25
OK folks... this is for **windows** Users... please read the following thread at the andLinux forum regarding the problem of paraview visualisation... hope this solve your problem...

[http://www.andlinux.org/forum/viewtopic.php?t=44](http://www.andlinux.org/forum/viewtopic.php?t=44)

I haven't tried yet but I will do it as soon as I can...

cheers
j

---

### Post by Chegdan on 2008-06-04
First of all, I used this thread a few months ago when I installed OF on 7.10 and it help immensely.  Now, I'm compiling OF-1.4.1-dev on 8.04...and man do I have problems with it.  I have read the OF wiki on how to compile openfoam, but it is difficult to do.  That particular wiki post was based on someone who had successfully compiled OF on opensuse before and therefore had all of the required libraries and such on their computer.  Therefore, this makes the compiling of OF straightforward (not really but ok).  So I ask, has anyone compiled OF on ubuntu from a completely vanilla version of 8.04?  If so, did you document it?  If you did...how about a nice descriptive post?  I really need this compiled in order to access a few of the additional models offered only in the dev version...and I kinda prefer to use Ubuntu over opensuse.  Any help is much appreciated.

---

### Post by derjames on 2008-09-13
Perhaps a bit late but OpenFOAM-1.5 has been released...

[http://www.opencfd.co.uk/openfoam/version1.5.html#version1.5](http://www.opencfd.co.uk/openfoam/version1.5.html#version1.5)

Comments about the installation have been added to the guide...

cheers

---

### Post by waspbr on 2008-09-17
I thought I would make myself useful and contribute to this thread. Thanks to this thread, a few fresh installs and extensive googling OpenFOAM 1.5 now runs well in my 32 bit box.

in order to make paraview read the foam files, it needs to be compiled. 

to do that you need those two packages:
```

libmpfr-dev

libmpfr1|dbl
``` 

you can just get them in synaptic, if you don't get them the compilation is going to give you errors. then enter the following commands in terminal

for paraview


 ```
cd $FOAM_INST_DIR/ThirdParty
rm -rf ParaView3.3-cvs/platforms
buildParaView3.3-cvs
```

The compilation is going to take a while, a very long while. just leave you machine running and go do something else.

now for the reader



    ```
cd $FOAM_UTILITIES/postProcessing/graphics/PV3FoamReader
./Allwclean
./Allwmake
```

don't try to navigate to the directories yourself, just copy and paste the terminal cd commands above and all should run smoothly.

cheers

---

### Post by bigbrovar on 2008-09-18
Thanks for the great how to .. am the system admin for the African [University of Science and technology]("http://aust.edu.ng") we run ubuntu on all our lab computers and i would like to add OpenFOAM to our list of softwares .1 question though .. how do i install OpenFOAM so that its accessible by more than one user . if i follow your guide and do the installation in /home/username .. then other users to the system wont have access to the program .. is it a must to use /home or can i use /opt instead . and if i did would it work ? sorry for my bad english

---

### Post by mediocreguitarist on 2008-10-07
Hello
I am new to ubuntu (have first year uni computing knowledge and C, C++ programming) and also new to OpenFOAM. I am running openfoam 1.5 on hardy and when i try to run it i get this message....
james@ubuntu:~$ icoFoam

/*---------------------------------------------------------------------------*\

| =========                 |                                                 |

| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |

|  \\    /   O peration     | Version:  1.5                                   |

|   \\  /    A nd           | Web:      [http://www.OpenFOAM.org](http://www.OpenFOAM.org)               |

|    \\/     M anipulation  |                                                 |

\*---------------------------------------------------------------------------*/

Exec   : icoFoam

Date   : Oct 07 2008

Time   : 15:23:31

Host   : ubuntu

PID    : 6465

Case   : /home/james

nProcs : 1


// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

Create time




cannot open file


file: /home/james/system/controlDict at line 0.

    
From function regIOobject::readStream(const word&)
    
in file db/regIOobject/regIOobjectRead.C at line 66.



FOAM exiting



james@ubuntu:~$ grrrrrr!

I was just wondering if i installed it incorrectly or if i need to change the directory for something etc and how to do it 

(i am also new to web forums so hope i posted in right section etc etc etc)

Thankyou in advance for your help :-)

---

### Post by derjames on 2008-10-26
> **bigbrovar said:**
> ...how do i install OpenFOAM so that its accessible by more than one user . if i follow your guide and do the installation in /home/username .. then other users to the system wont have access to the program .. is it a must to use /home or can i use /opt instead . and if i did would it work ? sorry for my bad english

hello there, you can install OpenFOAM in any directory, you can install it in /opt, /share, /etc or any other suitable directory perhaps as a root or using sudo. However you will need to modify the environment variables since the installation scripts are using $HOME as the main path... I haven't done this but it is not difficult to do it... 

good luck

j

---

### Post by seenxu on 2008-11-11
> **waspbr said:**
> 
 ```
cd $FOAM_INST_DIR/ThirdParty
rm -rf ParaView3.3-cvs/platforms
buildParaView3.3-cvs
```




I am trying this on my amd64, but it end up with the error message

"make: *** No targets specified and no makefile found.  Stop."

any ideas?

but the same command runs well on 32bit

---

### Post by derjames on 2008-11-22
> **seenxu said:**
> I am trying this on my amd64, but it end up with the error message

"make: *** No targets specified and no makefile found.  Stop."

any ideas?

but the same command runs well on 32bit


I think you are running the 32 bit version on linux 64 bits... Did you download the 64 bit version of OpenFoam??

cheers

---

### Post by kjetilbmoe on 2008-11-28
I get the exact same result. It just stops. And I have 32 bit for sure.

---

### Post by kjetilbmoe on 2008-11-28
> **waspbr said:**
> 
 ```
cd $FOAM_INST_DIR/ThirdParty
rm -rf ParaView3.3-cvs/platforms
buildParaView3.3-cvs
```


I don't really know where the error might be. I see from the terminal that it is not totally satisfied with my version of Qt. See attached screenshot.

And ends like this:

```
-- Plugin: Prism enabled
-- Found Qt-Version 4.4.3
-- Configuring done
make: *** No targets specified and no makefile found.  Stop.
done

```

Suggestions on how to rebuild the reader now? Guess openfoam is pretty useless in its current condition ... :(

---

### Post by waspbr on 2008-12-04
your qt is a little too new.

one option would be to get the old 4.3.* packages, but I reckon it is a hastle. 

One odd thing is that in my intrepid 64 machine, everything works, no compilation, no nothing, just untarred the 5 packages .gtgz at my ~/OpenFOAM  directory then did the bash editing found on page 1. 

then the 
```
source ~/.bashrc
```

command. 

I am not sure if compiling is really necessary, compiling paraview can be very painful.

have you tried running a case? 

try making a run directory and try one of the test cases,eg cavity using the following commands (blockMesh > icoFoam > paraFoam). 

if paraFoam gives you the "open with" bug then instead of parafoam do

> foamToVTK

then try running

> paraview 

 @ your case directory

go to open file and you should notice that there is a VTK folder at your case directory, open it and view your results using by opening the last file. 

this is the procedure that I follow in my fedora 9 machine, it is always best to avoid compiling paraview

---

### Post by kjetilbmoe on 2008-12-04
Thanks for your comprehensive reply!
I "reinstalled" the OpenFoam, executed the .bashrc, and the installation test script.
I then copied the *cavity* to a new dir, did blockmesh and icofoam, and finally parafoam. But it still asks for the correct reader.
I then did the foamToVTK, it outputted whatever it did. The funny thing is that when I open the last file - cavity_6.vtk, nothing outputs !? (I'm running from remote and my resulution is quite low). But the only thing outputting is the three colored axis in the middle. Was something wrong with the calculations you think?

---

### Post by waspbr on 2008-12-10
hmm, everytime you re-run a case file, remember to erase the old files, keep your 0 folder (also your constant and system) and remove the rest (I would remove the vtk folder).

also it may help to use the edit color map menu (icon with a colour degrade and a green circle on top) and use the "rescale to data ..." button, this may help.

anyway good luck

---

### Post by basilwatson on 2009-01-06
Hi can someone explain to me how to use the foamToVTK utillity ..I am not sure of the structure of the comands is it 

 $foamToVTK ( name of folder where the output is going) ( path to file to be converted )


Kind regards Stephen

---

### Post by waspbr on 2009-01-26
sorry for the late reply, I haven't checked this in a bit, a PM is going to reach me faster. 

there' s no need to add any further parameters to the foamToVTK command. Once you have run your case file (whether it is building a mesh or using a solver), all you have to do it run foamToVTK inside the case directory, for instance in the cavity example, it would be inside the $FOAM_RUN/tutorials/icoFoam/cavity directory. 

This will automatically a vtk folder inside the case directory directory.

then you can use the command

```
paraview
```

to load paraview and open the files inside the vtk folder, you should see a bunch of folders, the complete vtk files are going to be a the bottom.

---

### Post by jeannot on 2009-02-13
I am more than ready to install Qt4.3.2 on Ubuntu, but I don't find the right package. Any chance that someone did find it?

---

### Post by kjetilbmoe on 2009-02-13
Thanks! This actually works quite well!

One thing with paraview though: the display output is quite bad - it is not displaying the geometry at all at first, or displaying it partly in a "blinds" fashion. Is there a setting I can adjust to fix this?

---

### Post by Lau@raffnsoe on 2009-02-17
Hello 

Thanks for the detailed instructions. But I cant make it work on my ubuntu8.10

I get this error message when building PV3FoamReader
"
[ 45%] Building CXX object CMakeFiles/PV3FoamReader.dir/qrc_PV3FoamReader.o
Linking CXX shared library /home/user/OpenFOAM/OpenFOAM-1.5/lib/linuxGccDPOpt/libPV3FoamReader.so
/usr/bin/ld: cannot find -lpqComponents
collect2: ld returned 1 exit status
make[2]: *** [/home/user/OpenFOAM/OpenFOAM-1.5/lib/linuxGccDPOpt/libPV3FoamReader.so] Error 1
make[1]: *** [CMakeFiles/PV3FoamReader.dir/all] Error 2
make: *** [all] Error 2
"

Does anybode have an idea whats going wrong for me.

Thanks
Lau

---

### Post by maja.ondracka on 2009-03-09
Hello! I have exactly the same problem. What should I do? I tried sudo apt-get install lpqComponents, but it ended up with a message: cannot find package lpqComponents. I am new in Linux, so can anyone help me? Thanks

---

### Post by xfgygz on 2009-03-21
Hello!  I am a noobie for both Ubuntu and OpenFOAM,but quit interested in both of them.
and.. I have a noobie question!

when I try to extract those files with ”tar xzf <filename>”
system reply me a error message "bash: syntax error near unexpected token `newline'"

and I do not really understand this step
(3)Extract the files in this location in starting with those marked as *general*

thanks lot for your help!

---

### Post by waspbr on 2009-04-03
ok, 

the commad I would use to extract the files in this case would be ```
 tar xfzv OpenFOAM-1.5.General.gtgz 


```

use this command in terminal after downloading and copying the files into the newly created /home/<username>/OpenFOAM/ directory

after unpacking the first file, unpack the other ones, just use the same code replacing the name of the file. 

good luck

---

### Post by showerlin on 2009-05-05
I just installed OpenFOAM 1.5 on kubuntu 9,
but as usual.. the ParaView seems troublesome.

This time is not qt issue, I got this message says,

> paraview: symbol lookup error: /usr/lib/libmpi_cxx.so.0: undefined symbol: ompi_registered_datarepsseems something to do with MPI...

any idea?:confused:


Thanks.

-Shower

---

### Post by rieuk on 2009-05-14
Hey guys,

 I have the exact same problem as showerlin. I really need to get this software up and running urgently and am a Lnux n00b. Does anyone have a solution for this?

---

### Post by derjames on 2009-09-19
Just to let you know that OpenFOAM 1.6 and 1.6.x have been released...
I will let you know if I found any issue during the installation.

cheers
j

---

### Post by redrocket5 on 2009-09-23
> **derjames said:**
> Just to let you know that OpenFOAM 1.6 and 1.6.x have been released...
I will let you know if I found any issue during the installation.
 
cheers
j
 
Hi Derjames,  you have done a seriously great job both with Unbuntu and OpenFoam.  I put on andLinux, then Unbuntu and then OpenFoam. 
 
So far so good.
 
Where I simply run out of ideas is managing linux.  For example where your instructions say  ad blah blah to your environment or  just use /.basch and append following  (excuse but I do not have the exact stuff in font of me) I am buggered.I am a windows only user to date so it really overwhelms when need to learn a language and mange a completely unfamiliar system and an application and get it all running.
 
I know you have done step by step but some of the obvious simply isn't, and I'm not dumb.
 
Not meant as any criticism, just hoping that pass on that dumb as dog stuff information/instructions isn't a bad thing for earnest people trying to grab on to all this new stuff.
 
Look forward to your next post.

---

### Post by Blitz Tungsten on 2009-11-01
-edit-

---

### Post by tedk89 on 2009-12-12
"$HOME/OpenFOAM/OpenFOAM-1.6/etc/bashrc"

when running this in the appropriate "home" I am getting a permission denied, and when attempting to run as sudo I am getting bashrc command not found. I am very new to linux so you will have to bare with me.  I also checked echo $SHELL, and the reply was /bin/bash so I am pretty sure this is not the problem. Any help will be appreciated. Thanks!

---

### Post by gbrubal on 2010-03-09
Hi, i have been trying, for the past couple of days, to install openfoam in ubuntu 9.10 64-bit. Now i am very new to the whole linux and openfoam thing, so bare with me. After reading the initial post i decided to erase everything i had and start again from scratch. So far so good, i managed to extract the files without issues, but i can't source the bashrc.

I put this in my bashrc, i don't know if it has to be in any particular line, i put it in the line right before the last one. Now when i type:

~ /.bashrc, i get this message:

bash: /home/gustavo/OpenFOAM/OpenFOAM-1.6/.OpenFOAM-1.6/bashrc: No such file or directory

What i don't get is why its looking for it in OpenFOAM-1.6/OpenFOAM-1.6

It doesnt make sense to me, can anyone help me out?

Thanks in advance!

---

### Post by gbrubal on 2010-03-10
i have solved the problem. I had, mistakenly, modified the bashrc in the openfoam-1.6/etc folder. and when i sourced the $HOME/.bashrc, apparently that created the conflict.

Now, i fixed both files and it worked no problem.

However, i do have a situation with paraview, its not working, apparently i have to update the qt4. Should i do that with the synaptiic package manager?  If, yes, which libqt4 should i get? Theres like a ton of versions, my guess is -sql and -dev.

Thanks again!

---

### Post by Canesin on 2010-04-20
You could also just use the automatic installer script for ubuntu...
It is a opensource project and can be found in:  [http://code.google.com/p/openfoam-ubuntu](http://code.google.com/p/openfoam-ubuntu)

It fix several problems and also do multi-core build

---

### Post by bentleywatson on 2011-05-12
I am searching a new platform for CFD trading.I have Linux in my system.It is beneficial to invest in CFD trading due to less risk.What platform  should i have to use for CFD trading online.
__________________
For more information Visit:[CFD]("http://www.igmarkets.com.au/") and [CFD Provider]("http://www.igmarkets.com.au/cfd/award-winning-service.html")

---

### Post by meballav on 2012-10-09
Hi could you please help me 
how can i update paraview 3.8 to paraview 3.12 or 3.14
using command on ubuntu 11.04

can i use sudo apt-get update312

---

