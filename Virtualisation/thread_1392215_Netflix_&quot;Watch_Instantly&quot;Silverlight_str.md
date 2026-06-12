---
title: "Netflix &quot;Watch Instantly&quot;/Silverlight streaming - Win7 VirtualBox"
date: 2010-01-27
forum: Virtualisation
---

### Post by clconway on 2010-01-27
I am running Windows 7 as a guest in a VirtualBox on a Ubuntu 9.10 host, primarily for the purpose of using Netflix "Watch Instantly." I have the sound card and network working and get decent performance out of local and Flash videos (e.g., I can watch Hulu without any significant problems*). Unfortunately, Silverlight video (which Netflix uses) doesn't work well at all. The sound breaks up and skips on high frequencies. On the [IIS "Smooth Streaming" demo]("http://www.iis.net/media/experiencesmoothstreaming") (which might be a bad example, since it might rely on 3D acceleration?), I get a frame rate of 5-12 fps and a consistently low bit rate of 350 kbps despite speedtest.net scores of 2-5 Mbps both in the guest and the host. Netflix movies are unwatchable, both in terms of frame rate and audio quality.

I have no idea if the problem here is VirtualBox, Silverlight, the drivers, or my network connection. Any tips on how to isolate this and get it fixed?

Details:

Host:
OS: Ubuntu 9.10 (32-bit)
RAM: 4 GB
GPU: NVIDIA GeForce 8200
Sound: Intel ICH9

Guest:
OS: Windows 7 (64-bit)
RAM: 1 GB

Network:
Attached To: NAT
Adapter Type: Intel PRO/1000 MT Desktop

Video Memory: 32MB

Audio:
Host Driver: ALSA Audio Driver
Controller: ICH AC97
Driver: Realtek v6.0.1.6305

* There is one somewhat significant problem with Hulu/Flash: Going fullscreen doesn't seem to work. Fullscreen basically freezes the image (while the audio continues) until I hit Esc. Any tips?

---

### Post by zami on 2010-01-28
I was trying to get Netflix, in Vista, in VirtualBox going a while ago.  I got it working (no setup fuss even) but it was unwatchably choppy.  But others reported more positive experiences.  Maybe some of their setup info will help you troubleshoot?

[http://ubuntuforums.org/showthread.php?t=736400](http://ubuntuforums.org/showthread.php?t=736400)

Be warned - I don't remember now if I was trying different virtual setups, or just changing the settings on the same virtual "disk", but whatever I was doing it was registering with Netflix as me logging in from different computers/locations after every change.  And, Netflix only allows something like five log-in locations per account, per year.  So try and get your virtual setup exactly how you want it, before testing Netflix.  (Which it sounds like you are doing already with the Silverlight test, but I wanted to throw that warning out.)

You'll notice my machine was not 1/4 as burly as yours, and I was running Vista which is a resource glutton... 7 seems a much better candidate for this setup.  

One more thing - did you try enabling/disabling the 3D and 2D acceleration?  Those options are somewhere under the Display settings.  (I've got VirtualBox, the closed source version from the website, version 3.1.2).

Good luck!

-zami

---

### Post by bedhead75 on 2010-01-28
While running an Intel Q6600 CPU and Nvidia 9800GT GPU, watching Netflix in 64-bit Windows 7 guest and Ubuntu 9.10 64-bit host still led to choppy sound quality, but decent video play back (maybe slightly more choppy than running Windows 7 natively).  The choppy sound issue for me is resolved when I watch Netflix in Virtualbox with Windows XP 64-bit as guest instead.  The video playback is still just a bit choppy, but it's certainly watchable.  I have 2D acceleration already turned on in Virtualbox.
    The only annoying problem is that sometimes the video stream freezes up even though there is buffered content remaining.  It's like the Silverlight application "loses track" and I have to reload the page in order to resume playback.  This might be a Silverlight problem and not Virtualbox.

---

### Post by clconway on 2010-01-28
> **bedhead75 said:**
> While running an Intel Q6600 CPU and Nvidia 9800GT GPU, watching Netflix in 64-bit Windows 7 guest and Ubuntu 9.10 64-bit host still led to choppy sound quality, but decent video play back (maybe slightly more choppy than running Windows 7 natively).

This sounds like exactly what I'm seeing. I'm going to have to dig out an XP disc and see if it works there.

---

### Post by clconway on 2010-01-28
> **zami said:**
> 
One more thing - did you try enabling/disabling the 3D and 2D acceleration?  Those options are somewhere under the Display settings.  (I've got VirtualBox, the closed source version from the website, version 3.1.2).

I actually haven't tried this, but it seems like a good idea. I don't think 3D acceleration is even supported in Win7 guests. In your tests, did you every see video performance getting *better* when you turned off acceleration?

---

### Post by clconway on 2010-01-31
I just set up a Windows XP guest. With 2D/3D acceleration enabled and 2 CPUs, I get sustained frame rates of 30+ fps on the Smooth Streaming demo, although with very low bit rates. On Netflix, the sound is fine and the video resolution is fine, but the video frame rate is very low (looks like 10-15 fps). Speedtest.net reports a download speed of 1.44 Mbps... I have no idea if this is sufficient for good Netflix streaming, but it's about as good as I can expect on my cable modem.

---

### Post by redcharlie on 2010-06-24
I had issues with choppy netflix playback with a 32bit Jaunty host/ 32bit XP guest until I changed from pulseaudio to OSS.

[http://ubuntuforums.org/showpost.php?p=9506867&postcount=6](http://ubuntuforums.org/showpost.php?p=9506867&postcount=6)

---

### Post by clconway on 2010-06-25
I use ALSA for sound. I actually can't get sound working with the OSS driver at all... I tried using the null driver to see if the frame rates improved, but it doesn't seem to have worked.

---

