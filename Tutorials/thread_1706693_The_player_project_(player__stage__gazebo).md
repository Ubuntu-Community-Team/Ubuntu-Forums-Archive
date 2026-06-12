---
title: "The player project (player / stage / gazebo)"
date: 2011-03-14
forum: Tutorials
---

### Post by Morten ML on 2011-03-14
Hi all

I am posting my own "personal" notes on how to install gazebo player and stage here - so i can find it later. Hope this helps anybody else who wants to use these programs. I am currently using Merkat in 64 bit version... But have also tested this approach on a 32 bit machine and it works.

EDIT (20/4-11 and 21/4-11) **Pre-Installation**
Before gazebo - and only gazebo - can be used two programs has to be installed. One of these can be installed from the normal "Ubuntu Software Center" and one has to be compiled from source. The two programs are called "Object-oriented Graphics Rendering Engine" (OGRE) and "Open Dynamics Engine" (ODE). 
Ogre can be installed from the "Ubuntu Software Center" or by pasting the code shown below into a terminal. The three packages are called "ogre-tools", "libceguiogrerenderer-1.6.4" and "libogremain-1.6.4". I am actually not sure if the first two ones are needed, but they are installed on the machine I am using now and gazebo works...
Code for pasting into terminal:
```

sudo apt-get install libogremain-1.6.4 ogre-tools libceguiogrerenderer-1.6.4

```
Now ogre has been installed.

Open Dynamics Engine (ODE) also has to be installed. This program can not be found in the "Ubuntu Software Center" and has to be compiled from source.
This is not hard and a good guide can be found here: [http://playerstage.sourceforge.net/wiki/Install_ubuntu]("http://playerstage.sourceforge.net/wiki/Install_ubuntu")
But what it says is also copied here:
download ode-0.11.1 source code archive: [http://sourceforge.net/projects/opende/files/]("http://sourceforge.net/projects/opende/files/")
extract archive and enter directory
```

./configure --with-trimesh=opcode --enable-new-trimesh --disable-demos --enable-shared --with-arch=nocona --enable-release --enable-malloc --enable-ou --disable-asserts --with-pic
make
sudo make install
sudo ldconfig

```
Dont ask me what the ldconfig command does but after doing this i got gazebo to run... (I haven't tested it without typing ldconfig)

**Optional installations**
gdal 
libgdal1-1.6.0
libgazebo-dev

the latter of these three makes it possible to write a c++ program that connects to gazebo...

**Installation**
adding all of the three (player/stage/gazebo) to ubuntu software center:
from this page: 
[http://playerstage.sourceforge.net/wiki/Download]("http://playerstage.sourceforge.net/wiki/Download")
read it and you get redirected to:
[https://launchpad.net/~thjc/+archive/ppa/]("https://launchpad.net/~thjc/+archive/ppa/")
Now all three programs can be found in the software center. However "player" and "stage" are called "robot-player" and "robot-stage" since other programs already have names of "player" and "stage". For "gazebo" this is not the case...
EDIT (20/4-11): in the software center search for "robot-player" and press the "show 61 technical items" to find player
EDIT (21/4-11):
Instead of finding all the programs in the "Ubuntu Software Center" the code below can be copied into a terminal:
Code for installing gazebo:
```

sudo apt-get install gazebo gazebo-doc gazebo-data libgazebo0

```
Code for installing stage:
```

sudo apt-get install stage stage-player-plugin libstage3

```
Code for installing player:
```

sudo apt-get install robot-player libplayerinterface3 libplayerjpeg3 libplayerwkb3 libplayerc3 libplayerc++3 libplayerdrivers3 libplayertcp3 libplayercore3 libplayercommon3 libpmap0 liblodo0

```
to launch player the code is therefore:
```
robot-player /usr/share/stage/worlds/simple.cfg

```

**Using stage**
To start stage you can enter the code below in a terminal:
```

robot-player /usr/share/stage/worlds/simple.cfg

```
This code has been modified from here [http://playerstage.sourceforge.net/doc/Player-cvs/player/start.html]("http://playerstage.sourceforge.net/doc/Player-cvs/player/start.html")

**Using player with stage**
If you used the above command for starting stage you can now control the robot from player. This can be done by entering the code below in a terminal:
```

robot-playerv --position2d --laser

```
In the window that opens from this command you can click devices->position2d->command. Now you can drag the red target marker and make the robot move.
This command is also a modification from [http://playerstage.sourceforge.net/doc/Player-cvs/player/start.html]("http://playerstage.sourceforge.net/doc/Player-cvs/player/start.html")  

EDIT 22/5-11 **Using gazebo**
To start a gazebo simulation use the code below:
```
gazebo /usr/share/gazebo/worlds/pioneer2dx.world
```
when this simulation is started there should be two robots, rolling down some slides.

**Using player with gazebo**
Inspired by : [http://playerstage.sourceforge.net/wiki/Gazebo:Tutorials:pioneer2dx_moving]("http://playerstage.sourceforge.net/wiki/Gazebo:Tutorials:pioneer2dx_moving")
The same way as player can be used with stage, it can be used with gazebo.
create a *.cfg file as shown below:
```
driver
(
  name "gazebo"
  provides [ "simulation:0" ]
  plugin "libgazeboplugin"
  server_id "default"

# load the named file into the simulator
  #worldfile "pioneer2at.world"
)

driver
(
  name "gazebo"
  provides ["position2d:0"]
##model "pioneer2at_model"
  gz_id "pioneer2dx_model1::position_iface_0"
)
```
Lets assume you named this file "gazebo.cfg"
this script should be run after the gazebo simulation has started. 
After this "gazebo.cfg" file has been run in a terminal you should type:
```
robot-playerv -h localhost
```
And you should be able to control the robot like with stage, but unnfortunately this does not work. i am working on how to get it to work...


**Gazebo Problems**
```
gazebo /usr/share/gazebo/worlds/pioneer2dx.world
Gazebo multi-robot simulator, version 0.10.0

Part of the Player/Stage Project [http://playerstage.sourceforge.net].
Copyright (C) 2003 Nate Koenig, Andrew Howard, and contributors.
Released under the GNU General Public License.

[/build/buildd/gazebo-0.10.0/server/GazeboConfig.cc:124]
  Unable to find the file ~/.gazeborc. Using default paths. This may cause OGRE to fail.
terminate called after throwing an instance of 'Ogre::InvalidParametersException'
  what():  OGRE EXCEPTION(2:InvalidParametersException): Sky dome material 'Gazebo/CloudySky' not found. in SceneManager::setSkyDome at OgreSceneManager.cpp (line 1801)
Aborted

```
FIX:
The fix is is copied from here:
[http://www.mail-archive.com/playerstage-gazebo@lists.sourceforge.net/msg00851.html]("http://www.mail-archive.com/playerstage-gazebo@lists.sourceforge.net/msg00851.html")
You have to create a file named ".gazeborc" in home directory. I have created this file using root permissions and gazebo works. I am not sure you normal login have permission to create a file in this directory. To create this file using root permissions press "alt+f2" and type "gksudo nautilus" and enter password. You have now opened a file browser window using root permissions. Go to you home directory eg. if you name is "NAME" go to "home->NAME" and create the file - remember the "." before the rest of the file name. (This is how hidden files are named in linux...) 
but since ubuntu does not have the "local" folder change to:
```
<?xml version="1.0"?>
 <gazeborc>
   <gazeboPath>/usr/share/gazebo</gazeboPath>
   <gazeboPath>/home/YOUROWNNAME/share/gazebo</gazeboPath>
   <ogrePath>/usr/lib/OGRE</ogrePath>
   <gazeboPath>/home/YOUROWNNAME/lib/OGRE</gazeboPath>
   <RTTMode>PBuffer</RTTMode>
</gazeborc>
```
(Substitute YOUROWNNAME with you name on the machine)
and wow gazebo runs. You can test it using this code:
```

gazebo /usr/share/gazebo/worlds/pioneer2dx.world

```
huha!
EDIT (20/4-11) the pioneer2dx.world file is not installed by default. You will need to install the "gazebo-doc" stuff. (AKA: 3d multiple robot simulator with dynamics-documentation)

**Stage problems**
```

robot-player /usr/share/stage/worlds/simple.cfg
Registering driver
Player v.3.0.2

* Part of the Player/Stage/Gazebo Project [http://playerstage.sourceforge.net].
* Copyright (C) 2000 - 2009 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig, and contributors. Released under the GNU General Public License.
* Player comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
* are welcome to redistribute it under certain conditions; see COPYING
* for details.

invoking player_driver_init()...
 Stage driver plugin init

 ** Stage plugin v4.0.0 **
 * Part of the Player Project [http://playerstage.sourceforge.net]
 * Copyright 2000-2009 Richard Vaughan, Brian Gerkey and contributors.
 * Released under the GNU General Public License v2.

success
 Stage plugin:  6665.simulation.0 is a Stage world
 [Loading /usr/share/stage/worlds/simple.world][Include pioneer.inc][Include map.inc][Include sick.inc]f: /usr/share/stage/worlds/simple.world
Libtool error: file not found. Can't open your plugin controller. Quitting
err: Failed to open "wander". Check that it can be found by searching the directories in your STAGEPATH environment variable, or the current directory if STAGEPATH is not set.]
 (/build/buildd/stage-4.0.0/libstage/model_load.cc LoadControllerModule)
libtool error #2

``` 
This error is caused by a some call to a "demonstration" of a plugin controller in the file "simple.world" which the file simple.cfg points too/ opens. If the line "ctrl wander" ( line 48 ) is omitted in the file simple.world it works... sort of.

**Uninstalling everything**
The uninstallation process has to be done in the reversed order.

*Player*
removing player can be done from the "Ubuntu Software Center" (it is called "robot-player") or by pasting the code below into a terminal.
```

sudo apt-get remove robot-player libplayerinterface3 libplayerjpeg3 libplayerwkb3 libplayerc3 libplayerc++3 libplayerdrivers3 libplayertcp3 libplayercore3 libplayercommon3 libpmap0 liblodo0

```
Now player has been removed.

*Gazebo*
First delete the file .gazeborc you have created in you home directory. This is only possible with root permissions so: "alt+f2"-> enter "gksudo nautilus", browse to the file and delete it.
Gazebo can now be removed by using the "Ubuntu Software Center" or by entering the code below into a terminal:
```

sudo apt-get remove gazebo gazebo-doc gazebo-data libgazebo0

```
if you have used the code above it is recommended to check if any other gazebo files are installed using the "Ubuntu Software Center".
Now gazebo has been removed.

*Stage*
Stage can also be removed from the "Ubuntu Software Center" (it is called "robot-stage") or by pasting the code below into a terminal:
```

sudo apt-get remove stage stage-player-plugin libstage3

```
Now stage has been removed.

*ODE*

*Ogre*
OGRE can be removed from the "Ubuntu Software Center" or by pasting this code into a terminal:
```

sudo apt-get remove libogremain-1.6.4 ogre-tools libceguiogrerenderer-1.6.4

```

**Personal notes**
In gazebo joints (or hinges) can only be created in the model files and not the world files.
It seems like gazebo can import files from the free 3d CAD program "Blender" - which can be installed from the "Ubuntu software center". (Or rather blender can export in a format that gazebo can read). See this link: [http://playerstage.sourceforge.net/doc/Gazebo-manual-svn-html/tutorial_mesh.html]("http://playerstage.sourceforge.net/doc/Gazebo-manual-svn-html/tutorial_mesh.html")
Blender can import files from google sketchup see this link : [http://www.katsbits.com/tutorials/blender/import-google-sketchup-kmz-models.php]("http://www.katsbits.com/tutorials/blender/import-google-sketchup-kmz-models.php")
When installing google sketchup see this thread about how to do that: [http://ubuntuforums.org/showthread.php?t=1573182]("http://ubuntuforums.org/showthread.php?t=1573182")
There are apereantly two ways to talk to gazebo while it is running. one of these is directly through the "gazebo.h" file found in "usr/include/gazebo". In this file all public functions should be declared.
see this also:
[http://www-robotics.usc.edu/interaction/teaching/PSG.pdf]("http://www-robotics.usc.edu/interaction/teaching/PSG.pdf")

EDIT: I will keep reediting this post everytime i make a new "baby step" towards the final goal of having all three running on my system. I any moderaters see a problem with this please post here.

---

### Post by Sef on 2011-03-16
Moved to Tips and Tutorials.

---

### Post by daniloricfer on 2011-04-12
Dude, I'm having the same problem with gazebo. I followed your tips, created a file named ".gazeborc" in home directory, but I still having the same error message. Could you help me, please?

---

### Post by Morten ML on 2011-04-16
If you get exactly the same error then perhaps double check if you used the right paths... I have been away for a while so i haven't worked on this for some time. I think after that "fix" another error occurs and i haven't figured out how to fix that... sry - but thats the best help i can give u right now...

EDIT (21/4-11): I have updated the initial post with some missing information. Gazebo works for me now and i am working on getting the other programs to work. Please repost if you still have problems with gazebo. Btw: please do not quote the original post as it is so long and i see no reason for crowding the thread. 
Best Regards
M

---

### Post by daniloricfer on 2011-04-21
Thank you so much! Its working now... =D

---

### Post by Morten ML on 2011-04-23
You are very welcome. Just glad I could help :)

---

### Post by jeree on 2012-02-09
I am missing gazebo worlds.
```
kristjan@kupo:~$ ls /usr/share/gazebo
Media

```
Do you have any ideas why are they missing?

---

### Post by Morten ML on 2012-02-20
Hi jeree
I don't know sry. I haven't got time right now to check everything on the new version of ubuntu (11.10) - I upgraded my OS and haven't installed The Player Project yet. When i have time i will do a full installation and check everything and update this thread. But I don't think I have time before the weekend.
Hope you can wait that long. 
Btw could you be more specific of how you installed it? (what version of what you installed and what version of ubuntu you are using 32 or 64 bit etc. Where should the gazebo worlds be and maybe they have moved it to another folder)
Best Regards.
M

---

### Post by xclusive585 on 2013-02-12
I wish this group of software had better support in Ubuntu. Even a PPA. :-(

---

### Post by Morten ML on 2013-02-12
Gazebo has changed name to "Gazebosim" 
[http://gazebosim.org/]("http://gazebosim.org/")

and it does have a PPA.
[http://gazebosim.org/wiki/1.4/install]("http://gazebosim.org/wiki/1.4/install")

I have not looked at the other parts of the player project.

---

