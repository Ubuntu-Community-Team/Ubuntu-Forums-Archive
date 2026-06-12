---
title: "My experiences with Xubuntu"
date: 2014-05-19
forum: Ubuntu, Linux and OS Chat
---

### Post by antik2 on 2014-05-19
Hi there!

First of all, english is not my nativ language but I do my very best ;-)
I don't know if this is the right place, but I want to share my experiences with linux and especially Xubuntu (14.04).
There are a few things I've struggled with and a few things I'm still struggling.
I hope you will share your thoughts with me.

Before I start I will give a short description of my System:

CPU: Intel i7 4770
RAM: 16GB
SSD: 240GB
VGA: Nvidia Geforce GTX 780 Ti

Onboard Audio/Video is disabled by UEFI Bios

Very important: I've connected my graphics card with an av-receiver via hdmi to get high quality digital surround sound.
Video is forwarded by the receiver to a flat screen full-hd tv.

Experiences with the installation of Xubuntu 14.04 via DVD:
Like on most other Linux distributions I have to edit the grub boot entry and add "nomodeset". Otherwise my screen stays blank.
I think this is very critical because as a newbie this prevents you from installing ubuntu at all.
Now I was able to install Xubuntu. After installation the system reboots and gues what? Blank screen!
It's very problematic that after the installation grub menu is hidden by default. Even holding the shift key doesn't work, because grub menu waits for 0 seconds by default.
So there was no other way than booting again from dvd and fixing the grub config (either show grub menu longer than 0 seconds or directly add the nomodeset option) of the freshly installed xubuntu.
(OK, I guess most newbies were knocked out here!)
So now I was able to boot my installed xubuntu system. First thing I did of course was installing the proprietary nvidia drivers, so nomodeset option is no longer needed.

Hurray Xubuntu!

The Hell of Video Tearing:
Most fun of using Linux is gone, when you realize the terrifying video tearing while watching videos or playing games.
So I'm very lucky that I've already found a solution to this problem: Compositing with compton.
I've heard this could lead to performance problems, but since my system is pretty fast evrything is working very well here.
(Nevertheless I'm looking forward to Wayland, which hopefuly rescues us all from x-server terror)

Flash (or the unholy spirit of yesterdays technology):
Since I want to use chromium as web browser, I'm relying on pepperflash to display flash content.
Unfortunately this plugin don't seems to be able to view webvideos in fullscreen.
If I switch to fullscreen mode it only opens a large (but not maximized) window playing the video.
The fact, that most flash video players don't show me any video navigation in (this kind of) fullscreen mode, is also very frustrating.
But while html5 on the other hand works very well I hope that flash content disapears from the web constantly.

Ok, what's next?
One day I left my room and decided not to turn off my system as usual.
Instead I just turned off the tv.
When I came back and turned on the tv again, I realized that x must be crashed.
I rebooted and tried to reproduce this. BAM! Everytime I turn of the tv, x seems to crash.
Switching to tty1-6 works but ctrl+alt+f7 just shows me a blinking underscore.
This is frustrating and also not very energy efficient because I'm forced to leave the tv switched on!

Finally the mother of problems in linux desktop environments: sound!
I don't need to mention that sound quality suffers from resampling and resampling and reresampling again by alsa and pulseaudio.
But that is a point I can live with, if only I had the option to pass DD and DTS streams directly to my receiver.
Normaly I've done this by using VLC media player and configured it to use ALSA only.
Sometimes I need to use pasuspender to get the whole thing working. Sometimes it works without.
I guess this is because ALSA needs to block the whole device (which is exactly what I want in this case).
But now comes the next problem. If video is played correctly by VLC and I accidently change the playback volume of VLC,
the sound output becomes very very loud and distorted (even if I turn down the volume).

That's it!
Years ago I experienced much more problems which prevented me completely from using linux.
So the problems above seems now to be the remaining core problems of linux on my current system.
(I've tried a lot more linux distros but the problems stay mainly the same.)

What do you (especialy the experts among yourselves) think?
How far is Linux away from handle these sort of things?
Is linux on a good way to conquer the everyday desktop world?

Greetings,

AntiK

---

### Post by ventrical on 2014-05-20
I have had a few problems in the past with  matching monitors to a system. They were either too old or too new, but I just perservered and have always been successful in getting Ubuntu to work just fine. I have 11 machines , 9 towers and 3 laptops, all with Ubuntu on it. I have a few machines with Win7 and 8 because I have clients who  choose not to try Ubuntu and are die-hard Windows end_users. (they are always in need of anti-malware help so I needs to keep updated on new security issues with MicroSoft as it is extra buisness income).

  I have had only one instance (on an older machine) where I could not get sound and that was in the days of Lucid Lynx. (I solved it by changing sound cards) I hear of this problem always but I rarely see it here on my KVM.

> 
Very important: I've connected my graphics card with an av-receiver via hdmi to get high quality digital surround sound.
Video is forwarded by the receiver to a flat screen full-hd tv.


I am just curious if you did the original install while the above hardware arrangement was hooked up. The reason I ask is because even Ubuntu does have jockeying problems with monitors and video drivers from time to time. One of the really kewl things about Ubuntu is that one can easily switch hardware from one mo-bo to another and still have a hard install work just great but even Ubuntu has a hiccup now and then, especially with monitors.

 People who have < monitor> fails with newer monitors tend to forget that a lot of those monitors are designed for MicroSoft Windows(C) and there is a matter of loopback, which may not be there with Ubuntu on newer monitor unless install is run with original hookuo.

Great read.

Thanks ..

---

### Post by antik2 on 2014-05-20
Thanks for your reply! =)

I did the install with exactly the described hardware system.
I think my tv was neither designed for windows nor for linux but for watching tv in the first case ;-)
But you are right. I'm pretty sure this constellation of hardware tend to become problematic for linux systems.
Windows works like a charm but I realy prefer Linux because I like the power to choose =)

But I hope in future Linux will become better and better in handling such "home-cinema" like systems.
Having distributions like SteamOS or openelec in mind, I believe supporting this kind of systems is very important.
Unfortunately these distros don't fit me needs. I need the allround desktop ;-)

EDIT:
I forgot to mention that the sound related problems also have their origin in using digital audio over hdmi.
It's very important for me to have the ability of geting best quality digital surround sound.
At least while watching movies I want the system to pass DD or DTS streams directly to the av-receiver without any software conversions.
I know the problem of switching flawless between pcm and digital encoded streams is not as easy.
But the way pulseaudio tries to solve it (mixing everything into one pcm signal) is not what I want.

---

### Post by ventrical on 2014-05-20
There are these other distributions, Ubuntu Studio and Mythbuntu,

[http://cdimage.ubuntu.com/ubuntustudio/releases/14.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/14.04/release/)

[http://cdimage.ubuntu.com/mythbuntu/releases/14.04/release/](http://cdimage.ubuntu.com/mythbuntu/releases/14.04/release/)

The latter is  for setting up a direct system mostly for TV (but will work excellently like a desktop) I have experimented with them both. Ubuntu Studio is very stable. These releases may or may not  help with audio/visual specs.  You could always try the live DVDs.

Regards..

---

### Post by antik2 on 2014-05-20
Okay cool, thanks! =)
I will try these maybe next weekend.
I always thought the only difference between regular ubuntu and these is another set of applications preinstalled.

---

### Post by ventrical on 2014-05-20
btw .. those two distros use xubuntu-desktop!  :)

---

### Post by antik2 on 2014-05-20
Yeah, I really like Xfce and also Cinnamon for keeping the old fashioned desktop metaphor alive ;-)

---

### Post by Tar_Ni on 2014-05-20
> **antik2 said:**
> 
CPU: Intel i7 4770
RAM: 16GB
SSD: 240GB
VGA: Nvidia Geforce GTX 780 Ti

With those specs you could run Ubuntu like smooth, creamy butter!


> **antik2 said:**
> What do you (especialy the experts among yourselves) think?
How far is Linux away from handle these sort of things?
Is linux on a good way to conquer the everyday desktop world?

I am very optimistic that it will be the case. China is moving towards Ubuntu Kylin, as the governement and many of it's citizen are dropping out XP. Ubuntu is sold pre-installed in computers by Canonical's partners. So if the world's largest population use a Linux operating system massively in years to come, that will certainly have an impact worldwide.

[http://betanews.com/2014/02/16/the-chinese-love-ubuntu-linux-over-1-3-million-downloads-in-less-than-6-months/](http://betanews.com/2014/02/16/the-chinese-love-ubuntu-linux-over-1-3-million-downloads-in-less-than-6-months/)

[http://www.zdnet.com/china-switches-on-to-ubuntu-in-hunt-for-windows-xp-successor-7000026355/](http://www.zdnet.com/china-switches-on-to-ubuntu-in-hunt-for-windows-xp-successor-7000026355/)

---

### Post by mastablasta on 2014-05-21
i actually read through the wall of text and what i see is driver issue, driver issue, driver issue... for most of your issues nvidia is responsible so why not post on their forums how their stuff they claim to work in linux is actually not working propperly?

i agree newbie shouldn't battle with these issues. but these issues are from hardware manufacturers that do not release drivers as opensource (so they oculd be fixed) or they release closed source blobs that they do not want to fix.

furthermore on Linux preinstalled mashcine (non tech people buy OS preinstalled PC) driver issues do not exist. well at leats until the system upgrade (since again manufactures provide the initial install drivers but fail to update them).

---

### Post by antik2 on 2014-05-21
> [COLOR=#000000]for most of your issues nvidia is responsible[/COLOR]
So you think the success of linux on private desktops depends on the good will of hardware manufacturers?

I guess in their opinion the market for linux desktops is not big enough to serve.
On the other hand linux on dektops will not grow until these driver issues will be fixed.

It's a doom loop ;-)

I noticed that especially the nvidia related problems depends on what driver version is installed.
I always prefer to install the drivers from the distro repos, because they tend to work at best on that distro.
But since the different distros use different driver version some problems are fixed in one distro while they still apear in another.

In my case, when I received my new hardware I had to download the drivers from the nvidia website,
because the ones in the repos where too old and didn't work with my card.
A few months later only then I was able to work with the driver in the repos.

But you are right. Nvidia and the linux comunity should cooperate better and it's obvious that we are more interested in that than nvidia.
But I think a "**** you nvidia" wont help us out ;-)

Greetings,
AntiK

---

### Post by monkeybrain20122 on 2014-05-21
I installed xubuntu 14.04 on someone's old machine tonight, thinking may be it would be more feature completed than lubuntu so would save me some time installing stuffs. But it is even less functional than lubunu out of the box, what a shocker. synaptic are gdebi are not preinstalled, instead we have the Ubuntu Software centre (Not a great choice for a light distro). Battery icon is missing because I have to install a panel plugin, I still haven't figured out how to switch virtual workplaces except with the keyboard (no switcher or even little rectangles on the panel like lubuntu)The list of preinstalled apps is even smaler than lubuntu's. In pcmanfm I can configure delete to bypasses trash but I don't seem to be able to find that option in xubuntu, a web search lead to a blog where the guy said I have to make a thunar action script or something (though I don't remember having to do this in Manjaro)

And boy it is really ugly out of the box(what is with the blue and grey??)

My latest experience with xfce is with Majaro, it looks so much more polished and it is so much more feature complete out of the box than xubuntu.  I played with xubuntu a few years ago and felt that it was generally ok and was more polished than lubuntu. But my experience with xubuntu 14.04 tonight is rather underwheming. I get two old laptops tonight to replace xp with some linux distro, originally I planned to do two xubuntu. Now I am going back to lubuntu for the other one.

---

### Post by ventrical on 2014-05-21
> **monkeybrain20122 said:**
>  Now I am going back to lubuntu for the other one.


 I use lubuntu for difficult hardware. I can often install unity-desktop on top of lubuntu without invoking llvmpipe on some older graphics adapater cards. 14.04 has been a success for overclocking. also.

---

