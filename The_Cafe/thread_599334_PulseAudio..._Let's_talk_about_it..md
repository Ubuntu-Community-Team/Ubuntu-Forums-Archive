---
title: "PulseAudio... Let's talk about it."
date: 2007-11-01
forum: The Cafe
---

### Post by Kosimo on 2007-11-01
Looks like next version of Fedora will include Pulse audio as a default audio server.

I think it's gonna be the real revolution in Linux. Something I've been waiting for a long time now... I always had problems in this particular area... Like, when using Audacious, PIdgin sounds don't play, etc... I could never use the real full duplex at all... Not even mixing ALSA & OSS..


Hope that PulseAudio will fix that.

But the very important news in here is that with PulseAudio is going to be possible to adjust the volume of any single application independently and redirect that audio to any sound card (even USB headphones) that's going to be awesome... Using Ekiga with USB headphones, listening music to the normal speakers... Or adjust a youtube video volume without changing the general volume..

Here, the news:
[http://www.genbeta.com/2007/10/31-pulseaudio-mejoras-en-la-gestion-de-audio-en-linux]("http://www.genbeta.com/2007/10/31-pulseaudio-mejoras-en-la-gestion-de-audio-en-linux")


Will herdy include this?

---

### Post by Kimm on 2007-11-01
Its possible to install PulseAudio in Gutsy also :)

Just do:

sudo apt-get install pulseaudio-esound-compat

I dont use it myself, so I dont know if it needs any tweeking

---

### Post by groggyboy on 2007-11-01
to install pulseaudio 0.9.6 in Gutsy:```
sudo apitude install pulseaudio libao-pulse libgstreamer-plugins-pulse0.10-0 libpulse0 libpulse-browse0 libpulse-mainloop-glib0 padevchooser paman paprefs pavucontrol pavumeter pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-lirc pulseaudio-module-X11 pulseaudio-module-zeroconf pulseaudio-utils
```
then tell ALSA that you wish to use pulseaudio:```
asoundconf set-pulseaudio
```After that, I had to reboot.  Once I did that, PA was working.
[I]
Most apps will require no further tweaking to work.[/I]

There are some exceptions though.  PulseAudio's wiki has a good page for getting Flash 9 to work located [here]("http://www.pulseaudio.org/wiki/FlashPlayer9Solution").  If you have any problems with any other programs, a good place to find solutions is on PulseAudio's ["PerfectSetup" wiki page]("http://www.pulseaudio.org/wiki/PerfectSetup").  Xine-based programs may be tricky, and Audacity doesn't work at all.  To get MPD working, read the final post on [this thread]("http://ubuntuforums.org/showthread.php?t=603791").

The PulseAudio programs that might interest you are paprefs, paman, padevchooser and pavucontrol.  they are located Applications >> Sound & Video.

----------------

My understanding is that Phonon (for KDE) plays a similar role to pulseaudio in that DE.  What I wanna know is if the two will be able to communicate.  When KDE4 comes out, will I be able to use PulseAudio on my computer to communicate with Phonon on my roommate's computer?

---

### Post by Polygon on 2007-11-01
if i install pulseaudio, will i have to do edit every single program that has sound and tell it that i want to use pulseaudio instead of ALSA?

---

### Post by leovalles on 2007-11-01
Hey I installed pulseaudio in my gutsy about 3 weeks ago since I had some sound problemsn with the default settings for ubuntu. With pulseaudio almost everything works perfect for me: flash sound, media players, sytem sounds, etc. But there are two applications that i can't make work: last.fm and skype, it's impossible, i've tried everything... any idea? is there a way to switch back to the other sound server (ESD i think) temporarily just to use these applications? Thanks guys.

---

### Post by graabein on 2007-11-01
Never heard of PulseAudio before and it sounds like a fantastic program. It has to be able to handle usual applications like Skype and Last.fm (web streaming) to be really successful though.

---

### Post by igknighted on 2007-11-01
> **leovalles said:**
> Hey I installed pulseaudio in my gutsy about 3 weeks ago since I had some sound problemsn with the default settings for ubuntu. With pulseaudio almost everything works perfect for me: flash sound, media players, sytem sounds, etc. But there are two applications that i can't make work: last.fm and skype, it's impossible, i've tried everything... any idea? is there a way to switch back to the other sound server (ESD i think) temporarily just to use these applications? Thanks guys.

I would check with the Fedora folk and see if they have had trouble with it (either their forums or mailing lists, or even bugzilla).  If the problem is with a limitation of pulseaudio they could confirm, but if the problem is a configuration one, perhaps since pulseaudio is default there it is configured properly.  Its worth a shot at least.

---

### Post by Tom Mann on 2007-11-01
PulseAudio is long overdue imho, they just need to sort that latency out... Then I can route my FreeBoB JACK through it and ditch my onboard audio!!! :)

---

### Post by leovalles on 2007-11-01
well i just managed to get skype to work correctly, just adding a default alsa-sink device to the /etc/pulse/default.pa. Now i'm able to make calls through it! Last.fm still not working, it says something like alsa audio system doesn't exist :( and there's no option to choose other than alsa in preferences.

---

### Post by daveisadork on 2007-11-01
I've been using PulseAudio for a while, and it's fantastic. Took care of my problem with Flash locking other software out of the soundcard until I rebooted. Plus there are lots of nice features... like using network audio devices to beam my music from my laptop to another computer that's connected to a stereo.

---

### Post by FuturePilot on 2007-11-01
Once they implement PulseAudio the Linux sound system will rock. It's a very advanced sound system.

I tried installing it in Gutsy, but afterwards I had no sound at all.:confused:

---

### Post by tikal26 on 2007-11-01
I am also wondering about phonon and pusle audio since I found this picture of what seems to be phonon and pulseaudi talking to each other
[http://img2.freeimagehosting.net/image.php?8b2d33a654.png](http://img2.freeimagehosting.net/image.php?8b2d33a654.png)

I wonder if I could install it in Kubuntu

---

### Post by kostkon on 2007-11-01
I have to say that you can do wonderful things With *PulseAudio*.

> PulseAudio will pave the way for intelligent audio hotplugging functionality—making it possible for the system to automatically redirect VoIP program audio streams when users plug in or remove USB headsets, for instance. PulseAudio's support for network transparency will also facilitate some impressive functionality. For instance, users will be able to use Zeroconf to detect other computers on the local network that are running audio servers and then dynamically redirect audio output to any of those computers.

Another possible feature is support for conditional dynamic volume adjustment. For instance, PulseAudio would make it possible for a VoIP program to automatically reduce the volume of music programs when a call starts. The software could also be used to automatically reduce the audio volume of all windows that aren't in the foreground so that if you are playing two movies simultaneously, for instance, the movie in the active window would have higher volume. PulseAudio could also be used for more esoteric "earcandy" like making it so that system event sounds play out of the left or right speaker depending the screen on which the event took place. 

Quoted from [*Ars Technica* article *PulseAudio to bring earcandy to Linux*]("http://arstechnica.com/journals/linux.ars/2007/10/17/pulseaudio-to-bring-earcandy-to-linux")

---

### Post by roobz on 2007-11-01
I played yesterday with Pulseaudio and it's really amazing. The only problem was that I couldn't listen the sounds coming from all channels (I have a 5.1 system), only from the front speakers.

If someone knows how to fix this, please tell me.

And yes, using Alsa everything was perfectly fine with the channels.


ps.: sorry for my English

---

### Post by Centx on 2007-11-01
> **roobz said:**
> I played yesterday with Pulseaudio and it's really amazing. The only problem was that I couldn't listen the sounds coming from all channels (I have a 5.1 system), only from the front speakers.

If someone knows how to fix this, please tell me.

And yes, using Alsa everything was perfectly fine with the channels.


ps.: sorry for my English

I *think* this type of hotplugging and autoconfiguring  has been at least partly fixed in 0.9.7 ([http://0pointer.de/blog/projects/pa-097.html]("http://0pointer.de/blog/projects/pa-097.html")) as it comes with a **great** deal of improvements. It's probably possible at present too, but with some more manual fiddeling. I'd recommend the pulseaudio website as a starting point if no one here knows how to help you.

I for one really hopes Ubuntu will adopt PulseAudio as its default sound server(the derivatives also, of course)  together with Fedora and Suse, and hopefully the new OSS v4 as its audio API if it shows to be superior over ALSA (the OSS-API used now is ten years old, and the new one has just been opensourced, and is cross-platform).

If all goes well, ESD will be replaced by PA as default sound server in GNOME and then you have almost all problems solved already:).

Link to screencast of PulseAudio[http://dev.gentooexperimental.org/~flameeyes/mezcalero-pulse-demo.ogm]("http://dev.gentooexperimental.org/~flameeyes/mezcalero-pulse-demo.ogm")

---

### Post by Götz on 2007-11-02
It should be enabled by default in Hardy and replace ESD.

There is an old blueprint 

[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble](https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble)

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by pt123 on 2007-11-02
> **Centx said:**
> I
Link to screencast of PulseAudio[http://dev.gentooexperimental.org/~flameeyes/mezcalero-pulse-demo.ogm]("http://dev.gentooexperimental.org/~flameeyes/mezcalero-pulse-demo.ogm")

:lolflag: Haha a screencast without any audio on a tool that will revolutionise audio on Linux. 
Typically what you expect from Linux developers. Like a GUI application webpage without screenshots.

---

### Post by Palmyra on 2007-11-02
> **Polygon said:**
> if i install pulseaudio, will i have to do edit every single program that has sound and tell it that i want to use pulseaudio instead of ALSA?

Could someone answer this question, please?

---

### Post by Anessen on 2007-11-02
Tried it, looks good but I only got one volume control for my whole card.

Also, I don't like having 5 shortcuts spammed into my Sound and Video menu folder - these are all accessible from the little tray applet anyway.

---

### Post by Tom Mann on 2007-11-06
I am using PulseAudio now, with hope to point it at JACK so I can disable my onboard sound and use my recording setup for all sound, however it seems that Ubuntu have removed JACK support for PA. :(

---

### Post by adam.tropics on 2007-11-06
[Quite a nice Debian guide which reportedly is ok in Ubuntu also.]("http://forums.debian.net/viewtopic.php?t=12497")

---

### Post by Tom Mann on 2007-11-06
Thanks for the link Adam, I'll be sure to try it :)

---

### Post by LuisAugusto on 2007-11-06
It's amazing, but, isn't it a little to resource hungry?

It uses around 4-5 CPU while playing something with GStreamer.

---

### Post by TaTaE on 2007-11-06
> **leovalles said:**
> Hey I installed pulseaudio in my gutsy about 3 weeks ago since I had some sound problemsn with the default settings for ubuntu. With pulseaudio almost everything works perfect for me: flash sound, media players, sytem sounds, etc. But there are two applications that i can't make work: last.fm and skype, it's impossible, i've tried everything... any idea? is there a way to switch back to the other sound server (ESD i think) temporarily just to use these applications? Thanks guys.

:idea:
For skype to work perfectly with pulseaudio, you should have a file called .asoundrc in your home directory containing (only) this:

```

pcm.!default {
type pulse
}

ctl.!default {
type pulse
}

pcm.pulse {
type pulse
}

ctl.pulse {
type pulse
}


```

Hope this will help many users...
I don't know anything about lastfm , as I don't use it yet.

---

### Post by Kosimo on 2007-11-08
Question:

How about the PULSEAUDIO that we can install in Add and remove programs? (Gutsy)  

Is this version that we are talking about?

---

### Post by leovalles on 2007-11-08
well i was not aware pulseaudio is available in add and remove until now, but i already installed all that appears there (volume control, preferences, etc) from synaptic, it's the same thing, but i don't see pulseaudio itself there.

TaTaE thanks for the solution, but i already solved it with a something found somewhere, adding a default device... well it's a little complicated (i don't even know for sure what i really did) but now it's working beautifully.

---

### Post by groggyboy on 2007-11-10
> **Polygon said:**
> if i install pulseaudio, will i have to do edit every single program that has sound and tell it that i want to use pulseaudio instead of ALSA?

to anyone wondering the answer to this: no, you shouldn't have to.  most GNOME based programs should run out of the box with PA.  exceptions include: Audacity, Skype and Flash.  I've also heard of Xine-based programs like Amarok and Last.fm causing problems (both of which are for KDE).

---

### Post by leovalles on 2007-11-11
I've used amarok as well as some other media players (including xine-based) and none of them has given me any trouble with pulseaudio neither have they needed major adjustments, except for last.fm, still haven't found a way to make it work, yet i'm able to access last.fm stream through rythmbox or amarok, so for me it's really worth it having pulseaudio features instead of last.fm.

PS: hope you understand my english, my native language is spanish... so I try to do the best I can, thank you.

---

### Post by toupeiro on 2007-11-12
Has anyone used pulse-audio with Wine?  Any success stories, failure stories.  Lets pick one obvious example:  World of Warcraft?

---

### Post by Polygon on 2007-11-12
> **groggyboy said:**
> to anyone wondering the answer to this: no, you shouldn't have to.  most GNOME based programs should run out of the box with PA.  exceptions include: Audacity, Skype and Flash.  I've also heard of Xine-based programs like Amarok and Last.fm causing problems (both of which are for KDE).

is there any workarounds to make sound in flash work? i do use flash to watch the occasional youtube video so yeah it would be nice if i could have it :D

---

### Post by TaTaE on 2007-11-13
You may try to insert at the and of .bashrc this line

```
export FLASH_FORCE_PULSEAUDIO=1
```

---

### Post by hyperair on 2007-11-13
I installed the libflashplugin.so deb and it works fine for me without that flag. Does that flag work? I might consider removing the package.

For those interested in the libflashplugin.so: [http://pulseaudio.vdbonline.net/libflashsupport/libflashsupport_1.0~2219-1_i386.deb](http://pulseaudio.vdbonline.net/libflashsupport/libflashsupport_1.0~2219-1_i386.deb)

---

### Post by hanzomon4 on 2007-11-13
OMG, I don't know if it's Fedora 8's way of configuring my sound card or pulseaudio but for the first time my M-Audio Delta 66(ice1712) has a master channel by default! Everything else is just great, Ubuntu needs this. I would suggest giving the Fedora 8 livecd a spin if you want to try out pulseaudio

---

### Post by hyperair on 2007-11-13
Master channel? I've always had a Master channel. Using ALSA I mean. On a side note I read somewhere that Ubuntu Hardy will have Pulseaudio by default.

---

### Post by tikal26 on 2007-11-19
how do I disable it
I know that I started it with this
sudo pulseaudio –system=1 –high-priority=1 -D 

but what would be the command to stop it?

---

### Post by hyperair on 2007-11-19
sudo killall pulseaudio
or
sudo /etc/init.d/pulseaudio stop

should do the trick.

---

### Post by hanzomon4 on 2007-11-19
> **hyperair said:**
> Master channel? I've always had a Master channel. Using ALSA I mean. On a side note I read somewhere that Ubuntu Hardy will have Pulseaudio by default.

I never have, I always had to make my own in the asound.conf....

---

### Post by exactt on 2007-11-20
anyone on AMD64?

tried

export FLASH_FORCE_PULSEAUDIO=1

and

sudo dpkg -i --force-architecture libflashsupport_1.0~2219-1_i386.deb

both don't work...

in the latter: i don't know how nspluginwrapper works. do i need a amd64 package? if yes, how do i get a version from git that works with version 0.9.6 of pulseaudio?

thx

update: see [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/155820](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/155820) for more info.

---

### Post by Götz on 2007-12-22
PulseAudio will be enable by default in Hardy Alpha 2!

[http://www.ubuntu.com/testing/hardy/alpha2](http://www.ubuntu.com/testing/hardy/alpha2)

---

### Post by Polygon on 2007-12-23
yay. maybe from hardy and beyond, no one will get the dreaded 'cannot connect to sound server' or whatever message ever again.

---

### Post by Bou on 2007-12-23
> **Kosimo said:**
> with PulseAudio is going to be possible to adjust the volume of any single application independently

Sorry but how is that better than just using the volume slider?

Also, what's the difference between a sound server, a sound sink and a sound source?

---

### Post by bobbocanfly on 2007-12-23
[QUOTE=Bou;4001739]Sorry but how is that better than just using the volume slider?/QUOTE]

If applications are making noise while you are listening to music and there is no in-app way to mute it you would use this. Also for people using multiple music creation apps at the same time it would be useful to have a volume controller in one window.

---

### Post by Polygon on 2007-12-23
> **Bou said:**
> Sorry but how is that better than just using the volume slider?

Also, what's the difference between a sound server, a sound sink and a sound source?

i think the benefeit of using PA is that its a sound server, so pulse audio takes complete control of the soundcard or whatever, and then lets other programs connect to itself and deals out sound accordingly, rather then having ALSA and OSS constnatly fight over control of the sound card, PA does it and everything that supports PA will get sound as normal and you wont get 'cant connect to sound server' messages and stuff

---

### Post by twright on 2007-12-29
this is going to really mess with quite a few games

is there any way i can get it working in open arena

---

### Post by Centx on 2007-12-30
> **twright said:**
> this is going to really mess with quite a few games

is there any way i can get it working in open arena
Indeed it does, The Single Point Of Failure with PA for me was that it could not handle Enemy Territory: Quake Wars. This has been partially corrected though, with the new release of PA and the pasuspender utility, which suspends the PA process and frees up ALSA. Maybe we will get a backport, if not, it will come with hardy =)

---

### Post by samwyse on 2007-12-30
I thought ALSA was the cure for all sound issues. I don't see why people get so excited about PulseAudio.

---

### Post by happysmileman on 2007-12-30
> **samwyse said:**
> I thought ALSA was the cure for all sound issues. I don't see why people get so excited about PulseAudio.

People get excited whenever something new comes around, even if pulseaudio isn't that great (I wouldn't know, never used it), it shows that progress is being made and that people are putting time and effort into a project to fix these things.

---

### Post by oedipuss on 2007-12-30
I installed pulseaudio on gutsy to try it out, and though it seemed to work , I could hear a faint distortion on every sound.. This stopped only after uninstalling the pulseaudio packages and rebooting ..
Any ideas why ?

The distortion was like a faint gurgle, really prominent on the default sine wave test sound, but very easy to miss in an mp3

---

### Post by Polygon on 2007-12-30
a lot of programs arnt configured to use pulseaudio, so its most likely something to do with that everything doesnt recognize pulseaudio in gutsy  or some random config file

check back in hardy, its gonna be in there by default.

---

### Post by FuturePilot on 2007-12-30
> **samwyse said:**
> I thought ALSA was the cure for all sound issues. I don't see why people get so excited about PulseAudio.

Not when you get
```
Could not open /dev/dsp
```
](*,)

PulseAudio is a very advanced sound server that will let you interact with your sound card in a way that was never possible before. :D
It will make a lot of annoying issues like the above error go away.

---

### Post by oedipuss on 2007-12-30
> **Polygon said:**
> a lot of programs arnt configured to use pulseaudio, so its most likely something to do with that everything doesnt recognize pulseaudio in gutsy  or some random config file

check back in hardy, its gonna be in there by default.
Yeah I think I'll wait. It couldn't have been a single application causing this, though. I could hear it in rhythmbox, mplayer, the multimedia selector's test sound, everything . I'm using an audigy 2, btw, if it makes any difference.

All things considered though, it seems great. If Hardy includes a panel applet designed for pulseaudio, and a way to run jack easily, I'm sold =D

---

### Post by hyperair on 2007-12-31
There is a panel applet for pulseaudio! Sort of anyway, it's called padevchooser. Also, if you ever hear any sound distortion, it's probably from Pulseaudio not getting enough CPU time. You can fix that by doing this:
```

sudo renice -15 `pidof pulseaudio`

```

I had to do that in Gutsy, but for some reason, Pulseaudio didn't need it any more when I shifted to Hardy. And it uses less CPU too.

---

### Post by helliewm on 2007-12-31
How do I set the Default Sink? It says its not set?

Helen

---

### Post by hyperair on 2007-12-31
> **helliewm said:**
> How do I set the Default Sink? It says its not set?

Helen

Where do you see the message? A screenshot would be good. Also, try setting the default sink from the Pulseaudio tray icon (can be activated by running "padevchooser" or "PulseAudio Device Chooser" from the menu).

---

### Post by helliewm on 2007-12-31
Got the Device Sink now. Amarok is playing the internet radio but no sound at all ? 

What do need a Screenshot of?

Helen

---

### Post by hyperair on 2007-12-31
Ah, nevermind about the screenshot now. To get Amarok working, take a look here: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) under ALSA Applications. Then get Amarok to use ALSA.

---

### Post by helliewm on 2007-12-31
Brilliant thanks, will try this.

Helen

---

### Post by Götz on 2008-01-15
With Hardy alpha 3 I did not see any improvement in Pulseaudio, hopefully there is better support in alpha 4 or 5.

---

