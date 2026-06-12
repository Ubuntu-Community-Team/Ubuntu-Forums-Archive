---
title: "Focusrite Saffire LE"
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by prismatic7 on 2008-05-15
I've just got a Focusrite Saffire LE (firewire audio device, that is), on the strength of FreeBoB and FFADO support for it. However, even though it's recognised by the system I can't get jackd to play nicely.

Using qjackctl, I get an error stating "cannot complete execution of the processing graph (Resource temporarily unavailable)", followed by jack crashing. Naturally there's no sound or anything... 

I'm not sure how to debug and fix this problem - can anyone help?

---

### Post by beepo on 2008-05-16
I have the same problem with M-Audio Delta 1010LT card.

With a lot of googling I was able to get pulseaudio to work at all. (This is due to a fact that the M1010LT uses ice1712 driver that has no channel named 'Master' and that craps the pulse out)

The system was working flawlessly. jackd, ardour, system sound, the works.

Then I played some guitar lesson videos with Totem firefox plugin and they did not work. The video was really slow and no sound. Tweaking the plugin enabled / disabled for some reason made the videos to display correctly but only for one web session. Didn't get it working after that at all. Huge problems by the way with almost all good video players with selecting sound driver. Totem was only one to play any sound. However Totem really is NOT my favourite video player (or audio for that matter)

I don't know if it's anyway related but now I don't have any sound. The pulse audio for some reason does not start any more and jackd was complaining that the alsa hw:0 was already in use.

So I removed the pulseaudio with apt-get and reinstalled alsa. Reboot. Still the system complains the hw:0 is in use.

So I restarted alsa with sudo /sbin/alsa force-reload

After that jackd starts up (using qjackctl) but gives me a tons of 'cannot complete execution of the processing graph (Success)' and then
jackd: no process killed

---

### Post by beepo on 2008-05-16
Oh yeah, forgot to mention that I will really soon install Ubuntu Studio 7.10 back if this is really the story with hardy. Gutsy version worked without a single hickup.

---

### Post by prismatic7 on 2008-05-16
No, I don't think we have the same problem at all. Mainly because I'm using **jackd** and a **firewire audio card** and I'm not doing anything with pulseaudio (`pasuspender qjackctl` is your friend)

Look, here's the log output:

```
17:53:42.703 Patchbay deactivated.
17:53:42.756 Statistics reset.
17:53:42.765 ALSA connection graph change.
17:53:42.963 ALSA connection change.
17:54:12.979 Startup script...
17:54:12.979 artsshell -q terminate
17:54:13.401 Startup script terminated with exit status=256.
17:54:13.401 JACK is starting...
17:54:13.402 /usr/bin/jackd -v -R -P89 -m -dfreebob -dhw:0 -r48000 -p256 -n2 -D
17:54:13.404 JACK was started with PID=12942.
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x8070108 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 256
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG: Using FreeBoB lib version libfreebob 1.0.7
LibFreeBoB MSG: Device information:
LibFreeBoB MSG: Device options:
LibFreeBoB MSG: Port : 0
LibFreeBoB MSG: Device Node Id : -1
LibFreeBoB MSG: Samplerate : 48000
LibFreeBoB MSG: Period Size : 256
LibFreeBoB MSG: Nb Buffers : 2
LibFreeBoB MSG: Directions : 0
showDevice: not implemented
17:54:14.039 ALSA connection graph change.
FreeBoB MSG: Register MIDI IN port dev1c_Midi In
FreeBoB MSG: Register MIDI OUT port dev1p_Midi Out
FreeBoB MSG: Streaming thread running with Realtime scheduling, priority 93
FreeBoB MSG: Registering audio capture port C0_dev1c_Rec 1
FreeBoB MSG: Registering audio capture port C1_dev1c_Rec 2
registered port system:capture_1, offset = 1024
registered port system:capture_2, offset = 2048
FreeBoB MSG: Registering audio capture port C2_dev1c_Rec 3
FreeBoB MSG: Registering audio capture port C3_dev1c_Rec 4
FreeBoB MSG: Registering audio capture port C4_dev1c_Rec 5
FreeBoB MSG: Registering audio capture port C5_dev1c_Rec 6
FreeBoB MSG: Don't register capture port for dev1c_Midi In
FreeBoB MSG: Registering playback audio port P0_dev1p_Play 1
FreeBoB MSG: Registering playback audio port P1_dev1p_Play 2
FreeBoB MSG: Registering playback audio port P2_dev1p_Play 3
FreeBoB MSG: Registering playback audio port P3_dev1p_Play 4
FreeBoB MSG: Registering playback audio port P4_dev1p_Play 5
FreeBoB MSG: Registering playback audio port P5_dev1p_Play 6
FreeBoB MSG: Registering playback audio port P6_dev1p_Play 7
FreeBoB MSG: Registering playback audio port P7_dev1p_Play 8
FreeBoB MSG: Don't register playback port dev1p_Midi Out
registered port system:capture_3, offset = 3072
registered port system:capture_4, offset = 4096
registered port system:capture_5, offset = 5120
registered port system:capture_6, offset = 6144
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
registered port system:playback_3, offset = 0
registered port system:playback_4, offset = 0
registered port system:playback_5, offset = 0
registered port system:playback_6, offset = 0
registered port system:playback_7, offset = 0
registered port system:playback_8, offset = 0
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
FreeBoB MSG: MIDI threads running with Realtime scheduling, priority 92
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
12942 waiting for signals
17:54:14.219 ALSA connection change.
17:54:15.434 Server configuration saved to "/home/chris/.jackdrc".
17:54:15.435 Statistics reset.
17:54:15.436 Client activated.
17:54:15.439 JACK connection change.
17:54:15.442 JACK connection graph change.
new client: qjackctl, id = 2 type 2 @ 0xb7ed6000 fd = 17
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client qjackctl: wait_fd=16, execution_order=1 (last client).
-- jack_rechain_graph()
load = 2.1283 max usecs: 227.000, spare = 5106.000
load = 3.2393 max usecs: 232.000, spare = 5101.000
load = 3.8041 max usecs: 233.000, spare = 5100.000
load = 3.9084 max usecs: 214.000, spare = 5119.000
load = 3.9043 max usecs: 208.000, spare = 5125.000
load = 4.0804 max usecs: 227.000, spare = 5106.000
load = 4.2060 max usecs: 231.000, spare = 5102.000
load = 4.1469 max usecs: 218.000, spare = 5115.000
load = 4.0798 max usecs: 214.000, spare = 5119.000
load = 4.0088 max usecs: 210.000, spare = 5123.000
load = 4.0951 max usecs: 223.000, spare = 5110.000
new client: hydrogen-tmp, id = 3 type 2 @ 0xb7ed5000 fd = 20
removing disconnected client hydrogen-tmp state = Not triggered errors = 0
removing client "hydrogen-tmp"
removing client "hydrogen-tmp" from the processing chain
17:54:27.964 JACK connection graph change.
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client qjackctl: wait_fd=16, execution_order=1 (last client).
-- jack_rechain_graph()
new client: Hydrogen-1, id = 4 type 2 @ 0xb7ed5000 fd = 20
registered port Hydrogen-1:out_L, offset = 7168
registered port Hydrogen-1:out_R, offset = 8192
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client Hydrogen-1: in subgraph after qjackctl, execution_order=1.
client qjackctl: wait_fd=19, execution_order=2 (last client).
-- jack_rechain_graph()
unknown destination port in attempted connection [alsa_pcm:playback_1]
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client qjackctl: wait_fd=16, execution_order=1 (last client).
-- jack_rechain_graph()
removing disconnected client Hydrogen-1 state = Not triggered errors = 0
removing client "Hydrogen-1"
removing client "Hydrogen-1" from the processing chain
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client qjackctl: wait_fd=16, execution_order=1 (last client).
-- jack_rechain_graph()
17:54:28.018 ALSA connection graph change.
17:54:28.060 ALSA connection change.
load = 3.1445 max usecs: 117.000, spare = 5216.000
load = 3.5505 max usecs: 211.000, spare = 5122.000
load = 3.7160 max usecs: 207.000, spare = 5126.000
load = 3.9019 max usecs: 218.000, spare = 5115.000
load = 4.0792 max usecs: 227.000, spare = 5106.000
load = 3.9522 max usecs: 204.000, spare = 5129.000
load = 4.0106 max usecs: 217.000, spare = 5116.000
load = 4.1242 max usecs: 226.000, spare = 5107.000
load = 4.2091 max usecs: 229.000, spare = 5104.000
load = 4.2797 max usecs: 232.000, spare = 5101.000
load = 4.3337 max usecs: 234.000, spare = 5099.000
load = 4.2482 max usecs: 222.000, spare = 5111.000
load = 4.2055 max usecs: 222.000, spare = 5111.000
load = 4.0622 max usecs: 209.000, spare = 5124.000
load = 4.1688 max usecs: 228.000, spare = 5105.000
load = 4.1095 max usecs: 216.000, spare = 5117.000
17:54:48.050 ALSA connection graph change.
17:54:48.051 Shutdown notification.
17:54:48.055 JACK is stopping...
17:54:48.056 JACK is being forced...
cannot complete execution of the processing graph (Success)
zombified - calling shutdown handler
17:54:48.063 JACK has crashed.
17:54:48.096 ALSA connection change.
17:54:48.257 JACK was stopped successfully.
17:54:48.257 Post-shutdown script...
17:54:48.257 killall jackd
jackd: no process killed
17:54:48.667 Post-shutdown script terminated with exit status=256.
17:54:57.200 ALSA connection graph change.
17:54:57.303 ALSA connection change.
```

I know a number of users on this forum claim to have got this device working 'out of the box', so I'd really, really like to hear from someone who is using Focusrite Saffire-series devices - no offence, **beepo**, but I've got an M-Audio Delta 44 that works perfectly with Ubuntu (just not on a laptop, obviously)...

---

### Post by robeast on 2008-05-17
Is this the device that warranted the new freebob release? You may need to compile that from source and see what happens.

---

### Post by prismatic7 on 2008-05-17
> **robeast said:**
> Is this the device that warranted the new freebob release? You may need to compile that from source and see what happens.

I don't believe it is, but I can't find any information to back up that belief. 

I've got a bit further - the problem with Hydrogen's driver seems to be that the ~/.hydrogen/hydrogen.conf uses the deprecated alsa_pcm:playback swtich rather than system:playback, ie:

Change:
```

      <jack_driver>
            <jack_port_name_1>alsa_pcm:playback_1</jack_port_name_1>
            <jack_port_name_2>alsa_pcm:playback_2</jack_port_name_2>
            <jack_transport_mode>USE_JACK_TRANSPORT</jack_transport_mode>
            <jack_connect_defaults>true</jack_connect_defaults>
            <jack_track_outs>false</jack_track_outs>
      </jack_driver>

```

to

```
    
        <jack_driver>
            <jack_port_name_1>system:playback_1</jack_port_name_1>
            <jack_port_name_2>system:playback_2</jack_port_name_2>
            <jack_transport_mode>USE_JACK_TRANSPORT</jack_transport_mode>
            <jack_connect_defaults>true</jack_connect_defaults>
            <jack_track_outs>false</jack_track_outs>
        </jack_driver>

```

Which stops the driver errors when starting Hydrogen, but I still get no sound. I seem to have found the range of jackd options that keep the driver stable - but I don't get any sound output, and transport controls don't work either.

I have read somewhere that the device needs to be 'initialised' by installing it on a Windows system first and downloading the latest firmware - does anyone know the truth of this?

---

### Post by robeast on 2008-05-20
> **prismatic7 said:**
> 
I have read somewhere that the device needs to be 'initialised' by installing it on a Windows system first and downloading the latest firmware - does anyone know the truth of this?

I've also heard this of some devices but not of the Saffire LE. I'm pretty sure that the LE is not officially supported by freebob. Since it is probably very similar to the Pro and regular saffire it should work here and there but will probably be spotty with different computers.

---

### Post by jenny_thinkpad_t61p on 2008-07-19
> **prismatic7 said:**
> 
[/code]Which stops the driver errors when starting Hydrogen, but I still get no sound. I seem to have found the range of jackd options that keep the driver stable - but I don't get any sound output, and transport controls don't work either.

I have read somewhere that the device needs to be 'initialised' by installing it on a Windows system first and downloading the latest firmware - does anyone know the truth of this?

Hi,

I've had lots of issues using the Focusrite Fapphire LE with Ubuntu 8.04 but have finally figured it out, so I may be able to assist.

1. Forget the Freebob drivers, they don't work properly with this device, I found there was no sound out and the driver would keep crashing. 

2. Forget the windows initialization thing; unless you can keep it powered between each system it's pointless, and is just not practical or necessary. If it is an older unit then updating the firmware may be a good idea but can apparently also be done in linux. My own unit serial number is an 08 (i.e. 2008) and is fine.

3. You need to install the Freebob driver, which I personally found very tricky, but the main issue is that you need to ensure that you satisfy the dependencies. Make sure you install g++ and follow the instructions on the ffado website which detail installation under Ubuntu 8.04 - but again check the dependencies, you can do this by making sure you have the dependencies for freebob:

sudo apt-get build-dep freebob

install all the depencies and follow the installation instructions for ffado AND JACK as per:

[http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)

but don't install freebob - if you have installed it remove it then run the above command.

Under 8.04 generic kernel you will get xruns and I found Jack would drop intermittently (this isn't cpu speed related).

Therefore install the package for the realtime kernel "linux-rt" 

reboot into the -rt kernel and fix your graphics card if broken. (ensure you sort the graphics driver details before rebooting)

Optionally when you have sucessfully installed and booted into the realtime kernel  you can then do a synapitc search for "ubuntu studio" and install those packages.

Don't bother running jackd in terminal unless you wish to.

Open Jack Audio Connection Kit and see if the device will start and run.

If it won't you may need to change the firewire port from default to 1. Other issues are beyond the scope of this guide and may be beyond me! but you can ask on this forum and I'll do my best, or you can subsribe to ffado-user mailing and/or ffado-dev which is well maintained and extremely helpful.

The LE version will run a samlpe rate up to 96000 and I've found it rock solid once but you may need to adjust the settings to do that and ensure you firewire connection is up to scratch as this can easily introduce problems. 

I really like "gscanbus" and personally I've found it very stable (though other's haven't) and if the device is working there then your connection is good, if there are errors or a question mark on your device in the gui then you have a more fundemental problem. Once Gscanbus is showing your system is good then your ready to install ffado with some assurance that the basic firewire is working which for me was 25% of the battle!

Also please register your device on the ffado website, when it is installed (not before).

Jenny

---

### Post by jukingeo on 2008-07-21
Hello Jenny,

So I am taking this as a "Yes" that you managed to get the Saffire LE working in Ubuntu?

I am seriously considering purchasing this card, but I DID notice that only the Saffire was listed both under the old FreeBob as well as FFADO.  The Saffire LE only had a FFADO listing.

I am a bit hesitant to buy the Saffire LE as supposedly the FFADO support is not fully completed yet.  So I wasn't sure if there were any issues or not with the LE.  Otherwise if there were still issues with FFADO, then I would opt for the original Saffire, which seems to be supported with both.  The only thing is that while the Saffire does have 192khz capability, I do prefer the 4 inputs of the the LE and I know the Saffire's DSP function will not work in Linux.  Not to mention it is $50 more.

But if you managed to get the Saffire LE to work, then great!  Do you have the full 96khz support AND midi working with that as well?

Thanx,

Geo

---

### Post by jenny_thinkpad_t61p on 2008-07-21
Hi Geo

> **jukingeo said:**
> 
So I am taking this as a "Yes" that you managed to get the Saffire LE working in Ubuntu?

Yes it is working great at up to 96khz. It really is a superb box, and I've kept it running with jack for a couple of days without any drop outs or xruns. 

I haven't used the midi myself but I can tell you that it is recognised by jack so it is fair to say that it is probably working.

>  I am seriously considering purchasing this card, but I DID notice that only the Saffire was listed both under the old FreeBob as well as FFADO.  The Saffire LE only had a FFADO listing. The Sapphire LE doesn't really work with Freebob and from what I've read and on the reasonable assumption that they are basically the same unit from the software perspective the Sapphire (standard) woudn't work reliably with freebob either. 

I tried freebob with my Sapphire LE, there was no sound out and it frequently dropped the connection.

>  I am a bit hesitant to buy the Saffire LE as supposedly the FFADO support is not fully completed yet.  So I wasn't sure if there were any issues or not with the LE.  Otherwise if there were still issues with FFADO, then I would opt for the original Saffire, which seems to be supported with both. You will likely have the same issue with the Sapphire and LE version so I wouldn't use that in your reasoning when making the purchasing decision.

My advise is download and install ffado BEFORE you buy anything, if it installs ok then your ready to connect something to it, I found that this stage can take some time if you've not done it before and is a prerequisite for the Sapphire (inc. LE). 

>  The only thing is that while the Saffire does have 192khz capability, I do prefer the 4 inputs of the the LE and I know the Saffire's DSP function will not work in Linux.  Not to mention it is $50 more. I myself struggled with this dilemma myself. For $50 it might be nice to have the Sapphire (standard version) but as I live in rip off Britain the difference is 50 pounds sterling which is significantly more. 

I was advised that the perceptual difference between the 24bit / 96 khz and 24 bit /192 khz is negligible and of course you have to worry more about the disk space it consumes, I use the device for analytical purposes and would have chosen the 192khz version if it wouldn't mean that I would be paying so much for a DSP that I'll never be able to use. 

Fact is 96khz is very detailed, I use it with a Sennheiser K6 / ME66 and it gets all the detail I need for my purposes. There may also be increased likelyhood of xruns when running at 192khz.

Personally I used the money I saved on the LE to by a better audio monitor! - and with that you CAN tell the difference :)

Also the black LE looks better with my black Thinkpad, black Sennheiser Mic, black cables and black and yellow KRK monitor; this probably isn't a big issue but most things seem to have gone black and it is nice if the match - even if they do collect dust like it's going out fashion.

Like so many things "you pay's yer money - yer takes ya choice!" There both excellent.

Jenny

---

### Post by jukingeo on 2008-07-21
Hello Jenny, thank you for getting back to me.  I been having a tough time trying to pick out a card and I kind of homed in on the Saffire LE or the Echo GINA 3G.  It is just that overall the Saffire has more features and Focusrite is more known in the industry.  Another thing is that firewire gives me the advantage to move the device to another machine easily.


> **jenny_thinkpad_t61p said:**
> Hi Geo



Yes it is working great at up to 96khz. It really is a superb box, and I've kept it running with jack for a couple of days without any drop outs or xruns. 

I haven't used the midi myself but I can tell you that it is recognised by jack so it is fair to say that it is probably working. 

That is a good sign, more then likely if you can see the port, you should be good.

> The Sapphire LE doesn't really work with Freebob and from what I've read and on the reasonable assumption that they are basically the same unit from the software perspective the Sapphire (standard) woudn't work reliably with freebob either. 

I tried freebob with my Sapphire LE, there was no sound out and it frequently dropped the connection.

You will likely have the same issue with the Sapphire and LE version so I wouldn't use that in your reasoning when making the purchasing decision.

My advise is download and install ffado BEFORE you buy anything, if it installs ok then your ready to connect something to it, I found that this stage can take some time if you've not done it before and is a prerequisite for the Sapphire (inc. LE).

I was just about to ask you that.  Because I noticed that FreeBob comes with Jack, but there must be something that had to be done to upgrade to ffado.  How can you tell that you have a successful installation of ffado without owning a firewire card? 

> I myself struggled with this dilemma myself. For $50 it might be nice to have the Sapphire (standard version) but as I live in rip off Britain the difference is 50 pounds sterling which is significantly more. 

I was advised that the perceptual difference between the 24bit / 96 khz and 24 bit /192 khz is negligible and of course you have to worry more about the disk space it consumes, I use the device for analytical purposes and would have chosen the 192khz version if it wouldn't mean that I would be paying so much for a DSP that I'll never be able to use.

That was my thinking as well.  There are very few devices that have 192k capability in the affordability bracket.  In Windows, I scored BIG with the ALESIS IO|26 which is an 8 XLR In and 8 balanced out device with phono inputs and digital inputs (both kinds) and it goes up to 192k. So it was very disheartening to find out that Alesis doesn't support it in Linux.  But I was thinking too that for most applications 96k would be enough.  But for certain critical applications or archiving old vinyl that isn't made anymore (and wasn't pressed to CD), then I would go with 192k.  But other that for testing, I never really used that mode with the Alesis unit.  I never really did a side by side comparison.  I just checked to see if it worked.

> Fact is 96khz is very detailed, I use it with a Sennheiser K6 / ME66 and it gets all the detail I need for my purposes. There may also be increased likelyhood of xruns when running at 192khz.

Really?  Is that what happened on your system when recording at that frequency?

<<Personally I used the money I saved on the LE to by a better audio monitor! - and with that you CAN tell the difference :)>>

Well, there I wouldn't fair to bad with.  Someone turned me on to KRK monitors and they are not very expensive either.  He has the little guys and I am going for the big 8" ones.

> Also the black LE looks better with my black Thinkpad, black Sennheiser Mic, black cables and black and yellow KRK monitor;

LOL!  You have the KRK's as well.  Do you have the 5" model or the 8" one?

> this probably isn't a big issue but most things seem to have gone black and it is nice if the match - even if they do collect dust like it's going out fashion.

Like so many things "you pay's yer money - yer takes ya choice!" There both excellent.

Jenny

Ahhh, Yes I remember that quote very well.  Williams Cyclone 1988 pinball machine.  One of my favorite machines.  But I believe the last word was "chances".

Anyway, thanx for the tip. Now I just need to know how to set up ffado.

Geo

---

### Post by jenny_thinkpad_t61p on 2008-07-23
Geo,

>  Really?  Is that what happened on your system when recording at that frequency? when using the generic linux kernel (not the -rt) there were more xruns at higher sampling rates.

>  LOL!  You have the KRK's as well.  Do you have the 5" model or the 8" one? I have the Rokit 6, though I would recommend the 8 as the 6 is a little underpowered.

>   How can you tell that you have a successful installation of ffado without owning a firewire card? Installing ffado can be a hurdle that you need to overcome, which is why I would recommend doing it first. 

The correct output if you have configured it is:

[http://www.ffado.org/?q=node/622](http://www.ffado.org/?q=node/622)

>  Anyway, thanx for the tip. Now I just need to know how to set up ffado. [http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)

I recommend gscanbus to check your firewire hardware is working.

If you have install problems let me know or check out the ffado user mailing list.

Jenny

---

### Post by jukingeo on 2008-07-24
> **jenny_thinkpad_t61p said:**
> Geo,

when using the generic linux kernel (not the -rt) there were more xruns at higher sampling rates.

I have the Rokit 6, though I would recommend the 8 as the 6 is a little underpowered.

Installing ffado can be a hurdle that you need to overcome, which is why I would recommend doing it first. 

The correct output if you have configured it is:

[http://www.ffado.org/?q=node/622](http://www.ffado.org/?q=node/622)

[http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)

I recommend gscanbus to check your firewire hardware is working.

If you have install problems let me know or check out the ffado user mailing list.

Jenny

Hello Jenny,

Well, I guess all is for naught.  I got sidetracked in a BIG way.  Two major changes.  The first was purchasing a firewire device.  I found this on Ebay and won it for less than $200

[http://www.echoaudio.com/Products/Discontinued/Mona/index.php](http://www.echoaudio.com/Products/Discontinued/Mona/index.php)

It is almost like the Saffire LE except that it has four full pre-amps instead of two, it supports XLR-1/4" balanced AND RCA unbalanced connections.  I DO loose MIDI (but I can pick that up via a USB interface and can get more ins/outs to boot!), but gain optical digital connections and work clock In/Out.  I also gain full metering for the input channels.  The best part is that this is a PCI interface.  So no need to deal with Freebob/ffado and having to route through jack for basic system sounds.

The other major change was that while I was having so many problems with my system, I went for a COMPLETE overhaul.   Ubuntu Hardy is really very buggy and I experienced at least 5 major problems with it already.  So with my Grub bootloader getting messed up because of reloading Windows, I decided to jump ship on Ubuntu and hop on board with 64Studio.  Since 64Studio has SEPARATE LiveCD & Install disc, I didn't want to waste a disc.  So I went right for the install version.  All the while I was crossing my fingers that because 64Studio is Debian based it should be not too far from appearance and function of Ubuntu.  Well, I was right.  64Studio has the appearance of a more refined and polished Ubuntu.  I went this route mainly because I heard more success stories with 64Studio than with JackLab.  However, both distributions seem to rank much higher on the audio production list than Ubuntu Studio.  So as of now in regards to Hardy Heron, it's bye bye birdie!

---

### Post by jukingeo on 2008-09-22
Hello all,

I am back to this thread again.  The Echo Mona has not made a peep in Linux since I got it over a month ago.  So tired of constantly swapping cards out of my system, I am thinking about going to a Sound Blaster Live/Firewire set up.  (Soundblaster Live for games and on computer sounds and Firewire for pro audio work).

So I am going to revisit the FFADO/Focusrite Saffire LE scenario.

So question #1) Has FFADO released a finalized version yet?

---

### Post by purplecar on 2008-09-30
Hey there I've read this thread in the hopes of getting my Saffire LE running on Ubuntu studio.  I had gotten Jack to start with it but with no sound so I uninstalled freebob and followed the instructions at the ffado site that Jenny had linked ([http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)) then as suggested re-install the studio package from Synaptic.  Once all this had been done I tried starting Jack up again I heard the click and Jack crashed again.  I tried a different sample rate and Jack stayed running but again with no sound.  Am I missing something?  Thanks....

---

### Post by jukingeo on 2008-10-02
> **purplecar said:**
> Hey there I've read this thread in the hopes of getting my Saffire LE running on Ubuntu studio.  I had gotten Jack to start with it but with no sound so I uninstalled freebob and followed the instructions at the ffado site that Jenny had linked ([http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)) then as suggested re-install the studio package from Synaptic.  Once all this had been done I tried starting Jack up again I heard the click and Jack crashed again.  I tried a different sample rate and Jack stayed running but again with no sound.  Am I missing something?  Thanks....


From what I hear getting the Saffire LE is pretty much hit and miss.  FFADO is still in the beta stages and while I do eventually want the Saffire LE, I am going to hold out until a stable version of FFADO is released.

After four months of sound issues and 3 different sound devices, I decided to go with something more 'proven to work'...Or in simpler terms somthing "automagically" recognized.  I ended up buying the M-Audio Delta 44.  Granted it isn't as nice as the Saffire LE (nor has it's features), but I didn't want to go through yet another configuration nightmare.

Sure I would like something more advanced and "better", but I am just happy now that I do have sound in all my Linux distros...FINALLY!

---

### Post by Pablo Enrici on 2008-10-03
> Hey there I've read this thread in the hopes of getting my Saffire LE running on Ubuntu studio. I had gotten Jack to start with it but with no sound so I uninstalled freebob and followed the instructions at the ffado site that Jenny had linked ([http://www.ffado.org/?q=node/613](http://www.ffado.org/?q=node/613)) then as suggested re-install the studio package from Synaptic. Once all this had been done I tried starting Jack up again I heard the click and Jack crashed again. I tried a different sample rate and Jack stayed running but again with no sound. Am I missing something? Thanks....

Hi, I bought a Saffire LE yesterday and I managed to make it work in Ubuntu Studio (after hours of browsing tutorials and dodging errors). Honestly I can't recall all the steps I made to make it work now (I mean, any variation of the tutorial I could have done), but something interesting I found and I didn't note anywhere else is that once you have ffado and jackd properly installed, the interface recognized by jack, etc, the internal mixer in the board has all faders at minimum, so you won't hear anything in any output!!

I realized this after running the ffadomixer app (thanks Focusrite and ffado folks!), so I would recommend to get the ffadomixer properly installed and running (I had dependencies problems to achieve this).

Good luck!

---

### Post by jukingeo on 2008-10-04
> **Pablo Enrici said:**
> Hi, I bought a Saffire LE yesterday and I managed to make it work in Ubuntu Studio (after hours of browsing tutorials and dodging errors). Honestly I can't recall all the steps I made to make it work now (I mean, any variation of the tutorial I could have done), but something interesting I found and I didn't note anywhere else is that once you have ffado and jackd properly installed, the interface recognized by jack, etc, the internal mixer in the board has all faders at minimum, so you won't hear anything in any output!!

I realized this after running the ffadomixer app (thanks Focusrite and ffado folks!), so I would recommend to get the ffadomixer properly installed and running (I had dependencies problems to achieve this).

Good luck!

I have not delved fully into the relationship between FFADO and Jack, but it is true that once you successfully configure Jack to work with FFADO, you are pretty much 3/4 the way out of the woods.   The big problem is that currently Jack is set up to work with FreeBob, and only a handful of firewire devices work under that system.   FFADO is supposed to change that.  But as it stands now, the current version of Jack isn't set up for FFADO, you have to do that yourself and that can be a nightmare to do.

What I am going to do is wait until the next version of Jack is released and hopefully by then FFADO has been proven and already included in the Jack release.  This way all anyone has to do is hook up their firewire device to their computer and select FFADO in Jack and then start making music.

Sure the more adventurous types can get FFADO to work now, but I personally struggled for four months trying to get consistent audio out of ALL of my Linux distributions and I had nothing but problem after problem.  So I got fed up and decided to go with something that is KNOWN to work.  While it doesn't have all the features I want, I am happy with my decision as I DO have sound in all my Linux distros now, and I can start messing about with all those nice Linux applications.

So for those of you that want true, plug and play...go with the M-Audio Delta Line for headache free operation.  (Unless of course you have the big bucks to afford the RME Hammerfall cards...they supposed to be plug-n-play too).

---

### Post by unclernie on 2008-10-10
> **jenny_thinkpad_t61p said:**
> 
 you can do this by making sure you have the dependencies for freebob:

sudo apt-get build-dep freebob



There is no freebob package in hardy.  The freebob drivers are part of the jackd package, so I did:

[FONT="Fixedsys"]sudo apt-get build-dep jackd[/FONT]

instead.

---

### Post by unclernie on 2008-10-10
Well, the ffado and jackd builds went smoothly.

However, now I launch jackctl and select 'settings', I don't find a ffado driver, although there is a 'firewire' driver listed that I don't remember seeing before.  I tried selecting it, but jackd won't start, complaining that it can't find the driver to load.
  Looking back thru the output of the jackd build, I find a note about adding /usr/lib/jack/ to /etc/ld.so.conf, but I don't see any evidence that this was done by the `make install` process.  Ubuntu uses a slightly different file structure, and ld.so.conf only includes a reference to ld.so.conf.d/, but I don't see any evidence of update in there either.
  Could this be why I'm stuck?

---

### Post by robeast on 2008-10-11
> **unclernie said:**
> Well, the ffado and jackd builds went smoothly.
  Looking back thru the output of the jackd build, I find a note about adding /usr/lib/jack/ to /etc/ld.so.conf, but I don't see any evidence that this was done by the `make install` process.  Ubuntu uses a slightly different file structure, and ld.so.conf only includes a reference to ld.so.conf.d/, but I don't see any evidence of update in there either.
  Could this be why I'm stuck?

Most likely. Add this line to /etc/ld.so.conf:

/usr/lib/jack

However, since you compiled the latest version of JACK yourself (right?) you may have to add this line instead:

/user/local/lib/jack

I don't know the specifics about how JACK finds its drivers, but that is my best guess.

---

### Post by pointfive on 2008-10-29
I've been working on getting my Saffire LE running on Ubuntu for a few weeks now, and have made a lot of progress. I've come miles, but I need help making it that last few inches. I'm almost there!

I followed the installation guide on the ffado website, compiling jack myself per its instructions. After a long, hard road, I was finally able to hook everything up, start ffado-dbus-server & ffadomixer, and start jackd/qjackctl! I actually **hear sound** come through the device, but it lasts only a few seconds. Here is the output that seems to indicate the problem in the jack Messages panel:

```
01:17:07.655 JACK is starting...
01:17:07.656 /usr/bin/jackd -dfirewire -dhw:0 -r44100 -p128 -n3
01:17:07.673 JACK was started with PID=6315.
no message buffer overruns
jackd 0.115.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
00296232505:  (ffado.cpp)[  99] ffado_streaming_init: libffado 1.999.36- built Oct 28 2008 21:40:30
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
01:17:09.822 Server configuration saved to "/home/pointfive/.jackdrc".
01:17:09.825 Statistics reset.
01:17:09.828 Client activated.
01:17:09.834 JACK connection change.
01:17:09.845 JACK connection graph change.  [COLOR="Green"]* I start hearing sound here *[/COLOR]
firewire ERR: Could not start streaming threads: -1 [COLOR="Red"]*** this is where the audio cuts out, 2-4 seconds later ***[/COLOR]
DRIVER NT: could not start driver
cannot start driver
01:17:14.657 JACK connection graph change.
01:17:14.672 JACK connection change.

```

Please, please someone help me solve these last few seemingly minor problems. Thanks!

Further edit: This page [http://www.ffado.org/?q=node/516](http://www.ffado.org/?q=node/516) seems to hint at the problem. And it does seem that I have sound for a *little* longer if I set the Frames/Period really high. Still only a few seconds, though.

I have yet to install the rt kernel, but something tells me that's not the problem since I don't even have Realtime enabled. Thoughts? I'll do that tomorrow.

---

### Post by pointfive on 2008-10-29
Okay, so I've installed the rt kernel and enabled realtime in Jack. The result is I now I'm getting inconsistent results. Usually I have sound for anywhere between 5 and 30 seconds.

When I first boot up and run it, this is the result:
```
02:50:48.959 JACK connection graph change. [COLOR="Green"]* I get sound here *[/COLOR]
firewire ERR: Could not start streaming threads: -1  [COLOR="Red"]*** Sound cuts out here ***[/COLOR]
DRIVER NT: could not start driver
cannot start driver
02:50:53.148 JACK connection graph change.
02:50:53.183 JACK connection change. [COLOR="Blue"]* hangs here, so I click Stop *[/COLOR]
02:51:06.155 Client deactivated.
02:51:06.162 JACK is stopping...
jackd watchdog: timeout - killing jackd
02:51:07.661 JACK was stopped successfully.
02:51:07.663 Post-shutdown script...
02:51:07.665 killall jackd
02:51:07.667 JACK has crashed.
jackd: no process killed
02:51:08.092 Post-shutdown script terminated with exit status=256.
```

Subsequent times I get this:
```
jackd watchdog: timeout - killing jackd
03:03:55.879 Client deactivated.
03:03:55.889 JACK was stopped successfully.
03:03:55.890 Post-shutdown script...
03:03:55.892 killall jackd
03:03:55.893 JACK has crashed.
cannot continue execution of the processing graph (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
.
...pages of the same error...
.
cannot continue execution of the processing graph (Broken pipe)
cannot send request type 7 to server
cannot continue execution of the processing graph (Broken pipe)
cannot read result for request type 7 from server (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
cannot send request type 7 to server
cannot continue execution of the processing graph (Broken pipe)
cannot read result for request type 7 from server (Broken pipe)
cannot continue execution of the processing graph (Broken pipe)
jackd: no process killed
```
In these cases, I still hear my instrument output, but jack is not running. Even if I close jack and stop ffado-dbus-server, I continue to hear sound.

Any insight, anyone? Please help!

---

### Post by prismatic7 on 2008-10-29
> **pointfive said:**
> Any insight, anyone? Please help!

Hi... Sounds a lot like the problem I am still having...

Check /var/log/syslog and look for a line like
```

fw-host0: Unrecoverable error!
ohci1394: fw-host0: Iso Xmit 0 Context died: 
```

If you see that, it means that you're suffering from an error in the upstream kernel that no-one's working on at the moment... add your voice to [this bug](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/232490)

---

### Post by pointfive on 2008-10-29
Thanks, prismatic. That's really discouraging. I'll join the chorus  on that bug, but it looks like I'll have to go with XP for awhile. It's really frustrating to have to jump through so many hoops only to reach a dead end like this.

Are you using your Saffire LE? What's your setup and how do you like it?

One more quick question: I'm using an Expresscard firewire adapter (into a Dell Inspiron 1501). On that bug, Stephan says "The problem is between the controller and how our drivers update its DMA program." Does this mean if I use a different Expresscard, there might be a chance it would work?

---

### Post by pointfive on 2008-10-29
I found something. This [Ubuntu Studio hardware optimization guide]("https://help.ubuntu.com/community/UbuntuStudio/HardwareOptimization") mentions:

> Some of Ricoh chipsets are reported _not_ to work well, some seem to work fine. NEC chipset has been tested by a developer and is reported to work fine, but since Presonus advises against them, there must be a reason to avoid them.

So far, in order of preference (best to worst) according to developers: Texas Instruments, VIA, NEC, O2 Micro (all are OHCI controllers)

I'm pretty sure I saw "Ricoh" somewhere when I was compiling/installing everything, so the question it raises for me is... is the Ricoh chipset in my laptop, or in the firewire expresscard I'm using? (May be a dumb question, but I'm still a newbie.)

---

### Post by thorgal on 2008-10-29
type lspci in a terminal.

---

### Post by prismatic7 on 2008-10-29
> **pointfive said:**
> I found something. This [Ubuntu Studio hardware optimization guide]("https://help.ubuntu.com/community/UbuntuStudio/HardwareOptimization") mentions:



I'm pretty sure I saw "Ricoh" somewhere when I was compiling/installing everything, so the question it raises for me is... is the Ricoh chipset in my laptop, or in the firewire expresscard I'm using? (May be a dumb question, but I'm still a newbie.)

Probably in the expresscard, which means you may well be able to buy a new one. Try and find one with a TI chipset, for preference. But seriously, add your voice to the bug!

---

### Post by pointfive on 2008-10-29
> **prismatic7 said:**
> Check /var/log/syslog and look for a line like
```

fw-host0: Unrecoverable error!
ohci1394: fw-host0: Iso Xmit 0 Context died: 
```
Hmm. Can't find that specific line in my syslog. Here's the closest I can find: 
```
ohci1394: fw-host0: isochronous cycle too long
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00130e0100042e10]
doh, someone wants to mess with state set
ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00130e0100042e10]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00130e0100042e10]
doh, someone wants to mess with state set
ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00130e0100042e10]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Error parsing configrom for node 0-00:1023
```

Don't know if that means anything to anyone. Sure doesn't to me, but "doh" in the syslog isn't comforting.

I also see a lot of APIC errors ("APIC error on CPU0") in the syslog. Could that be the problem? Should I disable APIC?

---

### Post by pointfive on 2008-10-29
> **prismatic7 said:**
> Probably in the expresscard, which means you may well be able to buy a new one. Try and find one with a TI chipset, for preference. But seriously, add your voice to the bug!
Here are the pertinent lines I find with lspci (thanks, thorgal):

```
02:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
03:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

```
So I guess the bad news is that my expresscard is apparently a TI chipset, but my "SD Host controller" and "System peripheral" (whatever those are) have the Ricoh chipset. Are these causing the problem? Anyone know?

---

### Post by prismatic7 on 2008-10-29
> **pointfive said:**
> ```

03:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)


```


Looks like your ExpressCard *is* a TI... hm. I was never able to make my Saffire work with an ExpressCard, but I think that's a different issue to this one. Sorry, **pointfive** - I think I've lead you astray!

---

### Post by pointfive on 2008-10-29
No worries. It's good to eliminate potential issues too. Any insight into those errors in my syslog?

I'm gonna try disabling apic (and lapic) in the boot menu and see if that does anything. EDIT: It didn't.

---

### Post by pointfive on 2008-10-30
I'm convinced at this point that the problem is with jackd. I've gotten floods of the message "cannot continue execution of the processing graph (Broken pipe)" with ALSA (before I installed ffado), and I'm seeing it again with ffado.

From everything I can tell, ffado is working flawlessly. ffado-dbus-server and ffadomixer respond predictably and reliably.

Unless I can figure out what's causing jack to crash, I'm done hitting my head against this. Can anyone point me in the right direction?

Thanks for the guidance. I really do appreciate it.

---

### Post by pointfive on 2008-11-03
UPDATE: Having continued to research this, here's what I've found. According to what I've read in [this thread]("http://forum.cakewalk.com/printable.asp?m=1297349") and other places, even though the Expresscard itself has the TI chipset, if the controller for the Expresscard slot uses the Ricoh chipset (as my Dell Inspiron 1501 does), it causes problems. There are arguments about this, though... does anyone know whether this is the case?

My only hope at this point rests on two possibilities:

1) Disabling the Ricoh firewire controller. How would I do this in Ubuntu?
2) Replacing my Expresscard. I have an [ASTPro IEEE 1394a]("http://www.buyextras.com/syie13fiexti.html?gclid=COep2K_n2ZYCFQxzHgodM0es3w") I bought for $30. Can't find much information on it. People seem to have more success with the [SIIG 800]("http://www.buy.com/retail/product.asp?sku=202730410&SearchEngine=ciao&SearchTerm=202730410&Type=ciao&Category=Comp&dcaid=17926"), but I'm reluctant to drop $80 on something that's not guaranteed to work.

As a next step, can someone help me by explaining how to go about disabling the Ricoh firewire chipset, which I'm assuming is one of the below:

```
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

```

---

