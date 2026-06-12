---
title: "a wee bit lost"
date: 2010-05-25
forum: Ubuntu Studio
---

### Post by andru183 on 2010-05-25
hello my helpful friends, ive moved to ubuntu studio for home recording, ive done a bit in windows so i know a thing or 2, trouble is ive only been with ubuntu about a year so im not very knowable

i have an electric kit and an emu 0404 sound card connected via midi, but i dont know if jacks ment to be be handling the drums in or hydrogen, but either way i cant get the drums picked up

is hydrogen ment to be used like reason drum map or is it just for writing midis?

if its not what should i use to pick up drums?

mucho thanks guys!!

---

### Post by sgx on 2010-05-25
Hi, hydrogen plays back samples arranged from kits, in patterns and sequences of patterns you place on a song grid. It does not
use midi itself, but can export midi files from patterns you
create. It is one of the best audio tools available, making your beats
on the fly, hearing the results while creating them. Two great kits are at the link below, gscw 1 and 2, scroll down that page for the link

[http://www.autodafe.net/](http://www.autodafe.net/) EDIT click the samples link, and scroll down a bit


See next post about your soundcard.

To make your own kits, out of any samples,(not just drums):


A simple new 'no brainer' how2 guide for Hydrogen 9.4 drumkits!

Make a folder called something like a1samples in your user directory (so its convieniently at the top of file-requestor lists).
Fill it with the samples for your new kit, .wav, flac, whatever Hydrogen can take.
Start hydrogen, then

1. load a drumkit that contains as many, or more drums than the kit you will be making, (the limit is 32).
2. select the first drum in the kit you loaded. (its probably already selected)
3. click the 'Instrument' button on the right side of the gui, a third of the way down.
4. click the 'Layers button' below that.
5. click the 'Delete Layer' button, even further below (this will soon remove the first drum in the kit you started from)
6. click the 'Load Layer' button, this will open a file browser, so browse to your asamples folder, and select a sample for the first drum in your kit. 
7. click the check-box by 'Filename to instrument name'.
8. click the 'Open' button. Now the name changes for the first drum in the list of the kit you started with, to the name of its replacement.
9. select the second drum from the kit you started with, and repeat steps 4 through 9 incrementally, and keep doing this repetitious process till you use all the samples you intend to.
10. now go to the Instruments menu, and choose 'Export library', and give it a name in the popup that appears.
11. now again in the Instruments menu, choose 'Save library'. Give it a name, fill in more info if desired, in the other fields, and you're done. And ready to make the next one!

Remember, Computer Music Magazine dvds are bristling with samples, just waiting for new creative homes.
Cheers

As a bonus, there is Gamelan drumkit out there for Hydrogen, if you are good at google, you can find it, and the free samples it was made from. There are more than 50 samples, so with audacity skills, the extra samples could make a second kit! The kit itself uses 32 of them, and is a hair over 18 megs of melodic goodness!

---

### Post by sgx on 2010-05-25
> **andru183 said:**
> hello my helpful friends, ive moved to ubuntu studio for home recording, ive done a bit in windows so i know a thing or 2, trouble is ive only been with ubuntu about a year so im not very knowable

i have an electric kit and an emu 0404 sound card connected via midi, but i dont know if jacks ment to be be handling the drums in or hydrogen, but either way i cant get the drums picked up

is hydrogen ment to be used like reason drum map or is it just for writing midis?

if its not what should i use to pick up drums?

mucho thanks guys!!

Yikes! i forgot about your 0404! Support for this may be incomplete.
There is a long thread here where talented coders made patches for the USB 0404, and I think the patches made it to alsa 1.23.
Are you getting any sound at all in other apps?

Also, Hydrogen requires jackd to be running, so

jackd -d alsa -r 44100

starts it, then start hydrogen, it should connect automatically.
Cheers

---

### Post by andru183 on 2010-05-26
firstly thanks very much for getting back to me

sound plays out of the card fine, i found a page on how to set it up with a bit of magic, i installed windows last night to see if it was a problem with the kit and its not, its just the 0404 in ubuntu cant take either midi in or maybe no input at all, but def no midi in

i plan on using adour, if hydrogen is just used for jotting down ideas (which i will use it for) will i need a drum map for adour so it know what sound to make for each pad or can adour handle that (like reason is to cubase in windows)

for the mean time the drum map part wont matter while i cant record from the kit

thanks for the link for the samples, there was no download section so i just went back to [http://www.autodafe.net/](http://www.autodafe.net/) incase anyone else tries to follow it and thinks its a dead site

---

### Post by sgx on 2010-05-26
Hi, just to be clear for hydrogen, if you start jackd with

jackd -d alsa -r 44100

then start qjackctl

It should show jackd as already running.

Now start hydrogen. 

In the qjackctl, press the Connect button on the main screen, and a
tabbed page opens. Each tab has left and right sides, read and write.

In both the Audio tab, and the alsa tab, you should see hydrogen connected
a device in the opposite side of the tab, the Audio tab is your sound,
the Alsa tab is your midi.

If this is what you see, go to the hydrogen Project menus and choose
Open demo, and select one of the songs to play, and hit the transports
play button, and loop mode to keep it going.

Cheers

---

### Post by cchhrriiss121212 on 2010-05-26
I think what the OP wants to do is to hook up his electric drum kit and record the playing via midi, then use something like hydrogen to playback the rhythms. Is that right, andru183?

sgx has explained jack and hydrogen for you very eloquently but you will need something like qtractor or Rosegarden to record midi as Ardour is focused on live instruments (no midi or vst support). Then you could run the patterns through hydorgen and into Ardour using jack if you are set on using Ardour.

The main thing to get sorted will be jack as it is the base from which you will be recording. I have not used/recorded any electric drum kits like this so I'll be interested to hear how it goes.

---

### Post by sgx on 2010-05-26
> **cchhrriiss121212 said:**
> I think what the OP wants to do is to hook up his electric drum kit and record the playing via midi, then use something like hydrogen to playback the rhythms. Is that right, andru183?

sgx has explained jack and hydrogen for you very eloquently but you will need something like qtractor or Rosegarden to record midi as Ardour is focused on live instruments (no midi or vst support). Then you could run the patterns through hydorgen and into Ardour using jack if you are set on using Ardour.

The main thing to get sorted will be jack as it is the base from which you will be recording. I have not used/recorded any electric drum kits like this so I'll be interested to hear how it goes.

Hydrogen does respond to midi keyboards, so it should work in the sequencers you mentioned. I'm more cowboy than composer, so I defer
to actual users of those apps for guidance:)

---

### Post by andru183 on 2010-05-27
thanks [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") that is what i was trying to say but seemed to have difficulty getting it across, there no chance of recording with this card in ubuntu at the moment but if i ever do find a way ill post here and message you and let you know how i got on thanks

---

### Post by mango42 on 2010-07-01
[QUOTE="sgx"]Two great kits are at the link below, gscw 1 and 2, scroll down that page for the link[/QUOTE]

Am I on dodgy ground asking more about these 'kits'? I've checked out smoors.de, cannot figure whether there's really a copyright issue involved, downloaded the .zip files, only to find they're zips-within-zips and the final decompress of **GSCW-1.h2drumkit** and **GSCW-2.h2drumkit**throws up errors on both files. Any tips?

Also, is it feasible to just go straight to each kit's .xml file in usr/share/.hydrogen/data/drumkits and load one's own samples right there in the .xml? 'twould save an awful lot of mouse-provoked RSI & boring repetition...

Re: the whole society stifling nonsense of patents and copyright, here's an excellent way forward out of the morass global cabals have led us all into:-

[http://globalresearch.ca/index.php?context=va&aid=19959](http://globalresearch.ca/index.php?context=va&aid=19959)
> Ending the Monopoly of Ideas: Compulsory Licensing in Intellectual Property - by Joshua Fulton

---

### Post by AutoStatic on 2010-07-01
mango42, the gscw kits can be found here: [http://www.autodafe.net/gscw-drum-kit-for-hydrogen-drum-machine.html](http://www.autodafe.net/gscw-drum-kit-for-hydrogen-drum-machine.html)

Just download the zips, unzip them and import the h2drumkit files in Hydrogen. And maybe the Big Mono kit is interesting too: [http://linux.autostatic.com/hydrogen/BigMono.h2drumkit](http://linux.autostatic.com/hydrogen/BigMono.h2drumkit)

---

### Post by sgx on 2010-07-01
Big Mono is a nice set, I recorded the beats in audacity, and made a Hydro kit, sounds good enough to pay for diskspace ;)

Running hydro through multiple Rakarracks can exponentially alter your rythym section. Especially the
5.8 versions in the PPAs

---

### Post by mango42 on 2010-07-02
Thanks for the responses. I can envisage this program taking over from my drumpads-coupled-to-outboard-FX approach before long;-)

[QUOTE="AutoStatic"]mango42, the gscw kits can be found here: [http://www.autodafe.net/gscw-drum-ki...m-machine.html](http://www.autodafe.net/gscw-drum-ki...m-machine.html)[/QUOTE]

yep, that's where I got what look to be corrupted downloads - I'll try again - thanks for the reminder (have any Opera users noticed how bookmarks sometimes go missing?)

I'd been puzzling out the .h2drumkit issue and not getting anywhere until I came across a windoze-oriented blog, wherein:-

> How To Install New Drum Kits In Hydrogen Without Crashes
Download a kit from Hydrogen&#8217;s drum kit page.
Unzip the file until you have an .h2drumkit file. The .h2drumkit file is just a zip file containing a bunch of sounds (kick drum, snare, high hat, etc.) and an XML file. The file is usually a zip of a zip of a zip, so you use your favorite unzipping tool (such as 7-Zip) to unzip the .h2drumkit until you have a folder of audio files and an XML file called drumkit.xml.
Open the drumkit.xml in your favorite text editor (Notepad++, anyone?) make note of the line that looks like <name>DrumKitName</name>.
Create a folder under <installation dir>\Hydrogen \data \drumkits that is named exactly the same as what you found between <name> and </name> in the drumkit.xml file. If the folder that you create isn&#8217;t exactly the same as the name line, Hydrogen will crash when you try to use the drum kit.
Copy all of the files that you unzipped in Step 2 into the folder you created in Step 4.
Now, open Hydrogen and click on &#8220;Sound Library&#8221; and your new kit should be available under &#8220;System drumkits&#8221;.

Presumably on 'our' OS, for new kits to be recognised, they need to go into /usr/share/.hydrogen/data/drumkits from root?

---

### Post by sgx on 2010-07-02
/usr/share/hydrogen/data is where the drumkits and other folders reside.
The /home/usr/.hydrogen/data is where saved songs, patterns, and midi files can go. Can be the source of an addiction issue if one engages the imagination :) .

---

### Post by AutoStatic on 2010-07-02
[LIST]
[*]Open Hydrogen
[*]Click Instruments in the menu
[*]Click Import Library
[*]Select Local File tab
[*]Browse to your h2drumkit file
[*]Click Install[/LIST]

---

### Post by mango42 on 2010-07-02
LOL. That sounds *way* too easy!

However, thanks for steering me back onto a sane(r) path {;-)

@**sgx**: Imagination fully engaged - shame about reality... :popcorn:

---

