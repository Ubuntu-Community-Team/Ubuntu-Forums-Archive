---
title: "The only things frustrating me now about Ubuntu."
date: 2010-03-25
forum: Testimonials &amp; Experiences
---

### Post by Laxman_prodigy on 2010-03-25
Hi.
I have been using Ubuntu now for nearly 7 months. While I was browsing to find free softwares for Windows:-k, I found a link to download free linux OS called Ubuntu.

I was kind of very surprised on finding as to how can an OS be free. I was very keen on downloading it and I did.

I googled and really liked the philosophy and installed it. I was very sad on finding that .exe files don't run(haha) nor many proprietory softwares. Neither could I play or watch any song or video.

On browsing I found "Ubuntuforums" and was really surprised as to how large the community of Ubuntu is.

I became very happy on finding tutorials, tips, links and how-tos and now my system is with par or even better than I had setup my Windows system. Damn those viruses and other magnetic malwares.

Now, coming to my frustrations:

1. On playing mp3 and using "top" on the command line; cpu usage is 100% by pulse audio. I mean what is this? An mp3 playback taking all my cpu? I have Intel Core 2 duo machine.

2. Also, I am pissed off by mplayer. It has taken me now around 2 months and still I am not able to get vdpau support on playback. I have 8500GT card. 

I have used VLC and Totem. They are very good. But, I need to get the vdpau enabled player.

Since I joined this forum, I can't tell you here how much I have learned about the computer. I have never had any bad experience with any members or I have always been helped by the forum members.


And, there is one thing I would like to well draw attention: Many threads are well not answered but the community cafe is very busy.....

Regards.
(Laxman Neupane, New Delhi, India)

---

### Post by jpeddicord on 2010-03-25
*Moved to Ubuntu Testimonials & Experiences*

---

### Post by OgreProgrammer on 2010-03-25
> **Laxman_prodigy said:**
> Hi.

1. On playing mp3 and using "top" on the command line; cpu usage is 100% by pulse audio. I mean what is this? An mp3 playback taking all my cpu? I have Intel Core 2 duo 

It might be misreporting its usage. Is your machine lagging?

---

### Post by Laxman_prodigy on 2010-03-25
> **OgreProgrammer said:**
> It might be misreporting its usage. Is your machine lagging?


No, the machine doesn't seem to be lagging. It's okay. Can a command be considered unreliable?

But, the system manager also shows the same statistics.

When I listen to music or movie only it happens. I bet it has something to do with this pulseaudio.

On googling, I found that in Karmic there is no such issue.

Please help me as to what I should do?[-o<

---

### Post by Tamlynmac on 2010-03-25
> Laxman_prodigy
And, there is one thing I would like to well draw attention: Many threads are well not answered but the community cafe is very busy.....

Not all users are capable of answering all or any of the questions asked in the Help Sections, but still may enjoy the forum (Cafe/T&E, etc.). For example, I use 9.04 and have little to no experience with 9.10. My helping others with problems directly related to 9.10, is questionable at best.

Might I suggest you post a thread specifically asking your question in the appropriate Help Section and provide all the details, including your system specs. As the T&E is not a support section of the forums, as defined in both the T&E header and [this]("http://ubuntuforums.org/showthread.php?t=1343965") sticky.

It's been my experience that some threads in the help sections lack sufficient information when requesting assistance. That issue alone may impact the number of responses a requester receives. Keep in mind that those volunteers who regularly participate in the help sections also have limited time. They may choose to ignore threads that requires additional investment in extracting system info or other similar info. I always advise those who ask, to supply as much info as possible when seeking assistance. Thus, eliminating the need for additional info requests.

Good Luck and I hope you find the solution your searching for.

Just my $0.02 and opinions.

---

### Post by 3rdalbum on 2010-03-26
If you're using an old tutorial, then VDPAU will appear to be very difficult indeed to get working.

However, some clever people run an Nvidia/VDPAU repository for Karmic that will give you Nvidia drivers and VDPAU functionality without having to compile Mplayer. You can even use VDPAU in Gnome-Mplayer rather than fiddling around with mplayer on the command-line.

The repository can be added here:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Or simply put this into a command-line:

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-195 mplayer gnome-mplayer
```

---

### Post by stalkingwolf on 2010-03-26
and on the other hand there may be times that no matter how much information you post nobody seem to know the magick spell that will help you.

---

### Post by MarcusW on 2010-03-26
Try XBMC for VDPAU.

---

### Post by doas777 on 2010-03-26
I've had real troubles with geforce 8200-8500 cards that aren't present with other models. just little things like overscan control is not available (even if you manually put it in xorg it is ignored).
that may be half your issue with the VDPAU. 

also for mplayer, look for the ppa version, rather than the gnome-mplayer package in the repos, and consider using smplayer for a frontend. there is a ppa for it as well. 

good luck

---

