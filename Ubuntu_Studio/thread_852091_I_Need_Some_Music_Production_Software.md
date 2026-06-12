---
title: "I Need Some Music Production Software"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by sartajc on 2008-07-07
I decided to make my next album entirely on linux, if possible. No live instruments, all software (I've already done live).

I already know about Audacity, but I was wondering what other software is available.

Personally, I HAVE to have a drum machine and/or software instruments. Basically, if I can do most of the things Garageband can do, I'm good to go.

I need this because I am making a rap album. I want to do it on Linux because I want to show people that it is possible to make an entire album with free software and all that people would need to buy is a mic.

---

### Post by Fingers &amp; Thumbs on 2008-07-07
Good on you, I definitely support your efforts.

You should try ubuntustudio, it comes prepacked with much of what you will need, and much more in the repositories. Of course all of these packages can be added to a standard ubuntu desktop, but to take full advantage and have it runnng without latency issues, you will be needing ubuntustudios real-time kernal.

Just about everything you need to know to get started is [[COLOR="Blue"]here[/COLOR]]("http://lau.linuxaudio.org/")
  

Good luck with your project

---

### Post by snowpine on 2008-07-07
> **sartajc said:**
> I decided to make my next album entirely on linux, if possible. No live instruments, all software (I've already done live).

I already know about Audacity, but I was wondering what other software is available.

Personally, I HAVE to have a drum machine and/or software instruments. Basically, if I can do most of the things Garageband can do, I'm good to go.

I need this because I am making a rap album. I want to do it on Linux because I want to show people that it is possible to make an entire album with free software and all that people would need to buy is a mic.

I agree with the previous poster, Ubuntu Studio has more than enough software to get you started. The drum machine, Hydrogen, is really powerful and fun. Good luck!

---

### Post by secondstage on 2008-07-07
If you want a synth/organ sound, you can do Zynaddsubfx, which will take the input from your (computer) keyboard, and it can the input from a MIDI keyboard, if you have one. Also Ardour is very good, some people say they prefer Ardour over Pro Tools.

--secondstage

---

### Post by Bucky Ball on 2008-07-08
Ubuntu Studio is definitely what you are after, and a truckload of soundfonts. Open source of these is not so plentiful. Check Rosegarden for recording but as mentioned, UStudio will keep you busy for sometime - there is heaps there!

Have fun.

(ps: Studio only comes in the alternate install cd version, text based, so don't do what I did when I first installed it ... forgot to install a desktop!!! lol.)

---

### Post by sartajc on 2008-07-08
Thanks for your help bro!

I have one more question. I have used Jam Packs for Mac for quite a while, and I have this particular sound instrument that has a Sitar and Tabla (international instruments from India). Is there any way I can get these sounds on Ubuntu Studio? If not its not that bad because I can still record that one instrument in GarageBand and transfer to Ubuntu Studio.

---

### Post by Bungo Pony on 2008-07-08
Hydrogen is a fantastic drum machine for Linux. I have used it, and it blows away ALL of the free ones that I've tried in Windows.

However, for multitracking, I don't use Linux software. I use a piece of Windows software in WINE called "Multitrack Studio". The free demo version is enough to get things accomplished, but the software is so good that I'm thinking about purchasing it. Since it works well under Wine and is extremely user friendly, I have no problem paying for it.

Also, just a word of warning... Audacity and Ubuntu are not on completely 'friendly terms' at this time since Ubuntu decided to adopt Pulse Audio, and Audacity currently doesn't support it. However, you can get around it if you fire up Jack Audio Control before using Audacity. Or you could do what I do and use Windows wave editing software under Wine.

---

### Post by Bucky Ball on 2008-07-09
This might be of some help;

[http://www.lesbell.com.au/Home.nsf/0/c4b39482154feb03ca256f8100150ad9?OpenDocument](http://www.lesbell.com.au/Home.nsf/0/c4b39482154feb03ca256f8100150ad9?OpenDocument)

... and for some ideas on soundfonts;

[http://soundfonts.homemusician.net/](http://soundfonts.homemusician.net/)

[http://www.hammersound.net/](http://www.hammersound.net/)

The Hammersound site is popular. There is another great soundfont package but I can't remember the name so can't find that one! If anyone has any ideas, kick in.

I don't know what you're into but I compose and need Sibelius type software for that and uni. I have been exploring MuseScore a bit and looks like it may be able to fill the gap in Linux (no more Vista!). I am about to start getting serious about loading some sounds and working out how to make some noise with that. It comes as part of Ubuntu Studio 8.04 nowadays (MuseScore that is, along with Rosegarden). Good luck with it all.

---

### Post by OutOfReach on 2008-07-09
I use Hydrogen, and [[COLOR="Blue"]LMMS[/COLOR]]("http://lmms.sourceforge.net") which I think are both very good tools.

---

### Post by sartajc on 2008-07-09
I wanted to try out Ubuntu Studio in VMWare before installing it for real, but it keeps starting in command line mode. Why is that? How do i get the GUI running?


I have a Macbook with Mac OS X and Ubuntu Normal partition installed, but don't want to erase my Ubuntu Normal till I try out Studio since it's hard to install Ubuntu on Macbooks and because I don't have access to a DVD RW right now.

Is this a problem with my Mac or VMWare

If VMWare is the problem, is there a way to install something on a separate partition without having to burn the ISO onto a DVD?

---

### Post by Bucky Ball on 2008-07-09
I mentioned the alternate install CD was the only flavour it comes in. Text based. You need to select to install a desktop (the Ubuntu Studio desktop) during install with Gutsy at least (not sure about Hardy Studio). The way you're doing it, maybe that is causing a glitch, because some audio/visual bods probably don't want to waste resources on desktops when they have the know how to run from command line so not automatic option. Again, this may be different in Hardy.

Also as I mentioned, I screwed it up and missed the desktop selection option the first time I did full install from the CD and wound up in the same spot you sound like you are in now.

You can probably apt-get install the desktop if you can get online, then your away perhaps? All an adventure! I'll have a look around and see what I can dig up.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-8.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-8.04)

That link might give you some tips and/or leads.

---

### Post by sartajc on 2008-07-09
oh.....oops. thanks man. sorry for not paying attention to you're post earlier. you're advice fixed the problem :guitar:

---

### Post by Bucky Ball on 2008-07-09
Cool. I have attached a screenshot of the bit where I screwed up. You must have 'Ubuntu Studio Desktop' checked, as it is in the shot. Glad to hear things are progressing ...

[http://linux-sound.org/](http://linux-sound.org/)

Have fun ...

---

### Post by Capoeira on 2008-07-10
if you already run Ubuntu you don't need to install Ubuntu-studio, just install the realtime Kernel (linux-rt) and all the software u need from the repositries.

> **sartajc said:**
> I have this particular sound instrument that has a Sitar and Tabla (international instruments from India). Is there any way I can get these sounds on Ubuntu Studio? 

are these VSTi-instruments? u can use most of the VST/VSTi plugins in Linux using dssi-vst: [http://dssi.sourceforge.net/download.html](http://dssi.sourceforge.net/download.html)
u can search for VST-instruments in google too.

---

### Post by snowpine on 2008-07-10
Ubuntu Studio is great and I recommend it. You don't need to install it separately; you can add the real time kernel and the audio applications using apt-get. 

If you're looking for a quick taste of linux music production, without changing or installing anything on your computer, check out dyne:bolic. It is a music/video production distro that runs from a live cd and has a distinct "underground" aesthetic. It has many of the same apps as Ubuntu Studio (including the Hydrogen drum machine). Might be perfect for your rap album.

---

### Post by Capoeira on 2008-07-10
all you need to know for installing Ubuntu-studio above your already installed Ubuntu you can find here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

the advantage is that you can decide during boot if you want to use the RT-Kernel or the "normal" Kernel - having like this 2 distros in one

EDIT: i also recomend not using a drum machine but audio-loops, sounds much more natural. with a beatslicer (look my thread i have just created) you can create any kind of beat u want to. this page helped me a lot: [http://www.linuxjournal.com/node/1000304](http://www.linuxjournal.com/node/1000304) part 2: [http://www.linuxjournal.com/node/1000315](http://www.linuxjournal.com/node/1000315)
EDIT1b: try out Recycle-Demo for Windows with Wine to explor what fatastic things you can do with a beatslicer (not only with beats): [http://www.propellerheads.se/download/index.cfm?fuseaction=get_article&article=recycle](http://www.propellerheads.se/download/index.cfm?fuseaction=get_article&article=recycle)

EDIT2: if you want to make some real funky sound you might want to use a analog-modelling-synthesizer like "amSynth" (you can create fat basses with this) or/and some modulations of some vintage synths like Minimoog or ARP2600 with "Bristol". those two can be found in the repositries too. (bristol homepage: [http://bristol.sourceforge.net/emulations.html](http://bristol.sourceforge.net/emulations.html))
there is a superb emulation in VSTi-standart for Minimoog too (better than the one in Bristol) - but this is not free
if you like, there is a superb VSTi-emulation of a clavinet (this is free) [http://bigtick.pastnotecut.org/index.php?action=PROD&pcode=120](http://bigtick.pastnotecut.org/index.php?action=PROD&pcode=120)

EDIT3: instruments for linux use the DSSI-architecture but most instruments u will only find in VSTi-standart but like i mentioned above u can use them with DSSI-VST even included in many programs like Rosegarden or Ardour or as standalone conected via Jack-server

EDIT4: sumary of all you need:
a) a midi-controler or virtual Keybord (vkeybd)
b) perhaps a midi-sequencer like Rosegarden
c) multi-track-recorder like Rosegarden, Ardour or even Audacity
d) a audio-editor like Audacity 
e) a drum-machine like hydrogen or a beatslicer like Freecycle and audioloops(sampels)
f) virtual instruments: DSSI-instruments, virtual syths, VSTi-instruments with DSSI-VST and Wine
g) audio effects with LADSPA-plugins or VST-plugins with DSSI-VST and Wine
h) perhaps a mastering-software like JamIn
i) Jackd (Jack-server) to conect all these

---

### Post by WiDzz on 2009-06-11
Ardour GTK2  ...SYNAPTIC

---

### Post by markbuntu on 2009-06-11
Hydrogen-Rosegarden-ZynAddSubFx-Ardour. They will all stop/start/play/record in sync using the jack transport control. Midi keyboard can hook into rosegarden, midi controller to ZynAddSubFX and the new version of ardour.

It is very hard to beat that, and its all free.


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by Bucky Ball on 2009-06-12
Midi is now fully operational in Rosegarden, markbuntu; in, out, thru? I could search for the answer but may as well ask you! ;)

---

### Post by fracturedmorals on 2009-06-12
> **sartajc said:**
> I decided to make my next album entirely on linux, if possible. No live instruments, all software (I've already done live).

I already know about Audacity, but I was wondering what other software is available.

Personally, I HAVE to have a drum machine and/or software instruments. Basically, if I can do most of the things Garageband can do, I'm good to go.

I need this because I am making a rap album. I want to do it on Linux because I want to show people that it is possible to make an entire album with free software and all that people would need to buy is a mic.

It isn't open source, nor free; but RENOISE

Get it. It's amazing.

---

### Post by caalamus on 2009-07-18
How about running Jack in Ubuntu 9.04, I understand this will allow me to take advantage of my G3 iBooks firewire 400 bus... then I can use either my Alesis MultiMix8 or Mackie Satellite.

It was recommended I instal Ubuntu as opposed to the studio version


(500Mhz G3 iBook 640MB RAM, original AirPort card)

for more info see thread:

[http://ubuntuforums.org/showthread.php?t=1206680&highlight=firewire+recording](http://ubuntuforums.org/showthread.php?t=1206680&highlight=firewire+recording)

:]

---

### Post by caalamus on 2009-07-18
So I just started reading this article:

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

(pretty cool)

Do I not need to "download" Jack at all?

Is Ubuntu Studio built in? ...just run some code and it surfaces???

Do I need to be connected to the internet while I run these codes in terminal???

(wow! my head is spinning... I'm just trying to make beats :] hahaha!)

[Http://www.MySpace.com/ProfanusCaalamus](Http://www.MySpace.com/ProfanusCaalamus)
(free compilation download)
[Http://www.MySpace.com/Caalamus](Http://www.MySpace.com/Caalamus)
[Http://www.MySpace.com/BornAzul](Http://www.MySpace.com/BornAzul)

---

### Post by vinutux on 2009-07-18
just install ubuntustudio pakages in your exixsting ubuntu

```
sudo apt-get install ubuntustudio-desktop
```

.

---

### Post by caalamus on 2009-07-18
cool thanks...

does that require being connected to the interwebs?

---

### Post by Bucky Ball on 2009-07-18
> **vinutux said:**
> just install ubuntustudio pakages in your exixsting ubuntu

```
sudo apt-get install ubuntustudio-desktop
```.

Not as simple as that.

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

Should work, but take your pick:

[http://www.google.com.au/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=n3n&q=install+ubuntu+studio+existing+ubuntu&btnG=Search&meta=]("http://www.google.com.au/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=n3n&q=install+ubuntu+studio+existing+ubuntu&btnG=Search&meta=")

Integrating Ubuntu Studio with Ubuntu is a good idea. I don't like the studio artwork and themes personally so you can leave them out. My desktop DAW setup is Xubuntu installed first, then studio installed using the method on the first link I gave in this post. As suggested in that post, I left ubuntustudio-desktop *out* because it contains all the artwork and themes (which I didn't want).

:)

---

### Post by caalamus on 2009-07-18
Thanks Bucky :]

(that's what we called my Great Gramps hahaha! :])

So, you got any advice regarding my desktop only showing up in the top left 3/4 of my screen?

You can find more info here and here :

[http://ubuntuforums.org/showthread.php?t=1114297&highlight=working+tutorial](http://ubuntuforums.org/showthread.php?t=1114297&highlight=working+tutorial)

no luck with these fixes :[

&
here:

[http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire](http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire)

(info about my system and background on ho I got to this point)


Appreciate your help &#8730;

---

### Post by paulmerchant on 2009-07-21
> **fracturedmorals said:**
> It isn't open source, nor free; but RENOISE

Get it. It's amazing.

No, it isn't open source, but almost everything in Renoise is free. The free version is an amazing tracker, a sequencer for your synths, a nice sampler, and it can output to everything to Ardour via Jack. Registration brings you rendering capabilities and a few other benefits.

I prefer to stick with open source for my general software needs, but Renoise serves a niche and has a great community.

---

### Post by caalamus on 2009-08-06
O.k. so I sorted out the display reso issue noted above. I am trying to install Ubuntu studio. I'm following the first of the two links that Bucky posted. It seems fine and then says it can't find 'linux-rt'?

in this thread:

[http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire](http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire)

a helpful Ubuntu user was saying that there isn't a Power PC version of Ubuntustudio.

But here 

[https://launchpad.net/ubuntu/jaunty/powerpc/ubuntustudio-desktop](https://launchpad.net/ubuntu/jaunty/powerpc/ubuntustudio-desktop)

I found (what seems like) info to the contrary [?]


Any thoughts

---

### Post by adzik on 2009-08-06
Thought I'd chime in....
Regarding the original post, if you are looking for something akin to garageband, try [Jokosher]("http://www.jokosher.org"). 
And I'll second, and third Renoise. :D

---

### Post by sgx on 2009-08-07
> **caalamus said:**
> O.k. so I sorted out the display reso issue noted above. I am trying to install Ubuntu studio. I'm following the first of the two links that Bucky posted. It seems fine and then says it can't find 'linux-rt'?

in this thread:

[http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire](http://ubuntuforums.org/showthread.php?t=1206680&highlight=recording+firewire)

a helpful Ubuntu user was saying that there isn't a Power PC version of Ubuntustudio.

But here 

[https://launchpad.net/ubuntu/jaunty/powerpc/ubuntustudio-desktop](https://launchpad.net/ubuntu/jaunty/powerpc/ubuntustudio-desktop)

I found (what seems like) info to the contrary [?]


Any thoughts
First keep it very simple. Focus on 5 things for 2 weeks, setup your soundcard/alsa, then qjackctl, its your alsa/jackd patchbay gui, ardour2, your recording app, zynaddsubfx, your softsynth, and Hydrogen, your drum machine.

For your soundcard, run the command     sudo alsaconf
and answer the questions it presents. If ubuntu has its own audio config control panel, run that instead.

In the settings for qjackctl, make the priority 70, make sure your soundcard shows up, then save the settings. The > input/output widgets on the far right of the settings panel may be clicked to reveal and choose soundcards.

Now, start both hydrogen, and zynaddsubfx, and connect as needed in qjackctl. Their output goes to your system input. Load the drum demos in Hydrogen, and hit the play button on the standard transport.

Zynaddsubfx has a V K button, to open a virtual midi keyboard for you to play notes. The default is a nice sinewave sound

When you can hear both those apps, start ardour, go to qjackctl, and disconnect the other 2 apps, and reconnect them to ardour, which should have automatically connected to your system sound. Its possible ardour will demand to be started first, if it gives an error, once you know how to get music from zyn and hyd, shut it all down, and let Ardour go first.
Get some good coffee and read up on each app, using google as a convoluted manual. Cheers :D

PS Shop for a used Pentium4 at 3 ghz, 1 gig memory, $100 max, you will not regret it.

---

### Post by caalamus on 2009-08-08
hey thank you :]

Rock out!

I'll try it.

---

### Post by Bucky Ball on 2009-08-08
Yea, nice one sgx. You should write a more formal HOWTO. :)

---

### Post by caalamus on 2009-10-19
terminal says that there is no command "sudo aslaconf"

(command not found)

---

### Post by VertexPusher on 2009-10-19
There is no alsaconf. What do you need it for?

---

### Post by karimruan on 2009-10-19
THere is a 'decent' program called jokosher. It is in a way similar to acid pro. ALso, I have heard great things about ardour, only i cant get it to run right. It keeps telling me that jack cant connect either because it is in use by another user or some other reason, both of which are not the case. CHeck to make sure your mic works, and DEFINITELY get ubuntu studio! Also, a great site to get free samples from is looperman.com. You might also want to check out RoseGarden. I just downloaded it, and haven't quite figured it out yet. 

You can get josher and rosegarden via apt-get:

sudo apt-get install jokosher
sudo apt-get install rosegarden

Not sure about ardour, try this:

apt-cache search ardour

This will list all of the packages related to that search, when you find it, sudo apt-get install * (where * is package name).

I am also working on a rap album, entirely from ubuntu studio. I just can't get my mic working for the life of me. Good luck!

---

### Post by Bucky Ball on 2009-10-19
karimruan, if you have Ubuntu Studio installed how come you had to install Rosegarden? That is part of the UStudio install.

---

### Post by caalamus on 2009-10-19
Vertex Pusher...

Quoting SGX from earlier in the thread: "**run the command sudo alsaconf**"

"First keep it very simple. Focus on 5 things for 2 weeks, setup your soundcard/alsa, then qjackctl, its your alsa/jackd patchbay gui, ardour2, your recording app, zynaddsubfx, your softsynth, and Hydrogen, your drum machine.

For your soundcard, run the command sudo alsaconf
and answer the questions it presents. If ubuntu has its own audio config control panel, run that instead.

In the settings for qjackctl, make the priority 70, make sure your soundcard shows up, then save the settings. The > input/output widgets on the far right of the settings panel may be clicked to reveal and choose soundcards.

Now, start both hydrogen, and zynaddsubfx, and connect as needed in qjackctl. Their output goes to your system input. Load the drum demos in Hydrogen, and hit the play button on the standard transport.

Zynaddsubfx has a ** button, to open a virtual midi keyboard for you to play notes. The default is a nice sinewave sound

When you can hear both those apps, start ardour, go to qjackctl, and disconnect the other 2 apps, and reconnect them to ardour, which should have automatically connected to your system sound. Its possible ardour will demand to be started first, if it gives an error, once you know how to get music from zyn and hyd, shut it all down, and let Ardour go first.
Get some good coffee and read up on each app, using google as a convoluted manual. Cheers 

PS Shop for a used Pentium4 at 3 ghz, 1 gig memory, $100 max, you will not regret it."


That's why I needed it...

:]

---

### Post by karimruan on 2009-10-19
> **Bucky Ball said:**
> karimruan, if you have Ubuntu Studio installed how come you had to install Rosegarden? That is part of the UStudio install.

I converted from ubuntu to studio, basically adding packages manually. I got as far as ubuntustudio-desktop, and forgot about it, so basically, I just had the theme and splash screen.

---

### Post by sgx on 2009-10-20
On my system, root can run the alsaconf command to open the
Alsa Configurator, which lets you choose which soundcards to
configure. Perhaps this is not default in Ubuntu? It may be in your
synaptic repositories, as it is in mine.
Cheers

---

### Post by VertexPusher on 2009-10-20
> **caalamus said:**
> Quoting SGX from earlier in the thread: "**run the command sudo alsaconf**"

That's why I needed it...
I recommend to be very careful whenever someone in this forum tells you to run arbitrary commands with sudo. Unfortunately many people don't know when to use sudo and when not. ALSA can be reconfigured completely without root privileges. So even if a command alsaconf existed, it would not require sudo.

---

### Post by Bucky Ball on 2009-10-20
> **karimruan said:**
> I converted from ubuntu to studio, basically adding packages manually. I got as far as ubuntustudio-desktop, and forgot about it, so basically, I just had the theme and splash screen.

From Synaptic Package Manager, ubuntustudio-audio will load all audio apps.

---

### Post by caalamus on 2009-10-20
thanks vertex...

---

