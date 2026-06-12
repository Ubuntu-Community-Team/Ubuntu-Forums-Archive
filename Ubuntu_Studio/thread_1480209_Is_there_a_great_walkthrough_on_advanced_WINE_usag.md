---
title: "Is there a great walkthrough on advanced WINE usage for audio?"
date: 2010-05-11
forum: Ubuntu Studio
---

### Post by hxcobd on 2010-05-11
I've never delved too deeply into using WINE for Windows audio programs/VSTs on linux, but the time is ripe now!

Is there a great walkthrough somewhere on doing some of this stuff? I know how to handle basic WINE usage, but last time I used it, sound wasn't very well-supported, so I have no experience whatsoever with WineASIO and whatnot.

I'd ultimately like to install VSTHOST, Reaper, Melodyne, possibly Samplitude, and a huge array of VSTs.

Any help appreciated!

---

### Post by sgx on 2010-05-11
> **hxcobd said:**
> I've never delved too deeply into using WINE for Windows audio programs/VSTs on linux, but the time is ripe now!

Is there a great walkthrough somewhere on doing some of this stuff? I know how to handle basic WINE usage, but last time I used it, sound wasn't very well-supported, so I have no experience whatsoever with WineASIO and whatnot.

I'd ultimately like to install VSTHOST, Reaper, Melodyne, possibly Samplitude, and a huge array of VSTs.

Any help appreciated!
Reaper is the best option, you'll waste vast quantities of time fooling with other hosts that are limited in function, or are unstable.

after installing wine and wineasio, run the command

regsvr32 wineasio.dll

make the needed folders to install plugins in this location:

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

Use the default installer locations of windows plugins,
and dongles, pace, and ilok plugins won't work, most others will.

the command 

wineprefixcreate  will create your .wine folder, check its contents.

Install your linux with a separate /home partition, install Reaper
in /home/username. Before you reinstall linux, rename .wine to oldwine, choose not to repartition /home  Your Reaper/vsts will be waiting for you.
Copy Steinberg/VstPlugins oldwine to the new .wine, and Reaper will be back in action.

In command lines used to run installers, spaces in paths and titles must be filled with a *  as in Program*Files

download Reaper  [http://www.cockos.com/reaper/download.php](http://www.cockos.com/reaper/download.php)

Install it with

wine /home/username/reaper351-install.exe

Google/youtube have lots of details.

Cheers

---

### Post by hxcobd on 2010-05-11
Hey sgx,

Thanks again for all the tips.

I'm a fairly "advanced" linux user, so I had already done all of the things you mentioned. I guess I overestimated how difficult it would be to get WineASIO up and running.

:)

I'm really trying to avoid using Windows DAWs, so I've opted instead for as minimalist a route as possible. I'm using VSTHOST with a handful of my favorite VSTis (Kontakt, Kore, and Battery, namely), and to my surprise, it works WONDERFULLY.

Easy as pie to route the output from VSThost into Ardour/other native Linux DAWs using WineASIO and JACK. I'm really floored.

The one thing I'd like to be able to do now, though, is program on a piano roll/sequencer using MIDI in another linux DAW, and have that control the Windows VSTis in VSTHost, and THEN have the output of THAT recorded by another linux native DAW.

So, I suppose a likely configuration would be:

Rosegarden -> VSThost (Kore/Kontakt/Battery) -> Ardour

I suppose I could streamline it a bit by using a host that has both audio AND MIDI capabilities, like QTractor, EnergyXT, or Renoise, making it:

QTractor -> VSThost -> Qtractor

But I've never used MIDI in linux and can't seem to see ANY MIDI inputs in VSThost whatsoever.

I'll be googling again like a madman, but I'd love any tips on setting up MIDI as well! (I don't use a USB MIDI controller or any of that nonsense; just mouse-entered piano roll stuff is fine.)

---

### Post by sgx on 2010-05-11
Thats why I recommended Reaper. It is the best option, and its midi capabilities have improved greatly in the last year. And using qjackctl,
you can route its input/output. A hydrogen drum track with Reaper vsts,
linux zynaddsubfx/phasex synths, then rakarrack for fx, is a strong setup.

In qjackctl, press the Connect button, and a 3 tabbed screen opens,
your system midi ports will be in the Alsa tab. When you start Reaper,
and load vst, you'll see the connections appear in the Audio tab.
When you start a linux app, you may see connections in both of those tabs, reroute as desired. I have few issues with an m-audio 24/96 pci card. Knocking on wood in both 3/4 and 4/4 for luck :)

---

### Post by sgx on 2010-05-11
a simple Reaper piano-roll video:

[http://www.untidymusic.com/wordpress/using-reaper/video-tutorial/reaper-piano-roll-create-drum-beat/](http://www.untidymusic.com/wordpress/using-reaper/video-tutorial/reaper-piano-roll-create-drum-beat/)

---

### Post by hxcobd on 2010-05-12
Sgx, I know Reaper is a pretty stable option as far as MIDI capability goes, but I'd really like to avoid having to use a Windows DAW for something as simple as programming MIDI patterns on a piano roll.

Can't a linux program take care of this? QTractor? Rosegarden? Seq24? And then route the MIDI output into Vsthost to the actual instruments?

---

### Post by fedexnman on 2010-05-12
vsthost is that a windows program ? (i see a vsthost over at kvraudiodotcom), im using ezdrummer with there stand alone host ezdrummer solo hooked up to ardour. if you guys are running vsthost under wine i could see ditching windows for good.:popcorn:

---

### Post by hxcobd on 2010-05-12
> **fedexnman said:**
> vsthost is that a windows program ? (i see a vsthost over at kvraudiodotcom), im using ezdrummer with there stand alone host ezdrummer solo hooked up to ardour. if you guys are running vsthost under wine i could see ditching windows for good.:popcorn:

Yeah! It's a completely free Windows program used solely for hosting VSTis and even VST effects, and it works GREAT under Wine!

I've got an instance of Kontakt, Kore, and Battery all open, and all using custom libraries, and they all work super well in it!

That's why I'm so interested in forgetting about Reaper altogether; with Vsthost hosting all my instruments, I don't really need a full Windows DAW; just a good linux MIDI sequencer and a good linux DAW to record all the sequenced stuff!

But getting a linux MIDI sequencer to sequence the Windows VSTis in Vsthost is a bit beyond my current knowledge... I'm sure it's not overly difficult, but I'm having some trouble.

---

### Post by fedexnman on 2010-05-12
cool !! reaper is cool, but i like ardour way better, reaper and my firewire device don't jive   xrun city. ill be trying out vsthost thx man

---

### Post by mr.thraz on 2010-05-12
you should be able to use those plugins in standalone mode.

they'll appear as pluginname_asio in jack.

[like i'm doing here]("http://www.youtube.com/watch?v=5AWGl5O9SK0").


then you just chose the midi device in the app itself.

---

### Post by hxcobd on 2010-05-12
Yeah; every plugin I've been able to open in Vsthost has also worked in standalone mode. You're right, that would probably be an easier way to organize/arrange everything, as well as probably lighter on the CPU.

I've never heard of that Guru before, I might have to look into that!

See, routing all the audio around is no problem, but routing MIDI is where I'm kinda stuck, simply because NO midi connections appear in my JACK at all. Also, in the lower left of JACK, there are a few options for midi: None, Raw, and Seq. Any idea what the difference is, and which I should be using?

---

### Post by hxcobd on 2010-05-12
Messing around with JACK and WINE midi a bit more...

Looks like the Seq midi option is going to be the most logical route to route MIDI from linux, into Windows' Vsthost. The Raw option doesn't even create a device in JACK's "Connect" panel, while Seq does.

Still, even after enabling this, no system MIDI devices show up in Vsthost's midi options. I'm thinking there must be some midi equivalent to WineASIO?

---

### Post by mr.thraz on 2010-05-12
open wine/ configure wine.

go to the audio tab.

make sure you only have the alsa sound drivers selected.

---

### Post by hxcobd on 2010-05-12
Doesn't that eliminate the ability to use WineASIO with JACK, though? I had been told numerous times to only have JACK selected in the Wine audio options.

---

### Post by mr.thraz on 2010-05-12
well i use it that way with  no problem at all. as you can see in the vid.

---

### Post by hxcobd on 2010-05-12
It appears you're right, Thraz; with only ALSA selected in the Wine audio config, a whole bunch of MIDI options appear in Vsthost now, as opposed to literally 0 before when I had JACK selected.

It does still appear to be using JACK as well, just as long as WineASIO is selected in Vsthost as well.

Now I've got MIDI Input in Vsthost set to the MIDI-thru port 0, and in JACK, I've got JACK-keyboard (which I'm using for testing the MIDI) connected to MIDI Playback 1 on the MIDI panel.

And it all works! I'm able to play the linux native JACK keyboard, which then plays into the WINEd Vsthost, controlling any VSTi I'm using, which can then be recorded by whatever native linux audio DAW I'm using.

I'm really blown away by this. It's probably a bit more complex to set up than simply using Reaper in linux, but I also think it's a bit more stable, relies less on Windows programs, and requires less system resources...

Now I just need to figure out how to use the numerous MIDI channels to control different instruments and I'll be more or less satisfied...

---

### Post by hxcobd on 2010-05-12
Well, all the MIDI functions I wanted and all the MIDI channels work wonderfully using the JACK keyboard, which was sort of my preliminary testing device...

But I'm finding that none of the linux sequencers I'm using create a MIDI device in JACK at all... Seq24 doesn't, Rosegarden doesn't, QTractor doesn't...

Am I doing something wrong? All I want to do is to be able to control the VSTs via MIDI the exact same way I was with the JACK keyboard. Why don't any of these programs create a nice-and-easy MIDI port within JACK like the keyboard does?

---

### Post by mr.thraz on 2010-05-12
turn your midi settengs back to none in jack settings

---

### Post by hxcobd on 2010-05-12
You're brilliant, thraz! Looks like that did it.

Seq24 still isn't working, but I'm assuming that's because my JACK install is totally screwed up anyway, so I'm reluctant to fault it. But QTractor now works with the MIDI rig I've got going.

I got Tuxguitar working as well, and I'm actually REALLY excited about that... I've never had the ability to write tablature while using high-quality VSTs before, especially not externally set-up like this, so that's pretty cool. Wish the repos had the newest version of Tuxguitar, though...

---

### Post by sgx on 2010-05-12
I'm glad things are coming together nicely. But consider the total dependencies of the needed linux apps, their lack of unified developer relationships, the uncertain pace of developement, variables in workflow, quality of documentation, depth and speed of technical support, and how
a breakdown or serious slowdown of just one component might affect things
a year from now, when faced with a special opportunity, or deadline. A year which might be wisely spent mastering just one application and gui, belonging to the most rapidly developed DAW in existence, with midi, audio, a growing plugins collection, the worlds most flexible qwerty assignment tools, excellent scripting capabilities, and used happily on macs, wintels, and linuxi, at a very affordable price, and still just a 4.5 megabyte download. I've done linux audio both with and without Reaper, and I know which way is more efficient, and offers greater creative freedom, while maintaining a solid grip on unified future development, insuring the musicians investment in learning curve will apply on all the main computing platforms far into the future.

In the meantime, save all the debs and burn them to media as future insurance, always install with a separate /home partition, and always
save the tips you read, and bookmark the good info pages.
Cheers :)

---

### Post by hxcobd on 2010-05-13
Sgx, I definitely see where you're coming from. I know Reaper has the most potential as a stable area of growth, especially on linux, but that's not really where my interests lie.

I work professionally in audio, so I'll always have a Windows partition/computer and Protools for my real audio work.

When it comes to linux and my free time, though, the world is my oyster!

I wouldn't bother with Reaper at all, on any operating system, for professional, paid work. I save Protools and my Windows partition for that type of thing.

:)

---

### Post by sgx on 2010-05-13
I love how you guys moan and groan about linux issues, boast of religious adherence to open-source, despite the apparent hypocrisy of using VstHost, then at the last second, belch out that you're a ProTools Supremacist :P

Here is a hint, CD quality is nothing more than CD quality, its the
same whether its created in Pro Tools, Sonar, Reaper, a consortium of linux apps, you name it.
You can tattoo your *** and your oyster with ubuntu beans, or corporate
logos, its still just CD quality.

I'm glad you are getting things working, but please start your future discussions with:

'Hi, I'm a Pro-Tools studio professional, using linux for audio production in my spare time, and need advice etc about X, Y, or Z'.

:rolleyes:

---

### Post by mr.thraz on 2010-05-13
reaper is very powerful and stable. only a linux daw can beat it at price point.

i use a linux daw cause i prefer to create my own work flow, but the guys at cockos put a lot of love into reaper and it shows.

i make a good living  doing production work with my linux daw, but i do get those looks when they see me opening ardour, specimen, zynaddsubfx and hydrogen.

but i refuse to go back to the virus infected world of windows or the expensive glamor and glitz of a mac.

i see windows like living in the projects, crack head always trying to break in to your home and steal stuff. but its cheap to live there.

i see mac as living in a high-rise condo with a bunch of snotty neighbors who get mad  whenever  you throw a party ad threaten to kick you out when ever you do something cool at your place.

i see Gnu/Linux as a commune, your expected to work harder to maintain the community. some people are dirty or down right crazy
but the atmosphere is relaxed, homie and nice.

all i'm saying is, stop paying for that place in the projects. spend more time at the commune

---

### Post by sgx on 2010-05-13
The gui of Ardour and Hydrogen are excellent, and zyns colors make me want
to head for the beach. From another forum, Subversound mocked the daw
opinion wars with this post (count the daws )


I am an avid Cubase user. It really gives the pro tools i wanted. It is just plain logic. There is no reason to play the reaper bashing everything that pops into your sonar. After all, you want your performer to be the best garage band ever, the peak of all live performances. So you should have the audacity to stop with your sound forgeries, childish innuendoes and acid comments. Recycle your ideas and bring that ardour for music back to your life! 

Cheers :)

---

### Post by hxcobd on 2010-05-13
> **sgx said:**
> I love how you guys moan and groan about linux issues, boast of religious adherence to open-source, despite the apparent hypocrisy of using VstHost, then at the last second, belch out that you're a ProTools Supremacist :P

Here is a hint, CD quality is nothing more than CD quality, its the
same whether its created in Pro Tools, Sonar, Reaper, a consortium of linux apps, you name it.
You can tattoo your *** and your oyster with ubuntu beans, or corporate
logos, its still just CD quality.

I'm glad you are getting things working, but please start your future discussions with:

'Hi, I'm a Pro-Tools studio professional, using linux for audio production in my spare time, and need advice etc about X, Y, or Z'.

:rolleyes:

I don't really understand this post.

1.) I'm forced by necessity to use Protools professionally. If you've ever worked in audio, you know that a huge portion of clients know one and ONLY one DAW: Protools. If you use anything else, you run the risk of losing clients. It's sad, but that's just how it is. 

I don't LIKE or LOVE Protools by any means. I'm forced to use it, period.

2.) I'm aware there's no difference between the output of one DAW and another, sonically. As long as you're using what works for you, it really shouldn't matter. But again, when I'm getting paid for it, I have to adhere to what clients desire.

3.) I have no "religious adherence to open-source." I'm more interested in alternative ways of doing things, primarily conserving CPU cycles and memory. To me, using an entire DAW (Reaper) seems less logical than simply using linux DAWs paired with a Windows VST host.

4.) Why would I start future threads with that? I don't understand.

---

### Post by sgx on 2010-05-13
Hi, if people know you are an experienced professional, replies
will in some cases vary. A kid new to linux might ask the exact
same question, but an answer perfectly sensible to you,
might leave him with the deer-in-the-headlights stare.
(I have mastered that stare, but nothing else :( )

Hint to your customers that you can save them time and money by integrating new tools now used in Russia, that supplant some aspects of Pro-Tools. 

Not to bore you to tears with Reaper chatter, but you say you are

"more interested in alternative ways of doing things, primarily conserving CPU cycles and memory"

yet a 4.5 megabyte powerhouse that works in everything from a 200 megabyte
Puppy Linux distro on a decrepit old PII, to the spendiest Mac under the sun, and all the multi multicore PCs in between, is anathema, while you futz about with routing virtual patchcords willy-nilly amongst a fistful of linux apps that will always be betas, by any professional or Pro-Tools standard. A standard you say you must adhere to in your day job.

Does something not seem odd about that picture? :)
(cue the X-Files theme, or suitable religious anthem ;) )

It is trivial to create complex audio/midi routings and projects in Reaper. I myself would be creating sonic mud when going beyond 8 or 10 elements. I suspect that an experienced professional could do sonic wonders.
Cheers, its almost the weekend!

---

### Post by hxcobd on 2010-05-13
Sgx, you know I appreciate your input and help muchly, so anything you say I feel has at least SOME merit to it!

:)

I do own a license for Reaper, so I'll give it a shot and see how it works out for me.

My interests/hobbies as far as linux audio goes revolve more around tinkering and doing "weird stuff," rather than actually producing a ton of musical/audio output. I do enough of that in the Windows realm. If I was solely interested in producing high-quality musical works, and lots of them, I'd just stick to Windows.

The whole fun of linux is tinkering, learning, and experimenting!

---

### Post by sgx on 2010-05-13
DUDE!!! After all this, you own a reaper license? (just how many MORE times will this hxcobd guy 'deke my *** :) )
Lucky you are not in tazer range!

Well, as a teaser, I did a great track in reaper using
only live input from a logitech usb dual joystick game controller,
with midi learn assignments, to play the music, using multiple secret softsynths. Nobody believes me until they peruse the relevant reaper forum topics, and fill in the blanks.

I need a drink.

But I don't drink.

Life can be like that :guitar:

---

### Post by sgx on 2010-05-13
> **hxcobd said:**
> Sgx, you know I appreciate your input and help muchly, so anything you say I feel has at least SOME merit to it!

:)

I do own a license for Reaper, so I'll give it a shot and see how it works out for me.

My interests/hobbies as far as linux audio goes revolve more around tinkering and doing "weird stuff," rather than actually producing a ton of musical/audio output. I do enough of that in the Windows realm. If I was solely interested in producing high-quality musical works, and lots of them, I'd just stick to Windows.

The whole fun of linux is tinkering, learning, and experimenting!

This line:

"If I was solely interested in producing high-quality musical works, and lots of them, I'd just stick to Windows."

You might want to edit it a bit, before the thickneck guys in other timezones show up with hot tar and pitchforks. :)

---

### Post by hxcobd on 2010-05-13
> **sgx said:**
> This line:

"If I was solely interested in producing high-quality musical works, and lots of them, I'd just stick to Windows."

You might want to edit it a bit, before the thickneck guys in other timezones show up with hot tar and pitchforks. :)

Haha, I don't mean to say that high-quality works AREN'T POSSIBLE in linux. The fact of the matter is that producing music/audio on linux requires a LOT more work than it does on Windows. For some of us, that's half the fun. For the other half, it's a pain in the *** and hard to justify the difficulty!

And I never said I hated Reaper by any means! It's a fine program; just not particularly my cup of tea. The workflow's weird and I find the interface rather clunky. (Also, its handling/sorting of plugins is abysmally poor.) I own licenses for a lot of the smaller, cheaper DAWs (EnergyXT, Podium, Orion).

---

### Post by sgx on 2010-05-13
Yes, Reaper does sometimes require multiple passes to scan plugins,
tracking plugins is like herding cyber-cats. Luckily most work in linux.

I was going to suggest right and left-clicking all the widgets and open
araeas, as some of them have both a function on left click, and/or a pop-up on right-click. But you already discovered how clunky that is ;)

My favourite use is the io button, it opens a handy routing dialog for sends and receives, you can make nice fx chains as the basis for different genre.

A google search of 
daw ferarri "pro Tools" 

has some interesting discussions.
Cheers

---

### Post by sgx on 2010-05-13
> **hxcobd said:**
> Haha, I don't mean to say that high-quality works AREN'T POSSIBLE in linux. The fact of the matter is that producing music/audio on linux requires a LOT more work than it does on Windows. For some of us, that's half the fun. For the other half, it's a pain in the *** and hard to justify the difficulty!

And I never said I hated Reaper by any means! It's a fine program; just not particularly my cup of tea. The workflow's weird and I find the interface rather clunky. (Also, its handling/sorting of plugins is abysmally poor.) I own licenses for a lot of the smaller, cheaper DAWs (EnergyXT, Podium, Orion).

I can guaratee you that I can have a total computer newbie recording multi-track faster using my linux setup and Reaper, than any combination of windows + fill in the blank DAW. Most people are born near a windows
installation, so there is some headstart, as opposed to switching OS in midstream.

The total cost of service in windows, including reinstalls, re-registrations, firewall/anti-virus, a deluge of unwanted system popups and hand-holding, new hardware discovery of old hardware, yada yada is part of the equation. A fresh install of my daw with all the vsts, eyecandy, internet accounts, and my odd lot tweaks, runs around 20 minutes. Of course, Spielberg may have higher expectations, in line
with his wallet, but I never feel musically limited, except for the lack of 30 hour days, or the genious needed to utilize 24 with suitable skill.
My requests for 30 hour days are always turned down. 

I have a dual-boot XP partition thats existed 3 years with all my linux tinkerings. knocks on wood...does formica count? :)
used mainly as a storage device, or a testbed for demos of new synths. 

Cheers

---

### Post by hxcobd on 2010-05-13
Hahaha! I think you're absolutely right; a lot of people would probably take to (modern) installs of linux a lot faster than even they probably think they would. I don't doubt for a second that you could get a newbie up and running more quickly on linux than in Windows. I'd probably be frightened if it were the other way around!

I hate having to use Windows. I hate the feeling of typing in a search query in Google and, when coming across a lesser-known URL, that worrying feeling in the pit of your stomach, "God, I hope there's no spyware on this site."

I've been unable to get a number of my Windows audio programs running in linux so far. Melodyne and Izotope RX are two of the big ones. Melodyne installed, but I couldn't get it to boot without crashing. WineHQ says it should be stable, though... Hmm.

More tweaking needed, I guess!

That 'daw ferrari 'pro tools'' search query has me laughing and I haven't even tried it myself yet. Oh boy...

---

### Post by sgx on 2010-05-14
I actually tried the Reason demo last night, as I can't resist trying things that someone says won't work. To my surprise, I started the demo song, and nothing crashed, and I was able to change some instruments and mouse around some knobs while the tune played. I'm not a potential customer, but it seems hopeful for someone who uses it. Its sure not lacking numbers or vocalists in the userbase.

My basic premise is that linux apps are landmines, the fewer the better, so I start with a minimal linux, and uninstall everything that I know won't break the system, then add just the linux audio apps I actually use, around 12 at last count, the wine/wineasio setup, and opera for web access. Then I walk carefully on known paths. Wine is at 1.44, as of last night, and I don't install anything except libwine, wine, and wineasio to use windows apps. There are two font collections aimed at serving windows software, webcore-fonts and microsoftfonts, which I install for luck. Lastly, I add the typical audio codecs, and do a short raindance in 5/4 time. It would be 4/4 if I actuall could dance. :( 
Melodyne will never work, because it has a name weirder than linux,
which is not supported in the kernel. :)

oops, I also add these .dlls to wines drive_c/windows/system32 folder

mfc42
mfc71
msvsp60
msvcp71
msvcp90
msvcr70
msvcr71
msvcr80
msvcr90
gdiplus

they all have appeared over the years in
terminal output related to some crash, or failure to start, some are now part of wine, maybe one will be lucky. All are at free dll download sites.
Cheers

---

### Post by hxcobd on 2010-05-14
> **sgx said:**
> 

My basic premise is that linux apps are landmines, the fewer the better, so I start with a minimal linux, and uninstall everything that I know won't break the system, then add just the linux audio apps I actually use, around 12 at last count, the wine/wineasio setup, and opera for web access. Then I walk carefully on known paths. Wine is at 1.44, as of last night, and I don't install anything except libwine, wine, and wineasio to use windows apps. There are two font collections aimed at serving windows software, webcore-fonts and microsoftfonts, which I install for luck. Lastly, I add the typical audio codecs, and do a short raindance in 5/4 time. It would be 4/4 if I actuall could dance. :( 
Melodyne will never work, because it has a name weirder than linux,
which is not supported in the kernel. :)

oops, I also add these .dlls to wines drive_c/windows/system32 folder

mfc42
mfc71
msvsp60
msvcp71
msvcp90
msvcr70
msvcr71
msvcr80
msvcr90
gdiplus



THIS is the type of post I like to see regarding linux/Wine setups. I don't care about installing FLStudio or any of that garbage; I too like a MINIMAL setup with virtually everything uninstalled except the REQUIRED stuff.

I'll definitely be using all of these tips.

The bit about Melodyne made me laugh out loud, hahaha!

I had read that Winetricks add-ons were sometimes required for a lot of Wine programs, though I'm not sure exactly why, or even what Winetricks is, to be honest.

---

### Post by mr.thraz on 2010-05-14
winetricks is a quick and dirty script to download and install various redistributable runtime libraries sometimes needed to run programs in Wine.

/!\

---

### Post by psidrum on 2010-05-21
> **hxcobd said:**
> I've never delved too deeply into using WINE for Windows audio programs/VSTs on linux, but the time is ripe now!

Is there a great walkthrough somewhere on doing some of this stuff? I know how to handle basic WINE usage, but last time I used it, sound wasn't very well-supported, so I have no experience whatsoever with WineASIO and whatnot.

I'd ultimately like to install VSTHOST, Reaper, Melodyne, possibly Samplitude, and a huge array of VSTs.

Any help appreciated!

EnergyXT works great with wineasio,

---

