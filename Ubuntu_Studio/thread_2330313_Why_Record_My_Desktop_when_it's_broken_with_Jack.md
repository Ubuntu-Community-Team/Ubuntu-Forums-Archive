---
title: "Why Record My Desktop when it's broken with Jack?"
date: 2016-07-10
forum: Ubuntu Studio
---

### Post by kazakore on 2016-07-10
Why is Record My Desktop the defacto screen recorder in Ubuntu Studio when it hasn't worked with Jack for at least 4 years?? :eek:

[https://bugs.launchpad.net/gtk-recordmydesktop/+bug/1037402](https://bugs.launchpad.net/gtk-recordmydesktop/+bug/1037402)

---

### Post by CrocoDuck on 2016-07-10
Hi! Maybe a little off topic, as I don't really know why Record My Desktop has been chosen as a default. Also, I never used it. Just sharing with you what software I use: [SimpleScreenRecorder]("http://www.maartenbaert.be/simplescreenrecorder/"). It always worked well with JACK in my experience.

---

### Post by kazakore on 2016-07-10
> **CrocoDuck said:**
> Hi! Maybe a little off topic, as I don't really know why Record My Desktop has been chosen as a default. Also, I never used it. Just sharing with you what software I use: [SimpleScreenRecorder]("http://www.maartenbaert.be/simplescreenrecorder/"). It always worked well with JACK in my experience.

Thank you. I hadn't got around to checking the others I had heard of and seeing which worked well so I will give this one a try. (I came to the conclusion in the end that the issue I wanted to record evidence of may be due to my keyboard acting strange when it overheats in the end but always goof to know which tools work best :) )

Maybe we can make this a suggestion to change the default screen recorder from Record My Desktop to Simple Screen Recorder?? I'm not sure where you would do that, in these forums or through the bugtracker... There also may be the complications that Ubuntu Studio is based on Xubuntu, which obviously doesn't use Jack, and maybe they have their reasons for staying with Record My Desktop. Although I can't help but feel that any software that has a bug report open in a feature available in its software for four years, without either fixing the issue or removing the feature if they can't, doesn't seem like the best choice of software.... :-/


EDT: Except it's not even in the official repositories so guess a maintainer would have to be found first.....

EDIT2: Well just quickly tested SSR and it both recorded the audio fine and the video was much much smoother as well so definitely appreciate this suggestion and would like to see it moved to the official repositories and become the defacto standard screen recorder :)

---

### Post by Bucky Ball on 2016-07-11
> **kazakore said:**
> There also may be the complications that Ubuntu Studio is based on Xubuntu, which obviously doesn't use Jack, and maybe they have their reasons for staying with Record My Desktop. 

Off-topic, apologies, but just for clarity. It is one big happy family and ALL the flavours are based on the Ubuntu kernel so it doesn't matter much what you install in what (KDE apps from Kubuntu occasionally being the exception and one or two other oddities). Jack runs just fine in Xubuntu.

Open Synaptic Package Manager in Xubuntu, install Jack. Do the same with any other flavour. 

UStudio does use the xfce4 desktop environment. If it is also based on Xubuntu and Xubuntu can't use Jack, why would the UStudio folk have anything to do with xfce4 or Xubuntu? As far as I remember, Jack is default in a full UStudio install. I know xfce4 is and lots of other Xubuntu bits.

I personally don't install any flavour exactly but the Ubuntu minimal, which is just the Ubuntu kernel, no desktop environment or much else, then install what I want from there, Jack, Ardour, Audacity, whatever from pretty much wherever. (Recently I have started using Xubuntu-core as the base.)

For me, it is xfce4 for my desktop and some AV apps and other things I need. Lightening fast. 

Off-topic, sorry, but FYI to avoid confusion re. Jack working in Xubuntu. ;)

---

### Post by kazakore on 2016-07-11
> **Bucky Ball said:**
> Off-topic, apologies, but just for clarity. It is one big happy family and ALL the flavours are based on the Ubuntu kernel so it doesn't matter much what you install in what (KDE apps from Kubuntu occasionally being the exception and one or two other oddities). Jack runs just fine in Xubuntu.

Open Synaptic Package Manager in Xubuntu, install Jack. Do the same with any other flavour. 

UStudio does use the xfce4 desktop environment. If it is also based on Xubuntu and Xubuntu can't use Jack, why would the UStudio folk have anything to do with xfce4 or Xubuntu? As far as I remember, Jack is default in a full UStudio install. I know xfce4 is and lots of other Xubuntu bits.

I personally don't install any flavour exactly but the Ubuntu minimal, which is just the Ubuntu kernel, no desktop environment or much else, then install what I want from there, Jack, Ardour, Audacity, whatever from pretty much wherever. (Recently I have started using Xubuntu-core as the base.)

For me, it is xfce4 for my desktop and some AV apps and other things I need. Lightening fast. 

Off-topic, sorry, but FYI to avoid confusion re. Jack working in Xubuntu. ;)


I know this but different flavours have different programs which come packaged as the default program for that distro. This in a large part follows that which is from the Windows Manager and Desktop Environment in use, hence Gedit in Gnome based (main) Ubuntu and Mousepad for XFCE (Xubuntu and Ubuntu Studio.) As you yourself mention there is no reason to stick with these basic programs from the WM/DE provider, and in some instances (such as photo editing or the current subject of screen recorders) there may not be any choice to in the first place. With Ubuntu Studio being so specialist I do feel it should be brave enough to brake away from the mainstream Xubuntu a little bit. Hence my point that even though it is based on Xubuntu it would be nice to have Simple Screen Recorder become the default on Ubuntu Studio, where it will actually work for (nearly) all user cases rather than almost none, even if Xubuntu insists on staying with Record My Desktop.

Where did I ever claim Xubuntu (or any other distro) can't use Jack? My point is they don't come with it installed as standard (being used by a distro and being available within a distro are very different things) and they are aimed at general desktop users, thus the vast majority of people using them will be happy with working Pulse Audio recording audio in the Record My Desktop application and wont even ever know Jack doesn't work. Whereas I would suspect that almost every single user of Ubuntu Studio who tries to use it is likely to discover this issue, as chances are their videos will be including professional audio software (making tutorials, posting video bugs, etc) and these software are generally configured to use Jack.


Your Xubuntu-core method sounds of interest to me, but again not really while travelling and at times having slow or no internet at all. I tried to get my head around Arch before leaving on my travels this time and got a barely working install and not the time or data connection for the constant reading and learning that I needed to do. My install is very non-vanilla though, with a fair few things tweaked, added etc to try and get the system as I like. Always a work in progress though ;)

---

### Post by Bucky Ball on 2016-07-11
Must have misunderstood. Ignore, my apologies and please continue. ;)

---

