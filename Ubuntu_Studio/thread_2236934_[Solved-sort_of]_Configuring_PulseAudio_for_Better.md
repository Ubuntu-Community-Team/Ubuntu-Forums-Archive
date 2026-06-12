---
title: "[Solved-sort of] Configuring PulseAudio for Better Audio PlayBack"
date: 2014-07-29
forum: Ubuntu Studio
---

### Post by Nistegmos on 2014-07-29
OK, so I use Ubuntu Studio v14.04 LTS on a HP dc5800 Core2Duo desktop computer with 4 GB RAM.  The hard drive is a 7200 RPM SeaGate and the computer is NOT connected to the internet.  This post is the good news that the audio CAN be configured to be workable for MIDI and 44.1 kHz 32-bit float audio mulititrack mixing.  I use Ext3 as the filesystem, so it's possible that Ext2 users not using encryption might get better speeds at the cost of less filesystem reliability due to the lack of journaling in Ext2.  

I primarily use REAPER v471 installed running on Wine v162, which comes with Ubuntu Studio.  

The game changing optimizations were as follows:  

*Using gParted to recreate the swap partition as just a simple logical partition, not a logical partition inside of an extended partition as the installer does.  
This does require editing the fstab file a bit to make sure that the UUID matches, but that's also needed for the next option:  

*Setting the filesystem mode to noatime (disables file access time logging). 
[http://wiki.linuxaudio.org/wiki/system_configuration](http://wiki.linuxaudio.org/wiki/system_configuration)

The LinuxAudio wiki site has advice on how to fix IRQ conflicts and how to disable the CPU "ondemand" setting in favor of "performance" instead.  
There are several other optimizations posted there as well, and not all of them are necessary.  Thankfully, the more difficult ones are probably not needed by most people.  

*Installing WineASIO; I installed this from a KXstudio Debian archive, but it turns out that I really didn't need it since I don't use JACK most of the time.  But this is still very much worth mentioning because JACK does seem to be capable of better latency than PulseAudio.  On my system, WineASIO created some instability though, so I still don't use it.  

*Learning the playback, buffering, and default preferences settings within Reaper v472.  This required a bit of experimentation, and I still don't know all of them.  But a few of them are supposed to be changed from the defaults if you use Wine.  Sorry, that I don't have my DAW handy to explain which ones.  But the [http://forums.Cockos.com](http://forums.Cockos.com) website would possibly have the answers.  I do remember that my best stable results came from choosing WASAPI instead of WavOut or whatnot.  It seems that Reaper has problems if any of the buffer sizes are either too high or too low.  Also the CPU and process prioritizing types of tweaks also seem to suffer if set too high or too low.  

I will eventually try and make screenshots of my exact settings so that this can be demystified for myself and others.  

*I think it's worth mentioning that the harddrive was upgraded to a modern drive even though the old hard drive was probably also a 7200 RPM drive.  Modern drives usually have better caching of data than old drives.  Also, most laptops still usually have slower (5400 RPM) drives, so if you are on a laptop, you will need to contend with that first and take it into consideration when choosing a filesystem.  If you need to copy data between partitions, you can use a LiveCD of gParted.  But be warned that copying and pasting partitions requires attention to detail and usually means writing down UUID numbers of partitions or getting new UUID's in gParted so that you don't create confusion to the operating system.  Also, you will need to know how to use a GRUB installer/editor of some sort, preferably on a LiveCD so that you will be able to boot up/start up your system no matter what.  

*Editing /ETC/Pulse/ daemon.conf and default.pa for better compatibility with my soundcard and using a faster sample rate conversion setting.  This is not easy to explain.  This is best referred to other sites and other people.  But it's worth carefully doing because this is where PulseAudio can be cleaned up to work more smoothly.  In my configuration, i did add the tsched=0 setting in the default.pa file but I made different buffer settings than were recommended by a website that introduced me to the concepts.  It turns out that the default sample rate conversion setting is actually probably the best for lower CPU, but it might not sound as good as some other options.  

I can't yet seem to find the webpage that I was reading, and this one may not be entirely appropriate, since it's for Jaunty instead of Trusty Tahr, but here it is anyhow:  
[http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html)

Here is the website that introduced the concept to me, but be sure to read the entire page, including the comments at the end.  The commenters make some corrections to the procedures and insightful comments about why the settings may or may not be appropriate.  I did not end up using this page's tweaks exactly as described, but it was a starting point:  

[http://www.techrepublic.com/blog/linux-and-open-source/pulseaudio-an-achilles-heel-that-needs-repair/](http://www.techrepublic.com/blog/linux-and-open-source/pulseaudio-an-achilles-heel-that-needs-repair/)

Some people who did actual benchmark tests on the settings showed that the "trivial" setting isn't actually faster, though it's low on CPU burden.  I do remember enabling the alternative sample rate to what my USB soundcard can handle (48 kHz).  If I remember correctly, I set the buffer to something smaller than was there before since Reaper has it's own buffer settings as well and WASAPI does too.  I mathematically tried to get the sum total of latency of my computer to be closer to around 20 msec (milliseconds) or less since 20 is the perceptual maximum of delay that goes unnoticed by human hearing.  

Sorry I can't yet be more specific about these things.  But I will try to add more info as I go along and especially as I near completion.  I'm already mostly done.  Really the only thing left for me to do on my system is to see if I can boost the settings from 44.1 kHz sampling rate up to 48 kHz sampling rate for slightly better quality.  

I apologize that this is just a rough sketch and not as specific as I would like.  But hopefully this will be a sign of encouragement for others and maybe provide some useful hints.  
There is some info that I received as well as posted on [http://IDMforums.com](http://IDMforums.com) and [http://forums.cockos.com](http://forums.cockos.com) as user "Nystagmus" on both sites.  

good luck.  

EDIT:  I added a few more links.

EDIT:  I recently found out that disabling "anticipative FX processing" within Reaper's preferences also improves playback response.  Apparently, the function only works for Reaper plugins and similar, but is a disadvantage for most third party regular VST's.  So if you totally disable "anticipative FX processing" you will probably get back a more usable latency, better visual GUI sync, and more stability.

---

