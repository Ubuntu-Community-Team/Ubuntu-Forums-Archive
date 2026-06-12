---
title: "Can't hear Oxygen 25"
date: 2013-04-09
forum: Ubuntu Studio
---

### Post by 33Nicolas on 2013-04-09
I've read most of the threads associated wth getting this synth connect and I see Phasex and QSynth see it but I can't get the sound through.

I'm no expert wth MIDI interfaces coming frm the world of jacks and amps :guitar:

thanks fr any help you can shed. I'm stoked about Studio!

---

### Post by jejeman on 2013-04-09
It is a MIDI controler not a synth. So, there is no sound from it just MIDI messages.

---

### Post by 33Nicolas on 2013-04-10
Righto, so how do I used it as a synth? That's the part I'm stumbling on. I've searched as well as I could and have seen various messages but none saying how you can use it once detected, MIDI or not, apparently in this case.

---

### Post by 33Nicolas on 2013-04-10
I'm also getting a slew of borken pipes. Wow, tough little thing...

---

### Post by jejeman on 2013-04-10
> **33Nicolas said:**
> I'm also getting a slew of borken pipes. Wow, tough little thing...
What?
Plug it and give us
```
amidi -l
```

---

### Post by 33Nicolas on 2013-04-10
Does this make sense?

Dir Device    Name
IO  hw:2,0,0  Oxygen 25 MIDI 1

---

### Post by 33Nicolas on 2013-04-10
Oh and this is what I'm getting under QSynth:

 fluidsynth: warning: Requested 2 periods, got 3 instead

---

### Post by jejeman on 2013-04-12
> **33Nicolas said:**
> Righto, so how do I used it as a synth?Just to be formaly clear - You can not use it as a synth, but only as a controller for a synth.

Now, I'll give you a simple example using AMsynth and Korg Nanokey.
With Nanokey pluged in I get
```
$ amidi -l
Dir Device    Name
IO  hw:1,0,0  nanoKEY MIDI 1
```Exactly as you get with your Maudio, which means hardware is okay.
For the synth I'm choosing AMsynth because it works without JACK, and it is very simple and straightforward. Also it is preinstalled in UbuntuStudio. If not install it.
Start AMsynth, it will automaticly use ALSA. Then see what MIDI clients you have active
```
$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'nanoKEY' [type=kernel]
    0 'nanoKEY MIDI 1  '
client 128: 'amSynth' [type=user]
    1 'amSynth MIDI OUT'
$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'nanoKEY' [type=kernel]
    0 'nanoKEY MIDI 1  '
client 128: 'amSynth' [type=user]
    0 'amSynth MIDI IN '
```
Now connect MIDI controler to soft synth. In my case it is
```
$ aconnect 20:0 128:0
```
Try this. If it works we can then go further using JACK.

---

### Post by 33Nicolas on 2013-04-26
Thanks Jejemen, you don't know how much I appreciate your help.

OK:

Dir Device    Name
IO  hw:2,0,0  Oxygen 25 MIDI 1


It sees it.  Then:

aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 24: 'Oxygen 25' [type=kernel]
    0 'Oxygen 25 MIDI 1'
 So now I will connect the Oxygen with the correct MIDI path, I assume: 14:0 24:0 which doesn't work.

I'm one step closer now. I didn't know how to route things. Any more insights will be greatly appreciated!

---

### Post by jejeman on 2013-04-26
First, you didn't list the output and input ports, just input
```
aconnect -i
aconnect -o
```Second, connecting Maudio and MIDI thru will give you nothing.
List all ports and then connect: input>output
Install amsynth if you don't have it, run it, and try to connect it with hardware, like me.

---

### Post by gnuman on 2013-05-06
To the OP,

I just installed Ubuntu studio this last weekend and tested it out with several midi controllers, including the Oxygen 25.  It took me a little while to figure out how Jack was working with the software synths, but I was able to get it all working using nothing other than Jack--which is how it should be, IMO.  I'll admit that adding on a digital audio interface (Presonus 22VSL) was just a bit too much to try to sort out at once, so connecting the Oxygen 25 via USB was much easier.  If you're not using an audio interface, I can try to lead you through getting it working.  :)

---

