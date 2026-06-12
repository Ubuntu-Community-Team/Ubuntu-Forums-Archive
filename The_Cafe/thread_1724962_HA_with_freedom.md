---
title: "HA with freedom"
date: 2011-04-09
forum: The Cafe
---

### Post by nickleboyblue on 2011-04-09
I discovered LinuxMCE sometime in 2009 while searching for security systems that run on Linux.  It took me a computer and four months of almost non-stop tinkering to finally conclude that LinuxMCE, for all it claims to be, really doesn't stand up to the task of efficient home automation.  However, it did make me aware of several free and open source projects that can be used to control lighting in the home, to stream media, to intelligently run the telephone system, and even to take care of security surveillance.  Here I will share with you what I found.

	LinuxMCE is a complete add-on to the kubuntu 8.10 system that takes the approach of changing the entire system so much that it is difficult to use it for what a Linux box is typically used for.  This means that it requires a dedicated LinuxMCE server and several dedicated computers besides.  This setup isn't cheap, nor is it easy to assemble correctly.  It is impossible for even some of the most experienced Linux users to get it running on their machines, leaving beginners in the hopeless afterburner of a project that, while it is advertised to function well, doesn't manage to do so.

	On the bright side, LinuxMCE showcases the idea that there are already some very well developed free and open-source projects out there that can be used to such an end as home automation.  One of the most shining examples of this is Asterisk, the free PBX (Private Branch eXchange) telephony system.  Not only does Asterisk offer everything that a commercial PBX system should, it also has an add-on that can be used to track where in the house a cellphone is and, in theory, where it's owner is.  This ensures that you avoid unnecessary cellphone minutes while you are at home, and that you get your phone calls direct to your cellphone when you are not at home, without having to give out more than one phone number.  However, telephony is just to tip of the iceberg when it comes to cellphone tracking through bluetooth.

	If a home automation system knows which room you are in, it can then play your media automatically wherever you are in your home.  It can also automatically disable the security system, turn on lights, or any number of other things that it is configured to do, all based on where your cellphone is and what is going on in that room.  This means that, without even pushing a button, one could start watching a movie in the living room and continue in the bedroom, kitchen, or wherever else they have a screen set up, without even touching a button.  This means that you could walk in your front door without having to unlock it, or leave your home empty without having to lock it.  All of that is done automatically.

	Another great tool for the home automation enthusiast is ZoneMinder.  ZoneMinder is a fully functional security system based on the motionwrapper program.  ZoneMinder has a lot of features that are extremely useful in the realm of video and audio security.  It can even hook up to an alarm system!  It doesn't look all that pretty in it's user interface though.  My suggestion?  Improve on the original ideas and create a better user interface.  Once that has been done, incorporate it into the various media systems available for Ubuntu, like Boxee, XBMC, MythTV, etc.  By using multiple media systems, it will become easier to set up a system that agrees with it's users on a more basic level.

	There are a few tools available for command-line manipulation of electric signals in the walls of existing homes.  These signals turn on and off X-10 devices, allowing you to control lighting, window shades, door locks, and any non-digital appliance that plugs into the wall.  With a fully-implemented system, this tool would take care of watering plants, feeding animals, turning off lights for power conservation, opening the shades when someone is home in the middle of the day, and dimming lights when video media is being enjoyed.

	XBMC, Boxee, or MuthTV could be modified to automatically have access to any media on the home network, and to allow a user to keep other users from accessing their media in the interest of privacy.  All three of them could easily be modified to work for security systems as well, though it may be a good idea to put security in it's own interface, as long as it is easy to use, attractive, browseable, and has multiple themes to choose from.

	And the system that drives it all?  Unity of course!  Unity Zones (previously Unity Places) are little menu items in the Unity Launcher that can open a simple interface that spans the entire screen.  The interface is only there when the user needs it.  With entries for lighting, entertainment, security, telephony, and anything else that has to do with home automation, it would be easy to answer a phone call, browse through security triggers, view what other users have been doing (parental control), turn on and off lights, and anything else they have their system set up to do.  The touch-friendly interface of Unity lends its self to such use.  And, unlike with LinuxMCE, a truly FULLY operational desktop would be available to the user by default.

	The tools are all there, and with Unity, all that is required to get it to happen is a lot of scripting, a few additions to currently existing projects, and a lot of collaboration between projects like Boxee, XBMC, and MythTV.  When setting up a system like this, one should still be able to use their favorite media center, their favorite themes, and their favorite computer.  They should still be able to tweak their system a little here and a little there without worrying about breaking their lighting system.  And a beginner should have a fair chance at getting the system up and running without having to get a college degree in doing so before attempting such a feat.

	I am not yet a computer programmer, but I am studying to become one, and will be involved in projects like what I have just explained as soon as I get the skills necessary to do so.  In the mean time, I suggest that people get to work on it.  I would love to see the day when MythTV, Boxee, Rhythmbox, Banshee, Totem, VLC, Asterisk, Skype, XBMC, and the various games that are available in Ubuntu all coexist in the same centralized home automation system without any problems.  That will be the day when the Open-Source community can stand back and say that they have effectively proven their worth.

---

### Post by LowSky on 2011-04-09
Um... you seems to have some great enthusiasm.

linuxMCE is severely out of date. most of the things you wish to do can be done directly in MythTV these days with little effort.

also look into project jarvis
[http://projectjarvis.com/](http://projectjarvis.com/)
its home automation done in a more believable light, and easily duplicated

---

### Post by nickleboyblue on 2011-04-09
Project Jarvis, LinuxMCE, and Linux-HA don't do what I want them to do.  Honestly, it is theoretically possible to do home automation, from a software point of view, by simply installing the right packages and doing a minimal amount of configuration.

What I really want though is a system where I could install one of several media centers, one of several telephony systems, one of several automation controller systems, and any games I want, as nothing more than programs on my laptop, and have them work seamlessly with each other.  Unity would allow that to happen in a way that would still make all of those functions readily accessible (from a gui point of view).  Outside of social networking and media, home automation, in my opinion, is the area that Unity shows the most promise in.

---

### Post by tschak909 on 2011-04-14
Hello. I am Thomas Cherryhomes, one of the core developers for LinuxMCE.

LowSky, Your comments about LinuxMCE being severely out of date, and able to have its features replicated using readily available pieces are not true.

First, LinuxMCE has been in a state of constant development, since its separation from its original developers (Pluto) in 2007. Our development cycles are exceptionally long, and we've had to overcome some incredible obstacles to transition to an entirely community-based development model. We are currently developing on 10.04 LTS, and will switch to 11.04 LTS as fast as we can. We have over FOUR MILLION LINES of our OWN CODE, not counting what we appropriate from other sources.

Secondly, as for your feature set. LinuxMCE's strength lies in its well thought out messaging architecture. We spent close to a decade asking the question, "What would it take to control virtually every single piece of controllable technology within the home?" and we believe we have honestly achieved this goal, especially given the turbulent and fast changing nature of the current market. We did it by interacting with today's technology, while still providing a way to scale to future standards like DLNA, when they become more widespread. Our media, lighting, climate, security, and telecom streams can follow you around the house. This is _VERY_ hard to do without some sort of infrastructure in place. Not to mention that we have the ability to dynamically control A/V gear within an entertainment area, in virtually any possible configuration (even if you want to do a setup with switching matrices to route video, the system can and does effectively handle this! Try that with just MythTV! you can't.) 

I am very dismayed at the ill-advised and ill-educated opinions forming about LinuxMCE, especially since they are not contacting us and talking with us about the technology itself. Why don't you actually see what we can do, and talk with people who know the system inside and out, before dismissing it? When we started almost a decade ago, there was nothing like it in existance anywhere...And today, we can still say the same.

-Thom

---

