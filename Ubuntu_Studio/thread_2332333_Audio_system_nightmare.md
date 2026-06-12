---
title: "Audio system nightmare"
date: 2016-07-30
forum: Ubuntu Studio
---

### Post by hathalud on 2016-07-30
After a faulty upgrade of Ubuntu 14.04 LTS to 16.04.1 LTS I scrapped my install. Before I did so I learned of Ubuntu Studio and figured I'd give it a try from a blank slate. I work with Blender, Gimp, Inkscape and the like, why not have those preloaded right? I choose to go with the base install of everything because I don't know much about Studio at this point... No biggie, right? 

Studio brings a new learning curve... I can handle learning new things and I'm digging most of this stuff... But the one problem I'm not liking is the audio side of things... I don't plan to do a lot of audio stuff... Audacity is the most I'll need for the foreseeable future. 

But there are problems. I can't just change the volume from a little applet in my panel though... nor does using the multimedia keys on the keyboard work. I made some changes per other articles on the net, but that seems to just have over complicated things. For a while I could press the volume keys on my keyboard and two indicators would flash up and change.... and yet the volume would remain the same...  

I disabled one of those indicators... but I still have to go into AlsaMixer (a terminal app) to really change the volumes... And that's kinda a deal killer. It's not as user-friendly (in a media-center way, since a large function of my desktop is as a media center, playing movies and TV shows for my GF and I from halfway across the room) as I would like. 

And then there's the whole issue of audio playback on the speakers of my choice... I can't even change what is playing the audio now.... It doesn't let me switch from my speakers to my USB headphones when I want to play things over the headphones... 

So how do I either make the audio side of things more simple and work the way I want? Or simplify the whole system so that it works like it normally would on a normal Ubuntu install? Any response would be appreciated. Thanks in advance.

---

### Post by yoshii on 2016-07-30
Have you tried the QasMixer and the PulseAudio Volume Controls?
With those two, you can get pretty much everything done and they are graphical, not command line.  
I see no reason why you'd need any ALSA command line stuff.

---

### Post by hathalud on 2016-07-31
The QasMixer looked pretty awesome, but it wouldn't let me switch between the headphones and the speakers. Is there a way to do that? 

Setting the controls back to the pavucontrol worked and I found how to turn on the hotkey hooks to grab the multimedia buttons. 

Thanks for the your help!

---

### Post by Bucky Ball on 2016-07-31
If you're only doing vid stuff and don't need audio, may I suggest you think about this in another way (particularly as you don't mind a learning curve). Start from the bottom and work up.

You could do this by installing the [minimal.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") then building it up from there (it installs the kernel, you do the rest, from the desktop up). 

Another alternative is to start with [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") (see '[Community ISOs]("https://unit193.net/xubuntu/core/")' at the bottom of that link). This will install the kernel and the basic xfce4 desktop environment. Ubuntu Studio is more or less based on something like Xubuntu-core and uses the same desktop environment. From there, you can install Synaptic Package Manager and then ubuntustudio-video and that will give you the default video stuff from UStudio only, no audio. They install Audacity and anything else you might need and you're done. :)

If you have a look in the package manager you will see Ubuntu Studio provides a lot of packages specific for people in your situation. They want to do one thing and don't need all the others, so if you're wanting to do graphic art or photography, you'll find a ubuntustudio- package that suits you (they are available as ubuntustudio-graphics or photography, video, audio) . 

It is probably a rare user that would need or use everything that came as default in Ubuntu Studio, and probably why the good folk at UStudio give user's alternatives. Good luck.

---

### Post by hathalud on 2016-08-02
I finally got it the way I want it. The "PulseAudio Panel Plugin" applet is grabbing the MM keys with "enable keyboard shortcuts for volume control" being checked, but there is nothing defined in the "audio mixer" box. That allows me to control the audio from my keyboards' MM keys. Then to switch devices I added an app launcher nearby that runs the pavucontrol so that I can switch from speakers to headphones or adjust the master volumes if needed. Additionally I found this setting which I have disabled. Not sure it's helping or not, but incase someone else needs the same help as me, I went to Apps > System > Ubuntu Studio Controls and then I unchecked the Realtime Audio before relogging. It's not perfect, but it's more ideal than it was and works simply enough.

---

### Post by Bucky Ball on 2016-08-02
Thanks for sharing and marking as solved. Nicely done. ;)

---

