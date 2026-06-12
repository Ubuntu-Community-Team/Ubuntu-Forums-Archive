---
title: "Gui for configuring Xorg.conf"
date: 2006-10-31
forum: The Cafe
---

### Post by kingbilly on 2006-10-31
**Edit: I just wanted to make it clear that I am aware a similar program may exist.  This is just for me and a few interested from my school.  Just to save face I am not trying to tread on anyone's work.  This is a hobbie and I've come to the forums to ask for ideas on what people do when they edit the xorg.conf file.***

I've started working on a program for myself and my friends who installed ubuntu to configure xorg.conf with a gui.  But i'm not really sure what needs to be done for each aspect of the config file.  
So far I have had to open the file to:
1) Add more screen resolution options
2) Add modules for compiz
3) Add something to server layout for compiz
4) Disable a laptop touchpad

So can anyone give me some ideas?  
What have you had to configure in the xorg.conf file?

---

### Post by DoctorMO on 2006-10-31
Lets see,

Servers = Input Devices + Screens(multiple with arangement config) + Modules
Screen  = GraphicCard + Monitor
Monitor = Resolutions / Bit rates

---

### Post by PatrickMay16 on 2006-10-31
And also, don't forget that there can be more than one graphics card or monitor.

---

### Post by shining on 2006-10-31
Wasn't a similar project already started?

---

### Post by DoctorMO on 2006-10-31
I should hope so! but the question is. where is it?

---

### Post by shining on 2006-10-31
[http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

Maybe there are other informations there:
[http://ubuntuforums.org/showthread.php?t=80552](http://ubuntuforums.org/showthread.php?t=80552)

I believe I saw another thread too, but I'm not sure. Just use the search feature :)

---

### Post by DoctorMO on 2006-10-31
kingbilly give xord-edit a hand, move it towards none widget because wx is just not cricket.

installing it now ... hmmm, interesting. could do with more structure; I find most people program in a very flat way.

---

### Post by darkhatter on 2006-10-31
I think having it configured on the fly and built into xorg would be more useful, but have the ability to overrate the auto-configuration using the xorg.conf file. I think that would be far more useful then a gui tool to configure xorg.conf

---

### Post by DoctorMO on 2006-10-31
Nah we need all these tools, the auto config is important, so is the config file remaining a file, the man pages, the command line configurator and the simple gui for those who like such things.

Linux is for doing things the way you want it done, assuming you can program. if these fine chaps want to see a gui, so be it. lets just hope it's a nice one.

---

### Post by plb on 2006-10-31
you can just reconfigure xorg by going "sudo dpkg-reconfigure xserver-xorg"

---

### Post by kingbilly on 2006-10-31
@ pib : I wasn't going for a reconfiguration, more like when your following the compiz guide (though if you can do that you are smart enough to not need a gui) you have to add a module or two.  I'm just looking for a way to take that config file into a gui for when you need to adjust one or two things.  

@ DoctorMO : I haven't been able to download that and try it out myself so i don't know if it is going to be the same. i actually didn't know there was a similar project going since I just caught people saying there needs to be one.  Mine is based on python and the qt library though I've started one for gnome as well.  Ill explain the layout more when I have time to write about it.  -Also thanks for the above suggestions

@: Patrick yes I have thought of that too thank you.

It will be a couple days before I have anything worth showing but I will post again and if I have questions I will pm someone, if they don't mind.

_rich_

---

### Post by DoctorMO on 2006-11-01
> Files {
	+FontPath [ ... ]
	+RGBPath [ ... ]
	+ModulePath [ ... ]
}

ServerFlags {
	+Option [ ... ]
}

Module {
	+Load [ ... ]
	+SubSection [ Options... ]
}

Server { ID
	+Screen { ID, DefaultDepth
		+Device (Graphics Card) { ID, driver, BusID, Screen, Chipset, Ramdac, Clocks ... etc }
		+Monitor { ID, Options }
		+Display { BitRate => [ ListOfModes ] }
	}
	+InputDevices { ID => { Driver, Options }, ... }
	OptionsForMultiScreensfire
}

Modes {
	+Mode [ ... ]
}

Structure.

---

### Post by RedRightReturning on 2006-11-01
Kingbilly-
How about the ability to have multiple screen resolution profiles for when you dock a laptop?

---

### Post by Pixel on 2006-11-01
Importing/Exporting config files would be good too, for example, someone has a specialty mouse that requires extra configuration, they can just export that config once it's all setup and working.  Another person buys the same mouse, since someone allready exported the settings, they can simply import it without having to edit the files theirself.

---

### Post by DoctorMO on 2006-11-01
Pixel, I'll be working on that kind of thing with Dohickey. I'd hope HAL options will be used for those kinds of things and xorg would move towards using HAL much more (because it makes sense for configuration and because your not duplicating a ton of stuff)

---

