---
title: "[SOLVED] Cheap but not Easy -- Keeping up with the CODECs"
date: 2008-12-14
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-12-14
I have, since Breezy, wanted to rip a stream off the 'net. I've tried to find the right combination of software to do this, again, today. Making this the 5th or 6th attempt since Breezy (maybe Hoary)

When I googled: ubuntu ripping audio stream

I eventually found:

HowToRipRealaudioStreamsToMp3 (last edited 2008-10-14 18:12:18 by littlergirl)

[https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3](https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3)

I thought this would be a good starting point, as it had the Ubuntu "look". 

And, even though it uses Real Audio (which I had experienced very bad luck with a few years ago), I thought: "By now, it must be better", so I d/l-d realaudio. That worked, no problem! But when I tried to find vsound, it's not in the repositories. It is on the 'net but that page seems to have not had work done on it since 2004. Maybe that doesn't mean anything. I'm not a coder, I write cookbooks (food) for a living. So, I couldn't go further. I got confused. Maybe the vsound was perfected. Perfected a long time ago and it won't crash the new sound system. But the results of googleing for vsound & LaunchPad leaves me feeling bad. And as the package had been removed from the repositories, I chickened out. I don't like spending time fixing what something (somebody) else broke.

My point is: since there is no way for an end-user such as myself, who needs software and applications to be "user friendly" enough to not make things worse, to know whether the above mentioned page would work, yet DO NO HARM, and as in doing further research it seems as though Ubuntu may have moved more towards MPlayer, Lame, etc., but there is NO way for me to figure this out on my own, I'm posting about it here. In hopes that someone reading this can give me some directions.

Thanks for working your way through my long post.

---

### Post by billgoldberg on 2008-12-14
You can use vlc to rip streams.

There is a little how-to here.

I presume everything in that tutorial will apply to the Ubuntu version.

[http://forum.videohelp.com/topic316907.html](http://forum.videohelp.com/topic316907.html)

It will produce a ASF file.

I guess vlc can play that, but if you want to conver it to xvid or something (or mp3 if it's an audio stream) you can use this program:

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

---

### Post by logos34 on 2008-12-14
Yes, it looks like they dropped vsound from the repos.  But in any event I don't think vsound is what you want.  I started to use it way back, but the problem is it saves the stream as a huge .wav file, which you then have to compress down:

> VSOUND - capture streaming RealAudio to wav (--> output = ~/vsoundxxxx.au [Sun AU format])

$ vsound -d -t -f radiostream.wav realplay rtsp://<URL>

[Ctrl + C to end].  Then compress file:

$ lame radiostream.wav radiostream.mp3

#

I quickly abandoned it for the one-step process of mplayer:
> 
$ mplayer -playlist "URL" -dumpstream -dumpfile radiostream.ram

Mplayer is my preferred way to capture Realplay/.ram/.rm streams.  Streamtuner I use for .mp3 streams

---

### Post by Mark_in_Hollywood on 2008-12-14
Am I doing this correctly?

mark@Lexington-19:~$ mplayer -playlist "http://boss.streamos.com/real/csps/clerks_office/service/church_service.ram" -dumpstream -dumpfile church.ram
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) D CPU 3.06GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving boss.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: boss.streamos.com
Resolving boss.streamos.com for AF_INET...
Connecting to server boss.streamos.com[69.27.160.214]: 80...
Cache size set to 320 KBytes
Resolving boss.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: boss.streamos.com
Resolving boss.streamos.com for AF_INET...
Connecting to server boss.streamos.com[69.27.160.214]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://sos686-1-rm.edgestreams.net/clerks_office/service/.uid.MVnMAABWmJtduWy3yQ93d2be3fb4f3480cccc8a801308509e1.church_service.rm?auth=caEasa0asbCdmdGbJcTaAcydhdEbNdUchau-bjrB3e-eS-JCCnrwzzrBCyttzn&aifp=0001.
Resolving sos686-1-rm.edgestreams.net for AF_INET6...
Couldn't resolve name for AF_INET6: sos686-1-rm.edgestreams.net
Resolving sos686-1-rm.edgestreams.net for AF_INET...
Connecting to server sos686-1-rm.edgestreams.net[209.170.97.120]: 554...
Cache size set to 320 KBytes

[then I did ctrl-c] and the terminal said:

MPlayer interrupted by signal 2 in module: dumpstream

---

### Post by logos34 on 2008-12-15
that's correct.

here try this:

> user@ubuntu:~$ mplayer -playlist "http://www.bbc.co.uk/radio4/science/rams/earthmadeforlife_20050518.ram" -dumpstream -dumpfile bbc-earth.ram

I just did it so I know it works. look in your home dir for 'bbc-earth.ram' file

mine complained a little but I just ignored it.  mplayer playback is fine
> MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2600+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory

---

### Post by logos34 on 2008-12-15
I tried yours too--again, it works but it complains.  ignore

> mplayer: could not connect to socket
mplayer: No such file or directory

but I didn't get this:
> 
Failed to open LIRC support. You will not be able to use your remote control.

I'm not sure that's a fatal error though.

---

### Post by Mark_in_Hollywood on 2008-12-15
Waht a surprise! The file is there and in an mp3 format!!!

As for LIRC, that for Linux Infra-Red Control, something to do with MythTV. As far as I know, I have no parts of that installed and can ignore that message.

Thanks, I'm closing this thread.

---

### Post by logos34 on 2008-12-15
> **Mark_in_Hollywood said:**
> Waht a surprise! The file is there and in an mp3 format!!!

really?  are you sure?

check with
> 
file *filename*.mp3

that'll verify the format

---

