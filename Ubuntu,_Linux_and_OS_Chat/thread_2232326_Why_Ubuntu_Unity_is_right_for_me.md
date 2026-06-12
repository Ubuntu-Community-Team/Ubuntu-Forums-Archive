---
title: "Why Ubuntu Unity is right for me"
date: 2014-07-01
forum: Ubuntu, Linux and OS Chat
---

### Post by smirnich on 2014-07-01
Hi! I have now tried KDE, XFCE, LXDE, Openbox, Cinnamon, Enlightenment etc. in various distros, but I always end up with Ubuntu Unity. Here's why:
- I really like how Unity handles workspaces and hotcorners. This lets me get back to my old OS X workflow (before Apple ruined it with Mountain Lion) with 4 workspaces and the right hotcorner to show the workspaces. I know plenty of Linux distros let me do this, but i like the Unity implementation best (the same in Mint Cinnamon doesnt feel as smooth on my laptop.)
- I love the global menubar (It saves precious screenspace on my low-resolution laptop. Plus, when apps are fullscreen I go to the left corner to close apps, right corner to choose workspace. Easy :)
- Font-rendering in Ubuntu is great by default compared to some other distros.
- Chrome is much faster than in Windows 8, which is actually the main reason why I use Linux on my laptop.
- The touchpad on my laptop works all the time in Linux, compared to Windows where two finger-scroll randomly stops working and sometimes the whole touchpad is unresponsive.

But I still have to dual-boot because:
- I can't get suspend to work on my laptop (Well, I actually can using the proprietary ATI driver, but that screws up other stuff.)
- I have not found a photo management that rivals ACDSee Pro in Windows. DigiKam seems to have the features, but it works too slow and crashes to often on my laptop.

Just wanted to give Unity some love :)

---

### Post by TheFu on 2014-07-01
So ... you must be the 1 guy that likes it. ;)

I tried using a Mac a few years ago for 2 weeks.  Didn't enjoy the experience at all. Things that are trivial on Linux weren't possible.  Samba shares didn't work (there was a bug with that release), the keyboard layout and shortcuts were just "wrong" ... but consistent. The entire time, OSX felt like "linux-lite" to me.  Dumbed down to prevent me from being efficient.

I despise Unity.  
20 yrs of GUI use has taught me certain things. Why should I need to change?
Plus, most of my desktops and systems run inside virtual machines, so Unity's demand for 3D accelerated GPUs is all-wrong for that use case.  VMs don't work will with high-end graphics requirements, yet.  With 14.04, Canonical has made it tolerable at a new install, but since 11.04 pushed Unity as the default, it has sucked for VM users.  Sucked is putting it kindly.  I've seen Core i7 machines brought to their knees due to Unity.  

Don't get me started about the "lens" tracking stuff. Purged off every machine. At installation time, I should be asked if I want any remote queries.  It isn't like everyday, all day, I want to shop on Amazon. Duh. Why have every search hit the internet? It certainly isn't to help performance.

So ... since 10.04, I've always loaded XFCE or LXDE and purged Unity.
Since 12.04, I've loaded "server" and added LXDE. That seemed to be the shortest way to a non-tracking, useable, desktop.

Photo management is tough. I travel more often than most people and take lots of photos - 100-300 per day.  Trusting any app to manage those photos just isn't too smart, IMHO.  I've read about corrupt DBs and how people have lost years of photos.  I use a simple layout based on yyyy/mm/event/ then push metadata into each photo directly with a perl script that used libexif (CPAN module interface, of course).  The plan is to shove tags into the Exif too and create a web service that can be queried by date, location, people, tag, genre, etc .... it gets complicated.  I think of it as plex server, but for photos and the photo metadata.

Suspend works on my netbook. I don't suspend VMs, since that defeats the purpose to me.

Anyway - I'm happy that 1 person likes Unity. Sure, there are more, but they all have a different use-case than me and most seem to come from a Mac-loving (Linux-lite) background. At least that has been my impression.

---

### Post by smirnich on 2014-07-01
Yeah, I am that one guy:D But you are right, a lot about what I like about Unity are things I am/was used to when I had a Mac. But I actually prefer Unity because it hides the "file" etc menu to save space (I know many disagree with me on this).

But I agree about the "lenses" and stuff. I only use the dash to search after applications I don't have in the dock.

Talking about photo management, I use ACDSee but I also use a logic folder structure and export metadata to the files, so there is no crisis if the database get corrupted.

---

### Post by TheFu on 2014-07-01
Just to be clear - I love that you can be happy with the same OS that I love too!  
The OS isn't the GUI and Linux is nothing if not flexible.  There is a place for everyone at this bar.

You can purge all the lenses from the system. There was a thread here about that last month. Canonical knows the power of "the default" and has been abusing it for many things recently.

I'll take a look at ACDSee - thanks for the pointer - though I will not run Windows for this, perhaps the features will provide a few ideas for a webapp.

---

### Post by smirnich on 2014-07-01
Choice is part of what makes Linux so great :)

---

### Post by craig10x on 2014-07-01
You're not alone in loving unity...believe me...you have PLENTY of company...actually, a large majority of people here love it too (including myself) it's just that those who don't are a fairly loud minority so you can sometimes get the impression from them that they are the majority (which they are not) if that makes any sense ;)

Anyway, after leaving windows i spent about a year on the mac (only leaving it because i didn't want to get locked into the high priced hardware) then discovered linux, ubuntu first and eventually migrated to linux mint (because i didn't care for the original layout of ubuntu) but once unity came along in 11.04 i was BACK TO STAY :D

It DOES have a VERY MAC LIKE FEEL and that's what i love about it...and really, it's just a Dock...so often, those who don't like docks are the ones that do not like unity...

---

### Post by buzzingrobot on 2014-07-01
Most online chatter about Linux interfaces, or anything else, for that matter, is motivated by frustration and anger, and that draws a very skewed picture of who really likes what.  So, it's nice to see a post from someone about something they actually like.

The differences between Linux interfaces are really small when we think about it:  Sometimes we click here, sometimes we click there. Enough variety is out there so we should all be able to find something useful. No interface design can please everyone, and designers know that when they make choices some folks will be unhappy.  C'est la vie.

---

### Post by robert107 on 2014-07-01
Cinnamon has every virtue you listed

---

### Post by smirnich on 2014-07-01
Does cinnamon have a global menubar like unity? If so, how do you turn it on? Some of what I'm not so fond of in cinnamon is the space wasted on window titles compared to unity where it is on the top line (when maximized).

and yeah, I agree that the differences are quite small, and I like most of the desktop environments I've tried :)

---

### Post by craig10x on 2014-07-01
Cinnamon does not have a global menu available as far as i know (though maybe the cinnamon fans can tell us different)....although actually, i turn it off in my systems settings (that new option they added)...i would leave it on but since doing so only puts the menus back into the window's title bars, it does not affect the top panel which still saves space when i am web surfing...which is exactly what i wanted (Canonical you are a genius with that feature)...but i certainly didn't mind the global menu feature and had no problems when i used it...

---

### Post by monkeybrain20122 on 2014-07-01
I like Unity too, you are not the only one. :)

---

### Post by /ADM on 2014-07-02
I tried to like it, even after a month but I just couldn't do it.  I hate (hate hate hate) my menu layout to be on the side, it's just ugly.  The app search takes too long to appear (with a horrible blurred background) and I dislike the way the menu bars of apps merge into the top bar (even when global menu is disabled) upon fullscreening them.

I also don't want my searches tracked nor the details of my apps, music, documents etc to be 'anonymously' sent.

I will always be an LXDE/Lubuntu lover, because it does not do any of the above ;)

---

### Post by craig10x on 2014-07-02
The unity bar can't be moved...that is true...however, you can shrink the icons and i think that looks a LOT better (i set them to 38 pixels for my 17" laptop screen)...you can play around to see what looks best to you...
As far as the online searches on the dash...well, that can be totally turned off by hitting the "off" button in the privacy section of system settings (it's under searches)...

And even when the online searches is on, it doesn't send your apps, music and documents at all to anyone...
Also, as of 14.10, online searches will be turned off by default...

---

### Post by buzzingrobot on 2014-07-02
...and the dock can be set to autohide.

Many people seem to think the indexing of /home --" apps, music, documents etc" -- amounts to "tracking" by Canonical. It isn't. Searching an index is much faster than searching a file system in real time, and searching file content in real time is very, very much slower.

---

### Post by TheFu on 2014-07-02
> **buzzingrobot said:**
> ...and the dock can be set to autohide.

Many people seem to think the indexing of /home --" apps, music, documents etc" -- amounts to "tracking" by Canonical. It isn't. Searching an index is much faster than searching a file system in real time, and searching file content in real time is very, very much slower.

Take a look at 'locate'. If full text search is needed, 'recoll' - though recoll is heavier.  'whatis' will help find tool names too.
Also, setting the PATH can be useful - then add tab-completion in the shell - amazing results.

Don't get me started on alt-F2 and setting up accel key combos inside the window manager.

---

### Post by buzzingrobot on 2014-07-02
> **TheFu said:**
> Take a look at 'locate'. If full text search is needed, 'recoll' - though recoll is heavier.  'whatis' will help find tool names too.
Also, setting the PATH can be useful - then add tab-completion in the shell - amazing results.

Don't get me started on alt-F2 and setting up accel key combos inside the window manager.

I was spoiled by some of the "personal information managers" on OS X that basically toss anything and everything you want into archives, index them, and allow their manipulation and analysis in a bunch of useful ways. So... on Linux, I dump anything I want to save into a folder and use Recoll to find things. This turns out to be almost entirely PDF's of web pages. Recoll indexes everything else in place.  It's a great tool.

---

### Post by mooreted on 2014-07-03
I guess I've just gotten used to having a dock. I'm not a big fan of the Dash, but I never use it anyway. All my apps are on the dock. As far as the dock being on the left side of the screen; my screen is wider than it is tall, so it makes sense to me. 

I like Unity, and I have tried Xfce, Lxde, Icewm, Openbox, Fluxbox, Cinnemon and probably a few others I can't remember. They all seem so 1990's to me. 

As far as applications melding with the status bar; I just never close applications. I'm not using a 10th of the RAM I have available, so I see no reason to close anything. Of course, I'm just a user not a developer. I don't have a workflow.

---

### Post by peterseaford on 2014-07-03
Hi 
mooreted i am just new at this and am about to order a gazelle .
I use windows at present and wonder how much ram you have on your computer

regards

peter

---

### Post by mooreted on 2014-07-03
> **peterseaford said:**
> Hi 
mooreted i am just new at this and am about to order a gazelle .
I use windows at present and wonder how much ram you have on your computer

regards

peter

I have 8 GB of RAM.

total       used       free     shared    buffers     cached
Mem:       8126512    7966116     160396      51732    1585816    3771024
-/+ buffers/cache:    2609276    5517236
Swap:      8336380      25788    8310592

So, with 4 applications running, I'm only using about 2.6 GB of ram.

---

### Post by deadflowr on 2014-07-03
> **mooreted said:**
> I have 8 GB of RAM.

total       used       free     shared    buffers     cached
Mem:       8126512    7966116     160396      51732    1585816    3771024
-/+ buffers/cache:    2609276    5517236
Swap:      8336380      25788    8310592

So, with 4 applications running, I'm only using about 2.6 GB of ram.

So you're part of this crowd
[http://ubuntuforums.org/showthread.php?t=2228236](http://ubuntuforums.org/showthread.php?t=2228236)
:D

---

### Post by smirnich on 2014-07-04
One more thing I really like about Unity (and cinnamon, KDE and.. Windows 8) is that you can "snap" windows when moving them to the left or right side of the screen.

And that chrome web apps get their own icon in the dock when I choose that they shall be opened in their own window. I use this with Kindle Cludreader and think it looks much better than just opening it in chrome.

---

### Post by mooreted on 2014-07-04
> **deadflowr said:**
> So you're part of this crowd
[http://ubuntuforums.org/showthread.php?t=2228236](http://ubuntuforums.org/showthread.php?t=2228236)
:D

Yay, finally, I am 1337.

---

### Post by monkeybrain20122 on 2014-07-04
> **smirnich said:**
> One more thing I really like about Unity (and cinnamon, KDE and.. Windows 8) is that you can "snap" windows when moving them to the left or right side of the screen.


I really don't care for 'snapping' windows and not sure what the point is when you can enable multiple virtual desktops. I would rather be able to move my window to another workplace by dragging it across with the wall or the cube's edge flipping (so I disable snapping in ccsm and use those instead)

---

### Post by smirnich on 2014-07-04
The point is to see multiple apps at once. I use it now when I'm working my way through a beginners book in Python programming. I snap the book reader to the left and gedit to the right, and I can read and write code simultaneously. For moving the window to another workspace, I rather use the default CTRL + ALT +SHIFT + left/right/up/down :)

---

### Post by monkeybrain20122 on 2014-07-04
> **smirnich said:**
> The point is to see multiple apps at once. I use it now when I'm working my way through a beginners book in Python programming. I snap the book reader to the left and gedit to the right, and I can read and write code simultaneously. For moving the window to another workspace, I rather use the default CTRL + ALT +SHIFT + left/right/up/down :)

I can see multiple applications with either the shift switcher or a hot corner with the scale addon. With snap you may be able to see just two windows in the same workplace. :)

---

### Post by buzzingrobot on 2014-07-04
> **monkeybrain20122 said:**
> I really don't care for 'snapping' windows and not sure what the point is when you can enable multiple virtual desktops. I would rather be able to move my window to another workplace...


Same here. It simpler for me to size and position windows. More often that not, snapping would happen when I don't want it.

I don't maximize windows, either. Windows that are alone on a workspace, like this brower, are usually centered at about 70 percent of horizontal screen space, with space above and below.

---

### Post by smirnich on 2014-07-04
Do you have a high resolution screen or do you just like to scroll?:p

---

### Post by buzzingrobot on 2014-07-04
> **smirnich said:**
> Do you have a high resolution screen or do you just like to scroll?:p

1920x1080. 

There isn't that much empty space above and below, maybe 50 pixels each. So, no more scrolling than usual.

Reading text spread out full screen is annoying.

---

### Post by deadflowr on 2014-07-04
I, too, dislike windows snapping, with mouse/dragging.
I disable those in ccsm > grid > corners/edges > set all to none.
I do, however, like the keybindings to snap the windows.
So, since I don't mind those, I keep grid enabled, otherwise I'd disable the plugin entirely.

---

### Post by brandelvalico on 2014-07-04
I don't dislike Unity in and of itself. I do have a few issues such as the unity bar not being movable. (If I wish to I should be able to) As well as the auto opt in to dashes. (Yes it is easy to shut off, I shouldn't have had to) Other then those small issues that are all easy to fix. (Installed Cairo Dock and use their GUI instead of Unity.) Dock is now where I like it. 

Have installed Ubuntu with Unity on several relatives computers though and left it default and they all love it. (as their tech support which is getting rare now that more and more of them are on Linux instead of Windows I still get to play with Unity on occasion. Still not my cup of tea but usable)

---

### Post by Elfy on 2014-07-04
What I find absolutely hilarious is that these are the sorts of discussions that most people would have when something is new ... not 3 years later :)

---

### Post by Apollo8 on 2014-07-04
Let me chime in too. I really like Unity. I think its a gorgeous UI. I also love Windows 8.1, but I have a lot of fun running Ubuntu as well.

---

### Post by deadflowr on 2014-07-04
> **Elfy said:**
> What I find absolutely hilarious is that these are the sorts of discussions that most people would have when something is new ... not 3 years later :)

Unity is a lot like green eggs and ham.
It took some folks time to realize they like it.
Insisting for quite some time they hate it, without much time using it( if they used it at all)

Of course, many others still hate green eggs and ham...

---

### Post by craig10x on 2014-07-05
Just love that deadflowr humor :mrgreen:

---

### Post by Deneb211 on 2014-07-06
Unity is pretty good, I only wish it was a little snappier :D

---

### Post by hbutt875 on 2014-07-08
> **mooreted said:**
> I guess I've just gotten used to having a dock. I'm not a big fan of the Dash, but I never use it anyway. All my apps are on the dock. As far as the dock being on the left side of the screen; my screen is wider than it is tall, so it makes sense to me. 

I like Unity, and I have tried Xfce, Lxde, Icewm, Openbox, Fluxbox, Cinnemon and probably a few others I can't remember. They all seem so 1990's to me. 

As far as applications melding with the status bar; I just never close applications. I'm not using a 10th of the RAM I have available, so I see no reason to close anything. Of course, I'm just a user not a developer. I don't have a workflow.

+1 I am also a big fan of Unty.Gnome classic,Cinammon and MATE etc look like Windows XP.I switched to Ubuntu 12.04 about a year ago.after using ubuntu I just love unity. Then I reinstall Windows 7 later (for games). About a month ago I decided to try ubuntu 10.04.. When I install ubuntu 10.04 I hate it. After 2 days I upgrade to 12.04 for unity. just love unity.

---

