---
title: "Windows to Fedora to Ubuntu"
date: 2007-02-06
forum: Testimonials &amp; Experiences
---

### Post by bmartin on 2007-02-06
I've been using Linux for a few years now, mostly as a non-root user. I kept running into problems w/ Windows XP; my new laptop came with XP installed, but I could never reinstall it because the CD Key wasn't valid for the CD... MS has been very particular about that.

Eventually I got to the point where I couldn't take it any more and decided to give Linux a whirl. I was used to Fedora; I really like their distro; the RPM packaging system is especially appealing to me. A friend recommended Ubuntu, but it didn't play nicely with my USB devices. I ejected the Live CD and tossed it into my collection of distributions.

My brother's Dell's motherboard recently died a horrible death. His birthday is coming up soon; what better gift is there than a brand new computer? He's 10 and he plays lots of video games. After seeing how many free games there are for Linux, I decided that I'd load him up with a copy... but what distro? If he has any problems, he'll need help. Ubuntu was the obvious choice because of all the help provided.

I decided I should probably switch over to Ubuntu as well, in case he needs any help. The first thing I noticed was that my laptop (Ubuntu) was loading in about 1/3 the time of my PC (Fedora). This was odd; my PC has a much larger L2 cache, 3x the RAM, and a faster hard drive. The speed boost alone was enough to sell me on switching over. All of my computers run Ubuntu now, as does my girlfriend's PC and one of my room mates' laptops.

I now have 6 legit Windows keys (98, 2000 Pro, XP Home, and 3 XP Pro) not in use. None of these Ubuntu-powered computers lock up anymore. I can leave them on for days straight and the performance is the same as 5 minutes after I booted them. As I don't play the newer first-person shooters, I haven't seen a single downside to making the move. Quake 3 and the original Unreal Tournament v4.36 (running on Wine 0.9.30) run perfectly on my Linux boxes.

The Good:

-The speed of Ubuntu is unparalleled by similar types of distributions (e.g. Fedora, Mandriva, openSUSE).

-The ease of use is about on par with Fedora... which one is better depends on the specific task. However, you don't get as many "easter eggs" with Ubuntu. There are a lot of little problems that crop up in Fedora due to what I believe is "excessive kernel patching". One example would be Wine's complete refusal to run. Another would be the relative difficulty of getting ATI's fglrx driver to work properly; it was much easier on Ubuntu.

I'm not trying to put down Fedora; it's a great distro. The kernel used by Fedora seems "dirty" and I've had a lot of problems due to it. The speed was a huge issue; running Eclipse was unbearable.

-The amount of time it took me to get my system set up was much less than other distributions. There are tools to automate the installation of proprietary software. I had read about them long before installing Ubuntu, as I frequent digg.com.

-The community support is the best. I haven't been a Ubuntu used for long (this is my third day), but I've often had to look up distribution-independent information in an attempt to install strange/obscure/unsupported hardware. I've been able to get my USB wireless card and a strange Chinese web cam to run by finding instructions on these forums and applying them to other distributions.

The Bad:

-I need to compile from source quite frequently to get the latest version.

The Ugly:

-Many of the packages in the repos are a bit outdated. I read a post about Battle for Wesnoth a few minutes ago; I had noticed the same thing. Wine was also outdated. The old version of Wine caused my OpenGL to abort. Removing 0.9.29 and compiling/installing 0.9.30 made this problem go away.

-When I removed Wine using apt-get, it also removed a lot of X11 libs that were needed for 0.9.30. I had to track down removed libs (I realized they were gone much later) and reinstall them. I realize that a lot of people are emotionally attached to APT, but I was much happier with YUM.

-For compilation, I need more libraries than come with the default install and I have yet to locate a place to grab them from.

---

### Post by lhtown on 2007-02-06
Welcome to Ubuntu!

We are so attached to apt because it works so well and is so easy. Except for maybe an occasional install from source, I dare say most of us have never used anything but apt and debs. Also, if you are looking for packages like Wine, there are repositories where you can download new versions of them and either save them to your desktop and install them from there by clicking on them or add them to your sources list (/etc/apt/sources.list).

Also, it sounds like you might be interested in upgrading your computer to Feisty. It is getting pretty stable now. Generally, it wouldn't be recommendable for newbies since it is beta, but if you like to experiment and aren't doing anything mission critical or time sensitive, why not give it a try?

---

### Post by marx2k on 2007-02-06
Do you think Fiesty is ready for non-mission-critical prime time?

I have it installed in VMWare running under Edgy and it seems okay...

How would one upgrade Edgy to Fiesty without completely obliterating the system?

---

### Post by lhtown on 2007-02-07
Fiesty still has some issues to work through. It is useful mostly for playing around or debugging activities.

You can install two separate instances of Ubuntu on your hard drive on two different partitions. I would also suggest a separate directory for your home directory so you don't have to reinstall you personal files every time you reinstall Ubuntu.

---

### Post by rabid emu on 2007-02-07
I have my laptop tri-booted with XP, Edgy and Feisty.  For the most part Feisty has been very stable, actually.  I use it right now more than Edgy and haven't had any crashes or anything since I installed and set it up (display drivers were somewhat annoying, but once that got sorted out it was fine).  Many other people have problems though, so don't go by what I say :P

Also your brother has his own computer and he's 10?  Wow... kinda wish I did at that age.  I got my first computer at 18 for college.

---

