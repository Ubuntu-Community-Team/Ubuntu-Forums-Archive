---
title: "Running Mixx Under JACK"
date: 2010-02-22
forum: Ubuntu Studio
---

### Post by 4String_Gal on 2010-02-22
Hi All,

I just installed Ubuntu Studio 9.10 and wanted to try Mixx, mainly for the BPM feature. I have a firewire sound card and use FFADO through JACK. I started JACK and then started Mixx, which is what the manual said to do to use JACK. But there is no option in the preferences panel to use JACK, just Alsa or OSS.

Any suggestions?

Thanks!

---

### Post by AutoStatic on 2010-02-23
Mixxx uses the PortAudio library to 'talk' to JACK. So if JACK started correctly and you fire up Mixxx you should be able to select PortAudio as the Audio Output.

---

### Post by Stochastic on 2010-02-24
> **AutoStatic said:**
> Mixxx uses the PortAudio library to 'talk' to JACK. So if JACK started correctly and you fire up Mixxx you should be able to select PortAudio as the Audio Output.

This is true, however it does not apply to the default packages of Ubuntu 9.10 and earlier as PortAudio was not built with Jack support until a few days ago (i.e. in the upcomming 10.04 release).  Here's the bug that describes the problem: [Bug #360590 on Launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/portaudio/+bug/360590")

I'm not recommending running or upgrading to the development release.  If this is a major feature for you, then you should probably look forward to 10.04 Lucid Lynx in April.

For now, it's possible to get this setup working, but you'll need to recompile PortAudio with the libjack-dev header libraries installed on your system.  There are also some PPA repositories currently offering PortAudio versions for Ubuntu 9.10 (maybe earlier) that have been compiled with Jack support (this would be the easiest solution for now).

Once you have PortAudio built with Jack support, then AutoStatic's description is correct.

---

### Post by 4String_Gal on 2010-03-06
Thanks to both of you, and sorry for not replying sooner.

The BPM feature is something I'd like, mainly for learning new songs. April isn't that far off, so I think I'll wait. Figuring out that feature in Ardour is what I'd really like to do, but I'm not getting it at all. And I haven't taken the time to really figure it out, I've only been using the most basic features of that program. My to do list is just too big:(

I do hope that anything under the "audio production" menu will work with JACK for the next release. But, in general, I'm very pleased with Ubuntu Studio. 

Cheers!

-Susan

---

