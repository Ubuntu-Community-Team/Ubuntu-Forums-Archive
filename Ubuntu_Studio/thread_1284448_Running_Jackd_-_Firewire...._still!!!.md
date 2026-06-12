---
title: "Running Jackd - Firewire.... still!!!"
date: 2009-10-06
forum: Ubuntu Studio
---

### Post by Shugs81 on 2009-10-06
Right....

Running Ubuntu Jaunty 9.04,
Have installed RT Kernel, have installed Ubuntu Studio Controls

My PC is running
6GB Ram
1tb hd
320gb hd
athlon 64 x2 4400+

Using an edirol fa-66 which I bought specially cause it was fully supported by FFADO...

How the FU*K do I get it to work????????

is there a way to interrogate the system to tell me where the firewire device is? 

```
00555237078:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns

```

get this nearly every time... once it went to a pipe failure but i can't recreate it so can't tell you what settings i had.

I've tried doing stuff with the ffado mixer with no luck...

I'm seriously considering going back to windows cause i feel like i want to scratch my eyes out!!

is there a replacement for jack yet???? grr....

---

### Post by Shugs81 on 2009-10-06
reet... set device to default...

```
01315719353:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
01316298592: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
```

using "Firewire"

```
Freebob using Firewire port 0, node -1
[31mError (bebob_light/bebob_light_avdevice.cpp)[1666] setSamplingFrequencyPlug: setSampleRatePlug: IsoStreamInput plug 0 does not support sample rate 96000
[0m[31mError (bebob_light/bebob_light_avdevice.cpp)[1696] setSamplingFrequency: setSampleRate: Setting sample rate failed
FreeBoB ERR: FREEBOB: Error creating virtual device
LibFreeBoB ERR: Failed to set samplerate...
cannot load driver module freebob
[0m

```

using "Freebob"

Does this help?

---

### Post by kayosiii on 2009-10-06
Yeah both jack is borked with the default config on ubuntu and raw firewire access which the soundcard needs is blocked by default....

BTW... even Debian makes this easier... Isn't ubuntu supposed to be based on Debian (what is going on here).

So first problem...

copy the following to a file 

KERNEL=="raw1394",	NAME="raw1394", GROUP="audio"

call the file 50-raw-firewire.rules and save it to /lib/udev/rules.d/
you will need administrator privileges for this.
now you need to add your user to the audio group. you can do this using the user management tools for your ubuntu variant (ubuntu,kubuntu,xubuntu)

the second issue is that Jack Control is configured to use Realtime resources (different from using a realtime optimised kernel) but on non studio varients of Ubuntu this is not permitted by default. You will either need to turn off realtime option or give yourself permission to access realtime resources. to get started a line like the following should be added to /etc/security/limits.conf (needs administrator access)
@audio - rtprio  99
there are a few other options that can be written into this file but I will just cover this for the moment.


you will then need to either reboot or restart the udev service  

sudo /etc/init.d/udev restart

and log out then log in again

---

### Post by Shugs81 on 2009-10-07
I've tried thos options.. I followed a tutorial post that said to do all that...

I'll try it again tonight and see what happens...

---

### Post by kayosiii on 2009-10-07
ps the firewire driver is the one you want to be using

---

### Post by Shugs81 on 2009-10-07
the two error messages were for each of the firewire options... top one was firewire selected, bottow one freebob.

---

### Post by kayosiii on 2009-10-07
ok firstly
give me the output of the following command 
ls -l /dev/raw1394
secondly try starting jackd from the commandline directly, with the following command. (if you haven't already)
jackd -d firewire

though if everything shows up as it should I would suggest that the ffado website and mailing list should be the next port of call.
[http://www.ffado.org](http://www.ffado.org)

---

### Post by Shugs81 on 2009-10-07
hmmm....

```
ls: cannot access /dev/raw1394: No such file or directory

```

and...

```
desktop:~$ jackd -d firewire
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
22775467960:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
22775471777: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns

```

something aint right.... raw1394 is apparently installed according to synaptic...:confused:

---

### Post by Shugs81 on 2009-10-07
doh... had turned it off before doing the test

```
:~$ ls -l /dev/raw1394
crw-rw---- 1 root video 171, 0 2009-10-07 22:50 /dev/raw1394

```

```
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
00359982386:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
00360792935: Debug (bebob_mixer.cpp)[ 126] addElementForAllFunctionBlocks: Adding elements for functionblocks...
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
```

that was when i tried the jackd command again.... :(

---

### Post by kayosiii on 2009-10-07
ok your raw firewire device is not being loaded at startup time.... Sometimes this happens I am not sure why... You can force the loading of the raw1394 module at startup. by adding the following line to /etc/modules as administator.

raw1394 

(note - looking at my file - I had to do the same thing - I think somebody really doesn't want us to have raw firewire access)

Good luck

---

### Post by Shugs81 on 2009-10-08
checked and it's already there...

---

### Post by kayosiii on 2009-10-08
Seems I somehow missed your last post....
Ok - I can see there that raw1394 belongs to the video group...
Make sure that you are a member of that group. So either use the user management tool for your desktop 

or as administrator edit the following file 

/etc/group

find the group named video and add your username to the end of that line
then log out and in again.
eg.

```
video:x:44:my_user_name
```

---

### Post by Shugs81 on 2009-10-08
mine says 

```
video:x:44:steve,mythtv
```

don't remember that... will bin it...

bah... still not working...

---

### Post by kayosiii on 2009-10-10
ok try this as a temporary

```
sudo chown steve.steve /dev/raw1394
```

This will make you owner of the firewire device until you reboot next - if this still doesn't work... we know that it is not a permission problem.

---

### Post by holmes on 2009-11-08
You could try this.
[HTML]/usr/bin/jackd -R -dfirewire -dhw:1 -r44100 -p1024 -n3
[/HTML]

then start jack.
I had the same problem you had then remembered I have more than one firewire connection.

---

