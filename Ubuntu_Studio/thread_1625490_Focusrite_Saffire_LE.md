---
title: "Focusrite Saffire LE"
date: 2010-11-19
forum: Ubuntu Studio
---

### Post by dawiba on 2010-11-19
Hi

I'm trying to get my Focusrite Saffire LE running in Maverick. I'm not running Ubuntu Studio, just regular Ubuntu, no RT kernel.

Anyway, I've tried the following

Installed Ubuntu Studio Controls, set memlock to 50% and nice to -10 as per
[https://help.ubuntu.com/community/UbuntuStudioControls](https://help.ubuntu.com/community/UbuntuStudioControls)

I left 'Enable raw1394 access' unchecked as per advice here
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

I also added myself to the audio and video groups.

Typing
```

lsmod | grep 'firewire\|1394'
```

gives me

```
xt_limit 1394 7 
firewire_ohci 21394 0 
firewire_core 46675 1 firewire_ohci
crc_itu_t 1383 1 firewire_core
```

Typing

```
 ls -al /dev/raw1394
```

gives me

```
ls: cannot access /dev/raw1394: No such file or directory
```

And of course, Jack doesn't run :)

I had this interface running on an old laptop a long time ago, but never on this computer and I'd like to use it on this one. It's been a long time since I set one of these up and I guess I'm missing out something obvious and simple. Can anyone help?

---

### Post by trulan on 2010-11-19
You're running the new firewire stack, so /dev/raw1394 should not be there.  For the new stack,the equivalent command I believe is:
```
~$ ls -al /dev/fw0
crw------- 1 root root 251, 0 2010-11-18 17:21 /dev/fw0
```Due to the configuration of the new stack this device does not need user privileges, so 'root root' is fine here.

Does Jack run on your onboard soundcard?  (In other words, is realtime mode the problem?)
What errors is Jack throwing when you try to start it on your firewire device?
And does ```
ffado-test ListDevices
``` come up with anything?

---

### Post by dawiba on 2010-11-19
Thanks Trulan
[QUOTE=Trulan]
You're running the new firewire stack[/QUOTE]

That's what I thought should be the case.

Typing
```
ls -al /dev/fw0
```

gives me
```
crw------- 1 root root 251, 0 2010-11-19 13:24 /dev/fw0
```

Jack doesn't run with the Realtime option enabled or disabled using alsa or firewire.


Jack messages

```
13:30:46.825 Patchbay deactivated.
13:30:46.844 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
13:30:46.858 ALSA connection graph change.
13:30:47.055 ALSA connection change.
13:30:58.277 Startup script...
13:30:58.277 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
13:30:58.678 Startup script terminated with exit status=32512.
13:30:58.678 JACK is starting...
13:30:58.678 /usr/bin/jackd -r -dfirewire -dhw:0 -r44100 -p1024 -n3
13:30:58.686 Could not start JACK. Sorry.
13:31:08.766 JACK was stopped with exit status=255.
13:31:08.767 Post-shutdown script...
13:31:08.767 killall jackd
jackd: no process found
13:31:09.173 Post-shutdown script terminated with exit status=256.
```

Thanks again

---

### Post by dawiba on 2010-11-19
Sorry, forgot this part

Typing
```
ffado-test ListDevices
```

gives me

```
Cannot create thread 1 Operation not permitted
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
Node id GUID VendorId ModelId Vendor - Model
ERROR: messagebuffer not initialized: 00698318008: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 0 on port 0

```

---

### Post by prokoudine on 2010-11-19
> **trulan said:**
> You're running the new firewire stack, so /dev/raw1394 should not be there.  For the new stack,the equivalent command I believe is $ ls -al /dev/fw0

In my case (Saffire Pro 24) /dev/fw0 is not there.

> **trulan said:**
> And does ```
ffado-test ListDevices
``` come up with anything?

```
$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.0.1-1922M
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e0401c0173c  0x0000130E  0x00000007   Focusrite - SAFFIRE_PRO_24
   1       0x000800080008248f  0x00000800  0x00000000   Linux - ohci1394  - 
no message buffer overruns
```

---

### Post by trulan on 2010-11-19
This is still all pretty new to me.  The first unusual thing I see is that 'Operation Not Permitted' error on ffado-test ListDevices - I'm not sure what's causing that but it isn't there for me.

Secondly, set your device to default instead of hw:0 in Jack Control - the device setting has aldready given me problems and it is better just set to default for firewire.

---

### Post by dawiba on 2010-12-06
Update

After a few days not thinking about trying to get Firewire working, I dug out an old USB interface (a Mackie XD-2). I plugged it in and it worked straight away as a soundcard.

So I downloaded Ubuntu Studio Controls and Jack (I had removed them after my last attempt), set up jack to use alsa and the Mackie (it was hw:2) and everything seemed to work fine. Realtime was disabled in Jack and memlock in Studio Controls was set to 90% and Jack started without any problems. So I downloaded Ardour and fired it up. Success :D

So I messed around for a bit with this set up then thought I'd try the Saffire LE again. So I went into Jack and selected the hw:2 option (which I'm sure wasn't there before), hit the Start button on Jack and it started first time :). So I fired up Ardour and everything worked really smooth :D

To say I'm happy is a complete understatement :D I can also truthfully say that I have no idea as to why it works, but it does. I've downloaded some other bits and pieces and so far everything is running smoothly :)

Next stop is to try and get my vst's working #-o

---

