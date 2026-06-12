---
title: "How do I update Ardour?"
date: 2010-04-22
forum: Ubuntu Studio
---

### Post by G-Sun on 2010-04-22
Hi!
I run Ubuntu 8.04 and will soon update to 10.04 I guess.
But until then.. How do I update Ardour.
Mine is 2.3 and the latest is 2.8 something isn't it?

---

### Post by sgx on 2010-04-22
> **G-Sun said:**
> Hi!
I run Ubuntu 8.04 and will soon update to 10.04 I guess.
But until then.. How do I update Ardour.
Mine is 2.3 and the latest is 2.8 something isn't it?

First, I would maintain both 8.04 and also the newest working version.
Linux audio has few stable realtime audio distros, 8.04 is one of them.

Second, learning to compile from sourcecode is pretty easy these days,
and is sometimes the only way to access the newest features of the best apps.

Third, use the newest working distro to get 2.8xxx and other current apps.
This is usually done from the synaptic package manager, of by following
the directions on a PPA website that hosts special packages to make life
easier for end users.

Assuming  Ardour2.8 and its dependencies are not available for Ubuntu Studio 8.04, (I don't know, I hope they are) through someones PPA, or a synaptic repository,
and you don't want to compile software from sourcecode, you first must update the libraries, gui tools, and OS tools it is designed to use. Sometimes it is not possible. To display what is needed, download a .deb ardour2.8 somewhere, and

sudo dpkg -i ardourxxx.deb

when it fails, it will list what is needed. Fetch those .deb files from the net. Some of those needed apps may fail to install, and mention their own dependencies, get them to, it can easily be a dozen or more things to install, but only takes an hour or so, and if you are lucky, you won't hit a dead end at the last second. Keeping a text editor open is handy to chronicle the list as you go, and save a copy of the commands that install lots of .debs in one go for future reference. And keep a collection of .debs for dark times. In synaptic, their is a preference to keep downloaded .debs in the cache, 
/var/cache/apt/archives
burn them to CD as needed.

Cheers :)

---

### Post by trulan on 2010-04-22
Khashayar's ppa has a good version of Ardour for Hardy.  His ppa is no longer maintained, but IIRC the version of Ardour in there works well:
[https://launchpad.net/~khashayar/+archive/ppa?field.series_filter=hardy](https://launchpad.net/~khashayar/+archive/ppa?field.series_filter=hardy)
You can add that ppa to your sources, then upgrade Ardour and whatever dependencies it pulls.  I wouldn't do a full upgrade from that ppa, just upgrade the things you need, then remove it from your sources so you don't upgrade more than you want to.

As sgx said, you can also build Ardour yourself.  I've done it several times, but I usually end up with two Ardours in my menu (I stink at packaging apparently).   There are very good instructions for compiling Ardour on their website:
[http://ardour.org/building](http://ardour.org/building)

---

### Post by G-Sun on 2010-04-23
Ok, looks a little complicated for me.
I think I'm gonna wait until I have my new harddisk here and installed Ubuntu Studio 10.04
But, thanks! I will come back to this post, If I need to later :)

---

### Post by cub on 2010-04-23
> **G-Sun said:**
> Ok, looks a little complicated for me.
I think I'm gonna wait until I have my new harddisk here and installed Ubuntu Studio 10.04
But, thanks! I will come back to this post, If I need to later :)
I have only bad experiences from compiling myself so I have given up. I let the people who know do it and until then I run the available versions.

Is there something in Ardour 2.8 you need or miss that is not in 2.3? Otherwise, do you need the upgrade or do you just *want* it? :)

---

### Post by G-Sun on 2010-04-23
> **cub said:**
> I have only bad experiences from compiling myself so I have given up. I let the people who know do it and until then I run the available versions.

Is there something in Ardour 2.8 you need or miss that is not in 2.3? Otherwise, do you need the upgrade or do you just *want* it? :)
I dont' know, but I want to get to know Ardour and I guess the best way is to have the latest version...

---

### Post by trulan on 2010-04-23
Just like most things in life, it looks more complicated than it actually is.  Installing software from a ppa works just like installing anything else in Ubuntu (you use Synaptic Package Manager and it takes care of all the details).  The only 'issue' to work through is pointing synaptic at the ppa, or 'adding it to your sources'.  It's not a big deal, really.  But I understand too if you'd rather not dig into that stuff.

And, I think you'll like 10.04.  I've been running it for a few weeks now (Beta of course) and it's very good.  There are a few things I had to tweak to get it the way I like it - they moved the window control buttons to the left side, for example, and the indicator panel felt cluttery - but they did a good job with it in spite of those few annoyances.

The biggest downside to 10.04 for audio enthusiasts is the lack of an RT (Real Time) kernel.  This isn't Ubuntu's fault at all, it's just how things happened.  But unless you're trying to run low latencies and high volumes of data (for instance, recording 8 or more tracks via firewire) I doubt you'll ever miss the RT kernel.  And if you need it, there are options, it's just not as convenient as it was under 8.04 or 9.10 (The two releases with good RT kernels).

---

### Post by cub on 2010-04-23
> **trulan said:**
> The biggest downside to 10.04 for audio enthusiasts is the lack of an RT (Real Time) kernel.  This isn't Ubuntu's fault at all, it's just how things happened.  But unless you're trying to run low latencies and high volumes of data (for instance, recording 8 or more tracks via firewire) I doubt you'll ever miss the RT kernel.  And if you need it, there are options, it's just not as convenient as it was under 8.04 or 9.10 (The two releases with good RT kernels).
Umm what? I have the RT option in my boot list when I start my 10.04 Beta 2. I did the same kind of upgrade from an "normal" 10.04 to studio 10.04 as I did going from "normal" 9.10 studio 9.10.

On the other hand, I record max 2 channels with an USB sound card. Is running a RT kernel unnecessary for me?

Sorry for going a bit off-track here...

---

### Post by G-Sun on 2010-04-23
> **trulan said:**
> 
The biggest downside to 10.04 for audio enthusiasts is the lack of an RT (Real Time) kernel. 
So, if I install 9.10 with RT, and the upgrade to 10.04.
Then I can run with RT?
Any cons?

---

### Post by trulan on 2010-04-24
The RT kernel from Karmic (9.10) is in the Lucid (10.04) repos.  So you can do a fresh install of 10.04, then add the RT kernel via Synaptic.  You know, I haven't done a fresh install of Ubuntu Studio 10.04 so I'm not 100% sure what kernel comes with it by default.  I've heard talk of a 'low-latency' desktop kernel but I haven't messed with it.

The deal with the kernels is, the guys who develop the real time pre-emption patches decided to jump from 2.6.31 to 2.6.33.  But 2.6.33 generic wasn't finished soon enough to make it into the Lucid release of Ubuntu.  So Lucid will use the 2.6.32 kernel, which leaves those of us who like RT the option of using the same kernel as Karmic (2.6.31-rt), or with compiling 2.6.33-rt for ourselves (or finding somebody else's 2.6.33-rt and using it.)

Enough 'fighting' over the numbers.  Realistically, will we see any problems from not having an RT kernel to match the generic kernel?  Probably not.  If you choose to go with 2.6.33-rt in Lucid you will probably run into a few issues with things like driver kernel modules not building without some hacking.

---

### Post by G-Sun on 2010-04-24
Ok, thanks! I get a clue about how this things work..

---

