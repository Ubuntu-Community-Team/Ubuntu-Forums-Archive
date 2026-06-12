---
title: "Editing remote files as root"
date: 2008-04-17
forum: Server Platforms
---

### Post by lodp on 2008-04-17
I'm using Dolphin to log in to my web server with SSH, and manage files there, which is working very well.

What Dolphin doesn't accomplish for me though is to perform tasks that require sudo, like changing apache or php configurations, things like that.

The login I'm using is working fine with sudo in the plain shell. But when I hit "Open as Root" while browsing the remote box in Dolphin, it says "could not connect to host xxxx".

Is this a bug, or something that's not doable with the FISH protocol?

what are you guys doing to do things in a GUI? i guess i could probably make SSH allow root logins, but i don't like the idea..

---

### Post by twistedtwig on 2008-04-17
i might sound a bit daft (I dont know what dolphin is) but if you are coming from windows I use putty to connect via command line and can just do sudo.  If I am in linux I use the terminal and use the command line.

sorry if that doesnt help

---

### Post by lodp on 2008-04-17
yeah, i do command-line too for SSH right now, but a file-browser just saves a lot of time. i hate all the typing. and editing files with Kate (or gedit for that matter) is a whole different world from nano (or vi, lord have mercy). 

dolphin is the new kubuntu file manager. i like it a lot apart from that little issue.

EDIT: I totally forgot to post this bug report i once filed for this; [https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/201162](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/201162)

no reaction yet, though

---

### Post by timcredible on 2008-04-17
any chance you can just login with [xdm]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27")?

---

### Post by lodp on 2008-04-17
i've never thought about doing it this way, actually this in kinda intriguing .. is it secure?

security is a big issue for me. ssh allows me to turn off password authentication and use certificate authentication instead.

---

