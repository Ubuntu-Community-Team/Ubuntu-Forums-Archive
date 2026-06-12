---
title: "Media Center Solutions in Linux?"
date: 2008-02-10
forum: The Cafe
---

### Post by Visti on 2008-02-10
Hi guys, I was wondering what media center solutions there actually are available for Linux. I'm looking for something to replace my LinuxMCE which is a bit sluggish in th UI and which, for some reason, can't be set to overscan correctly. I need something that I can set to output to my TV through S-video as standard (As in, my box won't be connected to a proper screen as it runs or maybe even during installation, if that works) and I'm very little interested in television playback of any sort. I just need to play video from my HD to my TV.

I'd love it if there was a standalone install or with an installer that optimally installed both, so I don't need to first install a distro and then a Media Center solution on top, but I can probably compromise there.. In fact, I'm a bit confused as to how the media center would even run with a solution like that? Choose it at the login screen?

What I've found so far:

Elisa - Looks amazing, but is a little early in development
Geexbox - The interface seems cumbersome, but the nvtv drivers gave my TV the right overscan out of the box after months of trying with LinuxMCE
Oxine - Also looks good, but haven't tried it yet as it needs to be installed onto a distribution
MMS - Same as above
Freevo - Very attractive interface, am going to try this one later today..

Also, most of the time I won't have a keyboard connected to the box, so there's another thing I'm having trouble with. Although that would be easily solved by me getting a better remote. The one I have now doesn't use LIRC, instead it's detected as a USB keyboard and needs remapping in X to work.. Pff.

Anyway, do any of you have any experience with these or others and what do you use if any?

Thanks in advance,
Emil Visti

---

### Post by kaivalagi on 2008-02-23
Any reason why you don't have MythTV listed?

There are several distros out which incorporate it, mythbuntu being the one based on ubuntu, currently version 7.10

I have just started setting up a HTPC with MythTV, after getting over most of the hardware hurdles I am now starting to learn about it.

I have a long way to go, but it certainly looks worth playing around with...

---

### Post by jpmswiss on 2008-03-16
Count me in to follow up on this one. While i like linuxmce - not everything is working...mythtv (also 2 channel sound), docs (pdf/doc).

Is mythbuntu or freevo better or more reliable?

Other solutions?

---

### Post by madjr on 2008-03-17
> **Visti said:**
>  I'm very little interested in television playback of any sort. I just need to play video from my HD to my TV.



why u need a media center for this ?

why not just use "Nvidia-settings":

connect to your TV

type "Nvidia-settings" in terminal.

detect displays.

[IMG]http://bp1.blogger.com/_Xc3ug-O4s-g/Rnf8lGbAURI/AAAAAAAAANs/kycMs0_2hWM/s400/screenshot-nvidia-settings.png[/IMG]

no need for media center unless you are building a dedicated box for it.

don't over complicate your self in you just want to view a few vids on the TV

[http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html](http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html)

---

### Post by PCFascist on 2008-03-29
But that would be near impossible to use a remote with. The mouse doesn't work so well on the sofa.


> **madjr said:**
> why u need a media center for this ?

why not just use "Nvidia-settings":

connect to your TV

type "Nvidia-settings" in terminal.

detect displays.

[IMG]http://bp1.blogger.com/_Xc3ug-O4s-g/Rnf8lGbAURI/AAAAAAAAANs/kycMs0_2hWM/s400/screenshot-nvidia-settings.png[/IMG]

no need for media center unless you are building a dedicated box for it.

don't over complicate your self in you just want to view a few vids on the TV

[http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html](http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html)

---

### Post by encompass on 2008-09-17
Once you get your screen cloned.  You can use elisa to play your videos with a remote.  But you need a remote or a keyboard.
I personally use ganyremote and my bluetooth java enabled cellphone.
PM me and I can help you through it.

---

### Post by Paqman on 2008-09-17
> **PCFascist said:**
> But that would be near impossible to use a remote with. The mouse doesn't work so well on the sofa.

I use a [wireless keyboard that has a trackpad](http://www.novatech.co.uk/novatech/specpage.html?NOV-MINIKB) for watching video files on my TV. Dead simple.

---

### Post by _sAm_ on 2008-09-17
Check out XBMC, its a program to install on top on a distro(like (x)Ubuntu). You can make it autostart when you turn the pc on(and do turn of the login screen). 

Its very fast, can play all sorts of files(even ISO files, try that in MS Mediacenter), and looks good.

[http://xbmc.org/](http://xbmc.org/)

Just add the repositories to Ubuntu and install it from Synaptic.
[http://xbmc.org/forum/showthread.php?p=185738](http://xbmc.org/forum/showthread.php?p=185738)

Looks like they will come with there own distro soon(my guess its Ubuntu with it).

---

### Post by ulukapata on 2008-09-17
this is good info.


[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by god0fgod on 2008-09-17
I hate that thing. Pointless. I demand that post be removed. That website is purely annoying. Get your unique visitors to go to something interesting.

---

### Post by wipeout140 on 2008-09-17
i would go with xbmc aswell, a excellent program been using it on the xbox 1 aswell on ubuntu 8.04

---

### Post by god0fgod on 2008-09-17
I can't install it. Even after adding the repository.

---

### Post by Patrick793 on 2008-09-17
You can't install what? XBMC?

What's going on with it that you won't install?
I thought it was just a Media Center made for the Xbox, and I never knew there was a Linux/Mac/Windows version. I'm installing it now with no problem.

Pretty obvious, but did you remember to sudo apt-get update?

---

### Post by god0fgod on 2008-09-17
Well it works now. I think the server was off-line. It said it couldn't find the package but I tried again a little bit later and it worked.

---

### Post by wolfen69 on 2008-09-17
i find mythbuntu to be awesome.

---

### Post by _sAm_ on 2008-09-18
> **god0fgod said:**
> I can't install it. Even after adding the repository.
It worked just fine for me. Did you run sudo apt-get update after adding the repository?

---

### Post by billgoldberg on 2008-09-18
Try out Boxee.

Video link:
[http://blog.boxee.tv/2008/08/04/boxee-reviewed-by-tekzilla/](http://blog.boxee.tv/2008/08/04/boxee-reviewed-by-tekzilla/)

I am using it and it is great.

You will need an invite. 

PM me and mention your email adress and I'll send you an invite.

---

### Post by fh_scott on 2008-09-24
> **Visti said:**
> Hi guys, I was wondering what media center solutions there actually are available for Linux.

have you looked at the [networked media tank]("http://www.networkedmediatank.com/") devices?

it's a linux-based dedicated media player.  the devices are marked under brands like istar and popcorn hour with various features derived from the oem standard.

I have an [istar]("http://www.istarhd.com") and it's a lot of fun to hack around with.

It comes with myIhome (or something like that) which enables media sharing across your lan.  java based and works with linux.

-scott

---

