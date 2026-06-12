---
title: "Amarok and jack"
date: 2008-08-05
forum: Ubuntu Studio
---

### Post by Xecuter on 2008-08-05
I've tried getting amarok to play through jack using this guide, [http://ubuntuforums.org/showthread.php?t=267417&page=3](http://ubuntuforums.org/showthread.php?t=267417&page=3) , but with no luck. There is not jack option in Amarok settings.

Anyone know?

---

### Post by Stochastic on 2008-08-05
If memory serves correct, you need to download a newer version of xine (the audio engine amarok uses) - you may even need the SVN version.  The version in the repos doesn't have jack support, but newer versions do.  Once compiled, then reboot Amarok and Jack should be in the drop down menu of the audio outputs in amarok's preferences.

Also what version of Ubuntu are you running?  I think it "just works" in Hardy (but I may have done the xine upgrade when I did my hardy setup - I can't remember).

---

### Post by battles33 on 2008-10-26
Hey, this jack-less Amarok has been bothering me ever since I installed Hardy after having enjoying Amarok so much on Gutsy. Damn Pulseaudio, and damn xine/Amarok's lack of support for jack on Ubuntu! Anyway, here's what I've done. Hopefully this will work for you.

First off, I downloaded up xine-lib, as was mentioned on this thread [http://ubuntuforums.org/showthread.php?t=267417](http://ubuntuforums.org/showthread.php?t=267417)

wget [http://prdownloads.sourceforge.net/xine/xine-lib-1.1.8.tar.bz2](http://prdownloads.sourceforge.net/xine/xine-lib-1.1.8.tar.bz2)
tar -jxf xine-lib-1.1.8.tar.bz2
cd xine-lib-1.1.8
./configure
make
sudo make install

Once this was done, Jack support showed up for me in Amarok. If it still does not show up for you, then follow the instructions by motin on the second page of the above thread.

Then I encountered a problem with Amarok telling me "Amarok currently cannot play mp3 files" I had to install mp3 support. Then this installation would silently fail, as has been expressed in this bug [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/187406](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/187406). I tried their solutions to no avail. Note also this bug report is primarily dealing with alpha and beta versions and all that, apparently being fixed finally. I never even touched the pre release versions of Hardy, so somehow this problem has still remained in the final release.

And then I found the final answer that finally gave me a jack compatible and functioning Amarok.
copy /usr/lib/xine/plugins/1.1.8/ into  ~/.xine/plugins/
Now, all I had to modify for this was that for me the plugins folder is 1.20 rather than 1.1.8 as listed above. Also, if you go to  ~/.xine/ you'll find a file catalog.cache ---- for this file, just make sure all files listed within also refer to the proper plugin version folder, if not then with Text Editor go to Search>replace and there ya go.

I hope this will be of some help, as for myself the only things I have left to figure out is vlc to jack in Hardy, and general stuff that Pulseaudio apparently can route to jack but I have just not had any luck with (such as flash to jack, and video games that use what they use to jack) . For the latter, I guess I'll just have to wait until a future Ubuntu release will make jack and pulse work because pulse is much too big a mess right now for myself to make sense of.

---

### Post by markbuntu on 2008-10-26
If you want to set up Pulse Audio to play through jack you can do so. First of all, you need to install the pulse-audio-module-jack from the debian testing repository (this worked when this was in debian sid, the unstable repository so have no fear about that): 



[http://packages.debian.org/testing/sound/pulseaudio-module-jack](http://packages.debian.org/testing/sound/pulseaudio-module-jack)


Download the deb by clicking on the mirror site closest to you and install it with the gdebi package manager.
Then you need to make a little script. I keep mine in a /scripts directory in  /home/mark, my home directory . Just make a new file called jack_startup and make it executable and put these lines in it. (You can do all this with Nautilus if you want. file/new, name, double click to open, copy and paste, save, close.)

```

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

```


Then start up jack control and go to Setup/Options/Execute script after Startup. click on the... box and go to where the script is and click open. and then after you make sure the path is correct click the box on the left so it has an x in it. Click OK at the bottom and start jack. Make sure that an application is not using the sound card or jack will fail to start. 

You should now have jack sinks and sources in the Pulse Audio Volume Control and in the Volume Control on the panel. And a Pulse Audio JACK Sink and Pulse Audio JACK Source in the jack connection bay in the Audio section all connected up to system playback and system source automatically. When you close jack, the jack sinks and sources will automatically go away. Be sure to disconnect the pulse sink and source before closing jack or pulse will crash.

If the jack sink disappears from the Pulse Audio Volume Control after a few seconds, adjust the timeout in the jack control setup menu to 1000-5000. Applications that just play back audio streams through Pulse Audio are very lazy about talking to their sound server and this will prevent jack from timing out the connection.

---

