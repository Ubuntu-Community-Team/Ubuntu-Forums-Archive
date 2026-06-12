---
title: "New release: Mupen64Plus v1.99.1"
date: 2009-12-15
forum: The Cafe
---

### Post by argor on 2009-12-15
from Richard42  at [New release: Mupen64Plus v1.99.1 - EmuTalk.net](http://www.emutalk.net/showthread.php?t=50098)
> **Richard42 said:**
> Hello N64 fans! Just in time for a new decade, we are releasing the first beta (christened 1.99.1) of the forthcoming and long-awaited Mupen64Plus 2.0.  This release is revolutionary, with many months of design and implementation work going into it, in the hopes that the new modular architecture will encourage even more future development.

**Features of New 2.0 Architecture**
[LIST]
[*] Modular architecture: instead of monolithic Mupen64Plus releases, the core, front-end, and all plugins will be released separately in the future
[*] Simplified, more portable emulator Core
[*] Removed GUI code from plugins, making them simpler and more portable
[*] Messages from core/plugins can be shown in GUI instead of only on console
[*] Video Extension allows GUI to override video functions, to support embedded render window
[*] Startup immediately in Fullscreen mode
[*] Video resolution can be given via command-line parameter
[*] Configuration options for all plugins are in a single config file
[*] Dummy plugins are automatically used if plugin loading fails for any reason
[*] Better system integration: Core and plugins all use the same locations for storing data/config files
[/LIST]

**Core Emulator Library**
[LIST]
[*] New feature: cheat code support
[*] New feature: Keyboard shortcuts for Core commands are now user-configurable
[*] New feature: can load/save PJ64 state files
[*] Major code cleanup
[*] Removed many dependencies to simplify porting to other platforms
[*] Use XDG directory convention for file locations on Unix
[*] bugfixes: several different crashes and game incompatibilities, including collision problems in Banjo-Tooie
[*] bugfix: frame advance feature should advance every frame, instead of every vertical interrupt (every field)
[/LIST]

**Input Plugin**
[LIST]
[*] New feature: Joystick/Keyboard auto-configuration
[*] New feature: deadzone and peak analog joystick values are now configurable
[*] Major code cleanup: mouse movement and analog axis code was terrible, removed non-standard data types
[*] Improved debug messages
[*] bugfix: mapping the X/Y analog sticks to keypresses didnt work
[*] bugfix: LeftCtrl-LeftAlt key command when mouse is enabled to now toggles between grabbing and releasing the mouse pointer
[/LIST]

**Console Front-End Application**
[LIST]
[*] Brand new Console-based front-end for Mupen64Plus
[*] New feature: R4300 Core Comparison for debugging
[*] New feature: Cheat code support from command-line
[/LIST]

**Rice Video Plugin**
[LIST]
[*] removed unused configuration parameters
[*] bugfix: handle fullscreen video mode properly: start up in this mode instead of always starting in windowed and needing the core to switch to fullscreen
[/LIST]

This is a beta release, so it is not expected to be perfect.  Please try it out and post your findings here or report bugs on the [Google Code Issue Tracker]("http://code.google.com/p/mupen64plus/issues/list"). There are a couple of caveats that users should be aware of. First, there is no GUI front-end application in this release.  The only user interface is the console-based one. There is a Qt GUI which is being re-written and is in the early stages of development, so for now you'll have to use the command line interface.  Secondly, this release only includes the Rice Video plugin.  Warhaft has ported the successor to "gln64", called Arachnoid, to the new Mupen64Plus 2.0 API, and this is working and available in source code form at: [http://bitbucket.org/wahrhaft]("http://bitbucket.org/wahrhaft/mupen64plus-video-arachnoid/"). I also hope that there will be a Mupen64Plus 2.0-compatible port of the latest Glide64 video plugin, since Gonetz released the source code for Napalm several months ago.

**Quick start**
The easiest way to start running and testing this release is to download a binary bundle package from the Google Code site, unzip it into a directory, and run it with this command: "./mupen64plus m64p_test_rom.v64".  You can run it directly from this directory, or to install it to your system, simply do "sudo ./install.sh".  Likewise, to un-install it, "sudo ./uninstall.sh"

**You can help**
The Mupen64Plus team is focused on improving the quality and user-friendliness of our N64 emulator, and there are several important ways that people can contribute to this goal.
[LIST=1]
[*] Testing
For simple problems or help getting started, you can post here or join the developers in the #mupen64plus channel on irc.freenode.net.  For more serious problems, please report bugs on the [Google Code Issue Tracker]("http://code.google.com/p/mupen64plus/issues/list").
[*] Packagers
Packagers for Linux and BSD distributions are encouraged to help us reach your users by preparing Mupen64Plus packages for your distro.  Much work has been put into simplifying the build and installation of the various Mupen64Plus modules for this release, so creating packages should be easier than with earlier releases.
[*] Front-end authors
The biggest architectural change for the new Mupen64Plus 2.0 is separating the user interface from the core emulator functions.  This means that developers can create Front-End applications using any GUI technology to drive the Mupen64Plus emulator.  Currently we have a Qt GUI in the works, but the original GTK GUI will fall by the wayside if no-one picks it up and ports it to the new architecture.  The 2.0 API is fully documented at: [http://mupen64plus.emuwiki.com]("http://www.emuwiki.com/index.php?title=Mupen64Plus_v2.0_Core_API_v1.0"). The Console front-end is also quite simple and provides an excellent reference for understanding the operation of the new modular architecture.
[*] Joystick configurations
We have added a new auto-configuration feature to the SDL Input plugin which will automatically setup the joystick configuration for any joystick which is recognized.  If you have a joystick which is not recognized yet, please follow the instructions in this [emutalk post]("http://www.emutalk.net/showthread.php?t=49731") so that we can add support for your controller.
[*] Windows developers
Most of the unix-specific dependencies have been removed from the core library and plugins for this release, and the code should be easily ported to compile in Visual Studio 2005 for Win32.  If any competent Windows C++ developers would like to assist in bringing a native Mupen64Plus 2.0 build to Windows, please get in touch with us to get started.
[/LIST]

To download Mupen64Plus v1.99.1, just grab the package that you want:

[mupen64plus-bundle-bin-32-1.99.1.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-bin-32-1.99.1.tar.gz")
[mupen64plus-bundle-bin-64-1.99.1.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-bin-64-1.99.1.tar.gz")
[mupen64plus-bundle-src-1.99.1.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-src-1.99.1.tar.gz")

The MD5 sums for these packages are:

8b08e5706f4750931568776f1660f14e  mupen64plus-bundle-bin-32-1.99.1.tar.gz
8b677221100fe9b8d3f1510127f25e82  mupen64plus-bundle-bin-64-1.99.1.tar.gz
f55cfe9de9d1e99970d788ad36ccfc12  mupen64plus-bundle-src-1.99.1.tar.gz

Mupen64Plus has a [Home Page]("http://code.google.com/p/mupen64plus/") over at Google Code, with lots of useful information, screenshots, a bug tracker, a discussion forum, etc.

---

### Post by Rainstride on 2009-12-15
> **argor said:**
> from Richard42  at [New release: Mupen64Plus v1.99.1 - EmuTalk.net](http://www.emutalk.net/showthread.php?t=50098)

awesome, I'm so glad that we have mupen64plus in the repo's now. so we get these new updated versions every 6 months now:D.  I think I may wait till lucid for this, I'm sure by the time lucid hits there will be a few more beta releases. I'm glad the redesign is coming along so quickly though. looks great!

---

### Post by adeypoop on 2009-12-18
Looks good but anyone know how do i get my Saitek controller working, it hasn't been auto detected?

---

