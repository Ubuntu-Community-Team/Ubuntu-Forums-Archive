---
title: "Automatically connect MIDI in JACK?"
date: 2012-01-23
forum: Ubuntu Studio
---

### Post by lykwydchykyn on 2012-01-23
I'm pretty new to JACK and doing audio stuff on Linux, I just recently got my rig set up again.

I like to audition different software synths, and wondered if there's a way to make them automatically connect their MIDI inputs to a specific MIDI source when I launch them, the way some synths do with audio connections?  

It's getting a little tiresome manually connecting stuff each time I want to audition a different synth.

---

### Post by jejeman on 2012-01-23
a) Check their preferences, maybe thay have option for automatic connections.

or

b) Alter the their start up with script wich uses jack_connect command.

---

### Post by lykwydchykyn on 2012-01-23
I haven't found a synth yet with auto MIDI connections; I'll look into jack_connect, maybe I can just script some of my favourite setups.

---

### Post by CivilizationII on 2012-02-20
> **lykwydchykyn said:**
> I'm pretty new to JACK and doing audio stuff on Linux, I just recently got my rig set up again.

I like to audition different software synths, and wondered if there's a way to make them automatically connect their MIDI inputs to a specific MIDI source when I launch them, the way some synths do with audio connections?  

It's getting a little tiresome manually connecting stuff each time I want to audition a different synth.


To achieve that you need to use aconnect.

aconnect -i -l   and  aconnect -o -l   will list your MIDI input/output device, then  aconnect n1 n2  (where n1 and n2 are the devices you want to connect) will do the job.

Please note that aconnect is an alsa tool, which means this is not working if you are using network remote device (usb device are ok).

---

### Post by lykwydchykyn on 2012-02-20
Will that work with instruments that use Jack MIDI?

---

### Post by CivilizationII on 2012-02-21
> **lykwydchykyn said:**
> Will that work with instruments that use Jack MIDI?


This will work for every '_**non** jackified_' midi softwares (which are still numerous)

I had only answered around aconnect tool because for pure jack/midi you already had wrote it: the solution is jack_connect.

For listing devices and their ports, send:

> jack_lsp--> will list all the '_jackified_' midi connectors _and_ sound connectors ( so choose wisely, midi output to sound input is _not_ a good idea ;) ) 

Then send:

> jack_connect ***output**_port_your_software*:*type_port* ***intput**_port_your_other_software*:*type_port*And then:

> aconnect *port_midi1* *port_midi2*will finish the job for '_**non** jackified_' devices.

You can find a very good sample of scripting the whole stuff in Ubuntu forums, i don't think it is useful to re-write it, so thank for mister AutoStatic ;):

[http://ubuntuforums.org/archive/index.php/t-1663228.html](http://ubuntuforums.org/archive/index.php/t-1663228.html)

---

