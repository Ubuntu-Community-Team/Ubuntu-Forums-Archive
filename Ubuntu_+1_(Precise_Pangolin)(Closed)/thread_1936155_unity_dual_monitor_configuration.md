---
title: "unity dual monitor configuration"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nwadams on 2012-03-05
What do you guys think of the new dual monitor configuration in 12.04 where the unity launcher shows up on both monitors? I think this should at the very least be configurable to show up on one or both monitors.

See screenshot and bug report below for more information

screenshot:
[http://i.imgur.com/jRs42.png](http://i.imgur.com/jRs42.png)

bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/944525](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/944525)

---

### Post by prana on 2012-03-05
I can live with the Unity launchbar appearing on both screens. I just wish there was a way to visual determine which monitor is the primary monitor.

There also seems to be an inconsistency with respect to mouse movement. The mouse seems to encounter resistance when moving over the launchbar on its way to the other screen. This results in momentary confusion about where the mouse pointer is exactly. It is not hard to get used to it but it should be fixed.

---

### Post by kyleabaker on 2012-03-05
> **prana said:**
> There also seems to be an inconsistency with respect to mouse movement. The mouse seems to encounter resistance when moving over the launchbar on its way to the other screen. This results in momentary confusion about where the mouse pointer is exactly.

This is causing a lot of frustration for me. I'm constantly moving between screens, dragging across screens, etc and am finding that this is my single largest issue with Unity at the moment. I really hope to see this issue corrected before final release.

---

### Post by nwadams on 2012-03-05
> **kyleabaker said:**
> This is causing a lot of frustration for me. I'm constantly moving between screens, dragging across screens, etc and am finding that this is my single largest issue with Unity at the moment. I really hope to see this issue corrected before final release.

someone file a bug on it and link it here. I could live with the launcher on both screens without that

---

### Post by skewty on 2012-03-05
I too would be interested in following this bug.

Anybody have the bug#?

---

### Post by Script Warlock on 2012-03-05
i got dual monitors setup but nvidia vc keep on crashing unity 3d or vice versa so i use instead the unity 2d and there i found it stable and have not seen the unity panel on the second monitor.

---

### Post by everytimeref on 2012-03-06
Why???

I don't understand why I need 2 unity launchers. I want one Launcher and one set of indicator applets, one System settings shutdown button and one clock. And I want to decide where to put them. Is that too much to ask?

I like unity, I really do and am looking forward to seeing how much more functuinality it has in 12.04. in 11.10 in so many ways it's less useful as a launcher than Docky (Dash is excellent though, how did we manage without it?).

The most annoying thing about Unity for me is when set to auto hide, it always unhides when I use the "back" button on my browser and also when I'm using spread sheetsand click on row headers. Can't **I decide** where to stick the launcher so that it doesn't constantly interupt my workflow?(Troll warning) Even windows lets me do that (end Troll warning).

---

### Post by Script Warlock on 2012-03-06
@everytimeref, unity development is just a year old?... that means too young to cope your wants..

---

### Post by alphacrucis2 on 2012-03-06
I like the launcher on both screens and it works well for me. I guess it could be an option.

---

### Post by wgarcia on 2012-03-06
I entered a bug report on the mouse resistance problem:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950)

---

### Post by Script Warlock on 2012-03-06
> **wgarcia said:**
> I entered a bug report on the mouse resistance problem:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950) i don't think this is a bug but something like a feature. i saw this one inside the ccsm called "Launcher Edge Stop Overcome Pressure".

---

### Post by wgarcia on 2012-03-06
> **Script Warlock said:**
> i don't think this is a bug but something like a feature. i saw this one inside the ccsm called "Launcher Edge Stop Overcome Pressure".

But in the context of dual monitor this is a problem, because you have to be traversing the launcher all the time.

---

### Post by prana on 2012-03-06
> **wgarcia said:**
> I entered a bug report on the mouse resistance problem:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/947950)

I added a me too to the bug.

---

### Post by nwadams on 2012-03-06
> **Script Warlock said:**
> i got dual monitors setup but nvidia vc keep on crashing unity 3d or vice versa so i use instead the unity 2d and there i found it stable and have not seen the unity panel on the second monitor.

how did you get the dual monitor setup to only display one launcher. Aside from the crashing that is.

---

### Post by Script Warlock on 2012-03-06
> **nwadams said:**
> how did you get the dual monitor setup to only display one launcher. Aside from the crashing that is.
just login to ubuntu 2d.

---

### Post by nwadams on 2012-03-06
> **Script Warlock said:**
> just login to ubuntu 2d.

what about in unity 3d? (I have intel graphics so i don't have crashing problems)

---

### Post by Script Warlock on 2012-03-06
we're still using beta and very prone to bugs and crashes. intel try and observe

---

### Post by nwadams on 2012-03-06
> **Script Warlock said:**
> we're still using beta and very prone to bugs and crashes. intel try and observe

haha thanks. I will do.

---

### Post by meborc on 2012-03-08
I added myself to the bug. I understand why they implemented the "resistance", it is so that it would be easier to hit the target when you are trying to use Unity bar on the right side monitor. But it is the number one major annoyance I have with 12.04

EDIT: i was able to get "normal" edge movement back by setting:

Launcher Reveal Edge Responsiveness  = 1
Launcher Reveal Pressure             = 1
Launcher Edge Stop Overcome Pressure = 1
Pressure Decay Rate                  = 1
Edge Stop Velocity                   = 1 

in ccsm

I do not know which one did it and I dont care :) I have my normal edge crossing speed back

---

### Post by everytimeref on 2012-03-08
> **Script Warlock said:**
> @everytimeref, unity development is just a year old?... that means too young to cope your wants..

But if we don't say what we like and need how can we ever expect that functionality?

and to be fair, I made a point of saying that I like Unity. 

Talking about things on a forum is a why of finding out if others agree with your poin of view before you take things to the developer.

---

### Post by Aenima99x on 2012-03-08
> **meborc said:**
> I added myself to the bug. I understand why they implemented the "resistance", it is so that it would be easier to hit the target when you are trying to use Unity bar on the right side monitor. But it is the number one major annoyance I have with 12.04

EDIT: i was able to get "normal" edge movement back by setting:

Launcher Reveal Edge Responsiveness  = 1
Launcher Reveal Pressure             = 1
Launcher Edge Stop Overcome Pressure = 1
Pressure Decay Rate                  = 1
Edge Stop Velocity                   = 1 

in ccsm

I do not know which one did it and I dont care :) I have my normal edge crossing speed back

I left all defaults and only changed the stop velocity to 10.

---

### Post by nwadams on 2012-03-08
go vote here:
[http://www.omgubuntu.co.uk/2012/03/poll-multi-monitor-launchers-in-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/03/poll-multi-monitor-launchers-in-ubuntu-12-04/)

---

### Post by meborc on 2012-03-09
> **Aenima99x said:**
> I left all defaults and only changed the stop velocity to 10.

Yes, it seems the stop velocity is the main variable :) good to know

> **nwadams said:**
> go vote here:
[http://www.omgubuntu.co.uk/2012/03/poll-multi-monitor-launchers-in-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/03/poll-multi-monitor-launchers-in-ubuntu-12-04/)

done that. (two monitors, one launcher)

What about having two launchers, BUT having different apps, shortcuts etc on each?

---

### Post by spivee69 on 2012-03-14
Thanks meborc, that makes things much better. Now all I need is a way to define primary vs secondary monitors.

> **meborc said:**
> I added myself to the bug. I understand why they implemented the "resistance", it is so that it would be easier to hit the target when you are trying to use Unity bar on the right side monitor. But it is the number one major annoyance I have with 12.04

EDIT: i was able to get "normal" edge movement back by setting:

Launcher Reveal Edge Responsiveness  = 1
Launcher Reveal Pressure             = 1
Launcher Edge Stop Overcome Pressure = 1
Pressure Decay Rate                  = 1
Edge Stop Velocity                   = 1 

in ccsm

I do not know which one did it and I dont care :) I have my normal edge crossing speed back

---

### Post by verlyn13 on 2012-03-15
Still no work around for getting rid of the unwanted launcher in the middle of the screen without reverting to 2d?  This multiple launcher thing is a ridiculous idea and waste of desktop space.

---

### Post by DavidSommen on 2012-03-17
I use Precise Pangolin and have recently connected my computer to my TV via hdmi out. This way, ubuntu recognises my tv as a second monitor and now I can watch fullscreen movies via vlc om my tv.

However, when someone is working on the computer using the (first) computer monitor, the top panel and unity launcher are visible on the second monitor on top of the fullscreen video.

example:

I start vlc, open a movie and drag it to my tv (second monitor) and set it to fullscreen. It starts playing perfectly on my tv (sound also via hdmi)

My girlfriend wants to check her mail on the computer and opens a web browser. On the TV, the movie keeps playing fine, but the unity top panel and launcher pop up OVER the movie. This is quite annoying.

I must add that in Oneiric, I had the same problem, although there were no two launchers, so only the top panels revealed itself on top of the movie. So I don't think it's a bug exclusive to Precise.

---

### Post by ppd on 2012-03-17
@DavidSommen:

You are probably talking about this bug:

[https://bugs.launchpad.net/unity/+bug/734908](https://bugs.launchpad.net/unity/+bug/734908)

You can add yourself to the affected users and follow the progress...

---

### Post by DavidSommen on 2012-03-18
> **ppd said:**
> @DavidSommen:

You are probably talking about this bug:

[https://bugs.launchpad.net/unity/+bug/734908](https://bugs.launchpad.net/unity/+bug/734908)

You can add yourself to the affected users and follow the progress...

Thanks for your reply. I found that it is actually this bug:

[https://bugs.launchpad.net/unity/+bug/907464](https://bugs.launchpad.net/unity/+bug/907464)

that is wrongfully marked as a duplicate of the bug you are referring to. The behaviour is different in the sense that the launcher and top panel only reveal when the focus is brought to another application (for instance a web browser or office app).

---

### Post by ppd on 2012-03-18
Yes, as you can see in my bug comment (ppd) I thought the exactly same, but there was no further activity in this particular bug report...

---

### Post by DavidSommen on 2012-03-22
I subscribed myself to this bug:

[https://bugs.launchpad.net/unity/+bug/954446](https://bugs.launchpad.net/unity/+bug/954446)

I hope they will look into it at some point, because it's a real bugger :)

---

### Post by ubuntu27 on 2012-03-22
Before it turns in to a bigger aurgument...

It has been decided that the there will be only ONE Unity Launcher in Dual Monitor setep.

But, fortunatelt for some of us, it will be an *option* to add a Unity Launcher to the second monitor if desired.

[Ubuntu 12.04 Multi-Monitor Launcher Behaviour Decided]("http://www.omgubuntu.co.uk/2012/03/ubuntu-12-04-multi-monitor-to-be/")

---

### Post by DavidSommen on 2012-04-11
I wonder if anyone is actually looking after this bug. Perhaps it has real low priority, which is understandable. But its importance is still undecided on launchpad. If you are affected, please mark yourself as such.

[https://bugs.launchpad.net/unity/+bug/954446](https://bugs.launchpad.net/unity/+bug/954446)

---

### Post by cariboo on 2012-04-11
In your screenshot in the bug, it looks like you have other problems as well, it looks like you don't have the resolution on the tv set properly, or is that just a problem with the screenshot?

Are you actually watching the movie in full screen mode, or maximized?

---

### Post by DavidSommen on 2012-04-11
> **cariboo907 said:**
> In your screenshot in the bug, it looks like you have other problems as well, it looks like you don't have the resolution on the tv set properly, or is that just a problem with the screenshot?

Are you actually watching the movie in full screen mode, or maximized?
I don't know if this is a problem with the screenshot, the resolution seems te be set properly if watched on the television. It's a HD 'ready' (full support only for 720p I think) television and if I set the resolution on 1920x1080p some of the image 'fell off' the screen. So I adjusted the resolution to the next one available, 1366x768.

Following to your post, I tried the HD resolution, and it does seem to work now. It didn't work a few weeks ago - this is probably a bug that is solved. 

The problem with the top panel is still present, however...

I do watch the movie in full screen mode.

---

### Post by DavidSommen on 2012-04-11
What I notice now, after switching the resolution of my tv back to HD (1920x1080), almost every application I open, via terminal, launcher or otherwise, opens up on the 'wrong' monitor (my tv). It seems the applications open on the monitor with the highest resolution, even though they are not actually the primary monitor.

---

### Post by ubuntu27 on 2012-04-11
> **DavidSommen said:**
> ...almost every application I open, via terminal, launcher or otherwise, opens up on the 'wrong' monitor (my tv)...

Open **Display** Settings, and try changing the primary display by _dragging_ the Display icons. And then click on APPLY.

Play with that settings and see if it gets fixed.

---

### Post by DavidSommen on 2012-04-12
> **ubuntu27 said:**
> Open **Display** Settings, and try changing the primary display by _dragging_ the Display icons. And then click on APPLY.

Play with that settings and see if it gets fixed.

Thanks for your reply. Dragging the display icons (I assume you mean the coloured rectangles that represent the different monitors) does not seem to fix this issue. Sometimes the applications open up on the right monitor, but not all the time. I then have to use the workspace switcher to drag them to my monitor. If I revert to the lower resolution on my tv, the problem with the applications seems te be solved, but the black rectangle that notifies you of changes in your wired/wireless connection or new mail in thunderbird etc. always appears on the wrong monitor, which is also annoying.

I can't find a real, obvious setting to make the computer monitor a 'primary' monitor. Perhaps this will be fixed in the next version of unity? Or should I file a bug report?

---

### Post by NHclimber on 2012-04-12
The notion of what constitutes the "primary" display is complicated and varies by driver/DE.
What is the output of xrandr?
Is the TV a permanent connection or something you want to hook up every so often?
What graphics card is this on?

---

### Post by DavidSommen on 2012-04-12
> **NHclimber said:**
> The notion of what constitutes the "primary" display is complicated and varies by driver/DE.
What is the output of xrandr?
Is the TV a permanent connection or something you want to hook up every so often?
What graphics card is this on?
```
sommen@sommen:~$ xrandr
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     72.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   640x350        70.1  
HDMI-0 connected 1366x768+1280+179 (normal left inverted right x axis y axis) 640mm x 360mm
   1920x1080      50.0 +   24.0  
   1920x1080i     25.0  
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  

```
The television is permanently connected. My graphics card is an onboard ATI Radeon HD 3300 on a AMD 790GX chipset.

---

### Post by NHclimber on 2012-04-12
I don't know for certain if the ati restricted driver is randr 1.3 but if so you can set the primary attribute with
```
xrandr --output VGA-0 --primary
```

So if you use the mouse to launch from the dash, the app shows up on VGA-0, right?
Under what circumstances do apps show up on the HDMI output that you haven't specifically dragged there? Not counting of course the bug with unity panel ;)
Probably if you have the focus on an app on the TV and you alt+f2 and run an app,right? When else?

---

### Post by DavidSommen on 2012-04-13
> **NHclimber said:**
> I don't know for certain if the ati restricted driver is randr 1.3 but if so you can set the primary attribute with
```
xrandr --output VGA-0 --primary
```

So if you use the mouse to launch from the dash, the app shows up on VGA-0, right? Under what circumstances do apps show up on the HDMI output that you haven't specifically dragged there? Not counting of course the bug with unity panel ;)

The behaviour seems completely random to me. If I for instance start evince from the dash with my mouse, it shows up on VGA-0. If I start eog the same way, it shows up on HDMI-0 - even though both applications fit in both resolutions. If I drag eog to VGA-0, then close it and start it again, it always shows up on HDMI-0 again...
> 
Probably if you have the focus on an app on the TV and you alt+f2 and run an app,right? When else?
I have to say I almost never run an app that way, most of the time I just use the unity launcher and my mouse. The focus is almost always on VGA-0. I normally do not deliberately run programs on the TV, apart from VLC, when someone wants to see a movie via the hdmi cable. I might use it some time for watching photos and stuff but I haven't done that before.

The xrandr --output VGA-0 --primary does not seem the fix the issue...

Again, if I downsize the resolution for the TV, it seems to be fixed, more or less (apart from the black notify rectangle).

Thanks for your effort :)

---

### Post by NHclimber on 2012-04-13
> **DavidSommen said:**
> The behaviour seems completely random to me. If I for instance start evince from the dash with my mouse, it shows up on VGA-0. If I start eog the same way, it shows up on HDMI-0 - even though both applications fit in both resolutions. If I drag eog to VGA-0, then close it and start it again, it always shows up on HDMI-0 again...
[...]
Again, if I downsize the resolution for the TV, it seems to be fixed, more or less (apart from the black notify rectangle).


The reason this is happening with eog is that it's starting at the default window position and then binding to the monitor at the window's position. The default window position is *centered* in the virtual screen (which is why it shows up when the HDMI output is set to a higher resolution than your monitor -- the center of virtual screen 0 is now over on the HDMI).

This *should* be trivially controllable by compiz -- after all, window placement is exactly what a window manager is supposed to do -- but the Place plugin has been ridiculously broken.
[https://bugs.launchpad.net/unity/+bug/874146](https://bugs.launchpad.net/unity/+bug/874146)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/930660](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/930660)
<I'm sure there are other duplicates in there too!>

*Just* reported ([https://bugs.launchpad.net/ubuntu/+source/unity/+bug/930660/comments/10](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/930660/comments/10)) that the most recent compiz update fixed this problem (so that windows are actually placed on the same monitor as the pointer) but others here have been posting that compiz has been broken for them with latest updates
[http://ubuntuforums.org/showthread.php?t=1957518](http://ubuntuforums.org/showthread.php?t=1957518)
[http://ubuntuforums.org/showthread.php?t=1957980](http://ubuntuforums.org/showthread.php?t=1957980)

Edit: also you can use wmctrl to flip windows to the 'other' monitor.  Check out this thread [http://ubuntuforums.org/showthread.php?t=1045417](http://ubuntuforums.org/showthread.php?t=1045417)

---

### Post by rburkhal on 2012-04-14
The fix for this is really easy!  
After reading some of the post and one person mentioning to use the CCSM to change the Edge Stop setting.

1) I entered Unity in the filter, 
2) selected Experimental tab, 
3) then set the "Edge Stop Velocity" to 1 and 
4) changed "Launcher Monitors" to "Primary Desktop".  

Problem solved.  Then I changed "Hide Launcher" to Autohide in the Behaviour tab.  Now I have Unity only appearing when I use the Super command key!  Great! Love it!

Hope this helps.

---

### Post by DavidSommen on 2012-04-15
> **rburkhal said:**
> The fix for this is really easy!  
After reading some of the post and one person mentioning to use the CCSM to change the Edge Stop setting.

1) I entered Unity in the filter, 
2) selected Experimental tab, 
3) then set the "Edge Stop Velocity" to 1 and 
4) changed "Launcher Monitors" to "Primary Desktop".  

Problem solved.  Then I changed "Hide Launcher" to Autohide in the Behaviour tab.  Now I have Unity only appearing when I use the Super command key!  Great! Love it!

Hope this helps.
This seems to fix neither of my issues. It seems that similar settings can also be made in system settings -> Displays?

---

### Post by DavidSommen on 2012-04-22
The appearing top panel is still an issue. Precise Pangolin will be released in a few days. Will it be fixed by then?...

---

