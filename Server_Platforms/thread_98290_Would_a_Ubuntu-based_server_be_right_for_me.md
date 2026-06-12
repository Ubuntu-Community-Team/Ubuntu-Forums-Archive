---
title: "Would a Ubuntu-based server be right for me?"
date: 2005-12-02
forum: Server Platforms
---

### Post by MetalMusicAddict on 2005-12-02
I have a home server currently running XP Pro. There are 5 clients.

What I call a server is just a **really** stripped down desktop with a bunch of shares. Runs at about 80-100 megs active memory. Depending on what Im doing and most of the time it runs without explorer. I kill it.

_My thoughts and concerns:_
**-All drives are NTFS** (I could switch them all over if I get a dump drive to use)
**-I share with Bittornado and create torrents with MakeTorrent** (I know I can get Bittornado but I dont know about MakeTorrent)
**-I have a brand new HP Photosmart 8450 and I need its advanced printing features** (I know HP has some software now in Ubuntu for this but I dont know step 1 on how to use it)
**-I use VNC server on it and have seen people have problems with it** (Need this one to work as I dont use a monitor with the server)
**-Samba on a server level seems complicated** (One of my #1 concerns)
**-I still need drives to hotplug** (I played with a "server" install on my laptop but USB drives didnt auto-mount. Do I get gnome-volume-manager for this?
**-I still want to use Gnome**
**-I know knothing about startup.** ie: **Whats loaded at start-up and how to *really* change it.**

So Im thinking my command after I enable repos with **sudo nano /etc/apt/sources.list** and update should look like:

**sudo apt-get install x-window-system-core gnome**(or should it be ubuntu-desktop?) ** synaptic mozilla-firefox totem-xine samba smbfs gdm gthumb gparted gnome-system-monitor gconf-editor gnome-nettool gnome-terminal nautilus file-roller gedit unrar-free gnome-control-center gnome-system-tools gnome-volume-manager**

There seems to be so much I want installed I wonder about the RAM usage in the end.

My reasons for thinking of moving are these:

**-Wanting a single-OS network.**
**-No more MS.** :)
**-Future security concerns.** Not bad now its just "in mind".
**-I want to.**

So, with all of this, I dont know.

---

### Post by TeeSeeJay on 2005-12-02
It sounds like a great project box with which to learn the ins and outs of Linux and Samba. I'd give it a shot. Worst case you can dual-boot and not mess up your existing XP instance.

In that spirit, I would suggest you do as much of everything at the CLI as you can instead of using Gnome. Just because you'll learn more and understand what's going on. But whatever. A GUI can be handy.

You'll want to do a server install. I wouldn't do an "install ubuntu-desktop" because that will load up all the desktop stuff you're not going to want or need (e.g., OpenOffice, etc.).

You can install the "sysvconfig" package, which is a shell script to help manage the runlevel startup scripts.

Samba's really not that tough to configure. Before you load it up, take a look at the man for smb.conf and at least read the description of each configuration directive. The tricky part for most folk seems to be the relation of linux accounts to samba accounts, so read up on smbpasswd.

I can't speak to many of your specific requirements, but I think you should give it a shot. Do a "server" install. Remember you'll have to install ssh manually afterward.

---

### Post by MetalMusicAddict on 2005-12-02
I did just come into a 20gig HD that would be perfect to play with. :)

---

### Post by gil-galad on 2005-12-03
If you want gnome, I would just do a desktop install.  Ubuntu is only one cd, its not like its going to take up too much space.  Having extra packages around will not hurt anything, and you will save yourself the trouble of trying to pick and choose what you need.  

VNC should be very simple.  Just go to System->Preferences->Remote Desktop.

---

### Post by MetalMusicAddict on 2005-12-03
[QUOTE=gil-galad]If you want gnome, I would just do a desktop install.  Ubuntu is only one cd, its not like its going to take up too much space.[/QUOTE]
Its more about more running processes that I dont know how to stop. :)

---

### Post by gil-galad on 2005-12-03
System->Administration->Services allows you to stop services.  

The desktop install doesn't really start too many extra services though.  You will probaly want to uninstall evolution, and you might not need cups running, but thats about it.

---

### Post by MetalMusicAddict on 2005-12-03
[QUOTE=gil-galad]System->Administration->Services allows you to stop services.  

The desktop install doesn't really start too many extra services though.  You will probaly want to uninstall evolution, and you might not need cups running, but thats about it.[/QUOTE]
There are actually many more things that are started than what that app provides access to.

---

### Post by MetalMusicAddict on 2005-12-03
I think Ill switch over my drives to ext3 and install [Ext2 IFS]("http://www.fs-driver.org/index.html") to allow windows to read the drives and so Ubuntu has no problem reading the drives when I do a test install.

Ill make sure that there are no problems on 1 drive in windows before I do them all. :)

Anyone used Ext2 IFS?

---

### Post by skirkpatrick on 2005-12-03
Yes, I've got it on my dual-boot work laptop and also installed it on my daughter's dual-boot desktop and haven't had any problems with it.

---

### Post by gil-galad on 2005-12-04
[QUOTE=MetalMusicAddict]There are actually many more things that are started than what that app provides access to.[/QUOTE]

Yes, but all of them are supposed to run or run with gnome.

---

