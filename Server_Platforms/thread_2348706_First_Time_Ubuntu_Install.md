---
title: "First Time Ubuntu Install"
date: 2017-01-06
forum: Server Platforms
---

### Post by ccigas on 2017-01-06
Hello everyone, new here and new to Ubuntu. I have a server that I was able to bring home from work, dual CPU, 24GB of RAM and was hoping to install Ubuntu, desktop or server with GUI on the server in order to help a friend and I learn some coding for Android. 

Not sure if this would be the best place to post this but was hoping to figure out which version would be better for this? Also, was hoping to ask if there is any way for both of us to view the GUI through VNC on different desktop/laptops so we don't always have to be together to work together. 

Currently I use the console from the management port to access the screen but will be moving over to VNC when I know which install would be better for us.

I am a hardware guy for my company and know little about Ubuntu and how to work it, if anyone asks why I have a random server and don't know anything about it is because I only troubleshoot hardware and rack/unrack the servers.

Thank you everyone!

---

### Post by ajgreeny on 2017-01-06
*Thread moved to **Server Platforms**.* which is more appropriate for the problem and should be a better fit.

---

### Post by darkod on 2017-01-06
Linux servers are usually command line only, without a GUI. I have no idea of Android coding and don't know how that relates to a GUI and whether it needs it on the server. You need to think about what you actually need on the server, and plan accordingly. If you really install the server version with no GUI, you can have as many ssh sessions open as you want, so both of you could have a session open no problems. But I doubt that will be useful for coding... Sounds to me like coding is more appropriate to be developed on your local desktop/laptop than on a remote server... Then if you move it on a server for testing, that's OK, but in such cases you are not doing any actual coding on the server itself.

If you do decide to go for a GUI, use the desktop version straight away. No need to install server and then try adding components bit by bit, especially being new to ubuntu. Just install the desktop that has a GUI that is supposed to work like that.

There should be no problems to have two remote sessions open.

And another advice, stick to LTS releases, not always the latest one. Unless your needs really, really need the latest ubuntu, use only LTS for any serious work. Even at home. They have 5 years of support compared to 9 months of the other releases. So what ever you set up on non-LTS will be supported only very short time, basically making the setup not worth a while...

---

### Post by TheFu on 2017-01-06
@darkod is correct on most things.

There are many ways to do Android development. When I did some for about a year, it was common to download a number of pre-configured Android development setups which required a GUI.  I'm not a GUI person and have been doing software development for 25+ yrs, so quickly converted to using a terminal and building my code that way.  Vim is the only editor you need/want, if you are good. ;)  I'm a vi bigot, if that isn't clear. 

 If you are new to Android development AND new to Unix in general, that might be too hard.  Probably easier to just load up a desktop version of whatever OS the Android training you are following says to use - just be certain to use either 14.04 or 16.04 desktops, not 12.04 or any non-LTS releases. 

As for having 2 people in different locations seeing the same stuff - that is easy with tmux.  Probably not really what you had in mind, but terminals are how Linux servers are managed. [tmux will let multiple people share the same terminal]("https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen").  The tmux stuff will be over ssh and secure. tmux has other features which make it a way of life for most Unix admins/programmers worldwide.

The other option is to use a desktop sharing service, like talky.io. Just be aware that none of these providers are really secure.

---

### Post by Bucky Ball on 2017-01-06
> **darkod said:**
> And another advice, stick to LTS releases, not always the latest one. Unless your needs really, really need the latest ubuntu, use only LTS for any serious work. Even at home. They have 5 years of support compared to 9 months of the other releases. So what ever you set up on non-LTS will be supported only very short time, basically making the setup not worth a while...

+1.

---

