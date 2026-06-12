---
title: "NuBe Audacity problem with sound."
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by whodatpat on 2008-10-21
Playback error;
Error while opening sound device. Please check the output device settings and the project sample rate.

I am running Ubuntu Studio on a Dell laptop.  I am simply trying to noodle my way through this software to learn how it works so I can eventually record some music.  I am just testing with a USB mike and using earbuds in the laptop soundcard.

Just for reading to this point, your help is already appreciated.

Patrick

---

### Post by markbuntu on 2008-10-21
If you have UbuntuStudio you should really be using ardour for recording. Ardour is better integrated into jack and a much more professional recording application. You would be far better off learning to use ardour than learning audacity. Here are a few links to get you started off on the right foot:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by skullmunky on 2008-10-21
First, make sure you can play sound.  

go to Edit->Preferences
go to the Audio I/O section (it's the first in the list)
Under Playback and Recording are menus to choose the device / sound system driver to use.
Try different ones.

---

### Post by Zimmer on 2008-10-22
stop the process jackd   using the System Monitor.

JACK starts when you switch on, Audacity doesn't like it!
see
[http://ubuntuforums.org/showthread.php?t=710881](http://ubuntuforums.org/showthread.php?t=710881)

@markbuntu
Thanks for the links, I was up until 2:30am trying to figure out Ardour and JACK and only getting a distorted recording of my voice !
Then my Audacity would not play, because of the above error!!
:)
Looks like I will be spending a fair bit of time trying to figure Ardour now,
but Audacity is a lot easier for recording for us Amateurs..
Link for whodatpat  
[http://audacityteam.org/wiki/index.php?title=Main_Page](http://audacityteam.org/wiki/index.php?title=Main_Page)

EDIT: Have tried using JACK as Output for Audacity, works but horrible crackle and distortion as per Ardour , so at the moment I blame JACK (or maybe my lack of knowledge of how to configure JACK).. (have tried changing sample rates in JACK and Audacity but I fear a lot of research and fiddling will be required to get JACK working nice..  I will let you know if I get it to work!)

---

