---
title: "Recording from Gstreamer fails (stops at PAUSED state)"
date: 2012-10-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by moma on 2012-10-08
Hello,
I have started to port my audio-recorder to Ubuntu 12.10. The  recorder uses Gstreamer-pipeline to record sound from all kinds of audio devices.

The problem is this:
The recording pipeline stops very, very often at PAUSED state. It's virtually impossible to make the pipeline rolling after it blocks at PAUSED. Stopping the pipeline freezes the application/GUI and it has to be killed off. Only each 5.th attempt of recording succeeds.

Here is a minimal test-application (test10.c).
Please grab it, compile and test it on your Ubuntu 12.10 installation.
Ref: [http://www.futuredesktop.org/tmp/test10.c](http://www.futuredesktop.org/tmp/test10.c)

Compile it:
```
gcc -Wall test10.c -o test10 $(pkg-config --cflags --libs gtk+-3.0 gthread-2.0 gstreamer-0.10)

And run:
./test10
```
Click the [Create pipeline/start recording] button to create a recording-pipeline. It should go to GST_STATE_PLAYING state. 

**This is a normal output.** 
It outputs level values (audio peak values)  in a terminal window.
```
Setting state to GST_STATE_PLAYING. Should NOT stop at PAUSED!
Pipeline state changed from NULL to: READY  (stat=PAUSED pending=PLAYING).
Pipeline state changed from READY to: PAUSED  (stat=PAUSED pending=PLAYING).
Pipeline state changed from PAUSED to: PLAYING  (stat=PLAYING pending=VOID_PENDING).
level value=0.140
level value=0.219
level value=0.249
level value=0.163
...
level value=0.250
```

**This is erroneus output.** 
The pipeline stops at PAUSED, and PLAYING state is pending for ever/forever.
```
Setting state to GST_STATE_PLAYING. Should NOT stop at PAUSED!
Pipeline state changed from NULL to: READY  (stat=PAUSED pending=PLAYING).
Pipeline state changed from READY to: PAUSED  (stat=PAUSED pending=PLAYING).

```

This works absolutely correct on Ubuntu 12.04.

The audio-recorder in question:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

EDIT: GNOME's own sound recorder has the same issue. It freezes too.
The funny
[[img]http://bildr.no/thumb/1290726.jpeg[/img]](http://bildr.no/view/1290726)

---

### Post by mc4man on 2012-10-08
seems to work ok (test10), starts, stops, starts, ect. or starts, pause, continue, pause, continue, ect.

Haven't had it refuse to start. The only 'issue' with test10 is it records at a fairly low volume compared to regular ar

(previously had tested precise version in 12.10 - it also worked ok though _occasionally_ the indicator would lock up & do nothing

---

### Post by moma on 2012-10-08
Hello 
Very good mc4man.
I used rather old image to install this Ubuntu 12.10, although I upgraded it with latest packages. I will make a re-installation. I will let you know the result after that (maybe tomorrow ou quarta-feira).

Ok, I marked the latest code good-enough and pumped it to launchpad.net". Replaced GTK3's deprecated functions with newer syntax.  
$ bzr push lp:~osmoma/audio-recorder/trunk
Pushed up to revision 194.
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/changes/](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/changes/)
Of course, the code is not tested at all because the pipeline-bug.

---

### Post by xebian on 2012-10-08
It would be nice if you'd use gstreamer1.0 instead of gstreamer0.10 ?

---

### Post by moma on 2012-10-09
Hello,
Good idea Xebian.

Will Gstreamer 1.0 be installed in Ubuntu 12.10 and Fedora 18 as default? Or should I make Gstreamer 1.0 a dependency of audio-recorder so it is installed automatically.

**EDIT**: The changes in audio-recorder for Gstreamer-1.0 are relatively few. I also compiled the sample test10.c with gstreamer-1.0 and it has the same failure (as gstreamer-0.10) on this Quantal-machine.

Ref: [http://cgit.freedesktop.org/gstreamer/gstreamer/tree/docs/random/porting-to-1.0.txt](http://cgit.freedesktop.org/gstreamer/gstreamer/tree/docs/random/porting-to-1.0.txt)

I have decided to go for Gstreamer 1.0.  I cannot see any good reason for this move, but it has to be done sooner or later; and the word sooner tastes better.

---

### Post by moma on 2012-10-10
Re-hello,
Ok, the application behaves much better after new 12.10 installation. So that bug is now buried.

Other coisas:

The recorder uses libgnome-media-profiles-dev to get audio- profiles from GNOME's configuration registry.

Start gconf-editor and browse to:
system -> gstreamer -> 0.10 -> audio -> profiles.

This library now fails when ran with Gstreamer 1.0.

The error lies in gm_audio_profile_get_active_list() function.

It obviously tries to create gstreamer1.0 pipelines from Gstreamer 0.10 profiles, and prints:

(audio-recorder:8810): GStreamer-WARNING **: 0.10-style raw audio caps are being created. Should be audio/x-raw,format=(string).. now.

(audio-recorder:8810): GStreamer-WARNING **: 0.10-style raw audio caps are being created. Should be audio/x-raw,format=(string).. now.
....
....
And it fails to return values.

To support Gstreamer 1.0, they should replace "audio/x-raw-int" and "audio/x-raw-float" with "audio/x-raw".
Eg. see: [https://wiki.ubuntu.com/Novacut/GStreamer1.0](https://wiki.ubuntu.com/Novacut/GStreamer1.0)

Gstreamer 1.0 should have its own values in GNOME's registry (in GConf or DConf) with path: system -> gstreamer -> 1.0 -> audio -> profiles.

Any opinions.
-------

EDIT: I can temporarily avoid this error by using gm_audio_profile_get_list() instead of gm_audio_profile_get_active_list().

    GList *gm_audio_profile_get_list(void);

    // This fails: media_profiles_list = gm_audio_profile_get_active_list();
    media_profiles_list = gm_audio_profile_get_list ();

We have to wait util Totem or some other GNOME-app upgrades to Gstreamer 1.0 and puts new values to DGonf or CGonf registry.

Until then we use this implementation.
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c)

EDIT: Another small bug resolved here.
[http://lists.freedesktop.org/archives/gstreamer-devel/2012-October/037526.html](http://lists.freedesktop.org/archives/gstreamer-devel/2012-October/037526.html)

Things look good.

---

### Post by moma on 2012-10-11
Re-hi,
Audio-recorder for Ubuntu 12.10/Gstreamer 1.0 is starting to take shape. I have only tested basic recording tasks but it behaves very well.

Go on and test you too. Grab the code from
[https://code.launchpad.net/audio-recorder](https://code.launchpad.net/audio-recorder)
INSTALL file will tell you about dependencies.

---

