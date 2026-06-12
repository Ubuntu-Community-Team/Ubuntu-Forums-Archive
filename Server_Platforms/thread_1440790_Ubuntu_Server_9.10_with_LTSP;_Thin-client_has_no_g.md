---
title: "Ubuntu Server 9.10 with LTSP; Thin-client has no gui when logged in"
date: 2010-03-27
forum: Server Platforms
---

### Post by MikeLeePIY on 2010-03-27
[COLOR=black][FONT=Verdana]OK. I installed Ubuntu Server 9.10 i386 version onto my machine. I have a second machine acting as the thin client[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The Ubuntu server doesn't have a gui only cli. LTSP has been installed using this command:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sudo apt-get install ltsp-server-standalone openssh-server[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I also configure dhcp.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Here is my problem:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When the client machine boots up it gets an ip from dhcp and loads the tftp information and displays the LTSP Ubuntu login screen[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I enter my root username and password and it loads. Once loaded I only see a "command prompt cli" no gnome GUI no desktop nothing. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]How do I create a gui for the clients only? I want to keep the server running cli.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Do I have to install something in the chroot? [/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by MS-Hater on 2010-03-28
I remember that there was a package that allowed you to use a web-based GUI like you'd use for FreeNAS, but I can't remember where I saw it right off the top of my head. I'll search for it, and post what I find here for you. As far as setting up a GNOME desktop environment that will be used ONLY by remote users, I don't think that's possible (at least, not yet... you never know for sure that the Ubuntu devs are up to). Feel free to correct me if I'm wrong, but be ready to provide proof; I don't accept word-of-mouth. I just did a package search, and it looks like there is a dedicated LTSP client that you have to install on the client machines to get the GUI. I'd guess the syntax to be "sudo apt-get install ltsp-client" or something like that; play around and you're bound to get it eventually.

---

### Post by MikeLeePIY on 2010-03-28
[COLOR=black][FONT=Verdana]I installed the Ubuntu desktop version then installed the Ltsp package and it worked. I was able to log-in using the thin-client and the gnome Desktop appered and worked.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]If you goto ubuntu.com and look at the server benefits it listed ltsp as one. So when a school decides to install ltsp on ubuntu server your telling all the kids are forced to use the cli to do there math problems. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I don't understand.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Or I'm forced to use a Gui when using the server ltsp version? That way then the thin-client loads it will see a gnome desktop instead of the bash.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

