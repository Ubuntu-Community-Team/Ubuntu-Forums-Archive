---
title: "In Development: YAPSY"
date: 2008-02-02
forum: Ubuntu Brainstorm
---

### Post by allquixotic on 2008-02-02
Here is an idea write-up for an app that is currently in development. I have a proof of concept but it needs more refinement before I'm ready to embarrass myself with a public release ;) I apologize in advance for the long post, but I had to get out all these ideas, and set the stage for receiving feedback from users and developers alike.

**The Concept**: Yet Another Pitch/Speed (Y)utility [sic]. The idea is to leverage the existing GStreamer "pitch" plugin, which is itself based on the excellent [SoundTouch](http://www.surina.net/soundtouch) pitch-speed library, into a new GUI. The GUI will be functionally equivalent to the Winamp plugin [PaceMaker](http://www.surina.net/pacemaker/). As far as I know, there is no current SoundTouch GUI integrated into a media player for Linux/BSD. The advantages of such a plugin are given exactly on the PaceMaker webpage, above. YAPSY will enable GNU/Linux media players that use GStreamer to take advantage of SoundTouch functionality, allowing users to hear their music in a new light, or speed up / slow it down for the purposes of karaoke or guitar practice.

**Planned Project Features for Version 1.0:**:
1. Support all GStreamer applications that use GConf to build their audio pipeline; namely, by querying the properties /system/gstreamer/0.10/default/ (audiosink, chataudiosink, musicaudiosink). Examples: Rhythmbox, Songbird, Banshee. Exaile is unfortunately a counterexample, as it can be told to bypass GConf.

2. **Non-Real Time** pitch, tempo, and speed shifting, by leveraging the "pitch" gstreamer plugin. This plugin is in gstreamer-plugins-bad. "pitch" is not actually bad quality at all; I am not sure why it is still in gstreamer-plugins-bad. It is extremely stable and feature-rich.

3. 100% Free and Open Source Software, including dependencies.

4. Support Ubuntu out of the box as the project's "showcase" distro. The project will be actively maintained (by me) to be integrated into Ubuntu, and repackaged as required. Source will be provided in a tarball for other distros, and unsupported.

5. Support for "remembering" the last pitch/tempo/speed settings.

6. Support for using a non-standard partial pipeline chained to the "pitch" plugin and supporting plugins. 

7. Support for all input pipelines supported by your GStreamer codecs. In other words, there will be no limits on file format, source of input data, etc.

8. Individual control over each GConf category of playback: music, chat, and generic "audiosink". This will allow you to listen to pitch-shifted music without having e.g. Ekiga Smartphone change the pitch of your mother's voice as she speaks to you :)

9. Only use dependencies that are already in Ubuntu repos -- either main or universe.

**Implementation Details** -- plans for technically-oriented items above, in order.
1. I have created a very simple shell script that accomplishes this in the CLI, and the GConf APIs are simple enough to do this programmatically. You can find the shell script [here](http://tiyukquellmalz.org/gst-pitch.sh). If you want to know if your favorite media player will support this program before it's released, download this script and run it with the --help option, then proceed from there. Example: ./gst-pitch.sh -p 1.2 -t 1.2 would play back all GStreamer effects at 120% tempo and 120% pitch.

The YAPSY pipeline consists of audioconvert, then the pitch plugin, then audioconvert again, then audioresample. The audioresample is MANDATORY for osssink, but is needless excess processing for e.g. pulsesink. I can solve this problem by adding a checkbox for "resample", or by trying all shipped output plugins and seeing if they need to be resampled. By "need" I mean, if the audioresample isn't included and your backend is osssink, you get horrible, deafening static! I don't want any user to experience this, ever, while using my software. The safest route would be to forcibly enable it, but then again, audiophiles might notice a quality decrease when it's needlessly enabled.

2. Without modifying the "pitch" plugin itself, I can't make the pitch and tempo change in real-time. Currently, when a new stream is initialized, well-behaved media players (such as RhythmBox) will read the GConf entry again, and any updates will be reflected upon track change. No player restarts are required unless the client app doesn't re-read the GConf entry.

3. This is relatively easy; of course I can't stop people from using proprietary Gstreamer plugins for decoding, but that's neither here nor there. I don't touch the input or decoding phases of the pipeline.

4. My implementation language is Java. The program will be built via gcj into an ahead-of-time compiled app. I will make this app appear like it's written in native C by using the java-gnome bindings for a GTK gui, and GConf support. A performance difference for this small app will only be noticeable on computers that don't meet the Ubuntu minimum system requirements. Typical criticisms of Java are thus mitigated; a few widgets drawn natively in GTK won't make a significant difference to desktop performance. After all, the lifetime of this application is about the same as the Preferences -> Sound app: you start it up, change a few things, and close it. Memory bloat or GUI responsiveness are minimized by the planned scope of this project, and the average runtime of a program instance.

I have built several Debian packages before, but I might need some guidance if Ubuntu has special requirements.

5. This is accomplished by design. The current plan is to leave the GConf keys alone, once the user sets them, until they change them again. Depending on how testing goes, we might be able to use the CLI script above (or, alternately, a script that entirely removes the "pitch" plugin from the pipeline) to remove pitch/speed settings when the user logs in.

6. When YAPSY is first initialized, it will read the current values of the audio GConf defaults and store them away in a YASPY GConf key. The GUI will have a place for the user to change the pipeline after install-time, and dpkg-reconfigure should read the current pipeline and stuff it away also. Each time the pipeline is modified, the user's custom pipeline will be tacked on the end of the YAPSY pipeline.

7. This is by design.

8. I am planning a three-item, multiselect listbox to select which output types you want the settings to apply to. With a bit of careful design, I should be able to allow *different* pitch/tempo settings for each output type (generic, chat, music), without adding to the GUI complexity.

9. That's easy: building the app will require libgtk-java-dev, libgconf-java-dev, libglade-java-dev, and the standard GCJ distribution; running the app will require the equivalent runtime versions of these packages, along with gstreamer-plugins-bad (note: **NOT** gstreamer-plugins-ugly!)

**Requests from the Ubuntu Community**:
1. Users: Feedback on this concept is welcome. I will have UI screenshots posted to this thread as soon as they are respectable and contain all the features mentioned above. I want to get the UI solidified early in the design process.

2. Developers: Feedback on the concept is welcome from a technical perspective. Advice on how to press things through the Ubuntu package selection process is welcome. I am planning to comply as much as possible with established Ubuntu, Freedesktop and GNOME standards.

3. Everyone: Comments on whether or not this would be useful are welcome! Furthermore, I'd like to know if this has already been done. This project has the advantage that a handful of media players will be simultaneously enabled; however, I would appreciate any links to pre-existing GUIs for changing the speed/pitch/tempo of music on BSD/Linux. I Googled for this extensively before starting this project.

**Project Status**:
I've started implementation. Right now, the GUI only consists of two sliders that change all three of your GConf default audio keys when they are moved. Most of the commodity features listed above are not implemented. Code is sloppier than I'd like it to be.

**Development Methodology and Schedule**: I plan to have it officially supported in Ubuntu 8.10 **definitely**, if not Hardy. I have a feeling the support for Hardy will be unofficial, due to the early stage of development and the quickly-approaching Hardy deadlines. I also plan a Gutsy backport. Feisty and prior will not be supported by me.

I use SVN; version 0.1 of the development snapshot will be pushed to a new SVN repository on my website, tiyukquellmalz.org.

version 0.1 should be released in February, barring any catastrophes ;)

**License**: Tentatively, LGPL v2. I'm open to other license suggestions, though I will not entertain a BSD license.

Thanks,

Sean McNamara

EDIT: I suppose you all might want to know a bit about me as well, before you give me so much as half a vote of confidence ;)

I'm a senior Computer Science major at University of Maryland, College Park. I have tons of experience with sound processing, Java, and GUIs, so this seemed like a perfect cross-section app for me to work on. I am a long-term Ubuntu user, and also somewhat of a distro connoisseur; I have used Fedora, OpenSUSE, Linspire, and Gentoo for non-trivial lengths of time. Each time, I ended up coming back to Ubuntu for the long haul.

 I have used GTK in C, and the Java wrappers are even simpler to use. I selected Java as my platform because I am more confident about my code quality in Java than C. I didn't want to try bringing in SWT or Swing for performance, dependencies, and domain and GUI uniformity reasons. This app is already deeply entrenched in the GNOME and GStreamer world, so it made little sense to code the GUI in anything other than GTK.

Thanks again!

---

### Post by Fufkin on 2008-05-10
Even though this is kind of old I hope you are still working on it.

I have been searching for a 'Pacemaker' Linux equivalent ever since I transferred to Ubuntu but have had no luck at all.  

It's the only thing that sometimes makes me regret leaving Windows :(

Please finish this project :)

---

### Post by LevTermen on 2008-05-13
There is one cross-platform application using SoundTouch: Mixxx.
[http://www.mixxx.org]("http://www.mixxx.org")

Its pitch-independent time-stretching implementation doesn't sound convincing, AFAIK on my system the sound flow gets bursty, even with higher latency settings. Too CPU intensive maybe. The resampling mode closer to digital DJ's practises works seamlessly.

[Rubber Band]("http://breakfastquay.com/rubberband/"), another audio time-stretching and pitch-shifting library, has been considered as a replacement:
[Re: [Mixxx-devel] [Fwd: Re: Rubberband and Multithreading]]("http://sourceforge.net/mailarchive/forum.php?thread_name=1208958800.25368.6.camel%40Jupiter.home&forum_name=mixxx-devel").

I like your "application-independent" concept. Provided the playback of all running applications relying on GStreamer would be affected by the pitch/speed/tempo parameters, your GUI could as well be designed as an applet, like the volume control applet located on desktop environments taskbars that acts as a master volume (for egs. the one from the [gmome-media]("http://ronald.bitfreak.net/gnome-media.php") package).

To me the real-time feature is very important. In order to achieve that, would the modifications of the pitch plugin be difficult? 

Another feature would be great for interaction, the ability to change the playback direction, but I guess this wouldn't be possible using the GStreamer pipeline you described, one plugin of the pipeline accessing the playback controls of another plugin, unless all media players implement reversed playback at first, right?

BTW, the name is already taken:
[http://yapsy.sourceforge.net/]("http://yapsy.sourceforge.net/")

---

### Post by LevTermen on 2008-09-27
Looks like it's happening...

[LIST=1]
[*]ScaleTempo for GStreamer using custom code for time-scaling:
[http://scaletempo.sourceforge.net]("http://scaletempo.sourceforge.net")
[http://sourceforge.net/projects/scaletempo/]("http://sourceforge.net/projects/scaletempo/")

You can already try a GTK demo player using GStreamer: download packages gst-scaletempo and gst-scaletempo-demo, compile (./configure; make) both in the given order, launch the demo with the following command (assuming your current dir is where the second package files have been extracted):
```
$ ./src/scaletempo-demo --gst-plugin-load=../gst-scaletempo-r1/src/.libs/libgstscaletempoplugin.so
```

[*]ScaleTempo plugin for Rhythmbox using SoundTouch:
[http://willem.engen.nl/projects/musictools/]("http://willem.engen.nl/projects/musictools/")

As mentioned on the page, you just need to extract the package, install it on your user Rhythmbox plugin dir and activate the plugin.
[/LIST]

The demo of the first should have been implemented with sliders rather than spin buttons for a smoother control. A certain delay can be perceived while changing parameters on the second.

---

