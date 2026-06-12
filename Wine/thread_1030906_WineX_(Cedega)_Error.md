---
title: "WineX (Cedega) Error"
date: 2009-01-04
forum: Wine
---

### Post by axlekitty on 2009-01-04
Cedega support staff will not reply to me but I need some help. I cannot get Cedega to run wow even though it is supported. It will not run Spore Creature Creator Demo Either. The problem with wow when I run it in terminal is listed as: (I have tried opening launcher.exe and wow.exe with the same errors occuring)

[email]axlekitty@axlekitty:~/.cedega[/email]/World of Warcraft$ cedega launcher.exe
Traceback (most recent call last):
  File "/home/axlekitty/.cedega/.ui/app/classical/GameLibrary.py", line 407, in on_playButton_clicked
    self.handlePlay(self.getActiveUIShortcut())
  File "/home/axlekitty/.cedega/.ui/app/classical/GameLibrary.py", line 395, in handlePlay
    self.app.cedega.launch(launchinfo)
  File "/home/axlekitty/.cedega/.ui/lib/Cedega.py", line 506, in launch
    return engine.launch(launchinfo,wait)
  File "/home/axlekitty/.cedega/.ui/lib/Engine.py", line 489, in launch
    self.launchChild(launchinfo)
  File "/home/axlekitty/.cedega/.ui/lib/Engine.py", line 453, in launchChild
    os.execve(execpath,argv,env)
OSError: [Errno 13] Permission denied
python: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.
main.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


 but I don't know what this means or how to fix it. The .cedega folder permissions are set at 777 as a last-ditch effort.

The other problem with Spore is it says Direct X not installed. How do I install Direct X under Cedega? Isn't it supposed to come with it?

Tried in Ubuntu (few days ago) as well as Xubuntu (what I have currently).

---

### Post by Trueno22 on 2009-01-15
bump

---

### Post by beastrace91 on 2009-01-15
Do you have the game profile set to WoW?... Also try changing what windows versions you are running in as this tends to help from time to time for one reason or another.

~Jeff

---

### Post by Ameneon on 2009-01-16
The irony that paid support won't answer such questions..

In any event, WoW works just dandy on wine for most, have you tried this?

---

### Post by beastrace91 on 2009-01-16
> **Ameneon said:**
> The irony that paid support won't answer such questions..

I don't know that you are so much paying for just the support... not only is the Cedega UI really nice but it tends to run most games I have had with little to no tweaking on my part much smoother than they ever ran on Wine after hours of tweaks...

Be sides there are lots of services we pay for out there that have crappy tech support... ever sit on the phone with AT&T? :P

~Jeff

---

### Post by Ameneon on 2009-01-16
Was a little bit sloppy phrasing as I were at work at the time and calls were coming in (I, ironically, do work in support myself, one could say :P), I was mainly trying to point out that generally wine handles wow pretty well without any need for tweaks at all nowadays, although with that said the reg tweak and 3 settings one add to the config file makes a world of difference in the game's performance.

As a sidenote and perhaps more precisly to my point as far as the support part; I do think that any product you pay for should offer a modicum of support in particular when there are free alternatives to the product. But that's my 2c and opinions luckily do vary :)

---

### Post by axlekitty on 2009-01-24
After trying to get this to work and encountering the true meaning of "epic fail", I have since discontinued my Cedaga account and use wine instead. Better compatibility with most programs I need it for. 

Guess I thought as a paid program it would work better but I guess the best things in life really are free! :)  Boy was I wrong!!! Thanks for suggesting plain old wine (apparently for my setup I have to tell wine to use nt4.0 for some reason to make it work fast).

Set all the settings in cedaga to different stuff and still gave the same error. *sigh* Oh well, bye bye cedega... If you have this problem use regular old wine. It may take some extra time to get it working right but it's worth it.

---

