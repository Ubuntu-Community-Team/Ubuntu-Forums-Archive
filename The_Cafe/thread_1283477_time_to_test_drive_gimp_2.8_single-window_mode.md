---
title: "time to test drive gimp 2.8 single-window mode"
date: 2009-10-05
forum: The Cafe
---

### Post by madjr on 2009-10-05
[IMG]http://www.chromecode.com/temp/gimp-single-window-mode-in-progress-thumb.png[/IMG]

> When the news of the introduction of a single-window mode in GIMP 2.8 hit the net it became clear what an incredible desire for something like this there was. The reactions have been overwhelmingly positive, and this really helps to motivate you to hack on it. The news also revealed an interesting but previously rather anonymous group of people: multi-window zealots despising the idea of a single-window mode in their beloved multi-window application. I suspect they don't realize that single-window mode is going to be optional...

I am happy to tell that the implementation of the single-window mode is progressing well. I have refactored the code to allow docks to be put inside an image window and Michael Natterer have refactored the code to allow many images to be shown in a single image window. The code is already combined and pushed to git master and you can get a very good feeling for how **awesome** the single-window mode is going to be by trying out the current code. Above is a screenshot of a live GIMP built from git master with 'Windows&#8594;Single-window mode' enabled. You can see the toolbox and dockable dialogs docked to the image window and the tabs for images in the image window at the top. Still a lot of things left to do, I should stop writing now and continue coding instead.

*posted by [Martin Nordholts]("http://www.chromecode.com/")*



get the GIT, test and/or complain if you no like it:

[http://www.chromecode.com/2009/10/single-window-mode-progress-report.html](http://www.chromecode.com/2009/10/single-window-mode-progress-report.html)

:guitar:

-----update------

**not sure** but i think i found a ppa going here

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages)


-----update2------

ok **OMG ubuntu** has a nice easy steps to GIT and is testing it out

[http://www.omgubuntu.co.uk/2009/10/gimp-single-window-install.html](http://www.omgubuntu.co.uk/2009/10/gimp-single-window-install.html)

---

### Post by Tibuda on 2009-10-05
> The news also revealed an interesting but previously rather anonymous group of people: multi-window zealots despising the idea of a single-window mode in their beloved multi-window application. I suspect they don't realize that single-window mode is going to be optional...
This makes me happy.

---

### Post by Exodist on 2009-10-05
I like the Single-Window-Mode, but I am also glad they are leaving the multi-window-mode available as an option. Options are good! :P

---

### Post by FuturePilot on 2009-10-05
I'm a multi-window zealot. Phear me :twisted:


Seriously though, I'm glad they kept that option around as I liked the multi-window layout.

---

### Post by hyperdude111 on 2009-10-05
Much prefer single window, it took me a far longer time that it should to to get used to gimp because of the multi window. IMO a great step forward.

Also good that they kept the option for multi windows for those who prefer that. Nothing more annoying than being forced through a UI change.

---

### Post by hoppipolla on 2009-10-05
> **Exodist said:**
> I like the Single-Window-Mode, but I am also glad they are leaving the multi-window-mode available as an option. Options are good! :P

I agree ^_^

I think this is a good thing too :)

---

### Post by kevin11951 on 2009-10-05
How do you get a snapshot from the git repo?

---

### Post by jonian_g on 2009-10-05
I vote for multi window, but is great that people who prefer single window GUI have an option too.

---

### Post by coldReactive on 2009-10-05
I'm for single-window.

---

### Post by lovinglinux on 2009-10-05
> **Exodist said:**
> I like the Single-Window-Mode, but I am also glad they are leaving the multi-window-mode available as an option. Options are good! :P

I agree. I also prefer single-window, but option is always good.

It looks great by the way.

---

### Post by Chronon on 2009-10-05
> **kevin11951 said:**
> How do you get a snapshot from the git repo?

I found a blog that discusses getting source and building GIMP here: 
[http://www.graphics-muse.org/artistsguide/?p=247=1](http://www.graphics-muse.org/artistsguide/?p=247=1)

It links to here for GIT checkout instructions:
[http://live.gnome.org/Git/Developers#head-b0b7ea341a369e00341091c420ddf13ccec134ea](http://live.gnome.org/Git/Developers#head-b0b7ea341a369e00341091c420ddf13ccec134ea)

---

### Post by madjr on 2009-10-06
hmm i think we got a ppa here now:

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages)

---

### Post by Sand &amp; Mercury on 2009-10-07
I'd prefer to wait until it's stable, but single-window mode looks killer.

---

### Post by benmoran on 2009-10-07
I think the single window mode will work out better for computers with single, or smaller screens. The multi-window might be better for high res or multiple monitor setups. 

I'm looking forward to trying this out on my relatively low res (1280x800) laptop. But the main point here is the option to choose. YAY

---

### Post by Crunchy the Headcrab on 2009-10-07
I'm not sure what to think about this.  I like GIMP.  It's my favorite image editor by far (mostly because it balances features with speed).  I have to admit that sometimes my gimp windows can seem like kind of a hassle on my laptop, but at the same time, it's what I'm used to.  I'll definitely give single window a go, once it is in a stable build.

---

### Post by madjr on 2009-10-07
ok OMG ubuntu has a nice easy steps to GIT and is testing it out

[http://www.omgubuntu.co.uk/2009/10/gimp-single-window-install.html](http://www.omgubuntu.co.uk/2009/10/gimp-single-window-install.html)

oh and guys the whole point of the thread is to get enough volunteers to test it and make the experience as smooth as possible before code-freeze and stuff

so don't come complaining later on saying it should had "this and that"

thats why gimp has been multi-window for so long since no 1 at the start bothered testing and complaining about it (some did it way later)

am specially hopeful many **new users** to gimp will test it since they were (mostly) the ones who asked for it

---

### Post by ad_267 on 2009-10-21
I just installed from the PPA but there's no single window option in the Windows menu. Has this option been removed?

---

### Post by Skerit on 2009-10-28
It's still a bit buggy (well, what do you expect from trunk?) but overall it already works quite well. They're doing a good job!

---

### Post by Pasdar on 2009-10-28
multi windows is one of the main reasons I **don't** use gimp at all.

---

### Post by JillSwift on 2009-10-28
> **Pasdar said:**
> multi windows is one of the main reasons I **don't** use gimp at all.
GIMP 2.6.7 drags its other windows up with the window being given focus, makes having multiple windows far less of a pain.

---

### Post by Pasdar on 2009-10-28
> **JillSwift said:**
> GIMP 2.6.7 drags its other windows up with the window being given focus, makes having multiple windows far less of a pain.
Multi window is great pain in the butt because:
1. You have to click all windows to come up. If they are grouped, you even have to click twice for each window to come up and if its not grouped you have to figure out where the windows are each time.
2. The background (other programs) can be very distracting to what you're doing.

To people who take their work serious and want to work efficiently and fast the above is not acceptable.

---

### Post by leandromartinez98 on 2009-10-28
Excelent! Good job! I will try to try it. :-)

---

### Post by Tibuda on 2009-10-28
> **Pasdar said:**
> Multi window is great pain in the butt because:
1. You have to click all windows to come up. If they are grouped, you even have to click twice for each window to come up and if its not grouped you have to figure out where the windows are each time.
2. The background (other programs) can be very distracting to what you're doing.

To people who take their work serious and want to work efficiently and fast the above is not acceptable.
This assumes you use a taskbar and you don't use workspaces.

---

### Post by JillSwift on 2009-10-28
> **Pasdar said:**
> Multi window is great pain in the butt because:
1. You have to click all windows to come up. If they are grouped, you even have to click twice for each window to come up and if its not grouped you have to figure out where the windows are each time. Huh? I just said this version drags its own windows up when one window is focuded. This bit is solved.


> **Pasdar said:**
> 2. The background (other programs) can be very distracting to what you're doing.

To people who take their work serious and want to work efficiently and fast the above is not acceptable.
Then I guess the single window interface will be for you.

---

### Post by ad_267 on 2009-10-28
I haven't had an update from the PPA in a week and don't have the single window mode, it looks like this is only being built for Karmic. Guess I'll have to compile it myself or upgrade to Karmic to have a look.

---

### Post by misfitpierce on 2009-10-28
I like how they did it and left multi-window still as an option for people that are used to and like the free and open multi-window mode such as myself... The single window is cleaner but takes a bit more room trying to squeeze all into a window. I am a bit old school and have been using for years so I love my multi-window setup!

---

### Post by BuffaloX on 2009-10-28
I'm really looking forward to single window mode.
It's like dreaming of getting Deluxe paint back.

Also I hope they figure out better ways to work with transparrencies. I can't seem to get the hang of it, as it is now.

---

### Post by Arand on 2009-12-06
Currently very rough, (probably nothing to do with singe-window) but one major issue I saw was failing to relate the layers..-toolbox to images properly.
So yea, only try for testing and don't expect to actually do proper image manipulation work on it at the moment.
[[IMG]http://img215.imageshack.us/img215/3338/screenshotwartyfinalubuf.th.png[/IMG]](http://img215.imageshack.us/i/screenshotwartyfinalubuf.png/)
I compiled from current git master (I think at least) according to instructions here, on karmic: [http://www.gimpusers.com/news/2009-10-14/compiling-gimp-27-git-ubuntu-904-910.html](http://www.gimpusers.com/news/2009-10-14/compiling-gimp-27-git-ubuntu-904-910.html)
The "2.7" only refers to what was the master at the time of writing the guide, and the directory names it will use. Instruction _will_ get you the latest version, whether it be 2.8 or 4.2 (-- greetings from the past). 

(One small modification I did was substitute git://git.gnome.org/babl (and so on) with [http://git.gnome.org/cgit/babl](http://git.gnome.org/cgit/babl) (and so on) since I am unable to access ports other than http-related)

You might want to substitute  "make install" commands with checkinstall, to make sure you'll be able to uninstall easily, I instead used a snapshotted virtmachine for messing about.

- Arand

---

### Post by Exodist on 2009-12-06
Checkinstall,, eww.. How about install to opt using --prefix=/opt or learn to make real debs.

---

### Post by Arand on 2009-12-06
Hmm, in fact, the instructions given in the link already do install to /opt it seems, so I guess it should be fairly simple to remove regardless then. Proper packaging would happen had I the time to sit down and learn it, just wanted a quick peek for now.

- Arand

---

