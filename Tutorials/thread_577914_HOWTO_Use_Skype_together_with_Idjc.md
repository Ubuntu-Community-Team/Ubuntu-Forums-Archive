---
title: "HOWTO: Use Skype together with Idjc"
date: 2007-10-16
forum: Tutorials
---

### Post by Steveway on 2007-10-16
Skype and Idjc should both be pretty widely known.
So for us that want to make a live-interview using Skype and send this to an online-radio (Shoutcast, Icecast...) there is finally a clean way! (Well not very clean but pretty much.)
1. Get sure to have the latest versions of Skype and Idjc, I attached a .deb I made with checkinstall for Idjc. Otherwise go and compile it yourself from: [http://www.onlymeok.nildram.co.uk](http://www.onlymeok.nildram.co.uk) **Since I'm not sure if my .deb file also grabs the dependencies, I would advice at first installing IDJC from the repositories and then installing my .deb file.**
2. libasound2-plugins in Ubuntu has no Jack-support so we need to replace it.
Knowing that Ubuntu is based of a Debian-Sid Snapshot I easily took theirs and it works without a crash here: [http://packages.debian.org/sid/libasound2-plugins](http://packages.debian.org/sid/libasound2-plugins)
3. So Idjc and Skype are the newest versions, a new libasound2-plugins is installed and I presume that you allready set up jack.
4. We now add a file in our home directory called .asoundrc
We open this file with a texteditor and according to Idjc's page we add this:
>       pcm.idjcvoip { 
type plug 
slave { pcm "idjcjack" } 
} 
pcm.idjcjack { 
type jack 
playback_ports { 
0 idjc-mx:voip_recv_lt 
1 idjc-mx:voip_recv_rt 
} 
capture_ports { 
0 idjc-mx:voip_send_lt 
1 idjc-mx:voip_send_rt 
} 
} 

The formatting is wrong here but it should work.
5. Proceed as given in idjc's VOIP-Tutorial:
> To make the changes effective you need to log out and log back in again or restart ALSA, then you need to launch IDJC and the VOIP program and set the ALSA device to idjcvoip within the preferences of the VOIP program.

In Skype version 1.4.0.94 you need to log in, click the cogwheel icon, and choose 'Options', followed by 'Sound Devices'. After choosing 'idjcvoip' from all three drop-down lists you are ready to click the 'Make a test sound' button, you should be able to hear audio if IDJC is in VOIP mode with the green phone mode enabled. Provided you heard the test sound you are now ready to make a test call, to Skype user echo123 which is the Skype testing service.

If your version of Skype does not offer the opportunity to set an ALSA device it is too old and needs updating.

These configuration changes need only doing once after which you will be able to start IDJC, then Skype and it will just work. One word of caution for regular Skype users: with the new configuration the Skype account preferences you configured will prevent Skype from loading without IDJC since it will now require that jack be running in order to work (worse still you'll have to manually change the ALSA output device to default before you can use it). You can get around this in a number of ways. For instance you can have a specific Skype account for your radio work or have a specific user account for when you are using IDJC.
6. Usage is also explained there:
> You may have noticed two small telephone icons in the bottom part of the main IDJC window. Actually I would be surprised if you haven't.

Anyway, the Green Telephone allows you to stream audio from a voip service like Skype™ or Teamspeak™ and converse with people during your show. When in Green Phone mode your mic is open all the time and those people you are speaking with will be audible on the stream or on the recording you are making. They will not be able to hear your media players or jingles.

When speaking live (mic button pressed in), the red Telephone Button allows for the people who are on the VOIP service with you to hear your show via the VOIP service at the volume level determined by the volume control with the telephone icon which has just appeared, but not themselves take part. It is probably a good idea not to give them the full volume since they may want to speak among themselves, but on the other hand if the level is too low they won't be able to hear you announcing the next song.

When you are not speaking live, with the Mic Button pressed in you are in a private conference with the people on the phone with you. You would typically use this mode when playing a song since the listeners can no longer hear you. What you can hear of the streamed audio is dictated by the Volume Contol that has the Telephone Icon above it. When you play jingles in this mode the jingles audio goes to the VOIP listeners and not to the stream. You can confirm this by using the Stream Mon. button, which should normally be off when using the Red Phone mode.


Try around, you'll need a little bit to get in comfort with it but it's not very complex.
Have fun.

This has been tested on Gutsy Gibbon using the most recent versions of idjc (0.7.1_pre9) Skype (1.4.0.118) and version 1.0.14-1+b1 of Debian-Sid's libasound2-plugins.

---

### Post by Steveway on 2007-10-25
Thanks for the approval of my Thread.
I just created a .deb of the newest snapshot of idjc.
I didn't test if it didn't break anything but it shouldn't.
Stephen is a very talented programmer.
I'll try to keep posting new .deb files for you.

---

### Post by Steveway on 2007-11-04
Ok, here is a new version.
IDJC has now the version 0.7.2.

---

### Post by Steveway on 2007-11-10
Ok, here is the newest version, 0.7.2a.
I can confirm that it still works with the new beta of Skype 2.0.
Here are future changes and the recent changes in 0.7.2a:
> * Future changes

TODO: Add direct file streaming support
TODO: Add to the vorbis decoder the ability to handle sample rate changes
TODO: Implement a test / monitor feature in the server window

* Changes in version 0.7.2a

Fix to a regression in file kvpparse.c (memory leak).

Deactivated the pointless watchdog code in idjcsourceclient.


---

### Post by soodejuu on 2008-08-26
I have done everything suggested above but still skype tels me there is a "problem with playback".

I am using Skype 2.0.0.72. Could this be a problem?

I am also wondering if the created idjcvoip should "pop up" in any way in Jack.

Basicly I am stuck. Help would be appreciated.

---

### Post by ram130 on 2008-08-31
I am also have this problem with skype 2.0.0.72 and for the i have tried everyting,the idjcvoip  does not come up none at all in skype. can sumone help plzzz??

---

### Post by ram130 on 2008-09-01
i got the vdjcvoip to come up, apparently it was the wrong  file. the right file is in  /usr/share/alsa/alsa.conf for me.  But Vdjc keeps freezing when i make a call with skype. Any help??

---

### Post by ram130 on 2008-09-02
OK i got it working.....but dis took me a nite and half...damn..im beginin nt to like linux cause jack is unstable wit xruns more time

---

### Post by freyyr890 on 2008-11-29
> **ram130 said:**
> OK i got it working.....but dis took me a nite and half...damn..im beginin nt to like linux cause jack is unstable wit xruns more time

Jack is pretty much useless without the realtime kernel.

Try compiling a kernel with the rt patches installed, then configure it with jack.

Google around, there's a lot of tutorials on this.

---

### Post by afallenhope on 2009-03-25
Hey I tried doing this and I keep getting.

```
afallenhope@afh:~$ skype
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_jack.so
```

```
afallenhope@afh:~$ ls -al /usr/lib/alsa-lib/
total 1032
drwxr-xr-x   3 root root   4096 2009-03-25 01:38 .
drwxr-xr-x 242 root root 110592 2009-03-25 01:38 ..
-rwxr-xr-x   1 root root    951 2009-03-25 01:38 libasound_module_conf_pulse.la
-rwxr-xr-x   1 root root  13841 2009-03-25 01:38 libasound_module_conf_pulse.so
-rw-r--r--   1 root root  11304 2008-04-21 03:36 libasound_module_ctl_bluetooth.so
-rw-r--r--   1 root root  28812 2008-02-29 13:24 libasound_module_ctl_dsp_ctl.a
-rw-r--r--   1 root root    983 2008-02-29 13:24 libasound_module_ctl_dsp_ctl.la
-rw-r--r--   1 root root  22328 2008-02-29 13:24 libasound_module_ctl_dsp_ctl.so
-rw-r--r--   1 root root  13962 2008-02-29 13:24 libasound_module_ctl_oss.a
-rwxr-xr-x   1 root root    925 2009-03-25 01:38 libasound_module_ctl_oss.la
-rwxr-xr-x   1 root root  33581 2009-03-25 01:38 libasound_module_ctl_oss.so
-rw-r--r--   1 root root  31024 2008-02-29 13:24 libasound_module_ctl_pulse.a
-rwxr-xr-x   1 root root    945 2009-03-25 01:38 libasound_module_ctl_pulse.la
-rwxr-xr-x   1 root root  64745 2009-03-25 01:38 libasound_module_ctl_pulse.so
-rwxr-xr-x   1 root root   1107 2009-03-25 01:38 libasound_module_pcm_a52.la
-rwxr-xr-x   1 root root  61036 2009-03-25 01:38 libasound_module_pcm_a52.so
-rw-r--r--   1 root root  31244 2008-02-29 13:24 libasound_module_pcm_alsa_dsp.a
-rw-r--r--   1 root root    990 2008-02-29 13:24 libasound_module_pcm_alsa_dsp.la
-rw-r--r--   1 root root  23584 2008-02-29 13:24 libasound_module_pcm_alsa_dsp.so
-rw-r--r--   1 root root  37736 2008-04-21 03:36 libasound_module_pcm_bluetooth.so
**-rwxr-xr-x   1 root root    966 2009-03-25 01:38 libasound_module_pcm_jack.la**
**-rwxr-xr-x   1 root root  36810 2009-03-25 01:38 libasound_module_pcm_jack.so**
-rw-r--r--   1 root root  11934 2008-02-29 13:24 libasound_module_pcm_oss.a
-rwxr-xr-x   1 root root    925 2009-03-25 01:38 libasound_module_pcm_oss.la
-rwxr-xr-x   1 root root  32563 2009-03-25 01:38 libasound_module_pcm_oss.so
-rw-r--r--   1 root root  34620 2008-02-29 13:24 libasound_module_pcm_pulse.a
-rwxr-xr-x   1 root root    945 2009-03-25 01:38 libasound_module_pcm_pulse.la
-rwxr-xr-x   1 root root  69637 2009-03-25 01:38 libasound_module_pcm_pulse.so
-rw-r--r--   1 root root  10858 2008-02-29 13:24 libasound_module_pcm_upmix.a
-rwxr-xr-x   1 root root    937 2009-03-25 01:38 libasound_module_pcm_upmix.la
-rwxr-xr-x   1 root root  36065 2009-03-25 01:38 libasound_module_pcm_upmix.so
-rwxr-xr-x   1 root root    967 2009-03-25 01:38 libasound_module_pcm_usb_stream.la
-rwxr-xr-x   1 root root  35029 2009-03-25 01:38 libasound_module_pcm_usb_stream.so
-rw-r--r--   1 root root   7136 2008-02-29 13:24 libasound_module_pcm_vdownmix.a
-rwxr-xr-x   1 root root    955 2009-03-25 01:38 libasound_module_pcm_vdownmix.la
-rwxr-xr-x   1 root root  24426 2009-03-25 01:38 libasound_module_pcm_vdownmix.so
lrwxrwxrwx   1 root root     33 2009-03-25 01:38 libasound_module_rate_lavcrate_faster.so -> libasound_module_rate_lavcrate.so
lrwxrwxrwx   1 root root     33 2009-03-25 01:38 libasound_module_rate_lavcrate_fast.so -> libasound_module_rate_lavcrate.so
lrwxrwxrwx   1 root root     33 2009-03-25 01:38 libasound_module_rate_lavcrate_higher.so -> libasound_module_rate_lavcrate.so
lrwxrwxrwx   1 root root     33 2009-03-25 01:38 libasound_module_rate_lavcrate_high.so -> libasound_module_rate_lavcrate.so
-rwxr-xr-x   1 root root   1143 2009-03-25 01:38 libasound_module_rate_lavcrate.la
-rwxr-xr-x   1 root root  25737 2009-03-25 01:38 libasound_module_rate_lavcrate.so
-rw-r--r--   1 root root   5936 2008-02-29 13:24 libasound_module_rate_samplerate.a
lrwxrwxrwx   1 root root     35 2009-03-25 01:38 libasound_module_rate_samplerate_best.so -> libasound_module_rate_samplerate.so
-rwxr-xr-x   1 root root    999 2009-03-25 01:38 libasound_module_rate_samplerate.la
lrwxrwxrwx   1 root root     35 2009-03-25 01:38 libasound_module_rate_samplerate_linear.so -> libasound_module_rate_samplerate.so
lrwxrwxrwx   1 root root     35 2009-03-25 01:38 libasound_module_rate_samplerate_medium.so -> libasound_module_rate_samplerate.so
lrwxrwxrwx   1 root root     35 2009-03-25 01:38 libasound_module_rate_samplerate_order.so -> libasound_module_rate_samplerate.so
-rwxr-xr-x   1 root root  21583 2009-03-25 01:38 libasound_module_rate_samplerate.so
-rw-r--r--   1 root root  23218 2008-02-29 13:24 libasound_module_rate_speexrate.a
lrwxrwxrwx   1 root root     34 2009-03-25 01:38 libasound_module_rate_speexrate_best.so -> libasound_module_rate_speexrate.so
-rwxr-xr-x   1 root root    967 2009-03-25 01:38 libasound_module_rate_speexrate.la
lrwxrwxrwx   1 root root     34 2009-03-25 01:38 libasound_module_rate_speexrate_medium.so -> libasound_module_rate_speexrate.so
-rwxr-xr-x   1 root root  60921 2009-03-25 01:38 libasound_module_rate_speexrate.so
drwxr-xr-x   2 root root   4096 2009-03-25 01:38 smixer

```
> **OS:** Ubuntu Hardy 8.04.2
**Kernel** 2.6.24-23-generic
**Architecture:** amd64
**JACKd:** jackd version 0.109.2 tmpdir /dev/shm protocol 22 (amd64)
**Skype:** Skype 2.0.0.72 (i386)
**Alsa:** AlsaMixer v1.0.19 (amd64)
**Internet DJ Console Version:** Internet DJ Console Version 0.7.13 (amd64)



hopefully I provided enough debugging info.
Any help would be appreciated

---

### Post by StephenF on 2009-03-25
After installing a library in order for it to be usable you need to run the ldconfig command as root. It will rebuild the index of shared libraries.

---

### Post by bobince on 2009-04-29
Just an update: this method still works on Ubuntu Jaunty. You'll want [libasound2-plugins_1.0.19]("http://packages.debian.org/squeeze/libasound2-plugins") from Debian Squeeze; this seems to work OK with Ubuntu's ALSA 1.0.18.

afallenhope: you're using amd64 architecture, but the amd64 skype package is actually a wrapped 32-bit Skype (since Skype won't supply source or a 64-bit compiled version). So it's looking in the ‘lib32’ directory, which doesn't have its own 32-bit versions of the ALSA plugins. In addition to libasound2-plugins, you'll need to install [lib32asound2-plugins]("http://packages.debian.org/squeeze/lib32asound2-plugins").

Unfortunately, you can't use the package installer to do so, because it clashes with Ubuntu's ia32-libs (and Debian's ia32-libs are different enough in their packaging to make them thoroughly incompatible). What you can do instead is to extract ‘data.tar.gz’ from each of the asound2-plugins packages (eg. using Archive Manager), then again extract the ‘libasound_module_pcm_jack.*’ files  from those tars.

Then as root, drop those files into /usr/lib/alsa-lib/ (from the 64-bit libasound2-plugins package) and /usr32/lib/alsa-lib (from the lib32asound2-plugins package) and run ldconfig.

I get loads of these errors from Skype when running with the jack plugin:

```
    ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL idjcvoip
    ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL idjcjack
```But, curiously enough, it seems to work anyway.

---

### Post by Angel_Caido on 2009-09-13
It worked for me. Just a little "correction". The second path described by bobince [highlighted in the following quote] didn't exist form me: 
> Then as root, drop those files into /usr/lib/alsa-lib/ (from the 64-bit libasound2-plugins package) and **/usr32/lib/alsa-lib** (from the lib32asound2-plugins package) and run ldconfig.


The path that worked as a charm in my ubuntu jaunty 64 bits is **/usr/lib32/alsa-lib**, as a matter of fact the files "libasound_module_pcm_jack.*" didn't exist in this path, so, I didn't have to replace anything [at least within this directory].
Hope this helps a little.

---

### Post by deeq on 2009-11-21
Solved. Updated latest version.

---

### Post by Tege175 on 2010-01-22
Hello,
I installed IDJC 0.8.2 pre3 in here [http://web.bethere.co.uk/idjc/download.html](http://web.bethere.co.uk/idjc/download.html) to my Ubuntu 9.10 and i get IDJC+ Skype to working fine. But now the problem is that i can't IDJC get to connect Icecast 2 server.

There some errors:
[http://pastebin.com/f5c4ba18a](http://pastebin.com/f5c4ba18a)

But if i try to Darkice I get the connection to server and works fine but why not IDJC? Is there some bugs? I also try IDJC 0.8.1 but i got same erros.

IDJC configuration:
Type: Icecast 2 Master
Host: server.com (not the real server address)
Port: 8000
Mount: /live
Login: xxxxx
Pass: xxxxx (same that login)

Can somebody to help me?

Edit.

Is here something wrong:
[http://pastebin.com/f595bf472](http://pastebin.com/f595bf472)

Edit2.
Or is these the problem:
> ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/alsa-lib/libasound_module_rate_speexrate.so is not a symbolic link

/sbin/ldconfig.real: /usr/lib/alsa-lib/libasound_module_rate_samplerate.so is not a symbolic link

/sbin/ldconfig.real: /usr/lib/alsa-lib/libasound_module_rate_lavcrate.so is not a symbolic link


---

### Post by StephenF on 2010-01-22
Did you click the Add button?

Try changing the login to source.

---

### Post by Tege175 on 2010-01-23
Thx man. I am so embarrassing. But now the works.

---

### Post by maksymov on 2010-02-04
Hi! I have the same problem.
What I did:
1 - start jack
2 - start idjc
3 - start skype in terminal
```
avex@avex-server:~$ skype
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
Xlib:  extension "Generic Event Extension" missing on display ":1024.0".
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```and when I try test-call I see "problem with audio playback"

~/.asoundrc:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/avex/.asoundrc.asoundconf>


pcm.idjcvoip {
   type plug
   slave { pcm "idjcjack" }
}

pcm.idjcjack {
   type jack
   playback_ports {
      0 idjc-mx:voip_recv_lt
      1 idjc-mx:voip_recv_rt
   }
   capture_ports {
      0 idjc-mx:voip_send_lt
      1 idjc-mx:voip_send_rt
   }
}

```In skype preferences "audio device" I set 'idjcvoip (plug)' - [http://img684.imageshack.us/img684/5682/screenshotzw.png](http://img684.imageshack.us/img684/5682/screenshotzw.png)
If jack is not started - skype works well.
Can anybody help me?
thanks!

updt:
ubuntu 9.10 x64
pulseaudio was deleted

---

### Post by StephenF on 2010-02-04
Assuming there is no JACK module in /usr/lib/alsa-lib/, see post #12.

---

### Post by maksymov on 2010-02-05
to [StephenF]("http://ubuntuforums.org/member.php?u=368753")
ok! 
thank! all works fine. :)
-----------------
how about idjc russian translation? :)

---

### Post by maksymov on 2010-02-09
well, I install jack plugin for alsa.
But, when I start calling (with the green phone in idjc) I can speak only 10-15 seconds. Then i get xrun and don't hear suond from skype.
can you help me?

---

### Post by Bentai on 2010-02-11
I'm having a rough go of it. Reinstalled the lastes 0.8.x IDJC, and now when I launch the program from the commandline it keeps saying it's using a Jack configuration of 48000hz. I have the .jackdrc file that states 41000 created, it's like idjc is just ignoring all my settings.

Any ideas? This damned program has been a thorn in my side, I would love to get it fixed. :/

*edit*
I reinstalled the jackd stuff and it appears to be working properly again. Now if I can figure out why Skype won't change to anything but PulseAudio I might be in business.

---

### Post by AllRob on 2010-04-22
> **Bentai said:**
> 
*edit*
I reinstalled the jackd stuff and it appears to be working properly again. Now if I can figure out why Skype won't change to anything but PulseAudio I might be in business.

exact same issue here on ludic beta 2

i even got the pulse jack module to load, in another program called mumble, there's only an option to select a mic device, no speakers :( 

and when someone starts to talk, the whole thing just crashes (mumble, that is, not jack) also happends sometimes when selecting the new jack device for the mic.

it's almost there, the connect dialog in qjackctl also only displays a device for the mic, nothing else, same for patchage 

and when i start jack and check the qjackctl messages dialog, i sometimes see a warning : Error: module initialisation failed (my language is dutch, so that's a rough translation, not the exact thing)[I] and that can't be a good thing
[/I]

---

### Post by AllRob on 2010-04-23
i got it to work guys :)
i'm creating a small howto, will post it in a couple of hours with some screenshots.
i got jackd working together with pulseaudio via the pulseaudio jack plugin
idjc can now be linked to mumble, skype, etc, etc, just disable pulse on login, then your almost there.
i've created a patchbay with all my connections, works like a charm. more info soon.
:popcorn:

edit:
[http://h-space.be/en/node/3](http://h-space.be/en/node/3) (or try [http://h-space.be/en/content/howto-jackd-idjc-mumblevoip-lucid-ubuntu-10x](http://h-space.be/en/content/howto-jackd-idjc-mumblevoip-lucid-ubuntu-10x)  if the other link does not work)
for more info on what i did to get it to work (still WIP, got comments? post em please so i can fix it and maybe post it on the forum when it's finished.

---

### Post by Rowen91 on 2010-06-28
AllRob, in your guid you say you include a tar.gz file but it's not in there.

---

### Post by paris_l87 on 2010-07-16
yeah skype will only have pulseaudio in the list,nothing more and that tar file is nowhere in your tutorial :(

---

### Post by Anton Bondar on 2010-07-22
paris_l87,
Try this solution
[http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/](http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/)

One change though: in the qjackctl configuration window, when you are  modifying "Execute script after Shutdown" , substitute "pulse-session" with "pulseaudio --start" .

This worked for me yesterday with the whole system being up to date.

---

### Post by paris_l87 on 2010-07-24
Yeap thank you,it worked! now Skype has jack in its options:)
Thank you again:guitar:

---

### Post by razametal on 2010-09-20
> **AllRob said:**
> i got it to work guys :)
i'm creating a small howto, will post it in a couple of hours with some screenshots.
i got jackd working together with pulseaudio via the pulseaudio jack plugin
idjc can now be linked to mumble, skype, etc, etc, just disable pulse on login, then your almost there.
i've created a patchbay with all my connections, works like a charm. more info soon.
:popcorn:

edit:
[http://h-space.be/en/node/3](http://h-space.be/en/node/3) (or try [http://h-space.be/en/content/howto-jackd-idjc-mumblevoip-lucid-ubuntu-10x](http://h-space.be/en/content/howto-jackd-idjc-mumblevoip-lucid-ubuntu-10x)  if the other link does not work)
for more info on what i did to get it to work (still WIP, got comments? post em please so i can fix it and maybe post it on the forum when it's finished.


Hi, have you another link for the instructions? I'm using idcj 0.7.17 with skype 2.1.0.81 and puseaudio jack plugin, but can make it work :(

Regards,

---

### Post by kwabena39 on 2010-11-10
I get the same problem as maksymov above: xruns, idjc stops working as soon as i log into skype, etc.  Beeping sound...
When I quit Skype, however, everything goes back to normal.

Q: Is there an alternate phone or VOIP software besides Skype that would work better with: Ubuntu, Jackd, IDJC, etc?  Any alternatives?

---

### Post by Garcicasti on 2011-01-04
Hi there everybody!
Well, I've tried all of this things to try to put skype working togethr with idjc, but no results.
Any news?
Ah!by the way......how can i start skype in console mode so i can let you some log info??¿?

Thaks in Advance:popcorn:

---

### Post by Garcicasti on 2011-01-07
Hi there again!
I get it fixed!!!!
Just need to disable Pulseaudio ;D.
But now, again problems :'(
I have the same issue as other guys  here, xruns when i hve been tanking in skype for about 15-20 seconds, but everything goes to normal when i finish the call......how to fix it?

THanks again:popcorn:

---

### Post by ethos_dacapo on 2011-01-08
I just setup IDJC with Icecast today but am having the same problems with Skype. On my system pulseaudio is uninstalled completely because it never worked right with skype to begin with. I also use a telnet box if that makes any difference. When i set skype's sound options to idjc and do a test call it works fine until right before the beep to record a test message. At that point it hangs until i stop the call. The original tutorial mentioned earlier in this thread seems to have vanished from the net. Lots of us having this problem, any help out there?

---

### Post by ethos_dacapo on 2011-01-09
Ok i got it working on my end. I had to revert back to skype 2.1.0.47 and install jackd and idjc from source. Now everything runs fine and i'm running 10.10 currently btw.:D

---

### Post by Minchkin on 2011-01-23
I got IDJC from source, reinstalled Jackd, but for some reason, I am not getting any of the files with .la. What is going on?

---

### Post by eldafani on 2012-03-26
Hello,
I have followed the instructions here and in other posts and still am unable to use skype 2.2.0.35 together with IDJC 0.8.1 in Ubuntu 10.04 LTS. Can someone please explain step by step how to get this work?
Thank you,
Daniel

---

### Post by dimas869 on 2012-04-18
i am not able to hear Skype when i start IDJC

My Skype is a beta Version 2.2.0.35
and my IDJC is 0.8.5-2
and i am in Ubuntu Oneiric

so i wonder if the instructions here still apply for this versions as libasound2-plugin 1.0.24-0ubuntu6.1 (which i have installed) play and capture via Jack now

so i would appretiate if someone can give me update about how to get Skype and IDJC to work

thanks

---

### Post by tumutanzi.com on 2012-05-19
The first time I heard Idjc, anything is possible, seems.

---

