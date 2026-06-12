---
title: "DAW software"
date: 2008-10-18
forum: Ubuntu Studio
---

### Post by alloftheabove on 2008-10-18
I've been looking around for some Ubuntu equivalent to Sony Acid Music Studio ( not pro ).  I've looked at the latest versions of jokosher, ardour, and rosegarden.  Jokosher didn't even work out of the box; ardour looks nice, but so far no midi, and it definitely isn't as easy to use as Acid (I know I shouldn't be complaining lol); and rosegarden is a pain for me to work with.  I don't really like the composer matrix, and the regular matrix editor is the big pain in my...Well, anyways, I was wondering if there was any other DAW programs out there, that might be somewhat comparable to Acid.

---

### Post by eric71 on 2008-10-18
I've never used Acid, so I can't compare features, but there is a thread here:

[http://forum.cockos.com/showthread.php?t=26690](http://forum.cockos.com/showthread.php?t=26690)

that gives an easy way of installing Reaper in linux with the low latency wineasio driver. Just make sure you have the realtime kernel (or Ubuntustudio installed) and Wine installed. Run Cybolic's LinReaper script, and you'll be up and running in minutes.

Reaper is certainly far beyond anything available in Linux as far as usability (unless you need to use notation). Even has an Ubuntu Human skin available.

[IMG]http://www.hotlinkfiles.com/files/1964316_pjpxf/Screenshot.png[/IMG]

Another recommendation as far as native linux programs is Qtractor. 

[http://qtractor.sourceforge.net](http://qtractor.sourceforge.net)

It is rapidly developing and fairly intuitive to use. The developer usually has the latest version available as a .deb through sourceforge, so definitely use that over what is in the ubuntu repository.

---

### Post by alloftheabove on 2008-10-18
I have to wonder how to get midi working in qtractor.  It won't recognize the General Midi bank...I'll check out the Reaper, and the thread you mentioned.  Thanks!

---

### Post by eric71 on 2008-10-18
I've generally used Qtractor, connected via its own connections window, to Qsynth using a general midi soundfont. I don't recall all of the details as I've been using Reaper exclusively for a few months. Qsynth will also use dssi instruments and even VSTi if you have dssi-vst installed. The developer is very open to suggestions, and any questions you have will be answered at his website:

[http://www.rncbc.org/drupal/](http://www.rncbc.org/drupal/)

Hope Reaper works out for you. They have a great forum that is very supportive, even of the Linux users. The beauty of Reaper is that the learning curve is not so steep as Ardour or Rosegarden, yet it is capable of everything a professional leval DAW should be, all in a few megabytes. And it provides the best VST support you'll get under Linux.

---

### Post by alloftheabove on 2008-10-18
I downloaded the LinReaper installer, but even though it seems to have installed correctly, I noticed from the terminal that ran that it needed root permissions for something.  Also, I checked the .local directory to see what might be wrong, and there are a bunch of broken symlinks.  I feel sadness.

BTW: I ran LinReaper .62

EDIT:  I checked out the main reaper site, and it's not free?  So why is it being provided for free?  I'm trying to find alternatives for commercial software...And I was gonna sell the music I make.

---

### Post by alloftheabove on 2008-10-18
Also, I should mention that I don't really know how to use Jack.  All I know is how to start Jack.  I have the full range of Ubuntustudio programs installed, if I could figure out how to use them right maybe I could do more with what I have??

---

### Post by Stochastic on 2008-10-18
Check out Muse, [http://muse-sequencer.org/](http://muse-sequencer.org/) the version in the repos should work but it is getting to be out of date, so if you don't mind compiling from source it's probably a good idea.

LMMS is also an option.

Most people who want to work with both MIDI and Audio will end up using two dedicated applications (ardour + a midi sequencer) that communicate well over Jack to one another (i.e. both sync to jack transport).

If you don't mind using commercial software, EnergyXT is also available as a native linux application.

---

### Post by eric71 on 2008-10-19
I should have mentioned that Reaper is neither open source or free. It is non-expiring shareware. It costs a lot less than most commercial DAWs, but if you plan to sell your music you should pay up. 

For the most professional open source results in Linux,  using both Ardour and Rosegarden is definitely the best solution. They work together nicely with Jack. There is a bit of a learning curve, and if you want to use VST or VSTi plugins, there are a few more hoops to jump through. There is an adjustment to your workflow, no doubt, but when you get the hang of it you can do everything you need to. When Ardour 3 comes along with midi support, things will get even more exciting for Linux music production.

---

### Post by markbuntu on 2008-10-22
> **alloftheabove said:**
> Also, I should mention that I don't really know how to use Jack.  All I know is how to start Jack.  I have the full range of Ubuntustudio programs installed, if I could figure out how to use them right maybe I could do more with what I have??

Here are some links to get you started with jack and some of the apps in ubuntustudio:


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)


[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

