---
title: "Kubuntu - Auto start wine app at boot"
date: 2009-08-09
forum: Wine
---

### Post by Braeden2 on 2009-08-09
I would like to auto start a windows broadband usage meter when I boot kubuntu. 

After looking into ways to do this I came up with simply creating a link to /home/username/.wine/drive_c/Program Files/ProgramsFolder/ProgramName in /home/username/.kde/Autostart.

This starts that app, but it fails to function as it should. It is dependent on two .dll files in its wine folder. If i also create links to the 2 .dll files it needs in the Autostart folder then it works fine, bar the annoyance of three instances of "Wine Windows Program launcher" in my panels task manager whilst it loads.

All of the info I can find on running a wine app on boot relate to ubuntu and are variations of add the app to system> preferences > sessions > sessions option. There appears to be no such option for kubuntu.

What I am after is the "right" way to do this, or at least a cleaner, tidier way.

Cheers.

---

### Post by NightMKoder on 2009-08-10
Not saying its impossible, but have you considered a native solution? I think the kernel keeps tabs on that stuff.

EDIT: here's some - [http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

---

### Post by Braeden2 on 2009-08-10
Thanks for the reply,

The usage meter I am using is specific to one particular ISP. It lets me know how much 'net quota I have left for the month, usage history by day / month as well as advisories of any upcoming scheduled outages etc.

---

### Post by Braeden2 on 2009-08-10
I must be missing something obvious here...
PS: It is Internode's Monthly Usage Meter that I am trying to start.


I have now tried adding a file like so:

/home/username/.kde/Autostart/InternodeMum.sh

containing:

#!/bin/sh

wine /home/username/.wine/drive_c/Program\ Files/Internode/mum.exe

the line "wine /path to file" works fine when run in the terminal, but when it autostarts on boot all I get is the jumping wine glass cursor for a bit with a "Wine Windows Program launcher" in my panels task manager.

The app does not appear to launch, its system tray icon does not appear. What have I done, or forgotten to do, that is causing this to not work?

Thanks

---

### Post by andrea000 on 2009-08-12
I don't think wine is made to work that way i don't think
i have tried to add a launcher to cairo dock to start a
piece of software with no luck so if anybody finds a way
then pass that along to me and maybe i can use it to add
that launcher to cairo dock.

---

### Post by NightMKoder on 2009-08-13
> **Braeden2 said:**
> I must be missing something obvious here...
PS: It is Internode's Monthly Usage Meter that I am trying to start.


I have now tried adding a file like so:

/home/username/.kde/Autostart/InternodeMum.sh

containing:

#!/bin/sh

wine /home/username/.wine/drive_c/Program\ Files/Internode/mum.exe

the line "wine /path to file" works fine when run in the terminal, but when it autostarts on boot all I get is the jumping wine glass cursor for a bit with a "Wine Windows Program launcher" in my panels task manager.

The app does not appear to launch, its system tray icon does not appear. What have I done, or forgotten to do, that is causing this to not work?

Thanks

try:
env WINEPREFIX=/home/username/.wine wine /home/username/.wine/drive_c/Program\ Files/Internode/mum.exe

---

### Post by Braeden2 on 2009-08-13
Thanks for the reply,

Unfortunately that yields the same result of the jumping wine glass cursor for a bit with the "Wine Windows Program launcher" in the panel. No launch again.

Shouldn't launching the script:

```
#!bin/sh

command here
```

be identical to opening up a terminal window and typing the command? How does running the script and typing it in terminal differ?

Cheers

---

### Post by Braeden2 on 2009-08-13
Scratch that, I have got it working, somewhat, better.

I opened /home/username/.kde/Autostart, right clicked and selected create new: link to application.

In the "general" tab I named it "InternodeMum", under the "application" tab in the "command" field I entered:

 "wine /home/username/.wine/drive_c/Program\ Files/Internode/mum.exe"

Then hit ok, this created a file called InternodeMum.desktop, upon launch it opens the usage meter as it should.

---

### Post by Return Privacy on 2011-09-28
Hi Braeden2,
I am trying to do the same thing, and I did what you said, copied the file name command for autostart, and it tries to start the program (I'm trying to have FileZilla FTP Server start up on boot up, it runs under Wine) but FileZilla starts but can't connect? It just keeps trying and finally says it can't connect and is disconnected? I turned it off, and manually start it, and it works fine. I think it needs to wait until Ubuntu has finished booting up all the way BEFORE trying to auto start FileZilla Server? Do you or anyone else know how to add a delay to a Wine program autostarting?
Thanks

---

### Post by themusicalduck on 2011-09-28
To add a delay to the starting of a program do "sleep ## && command"

e.g.

```
sleep 10 && wine /path/to/exe.exe
``` would wait for 10 seconds and then run the exe.

---

### Post by Return Privacy on 2011-09-30
Hi, that sounds good, but where do I put that command? 
I've never done a script before, so you'll have to   t a l k  v e r y  s l o w l y,
I'm new with this, but excited to learn.....LOL

---

