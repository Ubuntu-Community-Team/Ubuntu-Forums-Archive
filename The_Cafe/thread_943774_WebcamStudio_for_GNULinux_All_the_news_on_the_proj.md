---
title: "WebcamStudio for GNU/Linux: All the news on the project!"
date: 2008-10-10
forum: The Cafe
---

### Post by patrickballeux on 2008-10-10
WebcamStudio for GNU/Linux 0.53 is now available on sourceforge.net

[http://www.ws4gl.org/](http://www.ws4gl.org/)


This software will let you create a virtual webcam like ManyCam does for Windows users. There is a bunch of features and it is compatible with Flash site (using Flash 10)

New Features:
> 
# Added Italian Language
# Added Dutch Language
# Added Spanish Language (+2 locales)
# Added Russian Language
# Some cleanup in classes
# Added Animations in Source Browser
# Moved menu WS4GL Animations into Source Browser
# Added new Widget feature
# Fixed performance issues
# Added Wide mode support for main window
# Added mini 16:9 format
# Added broadcasting capacity for FME/Wowza/Red5 servers (FME 2.5)
# Added Source Browser (Can add Devices, Images, Animations, Widgets and Movies)
# Added option to hide/show mouse cursor on Desktop source
# Added the GISS Caster to output live to the GISS server
# Added auto command to give read access to /dev/raw1394
# Added a new source list
# Added output framerate
# Added DV source
# Improved performance on recorders
# Changed AVI format to xvid instead of mjpeg
# Added option to display or not the splash background
# Added audio level input in animations
# Fixed scrolling speed in text sources
# Improved text rendering
# Added output Quality selection
# Minor fix on Desktop source
# Hot pluging of webcams supported



You do not need any webcam as you can simply broadcast your desktop, images or movies as a virtual webcam.

See the wiki for installation procedure and other details...

The project tries to give a fun and easy solution for the non-geek user to be able to broadcast in their own style.


Read the wiki for installation, you'll need the vloopback module from the Flashcam project to broadcast in a virtual webcam. But without you can at least see the results in the preview display.

---

### Post by patrickballeux on 2008-10-16
Version 0.18 is out!

---

### Post by patrickballeux on 2008-10-23
Version 0.19 is out!

---

### Post by YoungQuiz on 2008-10-23
thanks,i'll check it out

---

### Post by patrickballeux on 2008-10-24
The project is now in beta stage instead of alpha stage...  Wouhou!
:guitar:

---

### Post by DoctorMO on 2008-10-25
How goes? I have a webcam so I'm not sure I need emulation. But I like to see other developers in the Ubuntu forums. UF can be so unpleasantly boring to programmers, users just don't seem to worship you like they ort to ;-).

---

### Post by patrickballeux on 2008-10-25
> **DoctorMO said:**
> How goes? I have a webcam so I'm not sure I need emulation. But I like to see other developers in the Ubuntu forums. UF can be so unpleasantly boring to programmers, users just don't seem to worship you like they ort to ;-).

Hi, it's going well.

WebcamStudio is not about emulation, but about have a webcam with special effects, overlays, multiple webcams at the same time... See the wiki on the project for videos that show what it can do.  It's about having fun with your webcam.

Remember that users are not programmers so they don't know how much effort it takes to create a software... Black Magic Voodoo and Coding is essentially the same thing for "real" people! :)

Have a nice day!
:guitar:

---

### Post by patrickballeux on 2008-10-27
Version 0.20 is out!

---

### Post by quinnten83 on 2008-10-27
Time to start fighting to have it included in the repositories.

---

### Post by patrickballeux on 2008-10-28
> **quinnten83 said:**
> Time to start fighting to have it included in the repositories.

I looked how to proceed, and it is not really simple.  I was kind of lost over all the setup to put the project available for the repositories.  

If someone know how to do that or that the integration in charge, it would be appreciated.

---

### Post by HumanAnarchist on 2008-11-03
Nice work Patrick!!

Some issues that I got:

* I can't make it work with skype... don't know if it's skype or webcamstudio that's the problem
* Are there some logging info I can access? 
* Can you make it possible to mix effects, like cheese, like have one effect on top of another effect? 
* Why do I need to restart the source if I want to use the Gstreamer effects? 

And I could never make the sound work with jack... I would be cool to swich between diffrent sound sources. Like Rythmebox, front mic, headset mic, webcam mic++

And keep up the great work, you sure work fast :D 

-ha-

---

### Post by HumanAnarchist on 2008-11-03
how do I delete posts? gaaaah

---

### Post by patrickballeux on 2008-11-03
Hi HumanAnarchist!

It does not work with skype for now.  I'll have to try to find out why (Probably an issue with the vloopback module).  It is working with aMSN, Flash, Wengophone, camstream.  I'm still trying to find other software that can use V4L devices...

Mixing effects could be possible, but is not enabled for now.  I just need to make sure that everything is stable enough, and then I'll look to enable multi-effect.  It's a matter of time.

As for having to restard to apply a Gstreamer effect is a litimation of the gstreamer framwork.  I have filled a request on thise issue.  Actually, I was able to remove the effect, but not add/replace a Gstreamer effect using the library.  That's why they are in their own tab since they do not behave as other effects.

Jack can be a beast to master, but wait for the next release, I was able to use the pulseaudio server (that is installed by default in Ubuntu) to create a virtual microphone.  So no need anymore for Jack or Alsa as everything is done in the puslseaudio server.  To give you an idea, I can add a delay on the microphone to sychonize mic/webcam and use a 3 bands equalizer to have a better sound.  You will simply have to use the "pavucontrol" to managed what sound is sent to the "virtual" microphone.  For example, send the "real" microphone to the "virtual" microphone, send your music also to that "virtual" microphone as background music and more the recording stream for Flash to read from the virtual microphone...

For now things will be simple, but as releases will work better, new features will be possible.

Hope you like it!


> **HumanAnarchist said:**
> Nice work Patrick!!

Some issues that I got:

* I can't make it work with skype... don't know if it's skype or webcamstudio that's the problem
* Are there some logging info I can access? 
* Can you make it possible to mix effects, like cheese, like have one effect on top of another effect? 
* Why do I need to restart the source if I want to use the Gstreamer effects? 

And I could never make the sound work with jack... I would be cool to swich between diffrent sound sources. Like Rythmebox, front mic, headset mic, webcam mic++

And keep up the great work, you sure work fast :D 

-ha-

---

### Post by patrickballeux on 2008-11-04
WebcamStudio for GNU/Linux 0.30 is out!  Yeah! It's different!

---

### Post by HumanAnarchist on 2008-11-04
Got some exceptions...

```

Mon Nov  3 17:54:07 ARST 2008
~
workingnorm@smartypants: pts/2: 20 files 736Kb -> webcamstudio 
Error loading device: video1
Error loading device capacity video1
Pointer Size: 4
Error loading device: video2
Error loading device capacity video2
Pointer Size: 4
Exception in thread "AWT-EventQueue-0" java.lang.IllegalArgumentException: No such Gstreamer factory: ladspa-delay-5s
        at org.gstreamer.ElementFactory.makeRawElement(ElementFactory.java:172)
        at org.gstreamer.ElementFactory.make(ElementFactory.java:164)
        at webcamstudio.Pulseaudio.<init>(Pulseaudio.java:90)
        at webcamstudio.WebcamStudio.chkManagePusleAudioActionPerformed(WebcamStudio.java:3492)
        at webcamstudio.WebcamStudio.access$6300(WebcamStudio.java:35)
        at webcamstudio.WebcamStudio$88.actionPerformed(WebcamStudio.java:2265)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.JToggleButton$ToggleButtonModel.setPressed(JToggleButton.java:291)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6041)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5806)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4413)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4243)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2440)
        at java.awt.Component.dispatchEvent(Component.java:4243)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.IllegalArgumentException: No such Gstreamer factory: ladspa-delay-5s
        at org.gstreamer.ElementFactory.makeRawElement(ElementFactory.java:172)
        at org.gstreamer.ElementFactory.make(ElementFactory.java:164)
        at webcamstudio.Pulseaudio.<init>(Pulseaudio.java:90)
        at webcamstudio.WebcamStudio.chkManagePusleAudioActionPerformed(WebcamStudio.java:3492)
        at webcamstudio.WebcamStudio.access$6300(WebcamStudio.java:35)
        at webcamstudio.WebcamStudio$88.actionPerformed(WebcamStudio.java:2265)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.JToggleButton$ToggleButtonModel.setPressed(JToggleButton.java:291)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
	at java.awt.Component.processMouseEvent(Component.java:6041)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5806)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4413)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Window.dispatchEventImpl(Window.java:2440)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)



```

---

### Post by HumanAnarchist on 2008-11-04
Not sure if I like the new layout, since it was convinient to have always be able to see the display window, the you fiddle around with effects and text... 

But still great work, always fun to test new versions :) 

-ha-

---

### Post by patrickballeux on 2008-11-04
Hi,
 
You are missing a plugin for gstreamer...  

You should have gstreamer0.10-plugins-bad installed...  In that package, you have the required library: libgstladspa.so

Are you using the tar.gz or the debian package?  The debian is resolving those dependencies, but if your using the tar.gz, it would explain everything...

So run "sudo apt-get install gstreamer0.10-plugins-bad" in a terminal and you'll have the required module.

Let me know!

Pat


> **HumanAnarchist said:**
> Got some exceptions...

```

java.lang.IllegalArgumentException: No such Gstreamer factory: ladspa-delay-5s
        at 

```

---

### Post by patrickballeux on 2008-11-04
Thanks for the input.

That's what I had in mind, being able to see everthing at once.  But as I was using it, and looked at users trying to find their way around the controls, it was more annoying thant anything else.  95% of the time, you see your webcam in the software your are using to broadcast (Flash sites, aMsn...) so the preview is only useful for drawing or moving/resizing...  Also, having all the controls in tabs give the ability to display more controls in less space.

And it is easier to show more info and feedback with tabs than with frames in a virtual desktop. 

I'll continue improving the GUI with time, but I'm trying to find the perfect balance between functionalities and intuitive usage...  :)

Pat

> **HumanAnarchist said:**
> Not sure if I like the new layout, since it was convinient to have always be able to see the display window, the you fiddle around with effects and text... 

But still great work, always fun to test new versions :) 

-ha-

---

### Post by HumanAnarchist on 2008-11-04
> **patrickballeux said:**
> Hi,
 
You are missing a plugin for gstreamer...  

You should have gstreamer0.10-plugins-bad installed...  In that package, you have the required library: libgstladspa.so

Are you using the tar.gz or the debian package?  The debian is resolving those dependencies, but if your using the tar.gz, it would explain everything...

So run "sudo apt-get install gstreamer0.10-plugins-bad" in a terminal and you'll have the required module.

Let me know!

Pat

I'm using the .deb to install and gstreamer0.10-plugin-bad is installed, so then I dont know what's wrong. I'm using Mint Linux though, don't know if that got something to do with the problem. 

Let me know if you need some other debug info from my computer. 

-ha-

---

### Post by patrickballeux on 2008-11-04
Ok, you are using Mint...  Maybe the lapdsa plugin is not part of the gstreamer0.10-plugin-bad in Mint.

I am currently using Ubuntu 8.10 so maybe it is part of the new version only...  My version of gstreamer-plugins-bad is 0.10.8-1.  What is your version?

In a terminal, run this command:

```
gst-inspect ladspa-delay-5s
```

If it say that it does not exists, then it means that this plugin is not part of your gstreamer-plugins-bad...

So we need to figure out how to install this module in Mint.

Have a look in your repositories if this plugin could be available under another package name.

EDIT:  I just saw that I installed ubuntustudio-audio-plugins so it means that I have a lot of plugins normally not found in regular Ubuntu... I also found that there is a package named ladspa-sdk that seems to provide the plugin that could be used by gstreamer-plugins-bad...  Install that package to see if it would work.  

Let me know!



> **HumanAnarchist said:**
> I'm using the .deb to install and gstreamer0.10-plugin-bad is installed, so then I dont know what's wrong. I'm using Mint Linux though, don't know if that got something to do with the problem. 

Let me know if you need some other debug info from my computer. 

-ha-

---

### Post by HumanAnarchist on 2008-11-04
> **patrickballeux said:**
> Ok, you are using Mint...  Maybe the lapdsa plugin is not part of the gstreamer0.10-plugin-bad in Mint.

I am currently using Ubuntu 8.10 so maybe it is part of the new version only...  My version of gstreamer-plugins-bad is 0.10.8-1.  What is your version?

In a terminal, run this command:

```
gst-inspect ladspa-delay-5s
```

If it say that it does not exists, then it means that this plugin is not part of your gstreamer-plugins-bad...

So we need to figure out how to install this module in Mint.

Have a look in your repositories if this plugin could be available under another package name.

EDIT:  I just saw that I installed ubuntustudio-audio-plugins so it means that I have a lot of plugins normally not found in regular Ubuntu... I also found that there is a package named ladspa-sdk that seems to provide the plugin that could be used by gstreamer-plugins-bad...  Install that package to see if it would work.  

Let me know!


OK, that EDIT was usefull, because I did not have the ladspa-delay-5s, but maybe I will get it when I install the other stuff, will see... 

...please wait while testing... :) 

-ha-

---

### Post by patrickballeux on 2008-11-06
Version 0.31 is out!

---

### Post by patrickballeux on 2008-11-10
Version 0.32 is out!

---

### Post by buzzstray on 2008-11-11
I've installed WebcamStudio 0.32. But, I still get this error message:

> Error loading device: video0
Error loading device capacity video0
Exception in thread "Thread-5" java.lang.NullPointerException
        at webcamstudio.WebcamStudio.run(WebcamStudio.java:548 )
        at java.lang.Thread.run(Thread.java:619)

I'm using Ubuntu 7.10 Gutsy Gibbon.

---

### Post by patrickballeux on 2008-11-12
Hi Buzzstray

I haven't try WebcamStudio under Gutsy Gibbon, so you'll be my guinea pig :)


```
Error loading device: video0
Error loading device capacity video0

```
For this, it would be ok if you don't have a webcam or if you loaded vloopback module before connecting your webcam.  When scanning for video input, WebcamStudio is also scanning the vloopback virtual device which are alway returning with an error.  Can you validate if /dev/video0 is a vloopback or an actual webcam?

```

Exception in thread "Thread-5" java.lang.NullPointerException
at webcamstudio.WebcamStudio.run(WebcamStudio.java:54 8 )
at java.lang.Thread.run(Thread.java:619) 
```

This one does not make sense as it looks like you are trying to load a studio file that was not found (And thanks, you found a bug for me).  Were you trying to load a Studio file on loading Webcamstudio (java -jar WebcamStudio.jar -studio foo.studio)?  If that's the case, the the file you've provided was now found by WebcamStudio, make sure to provide the full path enclosed between "" if there is some spaces in the path...

If not, then I'll have to test using a vbox to find out what it not working.  Make sure that you are running Java 6 and not Java 5 as your default Java.  Have you started WebcamStudio using "java -jar WebcamStudio.jar" or "webcamstudio"?

We could do some investigation from there.

Let me know!

---

### Post by buzzstray on 2008-11-12
A guinea pig? Sounds not bad for me :)

/dev/video0 on my device is the ouput that's created by vloopback. And yes, I don't have real webcam. The reason of why I use WebcamStudio is for broadcasting video capture from my dv cam.

I run this program using java 6. Beside I run WebcamStudio from main menu, I also run this program using command line:
> java -jar WebcamStudio.jar
But the error message still same.

Thx

---

### Post by patrickballeux on 2008-11-12
Hi, 

I just tested in Ubuntu 7.10 (Gutsy Gibbon) 32 bits, inside a virtual box with all updates, and beside the vloopback wizard that does not run (Zenity compatibility problem), everything works well.

I tried starting without the vloopback module loaded, but it works as expected. I really wonder why you have this error message.

Is 0.31 (or any other version) working?  That could help me figure out what is not working...

Do you have a really fast computer?  I am wondering if the fact of starting the virtual webcam as WebcamStudio is starting could end-up in a race condition.  

You can prevent the webcam to autostart:  In your home folder, put that xml into file "~/.java/.userPrefs/webcamstudio/prefs.xml"
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE map SYSTEM "http://java.sun.com/dtd/preferences.dtd">
<map MAP_XML_VERSION="1.0">
  <entry key="LAF" value="javax.swing.plaf.metal.MetalLookAndFeel"/>
  <entry key="autostartwebcam" value="false"/>
  <entry key="dividerlocation" value="469"/>
  <entry key="height" value="624"/>
  <entry key="outputsize" value="0"/>
  <entry key="textbackground" value="java.awt.Color[r=0,g=0,b=0]"/>
  <entry key="textbackgroundint" value="-6750208"/>
  <entry key="textcolor" value="java.awt.Color[r=235,g=247,b=31]"/>
  <entry key="textcolorint" value="-6684673"/>
  <entry key="valign" value="1"/>
  <entry key="width" value="1005"/>
  <entry key="x" value="567"/>
  <entry key="y" value="59"/>
</map>

```

The "autostartwebcam" set to false should get you further when loading...


Let me know!

> **buzzstray said:**
> A guinea pig? Sounds not bad for me :)

/dev/video0 on my device is the ouput that's created by vloopback. And yes, I don't have real webcam. The reason of why I use WebcamStudio is for broadcasting video capture from my dv cam.

I run this program using java 6. Beside I run WebcamStudio from main menu, I also run this program using command line:

But the error message still same.

Thx

---

### Post by buzzstray on 2008-11-12
I've run WebcamStudio without vloopback and there no error message at all. This the output description of vloopback from dmesg command:
```
Linux video capture interface: v2.00
vloopback: Video4linux loopback driver v1.1.2
vloopback: Loopback 0 registered, input: video1, output: video0
```
This vloopback came from flashcam package. Almost all version of vloopback works good while the input video come from pipe, where the pipe is a result of combination ffmpeg and mjpegtools_yuv_to_v4l.

I also have tried version 0.31. It doesn't working as well. Still outputing the same error message.

My computer spec is Intel Dual Core 2.8 GB with 512MB RAM. 128MB video adapter's RAM.

You're XML code has been copied to the mentioned file. And, still no luck for me.

Thx a lot...

---

### Post by patrickballeux on 2008-11-12
This is a real mistery :)

EDIT:  When you start WebcamStudio without the module loaded, do you see the WebcamStudio icon in your system tray?  You should see a small icon and when you click on it, you have a menu to start/stop the webcam.

EDIT2: I think I found the problem...  If you don't see the tray icon of WebcamStudio, then that why it is crashing.  If forgot to check if the trayIcon object was initialized.  Normally, it would be set on all system, but in your case, that could be part of the problem...  I'll wait on your answer about the tray Icon and make a special version for you to test my fix.

EDIT3:  I just found out that SystemTray with Java 6 < update10 is not well supported if Compiz is enabled...  Is Compiz enabled on your desktop?  If so, try without Compiz.  The Java 6 => update 10 has solved this issue... (Next release of WebcamStudio will deal correctly with this...)

I see that you are using vloopback 1.1.2.  Have you tried using 1.1.3 instead.  I cannot use 1.1.2 on my setup since it won't compile at all (That's why I worked on 1.1.3).

Actually, I don't think it will make it work, but my tests under 7.10 were made with 1.1.3 and not 1.1.2...  Maybe something changed a little.

But you've narrowed the problem to the output to vloopback, so I have a better idea where to look now.


Using version 0.32, start it without the vloopback module driver loaded.  Then go in the option menu, and uncheck "autostart webcam". Close the WebcamStudio, load the vloopback driver and start again WebcamStudio.  Tell me what you see then in the "Virtual Webcam" tab.  Can you see the "Vloopback Input Device" in the list?

If so, then start the virtual webcam and have a look at the terminal, tell me if you see the number 4 or 8 when starting and any error messages.

Thanks


> **buzzstray said:**
> I've run WebcamStudio without vloopback and there no error message at all. This the output description of vloopback from dmesg command:
```
Linux video capture interface: v2.00
vloopback: Video4linux loopback driver v1.1.2
vloopback: Loopback 0 registered, input: video1, output: video0
```
This vloopback came from flashcam package. Almost all version of vloopback works good while the input video come from pipe, where the pipe is a result of combination ffmpeg and mjpegtools_yuv_to_v4l.

I also have tried version 0.31. It doesn't working as well. Still outputing the same error message.

My computer spec is Intel Dual Core 2.8 GB with 512MB RAM. 128MB video adapter's RAM.

You're XML code has been copied to the mentioned file. And, still no luck for me.

Thx a lot...

---

### Post by patrickballeux on 2008-11-12
Hi Andre,

Here is a small java code that I want you to run.  This will tell me if System Tray is supported in your desktop.  See attachement.

Uncompress in a folder, run "./testtray.sh" from a terminal.

It will compile the TestTray.java source code and run the java class.  This will tell us if you have System Tray support.

Bonus:  In case you are not able to compile, use the .class and run "java TestTray" from the same folder.


Let me know...

---

### Post by buzzstray on 2008-11-13
I have run testtray before and after installing new Java where the WebcamStudio is still running. It send this message:
```

./testtray.sh: line 1: javac: command not found
System Tray is not supported...

```

The actual problem is, as you ever mentioned, this program is not compatible with Java 6 < 10. After I've done installing Java 6.10, the icon tray showed up and WebcamStudio run without problem. It work fine in Flash Chat and Gyachi.

Now, I'm running WebcamStudio 0.32 with vloopback 1.1.3 and Java 6.10 under Gutsy Gibbon. I'm also using GNOME with Compiz enabled.

Thanks for your help. I'll be visit this forum as often as I can, in case there's new version of WebcamStudio. ;)

---

### Post by patrickballeux on 2008-11-13
Ha great...  Next release is now correctly working if SystemTray is not supported.

It was really a stupid bug that I introduced...

---

### Post by patrickballeux on 2008-11-13
Version 0.33 is out!

---

### Post by buzzstray on 2008-11-13
> **patrickballeux said:**
> Ha great...  Next release is now correctly working if SystemTray is not supported.

It was really a stupid bug that I introduced...

If there's something to miss in developing a program, it's not stupid at all. I think it oftenly happen. That's why you need volunteer tester.

You don't intend to make WebcamStudio is compatible with Java version below 6.10, do you? For me it's OK, but there are still many linux user who are using Gutsy Gibbon, where it doesn't include java 6.10 in its packages.

And, ahh... WebcamStudio version 0.33. Yup, system tray checking support is highly recomended. ;)

---

### Post by patrickballeux on 2008-11-13
> **buzzstray said:**
> If there's something to miss in developing a program, it's not stupid at all. I think it oftenly happen. That's why you need volunteer tester.

You don't intend to make WebcamStudio is compatible with Java version below 6.10, do you? For me it's OK, but there are still many linux user who are using Gutsy Gibbon, where it doesn't include java 6.10 in its packages.

And, ahh... WebcamStudio version 0.33. Yup, system tray checking support is highly recomended. ;)

Thanks,

0.33 is (fully) compatible with previous Java 6 version.  Actually, all version were meant to be compatible, but I had made a little bug in the code that prevented this... :)

I'm gonna work on the wizard also to install the vloobpack, currently, it is not working on old release of Ubuntu but there is always the terminal script that does the same thing from the /usr/share/webcamstudio/vloopback-src folder.

Back to coding!

Patrick
:guitar:

---

### Post by buzzstray on 2008-11-14
Hi Patrick,

I want to report that I found this error message.
```

Exception in thread "Thread-5" java.lang.NullPointerException
        at webcamstudio.WebcamStudio.run(WebcamStudio.java:548)
        at java.lang.Thread.run(Thread.java:619)
```

This message show up when I'm trying to run WebcamStudio under Java version 6.03 with vloopback enabled. But, if I'm trying to do the same thing with vloopback disabled, the error message won't show up. The version of vloopback  is 1.1.3.

Thx

---

### Post by patrickballeux on 2008-11-14
Hi buzzstray,

Thanks for the report.

It's the same as previous one.  I'M assuming that it was with version 0.33, right?

I'll make a test on my setup with this java release.  Something is not working as expected.

The problem is not with VLoopback, it releated to the system tray again (I think).

Thanks for reporting.


> **buzzstray said:**
> Hi Patrick,

I want to report that I found this error message.
```

Exception in thread "Thread-5" java.lang.NullPointerException
        at webcamstudio.WebcamStudio.run(WebcamStudio.java:548)
        at java.lang.Thread.run(Thread.java:619)
```

This message show up when I'm trying to run WebcamStudio under Java version 6.03 with vloopback enabled. But, if I'm trying to do the same thing with vloopback disabled, the error message won't show up. The version of vloopback  is 1.1.3.

Thx

---

### Post by buzzstray on 2008-11-14
Yup, it's the version 0.33.

> **patrickballeux said:**
> Hi buzzstray,

Thanks for the report.

It's the same as previous one.  I'M assuming that it was with version 0.33, right?

I'll make a test on my setup with this java release.  Something is not working as expected.

The problem is not with VLoopback, it releated to the system tray again (I think).

Thanks for reporting.

---

### Post by patrickballeux on 2008-11-14
Hi buzzstray,

I just tested with Java 6.3 (from Ubuntu 7.10), and all is working well with 0.33 (even 0.32)...  The only thing I cannot test is using Compiz since this is a VirtualBox setup.

Do you see in your terminal "Pointer Size is 4" (or 8 ) just before/after the exception?

And by disabling Compiz?

I'm gonna need you to test since I am unable to reproduce the problem.

Here is a link to a special build of Webcamstudio.  Put the jar in /usr/lib/webcamstudio, and from the terminal, run:

[URL="http://www.adrive.com/public/265dfdf910e6eba07672e19bef9de184b48a03dc2f08021d90eb7d2accbc8f04.html"]http://www.adrive.com/public/265dfdf910e6eba07672e19bef9de184b48a03dc2f08021d90eb7d2accbc8f04.html
[/URL]

```
/usr/lib/jvm/java-6-sun/bin/java -jar WebcamStudio-test.jar
```

Send me the output here...

Thanks!

> **buzzstray said:**
> Yup, it's the version 0.33.

---

### Post by buzzstray on 2008-11-15
WebcamStudio 0.33 is running well using Java 6.03 and without compiz.

I also have run WebcamStudio-test.jar with compiz disabled. And here is the error message:
```

Exception in thread "main" java.lang.NoClassDefFoundError: org/gstreamer/elements/RGBDataSink$Listener
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

I don't put all WebcamStudio files under "/usr" directory. I put those files under home directory $HOME/webcamstudio. So, I copied WebcamStudio-test in the same directory as WebcamStudio. Is it OK?

This is the command line:
```
java -jar $HOME/webcamstudio/WebcamStudio-test
```

I don't see "Pointer Size is 4" (or 8 ) in my terminal. The only things I see are those error message.

> **patrickballeux said:**
> Hi buzzstray,

I just tested with Java 6.3 (from Ubuntu 7.10), and all is working well with 0.33 (even 0.32)...  The only thing I cannot test is using Compiz since this is a VirtualBox setup.

Do you see in your terminal "Pointer Size is 4" (or 8 ) just before/after the exception?

And by disabling Compiz?

I'm gonna need you to test since I am unable to reproduce the problem.

Here is a link to a special build of Webcamstudio.  Put the jar in /usr/lib/webcamstudio, and from the terminal, run:

[URL="http://www.adrive.com/public/265dfdf910e6eba07672e19bef9de184b48a03dc2f08021d90eb7d2accbc8f04.html"]http://www.adrive.com/public/265dfdf910e6eba07672e19bef9de184b48a03dc2f08021d90eb7d2accbc8f04.html
[/URL]

```
/usr/lib/jvm/java-6-sun/bin/java -jar WebcamStudio-test.jar
```

Send me the output here...

Thanks!

---

### Post by patrickballeux on 2008-11-15
Hi,

If you want to do that, then copy the folder "lib" under webcamstudio in your ~/webcamstudio folder, that's why you got that new error.  There are some libraries needed to the Jar to run.

That's why I wanted you to put that test Jar into the same folder as the other one. 

You should have ~/webcamstudio/lib which would contain /usr/lib/webcamstudio/lib

(or create a symlink)...

Let's try again! :)


> **buzzstray said:**
> WebcamStudio 0.33 is running well using Java 6.03 and without compiz.

I also have run WebcamStudio-test.jar with compiz disabled. And here is the error message:
```

Exception in thread "main" java.lang.NoClassDefFoundError: org/gstreamer/elements/RGBDataSink$Listener
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

I don't put all WebcamStudio files under "/usr" directory. I put those files under home directory $HOME/webcamstudio. So, I copied WebcamStudio-test in the same directory as WebcamStudio. Is it OK?

This is the command line:
```
java -jar $HOME/webcamstudio/WebcamStudio-test
```

I don't see "Pointer Size is 4" (or 8 ) in my terminal. The only things I see are those error message.

---

### Post by buzzstray on 2008-11-15
I have make some test on WebcamStudio-test. Under Java 6.03 and with compiz enabled this program runs without trouble. The only message showed-up is
```

Step 1
Step 4
Step 5
Step 6
Pointer Size: 4
Step 7
Step 8
Step 9
Step 10
Step 11

```

---

### Post by patrickballeux on 2008-11-15
That's good, but I wanted it to crash :)

What's does it do when you run the original one the same way?

Pat


> **buzzstray said:**
> I have make some test on WebcamStudio-test. Under Java 6.03 and with compiz enabled this program runs without trouble. The only message showed-up is
```

Step 1
Step 4
Step 5
Step 6
Pointer Size: 4
Step 7
Step 8
Step 9
Step 10
Step 11

```

---

### Post by buzzstray on 2008-11-15
Sorry, there's no error message in original one too. The only behaviour that is bothering me is couldn't hit the play button when the WebcamStudio was stopped, because the button turn to grey (not functioning). Is that malfunction or what? But, the others function are running well. Well done, I think you did it. You really have solved my problem. :)

> **patrickballeux said:**
> That's good, but I wanted it to crash :)

What's does it do when you run the original one the same way?

Pat

---

### Post by patrickballeux on 2008-11-16
Quite a mystery we have here :)

About not being able to stop the virtual webcam, I know about it.  It seems that if some data was not read from the "pipe" (/dev/video1), WebcamStudio is stuck until that data is read.  I need to find a solution, but you can:

1- Close Webcamstudio and restart it
2- Use camstrean to read or at least scan the devices and you will see WebcamStudio returning to a normal state.

For the original problem, did you updated since last time?  Have you changed something in your desktop?


Anyway, I'll keep an eye on this issue and keep the test version.  If it happens again, simply use the test version to find out what is happening.

Thanks for your support!

Have a nice day!

> **buzzstray said:**
> Sorry, there's no error message in original one too. The only behaviour that is bothering me is couldn't hit the play button when the WebcamStudio was stopped, because the button turn to grey (not functioning). Is that malfunction or what? But, the others function are running well. Well done, I think you did it. You really have solved my problem. :)

---

### Post by buzzstray on 2008-11-16
I didn't do so much update since the last time. But, here are some conclusion, that can be reported, came from my experience using WebcamStudio.

Version 0.32 cannot run on Gutsy Gibbon with compiz enabled. Unless, it's running under Java version 6.10. Running this program using Java version below 6.10, we will met a trouble related to sytray. In the contrary, using Java version 6.10 is save. If we want to run WebcamStudio 0.32, we should have disabled compiz.

The version 0.33 .tar.gz package has same condition as above. But, the version 0.33 .deb package is defferent. It can run under Java version below 6.10 and with compiz enabled.

That's it, I think. Thx.

---

### Post by patrickballeux on 2008-11-16
The tar.gz and debian are exactly the same for the Jar files and binaries.   I'll have a look to make sure that there is not something missing in the tar.gz.  Just in case.

Thanks for reporting.

Pat

---

### Post by patrickballeux on 2008-11-16
Version 0.34 is out!  Up! Up! Up!

---

### Post by buzzstray on 2008-11-17
Yihaaa! It's time to download now.

> **patrickballeux said:**
> Version 0.34 is out!  Up! Up! Up!

---

### Post by patrickballeux on 2008-11-22
v0.35 is out!  Up! Up! Up!

---

### Post by patrickballeux on 2008-11-23
For those living on the edge with Linux, a new version of the vloopback module (1.1.4) was released to improve the compatibility with the newest headers of the V4L2 libraries.

If 1.1.3 refuses to compile because you have the newest headers, get the 1.1.4, it should work (it is at the time of writing this).

Have fun!

---

### Post by patrickballeux on 2008-11-25
For those living on the edge (again!) with Linux, a new version of the vloopback module (1.1.5) was released to improve the compatibility with the newest headers of the V4L2 libraries.

If 1.1.3 refuses to compile because you have the newest headers, get the 1.1.5, it should work (it is at the time of writing this).


Have fun!

---

### Post by patrickballeux on 2008-12-01
Version 0.36 is out!  UP! UP! UP!

---

### Post by patrickballeux on 2008-12-10
Version 0.37 is not available!  Up! Up! Up!

---

### Post by ubunaut on 2008-12-16
the .deb is pretty easy to install, any chance of inclusion in a release or maybe a PPA?

this program is a total lifesaver, thanks!

---

### Post by patrickballeux on 2008-12-16
> **ubunaut said:**
> the .deb is pretty easy to install, any chance of inclusion in a release or maybe a PPA?

this program is a total lifesaver, thanks!


I looked at how to include in the PPA, but I think I will need assistance on this part...

Pat

---

### Post by patrickballeux on 2008-12-17
Version 0.38 is available! Let's chat!

---

### Post by HumanAnarchist on 2008-12-20
Hey man! 

Been a while since I've tried webcamstudio, and now that I've upgraded to latest version of Mint Linux I thought about giving it a try again, but now it won't work. No virtual webcam... 

I get this

```

workingnorm@smartypants: pts/1: 30 files 67Mb -> webcamstudio
Error loading device: video2
Error loading device capacity video2
Error loading device: video1
Error loading device capacity video1
Error loading device: video2
Error loading device capacity video2
Error loading device: video1
Error loading device capacity video1

```

from dmesg

```

[  255.245668] vloopback: Video4linux loopback driver v1.1.5
[  255.245796] vloopback: Loopback 0 registered, input: video2, output: video1

```

Tried to install the vloopback module both manualy, first and then with the installer... same problems... What to do? 

-ha-

---

### Post by patrickballeux on 2008-12-21
Hi HumanAnarchist,

Make sure that you have read/write access to the devices /dev/videoX.

Normally, you should add your user to the "video" group or execute that command each time you boot: sudo chmod 666 /dev/video*

To do a quick test, run WebcamStudio as root, if it works, then you simply don't have the access...  If it still does not work, then we have some investigation to do :)

Let me know!


> **HumanAnarchist said:**
> Hey man! 

Been a while since I've tried webcamstudio, and now that I've upgraded to latest version of Mint Linux I thought about giving it a try again, but now it won't work. No virtual webcam... 

I get this

```

workingnorm@smartypants: pts/1: 30 files 67Mb -> webcamstudio
Error loading device: video2
Error loading device capacity video2
Error loading device: video1
Error loading device capacity video1
Error loading device: video2
Error loading device capacity video2
Error loading device: video1
Error loading device capacity video1

```

from dmesg

```

[  255.245668] vloopback: Video4linux loopback driver v1.1.5
[  255.245796] vloopback: Loopback 0 registered, input: video2, output: video1

```

Tried to install the vloopback module both manualy, first and then with the installer... same problems... What to do? 

-ha-

---

### Post by cooldude on 2008-12-24
Very cool, cool program. Rock solid. Used on blogtv playing music videos. But had trouble co-hosting saying webcam was being used by another web page. But I don't think it was the program itself. I just finished broadcasting earlier, so maybe stuck with my blogtv broadcast page.. But running too many things at once will slow things up though. But not really the programs fault. Webcamstudio downloaded latest vloopback module & compiled it...very neat. Good job!

---

### Post by patrickballeux on 2009-01-07
New version: 0.39 is now available!

---

### Post by patrickballeux on 2009-01-17
Version 0.40 is now available!

    *  Y Scroll position for setup is now remembered
    * Chat IRC, if no IRC source is selected, when writing, 1st IRC source will be used instead of doing nothing
    * Default volume for Source is now at 15% instead of 100%
    * Complete new look and icons

---

### Post by patrickballeux on 2009-02-15
new version 0.41 is now available!

    * Fixed Mouse Scrolling on setup list
    * Added new feature: Triggering keywords to start and stop any sources
    * Fixed looping in playlist
    * Fixed the preference on showing the viewer or not
    * Fixed display on some slider not showing properly
    * Filtering of the vloopback output so it won't show up as a webcam
    * Added multiple selection of images in a single Image source, creating a slideshow

---

### Post by dixon on 2009-02-17
Still can't get it work with skype :( Any news on how to get it work with skype? It's the only application I use webcam with.

---

### Post by patrickballeux on 2009-02-18
> **dixon said:**
> Still can't get it work with skype :( Any news on how to get it work with skype? It's the only application I use webcam with.

Hi,

Skype compatibility is a little harder because I will have to play in the vloppback module to be able to have it right.  The problem is that Skype does not support RGB colorspace, which is quite easy to manipulate.  But that's something I hope to achieve one day.


Pat

---

### Post by patrickballeux on 2009-03-06
Version 0.42 is available!

---

### Post by Sepero on 2009-03-17
Hello Patrick, I appear unable to get the program to work properly.

I have no actual video camera available to my system.

The vloopback module appears to be loaded correctly.
```
root@EMONSTER:~# lsmod | grep vloopback
vloopback              20192  0
compat_ioctl32          9344  1 vloopback
videodev               41344  1 vloopback
```


Am am unable to perform step #3 of the "Quick Start" on this page:
[http://webcamstudio.wiki.sourceforge.net/User+Manual](http://webcamstudio.wiki.sourceforge.net/User+Manual)


Everything else in the program appears to work correctly, but because of step #3, it does not appear to be able to broadcast.

Here is a screenshot showing that I am unable to press the start button under "Virtual Webcam" tab.
[http://img25.imageshack.us/img25/9164/screenshotstj.png](http://img25.imageshack.us/img25/9164/screenshotstj.png)


In the screenshot, you can see that Desktop has been added and is currently being played in the "Preview" tab.

---

### Post by Sepero on 2009-03-17
Problem resolved. I was not in the group video.
```
$ groups
a adm dialout cdrom plugdev users fuse lpadmin admin sambashare
```

It now appears to be working great. I looking forward to enjoying it further.

Thank you

---

### Post by prar on 2009-04-28
Hi... 
webcamstudio

Ubuntu 8.10 (perfect)

Ubuntu 9.04 (dont work) why?

in alpha 6 update working ...
in clean instalation, dont work... libraries?

No device found - message

vloopback compile fron program package and manualy ... nada.

dont work. Help!

code source
prar@prar:~$ lsmod | grep vloopback
vloopback              22688  0 
compat_ioctl32         18304  1 vloopback
videodev               45184  2 vloopback,compat_ioctl32

---

### Post by patrickballeux on 2009-04-28
> **prar said:**
> Hi... 
webcamstudio

Ubuntu 8.10 (perfect)

Ubuntu 9.04 (dont work) why?

in alpha 6 update working ...
in clean instalation, dont work... libraries?

No device found - message

vloopback compile fron program package and manualy ... nada.

dont work. Help!

code source
prar@prar:~$ lsmod | grep vloopback
vloopback              22688  0 
compat_ioctl32         18304  1 vloopback
videodev               45184  2 vloopback,compat_ioctl32

Make sure that the group "video" is created and that you are part of it.  I just found out the same thing on my laptop.

1 - Create the groupe "video"
2 - Add all users to the video group
3 - Reboot the computer.

It should work as expected now.

Pat

---

### Post by ronniet on 2009-05-16
WebcamStudio is a great looking app, just the thing I'm looking to use with Ustream. But I've hit one problem:

I'm using WebcamStudio to stream a video file (from my PC) to Ustream. Channel viewers can see the video no problem, but get no audio.

Is there an easy way to fix this?

**Thanks!**
:KS

---

### Post by Sepero on 2009-05-18
> **ronniet said:**
> WebcamStudio is a great looking app, just the thing I'm looking to use with Ustream. But I've hit one problem:

I'm using WebcamStudio to stream a video file (from my PC) to Ustream. Channel viewers can see the video no problem, but get no audio.

Is there an easy way to fix this?

**Thanks!**
:KS

To my knowledge, webcamstudio does not handle audio at all, so the problem is probably with your audio setup. Do you get audio on Ustream when webcamstudio is not running?

---

### Post by ronniet on 2009-05-19
> **Sepero said:**
> To my knowledge, webcamstudio does not handle audio at all, so the problem is probably with your audio setup. Do you get audio on Ustream when webcamstudio is not running?

Yes, I can get audio on Ustream if I am watching a video, or if I used an actual webcam. It's just WebcamStudio that doesn't seem to be streaming the video sound, video is fine, just the sound is missing...  :(

---

### Post by mag1 on 2009-05-21
I got video sound working after reading and watching the video [here]("http://sourceforge.net/forum/message.php?msg_id=6396485") but my problem is now two things, i want to have the option to mute the sound i hear from the video preview but still have the sound play through the webcam stream.

The other problem which is more important is how come i get no npviewer.bin under recording tab in the pulse audio volume control panel?  it shows firefox and alsa so perhaps its different in jaunty, anyway regardless i get no sound from fifo, i don't understand why and been messing with it for hours, i hope someone can help!

Edit: Almost forgot to say thanks to Patrick for making such a great piece of software, nice work! :D

---

### Post by ubunaut on 2009-05-22
> **patrickballeux said:**
> Make sure that the group "video" is created and that you are part of it.  I just found out the same thing on my laptop.

1 - Create the groupe "video"
2 - Add all users to the video group
3 - Reboot the computer.

It should work as expected now.

Pat

that fixed the permission errors, thanks

---

### Post by ronniet on 2009-05-23
YAY! Finally got WCS broadcasting video, AND AUDIO, over Ustream, here's how I did it:

[http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/](http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/)

---

### Post by mag1 on 2009-05-31
I still can't seem to get the mic working even though i could get sound from video, this is through flash in firefox but is there another app i can test it through to see if its just a firefox/flash issue?

---

### Post by stwschool on 2009-05-31
Thank you very very much, I've been after this since I moved to linux, and even posted a thread a while back asking for this very thing. I love all these wonderful open-source developers. Doesn't it just make you all warm and fuzzy inside?

---

### Post by patrickballeux on 2009-06-01
New version 0.43 is available!

---

### Post by blackgr on 2009-06-02
is there going to be skype support soon?

---

### Post by mag1 on 2009-06-05
> **mag1 said:**
> I still can't seem to get the mic working even though i could get sound from video, this is through flash in firefox but is there another app i can test it through to see if its just a firefox/flash issue?

Anyone have any ideas at least?  It seems like it should be simple after looking around and just work, why am i getting no help after asking nicely? it's been weeks now. :(

---

### Post by ronniet on 2009-06-05
Have you looked through my tutorial at:
[http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/](http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/)

It deals with routing video sound through PulseAudio. Not sure if it'd help you any, but you never know...

---

### Post by mag1 on 2009-06-07
I seem to be doing everything right and it doesn't work, i can get audio from video to record through flash but if i try it with a mic using fifo i get nothing, the mic works fine on its own.

---

### Post by GloryFish on 2009-07-23
Hello. I'm using webcamstudio in Ubuntu 9.04 and it's working well. Thanks for putting it together.

I would like to be able to control which source is currently active remotely over the internet. What would be the best way to go about that? Is there anything currently in the project that would enable something like that?

---

### Post by GloryFish on 2009-07-24
Using the IRC/Keyword method described here:

[https://sourceforge.net/forum/forum.php?thread_id=3342295&forum_id=862127](https://sourceforge.net/forum/forum.php?thread_id=3342295&forum_id=862127)

is working out pretty well.

---

### Post by domonics on 2009-07-26
need help in installing or getting vloopback to work with webcamstudio. When i go to the virtual webcam tab, "no device found" is listed under output device hence i can't start the webcam.  

Here's my machine specs:
Intel P4 2.8
512 RAM
80G HDD
Ubuntu 9.04 running kernel 2.6.28-13

Now, i'm tring to build vloopback but i keep getting this:

```
:~/downloads/video studio/vloopback1.1.5$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/tomcat/downloads/video studio/vloopback1.1.5 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** No rule to make target `studio/vloopback1.1.5'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [all] Error 2
:~/downloads/video studio/vloopback1.1.5$
```

is it that this version of vloopback can't work with this kernel or what?? If it can please tell me how.

Also, when i run: lsmod | grep vloopback 
this is what i get:

```
vloopback              20192  0 
compat_ioctl32          9344  1 vloopback
videodev               41600  1 vloopback

```
does this means that it is installed and working??

your help would be greatly appreciated.

Thanks

---

### Post by travmon69 on 2009-08-18
looks like  this project is dead!!  app  dosent  even  work!

---

### Post by cooldude on 2009-08-22
I believe it is still being developed but on sourceforge. Can't find any documentation on it though.

---

### Post by sandyd on 2009-08-22
> **patrickballeux said:**
> I looked at how to include in the PPA, but I think I will need assistance on this part...

Pat

if you tell me ALL the dependencies into compiling the tar.gz, ill do it for you!
and i mean all. if a ubuntu system has nothing installed and it installs the dependencies, it should be compile-able and runable.

meanwhile, i shall start adding your deb to my personal non-launchpad ppa using rerepopro

done.

```

http://apt.dolphinaura.studenthotspot.net

```
package is named webcamstudio

EDIT: i take that back. theirs a problem with the deb package from sourceforge. fixing tomrow.

EDIT2: Fixed.

---

### Post by ctsdownloads on 2009-09-26
I have been in direct contact with the developer. Project docs were hosed thanks to Sourceforge redesign, but are backed up and coming back online soon as I can get them up.

Patrick is already working on the next version and we are going to begin rebuilding a community around the software on Google Code asap. It's coming, just be patient. ;)

I am going to be helping Pat out with the docs and website side of things, he will continue with the coding as his schedule allows.

In the meantime, here is a couple of older videos showing off some of the stuff that can be done.
[http://www.ustream.tv/channel/webcamstudio-for-gnulinux](http://www.ustream.tv/channel/webcamstudio-for-gnulinux)

Just remember, this is best served on dual-core Intel systems. Older PCs can use the app too, but newer dual-core systems run this software on Ubuntu 64bit like a rock star...no stuttering even with everything going. ;)

Thanks all. :guitar:

---

### Post by ctsdownloads on 2009-09-26
> **carlee said:**
> if you tell me ALL the dependencies into compiling the tar.gz, ill do it for you!
and i mean all. if a ubuntu system has nothing installed and it installs the dependencies, it should be compile-able and runable.

meanwhile, i shall start adding your deb to my personal non-launchpad ppa using rerepopro

done.

```

http://apt.dolphinaura.studenthotspot.net

```
package is named webcamstudio

EDIT: i take that back. theirs a problem with the deb package from sourceforge. fixing tomrow.

EDIT2: Fixed.

It would be awesome if you can maintain a repo for us as the new releases start pouring forth once again! :)

PM me here, I can get you my email addy so we can coordinate.

---

### Post by ctsdownloads on 2009-10-03
The new site is up, next version is just around the corner...with a simpler UI, too.

[http://www.ws4gl.org/](http://www.ws4gl.org/) :popcorn:

---

### Post by patrickballeux on 2009-12-12
Just updated the main article on this thread.

Keep looking for the new version coming soon: 0.53...

Enjoy!

Patrick

---

### Post by travmon69 on 2009-12-12
Awesome!  Great App!  Thanks for the  great work Patrick!

---

### Post by patrickballeux on 2009-12-12
Just looking at some stats:

* Webcamstudio For GNU/Linux 0.43 was dowloaded almost 3000 times from Sourceforge...
* At the time of posting this, version 0.52 was already downloaded more than a 1000 time
* Since the opening, the official website of WS4GL is visited by more thant 1500 unique visitors each month and it's still growing
* The first release of WS4GL (as a bash script) was done on August 26th 2008
* Total size of the source code, not including libraries is around 1.5 mb
* Total number of line codes of what I have written is 20668

Hope you enjoyed!

---

### Post by nortexoid on 2009-12-28
Is there no Karmic repo? Can Karmic users add the jaunty entry to their sources and install that way?

---

### Post by jSalv on 2009-12-28
I'm assuming it's in Java =D
Or is it not?

I'll have a go at it at some point...
Can it record the desktop in 720p?

---

### Post by patrickballeux on 2009-12-29
> **nortexoid said:**
> Is there no Karmic repo? Can Karmic users add the jaunty entry to their sources and install that way?

You can use the Jaunty repos.  It will work the same...

---

### Post by patrickballeux on 2009-12-29
> **jSalv said:**
> I'm assuming it's in Java =D
Or is it not?

I'll have a go at it at some point...
Can it record the desktop in 720p?

Yep, it's in Java ;)

As for recording in 720p, I'm working on it...

---

### Post by patrickballeux on 2009-12-29
For all fans of WebcamStudio For GNU/Linux, I have just created a group in Facebook.  Come join us!

---

### Post by patrickballeux on 2009-12-30
Some news about WS4GL development...

The next release will be 0.53, with a lot of new features in it.  If you follow me on Twitter, you probably know about those already...

* Giss.tv native support: Actually, you can broadcast to any icecast2 server
* FME (2.5) support.  For now, broadcasting works with Bambuser and Justin.tv.  No luck with UStream as they use FME 3.0
* Source Browser was added.  Will make it easier to pick any image/movie from your library
* New sources preview 
* As new of today, a new source will be available: Widgets.  More info to come...

And as usual, bug fixes, minor improvement and so on...

Hope you have fun with WS4GL!

:guitar:

---

### Post by sandyd on 2010-01-10
And its released
sorry, but youll have to wait until tomorow for a repo update.
my computer just died on me. ( ->kde 4.4 beta<- )
--------------

EDIT: repo updated and ready to go.
EDIT2: and sorry about the flop. there was a bad line in the deb file causing it to become uninstallable

---

### Post by KanineN on 2010-04-05
How do I stream a movie with it? when I choose a .wmv movie the little square is gray and and I can't press the play button..

---

### Post by sombrancelha on 2010-09-24
This [post]("http://www.ws4gl.org/news-flash-/anewv4l2loopbackdriverskypeandcheesecompatibility"), from the official website, talks about compatibility with Skype. However, it wasn't clear to me if this feature is already available. I tried with no success. If it is, how to do it?

On a side note, I couldn't find the wiki mentioned on the first post...

Thanks

---

### Post by patrickballeux on 2010-09-24
Hi,

The compatibility is in the DEV, and will be part of the next release 0.57.  So 0.56 is not compatible with Skype.  

Keep looking for the next release.

Pat


> **sombrancelha said:**
> This [post]("http://www.ws4gl.org/news-flash-/anewv4l2loopbackdriverskypeandcheesecompatibility"), from the official website, talks about compatibility with Skype. However, it wasn't clear to me if this feature is already available. I tried with no success. If it is, how to do it?

On a side note, I couldn't find the wiki mentioned on the first post...

Thanks

---

### Post by lonegroover on 2010-09-25
> **KanineN said:**
> How do I stream a movie with it? when I choose a .wmv movie the little square is gray and and I can't press the play button..

I think you need to install vloopback. Would be interested to know if there's a "fake webcam" how-to somewhere now that AVLD no longer compiles (under 10.4).

Thanks for any help ..

---

### Post by 0N3 on 2010-09-29
Would be nice to have a minimise to system tray option or mimise to indicator applet!! But overall fantastic software one of my favourite Linux apps

---

### Post by lonegroover on 2010-10-01
> **lonegroover said:**
> I think you need to install vloopback. Would be interested to know if there's a "fake webcam" how-to somewhere now that AVLD no longer compiles (under 10.4).

Thanks for any help ..

No-one seems to know; I guess it's quite hard to do using WebcamStudio. A shame that AVLD is no longer an option; that was a very useful piece of software.

---

### Post by ctsdownloads on 2010-10-02
> **lonegroover said:**
> No-one seems to know; I guess it's quite hard to do using WebcamStudio. A shame that AVLD is no longer an option; that was a very useful piece of software.

Actually, it's rather easy in v0.56. I have tested this with avi and other video rips that all work out of the box.

As for WMV files, again tested it with [this file]("http://www.archive.org/details/WorkToFishtestwmv") by downloading it and testing it as follows.

1) Source> Movie>
2) pull down to "all files"
3) browse to wmv downloaded. test_wmv.wmv
4) click open
5) Under controls tab, hit the > play/pause button.
6) Preview it by using Show preview.

---

### Post by ilanesh on 2010-10-06
Hi, I have tried it, and need to use it with my webcam, but I can not find any option on it for webcams in sources, I have seen it on others but not on mine. Can anyone help me -please? I click on "sources" and there is only ,
desktop, dv, image, free text, irc, animation, movie, youtube, movie stream, movie viewer, playlist, and widget. But where is: "webcams"?
It is missing. So I can`t choose it. I need it for video on flash webpage. :confused:

---

### Post by ctsdownloads on 2010-10-06
> **ilanesh said:**
> Hi, I have tried it, and need to use it with my webcam, but I can not find any option on it for webcams in sources, I have seen it on others but not on mine. Can anyone help me -please? I click on "sources" and there is only ,
desktop, dv, image, free text, irc, animation, movie, youtube, movie stream, movie viewer, playlist, and widget. But where is: "webcams"?
It is missing. So I can`t choose it. I need it for video on flash webpage. :confused:

Just FYI, anytime you post to forums for any OS, best to provide specifics on stuff like webcams. Otherwise, I have no idea if your webcam is compatible or not. ;)

Assuming its something like a Logitech cam, see the attached images in the following order.

1) start.png (On the left side, pull the vertical bar out so you can see the sources list. Click on devices to expand, select webcam...assuming its compatible)

2) double-click.png (Once your cam is selected, double click it to make the screen appear like this. Then click the universal symbol for play. |> )

3) viewer.png (Assuming your going to need to see if the camera is working, Output>Show Preview will be the next thing to do.

For help with Ustream (when it's not down like today), go here.
[http://www.ws4gl.org/download/installing-on-ubuntu](http://www.ws4gl.org/download/installing-on-ubuntu)

Remember that your Flash camera source is vloopback, NOT the webcam when at the ustream streamer. Browser must be closed when starting and setting up WebcamStudio. Start browser only after step three above.

---

### Post by lonegroover on 2010-10-17
> **ctsdownloads said:**
> Actually, it's rather easy in v0.56. I have tested this with avi and other video rips that all work out of the box.

As for WMV files, again tested it with [this file]("http://www.archive.org/details/WorkToFishtestwmv") by downloading it and testing it as follows.

1) Source> Movie>
2) pull down to "all files"
3) browse to wmv downloaded. test_wmv.wmv
4) click open
5) Under controls tab, hit the > play/pause button.
6) Preview it by using Show preview.

That's useful - thanks! Worked perfectly with the test wmv, unfortunately WebcamStudio crashed when I tried it with an MPEG. Still - promising.

---

### Post by ctsdownloads on 2010-10-17
> **lonegroover said:**
> That's useful - thanks! Worked perfectly with the test wmv, unfortunately WebcamStudio crashed when I tried it with an MPEG. Still - promising.

Should work with most any popular media container. Crashing indicates something with how the media was encoded that WebcamStudio didn't like. Running WebcamStudio in a terminal would give you some insight as to what happened when the MPEG crashes the software I bet.

---

### Post by lonegroover on 2010-10-18
Thanks. The following invocation of mencoder has been used to encode the files I use for 'fake webcam' purposes:

(eg)

```

mencoder -nosound inputfile.wmv -ofps 15 -o filename.mpg \
            -ovc lavc -vf pp=de,scale=320:240 \
            -lavcopts vcodec=mpeg2video -of mpeg 


```

So MPEG2 video, no audio, 15 fps. It doesn't actually "crash" WebcamStudio in that sense; it just makes it freeze, so that it has to be ctrl-c-ed.

---

