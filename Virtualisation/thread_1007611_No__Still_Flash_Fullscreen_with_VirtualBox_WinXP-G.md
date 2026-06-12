---
title: "No / Still Flash Fullscreen with VirtualBox WinXP-Guest"
date: 2008-12-10
forum: Virtualisation
---

### Post by asdir on 2008-12-10
Hey guys,

can anyone tell me how to watch fullscreen flash videos (e.g. youtube) in a virtualized Windows XP under Intrepid? The virtualization software is VirtualBox.
As soon as I turn to fullscreen, the video simply stands still. Otherwise flash reacts as expected: Esc brings me back to normal view, etc.

[In case anyone questions why I don't watch videos under Ubuntu itself: I need certain network services to watch certain videos (e.g. Hulu) witch cannot be provided under Ubuntu yet.]

Thanks for any advice on that problem.

---

### Post by dandandan on 2009-03-07
I have the same Problem, did you find a Solution? If so please share :)

---

### Post by StopSpazzing on 2009-03-07
Have you tried it in firefox and IE? Maybe its browser specific even tho they use the same flash? 

Im testing possibilies right now.

---

### Post by StopSpazzing on 2009-03-08
Sorry for replying to my post but I cant duplicate your flash issue. 
On a fresh xp pro sp3 install on xubuntu host machine, works fine for firefox and IE in full screen on youtube and other sites. I have ENABLED graphics acceleration as well as dedicated the max allowed, 128 MB's of graphics ram, to the machine.

Could you please post your computer specs as well as your guest xp version you are using and virtual box settings??

---

### Post by dandandan on 2009-03-08
I have tried with IE and firefox, with and without 3d accel and VT thingie.
What specs do you want to know exactly?
Guest System is Windows XP professional with sp3 and all patches.
Host System is Ubuntu 8.10 with latest patches running with nvidia gfx card.
I tried with compiz and metacity.

P.s. i should mention that i dont mean putting the whole guestos in fullscreen but put the flashvideo in fullscreen mode, did you mean the same? :)

---

### Post by asdir on 2009-03-08
Yep, that's what I meant. If I find time later, I will try to give you my specs, but afair I used compiz under XP SP3 virtualized on my Intrepid-box. My driver is also nvidia 177.82, flash is the currently newest.

---

### Post by Therion on 2009-03-08
I'm confused. I have no problem at all watching hulu vids with fullscreen using Ubuntu; I'm doing it right now.

What is it that is preventing you from being able to do the same exactly?  Do you get an error message or something because it works effortlessly for me.

---

### Post by dandandan on 2009-03-08
I dont know about hulu, does not let me in due the fact that i am not an american.
Try for example youtube.com. When i watch a youtube video and i press the lower right button to make the video bigger, it goes bigger but the frame freezes. No error msg or anything just a froze frame, sound continues.

i can use xvidcap to make a small video if that helps somebody.

edit: i just tried it on my Laptop too with windows xp as guest and Ubuntu 8.10 32bit as Host -> same bug

---

### Post by StopSpazzing on 2009-03-08
My next guess would be your settings for virtualbox are different. Could you list the General settings you use...

These are mine:
Base Memory: 512
Video Mem: 128
ACPI: Enabled
IO APIC: DIsabled
VT-x/amd-v: Disabled
Nested Paging: Disabled
PAE/NX: Enabled
3D acceleration: Enabled


I am currently updating windows guest box to the latest updates to see if its the guest box and not the virtualbox settings.

And yes I know what you meant. My host resolution is 1280x1024 and my guest box is 800x600. I fullscreened the flash video on youtube in both IE and Firefox and I dont get freezing, just plays fine.
My only guess right now would be you are not giving the system enough base memory and/or video memory. It's unfortunate that the max video memory you can dedicated to the box is 128. :(



To watch hulu from another country, use a US proxy. :) A fast proxy...I would say Tor but its going to be laggy as heck, even if you can find US IP to connect to.

---

### Post by dandandan on 2009-03-08
I tried it with the same Options as you, still same Effect.
However, when i disable Hardware Acceleration in the Flash Settings, the Video plays fine.

So i guess i have to be without hw Accel.

---

### Post by StopSpazzing on 2009-03-08
Well, seems I found the problem. Guest Additions. I updated everything to the latest and worked just fine...so I decided to install guest additions, then it started freezing on youtube full screen. So, seems there is a bug they need to fix...you may want to report the bug if it hasnt already been reported.

---

### Post by dandandan on 2009-03-08
You are right, uninstalling the GAs fixes the Problem.

---

### Post by StopSpazzing on 2009-03-08
> **dandandan said:**
> You are right, uninstalling the GAs fixes the Problem.

:)

I would highly recommend you report the bug, telling them the problem and how to fix it...so that the next build it will be fixed. :)

Let me know if you are going to because If you wont I will.

---

### Post by dandandan on 2009-03-08
I have filled a Bug Report:
[http://www.virtualbox.org/ticket/3515](http://www.virtualbox.org/ticket/3515)

maybe you can "confirm" it there.

---

### Post by StopSpazzing on 2009-03-08
I have confirmed it and posted a link to this post.

---

### Post by quackeroni_pizza on 2009-08-02
That fixed it for me! Just disabling hw accel! Thanks.

---

### Post by mo.mashi on 2010-05-17
I have had the same issues. Installed latest guest addition and vbox ( 3.1.8 ). They do not solve the problems. Removing hardware acceleration will slow the video to a choppy speed on my pc which renders the full screen mode useless as far as I am concerned.

I would not hold my breath waiting for Sun to fix this bug (or any bugs in VBox - this thread was started in Dec 2008 and we're May 2010 as I write this reply). That's why I have figured out this little work around. It's a little ghetto and a little inconvenient but you won`t care if you want to watch a video in vbox badly enough (ex. if you don't trust the websites but want to watch certain types of videos or are running a proxy service to watch Hulu that installs software you don't trust etc etc).... 

You need to find the maximum zoom that would (in Firefox's full screen mode) allow you to see the video without loosing any of the image and the control bar (the line under the video that allow you to fast forward and set the volume). This varies depending on your monitor resolution and proportion. In my case, I found that for my 16:9 and 1920x1080 monitor, 280% for youtube (with some scrolling), 215% for another video website were good. I like my minimum zoom at 150%. The inbuilt firefox zoom function won`t allow you to be so precise. You need an extension from Mozilla Addons called Glazoom. Glazoom will allow you to key in the percentage of zoom you want. Once you`ve figure out the percentages you need, you can go to Glazoom's options menu and set exactly what percentages popup in the Glazoom menu in the status bar. For my zooms of 280%, 215% and 150% zoom percentages, I keyed in the options dialog: 2.8, 2.15 and 1.5 (zoom percentage divided by a hundred). You can also set the minimum zoom in the options menu, which I set to 150%. Unfortunately you cannot access the Glazoom menu from full screen as it is in the status bar, so you have to zoom to the level you want and then hit F11 and pan the video to the right position but this is still an improvement over Firefox`s native zoom functionality. When you're done with the video, hit F11 and select 150% (or whatever you set your minimum zoom at at) or go to another page and it will automatically revert to your minimum zoom.

This will allow you to see something very close to full screen flash without having to stop hardware acceleration (ie no choppiness). 

If some website put annoying adds next to the video, use Adblock Plus to get rid of the frame. If you use personas and the little sliver of color that sticks around in full screen mode is bothering you, choose a black or dark persona. If you find the scroll bars destracting, change their colors to black and dark grey. 

It's a little bit of a pain to setup but it works and becomes automatic once you have it setup.

---

### Post by wpl2010 on 2010-05-18
u can try install Guest additional at the devices there..

---

### Post by mo.mashi on 2010-05-18
> **wpl2010 said:**
> u can try install Guest additional at the devices there..

I have the latest (as of today, May 2010) VBox Guest Additions 3.1.8 running on the latest VirtualBox 3.1.8, they are  not helping with regards the flash full screen issue. Are they working for you?? Can you see Flash in full screen mode without having to disable hardware acceleration?

---

