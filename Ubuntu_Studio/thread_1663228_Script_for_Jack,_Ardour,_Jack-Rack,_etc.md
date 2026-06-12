---
title: "Script for Jack, Ardour, Jack-Rack, etc"
date: 2011-01-09
forum: Ubuntu Studio
---

### Post by pakito15191 on 2011-01-09
I was looking for a way to do a shell script to start several programs at the same time, in this case I could want to start Jack, Ardour and Jack-Rack at the same time, and in the future I'd maybe want to add some others
I wasn't sure if the question had to be here or in Scripts, but as this could help to lots of musicians, I posted it here
what I have is this

[HTML]
#!/bin/bash
/usr/bin/qjackctl
jack-rack
/usr/bin/ardour2

[/HTML]but it doesn't work, as jack-rack waits until jack finish, and I want they both working at the same time, I was thinking about some multi-threat shell script, or to the script not to wait an answer from the previous programs, but I'm not sure if this is possible :confused:

Thanks for the help!

PS, sorry for my English.

---

### Post by AutoStatic on 2011-01-09
Try adding an & (ampersand) after the commands, this will run them in the background.

```
#!/bin/bash
/usr/bin/qjackctl &
jack-rack &
/usr/bin/ardour2
```

I script all my sessions too, but there are other options like Ladish and JACK Session Management. And check this tutorial, it might come in handy: [http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)
I do it a bit differently though, less elaborate ;) An example:

```
#!/bin/bash
export SESSIONDIR=$HOME/Sessions/unawareofadirection.d

hydrogen -s $SESSIONDIR/unawareofadirection.h2song &
sleep 3
phasex -m 5 $SESSIONDIR/electro-lead-clean.phx &
sleep 3
phasex -m 4 $SESSIONDIR/harsh-saw.phx &
sleep 3
guitarix -r default -f $SESSIONDIR/guitarix_amp_rc &
yoshimi -N pizzi --state=$SESSIONDIR/pizzicatostrings.state &
sleep 2
yoshimi -N sharp --state=$SESSIONDIR/sharpsynth.state &
sleep 2
qtractor $SESSIONDIR/unawareofadirection.qtr &
sleep 3
export HYDROGEN=$(jack_lsp | grep "Hydrogen Midi-Out")
export QTRACTOR=$(jack_lsp | grep "(capture): Yoshimi Warm Synth")
jack_connect Hydrogen:Track_12_Bass_L guitarix_amp:in_0
jack_connect "$HYDROGEN" yoshimi-pizzi:midi\ in
jack_connect "$HYDROGEN" yoshimi-sharp:midi\ in
jack_connect "$QTRACTOR" yoshimi-sharp:midi\ in
aconnect Hydrogen:1 phasex-01
aconnect Hydrogen:1 phasex-02
```

---

### Post by Pablo_F on 2011-01-09
Hi, you need ampersands, and maybe some sleep. Something like this:

#!/bin/bash
/usr/bin/qjackctl &
sleep 4
jack-rack &
/usr/bin/ardour2


Note that qjackctl must be configured to start server at start up application (so jackd launches automatically with the last configuration you chose in the setup window). If you have more than one souncard this might not work unless you use card names instead of card numbers. See the word between square brackets in the output of "cat /proc/asound/cards" and name it like this in qjackctl's setup (even if it does not appear in the drop down menu): hw:name

Cheers! Pablo

---

### Post by Pablo_F on 2011-01-09
By the way, I don't see the point of using jack-rack if you are using ardour which is also a ladspa host. See:

[http://en.flossmanuals.net/Ardour/UsingPlugIns](http://en.flossmanuals.net/Ardour/UsingPlugIns)

---

### Post by MeGodzillaUDead on 2011-01-15
Good thread pakito, I had alot of trouble with this one at first too.  Long story short I had to start the JACK server manually and then launch QJackctl.  When starting JACK I had to send the output of stdout and stderr to /dev/null in order to execute other commands; is this a bad practice?  Have other people experienced this?  Would the sleep command work better? Here is the text of my script, thanks for any help!

 #!/bin/bash
 echo "Staring JACK Audio Connection Kit..."
jackd -t 1000 -d alsa -r 44100 -p 64 -n 3 -X raw &> /dev/null &
qjackctl&

---

### Post by pakito15191 on 2011-01-16
Thanks for all the answers! It really helped me! I didn't even know how Jack Rack worked at the time I wrote this, I just installed it, but I wanted to know how to make this kind of scripts to work.

---

