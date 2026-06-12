---
title: "Ubuntu Server 12.04.1 - problem installing/launching gnome-panel"
date: 2013-02-13
forum: Server Platforms
---

### Post by JDub8 on 2013-02-13
My computer:
Core i5 2500 -  8GB RAM
ASRock Z77 Extreme 6
Geforce 8800GT

I have a virtual machine set up in Virtualbox 4.2.6 where I've installed:

Ubuntu Server 12.04.1 64-bit - I checked the boxes for SSH server and  LAMP. After install I typed sudo apt-get install gnome-panel. Now when I  try to launch gnome-panel I get the error:  Gtk-WARNING **: cannot open  display

When I created the VM I had "enable 3d acceleration" - though i have since unchecked it the problem persists.

Ideas? I'd really like a basic GUI to help me administrate this server. Thanks in advance.

---

### Post by chrisguk on 2013-02-13
I can't take credit for other peoples work, I had a similar problem a while back and found this thread which helped.  See if it fits your situation?

[http://ubuntuforums.org/showthread.php?t=759389]("http://ubuntuforums.org/showthread.php?t=759389")

---

### Post by JDub8 on 2013-02-13
Hmm sorry I dont think so. I did see that suggestion before when i googled that problem about "export DISPLAY=:0.0 " Can anyone tell me how to browse to the file for editing? I'm not familiar with linux command line.

I'm working on a fresh install that (should?) just fire right up. Im wondering if because I checked expose 3d to host machine if ubuntu tried to configure itself for a Nvidia 8800 GT and now I need to do some side stepping because of the poor nvidia support in linux. OR maybe its worse than that? maybe virtualbox exposes the 3d capabilities in a hackneyed-ghetto way?

---

### Post by brent1975 on 2013-02-15
adding a desktop to a server is fairly simple: here are the typical general steps.

Run these commands
```
sudo apt-get update
```

then
```
sudo apt-get upgrade
```

and now to install the desktop

```
sudo apt-get install ubuntu-desktop
```


Don't forget when you are going to be Administering a server you will be in a terminal. So you will need to get used to terminal and before long you will say good bye to the desktop on your server.

---

### Post by chrisguk on 2013-02-15
I agree about the gnome on a server.  What are the benefits?  Ummmmmmmm

None! ;)

Although, some people do not feel comfortable with CLI so its easier to get around I suppose, but gnome is simply a no go area for me.

Just a thought.  Are you looking for a GUI control platform for your server?  If so why not install Webmin, Oops I cant believe I mentioned Webmin ;)  Its a powerful tool but not perfect.

---

### Post by brent1975 on 2013-02-15
HA I used webmin for a short while. Did I say short? Sure it works but if you really want to configure your server I found webmin a headache. I had problems with setting up samba shares and also setting up sub-domains. Of course I was new to linux at the time so that could have been the issue. :)  I personally Just loaded a LTS distro and planned out what I wanted to do and went step by step asking questions here and good old trusty google. Using a virtual box is a very good Idea. very simple to reload and start over. Oh how I remember the nights of bad language having to pull out the fold up lawn chair and park in the creepy basement at my server.

---

