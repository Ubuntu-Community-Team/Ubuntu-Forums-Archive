---
title: "Firepod/Jack/Ardour help......."
date: 2009-06-29
forum: Ubuntu Studio
---

### Post by pooptoof on 2009-06-29
Hi all. I just installed Ubuntu Studio(64 bit)  and am trying to get my fp10 up and running. I am not familiar with Jack at all so bear with me. So far I have just the red light so I am guessing that my firepod is not detected by the system. I have tried switching the driver in Jack to freebob (didn't change anything) and tried to switch the permission for 1394 to "audio" as described elsewhere in the forums here. When I type in the command "sudo /gedit.........etc...." I get nothing. Gedit opens up, but there is no code. I'm also a bit of a ubuntu newb... sorry.

Any help?

Pretty please?

:guitar:

---

### Post by Grishka on 2009-06-29
try ffado (firewire) driver.

---

### Post by pooptoof on 2009-06-29
i have and that doesn't seem to help. thanks though :)

---

### Post by Stochastic on 2009-06-30
Which version of Ubuntu Studio are you running?  This has direct impact on how the firewire permissions are setup.

In the meantime, make sure you open up System -> Administration -> Ubuntu Studio Controls, and check off 'Enable raw1394 access' click apply, then click close.

---

### Post by pooptoof on 2009-06-30
Well that seemed to work for a second. The light went blue but now it's red again. When I try to start Jack (by clicking the "Start" button I get this..


 p, li { white-space: pre-wrap; }  [COLOR=#999999]07:00:47.790 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]07:00:47.813 Statistics reset.[/COLOR]
 [COLOR=#66CC99]07:00:47.866 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]07:00:48.089 ALSA connection change.[/COLOR]
 [COLOR=#999999]07:01:03.345 Startup script...[/COLOR]
 [COLOR=#990099]07:01:03.346 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]07:01:03.748 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]07:01:03.748 JACK is starting...[/COLOR]
 [COLOR=#990099]07:01:03.748 /usr/bin/jackd -R -dfirewire -r44100 -p1024 -n3[/COLOR]
 [COLOR=#999999]07:01:03.751 JACK was started with PID=4206.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 SSE2 detected
 JACK: unable to mlock() port buffers: Cannot allocate memory
 JACK: unable to mlock() port buffers: Cannot allocate memory
 00139980799:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 05:33:49
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 00140004127: [31mError (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
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
 [0mno message buffer overruns
 [COLOR=#999999]07:01:05.147 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]07:01:05.147 Post-shutdown script...[/COLOR]
 [COLOR=#990099]07:01:05.147 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]07:01:05.580 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]07:01:06.794 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by Valenz on 2009-06-30
Check if all modules are loaded.

What Firewire controller do you use? A PCI card? Or one that is build into your mainbord?

I had also problems with my controller but the light turned finally blue after placing the card in another PCI Slot and reinstalling the System (8.10 and manually upgrading to 9.04). As you might have read in another thread, I now have problems with Xruns and bad latency - but the Firebox (in my case) is working.

---

### Post by Stochastic on 2009-06-30
Okay, so you're running Ubuntu Studio Jaunty (I assume from your jackd version - please correct me if this is wrong, it's very important!).

Can you post the output of this command (even if it doesn't output anything) ```
grep -H -n raw1394 /lib/udev/rules.d/*
```

also can you post the output of this command ```
groups
```

---

### Post by pooptoof on 2009-06-30
Yes it's Jaunty. Here's what I get.


ivan@ubuntu2719:~$ grep -H -n raw1394 /lib/udev/rules.d/*
/lib/udev/rules.d/50-udev-default.rules:121:KERNEL=="raw1394",        GROUP="video"


ivan@ubuntu2719:~$ groups
ivan adm dialout cdrom audio plugdev lpadmin admin sambashare





Thanks a BUNCH for your help. :guitar:

---

### Post by pooptoof on 2009-07-01
Keepin it at the top......

---

### Post by trulan on 2009-07-02
It doesn't look like you have a video group.
1. Go into system/administration/users and groups.
2. Unlock it, click manage groups.
3. Create a group named 'video' and make yourself a member.

It also might not hurt to make a 'disk' group as well, although I'm not certain if that is necessary in Jaunty.

Hope that helps.

---

### Post by Stochastic on 2009-07-02
No, don't make a disk group. But Trulan is right that you're not part of the video group and that's why your firepod isn't working.

---

### Post by pooptoof on 2009-07-03
Ok. Sounds good. How would I fix that?

---

### Post by trulan on 2009-07-03
Look on post #10 on page 1.

BTW, Stochastic, why do many tutorials say to create the disk group, and why is it no longer needed?

---

### Post by pooptoof on 2009-07-03
Sorry guys. I created a "video" group but that still doesn"t seem to help. When I tried to get Jack to run using a command line I get this..

ivan@ubuntu2719:~$ jackd -v -R -d freebob
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
jackd 0.116.1
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
start poll on 3 fd's
new client: freebob_pcm, id = 1 type 1 @ 0x8666c0 fd = -1
SSE2 detected
Freebob using Firewire port 0, node -1
new buffer size 1024
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
WARNING: 1 message buffer overruns!
cleaning up shared memory
cleaning up files
unregistering server `default'




This is after creating the group "video" and making myself a member. I know there has been  mention in other threads about changing permissions using Gedit, but trying to find that file doesn't seem to work. Is the permissions file in Jaunty different somehow?

---

### Post by trulan on 2009-07-04
I was helped a lot by this thread:
[http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues](http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues)

the problem is right here (copied from your log):
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?

You need to have the drivers loaded and the permissions set to get past this.

You'll need to use sudo to edit the permissions files, as in:
```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```(copied from Stochastic's post in the thread I linked.  Looks like the permissions file is not the in the same place as it had been in Hardy).

And always listen to Stochastic, not me. ;)

---

### Post by Stochastic on 2009-07-05
pooptoof, can you post the output of the following commands:
```
lsmod | grep 1394
```
```
cat /etc/modules
```
and one more time for good measure: ```
groups
```

trulan, the only reason why adding yourself to a 'disk' group would be mentioned in any tutorial is that 'disk' is the default group that raw1394 permissions are given to.  Creating this group would be a workaround for any unchanged permissions files, but it's a dangerous one as it essentially allows your user raw access to all permissions granted to the disk group.  Long story short is that it's a major security vulnerability and should be avoided.  As it is, the old firewire stack (in use in Ubuntu in all versions before Karmic 9.10) the raw access that users are granted through the firewire is considered a security vulnerability.  Moving all raw1394 access to 'audio' or 'video' prevents some serious attack holes that 'disk' would leave wide open.

---

