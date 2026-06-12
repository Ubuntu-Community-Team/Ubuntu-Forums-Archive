---
title: "ZynAddSubFX Zombifies!"
date: 2009-11-20
forum: Ubuntu Studio
---

### Post by gnomeout on 2009-11-20
Every time I ever run ZynAddSubFX it will always fail and produce no sound after a minute or 2. This usually happens while switching instruments, but also just happens randomly!

The Console shows as follows:

> brian@cog:~$ zynaddsubfx                                         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection         
lash_init: could not connect to server 'localhost' - disabling LASH     

ZynAddSubFX - Copyright (c) 2002-2005 Nasca Octavian Paul
Compiled: Feb 11 2008 12:53:23                           
This program is free software (GNU GPL v.2) and          
    it comes with ABSOLUTELY NO WARRANTY.                

Try 'zynaddsubfx --help' for command-line options.
Sound Buffer Size =     256 samples               
Internal latency =      5.8 ms                    
ADsynth Oscil.Size =    512 samples               
cannot read response from jack server (No such file or directory)
cannot read response from jack server (No such file or directory)
cannot read response from jack server (No such file or directory)
cannot read response from jack server (No such file or directory)
Internal SampleRate   = 44100                                    
Jack Output SampleRate= 44100                                    
zombified - calling shutdown handler 

And thats it. 

Any help would be greatly appreciated!

I am guessing this could possibly be related to my JACK config, or I could be missing something obvious. 

I would also be open to alternatives for synthesizing with a USB keyboard(Korg nanoKey). Preferably one that did not use JACK!

Or a program that can be easily virtualized with something like Wine. I tried running the default software but Wine couldnt do it and my virtualbox had a huge delay between my key press and the noise generated.

Thanks again,
B.

PS: Why does JACK suck so much?

---

### Post by raboofje on 2009-11-20
It's been a while since I tried, but I remember that when I downloaded and compiled zynaddsubfx manually it performed much better than the package.

---

### Post by gnomeout on 2009-11-20
> **raboofje said:**
> It's been a while since I tried, but I remember that when I downloaded and compiled zynaddsubfx manually it performed much better than the package.
worth a shot, I'll try that when I get some time(and let you know how it goes). 

Although its hard to see how/why that would work.

Still hopeful for more concrete solutions...

---

### Post by AutoStatic on 2009-11-20
Do you use it with JACK? I can't get under 256 Frames/Periods, then ZynAddSubFX chokes on most instruments upon selecting them. But normally I run JACK with 64 Frames/Periods so I have to switch all the time, very annoying.
Is this better when you compile ZynAddSubFX yourself raboofje?

---

### Post by sgx on 2009-11-20
I think a lot of zyn problems are hardware related. I have a pci soundcard, and real 5pin midi connectors, no usb/firewire devices, nvidia graphics, and typically run one zyn connected to rakarrack, one hydrogen connected to another rakarrack, and another plain zyn, if desired.

I suspect that conflicting software problems in linux audio workstations
are greatly reduced by starting with barebones linux, and adding only the audio apps you need, and never doing serious audio work until any online session has been rebooted into oblivion. 

The main problem in the above setup occurs if I stop jackd. Then, zyn, hydrogen and rakarrack turn into 'The Three Stooges'. But I don't often need to do that.

Cheers

---

### Post by AutoStatic on 2009-11-20
> **sgx said:**
> I think a lot of zyn problems are hardware related.It zombifies on my Quad CPU with 4Gb that runs flawlessly and comes from a respected vendor when it comes to Linux.

> **sgx said:**
> I have a pci soundcard, and real 5pin midi connectors, no usb/firewire devices, nvidia graphics, and typically run one zyn connected to rakarrack, one hydrogen connected to another rakarrack, and another plain zyn, if desired.I'm not willing to go back in time 5 years or more.

> **sgx said:**
> I suspect that conflicting software problems in linux audio workstations
are greatly reduced by starting with barebones linux, and adding only the audio apps you need, and never doing serious audio work until any online session has been rebooted into oblivion.That's what I did. It even zombifies in an IceWM session with just JACK running and I even modprobe -r'd all the network stuff.

Edit: just compiled ZynAddSubFX 2.4.0, going to try if that works better.
Edit2: gave it a test run and my problems seem to be solved, so thanks raboofje for the tip!

---

### Post by gnomeout on 2009-11-20
AutoStatic: Yes I run it with JACK. I wish I didn't have to, but I can't figure out any other way.

sgx: theoretically hardware should not be an issue, and my computer has run everything perfectly so far.

I can't compile the source code for ZASFX either, my compiler spews a million errors about "/Params/../Misc/XMLwrapper.h:148: error: ISO C++ forbids declaration of ‘mxml_node_t’ with no type" for like 200 lines. Which sounds like badly written code at first glance, but is probably also my compiler. Either way I can't be bothered. 

So as a summary:
NOTHING HAS CHANGED

still need help. Thanks for replying though, people.

---

### Post by raboofje on 2009-11-20
> **AutoStatic said:**
> just compiled ZynAddSubFX 2.4.0, gave it a test run and my problems seem to be solved

Indeed not sure why this should work, but good thing that it does! :).

---

### Post by raboofje on 2009-11-20
> **gnomeout said:**
> I run it with JACK. I wish I didn't have to, but I can't figure out any other way.

Iirc when you start zynaddsubfx when JACK is not running it'll just connect directly to ALSA.

> I can't compile the source code for ZASFX either, my compiler spews a million errors about "/Params/../Misc/XMLwrapper.h:148: error: ISO C++ forbids declaration of ‘mxml_node_t’ with no type" for like 200 lines. Which sounds like badly written code at first glance, but is probably also my compiler.

Sounds like you don't have the includes in which mxml_node_t is defined installed - a quick google tells us this is defined in 'mini-xml' - apt-cache shows libmxml-dev might include this.

Does installing libmxml-dev help? If not, could you paste the output/errors?

---

### Post by gnomeout on 2009-11-20
> **raboofje said:**
> 

Does installing libmxml-dev help? If not, could you paste the output/errors?

libxml-dev is probably my issue, but running it with JACK turned off works fine. Didn't work before, but I have figured out that since its not compatible with pulseaudio that it just wants my whole sound device to itself(actually I kind of just assumed thats what happening), which is fine by me for now.

now I just have to figure out a way to connect my nanoKey to ZASFX, right now I can do it using the jackctrl, but since i literally just turn it on to connect that one thing then turn it off and everything works I am assuming there is a better way to do this.


Anywho, thanks for the help. I'll probably just end up recompiling as was suggested when I am ready to move up in music production, right now just the one program is all I need for learning to play.

---

### Post by AutoStatic on 2009-11-21
> **raboofje said:**
> Indeed not sure why this should work, but good thing that it does! :).Yup, I can even use the drums bank now :)
But I do have a lot crackling when I hook up my MIDI keyboard and play something. It's a lot better when I direct a MIDI track through ZynAddSubFX.

---

### Post by AutoStatic on 2009-11-21
> **gnomeout said:**
> libxml-dev is probably my issue, but running it with JACK turned off works fine. Didn't work before, but I have figured out that since its not compatible with pulseaudio that it just wants my whole sound device to itself(actually I kind of just assumed thats what happening), which is fine by me for now.

now I just have to figure out a way to connect my nanoKey to ZASFX, right now I can do it using the jackctrl, but since i literally just turn it on to connect that one thing then turn it off and everything works I am assuming there is a better way to do this.


Anywho, thanks for the help. I'll probably just end up recompiling as was suggested when I am ready to move up in music production, right now just the one program is all I need for learning to play.Good to read that it works! I have a nanoKONTROL and it only works when you connect it through JACK, this doesn't happen automatically. You can automate it though through the Patchbay window in Qjackctl. Is this what you are looking for?

---

### Post by raboofje on 2009-11-21
> **AutoStatic said:**
> I do have a lot crackling when I hook up my MIDI keyboard and play something. It's a lot better when I direct a MIDI track through ZynAddSubFX.

That's odd. Where is the crackling coming from? xruns? if you record the zynaddsubfx output and play it back later, does it also crackle?

Perhaps hook up kmidimon and look for differences in the MIDI stream?

---

### Post by AutoStatic on 2009-11-21
Hé Raboofje, I'll check but no xruns so far so that's not the problem I think. If I don't get it right I'll open a new thread.

---

### Post by sgx on 2009-11-21
I wonder if running the lashd command might be lucky? I run
lashd, which also starts jackd, then I start Reaper/vsts, then
qjackctl, then zynaddsubfx and timemachine, make the connections,
and record as desired. (pretty lucky, for being so far in the past ;)

---

### Post by AutoStatic on 2009-11-22
Haven't had the need to run LASH yet, maybe I should give it a go :)

---

### Post by pdxken on 2009-11-22
I have had this problem also. Jack will drop zynaddsubfx from audio when instrument is changed.
For me Jack message will show this message "subgraph starting at qjackctl timed out (subgraph_wait_fd=16, status = 0, state = Running, pollret = 0 revents = 0x0)"

I found I could keep jack from dropping zen audio by changing:
"Timeout (msec) to 5000"

I still get a few x-runs but at least jack has a little more patience with zen and not dropping it.

Ken.

---

### Post by bluesscream on 2009-11-22
how is priority set in jackd (qjackctl gui, not  rtprio in etc/security/limits)? I run into freezes and zombifying apps if I set it too high. 60 is the limit for me

---

### Post by sgx on 2009-11-22
> **bluesscream said:**
> how is priority set in jackd (qjackctl gui, not  rtprio in etc/security/limits)? I run into freezes and zombifying apps if I set it too high. 60 is the limit for me

Hi, I see most configs have priority about 12% less in qjackctl, than in
limits.conf

With an Rt kernel, I see default configs between 90 and 99 in limits.conf,
with lower ones like 80 to 89 in qjackctl priority setting. I read where for non RT kernels, priority 50 in qjackctl is enough to give audio higher priority than other system apps, but this is hearsay, not expertise, and it works OK here, (no RT)to run apps totalling around 20 basic sounds, or lower numbers of very involved sounds. So a large gscw hydrogen drumkit with lots of beats, with a multimbral zynaddsubfx and 2 rakarracks, are pushing the lid off on 2 2ghz cpu and 2 gig memory, while a good RT config on the same computer should get much better numbers!

Cheers

---

