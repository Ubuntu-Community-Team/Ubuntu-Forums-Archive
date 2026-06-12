---
title: "yast or something like it"
date: 2005-11-24
forum: Server Platforms
---

### Post by SuperMike on 2005-11-24
One of the selling points for me with Ubuntu as a server would be to have a text-mode yast that I could pull up in order to make routine chores keep me from this ](*,) while I try to remember command --flags.

And if not yast, then something like it. At my office, the only reason they keep SLES9 around and don't go with Ubuntu is simply because of yast. And that's globally in this multi-billion dollar company. That's the only argument that people give me at this company except for the fact that Novell has a strong indemnification clause. They even tell me that Novell's indemnification is stronger than Red Hat's, so they rejected RedHat.

(BTW, and this is a side-thread, but it seems odd to me that we have to rely on a reseller of Linux to have to have an indemnification for stuff they only contribute to. Businesses who use Linux should be able to purchase some kind of umbrella insurance and use an offshore brand of Linux to not only skirt the lawsuit issue but have a landing pad (via insurance) that they can fall on if that falls through.)

And the tide is turning at my company. Many of us Linux-heads there put SLES9 installations in to please the corporate office, but we have secret rogue Ubuntu projects on our workstations simply because we like it better. So if Canonical could consider a text-based yast-like tool, they may sway multi-billion dollar corps like my employer.

---

### Post by diebels on 2005-11-25
Many years since I used yast, but isn't "configure-debian" something like it?

---

### Post by labrador on 2005-11-25
specifically what from yast?

Is it related to package management?  Then apt-get and other text window
alternatives with a long Debian heritage might be the answer.  Yes you
would need to learn some new commands, and after that, you would be
master of it.

---

### Post by oskude on 2005-11-25
and yast was why i stopped using suse :)
i just clicked some fancy buttons, and when that didnt work, i was screwed...
i mean, i didnt know what happened behind the buttons, so i couldnt fix it myself...
well, maybe its just me, but i want to know whats going on "behind the curtain"...
but then again, im only a home user...

and ubuntu allready "ruled" on small business ;)
[http://www.ubuntuforums.org/showthread.php?t=94850](http://www.ubuntuforums.org/showthread.php?t=94850)

---

### Post by Enki on 2005-11-26
Have you tried aptitude?

---

### Post by oskude on 2005-11-26
[QUOTE=Enki]Have you tried aptitude?[/QUOTE]yast is more than aptitude (package manager)

---

### Post by rackhost on 2005-11-26
I like also Yast from Suse, what i miss in other distributions.

Yast is more a full interface of all kind of services, pkg management, firewall setup/config, network config/setup, etc.  Like the webbased webmin, but a nice kind of program for KDE/GNOME and ... also command line.

Franky

---

### Post by -DarkMind- on 2005-12-10
[QUOTE=Enki]Have you tried aptitude?[/QUOTE]
yast it's more than a package manager, with yast you can configure ALL the system, network, mouse, tv card, wireless, web server, nfs, etc :)

---

### Post by gruepig on 2005-12-10
I think there are probably a number of people who would benefit from something like Libranet's adminmenu (the console version) for Ubuntu server installs.  Hmm ... is anyone working on this?

---

### Post by Rajan Varadarajan on 2005-12-19
I think a light weight gui admin tool for servers would be a wonderful addition to ubuntu as a server. No need to carry all the load of GNOME, Nautilus, and other junk. I have set up a ubuntu server but I like the GUI at times and so I chose the standard install. I would like to turn of loading GNOME, etc. with some kind of script but then load it on demand.

Thanks for the discussions.

---

### Post by SuperMike on 2006-07-22
You know, if you combine Bash with VT100 codes, or perhaps PHP or Perl with VT100 codes, you can build a yast-like console tool. (I'm not talking the GUI version, guys.) Therefore, on Ubuntu Server, they could have a tool like 'ust' (Ubuntu System Tool) that could permit things like:

* Adding, Modifying, Removing Users
* Modifying User Account Parameters
* Adding, Modifying, Removing Groups
* Modifying Group Account Parameters
* Assigning, Revoking Group Memberships
* Resetting Passwords
* Configuring a Service (postfix, courier, apache, etc.)
* Run-level Service Editing
* Net Card Settings Editing
* Stop/Start/Reset Netcard
* Stop/Start/Reset a Service
* Connecting to Aptitude To Install New Software
* Reset a Server
* Shutdown a Server

For the unwashed, a VT100 code is a set of keystrokes, usually starting with the Escape character, that when sent to the console it can do things like lock and scroll parts of the console, invert characters, change their color, make them blink, position a cursor and place text in a certain place, and so on. It comes from the old Vax Terminal days and VT100 was a brand of terminal type you could purchase. VT100 caught on as a fast way to do a 'TUI' (Text User Interface). Many bootup sessions on many distros still use VT100 codes even today.

Reasons why I liked Yast:

* Suse Minimal, perfect for server installs, doesn't come with a GUI.

* When a server went down late at night, and I only had the unwashed still there in the office, I could call the unwashed in my office, have them log into the server room, pull open yast, and do my bidding far easier than I could if I told them how to type a command.

* When I was lazy, I didn't have to remember parameters for many common tasks. Sometimes setting up a user account can have lots of switches if you're picky, and yast was a way around having to remember all that.

* While I was in it and thought that I needed to do something other system task, I was right there and it was only a menu choice away.

THEREFORE, I say all you developers out there -- we should get a project started in SourceForge to start talking about what this would look like, the feature set, what it does not need to do, and what language it could be written in but which others could extend fairly easily (PHP-cli comes to mind because it's popular and can even allow newbies to help write code, versus Perl, which usually only has sys admins with that kind of skill).

I have just submitted a project task on SourceForge (sourceforge.net) called 'ust' so that the project planning can begin.

---

### Post by peanut butter on 2006-07-22
this is one of the reasons i was hesitant to switch to ubuntu.
another idea is a terminal-gui for enabling and disabling apache vhosts.

---

### Post by SuperMike on 2006-07-29
I've just started the Ubuntu Sytem Tool project at Sourceforge:

[http://sourceforge.net/projects/ust/](http://sourceforge.net/projects/ust/)

A screenshot and a downloadable menu demo is available that will work on all Ubuntu desktops and server installations.

It's not much, but it's a start. The menus were a real pain to build but I got it working.

---

### Post by pirast on 2006-08-11
You may want to have a look at [http://ubuntuforums.org/showthread.php?t=223386](http://ubuntuforums.org/showthread.php?t=223386).. At the end of the thread I started to compile YaST on Ubuntu.. The QT gui and the user module work, sadly, the ncurses module does not work yet. But I am in contact with the YaST developers.

---

