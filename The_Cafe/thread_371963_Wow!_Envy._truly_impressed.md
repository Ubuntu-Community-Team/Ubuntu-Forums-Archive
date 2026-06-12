---
title: "Wow! Envy. truly impressed"
date: 2007-02-27
forum: The Cafe
---

### Post by FuturePilot on 2007-02-27
I was having some issues with video playback and finally came to the conclusion that conclusion that it was a driver problem. I was using the one in the repos, so that might explain it. So I downloaded Envy and ran it. That was so easy. Everything went perfectly. Now I've got the latest driver and my video playback issue is solved. I'm truly impressed by this script. The only thing I'm worried about is the next kernel update, but it seems that Envy should be able to get things running again when that time comes. The possibilities of open source software keeps amazing me. I'm always finding out cool things like this that amaze me.:guitar:

---

### Post by Sammi on 2007-02-27
It's very simple and it has made my live much easier. I now have the newest and greatest Nvidia drivers installed, running Beryl and World of Warcraft at the same time!  :guitar:

...ok I don't do this regularly as it gives unnecessary overhead. But still :D

It even uninstalls very gracefully if it should fail, so you can install default repo drivers again. Looking around this forum I haven't noticed it leaving many with broken systems. Very nice.

---

### Post by izanbardprince on 2007-02-27
My opinion is that I wish Ubuntu made it easy to get the latest video drivers, because with broken video support, the operating system just doesn't work very well.

Until the binary drivers are reverse engineered, the official ones will just have to do.

And if you use the official drivers and download kernel updates, you'll reboot and have X crash you out to a command line (just re-install the driver),t it's a pain in the butt.

---

### Post by lonce on 2007-02-27
Well, I have mixed feelings on this.  

On one hand, yes, it can be a hassle to install the video drivers and all that.

On the other hand, from having to do it many, many, many times because I just cant stop tweaking things, ( I am compulsive about messing with things ), I have learned allot about how Ubuntu and Linux function and its forced me to learn.

So while it can be easier, after 6 months of using nothing but Ubuntu, there are very few things that come up that I cannot handle from command line.  Even the video drivers.

---

### Post by ubdai on 2007-02-28
Just installed new Nvidia card drivers using envy.

What can I say, I am impressed. Great deal of thanks goes to Alberto, the creator of the script.

Thanks again 

Ubdai

---

### Post by DoctorMO on 2007-02-28
could you perhaps post a link? searching for the word 'envy' in google brings up too much porn.

---

### Post by ex_win_slave on 2007-02-28
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) so try this one...

---

### Post by ~LoKe on 2007-02-28
> **DoctorMO said:**
> could you perhaps post a link? searching for the word 'envy' in google brings up too much porn.

[http://www.google.com/search?hl=en&q=Ubuntuforums%2C+%22Envy%22&btnG=Google+Search](http://www.google.com/search?hl=en&q=Ubuntuforums%2C+%22Envy%22&btnG=Google+Search)

---

### Post by pt123 on 2007-03-06
I had major problems with the nvidia drivers on my computer causing x not to load. But this envy.deb was awesome, installed the correct drivers and even recognised by monitor. 

But because it went so smoothly I am scared to screw it up by trying to install beryl as some of the guides I have seen involve rebuilding nvidia drivers.

Is there a guide to install beryl after having used envy to install your video card?

---

### Post by maniacmusician on 2007-03-06
I see you're using edgy. If you want a stable Beryl, follow Step 1. and then Step 3. If you want the bleeding edge beryl (updated every few days, sometimes every day), follow steps 2 and 3. **Warning: Steps 1 and 2 are exclusive of each other. You must pick one of them, you can't do them both.**  Also, this is for Edgy Eft. It probably won't work on Dapper Drake or Feisty Fawn.

Step One:
> 
Add the following repository to /etc/apt/sources.list:
[QUOTE]deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
Then add the keys for the repos:
> sudo echo && wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
Then, 
> sudo apt-get update && sudo apt-get dist-upgrade
And then, 
> sudo apt-get install beryl emerald emerald-themes
[/QUOTE]

Step Two (Unstable Beryl)
> 
Add the following repositories to /etc/apt/sources.list:
[QUOTE]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Then add the keys for the repos,
> wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Then,
> sudo apt-get update && sudo apt-get dist-upgrade
And then, 
> sudo apt-get install beryl emerald emerald-themes
[/QUOTE]

Step Three (Configuring your system to optimize Beryl)
> 
Open /etc/X11/xorg.conf. Find Section "Modules" and put a # in front of dri like so:
[QUOTE]Section "Module"
 ....
#             Load    "dri"
....
EndSection

Find the Section "device" (where your driver is) further down in the document, and add these two options:
> Section "Device"
....
        Option "AddARGBGLXVisuals"
        Option "AllowGLXWithComposite" "True"
....
EndSection

Now scroll down to the very end of the document and paste in this part:
> Section "Extensions"
        Option "Composite" "Enable"
EndSection
[/QUOTE]
Some notes:
-You may want to install beryl-plugins-unsupported for some extra plugins.

-You may want to disable "Sync to VBlank" in Beryl Settings Manager" for improved performance

I think that's all correct. Enjoy.

---

