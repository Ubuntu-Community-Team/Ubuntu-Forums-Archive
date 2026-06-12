---
title: "LTSP client performance"
date: 2008-12-17
forum: Server Platforms
---

### Post by mk6032 on 2008-12-17
LTSP server installation went without a hitch using the 8.10 Alt. CD. The server I'm testing on is a 500MHz P3 with 384MB RAM, 500+ GB of drive space, 256mb PCI NVidia graphics, and two GB NICs. The test clients are a new AMD64 laptop and an old P4 desktop, all connected via a 5 port GbE switch. The clients boot, browse WWW, and perform regular day-to-day tasks at acceptable speeds. The only quirk is video output. I've tried watching a movie stored locally on the LTSP server, YouTube, Google Video, etc. They are all VERY choppy. Clients are configured to use the same server as a proxy to the 'net (configured with default settings--no filtering yet). Is there a way to increase the speed/smoothness of video output on the client?

Thanks in advance,
Matt

---

### Post by mk6032 on 2008-12-25
> **mk6032 said:**
> The server I'm testing on is a 500MHz P3 with 384MB RAM, 500+ GB of drive space, 256mb PCI NVidia graphics, and two GB NICs. The test clients are a new AMD64 laptop and an old P4 desktop, all connected via a 5 port GbE switch.

This is well within the recommendations: [http://wiki.ltsp.org/twiki/bin/view/Ltsp/ServerSizing](http://wiki.ltsp.org/twiki/bin/view/Ltsp/ServerSizing)

---

### Post by windependence on 2008-12-25
It may be within the recommendations but it certainly isn't optimal for what you are trying to do. First, you are severely memory starved for playing video. Second, your CPU is marginal at best for video.

Your video card is fine, and the two nics are fine, but make sure they are set to full duplex, and that they are actually running at GB speed. You may also want to look at nic teaming (trunking) as just because you have two nics doesn't mean you have twice the bandwidth. Your second nic might not even be up at boot. Do an ifconfig and find out.

-Tim

---

### Post by mk6032 on 2008-12-26
> **windependence said:**
> It may be within the recommendations but it certainly isn't optimal for what you are trying to do. First, you are severely memory starved for playing video. Second, your CPU is marginal at best for video.

Your video card is fine, and the two nics are fine, but make sure they are set to full duplex, and that they are actually running at GB speed. You may also want to look at nic teaming (trunking) as just because you have two nics doesn't mean you have twice the bandwidth. Your second nic might not even be up at boot. Do an ifconfig and find out.

-Tim

One is set to 192.168.0.0/24, the other is set to 192.168.1.0/24. Both are set full duplex and at 1000. The 0 network is the ltsp clients, the 1 network is my private lan. It's the default "Install LTSP server" setup.

Some additional info... the server is running two new IDE drives (both in udma5 mode) in a RAID0 config. Watching a video on the server itself is smooth... it's just the pxe client that is choppy. The multimedia is not stored on the LTSP but on a NAS drive--also connected via the same GbE switch. I know the server is old, but if I'm logged out and it's only ONE pxe client....

---

### Post by cariboo on 2008-12-26
I would suggest using iperf to check what your data transfer rates are. Iperf is available in the repositories. Run:

```
iperf -d 
```

on the server that is storing the media files, then on the client computer run:

```
iperf -c server
```

This will tell you what the data transfer rate is between the server and the client.

Jim

---

### Post by mk6032 on 2009-01-20
> **cariboo907 said:**
> I would suggest using iperf to check what your data transfer rates are. Iperf is available in the repositories. Run:

```
iperf -d 
```

on the server that is storing the media files, then on the client computer run:

```
iperf -c server
```

This will tell you what the data transfer rate is between the server and the client.

Jim

Sorry for the delay in response, I've been out of town a lot. Here's the iperf results:

------------------------------------------------------------
Client connecting to 192.168.0.1, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.24 port 38765 connected with 192.168.0.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    114 MBytes  95.4 Mbits/sec

---

### Post by mwdespi on 2009-02-28
Hi.

Sorry for reviving this thread.

I'm new to Ubuntu + LTSP, and I just finished a test setup with two thinclients connected to a server.

I have the same problem as "mk6032", only with a much more powerful server.

My server is a custom unit:
Intel Core i7 920 ES (21x133) 2.800GHz
Asus Rampage II Extreme X58 Motherboard
6GB (6x1GB) Kingston DDR3 @ 1333MHz
2x 640GB WD Caviar Black (RAID 0)
Palit Sonic ATI Radeon HD4870 512MB
2x Marvell Yukon Gigabit Ethernet

running Ubuntu 8.10 x86 (sorry, not x86-64) with the fglrx driver installed.

The thin clients are identical:
VIA C7-M @ 1Ghz
1GB DDR2 533
VIA CN700 + 8237R
100Mbps Ethernet
15" AOC LCD (1024x768)

They're connected via a Linksys SD216 100Mbps 16 port desktop switch.

So far they boot fast, all processing tasks complete quickly, but graphics performance (especially video and OpenGL) is abysmal. Video is choppy even at 480x320 (Youtube) or 640x480 (XVid).

I don't think it's the network. Using System Monitor to view network utilization on the server, I can only see around 4.3 to 5.0MiB/s going through eth1 while playing a video on one thin client. This is well below the ~10MiB/s capability of 100Mbps ethernet.

It's definitely not the processor, either - the CPU utilization hovers at around ~10% for one core and ~2.5% for the other 7 (4 physical + 4 virtual).

GLXGears gives absolutely abysmal performance. The gears almost do not turn at all.

Could you please help?

Thank you.

---

### Post by mk6032 on 2009-03-03
> **mwdespi said:**
> Hi.

Sorry for reviving this thread.



Don't be sorry for that! It's still an issue for me as well. If you find a solution other than this forum, please let me know or post it here.

Thanks,
Matt

---

### Post by yurtboy on 2009-03-07
Same here.
Slow video to not usefull.
Tried two different thin clients both with decent specs.

I ran the network tests the 1st was wireless the second wired
[  4] local 192.168.0.99 port 5001 connected with 192.168.0.109 port 57499
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.3 sec  18.2 MBytes  14.8 Mbits/sec
[  5] local 192.168.0.99 port 5001 connected with 192.168.0.24 port 46723
[  5]  0.0-10.3 sec    115 MBytes  93.9 Mbits/sec


Well if there are any thoughts on how to make video better.
Mythubuntu even has a ltsp install path so I figure it must be doable.

---

### Post by PsyberS on 2009-03-31
Same problem here.  Added LTSP to an existing Ubuntu 8.10 server, everything seems fine except any type of motion (videos in Totem and FF/YouTube, animations in Compiz if its enabled, etc) seems choppy.

I can use these things directly on the server without a problem or on a live cd on the clients without a problem.  I don't think its a hardware issue.

100mbps network with only the server and 1 client (at a time) on it, and the router is showing about 800kbps usage max so I'm doubting its a bandwidth issue either.

If I find anything I'll be sure to post here.

---

### Post by yurtboy on 2009-03-31
I turned off ssh with ldm so the clients communications are not secure.
It is in the lts.conf.
(LDM_DIRECTX=True)
But still not that great.
Movies are choppy

---

### Post by cornflake000 on 2009-05-03
Has anyone found any answers to this ltsp client video problem yet?  I have had the same problems with slow, choppy video performance on clients and have very fine machines as some of you do.  On the server, no problems at all. I have had this problem with intrepid but it's much worse in jaunty.

I'm just fishing!

thanks

---

### Post by mk6032 on 2009-05-17
> **cornflake000 said:**
> Has anyone found any answers to this ltsp client video problem yet?  I have had the same problems with slow, choppy video performance on clients and have very fine machines as some of you do.  On the server, no problems at all. I have had this problem with intrepid but it's much worse in jaunty.

I'm just fishing!

thanks

I was curious about how Jaunty would perform. Was it just choppy video or performance overall? Did you perform a clean install or an upgrade?

---

### Post by cornflake000 on 2009-05-17
I am using jaunty.  The problem for me is playing video of any kind.  All other network and non-network activity are fast and flawless. It's a clean install.

---

### Post by r5r on 2009-06-24
I have Jaunty on AMD Athlon 64 (2 GHz) server with 1 GB memory and client with Geode 500 MHz, connected on 100 mbit. 
Anything is like slideshow, except terminal window on clean desktop (CPU usage under 20%). I believe this has nothing with a physical network performance, but probably some limitations on serverside. I ran iptraf and there were no more than 500kbit bandwidth when I was doing all sorts on client.

---

### Post by mk6032 on 2009-07-07
Reported this to launchpad: [https://bugs.launchpad.net/ubuntu/+bug/396676](https://bugs.launchpad.net/ubuntu/+bug/396676)

---

### Post by windfix on 2009-07-17
We have put in a new thin client lab at our university with 9.04 server on a very powerful box (8 cpus and 16 GIG RAM) - same problem with video.  

Tested via a benchmarking utility called 'glxgears' to give an idea of the video performance. Same laptops gave this:

LiveCD:        1000 frames/sec
LTSP Client:    70 frames/sec

---

### Post by sbalneav on 2009-10-08
Hello, LTSP developer here.

Keep in mind 2 things:

1) Video or Multimedia performance on a thin client is NEVER going to be as good as on a local box.  When you view a video, with the session running on the server, you're sending *every single frame* over the wire.

2) As well, these bugs are being filed against LTSP, which really, isn't the correct place for them.  LTSP simply uses Xorg.  You'll find you have the exact same issues if you try to do remote X between 2 full workstations.

That having been said, there's some things you can do to help the situation.

1) First and foremost, as has already been stated, if you're wanting multimedia, you're going to want to make sure you have LDM_DIRECTX=True in your lts.conf file.  This will eliminate the ssh encryption, which will add latency on both the server and client.
2) Avoid using Flash where possible.  Flash doesn't seem to work very well over remote connections.  If possible, use the HQtube plugin for greasemonkey, at  [http://userscripts.org/scripts/show/24999](http://userscripts.org/scripts/show/24999).  This uses the gstreamer stack, which appears to work MUCH better over remote connections.
3) Run Firefox, Flash and your movie player as localapps on LTSP, if your workstation machine is fast enough.  This means that they now run on the local thin client, as opposed to on the remote server.

Hope this helps,
Scott

---

### Post by caustic386 on 2009-10-08
> **sbalneav said:**
> Hello, LTSP developer here.


3) Run Firefox, Flash and your movie player as localapps on LTSP, if your workstation machine is fast enough.  This means that they now run on the local thin client, as opposed to on the remote server.

Hope this helps,
Scott


I've never tried LTSP before, but I'm very familiar with Windows based VDI implementations.  It sounds like you're describing a streamed disk image to the client, with published apps on the desktop?  I didn't think Ubuntu had any disk streaming technology available?  Or am I completely understanding this whole thing wrong?

---

### Post by mk6032 on 2009-10-08
> **sbalneav said:**
> Hello, LTSP developer here.

1) Video or Multimedia performance on a thin client is NEVER going to be as good as on a local box.  When you view a video, with the session running on the server, you're sending *every single frame* over the wire.



Thanks for the help and information Scott. I'm a little confused by this statement. How are things like LinuxMCE able to work so well with thin clients? Is it because of the locally running apps, as you described below?

> 

3) Run Firefox, Flash and your movie player as localapps on LTSP, if your workstation machine is fast enough.  This means that they now run on the local thin client, as opposed to on the remote server.



Can you give a hint as to where this is configured? Thanks again for your time.

---

### Post by AlexanderDGreat on 2009-10-11
Hello Scott, thanks for ALL those information! Forgive me I'm just a newbie, but I've successfully thin cliented an Intel Atom Box. 

1. Where is the lts.conf located or where do I configure LDM_DirectX = True? I can't find the lts.conf file on my machine, do I have to create it?

2. How do you run Firefox, Flash, and Movie Player locally on the thin clients?

Once again, thanks.

---

### Post by epsolon77 on 2009-10-12
I have no idea how to run an app locally using LTSP, so information on that would be very helpful.

Your lts.conf file is located in //opt/ltsp/i386/etc/.  The file says something about an alternate directory at //var/lib/tftpboot/ltsp/i386/ but I can not find a conf file there.  If you make the change to //opt/ltsp/i386/etc/lts.conf you must run ltsp-update-image for this new lts.conf file to be used.

sbalneav--thank you for the response.  I'm looking forward to finding out how to run apps locally.

---

### Post by PsyberS on 2009-10-12
> **sbalneav said:**
> Hello, LTSP developer here.
1) Video or Multimedia performance on a thin client is NEVER going to be as good as on a local box.  When you view a video, with the session running on the server, you're sending *every single frame* over the wire.

Thanks for the reply Scott.  I am a bit confused on this however.

Most video plays at (around) 30fps.  As I have said (on the bug report, maybe here too I forget) this is not an issue with bandwidth, as I can play the video and monitor to see its using < 1mbps on my 100mbps network (with **no** other clients).  

I just checked the latency on that network and it is 0.1ms.   So at 30fps, the latency would be something like 6ms (accounting for acks), which is not observable!  This problem isnt making sense!

**Of course** we can run things locally, but that totally defeats the purpose of LTSP!  I gave up entirely and now just run 100% local using an exported NFS root, but I would really have loved to get LTSP working.

---

### Post by epsolon77 on 2009-10-13
> **PsyberS said:**
> Thanks for the reply Scott.  I am a bit confused on this however.

Most video plays at (around) 30fps.  As I have said (on the bug report, maybe here too I forget) this is not an issue with bandwidth, as I can play the video and monitor to see its using < 1mbps on my 100mbps network (with **no** other clients).  

I just checked the latency on that network and it is 0.1ms.   So at 30fps, the latency would be something like 6ms (accounting for acks), which is not observable!  This problem isnt making sense!

**Of course** we can run things locally, but that totally defeats the purpose of LTSP!  I gave up entirely and now just run 100% local using an exported NFS root, but I would really have loved to get LTSP working.

The problem with running an LTSP type system using video is that your display is not actually being created locally.  The server might be able to create the display at 30FPS, but your local screen doesn't actually update at 30fps because of the remote feature to any terminal server.  The problem is with the remote link software, whatever it may be, and how it compresses and sends the video.  A great example is to set up an RDP server, a VNC server and a FreeNX server and view the same video being streamed through all three.  You will see that the coppyness is very different because of how often they check for screen changes and how they compress and send the video.  The best I have used so far is FreeNX, but that does not incorporate with LTSP as far as your boot is concerned.

---

### Post by epsolon77 on 2009-10-13
I just tested running firefox and JAVA as local apps on 9.04 and video on HULU which was choppy before was silky smooth.  Remember that this does not run EVERYTHING local, only selected programs. It took a bit to get the local apps setup correctly, but was well worth it.

[https://help.ubuntu.com/community/Ub...ocalAppsJaunty](https://help.ubuntu.com/community/Ub...ocalAppsJaunty)

Thank you to AlexanderDGreat for his research and finding me the link above.

---

### Post by tjh_ltsp on 2010-01-26
Hi I am trying to experience the limits of video streaming over 100Mps LAN.

Here is what I did. Server = AMD ATHLON X2 3800+ and thin client = thinkpad T40 laptop; connected via 100Mbps lan.

I installed locally on the thin-client: xbmc, vlc, firefox, mplayer after finding out that non locally installed video players lead to very choppy video performance.

The following to configurations seem to lead to smooth video performance (NOT h264 encoded!):
1) ltsp local mplayer playing nfs mounted video files from the server
2) using mediatomb on the server and vlc on the client via upnp

However for h.264 video both approaches are not good -> choppy video.
Therefore I tried a third. On the fly transcoding to mpeg2 with mediatomb with ffmpeg. This improves video streaming performance, but leads to 99% singe CPU usage on the server and 99% CPU usage on the thin client.

Question: How can I further improve the h.264 video streaming experience in a thin client cluster using ubuntu 9.10 ? Would a gigabyte LAN help?
**Please advice.**

---

### Post by HighCommander540 on 2010-01-26
> **epsolon77 said:**
> The problem with running an LTSP type system using video is that your display is not actually being created locally.  The server might be able to create the display at 30FPS, but your local screen doesn't actually update at 30fps because of the remote feature to any terminal server.  The problem is with the remote link software, whatever it may be, and how it compresses and sends the video.  A great example is to set up an RDP server, a VNC server and a FreeNX server and view the same video being streamed through all three.  You will see that the coppyness is very different because of how often they check for screen changes and how they compress and send the video.  The best I have used so far is FreeNX, but that does not incorporate with LTSP as far as your boot is concerned.

Ok, well if this is really how it works. Then the bastards at LTSP need to fix it. Or stop using x.org if that is the problem. Because honestly. This shouldn't be a problem.

---

### Post by epsolon77 on 2010-01-26
> **HighCommander540 said:**
> Ok, well if this is really how it works. Then the bastards at LTSP need to fix it. Or stop using x.org if that is the problem. Because honestly. This shouldn't be a problem.

I disagree.  I am not sure how you are expecting an LTSP setup to work.  The majority of the work is done server side, which means it is rendered server side.  Then the graphics data needs to be transmitted over 8 little copper wires using TCP/IP.  Using TCP/IP for the transport causes all sorts of issues with packets being delayed, not showing up on a consistent time spacing, or being lost and re requested.  Because of this flexibility in TCP/IP running a display across this protocol is difficult.  Just the fact that you can seamlessly run some tasks local and others server side is a great step forward.  I would challenge you to come up with a better scheme to accomplish the end goals of terminal servers.

---

### Post by tjh_ltsp on 2010-01-27
Any comments on my questions?

---

### Post by epsolon77 on 2010-01-27
> **tjh_ltsp said:**
> Any comments on my questions?

I am sorry about not addressing your question.  I seem to be very distracted lately...

I am a little confused on why you are using LTSP to stream media to a thin client. I do not believe a gige lan will help any.  What is the size and resolution of the video you are trying to play?  Where are you playing it from (What is the source)?  Why are you trying to force the h.264 codec in a stream.  If the source is on the server, just play via the share?  I am sorry that I don't understand exactly what you are shooting for here.  I still have newb moments.

---

### Post by jaxxed on 2010-11-06
> **epsolon77 said:**
> Then the graphics data needs to be transmitted over 8 little copper wires using TCP/IP.

Even worse, it only uses four of those eight wires, the others are not used or are used for PoE.

---

### Post by theller on 2010-12-02
Have you tried connecting the thin clients using NoMachine <http://www.nomachine.com/download-package.php?Prod_Id=2249>. I have 25 thin clients running on a Dell Optiplex 755 and the video runs smooth on all 25 at once. I just can't get the sound working.

---

### Post by Loctrice on 2011-03-31
I'm just getting my home network up and running with thin clients. I got the clients to boot, and switched to running firefox as a local app. Of coarse I got caught up with the nat. I went through all the online walkthroughs I could find, I think networking is a little over my head sometimes. 

I installed squid and got it configured as a solution for the thin clients. It worked great! Hulu (which I forgot to state is my end goal for the users) starts up and runs without a problem ... at first... The ads play normall, imagine that, but then it stops while trying to load the movie/show. I'm not sure why it does that, and I'm out of ideas.

As a side note, chrome running normally instead of a local app will play hulu on the clients except you can't full screen it or you suffer the video lag mentioned before.

Any ideas?

---

### Post by pmwangi80ke on 2012-03-30
> **theller said:**
> Have you tried connecting the thin clients using NoMachine <http://www.nomachine.com/download-package.php?Prod_Id=2249>. I have 25 thin clients running on a Dell Optiplex 755 and the video runs smooth on all 25 at once. I just can't get the sound working.


Hello,
is there a how to you can recommend to a newbie like me. I have a thin client setup on Ubuntu 10.10 server which works pretty well apart from the choppy video streaming. 

Best regards..
peter

---

### Post by epsolon77 on 2012-03-30
The company I work for decided to go with a commercial Citrix product, so I have been away from the LTSP project for a while.  If it is working pretty well except for video, I would look into offloading video based programs to your thin clients processor, if the hardware will support it.  Best of luck to you!

---

### Post by headvampyre@hotmail.co.uk on 2012-04-01
For video playback - I would recommend using LTSP-LocalApps due to the significant reduction in strain on the server and network. 

Read this guide for information on setting these up (Personally, I'd recommend Java, all web browsers, media players & editors, and Flash, plus any resource heavy applications to run locally on the client):

[https://wiki.ubuntu.com/LTSPLocalAppSetup](https://wiki.ubuntu.com/LTSPLocalAppSetup)

---

### Post by martinwguy on 2012-08-06
I guses this is because the video is decompressed on the server and sent over the network entire frame by entire frame.
A rough calculation: 1280x1024 pixels x 4bytes per pixel x 25 frames per second = 120MB/second per terminal, outside what even gigabit ethernet can support with just one terminal.

   M

---

