---
title: "Second qwerty keyboard as midi keyboard."
date: 2010-06-10
forum: Ubuntu Studio
---

### Post by seegreen on 2010-06-10
I want two use two keyboards on my computer, one as a standard keyboard and the other needs to send midi. I am familiar with programs like vkeybd that provide a virtual midi keyboard that can be played with a qwerty keyboard but that does not allow to operate other programs with my other keyboard at the same time. Is there a program that does this?

---

### Post by Pablo_F on 2010-06-10
I suggest vmpk. I really don't know if you can achive what you want out of the box but at least vmpk is currently under development. You could ask this question in vmpk's sourceforge forum or just contact Pedro. He is very nice and helpful.

---

### Post by trulan on 2010-06-10
I'd second VMPK, as it's the best for being customizable - but I'm not sure how to set up two keyboards like you're suggesting.

The difficulty isn't so much with the virtual keyboard program as it is with getting Ubuntu (or maybe I should say the X Windows server) to use two separate keyboards, separate their outputs, and route their signals to two separate programs.  Without doing some research I'm not sure if it's feasible or not.

---

### Post by Breambutt on 2010-06-10
Are you some sort of an avant-garde artist and want to compose a song by recording the keystrokes of you programming something hardcore? Because I'm gonna do it if you aren't.

Not sure if this will be a clever idea but you could probably assign some bogus keys with [evrouter]("http://www.bedroomlan.org/projects/evrouter"). I did this in Hardy with my TV tuner's IR remote to control Amarok, Kaffeine and to play emulators with an intolerable lag without being able to hold a button down. 8D

Anyway, you can assign it to use keystrokes from /dev/input/event6 for example and assign the key to some sort of multimedia keys your keyboard doesn't have. Can't remember exactly how this went but it was controlled via a single configuration file in the home directory.

Edit: Nevermind the bogus keys, just have to use the correct event. I used bogus keys to map strange key combinations for more retarded stuff.

I wonder how much money schools and non-profit groups would save if they bought one powerful PC with separate X screen on each monitor and input routed like this.

---

### Post by sgx on 2010-06-10
> **seegreen said:**
> I want two use two keyboards on my computer, one as a standard keyboard and the other needs to send midi. I am familiar with programs like vkeybd that provide a virtual midi keyboard that can be played with a qwerty keyboard but that does not allow to operate other programs with my other keyboard at the same time. Is there a program that does this?
A difficult hurdle will be getting and maintaining focus. Tobybears
Minihost can circumvent OS keyboard focus to a musicians advantage, but
I never got it working in wine. I'll try again, its been over a year
since I tried, but he has possibly removed it from availability the web.
Cheers

---

### Post by Breambutt on 2010-06-10
Oh yeah, didn't think about the focus. But you can conf evrouter to register the keypresses by window titles (and probably other things) so it doesn't steal focus. As far as I recall.

Also used xmodmap, xbindkeysrc and whatnot, but I don't think those are needed unless you need silly key combinations.

I was gonna sleep but now I'm too "psyched" to try this out. Might even write a mini-mashup with step by step instructions for our friendly posse of which some are rather impatient.

---

### Post by sgx on 2010-06-10
> **Breambutt said:**
> Oh yeah, didn't think about the focus. But you can conf evrouter to register the keypresses by window titles (and probably other things) so it doesn't steal focus. As far as I recall.

Also used xmodmap, xbindkeysrc and whatnot, but I don't think those are needed unless you need silly key combinations.

I was gonna sleep but now I'm too "psyched" to try this out. Might even write a mini-mashup with step by step instructions for our friendly posse of which some are rather impatient.
There are many potential uses for dedicated keypresses, used to trigger
all manner and length of sounds. Pairs of keys could be assigned to
control the direction/amount of traditional controls like pitchbend,
modwheel, filter resonance...fill in the blanks :guitar:

---

### Post by Breambutt on 2010-06-10
Didn't think about that either, my brain is farting loud tonight. On the other hand I'm a guitarist first and even my MIDI keyboard is a basic model with only pitch bend and vibrato (and sustain pedal).

Already regretting that I bought the cheapest one available. It's not a bad one but nowadays I have more complex VST instruments that are programmed to the boot and I'd kill for some sort of expression control.

What a bummer if I end up using an excess QWERTY keyboard instead of the MIDI keyb. Wonder how hard it would be to reprogram those keys... I guess it wouldn't be too bad using a QWERTY keyboard for missing controls on the side. Or maybe it would, don't know jack about those and the VSTis seemed rather limited in terms of configuration.

Hey, this thread evolved into a pretty useful one.

---

### Post by sgx on 2010-06-10
I use a two-stick 13 button logitech usb game controller in Reaper,
as Reaper includes midi joystick control, topics over at the Reaper forum
enabled me to stumble my way to success.

[http://forum.cockos.com/showthread.php?t=41416](http://forum.cockos.com/showthread.php?t=41416)

[http://forum.cockos.com/showthread.php?t=37629](http://forum.cockos.com/showthread.php?t=37629)

 Using midi-learn on synths that have it,
and using one stick for pitchbend, and one for distortion intensity,
(or whatever you choose, delay speed, filter sweep etc) can yield great
results on some synths. The buttons trigger the notes them selves.
Massive from Native Instruments would be a good choice. And the demo
runs in 30 minute sessions if thorough testing is needed. 

This little jewel Fretkeys is for triggering midi from guitar, not tested in linux yet that I know of. But can be useful with an hour to get the knobs adjusted for the sounds you want to trigger. The link to the file itself is on the page below.)
  
[http://bass.forumeiros.com/home-studio-f13/fretkeys-audio-para-midi-t3005.htm](http://bass.forumeiros.com/home-studio-f13/fretkeys-audio-para-midi-t3005.htm)

---

### Post by Breambutt on 2010-06-10
Hmpgf. Never tried Reaper and wouldn't really want to start using it now, but I guess there's a workaround for everything. I have an Xbox controller which looks more or less like that Logitech pad I used in Hardy but there's no receiver and the Suxbox fight stick is actually a D-pad. :\

Thanks for the tip, might go looking around the local compewter store for some cheap crappy used joysticks.

Couldn't get much more ridiculous; joystick and qwerty keyboard that play like a live instrument.

---

### Post by seegreen on 2010-06-11
I think I have come up with a while not very elegant, simple solution. Use a evrouter config file that states that when ever a key is pressed on the midi keyboard that it will call a shell script to send a midi message. The only problem is I do not know how to send a midi message via shell command and also I will have to also create a virtual midi device to send from. Does any one know of a simple way to do this?

---

### Post by sgx on 2010-06-11
The results of using the gamepad are rewarding, if the implementation is unconventional. Reaper is a 4.9 meg download, chock full of
features, and affordable, and using it in wine is a pleasure. Its output
is just another instrument for jackd connections, as far as linux is concerned. Send it where you want.

The linux nanonoise app is for Korgs nice NanoKontrol

[http://www.sweetwater.com/store/detail/nanoKONTROL](http://www.sweetwater.com/store/detail/nanoKONTROL)

I hope to get one soon.
Cheers

---

### Post by Breambutt on 2010-06-11
seegreen,

Can't you just connect it via JACK? I thought this was given, considering we're talking about MIDI, keyboards and MIDI keyboards. There's a VMPK Output in the ALSA tab you can connect to any sample library / software synth.

I dediced not to even start on my little project yet since I would've had to "get up" before I could finish it, but I guess I'll give Reaper a go. I mean, what the hell - already using Wine anyway when noodling around with VSTs.

---

### Post by seegreen on 2010-06-11
Breambutt

When I said "MIDI keyboard" I was refering to my second qwerty keyboard, not sure if I made that clear.

Your proposed solution does not work for my needs. Maybe I was not clear on what I wanted. I want my second keyboard to work just like a MIDI controller. So I could be doing things like adding more tracks on sooperlooper by sending midi data from my second keyboard while at the same time be in emacs running a new chuck thread. Then continue working on manging the chuck threads via shortcuts in emacs but also by sending it more MIDI data from the second keyboard. VMPK cannot distinguish between the two keyboards and I must have its window open for it to get keyboard input unless I use "grab keyboard" but this makes my primary keyboard useless.

---

### Post by trulan on 2010-06-11
The closest thing to a solution I have found is doing what's called multi-seat.  It's typically geared toward two users on the same computer - two keyboards, two mice, two monitors - and it's done by logging in as two separate users, running two instances of X, and setting up xorg.conf accordingly.  See here for a discussion:
[http://ask.slashdot.org/article.pl?sid=07/04/27/021241](http://ask.slashdot.org/article.pl?sid=07/04/27/021241)

So you could set up something like that, and log yourself in as two users, running your virtual midi keyboard on one screen and your midi sequencer on the other.  However getting midi events from one user to another might be an issue.  You might have to use netjack for that - I know very little about that, I'm just imagining.  But I think you will have to use two instances of X to use two keyboards for two separate purposes at the same time.

---

### Post by AutoStatic on 2010-06-12
> **sgx said:**
> This little jewel Fretkeys is for triggering midi from guitar, not tested in linux yet that I know of. But can be useful with an hour to get the knobs adjusted for the sounds you want to trigger. The link to the file itself is on the page below.)Rakarrack as of development version 0.5.0 can do this too. It's in my PPA. Bit sketchy though still, but the devs are working on it.

---

### Post by AutoStatic on 2010-06-12
> **sgx said:**
> The linux nanonoise app is for Korgs nice NanoKontrolNot specifically. It also works with any other MIDI controller. The nice thing about nanonoise is that it allows you to map keystrokes/combinations to MIDI events. And you also don't need Reaper for that. I'm currently using it with my Behringer BCF2000 and Qtractor. nanonoise is in my PPA also. I will try uploading a Lucid version as soon as I have some time.
For the TS nanonoise is not an option because it only handles incoming MIDI events and outputs them as keystrokes/keycombinations. And the TS needs it the other way around. VMPK could be an option but then you have the problem that you can't assign it to a specific keyboard.

---

### Post by decomp on 2010-06-28
seegreen, autostatic has found a program that does just that. it's called lsmi-keyhack. he explained it here 
[http://ubuntuforums.org/showthread.php?t=1496517](http://ubuntuforums.org/showthread.php?t=1496517)

you just configure your buttons once, and then double check which process id your keyboard gets everytime you plug it in. 

cheers

---

### Post by seegreen on 2010-07-26
lsmi-keyhack works perfectly. Thanks you very much.

---

### Post by AutoStatic on 2010-07-27
You're welcome. Good to hear that it works, I'm planning on making a MIDI footswitch pedalboard myself and I might use lsmi for it.

---

