---
title: "An Open Letter to Ubuntu Developers"
date: 2010-09-06
forum: The Cafe
---

### Post by amauk on 2010-09-06
I've just posted this to the ubuntu-devel-discuss mailing list, but would be interested in other people's thoughts too.

--------------

An Open Letter to Ubuntu Developers
(apologies for the length)

First of all, I would like to thank all that participate in Free Software.
I could write for days about how I appreciate individual upstream projects and the work done by various distributions, but for brevity I'm lumping all this into one big thank you.

This is not meant to be a series of rants, please do not take it as such.
I am hoping this will come across as a comprehensive series of observations of desktop Linux usage, from a long-time (and I like to think, competent) Linux user / sysadmin.

I am targeting this at the developers of Ubuntu.
I could have broken this down and targeted specific upstreams, but for better or worse, I believe Ubuntu is gaining serious mainstream traction on the desktop, and I think this will reach more people and have more impact if I target Ubuntu specifically.
Having said that, none of this letter is intended to be Ubuntu specific, instead being applicable across distros and upstream projects.


1) Applications, and their dependence on desktop environment libraries

Currently certain application rely on specific desktop environment libraries to operate.

As examples, if you install kate on stock Ubuntu 10.04, you pull in 108 packages, totalling 330Mb

```
        akonadi-server exiv2 gdebi-kde icoutils install-package kate
        kdebase-runtime
        kdebase-runtime-data kdebase-workspace-bin
        kdebase-workspace-data
        kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs5
        kdelibs5-data
        kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo kpackagekit
        ksysguardd
        kubuntu-debug-installer libakonadiprivate1 libattica0 libaudio2
        libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2
        libexiv2-6
        libiodbc2 libkephal4 libkfontinst4 libkscreensaver5 libksgrd4
        libkworkspace4
        libmng1 libmodplug0c2 libmpcdec3 libmysqlclient16
        libpackagekit-glib2-12
        libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4
        libplasma-geolocation-interface4 libplasma3 libplasmaclock4
        libplasmagenericshell4 libpolkit-qt-1-0 libprocesscore4
        libprocessui4
        libqca2 libqimageblitz4 libqt4-assistant libqt4-dbus
        libqt4-designer
        libqt4-help libqt4-network libqt4-opengl libqt4-qt3support
        libqt4-script
        libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg
        libqt4-test
        libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
        libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4
        libstreamanalyzer0 libstreams0 libtaskmanager4 libweather-ion4
        libxcb-shape0
        libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
        libxine1-misc-plugins libxine1-x mysql-client-core-5.1
        mysql-common
        mysql-server-core-5.1 oxygen-icon-theme packagekit
        packagekit-backend-apt
        phonon phonon-backend-xine plasma-dataengines-workspace
        plasma-scriptengine-javascript plasma-widgets-workspace
        polkit-kde-1
        python-kde4 python-packagekit python-qt4 python-sip
        shared-desktop-ontologies software-properties-kde soprano-daemon
        ttf-dejavu
        ttf-dejavu-extra update-manager-kde virtuoso-nepomuk
```


By contrast, if you install gedit on stock Kubuntu 10.04, you pull in 62 packages, totalling 72Mb

```
        esound-clients esound-common gamin gedit gedit-common
        gnome-mime-data gvfs
        gvfs-backends indicator-application launchpad-integration
        libappindicator0
        libart-2.0-2 libaudiofile0 libavahi-glib1 libbonobo2-0
        libbonobo2-common
        libbonoboui2-0 libbonoboui2-common libcdio-cdda0
        libcdio-paranoia0 libcdio10
        libdbusmenu-gtk1 libesd0 libgail18 libgamin0 libgdu0 libgnome2-0
        libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common
        libgnomeui-0
        libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
        libgtksourceview2.0-0
        libgtksourceview2.0-common libgvfscommon0 libindicator0
        libjson-glib-1.0-0
        liblaunchpad-integration1 libnotify1 libproxy0 libsexy2
        libsoup-gnome2.4-1
        libsoup2.4-1 libstartup-notification0 libwnck-common libwnck22
        libxcb-atom1
        libxcb-aux0 libxcb-event1 libxres1 notification-daemon
        policykit-1-gnome
        python-cairo python-gconf python-gnome2 python-gnomecanvas
        python-gtk2
        python-gtksourceview2 python-pyorbit zenity
```

Note the requirement for MySQL client libs when installing kate on Ubuntu, and the requirement for Esound when installing gedit on Kubuntu.
These are obviously needed for some DE libraries, and (you'd hope) should not impact the functionality of a simple GUI text editor.

I understand the fact that desktop environments provide a multitude of services / functionality, including being platforms on which other applications can be built.
But surely it's desirable (and possible) for apps to be DE agnostic, and depend on plumbing libraries that are common (and shared) across DE's.

There must be a way for the plumbing elements of today's DE's to be shared, and for the look & feel of a GUI app to be nothing more than a very thin wrapper over a standard base.
I've never seen the logic in tying applications to specific DE libraries.

Please do not think I'd trying to advocate the need for a single desktop environment (far from it)
I like the choices that are available, and believe it sparks competition and innovation.
but do one thing, and do it well, and currently desktop environments seem to do a whole host of generic tasks, using their own bespoke libraries, that could be split out into cross-environment libraries.

It's not like this is uncharted territory, either
There's a few examples of protocols / APIs that cater for new features / abilities in specific implementations
OpenGL being one
Would it not be possible for all DE's to adhere to a standard protocol
Then, for example, if KDE 5, or Gnome 3.7 introduce a new concept, this can be dealt with by an extension to the protocol
If the new concept is picked up by other DE's, then it can be written into the core protocol


2) Everything's a file

This Unix philosophy seems to have been forgotten in many of today's applications / userland servers

Wouldn't it be wonderful if the sound being output to the systems soundcard(s) or individual apps were available via a file
Completely independent of whatever sound system (ALSA, OSS, OpenAL) or sound server (PulseAudio, Jack) happens to be in use

        cat /dev/snd/stereo_out1 > ~/speaker_output.wav
        cat /dev/snd/pid_1234 > ~/app_output.wav

rather than the various custom and bespoke recording programs / shell scripts that are needed currently

Also with capturing screencast videos
(ignoring arguments about codecs / containers)

        cat /dev/display/xscreen1 > ~/desktop_screencast.ogm
        cat /dev/display/pid_1234 > ~/app_screencast.ogm

Taking this one step further, if all AV produced by apps are available via files, I think the process of combining various AV streams would be
greatly simplified.

Pipe the video stream from your screenA into a multiplexer
Cat audio streams from appX and appY into a mixer, and pipe combined
audio into the multiplexer
Redirect multiplexer output to a file

Don't think of the above as the typical user-facing way of doing things
More a standard framework for writing GUI apps to achieve such tasks.
I think this would greatly simplify, standardise, and enhance such GUI helper apps for manipulating AV on a desktop machine, as all AV is dealt with in a standard (and simple) way, and again, it would be sound system and sound server agnostic.


3) Link GUI & CLI operations using common syntax

I'm in two minds about including this,
as this is not a usual use-case for the majority of people but I'd love for all GUI applications to be invokable via the CLI, using some standard syntax
I've found that often times I'll use a GUI app to perform some set of operations, then I'm wanting to perform the same operations across multiple files, and currently I'm forced to find alternative apps of automating said operations

Eg. I've recently needed to perform the following operations on several hundred photos in order for them to blend in with a user-configurable webpage colour scheme
(Making an image whose background gradually fades to transparent at the image boundaries)
- Open image in the Gimp
- add a transparent layer
- Select all
- Shrink selection by 5px
- Feather selection by 5px
- Invert selection
- Clear selection (to transparent)
- Save as a PNG

Surely it should be possible to automate such GUI operations using a CLI interface and if you've got experience with a specific desktop app, I think it would be hugely beneficial if you could keep using the same program both on the GUI and on the CLI

```
        for IMG_FILE in $IMG_FILES; do
                gimp-cli --process="layer-add:transparent;select-all;select-shrink:5px;select-feather:5px;select-invert;select-clear;file-save:${IMG_FILE}.png" $IMG_FILE
        done
```

I can think of a few examples of complex GUI operations that would benefit from easy CLI automation
If some sort of standard syntax could be developed to automate operations via a CLI interface, I'd die happy

And (this may be a little too ambitious, but just suppose) if the syntax of these CLI operations could be sufficiently generalised across all GUI applications, you could, given an arbitrary CLI command, spit back out a simple bullet point set of GUI instructions for users to follow.
CLI is universally English, GUI is not.
This may be beneficial to documentation writers and translators
Write one command, and ask it to output GUI instructions in x number of languages but that's probably not very do-able, I admit.


Anyway, if you got this far, then thanks for reading.
As I said at the start, this is just a collection of things I think (from my POV) could be done to improve the overall experience that is Linux.

---

### Post by neoargon on 2010-09-06
If I am not mistaken , Ubuntu can do nothing about the issues . Despite being a  popular distribution, they contribute a very small amount of code to the upstream . So , they have little influence .

---

### Post by del_diablo on 2010-09-06
neoargon: So what? They can attempt to upstream, and get **** done.
Ubuntu is too large to be ignored, sadly.

---

### Post by Austin25 on 2010-09-06
I agree completely.

---

### Post by gradinaruvasile on 2010-09-06
Dude, this is not for the Ubuntu developers, it is for Linux.

Ubuntu does little actual development, they take the stuff from Debian, apply some patches here and there, change the wrapping and thats it.

---

### Post by amauk on 2010-09-06
Canonical employs a number of FOSS & linux software veterans
Shuttleworth himself was the Debian maintainer of Apache for 10 years

I'm not a blogger seeking a suitably inflammatory headline to increase hits
so, I'd appreciate it if this didn't get derailed into a blog-comment-esque flame over contributions

---

### Post by TNT1 on 2010-09-06
> **amauk said:**
> 

As examples, if you install kate on stock Ubuntu 10.04, 


As an example, be grateful that Linux offers you choices like this. 

If it doesn't work for you, don't use it, if it does, and you want to change certain parts of it, go ahead. I think you are going about this the wrong way.

Good luck anyway.

---

### Post by toupeiro on 2010-09-06
my perspective answers to the OP's statements:

1)  If you install **k**ate on **U**buntu 10.04,  either through the Software center, or if you used aptitude show kate, It's going to tell you which DE its designed for before you install it.

```
$ aptitude show kate
Package: kate
State: not installed
Version: 4:4.4.5-0ubuntu1~lucid1~ppa1
Priority: optional
Section: editors
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 3,961k
Depends: kdebase-runtime (>= 4:4.4.3), kdelibs5 (>= 4:4.4.5), libc6 (>= 2.4),
         libplasma3, libqt4-dbus (>= 4:4.5.3), libqt4-qt3support (>= 4:4.5.3),
         libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.6.1), libqtgui4 (>=
         4:4.6.1), libstdc++6 (>= 4.4.0)
Suggests: aspell | ispell | hspell, khelpcenter4, konsole
Conflicts: kate-kde4
Replaces: kate-kde4
Description: KDE 4 Advanced Text Editor
 Kate is a powerful text editor that can open multiple files simultaneously. 
 
 With a built-in terminal, syntax highlighting, and tabbed sidebar, it performs
 as a lightweight but capable development environment.  Kate's many tools,
 plugins, and scripts make it highly customizable. 
 
 Kate's features include: 
 
 * Multiple saved sessions, each with numerous files * Scriptable syntax
 highlighting, indentation, and code-folding * Configurable templates and text
 snippets * Symbol viewers for C, C++, and Python * XML completion and
 validation 
 
 This package is part of the KDE 4 Software Development Kit module.

```

There are other applications which do what kate does that were designed for the Gnome DE and therefore most if not all of its libraries would be satisfied by the fact that the DE is installed and in use.  

Linux gives you the variety to run an application designed for one specific DE in a different DE than it was designed to, but it still has to satisfy that applications requirements.  This was ... MUCH HARDER ... to do not so many years ago really.  Whats important, in my opionion, is to know what you are using, and know what you are installing.  If you're running ubuntu, and something is asking you to use kate, use Gedit instead, if you don't want kate and all its libraries on your system.  Linux empowers us with options, use them. :)

2)  I hear what you are saying here, but what you are also saying is, be prepared to buy a cache drive just to play sound!

If I am having a party, and want to put my library on shuffle and record the music I've been playing at the party, my hard drive space is toast, especially in raw formats like wav.  So now, to save space, you are getting into the filetype wars of lossy versus lossless, and you're also getting into situations where you're looking at a custom app who can determine encoding by file extension.  (Cat, by the way, could never do this. Cat read's a file or list of files to STDOUT which you can pipe back to STDIN.  Analog audio is not STDOUT, and anything behind /dev is merely a device file.  Cat could likely not read the product of a device file in this way, even it it was STDOUT.  For example, I can't grab the file contentsout of /dev/sdb1 by catting it. :) )  Maybe it's a bad example of usage, but you get the idea.  This method offers no inline control over what you are recording.  If you would need to use an application outside of this function to complete your work, are you really solving the issue you're outlining?  

Pulseaudio gives you the ability to use internal-stereo as your input device, then all you have to do is enable it when you want something recorded.  Other sound servers do this as well.  It's on-demand, and very easy to do.  I could agree with the argument that you would want a way to do this at the command line, and I'm sure there is one.  It may just take a little research to identify.  Which comes to my next point, knowing what the right tool is for the job.

3)  To resoundingly echo some points in answer number 1, linux empowers us with options, use them. :) 

Linux, philosophically,is in great part about using the right tool for the job.  If a mechanic, or a general contractor, or electrician, or really any trade you can think of, were to go into their toolchest, would they have one big tool that claims it can do lots of things, or would they have sets of tools that scaled based on the size of the job they are needing to take on, which will change varying on the situation.  I've used this analogy before.  Say your one tool was a very well made craftsman screw driver or more appropriately a Swiss army knife, and your job was to drive screws through stone.  I am pretty sure you'd be wishing you had a toolchest with tools to scale for the job you are wanting to complete.  The same logic is reversable.  Lets say you have a huge electric jack hammer, and all you are wanting to do is break the rest of a 4"x4" cracked ceramic tile off the floor.  Overkill much?  Well, all this applies to computing as well.

There may be times when I want to do small operations, and I want to do them fast and clean.  There may also be times when I need to make sure I'm fully threading on all available cores, and using every percentage of my bandwidth thats available to do things, and I need tools that can scale to that degree.  I think it begins to stifle innovation when you start limiting your options for the sole sake of ones comfort zone.  There's definitely value for some of what you are saying, don't get me wrong.  Especially, in your use of a gimp-CLI.  However, things like that are not linux problems.  Gimp, which you used in your example so I will do the same, is merely a software application that happens to be GPL'ed.  It runs on linux and windows.  It's in the hands of the application developers (regardless of platform) to build in that functionality.  However, a better approach than trying to plead with developers to see things your way is to look for a tool thats already doing the same thing, or similar.  Just because gimp, a very versatile, free graphical application doesn't do it, doesn't mean nobody else has. :)  What improves the overall experience in linux is the repository based systems and software indexing and searching that allows you to search all of this natively, with full descriptions and even screnshots in many cases of what the software looks like.  Linux empowers you with choices, makes it very easy to find them, and almost always charges you nothing to use them.  Maybe the issue is not that linux needs more one-stop applications and frameworks, maybe its users who are just used to proprietary software companies telling them they have one stop applications and frameworks.  Sometimes they do, and sometimes they don't.  However, if somebody elects to switch to a linux operating system, then it would behove them to also change their thinking a bit as well to get the most out of their decision to switch.

Apologies for the wall of text, but thanks for the thought-provoking post!

cheers!

-T.

---

