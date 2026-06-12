---
title: "MPD &amp; Ubuntu-Server"
date: 2010-04-22
forum: Server Platforms
---

### Post by arrrghhh on 2010-04-22
Long story short, I was getting segfaults whenever I would try to play songs encoded with AAC - aka m4a files (iTunes non-DRM).

Basically the version of MPD that is bundled with Ubuntu has issues with AAC files.  Solution?  Install the newest version!

Now I prefer to install things from repo's so they stay up-to-date without needing to recompile.  With that said, when you do add this repo, you'll get updates VERY frequently for MPD.  Which I am personally fine with - if it causes an issue for you, compiling will be your best option.

First, if you have mpd installed, please uninstall ```
sudo apt-get purge mpd mpc
```

Next, just three simple commands:```
sudo add-apt-repository ppa:gmpc-trunk/mpd-trunk
sudo apt-get update
sudo apt-get install mpd mpc
``` Enter those as separate lines, one at a time!

Now, ```
mpd --version
``` should yield ```
mpd (MPD: Music Player Daemon) 0.16~git

Copyright (C) 2003-2007 Warren Dukes <warren.dukes@gmail.com>
Copyright (C) 2008-2010 Max Kellermann <max@duempel.org>
This is free software; see the source for copying conditions.  There is NO
warranty; not even MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Supported decoders:

[mad] mp3 mp2
[vorbis] ogg oga
[oggflac] ogg oga
[flac] flac
[sndfile] wav aiff aif au snd paf iff svx sf voc w64 pvf xi htk caf sd2
[audiofile] wav au aiff aif
[faad] aac
[mpcdec] mpc
[wavpack] wv
[sidplay] sid mus str prg P00
[wildmidi] mid
[ffmpeg] 16sv 3g2 3gp 4xm 8svx aa3 aac ac3 afc aif aifc aiff al alaw amr anim apc ape asf atrac au aud avi avm2 avs bap bfi c93 cak cin cmv cpk daud dct divx dts dv dvd dxa eac3 film flac flc fli fll flx flv g726 gsm gxf iss m1v m2v m2t m2ts m4a m4b m4v mad mj2 mjpeg mjpg mka mkv mlp mm mmf mov mp+ mp1 mp2 mp3 mp4 mpc mpeg mpg mpga mpp mpu mve mvi mxf nc nsv nut nuv oga ogm ogv ogx oma ogg omg psp pva qcp qt r3d ra ram rl2 rm rmvb roq rpl rvc shn smk snd sol son spx str swf tgi tgq tgv thp ts tsp tta xa xvid uv uv2 vb vid vob voc vp6 vmd wav wma wmv wsaud wsvga wv wve

Supported outputs:

shout null fifo pipe alsa ao oss openal pulse jack httpd recorder

Supported encoders:

null vorbis wave flac

Supported protocols:

file:// http:// mms:// mmsh:// mmst:// mmsu:// gopher:// rtp:// rtsp:// rtmp:// rtmpt:// rtmps://
```

You're done!  Enjoy that music & MPD!

---

### Post by arrrghhh on 2010-04-23
Really?  No one uses MPD on their server to play music locally?  This was one of the main things I want my server to do...  Well, that and a lot of other server-like things that are setup and doin fine :D  Just struggling with MPD!  Any help is appreciated!

---

### Post by arrrghhh on 2010-04-23
So MPD is definitely segfaulting:

```
decoder: audio_format=44100:16:2, seekable=true
Segmentation fault
```

Doesn't really give me a whole lot, and there's nothing from today in the MPD error log... However, I did find this in /var/log/messages:

```
Apr 23 15:09:01 nas kernel: [161048.253573] mpd[22957] general protection ip:b6efc1b5 sp:b53e1850 error:0 in libavcodec.so.52.20.1[b6ab4000+52b000]
```

Perhaps someone can help me make sense of that?

---

### Post by arrrghhh on 2010-04-26
So the guys in #mpd told me to compile the latest (of course) because the one in Ubuntu repo's is just soooo old...

At any rate, I did that, and now MPD doesn't see any of my music - like it doesn't have the rights.  But the repo version didn't have any issues with this at all... despite this, the #mpd guys made me chmod my Music dir to 777 and chown it all to my user.  Still no go.  So I'm at a loss here.  I have a custom compiled version of MPD installed now, and it doesn't work either.  I'm concerned about going back to the one from the repo's, because I don't know how to uninstall this custom compiled one...

Any help would be GREATLY appreciated.  I really miss MPD, and I'm sure someone here uses it!!

---

### Post by arrrghhh on 2010-04-28
Now I'm stuck.  The compiled MPD (v0.15.9) wouldn't see my music, kept saying error file/directory not found.  The version from the repo's .0 or .4, can't remember what it's up to now had NO problems seeing my music.  Same user, same rights...

At any rate, the version from the repo's segfaults every time it tries to play music.  I'd really like some help, mpd is by far my favorite cli music server!

---

### Post by arrrghhh on 2010-04-29
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556198](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556198)

So this looks like the EXACT problem I'm having... but for them it's resolved by an upgrade!!

I'm running the newest from the repo's, I think mpd is 0.15.4, and libavcodec52... I'm not sure.  I'll have to check... Any suggestions based on that thread tho?  I got excited when they said it was fixed, but it's not for me!!

Confirmed - MP3s are able to play, M4A or AAC files segfault... So definitely a codec issue, but why?  I have all the right codecs installed (I believe...)?

---

### Post by arrrghhh on 2010-04-29
So it seems the answer is to upgrade to 0.15.6 or newer.  The newest stable version is 0.15.9...

My question is now, can I get a repo for the newest MPD version?  I tried, and this is what resulted:

```
sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://archive.canonical.com lucid/partner Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

So I commented out those lines in my sources.list...:
```
# 
# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

#PS3 Media Server Repo
#deb http://deb.paissad.net/ unstable main contrib non-free
#deb-src http://deb.paissad.net/ unstable main contrib non-free
#deb http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main
#deb-src http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main

#libzen0 libmediainfo0 for above
# deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#MPD bleeding edge
# deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main

#More MPD Stuff
#deb http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
#deb-src http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
```

But it's still happening!!  I'm so close I can taste it, anyone help with a repo for MPD??

---

### Post by arrrghhh on 2010-04-29
Well perhaps it won't actually help anyone since no one here seems to use MPD... but if you do, and need to decode AAC files you have to upgrade to a version newer than 0.15.4.  There's a bug that causes it to segfault with a sync issue, that debian bug is the exact problem.

Add these to your /etc/apt/sources.list:
```
#Newest MPD Stuff
deb http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
deb-src http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
```

Do an apt-get update, if you already have MPD installed it'll update to the newest, currently 0.15.9.  Works beautifully now, kinda surprised no one else here uses MPD on their server.  It's simply fantastic.

---

### Post by jjw_uk on 2010-05-02
Thanks this sorted out my problem of mpd crashing when trying to play m4a/mp4 files.

---

### Post by arrrghhh on 2010-05-02
> **jjw_uk said:**
> Thanks this sorted out my problem of mpd crashing when trying to play m4a/mp4 files.

Glad to hear I helped someone :D

---

### Post by snkiz on 2010-05-14
I've been putting off installing mpd because I thought I'd have to compile acc support in. (had mpd on my server in karmic but no acc.) so I'll try the ppa see how that goes.

BTW In karmic i set mpd to connect directly to pulse on my desktop, I set my desktop to allow the connection. it was a beautiful setup.

your not alone :)

---

### Post by arrrghhh on 2010-05-14
I had an issue running Pulse sessionless on my server was the issue I recall.  I did eventually sort it out, but an update killed it, which prompted the eventual upgrade to Lucid.

Let me know if you do sort out how to properly run Pulse in a sessionless fashion.  Everywhere I read, and every response I got was that Pulse was meant to be tied to a user login, not meant to be run as a service...

---

### Post by snkiz on 2010-05-15
> **arrrghhh said:**
> I had an issue running Pulse sessionless on my server was the issue I recall.  I did eventually sort it out, but an update killed it, which prompted the eventual upgrade to Lucid.

Let me know if you do sort out how to properly run Pulse in a sessionless fashion.  Everywhere I read, and every response I got was that Pulse was meant to be tied to a user login, not meant to be run as a service...

The trick is you don't. I spent days trying before I figured that out. Let me show you, in you mpd.conf file we take care of the address we bind to 
```
# For network
bind_to_address		"0.0.0.0"
```
then under the audio output section we find an entry for pulse
```
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
audio_output {
	type		"pulse"
	name		"My Pulse Output"
	server		"<your desktop ip or host>"
#	sink		"remote_server_sink"	# optional
}
```
Then on your desktop
```
 sudo apt-get install padevchooser 
```
Its a little tray program to configure pulse. Run it and goto "configure local sound server" you'll see the network server tab, under that check "enable access to local sound devices" and "don't require authentication"

After all that mucking about you **should** be good to go. Connect with your favorite mpd client. (Mine is currently gmpc.)

---

### Post by snkiz on 2010-05-15
Still no love for acc, but I'm using mediabuntu repos to get the codecs, you would think they would be better. I'll have to try stock codecs see how that goes.

this is waht the log said:
```
May 15 09:27 : Failed to open file:///home/snkiz/Music/Tupac/Unknown/Tupac%20-%20All%20eyez%20on%20me.m4a: Unrecognized URI
```

---

### Post by arrrghhh on 2010-05-15
Weird, when I was running 0.15.4 from the repo's MPD would just segfault immediately.

0.15.9, plays 'em perfectly.  Do you have all the gstreamer stuff installed for AAC?  Crap, I guess I should've included that in my travels to get MPD workin with AAC files.

Oh and your guide for Pulse... perhaps we use our servers differently.  I had done that for the MPD side of things, the issue was I couldn't get an actual pulseaudio session on the backend unless I logged into the server.  I have my server headless, just power & network plugged into it.  So on a reboot, I need everything to be run as a service.  Currently I just stream to other rooms with the built-in HTTPd server.  It's a little laggy, but not too bad.  I think eventually I'm going to get a fairly powerful FM transmitter and just throw it onto the back of the server's audio output.  That way I can add "clients" very easily - any radio is now a client of the music server :D  Low-tech, I know but if you spend a little extra $$$ and get a quality transmitter, it works great.

---

### Post by snkiz on 2010-05-15
No I guess I wasn't clear what I'm saying is you don't even need pulse on you server you just need to be able to connect mpd to pulse on your desktop. My guide will do that. However that means you need all your clients to have pulse to connect to. An FM transmitter as "lo-tec" as it is would be an effective solution too :D

I have mpd 15.9 and I'm pretty sure I've got all the gstreamer stuff. (I'm going to double check.) The diffrence is I pulled the gstreamer stuff from medibuntu instead of the default repos. So I'm gonna try and purge those and use stock gtreamer as soon as my kids are in bed, we'll see how that goes.

---

### Post by arrrghhh on 2010-05-15
> **snkiz said:**
> No I guess I wasn't clear what I'm saying is you don't even need pulse on you server you just need to be able to connect mpd to pulse on your desktop. My guide will do that. However that means you need all your clients to have pulse to connect to. An FM transmitter as "lo-tec" as it is would be an effective solution too :D

I have mpd 15.9 and I'm pretty sure I've got all the gstreamer stuff. (I'm going to double check.) The diffrence is I pulled the gstreamer stuff from medibuntu instead of the default repos. So I'm gonna try and purge those and use stock gtreamer as soon as my kids are in bed, we'll see how that goes.

Cool, I'll give that a shot.  Pulse seems to sync it better, and I also wanted to play with ProjectM & pulse :D

Make sure you have the packages for faad2.  I can't remember if I compiled that or found a package for it... I did a lot of compiling of stuff suggested on the MPD wiki site trying to fix this issue initially... Let me know if you have more issues with AAC, I can try to take a closer look at my system to see what I had to install.

---

### Post by avatardvr@gmail.com on 2010-06-25
Cool. Just wanted to add my two cents.  I had a problem with mpd playing back mp4 files, and as i only had a few tunes and they wernt important i deleted them lol.  so issue resolved. been using mpd for about a year now, two different servers in the house, one for the landlord upstairs so they can play their tunes where ever they want (amped out to the living room and the pool out back) and my personal server.  gmpc is the best client out there that i can find so far.  would like a few extra features but I dont know how to code.  Thanks for the info!

---

### Post by arrrghhh on 2010-06-26
> **avatardvr@gmail.com said:**
> Cool. Just wanted to add my two cents.  I had a problem with mpd playing back mp4 files, and as i only had a few tunes and they wernt important i deleted them lol.  so issue resolved. been using mpd for about a year now, two different servers in the house, one for the landlord upstairs so they can play their tunes where ever they want (amped out to the living room and the pool out back) and my personal server.  gmpc is the best client out there that i can find so far.  would like a few extra features but I dont know how to code.  Thanks for the info!

Bummer!  Well pretty much all of my library is mp4/aac... so that wasn't an option :P  When I had previous builds of mpd working with these files previously, I knew there had to be an issue.  The segfaults we baffling, but I'm glad I got it worked out eventually.

Honestly after all the GUI interfaces I've tried, web interfaces be damned the Firefox addon "MPM" or MusicPlayerMinion - is by far my favorite.  Handles my gigantic list no problem.  Other clients... have issues when I have all my songs in a playlist.  MPM, no issues.  If you go to the Google code site as well, there's a wonderful v2 edition that's just fantastic!  Try it out!

---

### Post by avatardvr@gmail.com on 2010-06-26
Right on.  thanks for that, always looking to improve the client.

---

### Post by Cool Javelin on 2010-07-04
arrrghhh:

Thanks for this thread, I too am trying to make a music server for my home.

I tried the following on my brand spankin' new (well, to me anyway) 10.04 Ubuntu server:

```

Add these to your /etc/apt/sources.list:

#Newest MPD Stuff
deb http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
deb-src http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main

```

then did sudo apt-get update, but got the following error,

```

Fetched 63.2kB in 2s (31.1kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DB53B5AC116A57C

```

Did you get this, did my MPD update properly?

I am going to follow the rest of this thread and see if I can get it to work.

Thanks, Mark.

---

### Post by snkiz on 2010-07-04
you didn't get the gpg key, by just putting the ppa in your sources like that. There is a way, 
> To install the archive key for this PPA, please enter this command in a terminal:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C116A57C but an easy way to get everything you need in one swoop is to add the ppa through synaptic by adding the line:
> Adding this PPA to your system
You can update your system with unsupported packages from this untrusted PPA by adding ppa:gmpc-trunk/mpd-trunk to your system's Software Sources

quoted from [https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk](https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk)

---

### Post by arrrghhh on 2010-07-04
Ah right, forgot to include that piece.  Thanks snkiz!

---

### Post by spokie-szut on 2010-11-11
YES, I finally fixed that annoyance thanks to your post, thanks man.

Personnally I went that way:

sudo add-apt-repository ppa:gmpc-trunk/mpd-trunk
to add the repo. as suggested by: [http://www.webupd8.org/2009/11/gnome-music-player-client-gmpc-mpd-just.html](http://www.webupd8.org/2009/11/gnome-music-player-client-gmpc-mpd-just.html)

and indeed didn't have to enter the key. 

So, my chronology:

sudo add-apt-repository ppa:gmpc-trunk/mpd-trunk
sudo apt-get update
sudo apt-get install mpd mpc

Then, 

mpd --version

gives:

mpd (MPD: Music Player Daemon) 0.16~git 

Copyright (C) 2003-2007 Warren Dukes <warren.dukes@gmail.com>
Copyright (C) 2008-2010 Max Kellermann <max@duempel.org>
This is free software; see the source for copying conditions.  There is NO
warranty; not even MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Supported decoders:

[mad] mp3 mp2
[vorbis] ogg oga
[oggflac] ogg oga
[flac] flac
[sndfile] wav aiff aif au snd paf iff svx sf voc w64 pvf xi htk caf sd2
[audiofile] wav au aiff aif
[faad] aac
[mpcdec] mpc
[wavpack] wv
[sidplay] sid mus str prg P00
[wildmidi] mid
[ffmpeg] 16sv 3g2 3gp 4xm 8svx aa3 aac ac3 afc aif aifc aiff al alaw amr anim apc ape asf atrac au aud avi avm2 avs bap bfi c93 cak cin cmv cpk daud dct divx dts dv dvd dxa eac3 film flac flc fli fll flx flv g726 gsm gxf iss m1v m2v m2t m2ts m4a m4b m4v mad mj2 mjpeg mjpg mka mkv mlp mm mmf mov mp+ mp1 mp2 mp3 mp4 mpc mpeg mpg mpga mpp mpu mve mvi mxf nc nsv nut nuv oga ogm ogv ogx oma ogg omg psp pva qcp qt r3d ra ram rl2 rm rmvb roq rpl rvc shn smk snd sol son spx str swf tgi tgq tgv thp ts tsp tta xa xvid uv uv2 vb vid vob voc vp6 vmd wav wma wmv wsaud wsvga wv wve

Supported outputs:

shout null fifo pipe alsa ao oss openal pulse jack httpd recorder 

Supported encoders:

null vorbis wave flac 

Supported protocols:

file:// http:// mms:// mmsh:// mmst:// mmsu:// gopher:// rtp:// rtsp:// rtmp:// rtmpt:// rtmps://


And yes arrrghhh you're quite right, mpd just rocks. :)

cheers,

S.

---

### Post by arrrghhh on 2010-11-11
> **spokie-szut said:**
> YES, I finally fixed that annoyance thanks to your post, thanks man...

And yes arrrghhh you're quite right, mpd just rocks. :)

cheers,

S.

No thank you!  Y'know, I was thinking I should make this a how-to and modify the first post so when people start in the thread they get the solution right away.  Would you mind if I used these directions?  Seems like the best solution!

---

### Post by spokie-szut on 2010-11-17
oops !  sorry arrrghhh, _Thank you_. :)
.... was what I meant with all my positive comments. :popcorn:

you can put my post above if you like, no problem on my side.

...the only "cwirk" however, is since I've updated to that 0.16~git version, I'm having some little 'things' with my audio device. MPD sometimes will say: 

[I]ERROR: problems opening audio device

[/I]I tried what is advised there: [http://mpd.wikia.com/wiki/Sound_Device_Permission_Problems](http://mpd.wikia.com/wiki/Sound_Device_Permission_Problems)

but without too much success....  the weirdest thing is that it's not very 'repeatable', sometimes it would do, sometimes not.   Usually, it does it right off the bat (at login I have mpd starting automatically) then if I kill it (~$ killall mpd) and restart it (~$ mpd), it works...  unitl it doesn't! ...and send that message again.

In my config here (I followed [http://mpd.wikia.com/wiki/Configuration](http://mpd.wikia.com/wiki/Configuration) basically)

I've let: ~/.mpdconf
with:# An example of an ALSA output:
#
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "PCM"        # optional
    mixer_index    "0"        # optional
}
by default.
....and it used to work perfectly... until now.

Aside from that and since I have multple users here with different configuration, I got rid of the /etc/mpd.conf all together
....shouldn't have done that?
or it's just pb with my ~/.mpdconf audio setup I presented above?

I'm doing a test now with all audio setup commented out for 1 user as this config file mentions: "Setting this block is optional" and mpd autodetect if nothing is setup...   

I'm gonna give it a shot, but as I said, it's gonna be difficult to see the difference since this pb is quite erratic and do not occur all the time.

any suggestion guys? :)

cheers,

S/

---

### Post by arrrghhh on 2010-11-17
Odd, I use that exact same config for my alsa audio device.  Do you have any other outputs that have issues?  I also have an http stream output...

Have you tried removing all of the optional stuff?  You say it used to work, I assume with an older version of MPD?  As in an update broke it...?

Oh, and I modified the first post so people can just reference it for a how-to on this issue.  Thanks again spokie, let me know what's goin on with your current issue :D

---

### Post by spokie-szut on 2010-11-22
Yeash, it's f### annoying. :)

Today I have had a perfect example of that, at login mpd and gmpc was starting auto, but then GMPC gave me:

[I]ERROR: problems opening audio device

[/I]When pressed play from the gui.

So I did this:

guest@home-desktop:~$ mpd --kill
daemon: unable to kill proccess 3245: No such process
guest@home-desktop:~$ su
Password: 
root@home-desktop:/home/guest# killall mpd
root@home-desktop:/home/guest# exit
exit
guest@home-desktop:~$ mpd
guest@home-desktop:~$ mpc play
Moby - Hotel/02 Track 2.wma
[playing] #199/3120   0:00/3:46 (0%)
volume: n/a   repeat: off   random: on    single: off   consume: off

and it worked.

To respond to your questions: :)
 any other outputs that have issues?  --- haven't tried anythingelse than ALSA, ...should I?
tried removing all of the optional stuff? ---- nope, will give it a shoot
assume with an older version of MPD? ---- correct
 As in an update broke it...?  ---- seems like
modified the first post so people can just reference it for a how-to on this issue --- I think it's not a bad idea

Oh, I tried to do as mentioned last time, that is commenting out all output parameters, and it didn't work big time. 

house@home-desktop:~$ mpd
output: No "audio_output" defined in config file
output: Attempt to detect audio output device
output: Attempting to detect a alsa audio device
output: Successfully detected a alsa audio device
house@home-desktop:~$ mpc play
Peter Tosh - Vampire
[paused]  #11844/15269   0:00/3:29 (0%)
volume: n/a   repeat: off   random: on    single: off   consume: off
ERROR: problems opening audio device

....do you know if   /etc/mpd.conf *should* exist even though the ~/.mpdconf has all needed (I don't think it is this really, but anyways).
...I have to say that I'm a bit out of ideas...

cheers,

S/

---

### Post by jahvascriptmaniac on 2011-04-25
Thanks a lot arrrghhh, the solution in your first post solved the segfault issues I was having while playing wma files.

It works fine even though I have a crappy soudcard (Poulsbo / GMA500 on the Fit-PC) that requires a custom driver and library for libva (video/audio hardware accelerated decoding), which makes audo crashy and unstable, whatever player I use.

Thanks a lot, you made my day ! :D

---

### Post by SabreWolfy on 2011-08-31
Running MPD 0.15.4 from repos on Ubuntu 10.04 LTS. CPU usage slowly creeps up to 25%+ over time and seg faults with no message/log when playing aac/m4a files (according to #mpd discussion, this is because of the old version of libavcodec in 10.04 and the problem will remain because of this, regardless of which version of mpd is installed). Can create/update the database fine.

After some discussion on #mpd I was told to install the latest from source (0.16.3). After figuring out the various plugins to install, I installed it, but now I can't control it via /etc/init.d/ and now it does not create the database. Running 'mpc update' reports that the update is already running and the '--create-db' option to 'mpd' itself has been removed. I've added the PPA from post #21 above and I'm installing mpd 0.16.3 now.

The PPA actually gave me 0.17git, which installed fine, created a database and works. CPU usage is at 2% (initially).

Anyone manage to play m4a/aac files on Lucid 10.04 with the default installed libavcodecs?

---

