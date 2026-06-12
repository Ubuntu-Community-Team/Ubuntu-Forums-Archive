---
title: "WoW won't load on Wine"
date: 2010-04-18
forum: Wine
---

### Post by elegantmoose on 2010-04-18
I successfully installed WoW using Wine with no problems.  However, now when I try to launch wow, I only get a black screen.  I can hear the intro movie and I can see the cursor, but I can't see anything.  I have followed all the instructions on the WoW wiki to get it to work on Wine.  I tried running repair twice to no avail.  I can't modify the config.wtf file because there is none.  The only thing I haven't tried is reinstalling WoW, which would take an entire day.  Any help?

---

### Post by castlefox on 2010-04-18
Common dude.   Post more info about your hardware and wine version if you want some help.  Maybe link to that wow wiki that not everyone knows what your talking about.

And dont forget to read the stickies.  [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

---

### Post by asdfoo on 2010-04-19
which video card and drivers?

---

### Post by goatgonads on 2010-04-21
If it is a fresh install you need to tell it to run in opengl. I have had that same error when d3d tries to render all of the fancy movies. Right click your desktop, and "create launcher". Hit browse, and navigate to your wine folder (you will have to hit ctrl-H to show hidden files). If you installed it in wine's "program files" folder, it should be located at ./wine/drive_c/program files/world of warcraft/wow.exe. Once you tell the launcher to go there open it back up and add a wine command in front of the target,  followed by -opengl after the target.

This is what my launcher command looks like:
wine "/home/myusername/.wine/drive_c/Program Files/World of Warcraft/Wow.exe" -opengl

As far as the config.wtf file, if the game installed correctly, it is there. It should be located inside your WTF folder.  I personally like launching opengl by the command above, but you can add a: SET gxApi "OpenGL" to your config.wtf also.

Also keep in mind that linux is caps sensitive, and will fail to find the shortcut if you use caps where you aren't supposed to (unless something has changed recently).

---

### Post by D0kt0r_D on 2010-05-25
I figured I would just reply to an existing thread.

I attempted running the command suggested,

env WINEPREFIX="/home/zakk/.wine" wine C:\\Program\ Files\\World\ of\ Warcraft\\Launcher.exe -opengl 

and term spit this long thing out..

> zakk@Zakk:~$ env WINEPREFIX="/home/zakk/.wine" wine C:\\Program\ Files\\World\ of\ Warcraft\\Launcher.exe set gxapi -opengl
failed to open C:\Program Files\World of Warcraft\WTF
failed to open C:\Program Files\World of Warcraft\WTF
fixme:reg:RegSetKeySecurity 0x68,4,0x13067: stub
fixme:shdocvwersistStreamInit_Load (0x1765e->(0x32da0
fixme:shdocvw:OleControl_FreezeEvents (0x1765e->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1765e->(0)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1765e
fixme:shdocvw:OleObject_Close (0x1765e->(1)
zakk@Zakk:~$ X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  197
  Current serial number in output stream:  197
^C
zakk@Zakk:~$ 
Up until today I was able to load wow, granted without a video card prior it wasnt worth running but I just installed a new ATI Radeon x1600 Pro 512MB graphics card, and everything looks much better otherwise but now I can't even get past the launcher...please help.  I'm very new to linux and just want to play my game.  :(

---

### Post by D0kt0r_D on 2010-05-25
> **D0kt0r_D said:**
> I figured I would just reply to an existing thread.

I attempted running the command suggested,

env WINEPREFIX="/home/zakk/.wine" wine C:\\Program\ Files\\World\ of\ Warcraft\\Launcher.exe -opengl 

and term spit this long thing out..

Up until today I was able to load wow, granted without a video card prior it wasnt worth running but I just installed a new ATI Radeon x1600 Pro 512MB graphics card, and everything looks much better otherwise but now I can't even get past the launcher...please help.  I'm very new to linux and just want to play my game.  :(


Oh, and I'm running Ubuntu Karmic 9.10; my PC is 2.6GHZ, 2GB RAM, 320GB, the video card and I believe my version of wine is the most current as I had just upgraded a few hours ago.

---

### Post by dardack on 2010-05-25
> **D0kt0r_D said:**
> Oh, and I'm running Ubuntu Karmic 9.10; my PC is 2.6GHZ, 2GB RAM, 320GB, the video card and I believe my version of wine is the most current as I had just upgraded a few hours ago.


Did you install the drivers for your ATI card?

---

### Post by D0kt0r_D on 2010-05-25
> **dardack said:**
> Did you install the drivers for your ATI card?

Well I went through installing them quite a few times,  but nothing is showing up under hardware drivers.  Sorry but I'm really new to linux; I've been using windows virtually all my life and know quite a bit about how to use windows, but I'm still learning linux.

---

### Post by D0kt0r_D on 2010-05-25
BTW I'm also running a GMA Intel Graphics Accelerator which came with my pc.  It just was not enough for WoW even on minimum graphics so I shelled out for an affordable video card.

---

