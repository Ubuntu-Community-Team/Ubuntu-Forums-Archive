---
title: "Two soundcards simultaneously: one for jack and one for pulseaudio"
date: 2010-07-10
forum: Ubuntu Studio
---

### Post by jorgealfonso on 2010-07-10
Hello,

Ever since I moved to Ubuntu Studio I've been having the issue of having to switch sound servers all the time: common applications (skype, firefox, etc) work ONLY with pulse audio, while music production applications require jack.

I've never managed to use pulseaudio through jack (and it seems that it's not a very good idea performance-wise anyway...)

So I was wondering: **would it be possible to run both jack and pulse audio SIMULTANEOUSLY if I have 2 sound cards?** (each card dedicated to one server)

I just bought a good external firewire sound card to produce music, in top of the internal-simple that comes with my laptop. Both are working OK with jack (only one at a time, of course).

Ideally, **the cheap-built-in-card would be dedicated to pulse audio, while the external would be dedicated to jack only**.

This would allow me to use any application at any time! It is NOT a problem if both cards can't interact with each other.

Thanks a lot for your advice! ;)

---

### Post by markbuntu on 2010-07-12
Yes, that is possible, I have been doing it since Hardy. If you are using Lucid I am not so sure exactly how to do it since I am not using Lucid yet but it should be fairly easy since the pulse-jack modules are in the Lucid repository. 

If you start pulseaudio first and load the pulse-jack modules when you start jack pulseaudio will fall over to whatever card jack is not using.

There are a bunch of old threads around here about all that.

---

### Post by trulan on 2010-07-12
If your external card is firewire, the only reason the internal card quits working when you start jack is because Jack control is suspending Pulse when you start it.  If you start Jack from the command line, or change the way Jack Control starts (don't know how to do this off the top of my head), it should work without doing anything else.

---

### Post by markbuntu on 2010-07-12
This is what I did with Hardy and jaunty and karmic, I have tried it with lucid during testing and it worked sometimes but I am too lazy to try to upgrade right now so I have not tried it in a few months. 

But anyway, you can give this a try. I have two sound cards so this works to default one to jack and one to pulseaudio but it also gives you the option to connect pulse using apps with jack for you youtube and stuff which is cool because then you can record anything from pulseaudio into ardour or whatever for sampling/remixing etc.

First, get the pulse-jack modules from the lucid repository, search pulse.

pulseaudio-module-jack-sink
pulseaudio-module-jack-source

Then you need to make a little script to load them when jack starts. I keep mine in a /scripts directory in my /home directory. Just make a new file with Nautilus called jack_startup and make it executable and put these lines in it.

Code:

#load pulseaudio jack modules
#!/bin/bash

pactl load-module module-jack-sink
pactl load-module module-jack-source

Then start up jack control and go to Setup/Options/Execute script after Startup. click on the... box and go to where the script is and click open. and then after you make sure the path is correct click the box on the left so it has an x in it. Click OK at the bottom. Make sure no application is using the sound card before you start jack or jack will not start. 

If the jack sink disappears from the Pulse Audio Volume Control after a few seconds or you do not see it, adjust the timeout in the jack control setup menu to 1000-5000. Applications that just play back audio streams through Pulse Audio are very lazy about talking to their sound server and use very large buffers so this will prevent jack from timing out the connection. 

You should now have jack sinks and sources in the Pulse Audio Volume Control. and a Pulse Audio JACK Sink and Pulse Audio JACK Source in the jack connection bay in the Audio section all connected up to system playback and system source automatically. When you close jack, the jack sinks and sources will automatically go away.

You can now start up any non-jack application and it will play through the pulseaudio-jack sink if you select it with move stream in the Pulse Audio Volume Control. You can connect the pulse audio sink to any jack application in the jack connections bay and record, add effects, eq, pretty much anything you want that jack can hook you up with.

There is a thread around here somewhere by motin that is more up to date so you should probably look around for that, I think it might be in the ubuntu-studio section. Also, I am not sure but there seemed to be some problems with the udev rules concerning jack and pulseaudio at some point in the lucid testing. Like I said I have not tried this lately but it should do no horrible unrecoverable damage to your system if it does not work.

---

### Post by jorgealfonso on 2010-07-17
**trulan> **Wow, that was simpler than I expected! :D

On jack control setup there is an option "Execute script on Startup", that was enabled with this line:

```
artsshell -q terminate
```

This should be the command stopping pulseaudio. I unchecked the box to prevent it from running at startup, restarted the server, and that's it!

I have now jack working on my firewire soundcard, and pulseaudio on the laptop speakers :)


**marcubuntu> **That worked as a charm too! if I enable the script, I get pulseaudio running over jack.

I can even run the script (from a terminal) WHILE I have the setup described above (pulseaudio running on one card and jack running on the other card) and it will transfer the pulseaudio sinks to jack ON THE FLY! I don't even need to stop/restart anything! :D

Have some of the elements of this setup been improved lately? I remember trying to run the pulseaudio sinks over jack some months ago without much success... and now everything worked oh-so-smoothly! :)


Two more questions:
[LIST]
[*] Is there a way to make to PREVENT the *Pulseaudio JACK Sink* from connecting AUTOMATICALLY to *system playback*? I have a patchbay doing the routing that I want (which is different to the default one), so I get connections duplicated and I need to manually disconnect everything. I googled around for a solution without much results...
[*] The sinks still crash from time to time, even with 1000ms timeout... running "pactl load-module module-jack-sink" from a terminal gets it back to life easily. Is there a way to make this line to be invoked automatically, or some other way to make it persistent?
[/LIST]

---

### Post by jorgealfonso on 2010-07-17
> Is there a way to make to PREVENT the Pulseaudio JACK Sink from connecting AUTOMATICALLY to system playback? I have a patchbay doing the routing that I want (which is different to the default one), so I get connections duplicated and I need to manually disconnect everything. I googled around for a solution without much results...

Found it! just need to add "connect=0" as a parameter

```
pactl load-module module-jack-sink connect=0
```

Source, and more details, [here]("http://pulseaudio.org/wiki/Modules#module-jack-sink")

> 
**module-jack-sink**

This module implements a PulseAudio sink that connects to JACK and registers as many output ports as requested.

sink_name

The name for the PulseAudio sink. If omitted defaults to jack_out.

server_name

The JACK server to connect to. If omitted defaults to the default server.

client_name

The client name to tell the JACK server. If omitted defaults to PulseAudio.

channels

Number of channels to register. If omitted defaults to the number of physical playback ports of the JACK server.

connect

Takes a boolean value. If enabled (the default) PulseAudio will try to connect its ports to the physical playback ports of the JACK server

module-jack-source

This module implements a PulseAudio source that connects to JACK and registers as many input ports as requested. Takes the same arguments as module-jack-sink, except for sink_name which is replaced by source_name (with a default of jack_in) for obvious reasons.

---

