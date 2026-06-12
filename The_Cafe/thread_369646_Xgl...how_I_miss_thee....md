---
title: "Xgl...how I miss thee..."
date: 2007-02-24
forum: The Cafe
---

### Post by 4KvRMU7Nnv on 2007-02-24
This thread is not exactly what the title suggests.  I know it's still possible to get Xgl working and running and it is still used by a significant portion of linux users everywhere.  The point I'm trying to make is this: Xgl is losing popularity to the supposedly "faster" and "safer" Aiglx.  I am distressed by this because I have found that Xgl has always been faster than Aiglx or native Nvidia compositing on my Nvidia GeForce4 440 64M video card.  The days of Xgl are soon to be over, I fear, and the only hope for salvation is to wait for Xegl!  Don't get me wrong, Aiglx isn't all bad.  It works moderately on my computer but it is nothing compared with the blazing speed of Xgl.  :(

---

### Post by spockrock on 2007-02-24
I really cant see the speed difference......... I know the benchmark tool is at an even 60fps, on aiglx, and on xgl its at like 300 both, but xgl uses more memory then aiglx,  :\  thats the reason why I use that and or nvidia......

---

### Post by 4KvRMU7Nnv on 2007-02-24
interesting...It doesn't use hardly any memory for me...like 5 Mg at most at the most intensive point...CPU useage is also spectacular... at its most wobbly, 3d graphical intensity, Xgl never even reaches 30%.  And my computer is nothing amazing.  Athlon64 3000+ processor and i only have a 64Mb nvidia graphics card.  AND in addition to this, I can play xmoto at full speed.  I don't even notice the slowdown which was abundantly apparent with Aiglx (it would lag for a couple of secconds and run jerkily).  

Another thing, In addition to useing Xgl, i also use the version of compiz in the universe repository because it is the most stable.  It never crashes...ever.  And the effects are much smoother.  Overall, if you aren't in love with messing around with beryl or the latest compiz, go with the one in the repos because it is the most stable and efficient.  believe me....I have literally tried all of the combinations possible and ive always come back to this.  I will list the different possibilites in order from slowest to fastest here:

Beryl+Native Nvidia
Latest Compiz+Native Nvidia
Beryl+Aiglx
Latest Compiz+Aiglx
Stable Compiz+Aiglx
Beryl+Xgl
Latest Compiz+Xgl
Stable Compiz+Xgl <------USE THIS!!!!!!

It sort of forms a pattern :)  Anyway, seriously, I am completely content with my compositing.   If you have a similar graphics card, try it and you will be too!  It is for this reason I am sad that Xgl is dying out.... :'(

---

### Post by manmower on 2007-02-25
> **d3br074 said:**
> 
Beryl+Native Nvidia
Latest Compiz+Native Nvidia
Beryl+Aiglx
Latest Compiz+Aiglx
Stable Compiz+Aiglx
Beryl+Xgl
Latest Compiz+Xgl
Stable Compiz+Xgl <------USE THIS!!!!!!
Thanks for that list, I had been looking for something like this.
So you are implying you can use AIGLX with the NVIDIA drivers instead of their built-in AIGLX-type extension?

---

### Post by timpino on 2007-02-25
On a complete side note: I've been trying to get it to work on my Inspiron 8200 with a 440go 64MB, HOW did you do it? Searching around All I find is how to do it on newer hardware and/or on desktops...

Nice that you took the time to benchmark! :)

---

### Post by 4KvRMU7Nnv on 2007-02-25
yes is inspiron an nvidia card?  If so, it should work.  Install the 8776 driver from the repository and follow the instructions from ubuntuguide.org.  Don't install compiz from the gandalfn repo though, just use the one built in and then make a script /usr/bin/thefuture and put the following inside of it:  

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

put /usr/bin/thefuture in your sessions startup and you'll be good to go.  On a side note, i did get that weird, shift+backspace glitch that restarts X but this is easilly fixable with another script.  inside of it put:

#!/bin/bash
xmodmap -e "keycode 22 = BackSpace Delete"

save as whatever you like, and put it in the startup as well.  With all this done, most say just restart the X server, but I say restart the whole computer becuase, well, you have a whole new X server running on top of your current one...i think that deserves a restart.  after this, you should be in your new glorious Xgl session by default.  One thing, though, the cube and wobbly windows won't be enabled by default and there isn't a little try icon like with gandalfn's compiz or with beryl.  There is, though, a wonderful tool called gconf-editor.  Type "gconf-editor" into a terminal, or find it under "system tools" on the main menu.  Go to Apps>Compiz>General>allscreens>options then edit the "active plugins" section.  Add cube, rotate, wobbly  IN THIS ORDER [otherwize they won't work and you will be mystified] put them in this order exactly:

gconf, decoration, wobbly, fade, minimize, move, place, dbus, resize, cube, switcher, rotate, scale

Individual customization for each plugin is availiable under the "plugins" section under "compiz"

Hope this helped.  OH as a side note, i recently learned that instead of useing metacity borders that sometimes have resizing issues on maximization and such, you can use the old compiz window borders instead.  They are beutiful and work at blinding speeds simply goto Apps>gwd and uncheck "use_metacity_theme" and they will change automatically.

---

### Post by bastiegast on 2007-02-25
> **d3br074 said:**
> This thread is not exactly what the title suggests.  I know it's still possible to get Xgl working and running and it is still used by a significant portion of linux users everywhere.  The point I'm trying to make is this: Xgl is losing popularity to the supposedly "faster" and "safer" Aiglx.  I am distressed by this because I have found that Xgl has always been faster than Aiglx or native Nvidia compositing on my Nvidia GeForce4 440 64M video card.  The days of Xgl are soon to be over, I fear, and the only hope for salvation is to wait for Xegl!  Don't get me wrong, Aiglx isn't all bad.  It works moderately on my computer but it is nothing compared with the blazing speed of Xgl.  :(

So what's the problem? Just stick with Xgl if you like it so much. It's not dying, from what ive heard aiglx isn't even supported for ati users.
And for a vast majority of users aiglx is faster, has a smaller memory footprint and doesn't require you to start another X server to play open gl games so from that PoV theres nothing wrong with that trend. But still, what makes you think Xgl is dying?

---

### Post by timpino on 2007-02-25
thanks a million for the reply, Finally I can have the cube! :D

---

### Post by 4KvRMU7Nnv on 2007-02-25
why do i say that Xgl is dying?  I think it is dying because everyone is moving toward Aiglx.  I'm afraid that people will eventually stop caring for xgl because they will only want to work on Aiglx because it supposedly works better.  

Another thing, When I installed Xgl, my Super Key got unmapped somehow.  So i can't do the Zoom plugin or the Annotate plugin becuase they both require the use of the Super Key.  If anyone knows how to remap this key please tell me! thanks!

**EDIT**  

I found out how to fix the super button.  Go to System>Preferences>Keyboard>Layout Options>Alt/Win key behavior then click "Super is mapped to the Win-keys (default)" even if the "Default" radio button is already checked.  Then activate Zoom and Annotate in the plugins section of Gconf and you'll be good to go!

---

### Post by BarfBag on 2007-02-25
Last time I used XGL was when it first came out.  I ditched it because of how much memory it hogged.  I'm sure they've tweaked it and improved the performance, but if I have the need for candy - I use AIGLX + Beryl.  Even that occasion is rare, though.

---

### Post by bastiegast on 2007-02-25
> **d3br074 said:**
> why do i say that Xgl is dying?  I think it is dying because everyone is moving toward Aiglx.  I'm afraid that people will eventually stop caring for xgl because they will only want to work on Aiglx because it supposedly works better.  

Another thing, When I installed Xgl, my Super Key got unmapped somehow.  So i can't do the Zoom plugin or the Annotate plugin becuase they both require the use of the Super Key.  If anyone knows how to remap this key please tell me! thanks!

Can't help you on that, but appeareantly for most people AIGLX does function better and I think by the time XGL dies(if ever) AIGLX and compiz/beryl have matured enough so it will function better for you too. If not, your probably not the only one with aiglx problems so then xgl probably won't just die.

---

### Post by 4KvRMU7Nnv on 2007-02-25
yeah they have fixed it, my fan does not ever turn on becuase of strain from Xgl.  Only time it becomes a problem is with games slightly.  THen the fan turns on.

---

### Post by spockrock on 2007-02-25
oh I may re-run XGL, where did you get your xserver-xgl package from d3br074?

I am really interested if xgl memory leak has been plugged, my version;
Installed: 7.0.0.git.20060725-0ubuntu2.1

---

### Post by 4KvRMU7Nnv on 2007-02-25
There is a memory leak?  Hmm... I never noticed a problem. I am using the 0ubuntu2 version so the version below yours...ive never noticed a problem though.  i'll look for an updated version although i don't see whats wrong with this one.

---

### Post by spockrock on 2007-02-25
hmm maybe I am wrong then, but I do notice a significant difference in memory usage. ok, I am gonna try it again... :\

edit tried ti again, saw no visable speed difference after I got around the white screen of death, and also under xgl my keyboard frglx's up, >_< sticking with nvidia and aiglx.

---

### Post by 4KvRMU7Nnv on 2007-02-25
interesting, the keyboard shouldn't have been TOO much messed up, for me the only thing was the Super key, but that was easily fixable.  I guess the speed I am talking about is it just seems smoother and happier...like the windows seem more responsive, the switcher seems more intuitive and natural.  It just seems "meant to be" with Xgl and not with Aiglx.  Don't knwo how else to explain it.  undoubtedly people are having much better expierences with aiglx than Xgl but xgl is still valid and that is why i wish feisty would offer an option for both.

---

### Post by igknighted on 2007-02-25
> **d3br074 said:**
> interesting, the keyboard shouldn't have been TOO much messed up, for me the only thing was the Super key, but that was easily fixable.  I guess the speed I am talking about is it just seems smoother and happier...like the windows seem more responsive, the switcher seems more intuitive and natural.  It just seems "meant to be" with Xgl and not with Aiglx.  Don't knwo how else to explain it.  undoubtedly people are having much better expierences with aiglx than Xgl but xgl is still valid and that is why i wish feisty would offer an option for both.

Not a great example, but I have noticed the same (my NVIDIA card is light years behind my ATI card though...).  With nvidia/beryl I got 60 FPS max.  With ATI/xgl I get over 500 FPS.  Due to a new mobo (going pci-e) I am getting a new nvidia card however, so sometime later this week I'll report how that goes.

---

