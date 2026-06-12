---
title: "mplayer + .lircrc"
date: 2009-04-05
forum: System76 Support
---

### Post by Lee_Machine on 2009-04-05
I have posted this on a few other threads in various locations and I have yet to get an answer.

Does anyone now what the config command is to change or toggle the aspect ratio with mplayer in the .lircrc config file?

This is in reference to configuring an Infrared remote with LIRC. I am able to get this working in VLC, and Totem, but not mplayer (The change or toggle aspect ratio that is)

ie 

begin
prog = mplayer
remote = panasonic
button = Aspect
config = ?
end

In Totem its config = ToggleAspectRatio

No where can I find it for mplayer! After this I'll just assume it doesnt exist for mplayer :lolflag:

Thanks,

---

### Post by thomasaaron on 2009-04-06
Hi, Lee_Machine.

I don't know much about this, but this thread offers two suggestions. Have you tried them?

[http://www.linuxquestions.org/questions/linux-software-2/mplayer-1610-aspect-ratio-590474/](http://www.linuxquestions.org/questions/linux-software-2/mplayer-1610-aspect-ratio-590474/)

Here are some configuration examples too. I see one in there with aspect ratio...

[http://www.wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://www.wilsonet.com/mythtv/lircrc-haupgrey-g3.txt)

Sorry I can't be more helpful here.

---

### Post by Lee_Machine on 2009-04-06
Thanks ThomasAaron,

For some unknown reason each program has different config commands and those are for mythtv. 

I thought about the second post where you point to the option mplayer -aspect 16:10, but you have to specify for what file. 

I gave up, seems to not exist, the only two i really care about is elisa, and boxee. Both of which work just fine. 

Just a few hours ago I discovered a mythtv script written in python that literally saves many hours of witting a config file for each button, each command, each program :lolflag:

Anywho this was just a small project for me to better learn LIRC. 

If anyone cares the iguanaworks USB IR dongle works perfectly in Ubuntu 9.04. Plus they offer the drivers for it in .deb format.

[http://iguanaworks.net/](http://iguanaworks.net/)

Thanks again,

---

