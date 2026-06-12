---
title: "Figuring out home server things"
date: 2014-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by ndc2 on 2014-09-22
Hey all. I have put together a server box from old components a friend had from his own server. It has a dual core Xeon processor, 8GB RAM and a couple terabytes of HDD space. I'm coming here for some technical advice.

I'm planning on making this thing a file server and occasionally a game server (like a counter strike server). First and foremost I am wondering if I should use virtual machines (one for file server and one for the gaming stuff) or if it's okay to clump the two together on one OS (security-wise). The game server would only run for maybe hours at a time and maybe once or twice a week.

Second -- would Ubuntu 14 be a resource hog? I would prefer having the GUI (I'm okay with the terminal but by no means an expert) but obviously will not need stuff like the mail client, open office, etc.

Third -- and this is fairly important: Would it be possible to use a portion of this server as a Time Machine backup partition? Has anyone ever done something like this?

I'd also like to use this as a media server for the Playstation 3 in the living room but I assume that shouldn't be too difficult to implement in Ubuntu.

Lastly: I have the option of using Windows Server 2012. Would it make sense to use that instead?

Sorry for the vague questions :p

---

### Post by Lars Noodén on 2014-09-22
1.  Linux systems are designed to run multiple services concurrently.  Adding virtual hosts would greatly increase your resource overhead as well as complexity.  

2. Programs get pushed to the background when not used, so I would not worry about a GUI consuming resources when the GUI itself is not in use.  If you want to, you can use a lighter choice like a plain window manager instead of a full GUI.  Then you would run Openbox, FVWM or something like that.  You can also train up with both a GUI and a terminal connection, using the terminal over SSH when you feel like trying something new and falling back to the GUI when you need to.

3. Do you mean Time Machine(R) itself or just something with similar functionality?

---

### Post by ndc2 on 2014-09-22
> **Lars Noodén said:**
> 1.  Linux systems are designed to run multiple services concurrently.  Adding virtual hosts would greatly increase your resource overhead as well as complexity.  

2. Programs get pushed to the background when not used, so I would not worry about a GUI consuming resources when the GUI itself is not in use.  If you want to, you can use a lighter choice like a plain window manager instead of a full GUI.  Then you would run Openbox, FVWM or something like that.  You can also train up with both a GUI and a terminal connection, using the terminal over SSH when you feel like trying something new and falling back to the GUI when you need to.

3. Do you mean Time Machine(R) itself or just something with similar functionality?

I mean I want my Macbook to basically back up to the server using Time Machine. The same way it would if I inserted an external HDD to back up to. So yes I mean Time Machine itself

---

### Post by Lars Noodén on 2014-09-22
> **ndc2 said:**
> I mean I want my Macbook to basically back up to the server using Time Machine. The same way it would if I inserted an external HDD to back up to. So yes I mean Time Machine itself

I think there is a way to do it using Netatalk:

[http://ubuntuforums.org/showthread.php?t=2105755](http://ubuntuforums.org/showthread.php?t=2105755)

but I have not tried that method myself.  It should be doable though.

---

### Post by mastablasta on 2014-09-23
for server GUI check the Ubuntu based Zentyal. default install installs a desktop, but expert mode will allow you to install a webgui. so you connect via web to server and then maintain it with gui.there are a few other GUI available like that (such as webmin, ajenti ...).

you might also want to explore owncloud for storing files.

otherwise the fileserver gui openmediavult just went to 1.0 (Debian based). there is also an option to install xfileserver or something like that.

if you are more accustomed to WIndows and you have the server CD you can use that as well.

---

### Post by cariboo on 2014-09-23
You can also use rsync and ssh to backup your Mac, both are supported by OSX

---

