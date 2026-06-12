---
title: "Set screen resolution without autodetection"
date: 2008-03-16
forum: Ubuntu Brainstorm
---

### Post by steve196 on 2008-03-16
Have all thinkable screen resolutions at all frequencies available in the screen resolution panel. The user knows what his monitor is capable of. The computer usually doesn't and it is extremely frustrating to be limited by its arbitrary choices. Also let the user determine if a dual monitor setup is there or not and what capabilities it should have, instead of trying to autodetect that.
Also stop the wear and tear of trying around with screen resolutions at startup (this is fairly new behaviour. Older versions do not do that). If King User said, that a particular setup works, the computer should just believe it and use it.

---

### Post by smartboyathome on 2008-03-16
I like the autodetection. It has only failed me once, and that was because the driver didn't support my screen resolution. If all resolutions were given, it could ruin the resolution more than help it. Ubuntu aims to be simple, this is more complex (especially refresh rates).

---

### Post by steve196 on 2008-03-17
The current status quo is too complex for me, and i am quite good at computers. Taking autodetection out would make it estremely simple: Choose your desired resolution, choose your desired refresh rate, finished. I cannot see, how things can get any simpler than that.

The new alpha has the stupidest possible solution. It has two tools for screen resolution, one in preferences, the other in administration. They ignore settings set by each other and if you use one after the other, the screen gets stuck in weird settings, that have little to do with those you set with either tool. KISS should be the principle here. It cannot be that difficult to give an option to turn autodetection off (which makes the second tool unnecessary)  or at least, if it has to be split in some awkward way between two tools, to use compatible ones.

---

### Post by qamelian on 2008-03-17
The problem is not necessarily the auto-detection. Even though your hardware might handle a certain resolution, the driver you are using might not. For example, the open-source nv driver will not allow me to use a resolution higher than 1280 x 1024 on my widescreen LCD monitor. If I change the xorg.conf file to get the desired resolution, I'm left staring at the tty, because the nv driver just doesn't handle the specific resolution my monitor defaults to. Switching to the Nvidia driver allows the full range of resolutions. The auto-detection seems fine on most systems i've used, but tends to frustrate some people because it tries to only show you resolutions that your driver is comfortable with.

---

### Post by steve196 on 2008-03-17
Nope, definitely not the driver. This is not the place to normally tell personal stories, but i had 1600x1200@85 before i tried attaching a second monitor (also easily capable of 1600x1200@85). The second monitor made the system go down to 640x480, so i took it away. Since then it is stuck at 640x480@85 as the only option, even although the monitor is correctly described in xorg.conf.

The point is: Autodetecting monitors is and always was and probably always will be a messy business in Windows and Linux alike. Just look at any computer related forum for proof. In Windows there are easy ways around that. In Ubuntu there aren't.

---

### Post by smartboyathome on 2008-03-17
> **steve196 said:**
> Nope, definitely not the driver. This is not the place to normally tell personal stories, but i had 1600x1200@85 before i tried attaching a second monitor (also easily capable of 1600x1200@85). The second monitor made the system go down to 640x480, so i took it away. Since then it is stuck at 640x480@85 as the only option, even although the monitor is correctly described in xorg.conf.

The point is: Autodetecting monitors is and always was and probably always will be a messy business in Windows and Linux alike. Just look at any computer related forum for proof. In Windows there are easy ways around that. In Ubuntu there aren't.

That might of happened to you, but it would mess up Nvidia users, who get the NV driver by default, and when they try to set their resolution they get a broken X. I think I know your problem, dual monitors are more complicated, and you have to stick with what the highest for both is. If one is full screen and one is wide, for example, this might happen.

---

### Post by steve196 on 2008-03-17
Nope this is not about dual monitors. In my personal case, the second monitor is gone, just the problem isn't (and, as i wrote, they were both capable of the desired resolution). Furthermore my personal case is irrelevant, since this is not the support forum. This stuff happens everywhere.
The general problem, that Ubuntu has no workarounds in place for the case of misdetection.
Putting the limits of NV in or, better,  a warning message when they are exceeded is another thing because the properties of NV are not "detected" some way. They are known. 

"It just works" should be a goal, not a presupposition.

---

### Post by smartboyathome on 2008-03-17
Though "the user makes it work" wouldn't always work, as stated above some open source drivers (which Ubuntu ships with) don't support the desired resolution, and this would make support for those a nightmare.

---

### Post by steve196 on 2008-03-18
It is frustrating when people do not read what they reply to.

That said, there should be a middle way.
I am quite good at computers and this one single  issue defeated me and made me switch back to win2k after two years. 
If just skipping autodetection is the end of the world, then Ubuntu should at least give the contents of xorg.conf priority over the stupid gnome resolution changer. Then at least an advanced user, who knows that xorg conf exists, is editable and has a manpage with good information, can repair things if they go wrong.

---

### Post by smartboyathome on 2008-03-18
You can already do something like that with dpkg-reconfigure xserver-xorg, can't you? That is how I always repair broken xservers.

---

### Post by 23meg on 2008-03-18
The "stupid gnome resolution changer" got replaced in Hardy.

[http://bryce.homelinux.org/drupal/display-config-1](http://bryce.homelinux.org/drupal/display-config-1)

---

### Post by steve196 on 2008-03-18
Of course i  tried "sudo dpkg-reconfigure xserver-xorg" just as i tried all other commonly recommended solutions. 
It rewrites xorg.conf, which helps nothing if xorg.conf is overruled by something else.
I know the new tool from a wubi installation i had and it is a horrible mess. To be honest, i tried it with two monitors on, which might have overwhelmed it, but the changes it caused were almost random with no relation to the settings i made. 
xrandr (without gui) exists in dapper also but failed to accomplish anything.

---

### Post by steve196 on 2008-03-18
Deleted. This one was garbage. Sorry.

---

### Post by steve196 on 2008-03-19
I found, why xorg.conf did not do anything for me. My radeon7500 has a vga port and a dvi port with a dvi>vga adapter. After my experiment with two monitors, i had my monitor on the adapter and did not put it back. On Windows, that had no consequences, but on linux, xorg.conf seems to describe only the right one of the ports. I solved my problem by plugging my monitor back to the right side. 
Though my problem is solvd now, the general problem still remains.

---

