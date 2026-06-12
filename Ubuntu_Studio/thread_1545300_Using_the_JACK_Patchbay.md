---
title: "Using the JACK Patchbay"
date: 2010-08-03
forum: Ubuntu Studio
---

### Post by MikeRivers on 2010-08-03
Or maybe my question is about "connections." After a struggle and not knowing what finally caused it to start working, I finally got JACK to recognize my interface, a Mackie Onyx mixer, and got it working. I'm trying to figure out how to use qjackctl to route the mixer input (which may be called an output since it's the Firewire output to the computer) to where I want it to go.

I'm confused as to what's an input and what's an output in JACKspeak. I think that what I'm talking about here is called "capture." It seems to default to Mixer Input 1 going to Track 1, Input 2 to Track 2, and so on. This is fine if I'm recording one mic to one track in a multitrack program like Ardour. But what I'd like to do is connect the stereo output of the mixer, which is 17 and 18, to the inputs of a stereo track, for example in Audacity.

Note: These are from the qjackctl FAQ, not my own screen shots

Do I use the Connections panel? 

[img]http://qjackctl.sourceforge.net/image/qjackctlConnectionsForm1.png[/img]

Or the Patchbay panel? 

[img]http://qjackctl.sourceforge.net/image/qjackctlPatchbayForm1.png[/img]

Or both?  Or something else? I know what a patchbay is, but I can't seem to find any terminology that I recognize. I can connect things in the Connections pane, but I can't tell that I'm making any difference. I tried the same procedure in the Patchbay pane and can't highlight anything so I can't connect what I think is gozouta 17 to gozinta 1 and same for 18/2. 

I tried to register for the JACK forum and ask there, but it doesn't seem to recognize me, and besides, that looks like it's mostly about programming for JACK. Feel free to point me to a better place to ask.

---

### Post by sgx on 2010-08-03
Hi, when you start an instrument like zynaddsubfx or hydrogen, it appears
in the alsa and audio panels, each panel having two sides, so make the connections you desire.

For example, you may want to play zyn from a midi keyboard, so that first connection needs to be made. Then, to hear zyn, a second connection in the
other panel, the one to your sound system, would need to be made. If later, you wanted fx, you could start rakarrack, disconnect zyn from your sound system, connect it to rakarrack, then connect rakarrack to your sound system. 

The midi panel of qjackctl gets little use. The alsa tab will display your midi keyboard, line-in, hardware and i/o ports, the audio panel will display your sound system ports.

Some instruments autoconnect when started, like hydrogen. If you disconnect an instrument, you may need to snoop around in its menus to
restart its awareness of the jackd connections, before reconnecting.

Cheers

---

### Post by AutoStatic on 2010-08-04
> **MikeRivers said:**
> I'm confused as to what's an input and what's an output in JACKspeak. I think that what I'm talking about here is called "capture." It seems to default to Mixer Input 1 going to Track 1, Input 2 to Track 2, and so on. This is fine if I'm recording one mic to one track in a multitrack program like Ardour. But what I'd like to do is connect the stereo output of the mixer, which is 17 and 18, to the inputs of a stereo track, for example in Audacity.system: capture ports are the inputs and system: playback ports are the outputs of your Firewire device. In QjackCtl they are named the other way around which is a bit confusing but still logical nonetheless: output ports output sound and input ports receive it. Actually, consider the connections window of QjackCtl as the internals of a soundcard/mixer. So you can't really connect anything in QjackCtl to your stereo output ports of your mixer because for QjackCtl those are input ports, so only writeable, not readable (still following?). If you want to record a stereo track in Audacity you have to connect readable output ports in QjackCtl of which you want to capture sound to the Audacity input ports.

> **MikeRivers said:**
> Do I use the Connections panel? Or the Patchbay panel? Stick with the Connections window. I've been working with QjackCtl quite a while now but the Patchbay functionality is in great parts still a mystery to me too.

---

### Post by MikeRivers on 2010-08-04
> **sgx said:**
> Hi, when you start an instrument like zynaddsubfx or hydrogen, it appears
in the alsa and audio panels, each panel having two sides, so make the connections you desire.

For example, you may want to play zyn from a midi keyboard, so that first connection needs to be made. Then, to hear zyn, a second connection in the
other panel, the one to your sound system, would need to be made. If later, you wanted fx, you could start rakarrack, disconnect zyn from your sound system, connect it to rakarrack, then connect rakarrack to your sound system. 
That's not what I'm after. I'm not working with virtual instruments, I'm working with recording (DAW) software. I want to connect the left output of a mixer to the left input channel of Audacity and the right mixer output to the right channel. No MIDI or virtual instruments involved. 

When I use the Connections panel, I can get to what I want, sometimes, but what I'm having trouble getting my head around is what I see, and when. It's kind of a now-you-see-it-now-you-don't situation. Sometimes I see In 1 and In 2 to which I can connect Capture 17 and Capture 18 and make Audacity work. But sometimes, I don't see In 1 and In 2, but see In 3 and In 4 instead.

Perhaps I'm confusing things by switching between Audacity (a 2-track program) and Ardour (a multitrack program).

---

### Post by AutoStatic on 2010-08-04
> **MikeRivers said:**
> But sometimes, I don't see In 1 and In 2, but see In 3 and In 4 instead.That's right, Audacity assigns random numbers to its input ports, no idea why, probably a PortAudio thing (the extra layer Audacity uses to talk to JACK). But afaik the numbering shouldn't matter and Audacity should record what's coming in nonetheless.

---

### Post by MikeRivers on 2010-08-04
> **AutoStatic said:**
>  In QjackCtl [they are named the other way around which is a bit confusing but still logical nonetheless]:

output ports output sound and input ports receive it. Actually, consider the connections window of QjackCtl as the internals of a soundcard/mixer. So you can't really connect anything in QjackCtl to your stereo output ports of your mixer because for QjackCtl those are input ports, so only writeable, not readable (still following?).
Not really following what you're saying here, but I've found something that works, when I can get it to stick. But I often have to fool around, stopping and starting things, before I get the connections I want. 

You can save a patchbay setup (which apparently isn't for audio routing, but I'm not sure that's correct) but you can't save a Connections setup. I think the reason for that is that Connections is dependent on the program (or programs) you're running and it changes dynamically. 

For example, when I have Audacity (a stereo recording program) running, I can set Capture 17 and Capture 18 (the Mackie mixer's stereo outputs) to Inputs 1 and 2. I can enable monitoring in Audacity (this makes the record level meters active) and see what I expect. 

But if I start and stop recording, then start recording again, instead of seeing In 1 and In 2, I see In 3 and In 4 connected to Capture 1 and Capture 2,and I need to re-connect to get what I want. Further, I only SEE the inputs when it's in the Record or Record Monitor modes, so I can't pre-set a routing and expect it to stay there. 

I think that qjackctl (and I assume jackd) looks at each recording in Audacity to be a new setup. 

When I'm working with Audacity, each time I add a new track to the project, a new In appears on the right hand pane of the Connections window and it's by default connected to the corresponding mixer input. 

Normally that's what I want, but if I want to record several tracks (one at a pass) from the same input, for example, if I'm overdubbing several harmony parts, all singing into the same microphone, connected to the same mixer channel, I want to be able to assign that mixer channel to several inputs. and I can do that by going to the Connections window.

In the DAW programs that I'm accustomed to using, I can make those assignments to the track inputs from the DAW program itself. I realize this is part of "the Unix principle" of using a single program, in this case JACK, to route signals to wherever they need to go. But the inconvenience is that you have to go back to JACK to control that routing. There's no "remote" that's extended to the application that you're actually using.

---

### Post by MikeRivers on 2010-08-04
> **AutoStatic said:**
> That's right, Audacity assigns random numbers to its input ports, no idea why, probably a PortAudio thing (the extra layer Audacity uses to talk to JACK). But afaik the numbering shouldn't matter and Audacity should record what's coming in nonetheless.
It does, though they're not random. Each time you start recording, you get the next consecutive pair of numbers that represent the inputs to the track. but it goes back to In 1 and In 2 (as the source) connected to the Audacity inputs 3 and 4 (and 5/6, 7/8 and so on) and I have to re-connect In 17 and In 18 to those inputs before I can record the mixer output. 

Perhaps by using Audacity I'm making things hard to understand, because each time you re-start recording in Audaicity, it does it on a new track, so I suppose this gets numbered as a new set of inputs. That doesn't happen in real hardware where nothing changes until you move the cable. When using Audacity with a simple 2-output interface, there's no place to move so the mixer output stream source doesn't change. 

It would work as I expect if the mixer (the Firewire interface) had only two Firewire stream outputs, but it has eighteen, and there doesn't seem to be a way to say "I always want to use THESE two streams," at least until I close Audacity.

---

### Post by AutoStatic on 2010-08-04
Hello MikeRivers, Audacity is a nice wave editor but for multitracking there are way better solutions like Ardour and Qtractor. You already stumble upon some of the drawbacks of Audacity (and PortAudio in particular) when it comes to recording more than one track. That's got nothing to do with the Unix principle (Audacity is cross-platform, hence the PortAudio solution) but more with the limited JACK support and multitrack functionality of Audacity.

---

### Post by AutoStatic on 2010-08-04
> **MikeRivers said:**
> It does, but it goes back to In 1 and In 2 connected to the Audacity inputs 3 and 4 and I have to re-connect In 17 and In 18 to those inputs before I can record the mixer output. 

It would work if the mixer (the Firewire interface) had only two Firewire stream outputs, but it has eighteen, and there doesn't seem to be a way to say "I always want to use THESE two streams," at least until I close Audacity.This is a drawback of Audacity. If you'd use Qtractor for example you can create a Qtractor template that will always connect the Master output ports to the 17 and 18 system input ports. This can also be done with a Patchbay file and then tell QjackCtl to load this Patchbay file when starting.

---

### Post by MikeRivers on 2010-08-04
> **AutoStatic said:**
> Audacity is a nice wave editor but for multitracking there are way better solutions like Ardour and Qtractor. You already stumble upon some of the drawbacks of Audacity (and PortAudio in particular) when it comes to recording more than one track. 
I've noticed "PortAudio" there. What's that? Yet another intermediate program that's used for routing?

I'm only using Audacity because it's there and it works. But when I use Audacity under Windows (with the same mixer as the audio interface), in the Preferences, I can choose whatever pair of streams I want (17 and 18 in this case) and it sticks. When running it under Linux, my only input choice is "default."

When using Reaper (or Nuendo, or Sonar or practically any other multitrack DAW program) under Windows, you can click on a button on the track you're recording and select its input source, but Ardour doesn't have such a button, or if it does, I still haven't found it. If it does, please tell me where it is. 

I should probably add Wine to this system, install Reaper, and see if that gives me the same degree of control in Ubuntu as in Windows. I've had many arguments over the years with Paul Davis (principle developer of both JACK and Ardour) about how Linux audio programs didn't seem to be designed by anyone who has ever worked in a studio and he keeps telling me how much more important it is to be totally flexible. ;)

---

### Post by MikeRivers on 2010-08-04
> **AutoStatic said:**
> This is a drawback of Audacity. If you'd use Qtractor for example you can create a Qtractor template that will always connect the Master output ports to the 17 and 18 system input ports. This can also be done with a Patchbay file and then tell QjackCtl to load this Patchbay file when starting.
I was trying to do essentially that. Create a Patchbay with consecutive mixer channels connected to consecutive tracks and save it as "Audour Multitrack Recording," then make another one with mixer outputs 17-18 connected to inputs 1-2 and save that as "Audacity Stereo Recording." I could live with that. But the Patchbay doesn't seem to relate to the audio routing. I expect it to. Maybe it's using a different language and I haven't interpreted it properly.

---

### Post by MikeRivers on 2010-08-04
> **MikeRivers (That's me!) said:**
> 
I should probably add Wine to this system, install Reaper, and see if that gives me the same degree of control in Ubuntu as in Windows. 
Nope!  I am able to get Reaper running with the internal sound card or the Behringer external 2 channel I/O interface, but not with the Mackie mixer. None of the Preferences/Device choices get me there. Perhaps the Wine layer sufficiently isolates it from JACK, because JACK Connections doesn't show anything on the "program" side, sort of like what I see when, in Ardour, I don't have any tracks in the project.

Pfffft!  :tongue:

---

### Post by transmogrifox on 2010-08-04
Audacity is a program that is an anomaly as far as jack programs go.

The only way I can sanely deal with Audacity & Jack is to go to Audacity Edit->Preferences->Audio I/O

Select the desired jack interfaces for playback and recording.  Then Audacity will automagically connect to those ports when you hit record or play.  Don't use qjackctl for Audacity because Audacity's jack connections are only present during playback and recording, and as you have seen, they have a different designation each time.  Audacity wasn't designed for jack.  Jack support appears to have been added to Audacity in a manner that didn't require the developers to significantly rework the way Audacity handles Audio I/O.  I really like Audacity for simple things & scratch tracks but good multitrack recording is not what it's designed to do.  It's worth your time to get familiar with Qtractor or Ardour.  Those programs interact with jack in a more consistent manner.

The qjackctl Patchbay is a good way to set up a recording environment and save it...then the connections are persistent.  It's clumsy to make patches initially but it's worth it if you have a certain project with a set number of connections and routing.  The you connect everything once and then activate that patch when you have opened the given environment.

If you want to be a wizard you can always write scripts to make jack connections for you.  This would be the non-gui implementation of the Patch Bay.

Hope for the future:  Jack has added session management in the most recent development, which will be a less clumsy way to recall a working environment.

Think of it as a physical studio.  You select your gear (plugins, mixers, DAW, etc) then you connect all the cables.  You only have to do this once for most things, and thereafter you walk into the studio, flip on the power switch and start rolling.  Generally there are not many changes in the overall connection layout until you change bands or something.

The work flow truly is productive given two caveats:
1) You have to be open to learning something that is different from what you have previously have come to expect in a software production environment.
2) Initial configuration & setup is time consuming and frustrating when you're trying to climb the learning curve.


After those two hurdles, things move along gracefully and I consider these to be one-time hurdles.

---

### Post by transmogrifox on 2010-08-04
> **MikeRivers said:**
> I was trying to do essentially that. Create a Patchbay with consecutive mixer channels connected to consecutive tracks and save it as "Audour Multitrack Recording," then make another one with mixer outputs 17-18 connected to inputs 1-2 and save that as "Audacity Stereo Recording." I could live with that. But the Patchbay doesn't seem to relate to the audio routing. I expect it to. Maybe it's using a different language and I haven't interpreted it properly.

Here is a good tutorial on the Patch bay:
[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

...and you're right, it is a little different.  More flexible once you understand it, but not immediately intuitive.

---

### Post by MikeRivers on 2010-08-04
> **transmogrifox said:**
> 
The only way I can sanely deal with Audacity & Jack is to go to Audacity Edit->Preferences->Audio I/O
This is what I've been doing, but I never see anything that looks like the Firewire interface until I start JACK. 
> 
Select the desired jack interfaces for playback and recording.  Then Audacity will automagically connect to those ports when you hit record or play.  Don't use qjackctl for Audacity because Audacity's jack connections are only present during playback and recording, and as you have seen, they have a different designation each time.  

If I start Audacity without first starting jACK, I only have ALSA as an option in the Audacity Preferences Host box. With jACK started, I can choose jACK Audio Connection Kit there. That's what I need to do in order to make the program use the Mackie Firewire mixer as an input source.  

The only way I know how to do start jACK is with qjackctl. I've tried to start it with the command line, but I can't figure out what to type. Ever see the documentation on jackaudio.org or the reference wiki page?  It's not very informative, at least not to me. Just plain jackd without any options doesn't seem to get me to the same place, and neither the docs that I've found nor the man pages are meaningful to me. 

But when I have it going, I can get it set up the way I want it by opening the Connections, disconnecting the 1-1, 2-2 connections (essentially direct outputs of mixer channels 1 and 2 to the left and right inputs of Audacity) and connecting 17-1 and 18-2. But I have to do it every time I want to use this setup. 
> 
Audacity wasn't designed for jack.  Jack support appears to have been added to Audacity in a manner that didn't require the developers to significantly rework the way Audacity handles Audio I/O.  I really like Audacity for simple things & scratch tracks but good multitrack recording is not what it's designed to do.  It's worth your time to get familiar with Qtractor or Ardour.  Those programs interact with jack in a more consistent manner.
This is true. I haven't looked at Qtractor, but I find Ardour pretty awkward to use, compared to the Windows programs I'm used to. I'm only using Audacity for test purposes now, but since most of my recording work these days is straight to stereo, I can use Audacity effectively for editing and cleanup. I had minimal luck with Sound Forge running on top of Wine, but it's not happy with a lot of things. I uninstalled it. 
> 
The qjackctl Patchbay is a good way to set up a recording environment and save it...then the connections are persistent.  It's clumsy to make patches initially but it's worth it if you have a certain project with a set number of connections and routing.  The you connect everything once and then activate that patch when you have opened the given environment.

That's what I was hoping to do, but Connections does what I want (and I have been able to interpret it, at least for inputs), but Patchbay appears to do something different and seems more suited for assigning virtual instruments to DAW tracks. 
> 
Think of it as a physical studio.  You select your gear (plugins, mixers, DAW, etc) then you connect all the cables.  You only have to do this once for most things, and thereafter you walk into the studio, flip on the power switch and start rolling.  

This is what I'd like to do, but I can't find the virtual properly labeled jacks. 

I'll check out the tutorial for the jACK patchbay that someone else pointed to and see if that helps me to make sense of it. 

Thanks for the help and encouragement. As I may have said before here, my goal isn't necessarily to get productive. I'm already productive on another system. What I'm trying to learn is what kinds of things someone would need to learn in order to work with audio in Linux and (let them) be productive.

---

### Post by transmogrifox on 2010-08-04
> **MikeRivers said:**
> This is what I've been doing, but I never see anything that looks like the Firewire interface until I start JACK. 
  
Ah yes, this is true.  When doing Linux audio it is anticipated that jack is running all the time.  Some jack programs will automatically attempt to start jack if it is not already running when you launch the program.  If the ~.jackdrc file contains a proper configuration for your audio hardware it will be successful.  Unfortunately Audacity does not attempt to start jack if it is not already running (as far as I know).  Instead it only connects to jack if running.

qjackctl is an easy way to play with settings to get jack to start properly simply because it puts all the normal command line arguments into the form of check boxes, buttons and drop-down menus.  Once you have configured your setup with qjackctl, it saves the configuration to ~.jackdrc.

My .jackdrc file contains the following:
/usr/bin/jackd -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2

This is the command to start jack from the terminal with my particular settings and sound card configuration.  If you can successfully start jack with qjackctl, then you can easily start jack with the following command in your user home directory:
sudo chmod +x .jackdrc
./.jackdrc

or you could copy paste the line from that file into the terminal for the same result.

When a program attempts to automatically launch jackd if not already running, it uses this file for the configuration.  If jackd does not start successfully in this case you need to change settings in this file to get things right.  The qjackctl settings menu gives a more user-friendly interface for selecting these settings.

Type
man jackd
in the terminal to learn about what these options mean.

> **MikeRivers said:**
> 
If I start Audacity without first starting jACK, I only have ALSA as an option in the Audacity Preferences Host box. With jACK started, I can choose jACK Audio Connection Kit there. That's what I need to do in order to make the program use the Mackie Firewire mixer as an input source.  

Yes, that's the drawback to the way Audacity handles jack.  Any connections you want to make in Audacity have to be active before you start the program.

I can tell you might not like this, but this is the only way to do it:
Start jackd
Start Audacity.

Or if you want Audacity to route playback into a certain program, or get input from a program (like FX first before Audacity) then you need to have all the other programs running before you can start Audacity.  Maybe more recent versions of Audacity will update the connections in real time, but my current version  1.3.5-beta needs to be restarted to populate the list with current available ports.

Audacity will remember its jack connections, so if jackd is running it comes up the way you left it the last time you shut down.  If in the interim you used Audacity without jack (through Alsa, OSS, etc) then it will have those settings in its memory and you will need to go into preferences and select your inputs and outputs again.

Perhaps this method of doing things seems backwards, but it would be transparent if your distribution set jackd to start automatically at boot time and defaulted all applications to use jack support.

If you set up your Linux box to start Jackd on boot then all these problems go away.  Then you simply need to use a jack-enabled flashplayer plugin for firefox if you want to hear audio from flash videos and then make sure you are using media players that are configured for jack outputs.  I think some people long for the day when jack is the default audio server and all Linux audio programs are written with jack support.  This idea of the user starting a server (jackd) to use certain applications is a side effect of UNIX philosophy, and yields more specific control to the user.  Unfortunately most people coming from a Windows environment don't want that level of control, but instead want it to work out of the box. This level of ease is excellent for a home user or sub-professional, but a studio engineer better understand his equipment, hardware and software to a level where configuration of this equipment in a linux environment is not the problem of the week.  

This thing I alluded to earlier, sessions in jack, will help to cure some of the problems you are experiencing.  You would set up a working environment in jack, save the session and everything is remembered.  Start the jack session, then jack starts, all the programs start, and all the connections are restored as before.  This would do away with the cumbersome patch bay or script writing.

For now, a person could append something to the .jackdrc file with the commands to start certain programs then issues the jack commands to connect the inputs and outputs to the proper place.

There is another program I haven't ever tried, called Patchage.  It is an alternative to qjackctl you may wish to investigate.

---

### Post by MikeRivers on 2010-08-04
> **transmogrifox said:**
> Ah yes, this is true.  When doing Linux audio it is anticipated that jack is running all the time.  Some jack programs will automatically attempt to start jack if it is not already running when you launch the program.  If the ~.jackdrc file contains a proper configuration for your audio hardware it will be successful.
One of the monkey wrenches that I have in the works here is that I'm not always using the same audio hardware. This may not be representative of a "normal" user, but I'm trying to learn what works and what doesn't, or how much trouble it is to get something working that isn't presently working. 

How can I tell if jACK is running if I don't start it from qjackctl? There's probably a command for that but I don't know it. In Windows, I'd look at the Task Manager or Process Explorer and it would give me a list of what was running. 

Even though Paul Davis told me that Ardour automatically starts jACK, I don't get any audio unless I start jACK myself. Perhaps he assumes a "proper" Linux setup. But all I know is what I got when I installed the Ubuntu Studio distribution. 
> 
Unfortunately Audacity does not attempt to start jack if it is not already running (as far as I know).  Instead it only connects to jack if running.
Perhaps this is an oversimplification, or a special case in my setup, but there's clearly a tie-in between jACK and FFADO. When I want to use the Firewire I/O, I need jACK. If I have the USB I/O connected (or not, and use the computer's internal sound card) I don't have to start jACK to get audio in and out of Audacity. Maybe without the help of qjackctl, jACK is starting in some sort of default mode. I'll have to look for a .jackdrc file and see, if it's present, what it says. 
> 
My .jackdrc file contains the following:
/usr/bin/jackd -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2

I suspect that it may be trying to start on boot-up and is looking for something familiar or common. The internal sound card is identified as hw:0,0. If I have the USB interface connected, that's hw:1,0. But the Firewire interface doesn't seem to be identified as hw:anything. 

Oddly, when I disabled the internal sound hardware in the computer's BIOS menu in an attempt to simplify the hardware setup, nothing worked, and the message in qjackctl said it couldn't find anything to connect to even though the Firewire interface that it had been working with was connected (the hardware, anyway). I thought it was broken again until I re-enabled the sound card. 
> If you can successfully start jack with qjackctl, then you can easily start jack with the following command in your user home directory:
sudo chmod +x .jackdrc
./.jackdrc

Where do I put those command lines (is that two lines?) so they'll execute on startup? Are the included in a file? If so, what's the file?
I probably don't actually want to do that, at least until I stop fooling around and decide on a single program and interface to use. Even though I would like to use the Firewire mixer as the input device with Reaper, Reaper doesn't see it. But it works fine with the USB interface (only 2 channels, though).
> 
I can tell you might not like this, but this is the only way to do it:
Start jackd
Start Audacity.

That's not a problem, but if I'm using the Firewire interface, I need to open the jACK Connections window and re-do that. It doesn't stick. I tried setting up a patchbay configuration for it, and I can load that patchbay (which looks correct) but if Inputs 1 and 2 are connected (in Connections) to Audacity inputs 1 and 2, even though the patchbay says 17-18 go to Audacity inputs 1-2, that doesn't happen. 
> 
Or if you want Audacity to route playback into a certain program, or get input from a program (like FX first before Audacity) then you need to have all the other programs running before you can start Audacity.  
That sort of routing has been pointed out to me several times as an example of how great jACK is, but I'll never use it. 
> 
Audacity will remember its jack connections, so if jackd is running it comes up the way you left it the last time you shut down. 

Not here. 
> 
If in the interim you used Audacity without jack (through Alsa, OSS, etc) then it will have those settings in its memory and you will need to go into preferences and select your inputs and outputs again.
Well, maybe with all the thrashing around that I'm doing, I may have inadvertently done that, or ran Ardour with the input-to-track routing.
> 
Perhaps this method of doing things seems backwards, but it would be transparent if your distribution set jackd to start automatically at boot time and defaulted all applications to use jack support.
There may be a good reason why it's not, but it smacks of the distribution being created by someone who never worked in a studio (or maybe did and doesn't want to, ever again). Everything I'm trying to do is based on having real microphones or other sound sources that you actually play. I realize that a lot of people using these programs don't use a microphone but do everything with virtual instruments and modify the sound with other processing programs, so they don't really need any audio interface hardware other than to listen to playback and monitor while they're recording. But if you want to record a band live and have a track for every microphone, you need something with a lot of inputs. 
> 
If you set up your Linux box to start Jackd on boot then all these problems go away.  
But only if you always use the same I/O hardware, or, best case, if you know how to address all of your hardware, which, at this point, I don't.
> I think some people long for the day when jack is the default audio server and all Linux audio programs are written with jack support.
Well, this is what we've come to expect with Windows. When you assign a device as the default Windows audio device any audio program that looks to Windows to tell it what the audio hardware is will use it. If I'm running Audacity in Windows, however, I can override that by selecting the Onyx Firewire driver in the Audacity Preferences. 
> 
This idea of the user starting a server (jackd) to use certain applications is a side effect of UNIX philosophy, and yields more specific control to the user.  Unfortunately most people coming from a Windows environment don't want that level of control
It's not exactly like that. I don't mind having control, but I want the controls to be labeled in plain language and appear in convenient places (like in the program I'm using at the time). 
> 
a studio engineer better understand his equipment, hardware and software to a level where configuration of this equipment in a linux environment is not the problem of the week.  
That would be nice. I'm comfortable with hardware, and I never had to think very hard about Windows, but I feel that I'm always fumbling around with Linux, largely because things aren't documented in a very organized way. If you start from the beginning and learn your way through it methodically, you can get  pretty good at finding what you need. But that isn't something that comes quickly. 

I've had this discussion before, but it always ends up along the lines of "Well, you probably had best not be trying to use Linux for your audio work." I'm perfectly willing to accept that, but all the people who tell you that it's simple can't be wrong. Or maybe they can. 
> 
There is another program I haven't ever tried, called Patchage.  It is an alternative to qjackctl you may wish to investigate.
I'll give it a look. There's a little video about it that seems to make sense to me. Now (from that video) I understand that "system" means what's connected to the monitor output (speakers). I never knew that.

---

### Post by MikeRivers on 2010-08-04
> **transmogrifox said:**
> 
My .jackdrc file contains the following:
/usr/bin/jackd -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2
Mine is:
/usr/bin/jackd -r -dfirewire -r44100 -p1024 -n3 -i2 -o2

Does this file get updated with the last used settings? Since this shows 2 input and 2 output channels, its last use was probably with Audacity.

If having that in my home folder is supposed to make jACK start when I boot up, why do I have to start qjackctl in order to get anything that uses jACK to work? 

Patchage looks like a replacement for qjackctl Connections and it makes a little more sense to me.

---

### Post by transmogrifox on 2010-08-04
I think your situation is starting to become more clear.  Thanks for explaining.  I don't have time right now, but I will see if I can narrow it down to some specific things that can help you.

One thing you have pointed out are all the points I take for granted as obvious to a seasoned Linux user but are not so plain to somebody new to the system.

To start jack on boot you need to edit the following file as root:
/etc/default/jackd

For example, open a terminal and type the following at the prompt
```
sudo gedit /etc/default/jackd
```

Mine has the following info in it:
 ```

# Set to "yes" to start jackd at boot
START_DAEMON=yes

# The jackd process will run under this user
USER=transmogrifox

# Options to pass to jackd
OPTIONS="--t 5000 -d alsa -d hw:0 -r 44100 -p 1024 -n 2"
```

You can obtain the OPTIONS from your .jackdrc file after you have configured it for the desired audio interface that you want active at boot time.  To see them easily, open a terminal and type:
```
cat .jackdrc 
```

Or if you want to do it the GUI way, open a text editor (like gedit), open new file, then in your home directory select the .jackdrc file (assuming your file browser is set to display hidden files).  Either way you look at it, .jackdrc is just a plain text file in your user directory, hidden by default, so you have to enable the "show hidden files" in nautilus if you want to see it.  Else in a terminal you need to do ls -a to see it.

From here: [http://www.debianhelp.co.uk/sound.htm](http://www.debianhelp.co.uk/sound.htm)
```
To see what indexes have been assigned to cards, run:

cat /proc/asound/cards

The first card that ALSA finds is usually given index 0 and thus is usually the 'default' sound card. If you are unlucky then the first sound card found is one that it not suitable for playing system sounds. There are two ways to fix this problem.

1. Force the cards to load in a different order. I chose this route, and added the following to my /etc/modprobe.d/sound:

options snd-trident index=0
options snd-usb-audio index=1
```

Sometimes on boot the card will get a different index than the previous time.  The above will force the same index to the appropriate card.  Then when in the /etc/default/jackd file you identify a hw number, it will reference the same card each time.

Really, you're on the right track.  It doesn't come immediately, but after a while you'll get a feel for how things are done and then it will seem less painful.

It all makes perfect sense ... to a programmer :)

---

### Post by transmogrifox on 2010-08-05
> 
Quote:
Originally Posted by transmogrifox View Post
My .jackdrc file contains the following:
/usr/bin/jackd -t5000 -dalsa -dhw:0 -r44100 -p1024 -n2
Mine is:
/usr/bin/jackd -r -dfirewire -r44100 -p1024 -n3 -i2 -o2

Does this file get updated with the last used settings? Since this shows 2 input and 2 output channels, its last use was probably with Audacity.

Um... this has nothing to do with Audacity.  These settings relate to the audio interface you last used.  Furthermore, you can only use one audio interface at a time, currently (I don't know if this will change in the future).  The way to deal with multiple audio interfaces now is to change the settings and restart jack.  The only place qjackctl plays in here is it gives you a user interface to configure this file so you don't have to use the UNIX style man page and command line to do it. Really, Windows apps do the same kind of thing, but they hide these settings in a binary format that can't be read or edited by a human.

> 
If having that in my home folder is supposed to make jACK start when I boot up, 

This is not for boot up, this is for jack aware applications that try to launch jack if it's not running. See my other post about starting jackd on boot.
> 
why do I have to start qjackctl in order to get anything that uses jACK to work?

You don't need qjackctl.  It's a graphical tool to supposedly make it easier to manage jack and make connections between programs.  
You could do this from the command line:
jack_lsp to find out the names of inputs and outputs
jack_connect  to connect port names
jack_discconnect  to disconnect port names.

You could write a bash script to launch programs you are using in an environment then issue the commands to make all desired connections.  This is essentially what jack patch bay attempts to do in a GUI format.
  
So...  I see a possible misunderstanding about jack.  Launching jack only launches the server.  Jack by default does this when launched:
Make inputs and outputs of the audio interface available for connection. The server jackd creates an environment where programs written using the jack API can connect to eachother and their processing threads will have highest priority so everything can be done in real time (no glitches, pauses or latency on a properly configured system).
Nothing more. The other programs need to be started and have their inputs and outputs registered with jack before you can even think about connecting them.  Most programs let you preconfigure where they connect in the settings, else you need to do it manually.

When you start jack, all you will see in the jack tab of qjacktl are readable and writable ports of the configured audio interface, labeled "System".  On the outputs side is everything your soundcard can feed to you (and it represents the inputs to the sound card, but is where jack outputs these signals for use by programs).  The System inputs side represents any place you can send audio, or write to.  If you want send audio out your sound card channel 4, then you connect the output of the last program in the processing chain to the soundcard *input* from the computer's point of view.

Other applications manage connections between ports.  For example, when you launch a new jack aware application you will see its input and output ports become available.  When you launch Audacity, it does not make any ports available until it is actually recording or playing.  Audacity expects to find other jack ports to connect itself to.  
Jack does not remember anything about the clients that were connected.  Piece by piece here is what the above options mean:
/usr/bin/jackd 
full path to the jackd executable
-r
that is strange that -r appears with no arguments, it should be -R to indicate realtime priority
-dfirewire
firewire interface
 -r44100
sample rate 44100
-p1024
1024 frames per period.  I recommend 256 or less if you desire low latency. This is the main reason applications use jack, is so you can get <5ms latency.
-n3 
3 of periods of latency.  This is better set to 2 
-i2
number of input channels
 -o2
number of playback channels.  
You can delete the -i and -o entries and the default will be the maximum number supported by the connected hardware.  This simply lets you limit the number you want to expose to jack.

You can find more about these options in the man page
man jackd

I hope I didn't use too many words. Jack is something similar to ASIO, only it isn't necessarily transparent to the user (as you have discovered).  ASIO just does its thing and you don't have to do anything other than open a program and stuff works.  On the other hand it isn't flexible.  It can't do anything more than what you get...and certainly can't route audio around between applications like jack is able to do.

The flexibility of jack is the strength, the weakness is complexity contributing to a steep learning curve.

I am assuming since you keep reading this thread and posting you really want to get a Linux audio system working and useable.  If that is the case, you will get there by doing what you're doing:
Read forum posts
Search the web
Try a bunch of stuff and observe the outcome.

Eventually these things will become plain to you :)

I wish we could all wave a wand and make it as easy as we wish it were, and I agree with you...I wish the names of audio cards and input/output channels made more sense to the common user.  They make sense from a system/machine point of view, but we're not machines who read it :)

take care

---

### Post by MikeRivers on 2010-08-06
I've tried to get JACK to start by itself but so far no go.  Here's what my revised /etc/default/jackd file looks like:

# Set to "yes" to start jackd at boot
START_DAEMON=yes

# The jackd process will run under this user
USER=mike

# Options to pass to jackd
#  OPTIONS="-R -d alsa -d hw"
OPTIONS="-r -dfirewire -n2 -r44100 -p1024 -d hw:1,0"

The options may not be all correct but at least something should start. I'm not sure about the structure of the options line, though. In your example, you have a space between d and alsa. I copied it as it is in my .jackdrc file. 

As far as the real time priority setting -R goes, I've found that Ardour consistently hangs if I have that set in the checkbox in the qjackctl Setup window, so probably it's best to leave it off, at least until other things are working better. 

The examples that you've been giving me have all been for alsa. Do you use any Firewire audio devices? I wonder if there's some disconnect (which it may be possible to connect) between jack starting and the specifed device being firewire. If I let Ardour start with the ALSA driver and the Intel (built in) sound card, it doesn't complain immediately, but still, when I try to open a project, it tells me that the audio engine can't start without jACK running. If I select FFADO as the driver before opening a project, Ardour won't let me go any further. I have to quit Ardour and manually start jACK before starting Ardour again. Maybe I'm at the point where I should be asking about this in an Ardour forum. 

I really appreciate your explanations here. You've helped me immensely in figuring out how it's supposed to work. Soon, though, I'm going to, in the words of our soon-to-be BP ex-CEO, get my life back.

---

### Post by Flaggmann on 2011-06-18
When you are using jackd (qjackctl) the patchbay display will show the system on opening with generic terms to identify inputs and outputs.

Some applications will automatically when you launch them (eg qtractor) however, others
like audacious won't show until you actually press or click on PLAY.

Some apps you need to use the prefs or menu options to tell the program to be "jack-aware" and use jack.

If you view the patchbay window and open the apps up you want, you will notice they come up with generic numbers and terms; you can click on any one of these items to highlight them and then click the edit button and change the descriptive names to whatever you are comfortable working with, then save it. Kind of like setting up a profile or template.

In the Connections window you can RIGHT-CLICK on any item and select rename to do the same thing for that session at least, if not always( have tested to see if renaming and restarting preserves the new name at this point.)

If you do changes in the Patchbay using the edit function and save it, giving it a new filename it will appear exactly as you saved it IN THE PATCHBAY WINDOW next time;however, whenever I have tried to have jack start with that template or profile file loaded on startup I have not seen those custom labels or patches implemented as saved. I don't know why it is supposed to I understand but for me it doesn't appear to load it.

---

### Post by Flaggmann on 2011-06-18
To autostart jack on login, add qjackctl to the "system --> preferences -->load on startup
options.

You can also use the /etc/init.d method, but unless you want it running when logged off, in the case of a server, the startup folder option gives you flex to deselect it and reselect it as your needs change. Just add or remove a check mark in the startup folder window.

---

### Post by Flaggmann on 2011-06-18
using the qjackctl in the startup folder method should solve your firewire and other apps throwing errors whe you start jack, because jack needs to be running BEFORE you start these apps etc. They are connecting to a configurable audio server that they expect to see running and available. Trying to start it after the fact is a bit like issuing a command to open the mysql window and connect to a database and then expecting that command to start when you start the mysqld running in the following command line; it won't work.

---

### Post by MikeRivers on 2011-06-18
Thanks for the tips. This is a year old thread and I've long abandoned any hope of using Ubuntu with any of the more "pro" audio hardware that I own. So I continue to remain a non-convert. But I'll give it a shot again in another year or so, and will likely be back with some new questions.

---

### Post by Flaggmann on 2011-06-18
See attachment. As I said in earlier posts, you can tailor the generic PortAudio designation that **AUDACITY generates NOT jack audio**, to whatever you want in the patchbay template/profile window and then tell qjackctl setup to use it everytime. So it will always be familiar for you.



One should consider themselves fortunate that jack offers a user window GUI that allows you this control, there are other coding purists that would rather the GUI be left out entirely and you have to jump into the code and manually edit a slew of config files with notepad type editors instead.

The whole idea of opensource programming is that it maintains a specific standard that all developers can use and that means we get a couple of extra setup steps inthe process; a small price to pay for an amazing selection of no-cost or low cost software. 

Of course if you think that this doesn't suit your needs, and you have the extra disposable cash , fill your boots and buy a whack of what you consider to be BETTER
Windows based products.... Even when business wants customized open source linux products they PURCHASE the supported enterprise versions; they don't try and get away with the no cost versions and whine about having to learn about the systems themselves, because others won't give them what they want. 

You have the flexibility here to customize it to your needs so make use of it; if not then buy the supported versions and use their forums to get what you need.

Most here are just other users, some more experienced and advanced that others but all are just users helping users, and many are struggling artists trying to get their compositions to the public as economically as possible.

---

### Post by MikeRivers on 2011-06-18
> **Flaggmann said:**
> 
Of course if you think that this doesn't suit your needs, and you have the extra disposable cash , fill your boots and buy a whack of what you consider to be BETTER
Windows based products.... 


I'm not in any way anti-source, but I'm not a developer, I'm an end user. I've invested my cash in audio hardware years ago that works fine with Windows software when the manufacturer-supplied drivers are installed. 

None of the audio hardware that I have aside from the computer's built-in sound card and a Behringer stereo USB interface are supported by any of the open source audio projects currently available. So no matter how good, how flexible, and how configurable the open source audio applications are, I would have to re-equip myself with new hardware in order to run them.

But even if I did, I still wouldn't get the full benefit of the type of I/O hardware that I have now. Linux developers seem to call it quits when they get sound in and out of the box and don't attempt to support other useful features such as built-in DSP-based low latency mixing. 

At this time, it just doesn't make any sense for me to consider Linux based audio production to be anything but something to piddle with when I have the time to investigate what's new and how close they're getting to coming up with a platform that's as adaptable by a non-programmer as Windows is. I see some good progress in the software, but until either hardware manufacturers decide that it's worth their time to provide Linux drivers for their products, or until some really hip-to-audio driver writer jumps into the multichannel audio I/O hardware pool and provides full function support for contemporary hardware, It'll remain on my test bench. 

I don't want to start or participate in a Window vs. Open Source discussion here, I just want you to understand why I'm not bubbling over with enthusiasm about a couple of useful tips to using jack. 

Thanks, genuinely, for your recent contributions to this thread. I've saved them and they'll probably come in handy next time I decide to piddle.

---

### Post by cchhrriiss121212 on 2011-06-18
> **MikeRivers said:**
> Linux developers seem to call it quits when they get sound in and out of the box and don't attempt to support other useful features such as built-in DSP-based low latency mixing. 

I know your devices do not work fully on linux, but this statement is not fair to the devs. There are a great deal of devices supported, including high-end cards:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
[http://www.ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2](http://www.ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2)[]=perfect&filter2[]=verygood&filter2[]=good
The degree of completion these drivers reach often depends on the co-operation of manufacturers, and with that in mind, I think the devs do the best with what they have. 

I can't speak for any other devices, but I know my M-Audio card makes use of hardware mixing at a low latency.

---

