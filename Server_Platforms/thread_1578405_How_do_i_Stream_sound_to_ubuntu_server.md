---
title: "How do i Stream sound to ubuntu server?"
date: 2010-09-20
forum: Server Platforms
---

### Post by Artyom7 on 2010-09-20
Hi all,
I have a headless server set up at home ( ubuntu 10.04 64 bit ). It has a 4.1 capable soundcard and i just happen to have 4.1 speakers.

My laptop ( which i mostly use to do my work, and to watch movies ) does not have a 4.1 capable soundcard. There is only one point for the headphones and one for the mic.

This is what i want to do.
I want to be able to play videos on my laptop, and stream the sound over wifi to the server, and have the server play it off its sound card.

I have already managed to get the server to play mp3's using cplay over ssh ( its damn cool!! ), so i know that sound output is working fine.

I guess i somehow have to get the server to "receieve" sound over wifi and "redirect " to its sound device. at the same time i have to configure my laptop ( or a player ) to send the "output" through the network ( in this case WiFi ). The question is how?

Could someone point me in the right direction? i have not been able to find a solution online.
Thanks.

---

### Post by HermanAB on 2010-09-20
Howdy,

See this link and scroll down to piping audio around the house:
[http://www.aeronetworks.ca/ogg2mp3-howto.html](http://www.aeronetworks.ca/ogg2mp3-howto.html)

---

### Post by Artyom7 on 2010-09-21
Hey, thanks Herman. I will go over the instructions. seems a bit complicated ( i am kinda of a noob still ), but i will try, and will report back on the progress.

One thing i did notice is that the instructions are specifically to play mp3's.

---

### Post by Artyom7 on 2010-09-21
Hi,
I have gone through that link, and what i want to achieve is a bit different.

I want to play the video on my laptop, but i want to stream the sound over to my server.. is that even possible?

That guide explains how to play mp3's via a server.
I tried that as well, however i get an error saying

```

sox FAIL formats: no handler for given file type `mp3'
nc: timeout cannot be negative

```

how do i redirect the output of say "cat file.mp3" to a sound device?
if i do "cat file.mp3 > /dev/[whatever is the sound device], will it work?

---

### Post by Artyom7 on 2010-09-21
so i have an idea

VLC player has the option of setting the sound output to a file.

now i am thinking that if i somehow can set the output file to be written to a particular directory on my server, i can get the server to play that file. now obviously this will not work directly.
i am thinking maybe some sort of a daemon that waits for a particular file to be created in that directory, and the moment that file appears, start playing it with some sound player ( mpg123 or some other command line tool )

in theory, it sounds like it should work but here are the problems:

1 VLC does not seem to support network locations to save the audiofile

2. is there some sort of a deamon that waits for a file to appear in a particular directory?

a work-around for problem 1 could be to save the file locally, and immediately transfer it to the server by whatever means (scp should be able to do it). But this requires the aforementioned "Daemon" to run on the client machine as well.

can such a thing be scripted?

I am open to suggestions.

---

### Post by the_original_billq on 2010-09-21
How about playing the video on the server, and displaying it back to the laptop?  If the laptop is running windows, look at NX or Cygwin/X.

It works for me, quite well.

Cheers,
-Bill

---

### Post by Artyom7 on 2010-09-21
The laptop is running lucid 64 bit.

---

### Post by the_original_billq on 2010-09-21
Then it's really easy...

ssh -X to your server, and run the video app.

Your sound will use the server sound, and the video will play on your laptop...

You'll need opensshd running on the server to allow you to log in, but I'm betting you already have it.

HTH,

-Bill

---

### Post by Artyom7 on 2010-09-22
> **the_original_billq said:**
> Then it's really easy...

ssh -X to your server, and run the video app.

Your sound will use the server sound, and the video will play on your laptop...

You'll need opensshd running on the server to allow you to log in, but I'm betting you already have it.


Do i need to have gnome desktop installed to run a video app?
I do not think its possible to play videos on a command-line interface.. or is it?

ssh man page for -X option has this to say:
```

-X      Enables X11 forwarding.  This can also be specified on a per-host
             basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user's X authorization database) can access the local X11 display
             through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY
             extension restrictions by default.  Please refer to the ssh -Y
             option and the ForwardX11Trusted directive in ssh_config(5) for
             more information.

```

I have difficulty understanding this.

---

### Post by aeiah on 2010-09-22
you shouldnt need X on the server because you'll be forwarding that over to your laptop. on your laptop try:
```

ssh -f -T -X username@serverIP 'mplayer videoname.avi'

```

if this doesnt work, do the same but with -v, so you get some error messages.

if it does work you can think about working it into a script


edit: you need the quotes surrounding the command. ive just tested this and it works for me, producing sound from the server and displaying video on my netbook. if you're running over flakey wireless you may find it can't cope. this BRRIP .avi is pushing through about 8mb/s, which my wireless card cant do. its probably because its also pushing the sound, even though it isnt being played on the netbook.

---

### Post by Artyom7 on 2010-09-22
Thanks for the suggestion aeiah.
I can't try that right now since i am at work.
Will try in a couple of hour and post back.

---

### Post by aeiah on 2010-09-22
just edited my last post. it works for me. i use a similar command on my netbook to open exaile on my main pc and play it through my main pc's speakers

---

### Post by Artyom7 on 2010-09-22
> **aeiah said:**
> 
ssh -f -T -X username@serverIP 'mplayer videoname.avi'


i tried that command
this is the output i get 
```

/var/cache/apt/archives$ Creating config file: /home/artyom/.mplayer/config
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/ext320/home/share/Videos/video.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DIV3]  576x304  24bpp  23.976 fps  1059.8 kbps (129.4 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
vo: couldn't open the X11 display ()!
[vdpau] Could not open dynamic library libvdpau.so.1
vo: couldn't open the X11 display ()!
VO XOverlay need a subdriver
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
vo: couldn't open the X11 display ()!
commandline read: mplayer
svgalib: Cannot get I/O permissions.
commandline read: /media/ext320/home/share/Videos/video.avi

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.8 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-04-09 12:41) 
(*) Direct/Memcpy: Using Generic 64bit memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
[VO_SDL] SDL initialization failed: DirectFBCreate: Initialization error!.
Can't open /dev/fb0: Permission denied
[fbdev2] Can't open /dev/fb0: Permission denied

```
this looks very cryptic to me.

---

### Post by Blackrider69 on 2010-10-31
Hi!

Because I don't want to open a new thread, I will use this one. I would like to know, if it would be possible to stream audio with an application like [Nicecast]("http://www.rogueamoeba.com/nicecast/") for Mac (or [icecast]("http://www.icecast.org/") for the matter) from my laptop (a Mac) to my Ubuntu 10.04 Server in my living room in order to play music on my Hi-Fi system. 

The server is connected to the internet directly via a FiOS modem, while the Mac is connecting wirelessly to the internet over a Linksys WRT54G router. I use this configuration, because I found it to be more stable and reliable. I would try [Airfoil]("http://www.rogueamoeba.com/airfoil/"), but I doubt it would work over a router.

Any ideas or thoughts on the subject would be greatly appreciated.

Thanks, Jan

---

### Post by Artyom7 on 2010-11-06
I have not been able to make this work yet.
Not that i have tried much.
"ssh -X" does not seem to work. I can't understand how it will work either. I mean, what will happen if i play a video on the server via ssh? Will a window pop up on the client machine and play the video?

I thin a simpler alternative is to just stream only sound to the server.
But how?

---

