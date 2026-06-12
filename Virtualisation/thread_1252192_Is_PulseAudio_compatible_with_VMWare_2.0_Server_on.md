---
title: "Is PulseAudio compatible with VMWare 2.0 Server on Ubuntu 8.10 64-bit?"
date: 2009-08-28
forum: Virtualisation
---

### Post by sunbear on 2009-08-28
I have finally been able to get sound working within VMWare Server 2.0 on Ubuntu 8.10 64-bit host running a Windows XP SP2 guest, however I have to kill pulseaudio in order to achieve this.

It seems that many many people have been struggling with sound in Ubuntu. I personally have spent over 50 hours trying so get a working vmware server sound configuration, so I can only imagine the thousands of man hours that have been spent throughout the community. I'm putting together this post to capture the posts that helped me to get to the "almost-working" stage to help save the time of others and also in the hope that with some additional discoveries from others we can get VMWare Server 2.0 properly working on Ubuntu.

The recommendation of last resort (but the only one I haven't tried yet since I am reluctant to remove a core component of Ubuntu and potentially give myself problems with future updates) is to find a way of more permanently uninstalling and disabling PulseAudio
1) [http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
or
[http://ubuntuforums.org/showthread.php?t=973637&highlight=padsp+vmware](http://ubuntuforums.org/showthread.php?t=973637&highlight=padsp+vmware)
or
[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

and then make use of the aoss wrapper (which I have tried with success but without uninstalling PulseAudio)
2) [http://ubuntuforums.org/showthread.php?t=331175&highlight=libaoss.so+exec](http://ubuntuforums.org/showthread.php?t=331175&highlight=libaoss.so+exec)
or
[https://bugs.launchpad.net/ubuntu/+bug/81742](https://bugs.launchpad.net/ubuntu/+bug/81742)

It seems that many existing applications (VMWare Server included) access audio through /dev/dsp. One would think that when introducing a new sound API like ALSA and PulseAudio, developers would incorporate some backwards compatibility with the previous sound APIs so that applications like VMWare would continue to function. If that backwards compatibility exists, we could really use some pointers as to how to engage it with PulseAudio (any PulseAudio experts out there?)!

After my last battle with PulseAudio at the end of 2008, I actually had sound working in VMWare for 6 months, but I updated my Ubuntu installation last week and lost sound and keyboard mappings all over again. Very frustrating. I got the following error message when I start VMWare:
> "Failed to open sound device /dev/dsp: **Device or resource busy** Virtual device sound will start disconnected. "

My guess is that the update somehow re-exerted (the evil?) PulseAudio's control over my system and that PulseAudio is for some reason preventing any other program from accessing the sound device. I have found a workaround - if I used method 2 above, then type
>  sudo killall pulseaudio

This then frees up /dev/dsp and VMWare launches perfectly (with sound). Unfortunately it also now means that there is no more sound in any of my Linux Host machine's applications (firefox, etc) until I reboot.

I thought perhaps I could try a similar strategy to Method 2) but instead of pre-loading libaoss.so I would pre-load the PulseAudio wrapper padsp along these lines:
[http://communities.vmware.com/thread/163605](http://communities.vmware.com/thread/163605)


This does not work and yields a slightly different error message from VMWare:
> "Failed to open sound device /dev/dsp: **Connection refused** Virtual device sound will start disconnected."

Note the slightly different error message from before (Connection refused). So it seems that PulseAudio is still blocking access to /dev/dsp for an unknown but different reason.

I'm hoping that people who read this thread may be able to improve on the workaround of killing PulseAudio. Can anyone suggest a solution that will allow PulseAudio and VMWare to coexist peacefully? VMWare is an extremely important application to have working on Ubuntu as a means of being able to run Windows applications for which there is no current Linux replacement. For example, Webex does not run at all under 64-bit Linux (not even using Wine - I've wasted another 50 hours on that too!). Please don't suggest VirtualBox - I'm sure that would lead to another 50 hours of investment just to switch over. Also, the fact that I can get sound through killing PulseAudio suggests to me that there should be a cleaner workable fix.

Thanks for any helpful suggestions. I've also submitted a bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420794](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420794)

---

