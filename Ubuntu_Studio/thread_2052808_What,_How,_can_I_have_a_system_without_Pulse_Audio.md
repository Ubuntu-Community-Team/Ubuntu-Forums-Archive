---
title: "What, How, can I have a system without Pulse Audio?"
date: 2012-09-04
forum: Ubuntu Studio
---

### Post by bhilmers on 2012-09-04
I can't take it anymore. I can't handle my system randomly breaking or breaking everytime I install an update. If you guys in Ubuntu Studio can't make a stable system with PA and Jack, one of them needs to go. This is ridiculous.

So seeing as I need Jack more than PA, what steps can I take to have a Jack-only system, and what are the implications for doing so? Will Ubuntu Studio just break more? My productivity is going down the drain because of this. I can't have a system where I never know if it's going to work when I fire it up.

I can't even search the forum for answers because there are a million results for Pulse and Jack problems. It's a perpetual nightmare. This is my last stand. I've been using Linux for over two years because I highy support the principals of FLOSS. But if I can't get any audio work done, then I have no use for Linux. I'm tired of fixing my system every two months.

---

### Post by TenPlus1 on 2012-09-04
You could try this and see if it helps:

sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove

sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui

sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer

restart your computer!

---

### Post by jejeman on 2012-09-04
No need for uninstall. Just turn it off.
```
echo "autospawn = no" > ~/.pulse/client.conf && pulseaudio -k
```system will work fine with pulseaudio turned off.

---

### Post by bhilmers on 2012-09-04
> **jejeman said:**
> No need for uninstall. Just turn it off.
```
echo "autospawn = no" > ~/.pulse/client.conf && pulseaudio -k
```system will work fine with pulseaudio turned off.
Nope. This was the first thing I tried and had no success. This is why I want to remove pulseaudio completely.

@TenPlus1: I'll try that next. Right now I'm looking into another solution.

---

### Post by jejeman on 2012-09-04
Well, if turning off pusleaudio is not a solution then something wicked is going on with your system. Maybe you can tell us what exactly is wrong? Why do you think it is pulseaudio's fault?

---

### Post by sgx on 2012-09-05
> **bhilmers said:**
> I can't take it anymore. I can't handle my system randomly breaking or breaking everytime I install an update. 
There is the option of not using apps that use pulse, or
perhaps changing their preferences to alsa/jackd.

Have a few sessions with htop system monitor running, and maybe
you'll see what's causing problems.

Pulse is aimed at home theater, more than pro audio, so having
just one media player installed might help. vlc works with jackd
for simple overdubbing using timemachine to record both parts.

Having clean sessions, where no web browser was opened, might also
help. Updating a working daw is generally bad luck.
Using external drives to install new versions, is the best option.
Cheers

---

### Post by Splashmania on 2012-09-06
Audio-pro is the great forgotted in linux, its simply a non usable set, u must use other systems if u want do something else than record

---

### Post by bhilmers on 2012-09-07
Thanks for the advice so far. I've got one or two things I'm going to try before I go back to Windows XP for audio work. :)

---

### Post by sgx on 2012-09-08
> **Splashmania said:**
> Audio-pro is the great forgotted in linux, its simply a non usable set, u must use other systems if u want do something else than record

Mainstream linux devs may fail to consider pro audio as a high priority, but it is a myth that pro results are not readily achievable.

One needs to start by choosing alsa supported hardware, then jackd compatible software, and have the willingness to learn how the capabilities of jackd connections are best exploited.

There are many other audio distributions you can use, if some release of Ubuntu Studio is giving you problems (10.04 took ages, but is now quite stable, give 12.04 some more time before relying on it)
Cheers

---

### Post by sgx on 2012-09-08
> **bhilmers said:**
> Thanks for the advice so far. I've got one or two things I'm going to try before I go back to Windows XP for audio work. :)Describe the work you need to do, and I'll try to point to something specific. pclinuxos is extremely stable,
libpulse doesn't get involved in audio work, it uses a fast bfs kernel, and has synaptic for .rpm package management.

The newest .deb apps from 'debian unstable' can be converted to .rpm using alien, and manually installed. Several light versions of the
pclinuxOS are there to defeat bloatware,
and the attendant potential of floss incompatibilities.

A desktop computer, with nvidia graphics card (not the newest) and m-audio pci audio card, with a Yamaha keyboard, and Fender Mustang usb amp for guitar work, is extremely trouble free. I have a dualboot install with xp sp3, and it's 6 or 7 years now on the same install, just updating pclinuxos according to necessity.
(I always keep XP partition at less than 50% capacity, which really
helps keep it's paging panties from twisting into a knot ;)
:popcorn:

---

### Post by bhilmers on 2012-09-09
> **sgx said:**
> Describe the work you need to do, and I'll try to point to something specific. 
Oh sure, I started a thread at the LinuxMusicians forum with this info:

This is what I need in a *single application*:

1. Record from a microphone.
2. Edit the recording (cut/copy/paste, etc...)
3. Listen and apply a chain of VST effects in realtime.
4. Save the VST chain as a preset for future use.
5. Export as .wav
6. Does not use JACK.

That's the setup I need to continue making money with my freelance audio work. Unfortunately, I will not compromise these points. The VST plugins I use are essential to the sound of my product. JACK has very poor session support (LADIsh?, pft)  and I waste too much time setting it up, even with BASH scripting. Time is money and I need to turn around my product quickly.

As long as you are offering suggestions, you might as well offer a *viable* alternative to Propellerhead Software's "Reason" so I can have my music hobby back.

Good luck. I've tried every major software package over the past two years and everything pretty much sucks.

NOTE: I know the thread says a system without PulseAudio, but I've realized that both Pulse and JACK suck. JACK session management is a joke and non-JACK apps are weak as ****. At this point I don't really care anymore. I've got my WinXP disk on my desk ready to go if I can't find a solution by the end of this week.

---

### Post by jejeman on 2012-09-09
If you depend on VST then use windows, it is their native enviroment. Or if you have their source code maybe you can recompile them for linux.
There is no alternative for Reason and probably it will never be, but that is not a restriction for you to make music.

---

### Post by bhilmers on 2012-09-09
Yes, I'll use Windows. A friend of mine convinced me Linux was better than Windows, but after two years of struggle I see this is not true for audio work.

---

### Post by jejeman on 2012-09-09
Linux is better than windows, but OS &#8800; applications.

---

### Post by bhilmers on 2012-09-09
> **jejeman said:**
> Linux is better than windows, but OS &#8800; applications.
Correction: An OS without good applications to run on it is useless, not 'bad'... unless you define good as 'useful'. You are not educating me with your smart-*** comment, you're just being a ****. Hope you feel proud of yourself. I won't miss the attitude in Windows-land.

Have a nice day.

---

### Post by sgx on 2012-09-09
Reaper works fine in wine, with the wineasio driver, with many
many plugins. I can use the standalone Amplitube, with
the plugin version also running in Reaper. Pace/macromedia type protection schemes don't work, nor dongles/iloks etc,
but U-he, Native Instruments, Camel Audio, IK Multimedia,
Wusikstation, AlgoMusic, Ugo, yada yada have been staples for me
for a long time. What are your favorite vst plugins? Maybe I have tested/used them?

There are several people happily using FLStudio of which I
know almost nothing, beyond it's goal of being 'all inclusive'.

The advantages of jackd connecting hardware and software, using
multiple input devices, seeing Reapers sum output as just another instrument, outweigh the lack of session management. Reaper sessions
work as expected. aj-snapshot works for most jackd connections.

I keep windows around for Headcase, Rhino, 1977, and a few others
whose gui don't draw perfectly yet. The latest wine version has
almost fixed this. 
(I think jejeman's comment was actually supporting the quality of
windows audio apps, not implying them to be inferior.)
Cheers

---

### Post by sgx on 2012-09-09
> **bhilmers said:**
> Correction: An OS without good applications to run on it is useless

As someone with access to most any vst, I can accomplish more
with hydrogen, rakarrack, and yoshimi, than any three windows apps
at my disposal. It is simple to set up and switch between large numbers
of desktops, so gui clutter is not an issue. This makes for low stress
productivity.
No doubt, there are many wonderful and innovative windows apps,
but many just exist to correct failed musicianship,
and compensate for the lack of hard work
Practice time! ;)

:guitar:

---

### Post by bhilmers on 2012-09-10
You must be the greatest musician/producer ever. This forum is so lucky to have you.

---

### Post by smartboyhw on 2012-09-12
> **bhilmers said:**
> Correction: An OS without good applications to run on it is useless, not 'bad'... unless you define good as 'useful'. You are not educating me with your smart-*** comment, you're just being a ****. Hope you feel proud of yourself. I won't miss the attitude in Windows-land.

Have a nice day.

Well that's the truth. I do think that OS is just a baseline for usage. You still need good apps to use the function of the OS. OS needs apps, apps need OS. 

I also would like to pay tribute to sgx also:)

---

### Post by sgx on 2012-09-13
> **bhilmers said:**
> You must be the greatest musician/producer ever. This forum is so lucky to have you.
I was lucky, very early on, to have what turned out to be the most
compatible linux gear available. 
Then, I saw a picture of the Crystal softsynth in some now ancient magazine, 
and stumbled upon the early fst command, and it worked.

I try to help people to keep trying, learning, changing gear
that doesn't work, for things that do etc

Linux forums are lucky to have people like

lowtech
gmac
Fernando Lezcano
lump
Jaromil
Jeff Hoogland
Pemasu
without them, zip, nada, and zilch.
(add in your favorite distro creators to the list)

I have 17 gig of recordings, only about 3 gig were done
with windows, and then finished in linux, and in my own dubious opinion, 
only a third are dogs, the rest, are a roll of the dice,
as personal taste differs even among squirrels
with similar tales. So 80% luck, 10% workaholic, and
maybe the other 10% environmental influences.

Maybe try Ardour3 when it gets out of beta, time is on your side.
Things improve from year to year. (Well, maybe not windows 8,
but even microsoft can take a mulligan)
After 6 years of user funded
XP beta testing, it works pretty good for recording.
Cheers

---

### Post by bhilmers on 2012-09-24
> **sgx said:**
> Maybe try Ardour3 when it gets out of beta, time is on your side.
Things improve from year to year. (Well, maybe not windows 8,
but even microsoft can take a mulligan)
After 6 years of user funded
XP beta testing, it works pretty good for recording.
Cheers
Thanks anyway, but Ardour is not what I'm looking for. I need an editor, not a multi-track recorder. I'll keep watching Linux audio in the future, but honestly, until there is a unified audio stack like you see in Windows and Macintosh I can't see coming back to dealing with two or more classes of application, some which only work on Jack and others on Pulse. And I don't need something that works "pretty good." I'm a professional, not a hobbyist. I need something that works *great*.

For now I found the perfect application for my needs: [http://www.wavosaur.com/](http://www.wavosaur.com/)

Audacity should try to be that good. I wish Wavosaur was open-source, but I donated to the project anyway because it's a good tool and has increased my productivity.

And I don't understand why you would make a snide comment about Windows 8, which hasn't even been released and won't be for another month. You Linux people are ridiculous, talking about something you have no experience with.

---

