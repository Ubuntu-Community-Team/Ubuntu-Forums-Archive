---
title: "X won't start after kernel upgrade in Gutsy"
date: 2007-12-19
forum: System76 Support
---

### Post by ajlewis2 on 2007-12-19
This morning there was an upgrade on vmlinuz-2.6.22-14-generic in Gutsy.  I had some thrashing and slowdown to a crawl a bit after the upgrade, but I had not rebooted yet.  I used SysRq to sync and reboot.

Upon reboot, X wouldn't start.  I went into /etc/X11 and backed up xorg.conf and put in xorg.conf_sys76backup.  I was then able to restart kdm and have it load.  I still see a message that relates, I think, to synaptic touchpad.  It appears in my terminal windows and was on the console when X wouldn't start.  The message is:

Can't access shared memory area. SHMConfig disabled?

I did a diff on the sys76backup and the xorg,conf that doesn't allow X to start.  This part is in the one that doesn't let X start. It is not in the working sys76backup:

> 	Identifier	"Synaptics Touchpad"
> 	Driver		"synaptics"
> 	Option		"SendCoreEvents"	"true"
> 	Option		"Device"	"/dev/psaux"
> 	Option		"Protocol"	"auto-dev"
> 	Option		"HorizScrollDelta"	"0"
> 	Option		"SHMConfig"	"1"

The function key for turning off the touchpad is not working.  Also, I have a script somewhere that automatically disables the touchpad when I login.  That is probably what is causing the error message about SHMConfig.

Suggestions on how to fix this?  Do you think the kernel upgrade could have done this or was it more likely the SysRq thing I did.

Thanks,
Anita

Edit: The SHMConfig message comes when I attempt to run synclient TouchpadOff="1" which is in .bashrc.  That is not a big deal.  Also, I notice that my ~/bin directory is gone; so I obviously lost something during the SysRq.  :-(

---

### Post by thomasaaron on 2007-12-19
Interesting. I've not seen that update come down the pike. So far (and it may still be a tad early to tell), I've not gotten any more reports of hosed computers. So, for now, I'm putting my cards on the SysRq shutdown. Weird, though. Generally it doesn't hose stuff. Maybe you just got lucky.

There have been some changes in xserver with Gutsy, and it is possible that the xorg.conf that you had in there is now misconfigured. You might run:
sudo dpkg-reconfigure xserver-xorg to create a brand new one. Or run the restore function on your system 76 driver to drop in ours.

Regarding the function key for turning off the touchpad, see if one of the above messages fix it. If not, I've got a tendency to blame KDE. We've definitely run into key-mapping problems with it from time to time. And it is such a nice scapegoat.

---

### Post by ajlewis2 on 2007-12-19
linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38_i386.deb file dated  2007-12-07 was just installed.  Interesting since the kernel is dated 12-18-07 and is linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb

Ok, I did the restore of the system76.  It did not add the SHMConfig option in xorg.conf, but now I'm thinking that I may have installed synclient in order to automatically turn my touchpad off, but still keep the option for touchpad in xorg.conf.  Most times I don't use it, but every once in a while I need it.  So now I have it in xorg.conf and X still started.  This is after another upgrade of a few things including those modules.  I am pretty sure there was a module upgrade yesterday too, but they seem to have set it back for now.  

Well, it is working and that is the chief thing.  It could be that no one else who has not got that option in xorg.conf will have any problems along the way.  Besides, like you say, it may have been the SysRq, but isn't it odd that we have this backward install of the older modules?

PS. I found my precious bin scripts and especially a great program that I had there in a backup.  Whew!  

Thanks again, Tom.

Anita

---

### Post by thomasaaron on 2007-12-20
It's also interesting that you're getting the *i386 updates. I just got some updates and they are the *generic ones. I know we install the generic. If you are running the i386 kernel, that may have something to do with it too.

---

### Post by ajlewis2 on 2007-12-22
I'm using generic, too:

```
~$ uname -r
2.6.22-14-generic
```

The package names are kind of odd, because they include the generic and the i386 in the name.  And the version numbers are different for each.  Looking in Adept, I see only generic is installed.  Maybe the package is able to update according to what is installed?  Weird.  Anyway, rest assured that I have generic installed and that is what is running.

Anita

---

