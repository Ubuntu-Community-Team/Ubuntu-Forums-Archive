---
title: "Virtual Midi Keyboard v 1.9 makes no noise"
date: 2008-05-25
forum: Ubuntu Studio
---

### Post by sethtriggs on 2008-05-25
I have a Gateway MX6425 laptop with onboard audio. I have Timidity installed and it plays MIDI files just fine. However, I am not able to get anything to come out of the Virtual Midi Keyboard when I attempt to play it. In addition, all but the last five or six keys on the right will light up. I really want to get this working so I can noodle a bit on the keyboard and try to learn some music.

I've checked my ALSA mixer; the MIDI plugin is installed and the "Synth" output is unmuted and turned up to about 75%. It really should work, I'd think. I get the same problem with my desktop PC as well.

Is there anyone that has gotten the Virtual MIDI Keyboard working? I've searched through the forums and Google and nobody seems to have the exact issue I do.

Thanks in advance!

-Seth

---

### Post by rjmoerland on 2008-05-25
You possibly need to connect the midi port of the virtual keyboard to timidity. I only know how to do this with JACK Control, but it's very likely that there are other ways. With JACK Control: press the 'Connect' button and go to the 'MIDI' tab. Drag the output port (left side) of the virtual keyboard to timidity's input port (right side). Now Timidity should respond.

HTH

---

### Post by rjmoerland on 2008-05-25
woops, double post

---

### Post by sethtriggs on 2008-05-25
> **rjmoerland said:**
> woops, double post

Didn't get Virtual MIDI Keyboard to work, but ZynAddSUbFX works well! (I don't have all the upper and lower registers, but it works well enough for noodling at least.

Thanks for the suggestion!

-Seth

---

### Post by dlowerre on 2008-08-08
You are all right Jack!

I was able to use the Jack connections just as you suggested to get the virtual keyboard to play.

Here is a tip for chords:

 use View/Controls
 select Sustain
 Crank it UP!

Now you can create 'bell' chords.  

Thanks, rjmoerland, for your post.

Dave ;}o

---

### Post by ivanhoe75 on 2008-10-16
How to make zynaddsubfx to work with synthesizer?

---

### Post by Xoanan on 2008-10-25
I have never needed to do that;  zynaddsubfx comes with its one synth and virtual keyboard.  Works wonderfully!

---

### Post by kayosiii on 2008-10-25
Zynaddsubfx **IS** a synthesizer... So will work out of the box... Virtual midi keyboard is an app that will talk to a synthesizer that can accept midi input in much the manner you would do with a real midi keyboard - it has no sounds built in. 

To use it you need a to run a  midi patchbay application and a synthesizer. If you already have jack set up on your computer then Patchage is an excellent patchbay app. otherwise you can use qjackctl or there is an alsa app that does this and something like amsynth to plug in and make sounds.

In the patchbay app you connect the midi output of virtual keyboard to the input midi port of the synthesizer...

I bit to get your head around at first but very flexible and powerful in the long run.

---

### Post by Stamat on 2008-12-04
Jack did the thing! Thanks so much!

---

### Post by Mike-Chopper-Reeves on 2009-07-07
I've only just begun to play with music on my Ubuntu 9.04 laptop.
I'm now trying to afford a real midi keyboard to plug in!

I too have had problems & used the ZynAddSubFX synth instead but I wanted a realistic piano sound which ZASFX just doesn't do. So just yesterday I did this.

Get These Programs and start them from Applications>Sound & Video IN THIS ORDER (Important).
JACK Control
Hexter
Virtual Midi Keyboard

Once they are all running minimize Hexter after selecting prog 6 for a reasonable piano sound.

In Jack>Patchbay I made these connections by experimentation.
Hexter to playback_1 and separately
VirtualKB to Hexter

I'll send you a screenshot if you like.

Next, VMKB only comes with the QWERTY... and ...1234 rows of the computer keyboard working. But if you find and gedit the file vkeybdmap you can extend its range.
I can send you my VKeybdmap which has middle C on Q of qwerty and a second row starting on the C below middle C on Keyboard letter Z of zxcv... but it was designed for a laptop keyboard so you may have to play about with vkeybdmap to suit your computers KB

Last night I had the Hydrogen drum machine play a background  to my virtual piano. How-to-annoy-the-neighbours-101;)

Sorry about being a year late
Hope this helps
Mike

---

### Post by jago25_98 on 2009-10-01
Thanks for the tips people, especially patchage; this makes routing a lot clearer.

I now use vkeybd and aeolus no problems :-) (it's a virtual organ)

But dssi based intruments such as hexter and zynaddsubfx don't have a green MIDI-in port in patchage, so there is no way to control them afaik?
Also connected it with qjackctl and it's the same - no output. 

What happens when you try it?

By the way, the realtime kernel is easy to install (linux-rt) so lower latency is possible. Personally I now find I can select the realtime option if I run jackd as root, but then can't connect to it, only able to connect as a user.... anyway, I digress...

---

### Post by Firepowerforfreedom on 2009-10-08
I need some help with this process. I'm new to Ubuntu and don't know how to get MIDI working with Virtual Keyboard on this thing.
What plugins do I need to install from Synaptic?
I saw a "midi plugin" mentioned above with the ALSA mixer. What is it and how do I get it?

---

### Post by Nabo00o on 2011-02-19
> **Firepowerforfreedom said:**
> I need some help with this process. I'm new to Ubuntu and don't know how to get MIDI working with Virtual Keyboard on this thing.
What plugins do I need to install from Synaptic?
I saw a "midi plugin" mentioned above with the ALSA mixer. What is it and how do I get it?

Hi, its too bad that its been almost a year and a half without any replies to you.
Well, as to how to get midi working, it depends on what you want.

If you have a real midi keyboard there are several ways of using it by driving a synth/sound-generator with its midi input.
If you don't have a real keyboard, you can "substitute" it with a virtual keyboard. In one of those (there are several) you can use the computer keyboard instead as the keys, and even use the mouse to click and drag on notes. Its hard to do anything productive with that, but it helps you to test sound and setups.

Yet another way is to drive a synth with a program that can generate these midinotes for you, called a sequencer. In linux there are a lot of programs that can do this, many of them can both read midi music files and music you make in them. Rosegarden is one example.
Timidity is an all-in-one program, it opens and reads midi files and convert them into sound, by using soundbanks, so it is sampling instead of synthesizing.


Now, say you want to play midi songs, then in all likelihood it will be easiest to use timidity.
On ubuntu there follows a very small soundbank which timidity then uses, but it doesn't sound great. One free, great-sounding bank is called FluidGM, its 140 MB large so it will take some space (in harddrive and memory) but I think you will find it worthwhile.

You can download it in the Ubuntu software center by searching for: fluid-soundfont-gm
The next step is then to change Timidity so that it can use it, sadly this involves using a terminal but it is really simple.
Open up the terminal from applications > Accessories.
Inside type: gksudo gedit /etc/timidity/timidity.cfg 
Since it is located in a root protected part of your machine, you will need admin power to change it, hence the password.

When inside the cfg file, two lines needs to be changed. 
source /etc/timidity/freepats.cfg
#source /etc/timidity/fluidr3_gm.cfg

By switching the comment-out function like this

#source /etc/timidity/freepats.cfg
source /etc/timidity/fluidr3_gm.cfg

you change which sound bank is used. After you have done this, Timidty should be able to play all your midi music with good quality, however there exist some other, even larger sound banks to play with in the future if needed.


Since you now already have a good soundfont on your comp, you are a lot closer to play with midi music through an external midi device (like a keyboard), or the virtual keyboards you can download.
I haven't found that many good synthesizers in linux yet to be honest, BUT, there is a way to get VSTs like FM7/8 and Absynth working on ubuntu. However that is still hard and seems to be very buggy. One good native synth though is the Alsa Modular Synth, which contradictory to its name doesn't really work that well on alsa anymore :)
Its best to use with the Jack audio server instead, you should probably read about that here: [http://jackaudio.org/](http://jackaudio.org/)

Then, if you want to play with instruments in the fluid soundfont through a keyboard, you will need a program which generates sound from the midi inputs and the soundbank. This is were fluidsynth comes in! Fluidsynth is without a visual front-end (like jack) so in the ubuntu software center you download a program called Qsynth (and qjackctl also if you haven't yet). 

It will probably take too long to give you instructions on how to use everything, but these setups have a lot of possibilities. If you want to change or make midi files you should look into Rosegarden: [http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

Lastly, to get the FluidGM soundfont working in qsynth, you have to specify were it is, which should be here: /usr/share/sounds/sf2/FluidR3_GM.sf2


I hope this has been helpful to you and anybody else wondering about midi in linux!
Julian

---

### Post by tredsyn on 2011-10-12
> **rjmoerland said:**
> You possibly need to connect the midi port of the virtual keyboard to timidity. I only know how to do this with JACK Control, but it's very likely that there are other ways. With JACK Control: press the 'Connect' button and go to the 'MIDI' tab. Drag the output port (left side) of the virtual keyboard to timidity's input port (right side). Now Timidity should respond.


On my set-up, nothing was showing up under "midi", it's under "alsa" though. Now it's working :D 

> **dlowerre said:**
> 
Here is a tip for chords:

 use View/Controls
 select Sustain
 Crank it UP!

Now you can create 'bell' chords.  

wow there's a lot to play with :D
use View/program list

---

### Post by sgx on 2011-10-13
To get a port in the normally empty midi tab, install a2jmidid

and after starting jackd, use the command:

a2jmidid -j default.

You will now see a jackd midi port, useful for
Yoshimi synthesizer. Depending on your soundcard,
you connect both midi-through ports in the alsa tab,
the midi port to yoshimi, and in the audio tab,
yoshimi to system playback.
Among other uses.
Cheers

---

