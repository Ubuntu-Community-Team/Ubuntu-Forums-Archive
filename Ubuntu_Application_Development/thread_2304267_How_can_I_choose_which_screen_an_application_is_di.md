---
title: "How can I choose which screen an application is displayed on"
date: 2015-11-25
forum: Ubuntu Application Development
---

### Post by linuxonbute on 2015-11-25
I have seen a Windows program which allows you to choose where to send video output to.
For example with a laptop connected to a TV via the VGA port 'Display 1' is the laptop screen and 'Display 2' is the TV
Selecting 'Display 2' and then launching an mp4 video displays the video on 'Display 2' only.
On the laptop everything else is displayed including the program which launched the video.
Can this be done in Linux? Even better is it possible in python? 
I want to use this with a projector.
tia
Norman

---

### Post by T.J. on 2015-11-26
You can't, usually.  The best you can do is get the effect you want is to set the primary monitor.  Often a desktop environment will default to the primary screen, same as Windows.  Unlike Windows, it really depends on your desktop environment. What you can do is move the window after the application has started up, but the desktop environment and the window manager usually select the default screen.  I presently do not know of any helper programs to change that.

This is not to say that your request is impossible.  In fact, it is very possible. but most desktops designed after Windows, like Unity/Gnome and KDE do not do allow you to preset which monitor for a specific app. There are others that do, but you have to understand X11 window settings, specifically "window geometry" in order to do it. As for using Python, the answer is the same.  If you can reset the window geometry, then you can pretty much do whatever you want.  I suspect most of the "modern" DE's might annoy you in trying to do so.

---

### Post by linuxonbute on 2015-11-26
Thanks T.J, I thought that might be the case.
I wanted to display videos on a projector but nothing else except the wallpaper.
Up to now I have been doing it the way you indicated using vlc so today I started 
looking to see if there is some way of doing it from within vlc and came across this:
[http://albert-mylearning.blogspot.co.uk/2012/06/vlc-display-video-on-specific-monitor.html](http://albert-mylearning.blogspot.co.uk/2012/06/vlc-display-video-on-specific-monitor.html)
Of course Linux isn't mentioned and without a second screen connected nothing shows up.
When I get chance I will connect my TV via hdmi ( same connection  as used by projector ) and see if it then appears.
I will post back when I find out

---

### Post by T.J. on 2015-11-26
Actually, your question intrigued me.  My knowledge of X11 has slipped a great deal over the years.  I used to know a lot more.  If I find a way, I'll let you know.

As an afterthought, have you tried using Kodi (formerly XBMC)?  You can specify which screen it uses, in the settings.  It plays everything that VLC can. If it fills your need, it would be an easy fix.

---

### Post by Bucky Ball on 2015-11-26
I use two screens. If I click on a screen and launch an application, the application launches on that screen. I can move windows to any screen I want. 

Your video is displayed on display 2 only? Are you saying you want it on both screens, so they are identical, or mirrored? Then Settings> Display> Position> Same as.

---

### Post by linuxonbute on 2015-11-27
@Bucky Ball,
No, I only want the video to display on the projector. I have them set as extended. I don't want the audience distracted by all the other stuff.
Thanks for the thought anyway.
@T.J
I haven't tried kodi at all. I will have a look now.

---

### Post by linuxonbute on 2015-11-27
Kodi does look promising. I can launch it with the video I want playing and select which screen I want it to display on.
It doesn't automatically close after showing the video but I believe I can add an option in my python script which will simply kill it anyway.
I think this will work for me but I have also now seen mpv. It is a command line program which plays the video and then closes. Don't know yet if it can play video on the screen I want it to or not.
I will play about with them both and get back here and let you know how I get on.
Thanks
Update
mpv does what I need, it can be set to launch on whichever display I want and it closes by itself as soon as the video ends.
Kodi doesn't so I have to add an extra button or reprogram the one which launches the program to kill it, 
while vlc closes but doesn't have the option to launch on the screen I want.

---

### Post by T.J. on 2015-11-29
Great!  If there is anything else I can try to help with please post, but if you have what you need please mark the thread solved.

---

