---
title: "Allowing the Apache user to run mpg321"
date: 2010-04-06
forum: Server Platforms
---

### Post by tlevine on 2010-04-06
I'm currently at university and live in a dormitory, and I go to sleep much earlier than my peers. Because of this, I sometimes tell them to wake me up if they need me after I'm asleep. This can be difficult for them to do if I've locked my door.

I wrote a cgi script that plays music so people can wake me up,
```

#!/usr/bin/perl -w
print "Content-type: text/html\n\n";
system("mpg321 /home/tlevine/Musik/DragonForce/*/*.mp3");
```

but the Apache user, www-data, doesn't have the permissions to play the music.

```
$ ./alarm.cgi
Content-type: text/html

High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
/home/tlevine/Musik/DragonForce/*/*.mp3: Permission denied
```

I think I just need to add www-data to a certain group, but I already tried adding it to audio, and that didn't help. What group do I add it to, or what else am I missing?

---

### Post by tlevine on 2010-04-06
Oh, silly me! www-data didn't have permission to read my home directory! I made it read an mp3 in the same directory, but now I have a different problem.

```
$ ./alarm.cgi
Content-type: text/html

High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : Through The Fire And Flames     Artist: DragonForce                   
Album  : Inhuman Rampage                 Year  : 2006
Comment:                                 Genre : Power Metal                   

Playing MPEG stream from 01 - DragonForce - Through The Fire And Flames.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
No protocol specified
XOpenDisplay() failed
Home directory /var/www not ours.
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
ALSA snd_pcm_open error: Device or resource busy
/var/www/.esd_auth: Permission denied
Can't find a suitable libao driver. (Is device in use?)
```

And it doesn't play. Below is the script.

```
#!/usr/bin/perl -w
print "Content-type: text/html\n\n";
system('mpg321 01\ -\ DragonForce\ -\ Through\ The\ Fire\ And\ Flames.mp3');
```

---

