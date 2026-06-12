---
title: "Is it feasable to run Mythtv on Ubuntu Server 11.04"
date: 2011-08-04
forum: Server Platforms
---

### Post by grunge09 on 2011-08-04
I have 2 pc's ready to run each Mythtv and Ubuntu Server Separately, but SHOULD I run both off one PC?

Server1:
MD 965 3.4GHz Quad Core
4 GB Ram
1tb boot drive and 2x2tb Raid 1 
gigabit networking
Geforce 210 with HDMI out to 37" LCD
Hauppauge HVR-2250 Tuner Card with Windows MCE Remote

Server 2:
AMD 6000+ Dual core
1 GB RAM 
500GB HD
gigabit networking

I have Ubuntu Desktop 11.04 (classic gnome mode) and Mythtv running now on Server1.  

I have 3 PC's that I want to centralize their data to the machine above.  Been looking (and I may have overcomplicated it here) at Ubuntu Server and LDAP and Samba with roaming profiles.  

My question is SHOULD I run mythtv also on this SERVER1 box, or just have the 2nd SERVER2 box for the mythtv.  Oh forgot to mention that this box is connected to 37" LCD and used as master back end and front end for Mythtv.  

Would it slow the box down with ongoing 2 tuner recordings, and logging in across the network, working, streaming videos, playing music, etc. 

Has anyone tried this and how well does it work or not work?

---

### Post by cheryljosie on 2012-02-19
I am sorry that no one else responded to your question earlier, when you  were attempting to decide on a proper course. I did not see your post  earlier or I would have responded. I did not have as much info then but  at least I had some.

I am running one core2 duo desktop machine  with the 2250 and 4x1.5tb SATA 1.0 data storage in software raid5 under  ubuntu 11.10. I suspect my setup is severely underpowered compared to  yours, but probably comparable to your AMD dual core machine.

I  can simultaneously record both data streams from both tuners, and with  my pbs channels that means up to 6 programs simultaneously without  problems even with a slower encrypted raid5 setup and no special  processing registers for encryption in the cpu, not counting the kids  and spanish channels which would make 8 channels.

Anyway, it  seems that a dual core machine is adequate to capture all the output of a  2250 while simultaneously viewing at least one frontend and probably  has enough bandwidth to stream at least one more frontend worth of  programming to the network out its backend too, but you should be aware  that there may be a file format problem with the 2250.

See my post at this link: [http://ubuntuforums.org/showthread.php?t=1567490&page=11](http://ubuntuforums.org/showthread.php?t=1567490&page=11)  for details about the stream corruption and what it does to my attempts  to view or transcode them with applications outside of mythtv that do  not depend on mplayer, such as ffmpeg and handbrake and vlc. The 2250  tuner is relatively insensitive also, so plan on providing a very strong  signal to it from an 8-bay uhf bowtie array or something similar unless  you are using cable or are right next to the transmitting towers with  no multipath reflections.

When I try to use handbrake to  transcode a ripped dvd while ripping one of my DVD's simultaneously with  k3b or makemkv, especially if I am trying to play back video in mythtv  and especially high def playback, the recordings off the 2250 capture  output start dropping frames and their playback looks jerky due to all  the dropped frames during recording. Apparently mythtv will attempt to  keep recording the stream even with serious dropouts in disk or  processor bandwidth.

ota 1080i playback is dicey, so is 720p.  There are tears in the video. This machine does not have vdpau, it is a  geforce 7xxx graphics card with pciexpress 1.0 and not fast enough for  high def. It can barely handle mythtv playback in high def. You should  be aware that your AMD machine may have similar difficulty. I recommend  either looking into it carefully or at least upgrading it to quad core.  Dual core machines probably are limited to pciexpress 1.0 and that is  just not going to give you any options in video cards that will do high  def nicely. In fact, it means no Unity 3d support either, since  apparently there is not enough bandwidth for that, so even though the  card is technically capable of it no one bothers to put it into the  linux driver.

Another problem with this system is that it is not  fast enough to play back 1080p so blu-ray does not work on it, period.  The problem is related to the processor bandwidth and the video  interface, which is pciexpress 1.0. The core2 duo is an older processor.

You  should not experience these problems to the same degree on your quad  core and it should handle high def OK, but if you attempt to do too many  tasks all at once while capturing video off the 2250, I guarantee you  will drop frames in your recordings, especially if you run into a  bottleneck in the disk interface or the processor.

I am also  fairly certain that the only application besides mythtv that will  transcode or play your streamed recordings from the 2250 tuners is  mplayer/mencoder, since I have had no luck with other applications,  unless I am using recordings from the composite input and that is direct  frame buffer processed in an mpeg-2 hardware encoder on the 2250, not  captured as a stream from a tuner.

You might want to reconsider  the 2250 because of the level of linux development on the tuner, which  is now little to none as far as I can tell since it is basically working  even if the file format is subtly corrupted somehow. I have seen no  comprehensive comparison of PC tuners so probably the best thing is to  borrow captured video streams (recordings) from people with several  different tuners under Linux to find out if there is one that is both  sensitive to over-the-air signals and also standard-compliant in its  output format so that you know you will have no problem shrinking or  playing your archive of shows with other applications besides  mythtv/mencoder. I especially like handbrake and vlc and I am  disappointed that they do not work with ota captured on my 2250 mpeg-ts  output.

Then again, it might be mythtv and not the 2250 that is  responsible for my difficulties. I have no point for comparison. I only  recently started using linux and I have used no other tuner than the  2250. I do know that I had no difficulty transcoding or playing streams  captured under Windows with the WinTV application and firmware from  Hauppauge, even when I used handbrake and vlc under linux on them. I  have not figured out how to capture ota with other linux applications to  compare my results to what comes out of mythtv. But I digress..

Probably  the best strategy for you would be to put the backend and the 2250 and  your mass storage on your slower machine and let it handle the tuner  recordings and serve video without putting any other tasks on it. Then  you will know for sure that the only thing it is doing is capturing  broadcasts and serving video, which should not cause it any problems as  long as you are not serving a hotel-scaled television service with it  displaying high def movies in every room of your house simultaneously.

You  might even be able to use it as a frontend in your living room so that  you can watch your movies on the same machine that holds them, without  relying on network setup for your critical viewing. You might need a  separate solution for blu-ray since the AMD is probably not fast enough  for that.

This of course relies on that machine being fast enough  in the disk interface and processor to handle the bandwidth of all  these combined streaming tasks. I suspect it is, since mine seems to be,  and it is also a dual core.

That will leave you with all your  serious horsepower to do non-streaming tasks such as ripping,  downloading, editing, transcoding, internet browsing, simulating, etc.,  without ever having a situation where a sudden increase in load causes a  recording stream to start dropping frames, or a playback stream to  start glitching.

I know there must be other considerations. You  will need to figure those out before you finalize your decision. As far  as I know, no one seriously expects to store blu-ray recordings on a  computer at 50gig a pop, but you might want to store a transcoded,  downsized version? Then it might play just fine off your streaming  server. You will need all the horsepower you can get to chew that 1080p  down to size and probably should not do that on the same machine that is  capturing 1080i off your 2250.

My preference, if I had the  funding, would be to have one dedicated multimedia machine for  capturing, storing, and serving video, that is fast enough to handle  high-def, and one dedicated high-powered machine for processing (editing  or transcoding) video and extreme gaming and doing normal desktop  computing. That way I would know that my interactive use of my computer  would never corrupt a recording or playback in progress.

In other  words, I would treat one computer as a dedicated television appliance  with moderate processing and video bandwidth and most of my storage on  it and a more or less consistent streaming load to avoid bandwidth  bottlenecks, and offload all data-intensive tasks to the other,  high-performance system.

Then when it comes time to upgrade  again, I would swap tasks and use the current powerhouse as the next  dedicated moderate multimedia machine, taking advantage of its blu-ray  playback capability too, with the older one becoming a stripped-down  simple frontend tv/video player in a spare bedroom, for the children to  do their homework on?

Anyway, I hope someone finds some value in my rambling, late response.

---

