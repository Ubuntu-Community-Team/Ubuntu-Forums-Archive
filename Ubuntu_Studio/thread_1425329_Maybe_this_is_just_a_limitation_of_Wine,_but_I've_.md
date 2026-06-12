---
title: "Maybe this is just a limitation of Wine, but I've got a problem."
date: 2010-03-08
forum: Ubuntu Studio
---

### Post by Everynameistaken on 2010-03-08
So I'm trying to get Guitar Rig 4 working in Wine.  I've been following some of the tutorials for getting other Jacked/WineAISO stuff to work and it seems like I've got everything pretty much worked out, but it's not working.

I've got input and output working fine in my Ubuntu sound properties, I've got an option to use WineAISO in Guitar Rig's properties, but I've got no input or output in Guitar Rig.

I'm pretty green about this stuff, so maybe I'm doing something totally wrong here.

---

### Post by sgx on 2010-03-09
> **Everynameistaken said:**
> So I'm trying to get Guitar Rig 4 working in Wine.  I've been following some of the tutorials for getting other Jacked/WineAISO stuff to work and it seems like I've got everything pretty much worked out, but it's not working.

I've got input and output working fine in my Ubuntu sound properties, I've got an option to use WineAISO in Guitar Rig's properties, but I've got no input or output in Guitar Rig.

I'm pretty green about this stuff, so maybe I'm doing something totally wrong here.
Hi, GR4 standalone needs a sound source, so load Hydrogen, zynaddsubfx, any linux 'music instrument', and connect it to GR4 in the qjackctl gui. You would do the same for the rakarrack linux fx processor. If you have a soundcard/chip line-in, that can be connected to GR4 in qjackctl to, GR4 will then fx whatever comes through the line-in, pre-amped guitar/vocal, audio output from a hardware synthesizer etc

For the plugin version of GR4,  you will need  some vst host and wine/wineasio. Reaper, windows EnergyXT2, Cantabile 1.2, and discodsp Highlife will probably work, and perhaps the command fst path-to/name.dll. (insert a * in spaces of a windows path! as in Program*Files )Some of these apps do automatic connection to jackd, others you may need to doublecheck. N.I. reps always say you must run the standalone version of their softwares once before you run the plugin version. 

You will need to make sure GR4 has at least a default internal rig, an
amp and a cab, the pedals and racks are extra. 

In the following, loosely insert GR4 standalone for Rakarrack. (or install and use Rakarrack, its a great multi-fx setup.)

 If qjackctl is not installed, install it with synaptic, start it, and check the settings to insure the right soundcard is in use. See the 
Input Device  >  
Output Device  >

Click the  >  and soundcards/chips recognized will be listed, choose which one to use. 

On the Settings panel of qjackctl, if the 'realtime' box has its box ticked, undo that for now, and restart jackd, then start Rakarrack, and the sound source it will need, and connect them in qjackctl.  You must tick the 'FX On' box in the upper left of the gui, make sure your volume is low first time.

I use a preamp with a line-out to connect guitar to Rakarrack, press the qjackctl 'Connect' button, and a 3-tab page opens, the audio tab, has system (input) on the left, and System (output) on the right. So select your guitar line-in on the left, and Rakarrack on the right, and press the 'Connect' button on THIS page, and a line appears between them. Next,
select Rakarrack on the left side, and System (output) on the right side, and press connect again. Now whatever is cabled to your soundcard line in will be affected by Rakarrack, and sent to the soundcard. 

To connect a midi keyboard, use the same process, and also make connections in the Alsa tab, rightmost of the three tabs. So if you
start zynaddsubfx, (again, same user for the entire session) and you have connected midi devices on your computer, they appear in the Alsa tab,
so connect zynaddsubfx on the right, to your soundcard midi on the left. You may see Rakarrack already connected there.

Cheers

---

### Post by sgx on 2010-03-09
Hi again, to verify, I got the GR3 demo running in wine with both
Reaper and Cantabile12lite (a free 4 plugin version of
Cantabile -which is up to V2 now.) 

I ran the GR3 installer, and you will also need to run their Service Center, or if you have a windows partition, you can just copy all the NI
folders to you wine equivalents. GR3 does have some fine sounds, I've
read that GR4 is a big improvement.
Cheers

---

### Post by sgx on 2010-03-10
more testing for guitar addicts,
I set up a Guitar Rig 3 in Reaper, loaded a drum and bassline
on another track, with the 'import media file' menu,  sent the guitar
output to Rakarrack for even more fx, and recorded the whole thing
with timemachine. 

In a different session, I used fst to start LePou's Poulin Hybrit Fullstack (excellent free amp-sim) loaded free impulse response .wavs in both its cabinets, and then loaded some Kjaerhaus classic fx selections (free in the Computer Music Magazine dvd each month),
then use qjackctl to connect the misc fx, and connect the end of the chain to the system line-in, and then some pick'n an strumm'n.

---

