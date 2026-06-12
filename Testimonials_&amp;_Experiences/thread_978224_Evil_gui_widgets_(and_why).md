---
title: "Evil gui widgets (and why?)"
date: 2008-11-10
forum: Testimonials &amp; Experiences
---

### Post by BetterSense on 2008-11-10
I use ubuntu. I've been linuxy for about a year, praise the lord. But one thing that has been bothering me is the proliferation of GUI widgets that don't play well (IMO) with the 'real' system. I don't really understand this because I'm new to the unix philosophy and all and certain things just strike me as odd:

Example: I use knetworkmanager to connect to wireless. This suits me fine and I like it. Whenever I start my computer, it automatically connects to the local wireless network, passwords and all. This is as it should be. However, on certain occasions I boot my computer and never start X, because I simply want to read a file, use bc, or whatever. On those occasions, my computer never connects to the internet, because knetworkmanager never launches. I understand it's a GUI program that needs xorg to run...but why? Why is it developed that way, instead of being a program that can run without graphics? Why can't knetworkmanager simply be a 'front end' to a 'real'  (iwconfig?) program? In otherwords, if I start my system, but not X, then it should STILL connect to the local wireless network, why should it wait until X launches? So if I start my system, I have to use, what, iwconfig I guess, though I have no idea how I would do that...I don't even know how to check if there are any available networks with iwconfig. But my point is having a completely separate widget for the gui seems to separate the GUI and command line when they could be more integrated. 

Consider mplayer. A command line tool that has available gui frontends. Consider synaptic...as far as I can tell it does the same thing as apt-get, just with pretty pictures. IMO, this how EVERY program should be, including network managers. Instead you have this situation where gui tools are becoming tools in and of themselves, and that's weird.

Right now the little speaker icon in my taskbar has a red cross on it because it's muted. But if I run alsamixer in the command line, I see the master volume turned all the way up. WTF? Why isn't the speaker icon thing just wired straight to the alsamixer slider? How am I supposed to know which of 2,3 who knows many controls is actually controlling my sound level?

Consider pidgin. Pidgin should totally work from the command line, it's an IMer. But it doesn't; you could make a command-line IM client I guess, but why the disconnect?

---

### Post by 3rdalbum on 2008-11-11
You are 100% correct about Network Manager. It should run and connect to networks during the boot process, rather than wait for you to log into a GUI. The little icon on the panel is a seperate process to the actual NetworkManager, so why does it only run when the little icon is running?

The current situation just makes things less flexible, and more confusing. For instance, if you're on wireless and you remove a package that stops Gnome from working, then you're up the creek! The same for if an update breaks X, for instance, and you need to upgrade again to a fixed version. You can't, because Network Manager is not running, because X isn't running. You would need to learn the command-line ways of connecting to your wireless network, or plug in a cable and reboot.

For the record, there is a command-line version of Pidgin, called Finch. It's not installed along with Pidgin, but it uses the same back-end library and is designed for non-GUI use.

---

### Post by BetterSense on 2008-11-11
I'm glad I'm not the first one that's noticed this bit of inelegance.

---

