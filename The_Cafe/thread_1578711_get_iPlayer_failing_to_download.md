---
title: "get_iPlayer failing to download"
date: 2010-09-20
forum: The Cafe
---

### Post by chome4 on 2010-09-20
When I type a show I want to download:
get_iplayer --get 831

I get:

get_iplayer v2.78, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
831:    dirtgirlworld - 8. Hayman, CBeebies, Children's,Entertainment & Comedy,Learning,Pre-School,TV, default

INFO: 1 Matching Programmes
INFO: Checking existence of default version
ERROR: Failed to get iphone URL from iplayer site

INFO: No specified modes (iphone) available for this programme with version 'default' (try using --modes=flashhigh,flashlow,flashstd,flashvhigh,n95_3g,n95_wifi,subtitles)
ERROR: Failed to record 'dirtgirlworld - 8. Hayman (b00nyxk1)'

Any ideas as to what I need to do to resolve this?

---

### Post by neillmitchell on 2010-09-21
I'm seeing this as well. Was working fine at 10pm last night (the 20th), but this morning I'm seeing exactly the same error. Tried various modes without success. Looks like the BBC has changed something :( Using get_iplayer 2.78 and rtmpdump 2.3.

---

### Post by andymorton on 2010-09-21
Have you tried downloading through the iplayer desktop application instead? 

andy

---

### Post by neillmitchell on 2010-09-21
> **andymorton said:**
> Have you tried downloading through the iplayer desktop application instead? 

andy
I'm running Linux, but don't all the versions use the same perl script anyway?

Cheers
Neill.

---

### Post by andymorton on 2010-09-21
> **neillmitchell said:**
> I'm running Linux, but don't all the versions use the same perl script anyway?

Cheers
Neill.

The desktop application works on Linux. 

andy :)

---

### Post by nothingspecial on 2010-09-21
Development has ceased offcially on get_iplayer.

There are a couple of forks that may work for you.

I`m am unsure of the exact legality of the situation.

I used to use get_iplayer to download certain BBC radio shows to listen to on my iPod when out and about. Suddenly the BBC changed it`s position and the original developer of get_iplayer got a nasty letter/email from the BBC`s lawyers.

It was not downloading and keeping the content for 30 days that the bbc had an issue with. It was people sharing that content outside of the UK. A big chunk of the BBC`s income is made from selling content abroad. So I am unsure of the BBC`s legal position on end users using unsupported 3rd party apps to download content.

I know I miss it.

---

### Post by matthewbpt on 2010-09-21
get_iplayer is still being actively developed by a different set of developers, check [http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html), for support send an email to their mailing list [http://lists.infradead.org/mailman/listinfo/get_iplayer](http://lists.infradead.org/mailman/listinfo/get_iplayer) queries usually get replies within a day and they're very helpful.

EDIT: The output sugests there isn't an iphone stream for that particular programme, which is the stream which is trying to be downloaded, I usually download the flashvhigh or flashhd stream, these need you to also use rtmpdump which can be downloaded and installed/compiled easily (google). Once you have that installed you would do

```
get_iplayer -g xxx --mode=flashvhigh --flvstreamer=/path/to/rtmpdump
```

---

### Post by neillmitchell on 2010-09-21
> **matthewbpt said:**
> get_iplayer is still being actively developed by a different set of developers, check [http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html), for support send an email to their mailing list [http://lists.infradead.org/mailman/listinfo/get_iplayer](http://lists.infradead.org/mailman/listinfo/get_iplayer) queries usually get replies within a day and they're very helpful.

EDIT: The output sugests there isn't an iphone stream for that particular programme, which is the stream which is trying to be downloaded, I usually download the flashvhigh or flashhd stream, these need you to also use rtmpdump which can be downloaded and installed/compiled easily (google). Once you have that installed you would do

```
get_iplayer -g xxx --mode=flashvhigh --flvstreamer=/path/to/rtmpdump
```
Hi.

Been running this for a while now. Great that it did not die :) 

It does look like both get_iplayer 2.78 and iplayer-dl 0.1.20 have stopped working today. 

get_iplayer --get 856 --verbose --modes=flashhd,flashaachigh,flashaacstd,flashaudio,flashhigh,flashstd,flashnormal,iphone,realaudio,flashaaclow returns:

No specified modes (flashhd,flashaachigh,flashaacstd,flashaudio,flashhigh,flashstd,flashnormal,realaudio,flashaaclow) available for this programme with version 'default'

Tried a number of programme ID's with the same result. The Beeb must have changed something. Working yesterday, dud today. This has happened before. Let's hope it's not a show stopping change this time.

---

### Post by neillmitchell on 2010-09-21
Hmm. It seems that some programmes download whilst others do not. About 30% of the ones I've tried are failing. I've posted to the aforementioned mailing list. Let's see if anyone has an idea about what is going on.

---

### Post by chome4 on 2010-09-21
> **matthewbpt said:**
> get_iplayer is still being actively developed by a different set of developers, check [http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html), for support send an email to their mailing list [http://lists.infradead.org/mailman/listinfo/get_iplayer](http://lists.infradead.org/mailman/listinfo/get_iplayer) queries usually get replies within a day and they're very helpful.

EDIT: The output sugests there isn't an iphone stream for that particular programme, which is the stream which is trying to be downloaded, I usually download the flashvhigh or flashhd stream, these need you to also use rtmpdump which can be downloaded and installed/compiled easily (google). Once you have that installed you would do

```
get_iplayer -g xxx --mode=flashvhigh --flvstreamer=/path/to/rtmpdump
```

That code worked perfectly. Thank you.

How do I incorporate that into a command that will launch Terminal and get me going to download? I tried:

gnome-terminal get_iplayer -g xxx --mode=flashvhigh --flvstreamer=/path/to/rtmpdump

But it did nothing apart from appear in the Applications menu.

---

### Post by nothingspecial on 2010-09-21
To open gnome-terminal and execute a command you need the -x option

```
gnome-terminal -x *command you want it to do*
```

---

### Post by chome4 on 2010-09-22
> **nothingspecial said:**
> To open gnome-terminal and execute a command you need the -x option

```
gnome-terminal -x *command you want it to do*
```

It launches terminal and Get_iplayer but after it starts, terminal disappears! I've rebooted the pc just in case but the same thing happens. Terminal on its own launches OK.

---

### Post by scouser73 on 2010-09-22
These are the codes I use for get_iplayer.

**Example:** [http://www.bbc.co.uk/iplayer/episode/](http://www.bbc.co.uk/iplayer/episode/)[COLOR="Red"]**b00tr6g1**[/COLOR]/Climbing_Great_Buildings_Durham_Cathedral/#

The code in red is the only bit of information you need to copy from the URL to the terminal

**1** - This command forces the download of a programme > get_iplayer --force it --pid=[COLOR="red"]b00tr6g1[/COLOR]

**2** - This command downloads the programme in standard flash > get_iplayer --type=tv --pid=[COLOR="red"]b00tr6g1[/COLOR] --modes=flashstd

**3** - This command downloads the programme in a more higher quality of flash > get_iplayer --type=tv --pid=[COLOR="red"]b00tr6g1[/COLOR] --modes=flashhigh

---

### Post by t0p on 2010-09-22
**scouser73:** where do you find those codes?

---

### Post by Old Marcus on 2010-09-22
In the url of whatever program you want to watch.

---

### Post by scouser73 on 2010-09-22
> **t0p said:**
> **scouser73:** where do you find those codes?

From this website: [http://linuxcentre.net/getiplayer/documentation](http://linuxcentre.net/getiplayer/documentation)

The person who maintained that site was the original get iplayer developer but now has discontinued it, hence someone taking over the reins.

The codes still work.

Oh you mean the code in red?  Well you need to go to the BBC iPlayer website, select a programme that you want to download and copy & paste the code, as shown in the screenshot.

---

### Post by t0p on 2010-09-22
> **scouser73 said:**
> Oh you mean the code in red?

Yeah, that's what I meant.  Thank you.

---

### Post by chome4 on 2010-09-22
All's well now. Downloading again!

Thanks to everyone....

---

### Post by neillmitchell on 2010-09-24
> **chome4 said:**
> All's well now. Downloading again!

Thanks to everyone....
Yes, working again for me. Looks like it was a temporary glitch Beeb side. Worry over :)

---

### Post by chome4 on 2010-09-28
mistaken posting...

---

### Post by dangerjunkie2002 on 2010-10-23
Hi,

With 2.66 from the repo and 2.78 I can get stardard def material fine:

[COLOR="Blue"]*get-iplayer masterchef -modes flashvhigh --get *[/COLOR]  works fine for me.

If I try to go for the HD experience with [COLOR="Blue"]*get-iplayer masterchef -modes flashhd --get *[/COLOR] the following happens:

[INDENT][I]INFO: Checking existence of default version
INFO: flashhd1,flashhd2 modes will be tried for version default
INFO: Trying flashhd1 mode to record tv: Masterchef: The Professionals: Series 3 - Episode 1
INFO: File name prefix = Masterchef_The_Professionals_Series_3_-_Episode_1_b00v3kb5_default                 
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/paul/Videos/Masterchef_The_Professionals_Series_3_-_Episode_1_b00v3kb5_default.partial.mp4.flv via RTMP
INFO: skipping flashhd1 mode
INFO: Trying flashhd2 mode to record tv: Masterchef: The Professionals: Series 3 - Episode 1
INFO: File name prefix = Masterchef_The_Professionals_Series_3_-_Episode_1_b00v3kb5_default                 
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/paul/Videos/Masterchef_The_Professionals_Series_3_-_Episode_1_b00v3kb5_default.partial.mp4.flv via RTMP
INFO: skipping flashhd2 mode
ERROR: Failed to record 'Masterchef: The Professionals: Series 3 - Episode 1 (b00v3kb5)'
[/I][/INDENT]

This is the first time I've used get_iplayer. Am I doing something wrong, have the BBC done something to break HD downloads or should I be using a different fork of get_iplayer please?

Thanks,
Paul.

---

### Post by MeKino on 2010-12-11
Hi

I'm having problems also...

But - I found that installing the latest version of flvstreamer did the trick.

---

### Post by tinfanide on 2011-05-22
It might be a stupid question to ask:

If I live outside the UK, does it still work for me?
Coz
I've tried typing the code in CMD (My OS is Windows XP) and all the time it returns like

"NFO: No specified modes (iphone) available for this programme with  version 'default' (try using  --modes=flashhigh,flashlow,flashstd,flashvhigh,n95_3   g,n95_wifi,subtitles)
ERROR: Failed to record..."

I've got the same problem as the thread starter did.
Do I needa set up the proxy?
If so, can TOR work with it?

Any help is appreciated!

---

### Post by speedwell68 on 2011-05-23
Might I suggest that instead of messing around with the command line with this you try Giplayer, the GUI frontend of get_iplayer.

[http://www.ubuntugeek.com/giplayer-a-python-gtk-wrapper-for-get_iplayer.html](http://www.ubuntugeek.com/giplayer-a-python-gtk-wrapper-for-get_iplayer.html)

---

### Post by tinfanide on 2011-05-23
> **speedwell68 said:**
> Might I suggest that instead of messing around with the command line with this you try Giplayer, the GUI frontend of get_iplayer.

[http://www.ubuntugeek.com/giplayer-a-python-gtk-wrapper-for-get_iplayer.html](http://www.ubuntugeek.com/giplayer-a-python-gtk-wrapper-for-get_iplayer.html)

Thanks for your reply.
But I cannot use it on my Windows OS. It seems it only works for the Linux OS.

---

