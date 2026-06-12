---
title: "HOWTO: Set up a Jamming and Music production environment on-demand in seconds"
date: 2008-09-18
forum: Ubuntu Studio
---

### Post by motin on 2008-09-18
THIS POST IS OBSOLETE. PLEASE VISIT [ THE NEW THREAD]("http://ubuntuforums.org/showthread.php?p=8115773#post8115773") ABOUT THE FOLLOW-UP PROJECT ON THESE SCRIPTS: [http://ubuntuforums.org/showthread.php?p=8115773#post8115773](http://ubuntuforums.org/showthread.php?p=8115773#post8115773)

> I got some time to work on this, updated for Karmic and including a simple GUI: [Studio Launcher: Jamming and Music production environment on-demand in seconds]("http://ubuntuforums.org/showthread.php?p=8115773#post8115773")

Cheers!

Big thanks!

Old version of this post:

*Short version:*
1. Download the latest of the attached archives (highest revision-numer...)
2. Unpack it:
```
tar -xvf studio-r*.tar.gz
```
3. Run: 
```
./setup.sh
```
4. Follow the manual instructions in doc/readme-prerequisites.txt 
5. Run:
```
./studio.sh
```

For concurrent runs, only ./studio.sh needs to be run... 

Happy jamming!

*Long version:*
Ever since I started using Linux, I have wanted to use free applications for Jamming and producing music. This is "very possible" and over the years I have found how to combine many free tools to transform my laptop into a jamming box that has joined me at several performances. 

**But**... setting up all applications every time takes quite some time, (not accounting the research needed to get them running in the first place...). We are using Linux, right? So why not automate the process?

Cutting to the chase, I have finally written a helping script that configures my home jamming and music production environment most automagically. Actually, I haven't come to far in music production in this script (todo...), but at the current stage, at least it makes my MIDI keyboard useful, and should help quite some others to that as well I hope...

First, you need to set-up the required packages and resources:
```
Prerequisites:
 1. Run setup.sh in the base directory. This will inform you which the required packages are and install them for you
 2. Manual installation:
    dssi-vsti.so (this step is done by setup.sh):
		1. Download version 0.7 (greater may work if available, but I haven't tested) from http://sourceforge.net/project/showfiles.php?group_id=104230&package_id=127571
		2. tar -xvf dssi-vst-0.?.tar.gz
		3. cd dssi-vst-0.?/
	 	4. sudo apt-get install build-essential wine-dev liblo0-dev
		5. make
	 	6. sudo make install
    Qsynth and Unison.sf
		1. Find "Unison.sf" by searching the net and put it in a fitting directory
	 	2. Configure qsynth to load this soundfont (Start Qsynth -> Setup -> Soundfonts -> Open) 
		    as well as to use jack as audio driver. Don't forget to check "Auto connect JACK outputs".
    Grand Piano:
	A. LinuxSampler (this step is done by setup.sh)
		1. Download the latest liblinuxsampler and linuxsampler .deb files from http://download.linuxsampler.org/packages/debian/
		2. Save the edit-deb-control.sh script from http://ubuntuforums.org/showthread.php?p=5585977#post5585977 and make it executable
		3. Run "./edit-deb-control.sh ~/path/to/liblinuxsampler_*_i386.deb"
		4. Change "libgig" to "libgig6", save and exit gedit
		5. Install the modified liblinuxsampler package
		6. Install the linuxsampler package
	B. The samples (GIG):
		1. Find "maestro_concert_grand_v2.gig" by searching the net (may not be the 
		easiest, sorry - even though I am sure it was free to download and use at least 
		for personal usage I cannot recall if I am allowed to distribute 
		the file...) and put it in a fitting directory
	 	2. Edit res/grand-piano.lscp in a text editor and replace all instances 
		of "/store/res/gig/maestro_concert_grand_v2.gig" with the path to where 
		you put the gig-file.

Note:
After installing the above, you may need to configure JACK in an 
appropriate way depending on your hardware. Normally the default 
settings will work for testing, but adjusting the settings can 
decrease the audio latency and help provide smoother sound output.
A good start is to follow the guides at 
https://help.ubuntu.com/community/UbuntuStudioPreparation 
and https://help.ubuntu.com/community/HowToJACKConfiguration

In order to use non PulseAudio compatible OSS applications while JACK 
is running, launch them with the jacklaunch wrapper: "jacklaunch <app>"
```

Now take a minute to download the latest version of this script, try them out, and be sure to tell me if you are able to use them at all :)

Suggestions and preferable patches for enhancements are very welcome of course! In the best of scenarios, we could help each other build a script that would help setting up the most customized jamming and music production environments!

**CURRENT STATUS:**
Once required packages and resources are properly set-up, you will be able to run the main script and then within a minute or two jam away on your MIDI keyboard using various software synths, VST instruments and a sampled Grand Piano. Desktop applications will still be audible thanks to PulseAudio's JACK output sink. 
Instructions on how to get the required packages and resources are found within the script file. Tested to work on 8.04. Some tweaking of settings may be needed to play along with different system's sound set-up. 

Read more in the main script file: studio.sh

Note: Usage of this script requires decent knowledge of using free music production applications in Ubuntu. Please refrain from asking about help how to set-up JACK, get your particular sound card working etc in this thread. This way this thread can become more relevant to those seeking support on how to use this particular script. Thank you for you understanding!

Enjoy jamming in Ubuntu!

**TODO** (Encourage me to finish this stuff :) - or by all means feel free to help finishing these things):
 - Implement checks for required packages and resources
 - Automate installation of the packages and resources that currently needs manual installation and configuration
 - Move all customized settings to a configuration file
 - Automate setting up music production applications Rosegarden and Ardour
 - Supply different example configuration files for different environment set-ups
 - Anything more?

Hey, if anyone wants subversion access to the script just PM me. Eventually I'll set-up public access if enough are interested...

---

### Post by Stochastic on 2008-09-18
Hmm, looks very much like it has been built for your particular setup (which stands to reason, you did build it for you after all).  I'm not so sure including dss-vsti is a solid idea as it's not a point-click setup procedure for most computers.

I've yet to run the script but I did notice you've got an explicit MIDI keyboard call in the studio.sh file - which also might cause some troubles on other people's computers.

Overall I love the idea and deeply hope this thing evolves into a massive user-friendly interface for audio users.  I may just help out if I learn how to bash (it doesn't look that complex).  You've got a thanks from me! :grin:

---

### Post by motin on 2008-09-19
Hey Stochastic!

Yeah currently it is very adapted to my setup and most users will probably need to do some changes in the configuration and/or the script to make it useful for them. But hey, it's alpha software and there is a reason for the "- Move all customized settings to a configuration file" todo item :)

If you get this running, and can point out what changes you needed to do then please report back and I'll make sure that these things are the first to be moved into the configuration file. 

Thanks for the thank you :) Cheers!

---

### Post by motin on 2009-10-16
I got some time to work on this, updated for Karmic and including a simple GUI: [Studio Launcher: Jamming and Music production environment on-demand in seconds]("http://ubuntuforums.org/showthread.php?p=8115773#post8115773")

Cheers!

---

### Post by bolex100 on 2009-10-17
I must say that i like the idea of this, but I'm more interested in the USE of the packages than the installation.  (although fitting together is important!)
Perhaps you could enlighten use about what you actually do with them.

---

### Post by AutoStatic on 2009-10-20
Looks good, but I've checked some of the scripts and apparently this does not set up a real-time low-latency environment which seems a bit pointless to me. But correct me if I'm wrong :) And personally I disable PulseAudio completely when working with audio on my system.

---

### Post by motin on 2009-10-20
Hey guys, I have replied you in the newer thread: [http://ubuntuforums.org/showthread.php?p=8115773#post8115773](http://ubuntuforums.org/showthread.php?p=8115773#post8115773)

Please use that one as that is where I will edit info about the scripts etc :)

Cheers!

---

