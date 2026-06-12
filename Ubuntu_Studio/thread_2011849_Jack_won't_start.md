---
title: "Jack won't start"
date: 2012-06-27
forum: Ubuntu Studio
---

### Post by Miatch on 2012-06-27
I just installed Ubuntu 12.04 on my Imac, and qjackctl will not start.  This is the message I see:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]22:35:34.869 D-BUS: JACK server could not be started. Sorry[/COLOR]
 

56:21 2012: Starting jack server...
 Wed Jun 27 22:56:21 2012: JACK server starting in non-realtime mode
 Wed Jun 27 22:56:21 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
 Wed Jun 27 22:56:21 2012: [1m[31mERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init[0m
 Wed Jun 27 22:56:21 2012: [1m[31mERROR: Cannot initialize driver[0m
 Wed Jun 27 22:56:21 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Wed Jun 27 22:56:21 2012: [1m[31mERROR: Failed to open server[0m
 Wed Jun 27 22:56:23 2012: Saving settings to "/home/mitch/.config/jack/conf.xml" ...
 [COLOR=#ff0000]22:56:25.472 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


I haven't used Ubuntu much the last few years, so any help is appreciated!!

---

### Post by sgx on 2012-06-28
Hi, try this command in a terminal

jackd -d alsa -r 44100

should have lines something like these at the end of the output:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Then start qjackctl

Cheers

---

### Post by Miatch on 2012-06-30
I get this: 

jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following line
and correct/add it if necessary:

  @audio          -       rtprio          99

After applying these changes, please re-login in order for them to take effect.

You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!


Realtime is not checked, and the specs seem realistic, unless I've really missed something.  

I tried to change the limits.conf file but it won't allow me to.  I'm kind of lost in the new layout...

Thanks

---

### Post by CrocoDuck on 2012-06-30
You need superuser privileges to edit /etc/security/limits.conf. Check if your user is in the audio group.

---

### Post by Miatch on 2012-06-30
Sorry, I'm a total noob.  How do I do that?  In versions from a few years ago, the admin stuff was pretty easy to find, but I'm lost in the new(ish) layout.

Thanks

---

### Post by sgx on 2012-07-01
the single command:    groups
lists the groups you belong to.

To edit a file,

sudo kwrite /where/the/file/is/name-of-file

Replace kwrite in that line, with your text editors name.

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

scroll down to  Configuration Modifications, it is the
docs on this subject, echos what crocoduck explained,
with some details.

the file limits.conf has some spacing to be maintained,
between the elements, that is ignored in forum quotes.
So tap the spacebar as needed, to allign the columns.

Cheers

---

### Post by Miatch on 2012-07-01
Thanks for the link!  Jack appears to be running (after adding the commands to the limits.conf file), I will see what happens when i plug something in.

Cheers!

---

### Post by architectadrian on 2012-10-27
I have the same problem, cannot start jack. I tried this:

> **sgx said:**
> Hi, try this command in a terminal

jackd -d alsa -r 44100

should have lines something like these at the end of the output:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Then start qjackctl

Cheers

I received the following answer:

adrian@adrian-U-VAIO:~$ jackd -d alsa -r 44100
jackdmp 1.9.9
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2012 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist

Audio device hw:0 cannot be acquired...
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
adrian@adrian-U-VAIO:~$ 



Can you help, please?

Thank you.

---

### Post by bumBumBUM on 2012-10-27
are you sure that hw:0 is the correct sound device?

"amixer" and "aplay -l" are good commands to see what's what with regard to your audio hardware. If you're still not sure you can copy paste their outputs here...

---

### Post by sgx on 2012-10-28
> **architectadrian said:**
> I have the same problem, cannot start jack.

sudo jackd -d alsa -r 44100

Then

sudo qjackctl

This should work in case permissions are an issue, and all other
audio apps will also need sudo, during that session.

In qjackctl Setup page, on the Misc tab, is a box
to 'enable dbus support'. Change this opposite to what it is now,
reboot, and start jackd without sudo, and if it fails, use sudo.
Sometimes a web browser or other app gets hold of the
audio, so a fresh boot is best for testing.

Also try with the Setup page 'Realtime' box changed
to its opposite

cat /proc/asound/cards
aplay-l
arecord -l
aconnect -i
aconnect -o

the output from those commands should agree on the soundcard
and midi ports your kernel sees.

I would opt away from the dual boot, and just use synaptic to
add the audio capabilities one by one, to stock ubuntu, which
actually gives you more control. Best to stick with what works.

textfile etc/security/limits.conf has two lines at the bottom,
should look like this:

@audio          -       rtprio           99
@audio          -       nice             -10
@audio          -       memlock          unlimited

(my 'nice' value is not crucial to change, keep yours)

sudo gedit /etc/security/limits.conf  to modify it.
You must be in the audio group, add your user, if the
groups command output, does not show that.

bash-4.1$ groups
you lp floppy cdrom cdwriter audio video dialout users polkituser

Cheers

---

