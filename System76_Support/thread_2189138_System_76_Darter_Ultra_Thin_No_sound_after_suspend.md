---
title: "System 76 Darter Ultra Thin No sound after suspend (Ubuntu 13.10)"
date: 2013-11-20
forum: System76 Support
---

### Post by garyfallidis on 2013-11-20
Hello,

There is no sound sometimes after suspend. I tried things like sudo alsa force-reload. But nothing worked. The sound works okay again only if I reboot.

Any ideas? My notebook model is a System 76 Darter Ultra Thin with Ubuntu 13.10.

Thank you,
Eleftherios

---

### Post by ddraper2 on 2013-12-02
I am having the same issues with a Gazelle Pro that I updated over the weekend. Still investigating. Will post if I find anything out.

---

### Post by garyfallidis on 2013-12-08
Thank you ddraper2. If anyone has any suggestions on how to track down this problem. That would be much appreciated.

---

### Post by garyfallidis on 2013-12-17
Hi I figured out now that the problem is not with the suspend. The sound stops sometimes when the power cable is removed and the notebook goes on battery. Any ideas?

---

### Post by ddraper2 on 2013-12-17
I respectfully disagree. I have been looking at this problem and spending a lot of time on it. In my case with the Gazelle Pro 9 (new in September) it is the suspend/resume cycle. Have been playing with killing/stopping pulseaudio and then forcing an alsa reload. So far no luck. I also played around plugging/unplugging headphones with no luck.

I am going to try using an HDMI cable into a monitor with speakers and see if the HDMI sound has the same problems as the built in speakers.

This is really starting to annoy me and I am about to open a ticket with System 76 just to see what they have to say.

---

### Post by ddraper2 on 2013-12-20
I finally had some time to look this over and I have found a solution.

The problem appears to be that pulseaudio is not "letting go" of the sound devices when it is suspended and that stops alsa from resuming correctly. Perform the following steps and you should be OK.

1. Add the following line to /etc/pulse/client.conf file.
> sudo gedit etc/pulse/client.conf
Add to end of file: autospawn = no
This will allow you to stop pulse audio and not have it restart immediately. This also looks like ti can cause some problems with pulseaudio starting when you login.
The alternative is to not edit the file but instead create one name ~/.pulse/client.conf with a single line as listed above.

2. > pulseaudio --kill

3. > lsof /dev/snd/*
This should not show any devices. If it does then you need to stop those processes.

4. > sudo alsa force-reload
Should not be any errors.

5. > pulseaudio --start

Your sound sound be working again. If you created a local copy of client.conf file you might have to start pulseadio manually on login or add a command in your startup scrips to start it.

---

### Post by yug23 on 2014-07-02
Thanks for this, I can confirm it works for me too. :)

---

