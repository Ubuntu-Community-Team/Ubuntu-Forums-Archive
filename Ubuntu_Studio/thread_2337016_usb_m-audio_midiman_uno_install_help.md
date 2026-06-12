---
title: "usb m-audio midiman uno install help"
date: 2016-09-13
forum: Ubuntu Studio
---

### Post by fbfrankb5 on 2016-09-13
How do i install this?

i tried installing the firmware from an oooold ubuntu forum post.

worked in other linux distributions. but i guess it is more complicated in ubuntu studio. 

help
thanks  :-)

---

### Post by fbfrankb5 on 2016-09-13
i did [COLOR=#000000][FONT=&quot][I]amidi -l and it reads

[/I][/FONT][/COLOR]Dir Device    Name
IO  hw:1,0,0  MidiSport 1x1 MIDI 1

but the little virtual keyboard doesnt output midi to my external sampler

---

### Post by fbfrankb5 on 2016-09-13
also, i tried to run the Jack keyboard and it said " could not connect to jack server, run jackd first?" and i did and nothing

---

### Post by fbfrankb5 on 2016-09-13
I get this message when i start Qjackctrl

[COLOR=#999999]14:53:10.373 Statistics reset.[/COLOR]
[COLOR=#cccc99]14:53:10.397 ALSA connection change.[/COLOR]
[COLOR=#999999]14:53:10.526 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
[COLOR=#66cc99]14:53:10.718 ALSA connection graph change.[/COLOR]

---

### Post by CrocoDuck on 2016-09-17
At first sight it seems to me that your hardware is working correctly and that you just don't know how to use the software. There are [excellent tutorials]("http://libremusicproduction.com/tutorials?") at [Libre Music Production]("http://libremusicproduction.com/"). I suggest to have a good read at [this]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") first. The tutorial focus on audio paths, but jack is intended to manage MIDI as well. It works in complete analogy with audio, but you use the ALSA and MIDI tabs instead in the connection window of Qjackctl. You can create bridges between the two tabs with a2jmidid if needed. Hope it helps.

---

### Post by fbfrankb5 on 2016-09-19
ok, thanks

---

