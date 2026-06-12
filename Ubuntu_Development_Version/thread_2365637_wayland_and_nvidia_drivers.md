---
title: "wayland and nvidia drivers"
date: 2017-07-08
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2017-07-08
Hello 

i haven't installed the nvidia drivers as they didn't work together has this changed it. 

thanks

---

### Post by #&amp;thj^% on 2017-07-08
I guess this would depend on what/with you were using it for.
For a wayland session no nvidia drivers work,... **"prime-select intel"** dose.
For a regular X11 session they work great for me.
```
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 381.22

```
I'm probably falling short on a good answer for you...but the question is a bit vague.:)
Regards

---

### Post by terry_gardener on 2017-07-08
> **1fallen said:**
> I guess this would depend on what/with you were using it for.
For a wayland session no nvidia drivers work,... **"prime-select intel"** dose.


Thanks you this answered the question.
i won't install the nvidia drivers then and stick to the open source one. 
i have the nvidia gtx 960

---

### Post by mc4man on 2017-07-08
gnome-wayland would use EGLStreams, ect. It's not functional in Ubuntu & probably not great elsewhere - 
[https://bugzilla.gnome.org/show_bug.cgi?id=773629](https://bugzilla.gnome.org/show_bug.cgi?id=773629)
xorg-server currently works fine & will continue to do so.

---

### Post by VMC on 2017-07-09
I couldn't get nvidia drivers to work on ubuntu-gnome. Installed, but was in the proverbial login loop. Ironically, it work on debian install. Xorg on both. Using legacy-nvidia.

---

### Post by mc4man on 2017-07-09
If you read this it seems to indicate that wayland/nvidia would work with KMS (nvidia), enabled
[https://trello.com/c/7jWI9yjo/136-make-a-decision-about-wayland](https://trello.com/c/7jWI9yjo/136-make-a-decision-about-wayland)

That leads to this - 
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1697882](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1697882)
What I see is X11 (xorg-xserver) works just fine with KMS enabled in gdm/gnome-shell but gnome-wayland session doesn't start when KMS is enabled for nvidia

So in other words I don't know nothing (except xorg-xserver is working fine here & I get Prime Synchronization with xserver, i.e., no tearing with nvidia drivers on a hybrid (optimus) machine.

---

### Post by #&amp;thj^% on 2017-07-10
I have tried until I'm blue in the face with KMS and modeset...with no success. :(
But i do have the luxury of also having a Intel Gpu to switch to. (Works pretty good for me)

Quote from Will Cooke:
> While Wayland requires KMS (kernel mode setting) to be enabled, there is
a current limitation in the nvidia driver that causes X11 sessions to
crash with KMS. For this reason I am keeping KMS disabled by default, at
least for now. This is not going to be fixed anytime soon, as it
requires major changes in the driver.

Users who want to try Wayland with nvidia will have to set modeset=1 in
/etc/modprobe.d/nvidia-graphics-drivers.conf, and then update the
initramfs.

When KMS is enabled, GDM will start, but entering the default session
will fail with no error that is visible to the user. Ideally, I think we
would check if KMS is enabled with nvidia, and either show only the
Wayland sessions or maybe simply
default to the Wayland session.

I have filed a bug report about this, where I also explain how to check
if KMS is enabled:

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1697882](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1697882)

I hope it helps.

Regards,


And I also agree that (X11) xorg-xserver is a more pleasing/complete user experience.
I do have a satisfactory experience in a wayland session with the hacks listed in the random threads here in U+1

---

### Post by mc4man on 2017-07-10
> **1fallen said:**
> 

Quote from Will Cooke: Blah, Blah, Blah..


That's what I don't get, I have KMS enabled & the default session works fine. So what they're talking about I've no idea.

---

### Post by #&amp;thj^% on 2017-07-10
> **mc4man said:**
> That's what I don't get, I have KMS enabled & the default session works fine. So what they're talking about I've no idea.

Ok I think i have it now....KMS needs to be disabled first and just add the modeset=1. And don't forget to update the initramfs before rebooting
Will try this method a little later tonite.
Beware this setting will break the X11 session! (From my own experience ;)) And defaults to a wayland session.
Will report back later.
Just for the record my Graphic Specs are:
```
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 381.22

```

---

### Post by mc4man on 2017-07-10
> **1fallen said:**
> Ok I think i have it now....KMS needs to be disabled first and just add the modeset=1. And don't forget to update the initramfs before rebooting
Will try this method a little later tonite.
Beware this setting will break the X11 session! (From my own experience ;)) And defaults to a wayland session.
Will report back later.
Just for the record my Graphic Specs are:
```
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 381.22

```

look at my thread slightly below this one, I've got it working on both 17.10 & 16.04.2+, here the machine is a Haswell with 755m (I've a skylake with a 965m but it's currently on loan..
edit: and no, here wayland breaks, X11 (xserver-xorg) is just fine...

---

### Post by #&amp;thj^% on 2017-07-10
> **mc4man said:**
> look at my thread slightly below this one, I've got it working on both 17.10 & 16.04.2+, here the machine is a Haswell with 755m (I've a skylake with a 965m but it's currently on loan..
edit: and no, here wayland breaks, X11 (xserver-xorg) is just fine...

Well seems your right...wayland breaks with the changes I made ;)...Reverting back, So I can at least use prime-select.:D
About a week ago using the methods described by Will Cooke it would break my X11 login with GDM and wayland.
Thanks mc4man, I will continue playing till I get it right or Ubuntu dose. LOL

---

### Post by mc4man on 2017-07-10
> **1fallen said:**
> Well seems your right...wayland breaks with the changes I made ;)...Reverting back, So I can at least use prime-select.:D
About a week ago using the methods described by Will Cooke it would break my X11 login with GDM and wayland.
Thanks mc4man, I will continue playing till I get it right or Ubuntu dose. LOL
To me the only care is that KMS is the only way to take advantage of the Prime Synchronization available in xserver 1.19+. 
So for the moment the xserver experience has gained a lot, Wayland is still down the road so to speak. 

what bothered me about that bug report is it would serve to break this advance while gnome-shell, gnome-wayland, gdm & nvidia aren't ready to go yet..

---

### Post by #&amp;thj^% on 2017-07-10
> **mc4man said:**
> To me the only care is that KMS is the only way to take advantage of the Prime Synchronization available in xserver 1.19+. 
So for the moment the xserver experience has gained a lot, Wayland is still down the road so to speak. 
Yep I have noticed the changes, with this new option:
```
echo $DESKTOP_SESSION
ubuntu-wayland

```
I'm Going to go over your other thread now>
> **mc4man said:**
> 
what bothered me about that bug report is it would serve to break this advance while gnome-shell, gnome-wayland, gdm & nvidia aren't ready to go yet..
Agreeded...Have you been playing with Fedora and Nvidia-Wayland any?

---

### Post by mc4man on 2017-07-10
> **1fallen said:**
> 

Agreed...Have you been playing with Fedora and Nvidia-Wayland any?
Nope, pretty happy with 16.04.x which I'll keep advancing best I can. Actually keep 2 almost mirror installs, one on the nvidia drivers, the other on intel as both have their advantages, particularly between cuda or vdpau vs vaapi.
(- nvida gained some with  Prime Synchronization as previously I had to hack out lack of vsync that wasn't  as clean as it is now.

---

### Post by #&amp;thj^% on 2017-07-10
> **mc4man said:**
> Nope, pretty happy with 16.04.x which I'll keep advancing best I can. Actually keep 2 almost mirror installs, one on the nvidia 
I can see 16.04 Unity becoming a Collectors Item..so to speak:D
I also have a clone for safe keeping to show the Grand Kids i guess:D and One I tweak and play with pretty hard.(Rock Solid)

---

### Post by ventrical on 2017-07-11
> **1fallen said:**
> I can see 16.04 Unity becoming a Collectors Item..so to speak:D
I also have a clone for safe keeping to show the Grand Kids i guess:D and One I tweak and play with pretty hard.(Rock Solid)

+1 :) lol

---

### Post by mc4man on 2017-07-16
> **mc4man said:**
> . 

what bothered me about that bug report is it would serve to break this advance while gnome-shell, gnome-wayland, gdm & nvidia aren't ready to go yet..
The gist of this is the report was only about non hybrid machines using nvidia drivers. In other words nvidia-prime was unaffected. (never outright stated in report..
 Also noted was that there is currently  no wayland support for hybrid hardware so one must use xserver/xorg or don't use the nvidia drivers at all (thru nvidia-prime.
Not the worst 'news' as unless they want to exclude a whole class of hardware, xserver/xorg needs to remain available until such time there is wayland supoort for that hardware 
(or enough years pass to make such support irrelevant

---

